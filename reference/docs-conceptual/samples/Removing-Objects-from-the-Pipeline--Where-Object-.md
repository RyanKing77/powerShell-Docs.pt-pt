---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Remover objetos do Pipeline Where-Object
ms.openlocfilehash: c47efd38e2ff40ce3b7bf50b161cc38de922c5da
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030878"
---
# <a name="removing-objects-from-the-pipeline-where-object"></a><span data-ttu-id="4ac22-103">Remover objetos do Pipeline (Where-Object)</span><span class="sxs-lookup"><span data-stu-id="4ac22-103">Removing Objects from the Pipeline (Where-Object)</span></span>

<span data-ttu-id="4ac22-104">No Windows PowerShell, muitas vezes, gerar e passar mais objetos para um pipeline que desejar.</span><span class="sxs-lookup"><span data-stu-id="4ac22-104">In Windows PowerShell, you often generate and pass along more objects to a pipeline than you want.</span></span> <span data-ttu-id="4ac22-105">Pode especificar as propriedades dos objetos específicos para apresentar ao utilizar o **formato** cmdlets, mas isso não ajuda com o problema da remoção de objetos inteiros na exibição.</span><span class="sxs-lookup"><span data-stu-id="4ac22-105">You can specify the properties of particular objects to display by using the **Format** cmdlets, but this does not help with the problem of removing entire objects from the display.</span></span> <span data-ttu-id="4ac22-106">Pode querer filtrar objetos antes do final de um pipeline, pelo que pode executar ações em apenas um subconjunto dos objetos gerou inicialmente.</span><span class="sxs-lookup"><span data-stu-id="4ac22-106">You may want to filter objects before the end of a pipeline, so you can perform actions on only a subset of the initially-generated objects.</span></span>

<span data-ttu-id="4ac22-107">Windows PowerShell inclui um `Where-Object` cmdlet permite-lhe testar cada objeto no pipeline e apenas passá-lo ao longo do pipeline se ele cumpre uma condição de teste específico.</span><span class="sxs-lookup"><span data-stu-id="4ac22-107">Windows PowerShell includes a `Where-Object` cmdlet that allows you to test each object in the pipeline and only pass it along the pipeline if it meets a particular test condition.</span></span> <span data-ttu-id="4ac22-108">Objetos que não passar no teste são removidos do pipeline.</span><span class="sxs-lookup"><span data-stu-id="4ac22-108">Objects that do not pass the test are removed from the pipeline.</span></span> <span data-ttu-id="4ac22-109">Fornecer a condição de teste como o valor do `Where-Object` **FilterScript** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4ac22-109">You supply the test condition as the value of the `Where-Object` **FilterScript** parameter.</span></span>

## <a name="performing-simple-tests-with-where-object"></a><span data-ttu-id="4ac22-110">Executar testes simples com Where-Object</span><span class="sxs-lookup"><span data-stu-id="4ac22-110">Performing Simple Tests with Where-Object</span></span>

<span data-ttu-id="4ac22-111">O valor de **FilterScript** é um *bloco de script* -uma ou mais comandos do Windows PowerShell rodeados por chavetas {} -que é avaliada como verdadeira ou falsa.</span><span class="sxs-lookup"><span data-stu-id="4ac22-111">The value of **FilterScript** is a *script block* -  one or more Windows PowerShell commands surrounded by braces {} - that evaluates to true or false.</span></span> <span data-ttu-id="4ac22-112">Esses blocos de script podem ser muito simples, mas criá-las, precisa conhecer sobre outro conceito do Windows PowerShell, operadores de comparação.</span><span class="sxs-lookup"><span data-stu-id="4ac22-112">These script blocks can be very simple, but creating them requires knowing about another Windows PowerShell concept, comparison operators.</span></span> <span data-ttu-id="4ac22-113">Um operador de comparação compara os itens que aparecem em cada lado dele.</span><span class="sxs-lookup"><span data-stu-id="4ac22-113">A comparison operator compares the items that appear on each side of it.</span></span> <span data-ttu-id="4ac22-114">Operadores de comparação de começar com um "-" caráter e são seguidas por um nome.</span><span class="sxs-lookup"><span data-stu-id="4ac22-114">Comparison operators begin with a '-' character and are followed by a name.</span></span> <span data-ttu-id="4ac22-115">Operadores de comparação básicos funcionam em praticamente qualquer tipo de objeto.</span><span class="sxs-lookup"><span data-stu-id="4ac22-115">Basic comparison operators work on almost any kind of object.</span></span> <span data-ttu-id="4ac22-116">Os operadores de comparação mais avançados poderão funciona somente em texto ou matrizes.</span><span class="sxs-lookup"><span data-stu-id="4ac22-116">The more advanced comparison operators might only work on text or arrays.</span></span>

