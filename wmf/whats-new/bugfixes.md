---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Correções de erros no WMF 5.1
ms.openlocfilehash: 8edf295eb6304dc04de2fa5d3792b1c2fc4b01f3
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856211"
---
# <a name="bug-fixes-in-wmf-51"></a><span data-ttu-id="11784-103">Correções de erros no WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="11784-103">Bug Fixes in WMF 5.1</span></span>

## <a name="bug-fixes"></a><span data-ttu-id="11784-104">Correções de erros</span><span class="sxs-lookup"><span data-stu-id="11784-104">Bug fixes</span></span>

<span data-ttu-id="11784-105">Os bugs notáveis seguintes foram corrigidos no WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="11784-105">The following notable bugs are fixed in WMF 5.1:</span></span>

### <a name="module-auto-discovery-fully-honors-psmodulepath"></a><span data-ttu-id="11784-106">A deteção automática de módulo completamente honra PSModulePath</span><span class="sxs-lookup"><span data-stu-id="11784-106">Module auto-discovery fully honors PSModulePath</span></span>

<span data-ttu-id="11784-107">Módulo auto-discovery (módulos a carregar automaticamente sem um explícita Import-Module ao chamar um comando) foi introduzida no WMF 3.</span><span class="sxs-lookup"><span data-stu-id="11784-107">Module auto-discovery (loading modules automatically without an explicit Import-Module when calling a command) was introduced in WMF 3.</span></span> <span data-ttu-id="11784-108">Quando introduzida, o PowerShell marcada para comandos num `$PSHome\Modules` antes de utilizar `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="11784-108">When introduced, PowerShell checked for commands in `$PSHome\Modules` before using `$env:PSModulePath`.</span></span>

<span data-ttu-id="11784-109">WMF 5.1 altera esse comportamento que respeite `$env:PSModulePath` completamente.</span><span class="sxs-lookup"><span data-stu-id="11784-109">WMF 5.1 changes this behavior to honor `$env:PSModulePath` completely.</span></span> <span data-ttu-id="11784-110">Este procedimento permite que um módulo de criação do utilizador que define os comandos fornecidos pelo PowerShell (por exemplo, `Get-ChildItem`) para ser automaticamente carregado e substituir corretamente o comando interno.</span><span class="sxs-lookup"><span data-stu-id="11784-110">This allows for a user-authored module that defines commands provided by PowerShell (e.g. `Get-ChildItem`) to be auto-loaded and correctly overriding the built-in command.</span></span>

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a><span data-ttu-id="11784-111">Redirecionamento de ficheiros não mais impõe-codificação Unicode</span><span class="sxs-lookup"><span data-stu-id="11784-111">File redirection no longer hard-codes -Encoding Unicode</span></span>

<span data-ttu-id="11784-112">Em todas as versões anteriores do PowerShell, foi impossível controlar a codificação de ficheiro utilizado pelo operador de redirecionamento de arquivo.</span><span class="sxs-lookup"><span data-stu-id="11784-112">In all previous versions of PowerShell, it was impossible to control the file encoding used by the file redirection operator.</span></span>

<span data-ttu-id="11784-113">A partir do WMF 5.1, pode agora alterar a codificação de ficheiro de redirecionamento ao definir `$PSDefaultParameterValues`:</span><span class="sxs-lookup"><span data-stu-id="11784-113">Starting with WMF 5.1, you can now change the file encoding of redirection by setting `$PSDefaultParameterValues`:</span></span>

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a><span data-ttu-id="11784-114">Foi corrigido um regressão ao aceder ao membros de System.Reflection.TypeInfo</span><span class="sxs-lookup"><span data-stu-id="11784-114">Fixed a regression in accessing members of System.Reflection.TypeInfo</span></span>

<span data-ttu-id="11784-115">Uma regressão introduzida no WMF 5.0 interrompida membros ao aceder ao `System.Reflection.RuntimeType`, por exemplo, `[int].ImplementedInterfaces`.</span><span class="sxs-lookup"><span data-stu-id="11784-115">A regression introduced in WMF 5.0 broke accessing members of `System.Reflection.RuntimeType`, for example, `[int].ImplementedInterfaces`.</span></span> <span data-ttu-id="11784-116">Esse bug foi corrigido no WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="11784-116">This bug has been fixed in WMF 5.1.</span></span>

### <a name="fixed-some-issues-with-com-objects"></a><span data-ttu-id="11784-117">Corrigir alguns problemas com objetos COM</span><span class="sxs-lookup"><span data-stu-id="11784-117">Fixed some issues with COM objects</span></span>

<span data-ttu-id="11784-118">WMF 5.0 introduziu um novo associador de COM para invocar métodos em objetos COM e o acesso às propriedades de objetos COM.</span><span class="sxs-lookup"><span data-stu-id="11784-118">WMF 5.0 introduced a new COM binder for invoking methods on COM objects and accessing properties of COM objects.</span></span> <span data-ttu-id="11784-119">Este novo associador melhorou significativamente o desempenho, mas também introduziu alguns bugs que tem sido corrigidos no WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="11784-119">This new binder improved performance significantly but also introduced some bugs which have been fixed in WMF 5.1.</span></span>

#### <a name="argument-conversions-were-not-always-performed-correctly"></a><span data-ttu-id="11784-120">Conversão de argumento não sempre executada corretamente</span><span class="sxs-lookup"><span data-stu-id="11784-120">Argument conversions were not always performed correctly</span></span>

<span data-ttu-id="11784-121">No exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="11784-121">In the following example:</span></span>

```powershell
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

