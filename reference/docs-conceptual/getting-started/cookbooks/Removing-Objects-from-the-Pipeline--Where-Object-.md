---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Remover objetos a partir do Pipeline onde-objeto
ms.assetid: 01df8b22-2d22-4e2c-a18d-c004cd3cc284
ms.openlocfilehash: 2d89defdb1b234a9d0021fc06e1f05a95bb1bce9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="removing-objects-from-the-pipeline-where-object"></a><span data-ttu-id="249d8-103">Remover objetos a partir do Pipeline (onde-objeto)</span><span class="sxs-lookup"><span data-stu-id="249d8-103">Removing Objects from the Pipeline (Where-Object)</span></span>

<span data-ttu-id="249d8-104">No Windows PowerShell, muitas vezes gerar e transferem mais objetos para um pipeline que quiser.</span><span class="sxs-lookup"><span data-stu-id="249d8-104">In Windows PowerShell, you often generate and pass along more objects to a pipeline than you want.</span></span> <span data-ttu-id="249d8-105">Pode especificar as propriedades de objetos específicos para apresentar, utilizando o **formato** cmdlets, mas isto não ajuda com o problema de remover objetos de todos a partir do ecrã.</span><span class="sxs-lookup"><span data-stu-id="249d8-105">You can specify the properties of particular objects to display by using the **Format** cmdlets, but this does not help with the problem of removing entire objects from the display.</span></span> <span data-ttu-id="249d8-106">Poderá filtrar objetos antes do fim de um pipeline, pelo que pode realizar ações em apenas um subconjunto dos objetos gerou inicialmente.</span><span class="sxs-lookup"><span data-stu-id="249d8-106">You may want to filter objects before the end of a pipeline, so you can perform actions on only a subset of the initially-generated objects.</span></span>

<span data-ttu-id="249d8-107">O Windows PowerShell inclui um **Where-Object** cmdlet permite-lhe testar cada objeto no pipeline e transmita-apenas pelo pipeline se cumpre uma condição de teste específica.</span><span class="sxs-lookup"><span data-stu-id="249d8-107">Windows PowerShell includes a **Where-Object** cmdlet that allows you to test each object in the pipeline and only pass it along the pipeline if it meets a particular test condition.</span></span> <span data-ttu-id="249d8-108">Objetos que não são transmitidas o teste são removidos a partir do pipeline.</span><span class="sxs-lookup"><span data-stu-id="249d8-108">Objects that do not pass the test are removed from the pipeline.</span></span> <span data-ttu-id="249d8-109">Forneça a condição de teste como o valor de **onde ObjectFilterScript** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="249d8-109">You supply the test condition as the value of the **Where-ObjectFilterScript** parameter.</span></span>

### <a name="performing-simple-tests-with-where-object"></a><span data-ttu-id="249d8-110">Efetuar testes simples com Where-Object</span><span class="sxs-lookup"><span data-stu-id="249d8-110">Performing Simple Tests with Where-Object</span></span>

<span data-ttu-id="249d8-111">O valor de **FilterScript** é um *bloco de script* - um ou mais comandos do Windows PowerShell rodeados por chavetas {-} - que avalia como VERDADEIRO ou FALSO.</span><span class="sxs-lookup"><span data-stu-id="249d8-111">The value of **FilterScript** is a *script block* -  one or more Windows PowerShell commands surrounded by braces {} - that evaluates to true or false.</span></span> <span data-ttu-id="249d8-112">Estes blocos de script podem ser muito simples, mas a criação de-los requer saber sobre outro conceito de Windows PowerShell, operadores de comparação.</span><span class="sxs-lookup"><span data-stu-id="249d8-112">These script blocks can be very simple, but creating them requires knowing about another Windows PowerShell concept, comparison operators.</span></span> <span data-ttu-id="249d8-113">Um operador de comparação compara os itens que são apresentados em cada lado do mesmo.</span><span class="sxs-lookup"><span data-stu-id="249d8-113">A comparison operator compares the items that appear on each side of it.</span></span> <span data-ttu-id="249d8-114">Operadores de comparação de começar com um '-' caráter e seguido de um nome.</span><span class="sxs-lookup"><span data-stu-id="249d8-114">Comparison operators begin with a '-' character and are followed by a name.</span></span> <span data-ttu-id="249d8-115">Operadores de comparação básica funcionam em praticamente qualquer tipo de objeto.</span><span class="sxs-lookup"><span data-stu-id="249d8-115">Basic comparison operators work on almost any kind of object.</span></span> <span data-ttu-id="249d8-116">Os operadores de comparação mais avançados só poderão funcionar em texto ou de matrizes.</span><span class="sxs-lookup"><span data-stu-id="249d8-116">The more advanced comparison operators might only work on text or arrays.</span></span>

