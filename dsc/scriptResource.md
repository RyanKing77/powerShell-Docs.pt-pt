---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Recurso de Script de DSC
ms.openlocfilehash: 6a39fbd914f9a0bb0f192b7b1f81f404bb6b93c1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-script-resource"></a>Recurso de Script de DSC


> Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

O **Script** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para executar os blocos de script do Windows PowerShell em nós de destino. O `Script` recurso tem `GetScript`, `SetScript`, e `TestScript` propriedades. Estas propriedades devem ser definidas para blocos de script que serão executada em cada nó de destino.

O `GetScript` bloco de script deve devolver uma tabela hash que representa o estado do nó atual. A tabela hash só pode conter uma chave `Result` e o valor tem de ser do tipo `String`. Não é necessário para devolver nada. DSC não faz nada com o resultado deste bloco de script.

O `TestScript` bloco de script deve determinar se o nó atual tem de ser modificado. Deverá devolver `$true` se o nó é atualizado. Deverá devolver `$false` se a configuração do nó está desatualizada e devem ser atualizada pelo `SetScript` bloco de script. O `TestScript` bloco de script é chamado pelo DSC.

O `SetScript` bloco de script deve modificar o nó. É denominado pelo DSC se o `TestScript` bloquear retorno `$false`.

Se tiver de utilizar variáveis do seu script de configuração no `GetScript`, `TestScript`, ou `SetScript` blocos de script, utilize o `$using:` âmbito (consulte abaixo para obter um exemplo).


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

## <a name="properties"></a>Propriedades

|  Propriedade  |  Descrição   |
|---|---|
| GetScript| Fornece um bloco de script do Windows PowerShell que é executado quando invocar o [Get-DscConfiguration](https://technet.microsoft.com/library/dn407379.aspx) cmdlet. Este bloco tem de devolver uma tabela hash. A tabela hash só pode conter uma chave **resultado** e o valor tem de ser do tipo **cadeia**.|
| SetScript| Fornece um bloco de script do Windows PowerShell. Quando invocar o [início DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet, a **TestScript** bloco executa primeiro. Se o **TestScript** bloquear devolve **$false**, a **SetScript** bloco será executado. Se o **TestScript** bloquear devolve **$true**, a **SetScript** blocos não serão executado.|
| TestScript| Fornece um bloco de script do Windows PowerShell. Quando invocar o [início DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) executa o cmdlet, este bloco. Se devolver **$false**, o bloco de SetScript será executado. Se devolver **$true**, SetScript bloco serão não executado. O **TestScript** bloco também é executada quando invocar o [teste DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet. No entanto, neste caso, o **SetScript** blocos não serão executados, independentemente do valor que o TestScript bloquear devolve. O **TestScript** bloco tem de devolver VERDADEIRO se a configuração real corresponder a configuração atual do estado pretendido e False se não corresponde. (É a última configuração enacted no nó que está a utilizar o DSC da configuração atual do estado pretendido.)|
| credencial| Indica as credenciais a utilizar para executar este script, se são necessárias credenciais.|
| dependsOn| Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado. Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é **ResourceName** e o respetivo tipo é **ResourceType**, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.

## <a name="example-1"></a>Exemplo 1
```powershell
Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script ScriptExample
    {
        SetScript =
        {
            $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
            $sw.WriteLine("Some sample string")
            $sw.Close()
        }
        TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
        GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }
    }
}
```

## <a name="example-2"></a>Exemplo 2
```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script UpdateConfigurationVersion
    {
        GetScript = {
            $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            return @{ 'Result' = "$currentVersion" }
        }
        TestScript = {
            $state = $GetScript
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
```

Este recurso é ao escrever a versão da configuração para um ficheiro de texto. Esta versão está disponível no computador cliente, mas não se encontra em nenhum de nós, pelo que tem de ser transferidos para cada um do `Script` blocos de script do recurso com o do PowerShell `using` âmbito. Quando MOF o nó a gerar ficheiro, o valor da `$version` variável é ler a partir de um ficheiro de texto no computador cliente. Substitui o DSC de `$using:version` bloquear variáveis em cada script com o valor da `$version` variável.