<span data-ttu-id="11784-122">O **SendKeys** método espera uma cadeia de caracteres, mas o PowerShell não tiver convertido o caractere para uma cadeia de caracteres, adiar a conversão para **IDispatch:: Invoke**, que utiliza **VariantChangeType**para efetuar a conversão.</span><span class="sxs-lookup"><span data-stu-id="11784-122">The **SendKeys** method expects a string, but PowerShell did not convert the char to a string, deferring the conversion to **IDispatch::Invoke**, which uses **VariantChangeType** to do the conversion.</span></span> <span data-ttu-id="11784-123">Neste exemplo, isso resultou em enviar as chaves de '1', "7" e "3" em vez da esperada **Volume.Mute** chave.</span><span class="sxs-lookup"><span data-stu-id="11784-123">In this example, this resulted in sending the keys '1', '7', and '3' instead of the expected **Volume.Mute** key.</span></span>

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a><span data-ttu-id="11784-124">Enumerable objetos COM, nem sempre são processados corretamente</span><span class="sxs-lookup"><span data-stu-id="11784-124">Enumerable COM objects not always handled correctly</span></span>

<span data-ttu-id="11784-125">PowerShell normalmente enumera a maioria dos objetos de enumerable, mas uma regressão introduzida no WMF 5.0 impediu a enumeração de objetos COM que implemente IEnumerable.</span><span class="sxs-lookup"><span data-stu-id="11784-125">PowerShell normally enumerates most enumerable objects, but a regression introduced in WMF 5.0 prevented the enumeration of COM objects that implement IEnumerable.</span></span> <span data-ttu-id="11784-126">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="11784-126">For example:</span></span>

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

<span data-ttu-id="11784-127">No exemplo acima, WMF 5.0 escreveu incorretamente o **Scripting.Dictionary** para o pipeline em vez de enumerar os pares chave/valor.</span><span class="sxs-lookup"><span data-stu-id="11784-127">In the above example, WMF 5.0 incorrectly wrote the **Scripting.Dictionary** to the pipeline instead of enumerating the key/value pairs.</span></span>

### <a name="ordered-was-not-allowed-inside-classes"></a><span data-ttu-id="11784-128">[pedido] não foi permitida dentro de classes</span><span class="sxs-lookup"><span data-stu-id="11784-128">[ordered] was not allowed inside classes</span></span>

<span data-ttu-id="11784-129">WMF 5.0 introduziu classes com a validação de literais de tipo usadas nas classes.</span><span class="sxs-lookup"><span data-stu-id="11784-129">WMF 5.0 introduced classes with validation of type literals used in classes.</span></span> <span data-ttu-id="11784-130">`[ordered]` é semelhante a um literal de tipo, mas não é um tipo .NET verdadeiro.</span><span class="sxs-lookup"><span data-stu-id="11784-130">`[ordered]` looks like a type literal but is not a true .NET type.</span></span> <span data-ttu-id="11784-131">WMF 5.0 incorretamente comunicou um erro no `[ordered]` dentro de uma classe:</span><span class="sxs-lookup"><span data-stu-id="11784-131">WMF 5.0 incorrectly reported an error on `[ordered]` inside a class:</span></span>

