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
ms.locfileid: "34222195"
---
# <a name="bug-fixes-in-wmf-51"></a><span data-ttu-id="18f6a-103">Correções de erros no WMF 5.1#</span><span class="sxs-lookup"><span data-stu-id="18f6a-103">Bug Fixes in WMF 5.1#</span></span>

## <a name="bug-fixes"></a><span data-ttu-id="18f6a-104">Correções de erros</span><span class="sxs-lookup"><span data-stu-id="18f6a-104">Bug fixes</span></span> ##

<span data-ttu-id="18f6a-105">Os seguintes erros relevantes estão corrigidos no WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="18f6a-105">The following notable bugs are fixed in WMF 5.1:</span></span>

### <a name="module-auto-discovery-fully-honors-envpsmodulepath"></a><span data-ttu-id="18f6a-106">A deteção automática de módulo completamente honra `$env:PSModulePath`</span><span class="sxs-lookup"><span data-stu-id="18f6a-106">Module auto-discovery fully honors `$env:PSModulePath`</span></span> ###

<span data-ttu-id="18f6a-107">Módulo a deteção automática (módulos a carregar automaticamente sem um explícita Import-Module ao chamar um comando) foi introduzida no WMF 3.</span><span class="sxs-lookup"><span data-stu-id="18f6a-107">Module auto-discovery (loading modules automatically without an explicit Import-Module when calling a command) was introduced in WMF 3.</span></span>
<span data-ttu-id="18f6a-108">Ao introduziu, PowerShell verificado em termos de comandos no `$PSHome\Modules` antes de utilizar `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="18f6a-108">When introduced, PowerShell checked for commands in `$PSHome\Modules` before using `$env:PSModulePath`.</span></span>

<span data-ttu-id="18f6a-109">Este comportamento que respeite as alterações de WMF 5.1 `$env:PSModulePath` completamente.</span><span class="sxs-lookup"><span data-stu-id="18f6a-109">WMF 5.1 changes this behavior to honor `$env:PSModulePath` completely.</span></span>
<span data-ttu-id="18f6a-110">Este procedimento permite que um módulo criado por utilizador, que define os comandos fornecidos pelo PowerShell (por exemplo, `Get-ChildItem`) que seja automática-carregado e corretamente a substituir o comando incorporado.</span><span class="sxs-lookup"><span data-stu-id="18f6a-110">This allows for a user-authored module that defines commands provided by PowerShell (e.g. `Get-ChildItem`) to be auto-loaded and correctly overriding the built-in command.</span></span>

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a><span data-ttu-id="18f6a-111">Redirecionamento de ficheiros não mais impõe `-Encoding Unicode`</span><span class="sxs-lookup"><span data-stu-id="18f6a-111">File redirection no longer hard-codes `-Encoding Unicode`</span></span> ###

<span data-ttu-id="18f6a-112">Em todas as versões anteriores do PowerShell, foi impossível controlar a codificação de ficheiro utilizado pela operadora de rede de redirecionamento de ficheiro, por exemplo, `Get-ChildItem > out.txt` porque PowerShell adicionados `-Encoding Unicode`.</span><span class="sxs-lookup"><span data-stu-id="18f6a-112">In all previous versions of PowerShell, it was impossible to control the file encoding used by the file redirection operator, e.g. `Get-ChildItem > out.txt` because PowerShell added `-Encoding Unicode`.</span></span>

<span data-ttu-id="18f6a-113">A partir do WMF 5.1, agora, pode alterar a codificação de ficheiro de redirecionamento definindo `$PSDefaultParameterValues`:</span><span class="sxs-lookup"><span data-stu-id="18f6a-113">Starting with WMF 5.1, you can now change the file encoding of redirection by setting `$PSDefaultParameterValues`:</span></span>

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a><span data-ttu-id="18f6a-114">Corrigido um regressão ao aceder ao membros `System.Reflection.TypeInfo`</span><span class="sxs-lookup"><span data-stu-id="18f6a-114">Fixed a regression in accessing members of `System.Reflection.TypeInfo`</span></span> ###

<span data-ttu-id="18f6a-115">Um regressão introduzida no WMF 5.0 quebrou ao aceder aos membros de `System.Reflection.RuntimeType`, por exemplo, `[int].ImplementedInterfaces`.</span><span class="sxs-lookup"><span data-stu-id="18f6a-115">A regression introduced in WMF 5.0 broke accessing members of `System.Reflection.RuntimeType`, e.g. `[int].ImplementedInterfaces`.</span></span>
<span data-ttu-id="18f6a-116">Corrigir este erro no WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="18f6a-116">This bug has been fixed in WMF 5.1.</span></span>


### <a name="fixed-some-issues-with-com-objects"></a><span data-ttu-id="18f6a-117">Corrigir alguns problemas com a objectos COM</span><span class="sxs-lookup"><span data-stu-id="18f6a-117">Fixed some issues with COM objects</span></span> ###

<span data-ttu-id="18f6a-118">WMF 5.0 introduziu uma nova COM Gestor de enlaces para ao invocar métodos em objectos COM e aceder propriedades dos objectos COM.</span><span class="sxs-lookup"><span data-stu-id="18f6a-118">WMF 5.0 introduced a new COM binder for invoking methods on COM objects and accessing properties of COM objects.</span></span>
<span data-ttu-id="18f6a-119">O Gestor de enlaces novo melhorada significativamente o desempenho, mas também introduziu alguns erros que foram corrigidos no WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="18f6a-119">This new binder improved performance significantly but also introduced some bugs which have been fixed in WMF 5.1.</span></span>

#### <a name="argument-conversions-were-not-always-performed-correctly"></a><span data-ttu-id="18f6a-120">Conversões de argumento não sempre executados corretamente</span><span class="sxs-lookup"><span data-stu-id="18f6a-120">Argument conversions were not always performed correctly</span></span> ####

<span data-ttu-id="18f6a-121">No exemplo seguinte:</span><span class="sxs-lookup"><span data-stu-id="18f6a-121">In the following example:</span></span>

```
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

