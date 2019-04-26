---
ms.date: 08/24/2018
keywords: DSC, powershell, configuração, a configuração
title: Recursos de Script de DSC
ms.openlocfilehash: 4eee5625add4d96ade7ababf7f534f597a26712d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076995"
---
# <a name="dsc-script-resource"></a>Recursos de Script de DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.x

O **Script** recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para executar blocos de script do Windows PowerShell em nós de destino. O **Script** utilizações de recursos `GetScript`, `SetScript`, e `TestScript` operações de estado de propriedades que contêm os blocos de script que define para realizar o DSC correspondente.

## <a name="syntax"></a>Sintaxe

```
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> O `GetScript`, `TestScript`, e `SetScript` blocos são armazenados como cadeias de caracteres.

## <a name="properties"></a>Propriedades

|Propriedade|Descrição|
|--------|-----------|
|GetScript|Um bloco de script que retorna o estado atual do nó.|
|SetScript|Um bloco de script que utiliza o DSC para impor a conformidade quando o nó não está no estado pretendido.|
|TestScript|Um bloco de script que determina se o nó está no estado pretendido.|
|Credencial| Indica as credenciais a utilizar para executar este script, se as credenciais são necessárias.|
|DependsOn| Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será **ResourceName** e seu tipo é **ResourceType**, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.

### <a name="getscript"></a>GetScript

DSC não utiliza a saída do `GetScript`. O [Get-dscconfiguration para](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet é executado o `GetScript` para obter o estado atual de um nó. Não é necessário de um valor de retorno `GetScript`. Se especificar um valor de retorno, tem de ser um `hashtable` que contém um **resultado** chave cujo valor é um `String`.

### <a name="testscript"></a>TestScript

O `TestScript` executado pela DSC para determinar se o `SetScript` deve ser executado. Se o `TestScript` devolve `$false`, DSC executa o `SetScript` para colocar o nó para o estado pretendido. Tem de devolver um `boolean` valor. O resultado de `$true` indica que o nó está em conformidade e `SetScript` não deve ser executado.

O [Test-dscconfiguration para](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet, executa o `TestScript` para obter a conformidade de nós com o **Script** recursos. No entanto, no caso, o `SetScript` não é executado, não importa o que o `TestScript` bloquear devolve.

> [!NOTE]
> Todos os resultados da sua `TestScript` faz parte do valor de retorno. PowerShell interpreta unsuppressed saída diferente de zero, que significa que seu `TestScript` retornará `$true` independentemente do Estado de seu nó.
> Isso resulta em resultados imprevisíveis, falsos positivos e faz com que dificuldade durante a resolução de problemas.

### <a name="setscript"></a>SetScript

O `SetScript` modifica o nó para impor o estado pretendido. Ela é chamada pelo DSC se o `TestScript` devolve de bloco de script `$false`. O `SetScript` não deve ter nenhum valor de retorno.

## <a name="examples"></a>Exemplos

### <a name="example-1-write-sample-text-using-a-script-resource"></a>Exemplo 1: Escrever o texto de exemplo através de um recurso de Script

Neste exemplo, testa a existência de `C:\TempFolder\TestFile.txt` em cada nó. Se não existir, cria-o com o `SetScript`. O `GetScript` devolve o conteúdo do ficheiro e o valor de retorno não é utilizado.

```powershell
Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script ScriptExample
        {
            SetScript = {
                $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
                $sw.WriteLine("Some sample string")
                $sw.Close()
            }
            TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
            GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }
        }
    }
}
```

### <a name="example-2-compare-version-information-using-a-script-resource"></a>Exemplo 2: Comparar as informações de versão usando um recurso de Script

Este exemplo obtém o *em conformidade* informações sobre a versão de um ficheiro de texto no computador de criação e armazena-na `$version` variável. Ao gerar o ficheiro MOF do nó, DSC substitui o `$using:version` variáveis em cada script bloquear com o valor do `$version` variável. Durante a execução, o *em conformidade* versão é armazenada num arquivo de texto em cada nó e em comparação com e atualizada sobre as execuções subsequentes.

```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

                if( $state['Result'] -eq $using:version )
                {
                    Write-Verbose -Message ('{0} -eq {1}' -f $state['Result'],$using:version)
                    return $true
                }
                Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
                return $false
            }
            SetScript = {
                $using:version | Set-Content -Path (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            }
        }
    }
}
```