> [!NOTE]
> <span data-ttu-id="4ac22-117">Por predefinição, ao trabalhar com texto, os operadores de comparação do Windows PowerShell diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="4ac22-117">By default, when working with text, Windows PowerShell comparison operators are case-insensitive.</span></span>

<span data-ttu-id="4ac22-118">Devido a considerações de análise, símbolos, como <>, e = não são usados como operadores de comparação.</span><span class="sxs-lookup"><span data-stu-id="4ac22-118">Due to parsing considerations, symbols such as <,>, and = are not used as comparison operators.</span></span> <span data-ttu-id="4ac22-119">Em vez disso, operadores de comparação são constituídos por letras.</span><span class="sxs-lookup"><span data-stu-id="4ac22-119">Instead, comparison operators are comprised of letters.</span></span> <span data-ttu-id="4ac22-120">Os operadores de comparação básicas estão listados na tabela seguinte.</span><span class="sxs-lookup"><span data-stu-id="4ac22-120">The basic comparison operators are listed in the following table.</span></span>

|<span data-ttu-id="4ac22-121">Operador de comparação</span><span class="sxs-lookup"><span data-stu-id="4ac22-121">Comparison Operator</span></span>|<span data-ttu-id="4ac22-122">Significado</span><span class="sxs-lookup"><span data-stu-id="4ac22-122">Meaning</span></span>|<span data-ttu-id="4ac22-123">Exemplo (retorna verdadeiro)</span><span class="sxs-lookup"><span data-stu-id="4ac22-123">Example (returns true)</span></span>|
|-----------------------|-----------|--------------------------|
|<span data-ttu-id="4ac22-124">-eq</span><span class="sxs-lookup"><span data-stu-id="4ac22-124">-eq</span></span>|<span data-ttu-id="4ac22-125">é igual a</span><span class="sxs-lookup"><span data-stu-id="4ac22-125">is equal to</span></span>|<span data-ttu-id="4ac22-126">1 -eq 1</span><span class="sxs-lookup"><span data-stu-id="4ac22-126">1 -eq 1</span></span>|
|<span data-ttu-id="4ac22-127">-ne</span><span class="sxs-lookup"><span data-stu-id="4ac22-127">-ne</span></span>|<span data-ttu-id="4ac22-128">Não é igual a</span><span class="sxs-lookup"><span data-stu-id="4ac22-128">Is not equal to</span></span>|<span data-ttu-id="4ac22-129">1 - ne 2</span><span class="sxs-lookup"><span data-stu-id="4ac22-129">1 -ne 2</span></span>|
|<span data-ttu-id="4ac22-130">-lt</span><span class="sxs-lookup"><span data-stu-id="4ac22-130">-lt</span></span>|<span data-ttu-id="4ac22-131">É inferior a</span><span class="sxs-lookup"><span data-stu-id="4ac22-131">Is less than</span></span>|<span data-ttu-id="4ac22-132">1 -lt 2</span><span class="sxs-lookup"><span data-stu-id="4ac22-132">1 -lt 2</span></span>|
|<span data-ttu-id="4ac22-133">-le</span><span class="sxs-lookup"><span data-stu-id="4ac22-133">-le</span></span>|<span data-ttu-id="4ac22-134">é menor ou igual a</span><span class="sxs-lookup"><span data-stu-id="4ac22-134">Is less than or equal to</span></span>|<span data-ttu-id="4ac22-135">1 - le 2</span><span class="sxs-lookup"><span data-stu-id="4ac22-135">1 -le 2</span></span>|
|<span data-ttu-id="4ac22-136">-gt</span><span class="sxs-lookup"><span data-stu-id="4ac22-136">-gt</span></span>|<span data-ttu-id="4ac22-137">É maior do que</span><span class="sxs-lookup"><span data-stu-id="4ac22-137">Is greater than</span></span>|<span data-ttu-id="4ac22-138">2 -gt 1</span><span class="sxs-lookup"><span data-stu-id="4ac22-138">2 -gt 1</span></span>|
|<span data-ttu-id="4ac22-139">-ge</span><span class="sxs-lookup"><span data-stu-id="4ac22-139">-ge</span></span>|<span data-ttu-id="4ac22-140">é maior que ou igual a</span><span class="sxs-lookup"><span data-stu-id="4ac22-140">Is greater than or equal to</span></span>|<span data-ttu-id="4ac22-141">2 -ge 1</span><span class="sxs-lookup"><span data-stu-id="4ac22-141">2 -ge 1</span></span>|
|<span data-ttu-id="4ac22-142">-como</span><span class="sxs-lookup"><span data-stu-id="4ac22-142">-like</span></span>|<span data-ttu-id="4ac22-143">É como (comparação de caráter universal para texto)</span><span class="sxs-lookup"><span data-stu-id="4ac22-143">Is like (wildcard comparison for text)</span></span>|<span data-ttu-id="4ac22-144">"file.doc" -like "f\*.do?"</span><span class="sxs-lookup"><span data-stu-id="4ac22-144">"file.doc" -like "f\*.do?"</span></span>|
|<span data-ttu-id="4ac22-145">-notlike</span><span class="sxs-lookup"><span data-stu-id="4ac22-145">-notlike</span></span>|<span data-ttu-id="4ac22-146">Não é como (comparação de caráter universal para texto)</span><span class="sxs-lookup"><span data-stu-id="4ac22-146">Is not like (wildcard comparison for text)</span></span>|<span data-ttu-id="4ac22-147">"file.doc" -notlike "p\*.doc"</span><span class="sxs-lookup"><span data-stu-id="4ac22-147">"file.doc" -notlike "p\*.doc"</span></span>|
|<span data-ttu-id="4ac22-148">-contains</span><span class="sxs-lookup"><span data-stu-id="4ac22-148">-contains</span></span>|<span data-ttu-id="4ac22-149">Contém</span><span class="sxs-lookup"><span data-stu-id="4ac22-149">Contains</span></span>|<span data-ttu-id="4ac22-150">1,2,3 -contains 1</span><span class="sxs-lookup"><span data-stu-id="4ac22-150">1,2,3 -contains 1</span></span>|
|<span data-ttu-id="4ac22-151">-notcontains</span><span class="sxs-lookup"><span data-stu-id="4ac22-151">-notcontains</span></span>|<span data-ttu-id="4ac22-152">Não contém</span><span class="sxs-lookup"><span data-stu-id="4ac22-152">Does not contain</span></span>|<span data-ttu-id="4ac22-153">1,2,3 - notcontains 4</span><span class="sxs-lookup"><span data-stu-id="4ac22-153">1,2,3 -notcontains 4</span></span>|

