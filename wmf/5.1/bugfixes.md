---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Correções de erros no WMF 5.1
ms.openlocfilehash: 1e46d6d0419b3497450e6eaddbaa47456b004691
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="bug-fixes-in-wmf-51"></a>Correções de erros no WMF 5.1#

## <a name="bug-fixes"></a>Correções de erros ##

Os seguintes erros relevantes estão corrigidos no WMF 5.1:

### <a name="module-auto-discovery-fully-honors-envpsmodulepath"></a>A deteção automática de módulo completamente honra `$env:PSModulePath` ###

Módulo a deteção automática (módulos a carregar automaticamente sem um explícita Import-Module ao chamar um comando) foi introduzida no WMF 3.
Ao introduziu, PowerShell verificado em termos de comandos no `$PSHome\Modules` antes de utilizar `$env:PSModulePath`.

Este comportamento que respeite as alterações de WMF 5.1 `$env:PSModulePath` completamente.
Este procedimento permite que um módulo criado por utilizador, que define os comandos fornecidos pelo PowerShell (por exemplo, `Get-ChildItem`) que seja automática-carregado e corretamente a substituir o comando incorporado.

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a>Redirecionamento de ficheiros não mais impõe `-Encoding Unicode` ###

Em todas as versões anteriores do PowerShell, foi impossível controlar a codificação de ficheiro utilizado pela operadora de rede de redirecionamento de ficheiro, por exemplo, `Get-ChildItem > out.txt` porque PowerShell adicionados `-Encoding Unicode`.

A partir do WMF 5.1, agora, pode alterar a codificação de ficheiro de redirecionamento definindo `$PSDefaultParameterValues`:

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a>Corrigido um regressão ao aceder ao membros `System.Reflection.TypeInfo` ###

Um regressão introduzida no WMF 5.0 quebrou ao aceder aos membros de `System.Reflection.RuntimeType`, por exemplo, `[int].ImplementedInterfaces`.
Corrigir este erro no WMF 5.1.


### <a name="fixed-some-issues-with-com-objects"></a>Corrigir alguns problemas com a objectos COM ###

WMF 5.0 introduziu uma nova COM Gestor de enlaces para ao invocar métodos em objectos COM e aceder propriedades dos objectos COM.
O Gestor de enlaces novo melhorada significativamente o desempenho, mas também introduziu alguns erros que foram corrigidos no WMF 5.1.

#### <a name="argument-conversions-were-not-always-performed-correctly"></a>Conversões de argumento não sempre executados corretamente ####

No exemplo seguinte:

```
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

O método SendKeys espera uma cadeia, mas PowerShell não converter o char numa cadeia, diferir a conversão para IDispatch::, que utiliza VariantChangeType para efetuar a conversão, que, neste exemplo, resultou no envio em vez disso, as chaves de '1', '7' e '3' a chave de Volume.Mute esperado.

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a>Objetos de COM enumeráveis não sempre processadas corretamente ####

PowerShell normalmente enumera a maior parte dos objetos enumeráveis, mas um regressão introduzida no WMF 5.0 impediu a enumeração de objetos COM que implementem IEnumerable.  Por exemplo:

```
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

No exemplo acima, WMF 5.0 escrito incorretamente o Scripting.Dictionary pipeline em vez de enumerar os pares chave/valor.

Isto também alterar endereços [emitir 1752224 no Connect](https://connect.microsoft.com/PowerShell/feedback/details/1752224)

### <a name="ordered-was-not-allowed-inside-classes"></a>`[ordered]` Não foi permitida dentro de classes ###

WMF 5.0 introduzida classes com validação do tipo os literais que são utilizados em classes.
`[ordered]` aspeto de um tipo de literal mas não é um tipo .NET verdadeiro.
WMF 5.0 incorretamente comunicou um erro no `[ordered]` dentro de uma classe:

```
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a>Ajuda sobre sobre tópicos com várias versões não funciona ###

Antes de WMF 5.1, se tiver várias versões de um módulo instalado e todos eles partilhada um tópico de ajuda, por exemplo, about_PSReadline, `help about_PSReadline` iria devolver vários tópicos com nenhuma forma óbvios para ver a ajuda real.

WMF 5.1 corrige isto, devolvendo a ajuda para a versão mais recente do tópico.

`Get-Help` não fornece uma forma para especificar que versão pretende obter ajuda para.
Para contornar este problema, navegue para o diretório de módulos e ver a ajuda diretamente com uma ferramenta como o seu editor favorito.

### <a name="powershellexe-reading-from-stdin-stopped-working"></a>PowerShell.exe ler a partir de STDIN parou de funcionar

Os clientes utilizam `powershell -command -` de aplicações nativas para executar o PowerShell transmitir no script através de STDIN Lamentamos, mas isto foi está inoperacional devido a outras alterações do anfitrião da consola.

https://windowsserver.uservoice.com/forums/301869-powershell/suggestions/15854689-powershell-exe-command-is-broken-on-windows-10

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a>PowerShell.exe cria pico de pedidos na utilização da CPU no arranque

PowerShell utiliza uma consulta WMI para verificar se foi iniciado através da política de grupo para evitar a causar o atraso no início de sessão.
A consulta de WMI termina inserirem tzres.mui.dll para cada processo no sistema, uma vez que a classe WMI Win32_Process tenta obter informações de fuso horário local.
Isto resulta num grande CPU pico de pedidos de wmiprvse (o anfitrião do fornecedor WMI).
Corrija consiste em utilizar chamadas da Win32 API para obter as mesmas informações em vez de através do WMI.
