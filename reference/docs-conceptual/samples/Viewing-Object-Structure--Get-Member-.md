---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Membro do Get de estrutura de objeto de visualização
ms.assetid: a1819ed2-2ef3-453a-b2b0-f3589c550481
ms.openlocfilehash: cc93e45e4306b3d623c1d3d1096dd20c1afc59c8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058850"
---
# <a name="viewing-object-structure-get-member"></a><span data-ttu-id="d2026-103">Ver a estrutura de objetos (Get-Member)</span><span class="sxs-lookup"><span data-stu-id="d2026-103">Viewing Object Structure (Get-Member)</span></span>

<span data-ttu-id="d2026-104">Porque objetos desempenham um papel central no Windows PowerShell, há vários comandos nativos concebidos para trabalhar com tipos de objetos arbitrários.</span><span class="sxs-lookup"><span data-stu-id="d2026-104">Because objects play such a central role in Windows PowerShell, there are several native commands designed to work with arbitrary object types.</span></span> <span data-ttu-id="d2026-105">O mais importante é o **Get-Member** comando.</span><span class="sxs-lookup"><span data-stu-id="d2026-105">The most important one is the **Get-Member** command.</span></span>

<span data-ttu-id="d2026-106">A técnica mais simples para analisar os objetos que retorna um comando é encaminhar a saída do comando para o **Get-Member** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d2026-106">The simplest technique for analyzing the objects that a command returns is to pipe the output of that command to the **Get-Member** cmdlet.</span></span> <span data-ttu-id="d2026-107">O **Get-Member** cmdlet mostra-lhe o nome formal do tipo de objeto e uma lista completa dos seus membros.</span><span class="sxs-lookup"><span data-stu-id="d2026-107">The **Get-Member** cmdlet shows you the formal name of the object type and a complete listing of its members.</span></span> <span data-ttu-id="d2026-108">O número de elementos que são devolvidos às vezes, pode ser absurdo.</span><span class="sxs-lookup"><span data-stu-id="d2026-108">The number of elements that are returned can sometimes be overwhelming.</span></span> <span data-ttu-id="d2026-109">Por exemplo, um objeto de processo pode ter mais de 100 membros.</span><span class="sxs-lookup"><span data-stu-id="d2026-109">For example, a process object can have over 100 members.</span></span>

<span data-ttu-id="d2026-110">Para ver todos os membros de um objeto de processo e a saída de página, para que pode ver todos os-lo, escreva:</span><span class="sxs-lookup"><span data-stu-id="d2026-110">To see all the members of a Process object and page the output so you can view all of it, type:</span></span>

```powershell
Get-Process | Get-Member | Out-Host -Paging
```

<span data-ttu-id="d2026-111">O resultado deste comando será algo parecido com isto:</span><span class="sxs-lookup"><span data-stu-id="d2026-111">The output from this command will look something like this:</span></span>

```output
TypeName: System.Diagnostics.Process

Name                           MemberType     Definition
----                           ----------     ----------
Handles                        AliasProperty  Handles = Handlecount
Name                           AliasProperty  Name = ProcessName
NPM                            AliasProperty  NPM = NonpagedSystemMemorySize
PM                             AliasProperty  PM = PagedMemorySize
VM                             AliasProperty  VM = VirtualMemorySize
WS                             AliasProperty  WS = WorkingSet
add_Disposed                   Method         System.Void add_Disposed(Event...
...
```

<span data-ttu-id="d2026-112">Podemos fazer essa longa lista de informações mais utilizável ao filtrar para elementos que queremos ver.</span><span class="sxs-lookup"><span data-stu-id="d2026-112">We can make this long list of information more usable by filtering for elements we want to see.</span></span> <span data-ttu-id="d2026-113">O **Get-Member** comando permite que listar apenas os membros que são propriedades.</span><span class="sxs-lookup"><span data-stu-id="d2026-113">The **Get-Member** command lets you list only members that are properties.</span></span> <span data-ttu-id="d2026-114">Existem várias formas de propriedades.</span><span class="sxs-lookup"><span data-stu-id="d2026-114">There are several forms of properties.</span></span> <span data-ttu-id="d2026-115">O cmdlet apresenta as propriedades de qualquer tipo, se definirmos os **Get-Member MemberType** parâmetro para o valor **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="d2026-115">The cmdlet displays properties of any type if we set the **Get-Member MemberType** parameter to the value **Properties**.</span></span> <span data-ttu-id="d2026-116">A lista resultante ainda é muito longo, mas um pouco mais fáceis de gerir:</span><span class="sxs-lookup"><span data-stu-id="d2026-116">The resulting list is still very long, but a bit more manageable:</span></span>

```
PS> Get-Process | Get-Member -MemberType Properties

   TypeName: System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Handles                    AliasProperty  Handles = Handlecount
Name                       AliasProperty  Name = ProcessName
...
ExitCode                   Property       System.Int32 ExitCode {get;}
...
Handle                     Property       System.IntPtr Handle {get;}
...
CPU                        ScriptProperty System.Object CPU {get=$this.Total...
...
Path                       ScriptProperty System.Object Path {get=$this.Main...
...
```

> [!NOTE]
> <span data-ttu-id="d2026-117">Os valores permitidos de MemberType pedidos são AliasProperty, CodeProperty, propriedade, NoteProperty, ScriptProperty, propriedades, PropertySet, método, CodeMethod, ScriptMethod, métodos, ParameterizedProperty, MemberSet e tudo.</span><span class="sxs-lookup"><span data-stu-id="d2026-117">The allowed values of MemberType are AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, and All.</span></span>

<span data-ttu-id="d2026-118">Existem mais de 60 propriedades para um processo.</span><span class="sxs-lookup"><span data-stu-id="d2026-118">There are over 60 properties for a process.</span></span> <span data-ttu-id="d2026-119">O motivo pelo qual que Windows PowerShell, muitas vezes, mostra que apenas algumas poucas propriedades para qualquer objeto conhecido é que mostrando todos eles produziria uma impossível de gerenciar quantidade de informações.</span><span class="sxs-lookup"><span data-stu-id="d2026-119">The reason Windows PowerShell often shows only a handful of properties for any well-known object is that showing all of them would produce an unmanageable amount of information.</span></span>

> [!NOTE]
> <span data-ttu-id="d2026-120">Windows PowerShell determina como exibir um tipo de objeto ao utilizar as informações armazenadas em arquivos XML que têm nomes que terminem em. format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="d2026-120">Windows PowerShell determines how to display an object type by using information stored in XML files that have names ending in .format.ps1xml.</span></span> <span data-ttu-id="d2026-121">Os dados de formatação para objetos de processo, o que são objetos .NET Diagnostics, são armazenados no DotNetTypes.format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="d2026-121">The formatting data for process objects, which are .NET System.Diagnostics.Process objects, is stored in DotNetTypes.format.ps1xml.</span></span>

<span data-ttu-id="d2026-122">Se precisar de ver propriedades além das que o Windows PowerShell apresenta por predefinição, terá de formatar os dados de saída por conta própria.</span><span class="sxs-lookup"><span data-stu-id="d2026-122">If you need to look at properties other than those that Windows PowerShell displays by default, you will need to format the output data yourself.</span></span> <span data-ttu-id="d2026-123">Isso pode ser feito utilizando os cmdlets de formato.</span><span class="sxs-lookup"><span data-stu-id="d2026-123">This can be done by using the format cmdlets.</span></span>