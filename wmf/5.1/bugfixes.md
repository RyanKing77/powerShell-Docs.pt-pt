---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Correções de erros no WMF 5.1
ms.openlocfilehash: f53fc40b79a3906ac2025b0eff342c0705b82655
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085053"
---
# <a name="bug-fixes-in-wmf-51"></a>Correções de erros no WMF 5.1

## <a name="bug-fixes"></a>Correções de erros

Os bugs notáveis seguintes foram corrigidos no WMF 5.1:

### <a name="module-auto-discovery-fully-honors-envpsmodulepath"></a>A deteção automática de módulo completamente honra `$env:PSModulePath`

Módulo auto-discovery (módulos a carregar automaticamente sem um explícita Import-Module ao chamar um comando) foi introduzida no WMF 3.
Quando introduzida, o PowerShell marcada para comandos num `$PSHome\Modules` antes de utilizar `$env:PSModulePath`.

WMF 5.1 altera esse comportamento que respeite `$env:PSModulePath` completamente.
Este procedimento permite que um módulo de criação do utilizador que define os comandos fornecidos pelo PowerShell (por exemplo, `Get-ChildItem`) para ser automaticamente carregado e substituir corretamente o comando interno.

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a>Redirecionamento de ficheiros não mais impõe `-Encoding Unicode`

Em todas as versões anteriores do PowerShell, foi impossível controlar a codificação de ficheiro utilizado pela operadora de rede de redirecionamento de arquivo, por exemplo, `Get-ChildItem > out.txt` porque o PowerShell adicionados `-Encoding Unicode`.

A partir do WMF 5.1, pode agora alterar a codificação de ficheiro de redirecionamento ao definir `$PSDefaultParameterValues`:

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a>Foi corrigido um regressão ao aceder ao membros `System.Reflection.TypeInfo`

Uma regressão introduzida no WMF 5.0 interrompida membros ao aceder ao `System.Reflection.RuntimeType`, por exemplo, `[int].ImplementedInterfaces`.
Esse bug foi corrigido no WMF 5.1.


### <a name="fixed-some-issues-with-com-objects"></a>Corrigir alguns problemas com objetos COM

WMF 5.0 introduziu um novo associador de COM para invocar métodos em objetos COM e o acesso às propriedades de objetos COM.
Este novo associador melhorou significativamente o desempenho, mas também introduziu alguns bugs que tem sido corrigidos no WMF 5.1.

#### <a name="argument-conversions-were-not-always-performed-correctly"></a>Conversão de argumento não sempre executada corretamente

No exemplo a seguir:

```powershell
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

O método SendKeys espera uma cadeia de caracteres, mas o PowerShell não tiver convertido o caractere para uma cadeia de caracteres, adiar a conversão para IDispatch:: Invoke, que usa VariantChangeType para fazer a conversão, que, neste exemplo, enviar as chaves de '1', "7" e "3" em vez disso, o resultado da chave de Volume.Mute esperada.

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a>Enumerable objetos COM, nem sempre são processados corretamente

PowerShell normalmente enumera a maioria dos objetos de enumerable, mas uma regressão introduzida no WMF 5.0 impediu a enumeração de objetos COM que implemente IEnumerable.  Por exemplo:

```powershell
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

No exemplo acima, o WMF 5.0 escreveu incorretamente o Scripting.Dictionary para o pipeline em vez de enumerar os pares chave/valor.

Isto também alterar endereços [emitir 1752224 no Connect](https://connect.microsoft.com/PowerShell/feedback/details/1752224)

### <a name="ordered-was-not-allowed-inside-classes"></a>`[ordered]` Não foi permitida dentro de classes

WMF 5.0 introduziu classes com a validação de literais de tipo usadas nas classes.
`[ordered]` é semelhante a um literal de tipo, mas não é um tipo .NET verdadeiro.
WMF 5.0 incorretamente comunicou um erro no `[ordered]` dentro de uma classe:

```powershell
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a>Ajuda sobre os tópicos com várias versões não funciona

Antes de WMF 5.1, se tivesse várias versões de um módulo instalado e que todos os partilhados um tópico de ajuda, por exemplo, about_PSReadline, `help about_PSReadline` retornaria vários tópicos com nenhuma maneira óbvia para ver a ajuda de real.

WMF 5.1 corrige isso ao devolver a ajuda para a versão mais recente do tópico.

`Get-Help` não fornece uma forma de especificar a versão que pretende obter ajuda para.
Para contornar este problema, navegue para o diretório de módulos e exiba a ajuda do diretamente com uma ferramenta como o seu editor favorito.

### <a name="powershellexe-reading-from-stdin-stopped-working"></a>PowerShell.exe ler a partir do STDIN parou de funcionar

Os clientes utilizam `powershell -command -` desde aplicações nativas para executar o PowerShell passando no script via STDIN Infelizmente isso foi quebrado devido à outras alterações o host de console.

https://windowsserver.uservoice.com/forums/301869-powershell/suggestions/15854689-powershell-exe-command-is-broken-on-windows-10

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a>PowerShell.exe cria o pico na utilização da CPU na inicialização

PowerShell utiliza uma consulta WMI para verificar se ele foi iniciado por meio da diretiva de grupo para evitar que faz com que o atraso no início de sessão.
A consulta de WMI acaba injetar tzres.mui.dll cada processo no sistema, uma vez que a classe WMI Win32_Process tenta recuperar informações de fuso horário local.
Isso resulta num grande pico de CPU nas wmiprvse (o anfitrião do fornecedor WMI).
Correção é usar chamadas de API do Win32 para obter as mesmas informações em vez de usar o WMI.