> [!NOTE]
> <span data-ttu-id="249d8-117">Por predefinição, quando trabalhar com o texto, operadores de comparação do Windows PowerShell são sensível.</span><span class="sxs-lookup"><span data-stu-id="249d8-117">By default, when working with text, Windows PowerShell comparison operators are case-insensitive.</span></span>

<span data-ttu-id="249d8-118">Devido a considerações de análise, símbolos, tais como <>, e = não são utilizadas como operadores de comparação.</span><span class="sxs-lookup"><span data-stu-id="249d8-118">Due to parsing considerations, symbols such as <,>, and = are not used as comparison operators.</span></span> <span data-ttu-id="249d8-119">Em vez disso, operadores de comparação são compostos por letras.</span><span class="sxs-lookup"><span data-stu-id="249d8-119">Instead, comparison operators are comprised of letters.</span></span> <span data-ttu-id="249d8-120">Os operadores de comparação básica estão listados na seguinte tabela.</span><span class="sxs-lookup"><span data-stu-id="249d8-120">The basic comparison operators are listed in the following table.</span></span>

|<span data-ttu-id="249d8-121">Operador de comparação</span><span class="sxs-lookup"><span data-stu-id="249d8-121">Comparison Operator</span></span>|<span data-ttu-id="249d8-122">Significado</span><span class="sxs-lookup"><span data-stu-id="249d8-122">Meaning</span></span>|<span data-ttu-id="249d8-123">Exemplo (devolve true)</span><span class="sxs-lookup"><span data-stu-id="249d8-123">Example (returns true)</span></span>|
|-----------------------|-----------|--------------------------|
|<span data-ttu-id="249d8-124">-eq</span><span class="sxs-lookup"><span data-stu-id="249d8-124">-eq</span></span>|<span data-ttu-id="249d8-125">é igual a</span><span class="sxs-lookup"><span data-stu-id="249d8-125">is equal to</span></span>|<span data-ttu-id="249d8-126">1 -eq 1</span><span class="sxs-lookup"><span data-stu-id="249d8-126">1 -eq 1</span></span>|
|<span data-ttu-id="249d8-127">-ne</span><span class="sxs-lookup"><span data-stu-id="249d8-127">-ne</span></span>|<span data-ttu-id="249d8-128">Não é igual a</span><span class="sxs-lookup"><span data-stu-id="249d8-128">Is not equal to</span></span>|<span data-ttu-id="249d8-129">1 - ne 2</span><span class="sxs-lookup"><span data-stu-id="249d8-129">1 -ne 2</span></span>|
|<span data-ttu-id="249d8-130">-lt</span><span class="sxs-lookup"><span data-stu-id="249d8-130">-lt</span></span>|<span data-ttu-id="249d8-131">É inferior a</span><span class="sxs-lookup"><span data-stu-id="249d8-131">Is less than</span></span>|<span data-ttu-id="249d8-132">1 -lt 2</span><span class="sxs-lookup"><span data-stu-id="249d8-132">1 -lt 2</span></span>|
|<span data-ttu-id="249d8-133">-le</span><span class="sxs-lookup"><span data-stu-id="249d8-133">-le</span></span>|<span data-ttu-id="249d8-134">é menor ou igual a</span><span class="sxs-lookup"><span data-stu-id="249d8-134">Is less than or equal to</span></span>|<span data-ttu-id="249d8-135">1 - le 2</span><span class="sxs-lookup"><span data-stu-id="249d8-135">1 -le 2</span></span>|
|<span data-ttu-id="249d8-136">-gt</span><span class="sxs-lookup"><span data-stu-id="249d8-136">-gt</span></span>|<span data-ttu-id="249d8-137">É maior do que</span><span class="sxs-lookup"><span data-stu-id="249d8-137">Is greater than</span></span>|<span data-ttu-id="249d8-138">2 -gt 1</span><span class="sxs-lookup"><span data-stu-id="249d8-138">2 -gt 1</span></span>|
|<span data-ttu-id="249d8-139">-ge</span><span class="sxs-lookup"><span data-stu-id="249d8-139">-ge</span></span>|<span data-ttu-id="249d8-140">é maior que ou igual a</span><span class="sxs-lookup"><span data-stu-id="249d8-140">Is greater than or equal to</span></span>|<span data-ttu-id="249d8-141">2 -ge 1</span><span class="sxs-lookup"><span data-stu-id="249d8-141">2 -ge 1</span></span>|
|<span data-ttu-id="249d8-142">-como</span><span class="sxs-lookup"><span data-stu-id="249d8-142">-like</span></span>|<span data-ttu-id="249d8-143">É semelhante (comparação de caráter universal para texto)</span><span class="sxs-lookup"><span data-stu-id="249d8-143">Is like (wildcard comparison for text)</span></span>|<span data-ttu-id="249d8-144">"file.doc"-como "f\*.do?"</span><span class="sxs-lookup"><span data-stu-id="249d8-144">"file.doc" -like "f\*.do?"</span></span>|
|<span data-ttu-id="249d8-145">-notlike</span><span class="sxs-lookup"><span data-stu-id="249d8-145">-notlike</span></span>|<span data-ttu-id="249d8-146">Não é como (comparação de caráter universal para texto)</span><span class="sxs-lookup"><span data-stu-id="249d8-146">Is not like (wildcard comparison for text)</span></span>|<span data-ttu-id="249d8-147">"file.doc"-notlike "p\*. doc"</span><span class="sxs-lookup"><span data-stu-id="249d8-147">"file.doc" -notlike "p\*.doc"</span></span>|
|<span data-ttu-id="249d8-148">-contém</span><span class="sxs-lookup"><span data-stu-id="249d8-148">-contains</span></span>|<span data-ttu-id="249d8-149">contém</span><span class="sxs-lookup"><span data-stu-id="249d8-149">Contains</span></span>|<span data-ttu-id="249d8-150">1,2,3 - contém 1</span><span class="sxs-lookup"><span data-stu-id="249d8-150">1,2,3 -contains 1</span></span>|
|<span data-ttu-id="249d8-151">-notcontains</span><span class="sxs-lookup"><span data-stu-id="249d8-151">-notcontains</span></span>|<span data-ttu-id="249d8-152">não contém</span><span class="sxs-lookup"><span data-stu-id="249d8-152">Does not contain</span></span>|<span data-ttu-id="249d8-153">1,2,3 - notcontains 4</span><span class="sxs-lookup"><span data-stu-id="249d8-153">1,2,3 -notcontains 4</span></span>|