<span data-ttu-id="18f6a-122">O método SendKeys espera uma cadeia, mas PowerShell não converter o char numa cadeia, diferir a conversão para IDispatch::, que utiliza VariantChangeType para efetuar a conversão, que, neste exemplo, resultou no envio em vez disso, as chaves de '1', '7' e '3' a chave de Volume.Mute esperado.</span><span class="sxs-lookup"><span data-stu-id="18f6a-122">The SendKeys method expects a string, but PowerShell did not convert the char to a string, deferring the conversion to IDispatch::Invoke, which uses VariantChangeType to do the conversion, which in this example resulted in sending the keys '1', '7', and '3' instead of the expected Volume.Mute key.</span></span>

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a><span data-ttu-id="18f6a-123">Objetos de COM enumeráveis não sempre processadas corretamente</span><span class="sxs-lookup"><span data-stu-id="18f6a-123">Enumerable COM objects not always handled correctly</span></span> ####

<span data-ttu-id="18f6a-124">PowerShell normalmente enumera a maior parte dos objetos enumeráveis, mas um regressão introduzida no WMF 5.0 impediu a enumeração de objetos COM que implementem IEnumerable.</span><span class="sxs-lookup"><span data-stu-id="18f6a-124">PowerShell normally enumerates most enumerable objects, but a regression introduced in WMF 5.0 prevented the enumeration of COM objects that implement IEnumerable.</span></span>  <span data-ttu-id="18f6a-125">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="18f6a-125">For example:</span></span>

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

<span data-ttu-id="18f6a-126">No exemplo acima, WMF 5.0 escrito incorretamente o Scripting.Dictionary pipeline em vez de enumerar os pares chave/valor.</span><span class="sxs-lookup"><span data-stu-id="18f6a-126">In the above example, WMF 5.0 incorrectly wrote the Scripting.Dictionary to the pipeline instead of enumerating the key/value pairs.</span></span>