<span data-ttu-id="4ac22-154">Blocos de script WHERE-Object utilizam a variável especial `$_` para fazer referência ao objeto atual no pipeline.</span><span class="sxs-lookup"><span data-stu-id="4ac22-154">Where-Object script blocks use the special variable `$_` to refer to the current object in the pipeline.</span></span> <span data-ttu-id="4ac22-155">Eis um exemplo de como ele funciona.</span><span class="sxs-lookup"><span data-stu-id="4ac22-155">Here is an example of how it works.</span></span> <span data-ttu-id="4ac22-156">Se tiver uma lista de números e só quiser retornar os que são menos de 3, pode utilizar Where-Object para filtrar os números ao escrever:</span><span class="sxs-lookup"><span data-stu-id="4ac22-156">If you have a list of numbers, and only want to return the ones that are less than 3, you can use Where-Object to filter the numbers by typing:</span></span>

```
PS> 1,2,3,4 | Where-Object -FilterScript {$_ -lt 3}
1
2
```

## <a name="filtering-based-on-object-properties"></a><span data-ttu-id="4ac22-157">Filtragem com base nas propriedades do objeto</span><span class="sxs-lookup"><span data-stu-id="4ac22-157">Filtering Based on Object Properties</span></span>

<span data-ttu-id="4ac22-158">Uma vez que `$_` refere-se para o objeto de pipeline atual, pode aceder às respetivas propriedades para o nossos testes.</span><span class="sxs-lookup"><span data-stu-id="4ac22-158">Since `$_` refers to the current pipeline object, we can access its properties for our tests.</span></span>