<span data-ttu-id="249d8-154">Blocos de script WHERE-Object utilizam a variável especial '$_' referir-se para o objeto atual no pipeline.</span><span class="sxs-lookup"><span data-stu-id="249d8-154">Where-Object script blocks use the special variable '$_' to refer to the current object in the pipeline.</span></span> <span data-ttu-id="249d8-155">Eis um exemplo de como funciona.</span><span class="sxs-lookup"><span data-stu-id="249d8-155">Here is an example of how it works.</span></span> <span data-ttu-id="249d8-156">Se tiver uma lista de números e apenas pretende devolver aqueles que são inferior a 3, pode utilizar Where-Object para filtrar os números, escrevendo:</span><span class="sxs-lookup"><span data-stu-id="249d8-156">If you have a list of numbers, and only want to return the ones that are less than 3, you can use Where-Object to filter the numbers by typing:</span></span>

```
PS> 1,2,3,4 | Where-Object -FilterScript {$_ -lt 3}
1
2
```

### <a name="filtering-based-on-object-properties"></a><span data-ttu-id="249d8-157">Filtragem baseada nas propriedades do objeto</span><span class="sxs-lookup"><span data-stu-id="249d8-157">Filtering Based on Object Properties</span></span>

<span data-ttu-id="249d8-158">Uma vez que $_ refere-se para o objeto de pipeline atual, mas pode aceder a respetivas propriedades para o nossos testes.</span><span class="sxs-lookup"><span data-stu-id="249d8-158">Since $_ refers to the current pipeline object, we can access its properties for our tests.</span></span>