<span data-ttu-id="18f6a-127">Isto também alterar endereços [emitir 1752224 no Connect](https://connect.microsoft.com/PowerShell/feedback/details/1752224)</span><span class="sxs-lookup"><span data-stu-id="18f6a-127">This change also addresses [issue 1752224 on Connect](https://connect.microsoft.com/PowerShell/feedback/details/1752224)</span></span>

### <a name="ordered-was-not-allowed-inside-classes"></a><span data-ttu-id="18f6a-128">`[ordered]` Não foi permitida dentro de classes</span><span class="sxs-lookup"><span data-stu-id="18f6a-128">`[ordered]` was not allowed inside classes</span></span> ###

<span data-ttu-id="18f6a-129">WMF 5.0 introduzida classes com validação do tipo os literais que são utilizados em classes.</span><span class="sxs-lookup"><span data-stu-id="18f6a-129">WMF 5.0 introduced classes with validation of type literals used in classes.</span></span>
<span data-ttu-id="18f6a-130">`[ordered]` aspeto de um tipo de literal mas não é um tipo .NET verdadeiro.</span><span class="sxs-lookup"><span data-stu-id="18f6a-130">`[ordered]` looks like a type literal but is not a true .NET type.</span></span>
<span data-ttu-id="18f6a-131">WMF 5.0 incorretamente comunicou um erro no `[ordered]` dentro de uma classe:</span><span class="sxs-lookup"><span data-stu-id="18f6a-131">WMF 5.0 incorrectly reported an error on `[ordered]` inside a class:</span></span>

```
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a><span data-ttu-id="18f6a-132">Ajuda sobre sobre tópicos com várias versões não funciona</span><span class="sxs-lookup"><span data-stu-id="18f6a-132">Help on About topics with multiple versions does not work</span></span> ###

<span data-ttu-id="18f6a-133">Antes de WMF 5.1, se tiver várias versões de um módulo instalado e todos eles partilhada um tópico de ajuda, por exemplo, about_PSReadline, `help about_PSReadline` iria devolver vários tópicos com nenhuma forma óbvios para ver a ajuda real.</span><span class="sxs-lookup"><span data-stu-id="18f6a-133">Before WMF 5.1, if you had multiple versions of a module installed and they all shared a help topic, for example, about_PSReadline, `help about_PSReadline` would return multiple topics with no obvious way to view the real help.</span></span>

<span data-ttu-id="18f6a-134">WMF 5.1 corrige isto, devolvendo a ajuda para a versão mais recente do tópico.</span><span class="sxs-lookup"><span data-stu-id="18f6a-134">WMF 5.1 fixes this by returning the help for the latest version of the topic.</span></span>

<span data-ttu-id="18f6a-135">`Get-Help` não fornece uma forma para especificar que versão pretende obter ajuda para.</span><span class="sxs-lookup"><span data-stu-id="18f6a-135">`Get-Help` does not provide a way to specify which version you want help for.</span></span>
<span data-ttu-id="18f6a-136">Para contornar este problema, navegue para o diretório de módulos e ver a ajuda diretamente com uma ferramenta como o seu editor favorito.</span><span class="sxs-lookup"><span data-stu-id="18f6a-136">To work around this, navigate to the modules directory and view the help directly with a tool like your favorite editor.</span></span>

### <a name="powershellexe-reading-from-stdin-stopped-working"></a><span data-ttu-id="18f6a-137">PowerShell.exe ler a partir de STDIN parou de funcionar</span><span class="sxs-lookup"><span data-stu-id="18f6a-137">powershell.exe reading from STDIN stopped working</span></span>

<span data-ttu-id="18f6a-138">Os clientes utilizam `powershell -command -` de aplicações nativas para executar o PowerShell transmitir no script através de STDIN Lamentamos, mas isto foi está inoperacional devido a outras alterações do anfitrião da consola.</span><span class="sxs-lookup"><span data-stu-id="18f6a-138">Customers use `powershell -command -` from native apps to execute PowerShell passing in the script via STDIN unfortunately this was broken due to other changes it the console host.</span></span>

https://windowsserver.uservoice.com/forums/301869-powershell/suggestions/15854689-powershell-exe-command-is-broken-on-windows-10

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a><span data-ttu-id="18f6a-139">PowerShell.exe cria pico de pedidos na utilização da CPU no arranque</span><span class="sxs-lookup"><span data-stu-id="18f6a-139">powershell.exe creates spike in CPU usage on startup</span></span>

<span data-ttu-id="18f6a-140">PowerShell utiliza uma consulta WMI para verificar se foi iniciado através da política de grupo para evitar a causar o atraso no início de sessão.</span><span class="sxs-lookup"><span data-stu-id="18f6a-140">PowerShell uses a WMI query to check if it was started via Group Policy to avoid causing delay in login.</span></span>
<span data-ttu-id="18f6a-141">A consulta de WMI termina inserirem tzres.mui.dll para cada processo no sistema, uma vez que a classe WMI Win32_Process tenta obter informações de fuso horário local.</span><span class="sxs-lookup"><span data-stu-id="18f6a-141">The WMI query ends up injecting tzres.mui.dll into every process on the system since the WMI Win32_Process class attempts to retrieve local timezone information.</span></span>
<span data-ttu-id="18f6a-142">Isto resulta num grande CPU pico de pedidos de wmiprvse (o anfitrião do fornecedor WMI).</span><span class="sxs-lookup"><span data-stu-id="18f6a-142">This results in a large CPU spike in wmiprvse (the WMI provider host).</span></span>
<span data-ttu-id="18f6a-143">Corrija consiste em utilizar chamadas da Win32 API para obter as mesmas informações em vez de através do WMI.</span><span class="sxs-lookup"><span data-stu-id="18f6a-143">Fix is to use Win32 API calls to get the same information instead of using WMI.</span></span>