<span data-ttu-id="4ac22-159">Por exemplo, podemos ver a classe Win32_SystemDriver no WMI.</span><span class="sxs-lookup"><span data-stu-id="4ac22-159">As an example, we can look at the Win32_SystemDriver class in WMI.</span></span> <span data-ttu-id="4ac22-160">Pode haver centenas de drivers de sistema num determinado sistema, mas só poderá estar interessado num determinado conjunto de drivers de sistema, como aqueles que estão atualmente em execução.</span><span class="sxs-lookup"><span data-stu-id="4ac22-160">There might be hundreds of system drivers on a particular system, but you might only be interested in a particular set of the system drivers, such as those which are currently running.</span></span> <span data-ttu-id="4ac22-161">Se usar Get-Member para ver os membros de Win32_SystemDriver (**Get-WmiObject-classe Win32_SystemDriver | Get-Member - MemberType propriedade**), verá que a propriedade relevante é o estado e que tem um valor de "Execução" quando o controlador está em execução.</span><span class="sxs-lookup"><span data-stu-id="4ac22-161">If you use Get-Member to view Win32_SystemDriver members (**Get-WmiObject -Class Win32_SystemDriver | Get-Member -MemberType Property**) you will see that the relevant property is State, and that it has a value of "Running" when the driver is running.</span></span> <span data-ttu-id="4ac22-162">Pode filtrar os controladores de sistema, selecionar apenas aqueles em execução digitando:</span><span class="sxs-lookup"><span data-stu-id="4ac22-162">You can filter the system drivers, selecting only the running ones by typing:</span></span>

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq 'Running'}
```

<span data-ttu-id="4ac22-163">Isso produz ainda uma longa lista.</span><span class="sxs-lookup"><span data-stu-id="4ac22-163">This still produces a long list.</span></span> <span data-ttu-id="4ac22-164">Pode querer filtrar para selecionar apenas os controladores definidos para iniciar automaticamente ao testar o valor de StartMode também:</span><span class="sxs-lookup"><span data-stu-id="4ac22-164">You may want to filter to only select the drivers set to start automatically by testing the StartMode value as well:</span></span>

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Auto"}

DisplayName : RAS Asynchronous Media Driver
Name        : AsyncMac
State       : Running
Status      : OK
Started     : True

DisplayName : Audio Stub Driver
Name        : audstub
State       : Running
Status      : OK
Started     : True
```

<span data-ttu-id="4ac22-165">Isso nos dá muitas informações que já não precisamos pois Sabemos que os controladores estão em execução.</span><span class="sxs-lookup"><span data-stu-id="4ac22-165">This gives us a lot of information we no longer need because we know that the drivers are running.</span></span> <span data-ttu-id="4ac22-166">Na verdade, a única informação que, provavelmente precisamos neste momento é o nome e o nome a apresentar.</span><span class="sxs-lookup"><span data-stu-id="4ac22-166">In fact, the only information we probably need at this point are the name and the display name.</span></span> <span data-ttu-id="4ac22-167">O seguinte comando inclui apenas essas duas propriedades, resultando muito mais simples de dados de saída:</span><span class="sxs-lookup"><span data-stu-id="4ac22-167">The following command includes only those two properties, resulting in much simpler output:</span></span>

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Manual"} | Format-Table -Property Name,DisplayName

