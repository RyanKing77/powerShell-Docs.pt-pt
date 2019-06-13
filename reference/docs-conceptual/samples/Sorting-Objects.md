---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Ordenar Objetos
ms.openlocfilehash: ed78e7e333f3468781c9cd96df2194fbdfebe753
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030782"
---
# <a name="sorting-objects"></a><span data-ttu-id="646ef-103">Ordenar Objetos</span><span class="sxs-lookup"><span data-stu-id="646ef-103">Sorting Objects</span></span>

<span data-ttu-id="646ef-104">Podemos pode organizar os dados exibidos para que seja mais fácil verificar utilizando o `Sort-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="646ef-104">We can organize displayed data to make it easier to scan by using the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="646ef-105">`Sort-Object` obtém o nome de uma ou mais propriedades a classificação e retorna dados ordenados por valores dessas propriedades.</span><span class="sxs-lookup"><span data-stu-id="646ef-105">`Sort-Object` takes the name of one or more properties to sort on, and returns data sorted by the values of those properties.</span></span>

## <a name="basic-sorting"></a><span data-ttu-id="646ef-106">A classificação básica</span><span class="sxs-lookup"><span data-stu-id="646ef-106">Basic sorting</span></span>

<span data-ttu-id="646ef-107">Considere o problema de listagem subdiretórios e arquivos no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="646ef-107">Consider the problem of listing subdirectories and files in the current directory.</span></span>
<span data-ttu-id="646ef-108">Se queremos ordenar por **LastWriteTime** e, em seguida, por **nome**, podemos fazer isso digitando:</span><span class="sxs-lookup"><span data-stu-id="646ef-108">If we want to sort by **LastWriteTime** and then by **Name**, we can do it by typing:</span></span>

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
11/6/2017 10:10:11 AM  .localization-config
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:15 AM  tests
6/6/2018 7:58:59 PM    CONTRIBUTING.md
6/6/2018 7:58:59 PM    README.md
...
```

<span data-ttu-id="646ef-109">Também pode ordenar os objetos na ordem inversa, especificando o **descendente** mudar o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="646ef-109">You can also sort the objects in reverse order by specifying the **Descending** switch parameter.</span></span>

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name -Descending |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  reference
12/1/2018 10:13:50 PM  dsc
...
6/6/2018 7:58:59 PM    README.md
6/6/2018 7:58:59 PM    CONTRIBUTING.md
11/6/2017 10:10:15 AM  tests
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  .localization-config
```

## <a name="using-hash-tables"></a><span data-ttu-id="646ef-110">Utilizar tabelas de hash</span><span class="sxs-lookup"><span data-stu-id="646ef-110">Using hash tables</span></span>

<span data-ttu-id="646ef-111">Pode ordenar diferentes propriedades em ordens diferentes ao utilizar tabelas de hash numa matriz.</span><span class="sxs-lookup"><span data-stu-id="646ef-111">You can sort different properties in different orders by using hash tables in an array.</span></span>
<span data-ttu-id="646ef-112">Cada tabela de hash utiliza um **expressão** chave para especificar o nome da propriedade como cadeia de caracteres e uma **Ascending** ou **descendente** chave para especificar a ordem de classificação por `$true` ou `$false`.</span><span class="sxs-lookup"><span data-stu-id="646ef-112">Each hash table uses an **Expression** key to specify the property name as string and an **Ascending** or **Descending** key to specify the sort order by `$true` or `$false`.</span></span>
<span data-ttu-id="646ef-113">O **expressão** chave é obrigatória.</span><span class="sxs-lookup"><span data-stu-id="646ef-113">The **Expression** key is mandatory.</span></span>
<span data-ttu-id="646ef-114">O **ascendente** ou **descendente** chave é opcional.</span><span class="sxs-lookup"><span data-stu-id="646ef-114">The **Ascending** or **Descending** key is optional.</span></span>

<span data-ttu-id="646ef-115">O exemplo seguinte classifica os objetos por descendente **LastWriteTime** ordem e ascendente **nome** ordem.</span><span class="sxs-lookup"><span data-stu-id="646ef-115">The following example sorts objects in descending **LastWriteTime** order and ascending **Name** order.</span></span>

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = 'LastWriteTime'; Descending = $true }, @{ Expression = 'Name'; Ascending = $true } |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  dsc
12/1/2018 10:13:50 PM  reference
11/29/2018 6:56:01 PM  .openpublishing.redirection.json
11/29/2018 6:56:01 PM  gallery
11/24/2018 10:33:22 AM developer
11/20/2018 7:22:19 PM  .markdownlint.json
...
```

<span data-ttu-id="646ef-116">Também pode definir um scriptblock o **expressão** chave.</span><span class="sxs-lookup"><span data-stu-id="646ef-116">You can also set a scriptblock to the **Expression** key.</span></span>
<span data-ttu-id="646ef-117">Ao executar o `Sort-Object` cmdlet, que é executado o scriptblock e o resultado é utilizado para ordenação.</span><span class="sxs-lookup"><span data-stu-id="646ef-117">When running the `Sort-Object` cmdlet, the scriptblock is executed and the result is used for sorting.</span></span>

<span data-ttu-id="646ef-118">O exemplo seguinte classifica os objetos em ordem decrescente pelo período de tempo entre **CreationTime** e **LastWriteTime**.</span><span class="sxs-lookup"><span data-stu-id="646ef-118">The following example sorts objects in descending order by the time span between **CreationTime** and **LastWriteTime**.</span></span>

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = { $_.LastWriteTime - $_.CreationTime }; Descending = $true } |
  Format-Table -Property LastWriteTime, CreationTime
```

```output
LastWriteTime          CreationTime
-------------          ------------
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:15 AM
11/3/2018 9:58:17 AM   11/6/2017 10:10:11 AM
10/26/2018 4:50:21 PM  11/6/2017 10:10:11 AM
11/17/2018 1:10:57 PM  11/29/2017 5:48:30 PM
11/12/2018 6:29:53 PM  12/7/2017 7:57:07 PM
...
```

## <a name="tips"></a><span data-ttu-id="646ef-119">Sugestões</span><span class="sxs-lookup"><span data-stu-id="646ef-119">Tips</span></span>

<span data-ttu-id="646ef-120">Pode omitir os **propriedade** nome do parâmetro seguinte:</span><span class="sxs-lookup"><span data-stu-id="646ef-120">You can omit the **Property** parameter name as following:</span></span>

```powershell
Sort-Object LastWriteTime, Name
```

<span data-ttu-id="646ef-121">Além disso, pode consultar `Sort-Object` pelo seu alias incorporada, `sort`:</span><span class="sxs-lookup"><span data-stu-id="646ef-121">Besides, you can refer to `Sort-Object` by its built-in alias, `sort`:</span></span>

```powershell
sort LastWriteTime, Name
```

<span data-ttu-id="646ef-122">As chaves das tabelas de hash para ordenação podem ser abreviadas como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="646ef-122">The keys in the hash tables for sorting can be abbreviated as following:</span></span>

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

<span data-ttu-id="646ef-123">Neste exemplo, o **i** significa **expressão**, o **1!d** significa **descendente**e o **um** quer dizer **Ascending**.</span><span class="sxs-lookup"><span data-stu-id="646ef-123">In this example, the **e** stands for **Expression**, the **d** stands for **Descending**, and the **a** stands for **Ascending**.</span></span>

<span data-ttu-id="646ef-124">Para melhorar a legibilidade, pode colocar as tabelas de hash numa variável separada:</span><span class="sxs-lookup"><span data-stu-id="646ef-124">To improve readability, you can place the hash tables into a separate variable:</span></span>

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```