```powershell
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```

### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a><span data-ttu-id="11784-132">Ajuda sobre os tópicos com várias versões não funciona</span><span class="sxs-lookup"><span data-stu-id="11784-132">Help on About topics with multiple versions does not work</span></span>

<span data-ttu-id="11784-133">Antes de WMF 5.1, se tivesse várias versões de um módulo instalado e que todos os partilhados um tópico de ajuda, por exemplo, about_PSReadline, `help about_PSReadline` retornaria vários tópicos com nenhuma maneira óbvia para ver a ajuda de real.</span><span class="sxs-lookup"><span data-stu-id="11784-133">Before WMF 5.1, if you had multiple versions of a module installed and they all shared a help topic, for example, about_PSReadline, `help about_PSReadline` would return multiple topics with no obvious way to view the real help.</span></span>

<span data-ttu-id="11784-134">WMF 5.1 corrige isso ao devolver a ajuda para a versão mais recente do tópico.</span><span class="sxs-lookup"><span data-stu-id="11784-134">WMF 5.1 fixes this by returning the help for the latest version of the topic.</span></span>

<span data-ttu-id="11784-135">`Get-Help` não fornece uma forma de especificar a versão que pretende obter ajuda para.</span><span class="sxs-lookup"><span data-stu-id="11784-135">`Get-Help` does not provide a way to specify which version you want help for.</span></span> <span data-ttu-id="11784-136">Para contornar este problema, navegue para o diretório de módulos e exiba a ajuda do diretamente com uma ferramenta como o seu editor favorito.</span><span class="sxs-lookup"><span data-stu-id="11784-136">To work around this, navigate to the modules directory and view the help directly with a tool like your favorite editor.</span></span>

### <a name="powershellexe-reading-from-stdin-stopped-working"></a><span data-ttu-id="11784-137">PowerShell.exe ler a partir do STDIN parou de funcionar</span><span class="sxs-lookup"><span data-stu-id="11784-137">powershell.exe reading from STDIN stopped working</span></span>

<span data-ttu-id="11784-138">Os clientes utilizam `powershell -command -` desde aplicações nativas para executar o PowerShell passando no script via STDIN Infelizmente isso foi dividida por outras alterações no host de console.</span><span class="sxs-lookup"><span data-stu-id="11784-138">Customers use `powershell -command -` from native apps to execute PowerShell passing in the script via STDIN unfortunately this was broken by other changes in the console host.</span></span>

<span data-ttu-id="11784-139">Isso é corrigido para a versão 5.1 no Windows 10 Anniversary Update.</span><span class="sxs-lookup"><span data-stu-id="11784-139">This is fixed for version 5.1 in the Windows 10 Anniversary Update.</span></span>

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a><span data-ttu-id="11784-140">PowerShell.exe cria o pico na utilização da CPU na inicialização</span><span class="sxs-lookup"><span data-stu-id="11784-140">powershell.exe creates spike in CPU usage on startup</span></span>

<span data-ttu-id="11784-141">PowerShell utiliza uma consulta WMI para verificar se ele foi iniciado por meio da diretiva de grupo para evitar que faz com que o atraso no início de sessão.</span><span class="sxs-lookup"><span data-stu-id="11784-141">PowerShell uses a WMI query to check if it was started via Group Policy to avoid causing delay in login.</span></span> <span data-ttu-id="11784-142">A consulta de WMI acaba injetar tzres.mui.dll cada processo no sistema desde o WMI **Win32_Process** classe tenta recuperar informações de fuso horário local.</span><span class="sxs-lookup"><span data-stu-id="11784-142">The WMI query ends up injecting tzres.mui.dll into every process on the system since the WMI **Win32_Process** class attempts to retrieve local timezone information.</span></span> <span data-ttu-id="11784-143">Isso resulta num grande pico de CPU nas **wmiprvse** (o anfitrião do fornecedor WMI).</span><span class="sxs-lookup"><span data-stu-id="11784-143">This results in a large CPU spike in **wmiprvse** (the WMI provider host).</span></span> <span data-ttu-id="11784-144">Correção é usar chamadas de API do Win32 para obter as mesmas informações em vez de usar o WMI.</span><span class="sxs-lookup"><span data-stu-id="11784-144">Fix is to use Win32 API calls to get the same information instead of using WMI.</span></span>