<span data-ttu-id="249d8-159">Por exemplo, vamos pode ver a classe de Win32_SystemDriver no WMI.</span><span class="sxs-lookup"><span data-stu-id="249d8-159">As an example, we can look at the Win32_SystemDriver class in WMI.</span></span> <span data-ttu-id="249d8-160">Podem existir centenas de controladores do sistema num sistema específico, mas só poderá estar interessado num conjunto específico dos controladores do sistema, tais como as que estão atualmente em execução.</span><span class="sxs-lookup"><span data-stu-id="249d8-160">There might be hundreds of system drivers on a particular system, but you might only be interested in a particular set of the system drivers, such as those which are currently running.</span></span> <span data-ttu-id="249d8-161">Se utilizar o Get-membro para ver os membros de Win32_SystemDriver (**Get-WmiObject-classe Win32_SystemDriver | Get-Member - MemberType propriedade**), verá que a propriedade relevante está no Estado e de que tem um valor de "Em execução" quando o controlador está em execução.</span><span class="sxs-lookup"><span data-stu-id="249d8-161">If you use Get-Member to view Win32_SystemDriver members (**Get-WmiObject -Class Win32_SystemDriver | Get-Member -MemberType Property**) you will see that the relevant property is State, and that it has a value of "Running" when the driver is running.</span></span> <span data-ttu-id="249d8-162">Pode filtrar os controladores do sistema, selecionar apenas aqueles em execução, escrevendo:</span><span class="sxs-lookup"><span data-stu-id="249d8-162">You can filter the system drivers, selecting only the running ones by typing:</span></span>

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq 'Running'}
```

<span data-ttu-id="249d8-163">Isto ainda produz uma longa lista.</span><span class="sxs-lookup"><span data-stu-id="249d8-163">This still produces a long list.</span></span> <span data-ttu-id="249d8-164">Pode querer de filtro para selecionar apenas os controladores definidos para iniciar automaticamente ao testar o valor de StartMode, bem como:</span><span class="sxs-lookup"><span data-stu-id="249d8-164">You may want to filter to only select the drivers set to start automatically by testing the StartMode value as well:</span></span>

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

<span data-ttu-id="249d8-165">Isto dá-numa grande quantidade de informações que já não é necessário porque Sabemos que os controladores estão em execução.</span><span class="sxs-lookup"><span data-stu-id="249d8-165">This gives us a lot of information we no longer need because we know that the drivers are running.</span></span> <span data-ttu-id="249d8-166">Na verdade, as únicas informações provavelmente precisamos neste momento são o nome e o nome a apresentar.</span><span class="sxs-lookup"><span data-stu-id="249d8-166">In fact, the only information we probably need at this point are the name and the display name.</span></span> <span data-ttu-id="249d8-167">O seguinte comando inclui apenas essas duas propriedades, resultando na saída muito mais simples:</span><span class="sxs-lookup"><span data-stu-id="249d8-167">The following command includes only those two properties, resulting in much simpler output:</span></span>

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

<span data-ttu-id="249d8-168">Existem dois elementos Where-Object no comando acima, mas podem ser expressas num único elemento Where-Object utilizando- e um operador lógico, como esta:</span><span class="sxs-lookup"><span data-stu-id="249d8-168">There are two Where-Object elements in the above command, but they can be expressed in a single Where-Object element by using the -and logical operator, like this:</span></span>

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript { ($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual') } | Format-Table -Property Name,DisplayName
```

<span data-ttu-id="249d8-169">Os padrão operadores lógicos estão listados na seguinte tabela.</span><span class="sxs-lookup"><span data-stu-id="249d8-169">The standard logical operators are listed in the following table.</span></span>

|<span data-ttu-id="249d8-170">Operador lógico</span><span class="sxs-lookup"><span data-stu-id="249d8-170">Logical Operator</span></span>|<span data-ttu-id="249d8-171">Significado</span><span class="sxs-lookup"><span data-stu-id="249d8-171">Meaning</span></span>|<span data-ttu-id="249d8-172">Exemplo (devolve true)</span><span class="sxs-lookup"><span data-stu-id="249d8-172">Example (returns true)</span></span>|
|--------------------|-----------|--------------------------|
|<span data-ttu-id="249d8-173">- e</span><span class="sxs-lookup"><span data-stu-id="249d8-173">-and</span></span>|<span data-ttu-id="249d8-174">Lógica e; TRUE se ambos os lados forem verdadeiros</span><span class="sxs-lookup"><span data-stu-id="249d8-174">Logical and; true if both sides are true</span></span>|<span data-ttu-id="249d8-175">(1 -eq 1) -and (2 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="249d8-175">(1 -eq 1) -and (2 -eq 2)</span></span>|
|<span data-ttu-id="249d8-176">- ou</span><span class="sxs-lookup"><span data-stu-id="249d8-176">-or</span></span>|<span data-ttu-id="249d8-177">Lógico ou; TRUE se ambos os lados for VERDADEIRO</span><span class="sxs-lookup"><span data-stu-id="249d8-177">Logical or; true if either side is true</span></span>|<span data-ttu-id="249d8-178">(1 - eq 1) - ou (1 - eq 2).</span><span class="sxs-lookup"><span data-stu-id="249d8-178">(1 -eq 1) -or (1 -eq 2)</span></span>|
|<span data-ttu-id="249d8-179">-não</span><span class="sxs-lookup"><span data-stu-id="249d8-179">-not</span></span>|<span data-ttu-id="249d8-180">Não lógico; Inverte true e false</span><span class="sxs-lookup"><span data-stu-id="249d8-180">Logical not; reverses true and false</span></span>|<span data-ttu-id="249d8-181">-não (1 - eq 2)</span><span class="sxs-lookup"><span data-stu-id="249d8-181">-not (1 -eq 2)</span></span>|
|\!|<span data-ttu-id="249d8-182">Não lógico; Inverte true e false</span><span class="sxs-lookup"><span data-stu-id="249d8-182">Logical not; reverses true and false</span></span>|<span data-ttu-id="249d8-183">\!(1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="249d8-183">\!(1 -eq 2)</span></span>|