Name                                    DisplayName
----                                    -----------
AsyncMac                                RAS Asynchronous Media Driver
Fdc                                     Floppy Disk Controller Driver
Flpydisk                                Floppy Disk Driver
Gpc                                     Generic Packet Classifier
IpNat                                   IP Network Address Translator
mouhid                                  Mouse HID Driver
MRxDAV                                  WebDav Client Redirector
mssmbios                                Microsoft System Management BIOS Driver
```

<span data-ttu-id="4ac22-168">Existem dois elementos de Where-Object no comando acima, mas podem ser expressas num único elemento de Where-Object, utilizando a opção - e o operador lógico, como este:</span><span class="sxs-lookup"><span data-stu-id="4ac22-168">There are two Where-Object elements in the above command, but they can be expressed in a single Where-Object element by using the -and logical operator, like this:</span></span>

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript { ($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual') } | Format-Table -Property Name,DisplayName
```

<span data-ttu-id="4ac22-169">Os operadores lógicos padrão estão listados na tabela seguinte.</span><span class="sxs-lookup"><span data-stu-id="4ac22-169">The standard logical operators are listed in the following table.</span></span>

|<span data-ttu-id="4ac22-170">Operador lógico</span><span class="sxs-lookup"><span data-stu-id="4ac22-170">Logical Operator</span></span>|<span data-ttu-id="4ac22-171">Significado</span><span class="sxs-lookup"><span data-stu-id="4ac22-171">Meaning</span></span>|<span data-ttu-id="4ac22-172">Exemplo (retorna verdadeiro)</span><span class="sxs-lookup"><span data-stu-id="4ac22-172">Example (returns true)</span></span>|
|--------------------|-----------|--------------------------|
|<span data-ttu-id="4ac22-173">- e</span><span class="sxs-lookup"><span data-stu-id="4ac22-173">-and</span></span>|<span data-ttu-id="4ac22-174">Lógica e; VERDADEIRO se ambos os lados forem verdadeiros</span><span class="sxs-lookup"><span data-stu-id="4ac22-174">Logical and; true if both sides are true</span></span>|<span data-ttu-id="4ac22-175">(1 - eq 1) - e (2 - eq 2).</span><span class="sxs-lookup"><span data-stu-id="4ac22-175">(1 -eq 1) -and (2 -eq 2)</span></span>|
|<span data-ttu-id="4ac22-176">- ou</span><span class="sxs-lookup"><span data-stu-id="4ac22-176">-or</span></span>|<span data-ttu-id="4ac22-177">Lógica ou; VERDADEIRO se ambos os lados for VERDADEIRO</span><span class="sxs-lookup"><span data-stu-id="4ac22-177">Logical or; true if either side is true</span></span>|<span data-ttu-id="4ac22-178">(1 -eq 1) -or (1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="4ac22-178">(1 -eq 1) -or (1 -eq 2)</span></span>|
|<span data-ttu-id="4ac22-179">-not</span><span class="sxs-lookup"><span data-stu-id="4ac22-179">-not</span></span>|<span data-ttu-id="4ac22-180">Não lógico; reverte true e false</span><span class="sxs-lookup"><span data-stu-id="4ac22-180">Logical not; reverses true and false</span></span>|<span data-ttu-id="4ac22-181">-not (1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="4ac22-181">-not (1 -eq 2)</span></span>|
|\!|<span data-ttu-id="4ac22-182">Não lógico; reverte true e false</span><span class="sxs-lookup"><span data-stu-id="4ac22-182">Logical not; reverses true and false</span></span>|<span data-ttu-id="4ac22-183">\!(1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="4ac22-183">\!(1 -eq 2)</span></span>|
