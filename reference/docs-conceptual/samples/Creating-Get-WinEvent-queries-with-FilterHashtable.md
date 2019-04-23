---
ms.date: 3/18/2019
title: Criar consultas do Get-WinEvent com o FilterHashtable
ms.openlocfilehash: 28ba3c99a297944003a28eaba7de34b77d9df536
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984226"
---
# <a name="creating-get-winevent-queries-with-filterhashtable"></a><span data-ttu-id="641ea-102">Criar consultas do Get-WinEvent com o FilterHashtable</span><span class="sxs-lookup"><span data-stu-id="641ea-102">Creating Get-WinEvent queries with FilterHashtable</span></span>

<span data-ttu-id="641ea-103">Para ler o original 3 de Junho de 2014 **da equipe de scripts** blog post, consulte [utilização FilterHashTable filtro o registo de eventos com o PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).</span><span class="sxs-lookup"><span data-stu-id="641ea-103">To read the original June 3, 2014 **Scripting Guy** blog post, see [Use FilterHashTable to Filter Event Log with PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).</span></span>

<span data-ttu-id="641ea-104">Este artigo é um extrato de postagem original do blog e explica como utilizar o `Get-WinEvent` do cmdlet **FilterHashtable** parâmetro para filtrar registos de eventos.</span><span class="sxs-lookup"><span data-stu-id="641ea-104">This article is an excerpt of the original blog post and explains how to use the `Get-WinEvent` cmdlet's **FilterHashtable** parameter to filter event logs.</span></span> <span data-ttu-id="641ea-105">Do PowerShell `Get-WinEvent` cmdlet é um método poderoso para filtrar eventos do Windows e registos de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="641ea-105">PowerShell's `Get-WinEvent` cmdlet is a powerful method to filter Windows event and diagnostic logs.</span></span> <span data-ttu-id="641ea-106">Melhora o desempenho quando um `Get-WinEvent` consultar utiliza o **FilterHashtable** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="641ea-106">Performance improves when a `Get-WinEvent` query uses the **FilterHashtable** parameter.</span></span>

<span data-ttu-id="641ea-107">Ao trabalhar com registos de eventos de grandes, não é eficiente para enviar objetos pelo pipeline para um `Where-Object` comando.</span><span class="sxs-lookup"><span data-stu-id="641ea-107">When you work with large event logs, it's not efficient to send objects down the pipeline to a `Where-Object` command.</span></span> <span data-ttu-id="641ea-108">Antes do PowerShell 6, o `Get-EventLog` cmdlet foi outra opção para obter dados de registo.</span><span class="sxs-lookup"><span data-stu-id="641ea-108">Prior to PowerShell 6, the `Get-EventLog` cmdlet was another option to get log data.</span></span> <span data-ttu-id="641ea-109">Por exemplo, os comandos seguintes são ineficazes ao filtro da **Microsoft-Windows-executa a desfragmentação** registos:</span><span class="sxs-lookup"><span data-stu-id="641ea-109">For example, the following commands are inefficient to filter the **Microsoft-Windows-Defrag** logs:</span></span>

`Get-EventLog -LogName Application | Where-Object Source -Match defrag`

`Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }`

<span data-ttu-id="641ea-110">O comando seguinte utiliza uma tabela de hash que melhora o desempenho:</span><span class="sxs-lookup"><span data-stu-id="641ea-110">The following command uses a hash table that improves the performance:</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

## <a name="blog-posts-about-enumeration"></a><span data-ttu-id="641ea-111">Mensagens do Blogue acerca da enumeração</span><span class="sxs-lookup"><span data-stu-id="641ea-111">Blog posts about enumeration</span></span>

<span data-ttu-id="641ea-112">Este artigo apresenta informações sobre como utilizar os valores enumerados numa tabela de hash.</span><span class="sxs-lookup"><span data-stu-id="641ea-112">This article presents information about how to use enumerated values in a hash table.</span></span> <span data-ttu-id="641ea-113">Para obter mais informações sobre a enumeração, leia estas **da equipe de scripts** postagens no blog.</span><span class="sxs-lookup"><span data-stu-id="641ea-113">For more information about enumeration, read these **Scripting Guy** blog posts.</span></span> <span data-ttu-id="641ea-114">Para criar uma função que retorna os valores enumerados, veja [enumerações e valores](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).</span><span class="sxs-lookup"><span data-stu-id="641ea-114">To create a function that returns the enumerated values, see [Enumerations and Values](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).</span></span>
<span data-ttu-id="641ea-115">Para obter mais informações, consulte a [mensagens de série da equipe de scripts do Blogue acerca da enumeração](https://devblogs.microsoft.com/scripting/?s=about+enumeration).</span><span class="sxs-lookup"><span data-stu-id="641ea-115">For more information, see the [Scripting Guy series of blog posts about enumeration](https://devblogs.microsoft.com/scripting/?s=about+enumeration).</span></span>

## <a name="hash-table-keyvalue-pairs"></a><span data-ttu-id="641ea-116">Pares de chave/valor de tabela de hash</span><span class="sxs-lookup"><span data-stu-id="641ea-116">Hash table key/value pairs</span></span>

<span data-ttu-id="641ea-117">Para criar consultas eficientes, utilize o `Get-WinEvent` cmdlet com o **FilterHashtable** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="641ea-117">To build efficient queries, use the `Get-WinEvent` cmdlet with the **FilterHashtable** parameter.</span></span>
<span data-ttu-id="641ea-118">**FilterHashtable** aceita uma tabela de hash como um filtro para obter informações específicas de registos de eventos do Windows.</span><span class="sxs-lookup"><span data-stu-id="641ea-118">**FilterHashtable** accepts a hash table as a filter to get specific information from Windows event logs.</span></span> <span data-ttu-id="641ea-119">Utiliza uma tabela de hash **chave/valor** pares.</span><span class="sxs-lookup"><span data-stu-id="641ea-119">A hash table uses **key/value** pairs.</span></span> <span data-ttu-id="641ea-120">Para obter mais informações sobre as tabelas hash, consulte [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span><span class="sxs-lookup"><span data-stu-id="641ea-120">For more information about hash tables, see [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span>

<span data-ttu-id="641ea-121">Se o **chave/valor** pares estão na mesma linha, eles devem ser separados por ponto e vírgula.</span><span class="sxs-lookup"><span data-stu-id="641ea-121">If the **key/value** pairs are on the same line, they must be separated by a semicolon.</span></span> <span data-ttu-id="641ea-122">Se cada **chave/valor** par é numa linha separada, não é necessária o ponto e vírgula.</span><span class="sxs-lookup"><span data-stu-id="641ea-122">If each **key/value** pair is on a separate line, the semicolon isn't needed.</span></span> <span data-ttu-id="641ea-123">Por exemplo, este artigo coloca **chave/valor** pares em linhas separadas e não utilize ponto e vírgula.</span><span class="sxs-lookup"><span data-stu-id="641ea-123">For example, this article places **key/value** pairs on separate lines and doesn't use semicolons.</span></span>

<span data-ttu-id="641ea-124">Este exemplo utiliza várias da **FilterHashtable** do parâmetro **chave/valor** pares.</span><span class="sxs-lookup"><span data-stu-id="641ea-124">This sample uses several of the **FilterHashtable** parameter's **key/value** pairs.</span></span> <span data-ttu-id="641ea-125">A consulta concluída inclui **LogName**, **ProviderName**, **palavras-chave**, **ID**, e **nível**.</span><span class="sxs-lookup"><span data-stu-id="641ea-125">The completed query includes **LogName**, **ProviderName**, **Keywords**, **ID**, and **Level**.</span></span>

<span data-ttu-id="641ea-126">O aceites **chave/valor** pares são mostrados na tabela seguinte e estão incluídos na documentação para o [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="641ea-126">The accepted **key/value** pairs are shown in the following table and are included in the documentation for the [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** parameter.</span></span>

<span data-ttu-id="641ea-127">A tabela seguinte apresenta os nomes de chaves, os tipos de dados, e se os carateres universais são considerados aceites para um valor de dados.</span><span class="sxs-lookup"><span data-stu-id="641ea-127">The following table displays the key names, data types, and whether wildcard characters are accepted for a data value.</span></span>

| <span data-ttu-id="641ea-128">Nome da chave</span><span class="sxs-lookup"><span data-stu-id="641ea-128">Key name</span></span>     | <span data-ttu-id="641ea-129">Tipo de dados de valor</span><span class="sxs-lookup"><span data-stu-id="641ea-129">Value data type</span></span>    | <span data-ttu-id="641ea-130">Aceita carateres universais?</span><span class="sxs-lookup"><span data-stu-id="641ea-130">Accepts wildcard characters?</span></span> |
|------------- | ------------------ | ---------------------------- |
| <span data-ttu-id="641ea-131">LogName</span><span class="sxs-lookup"><span data-stu-id="641ea-131">LogName</span></span>      | `<String[]>`       | <span data-ttu-id="641ea-132">Sim</span><span class="sxs-lookup"><span data-stu-id="641ea-132">Yes</span></span> |
| <span data-ttu-id="641ea-133">ProviderName</span><span class="sxs-lookup"><span data-stu-id="641ea-133">ProviderName</span></span> | `<String[]>`       | <span data-ttu-id="641ea-134">Sim</span><span class="sxs-lookup"><span data-stu-id="641ea-134">Yes</span></span> |
| <span data-ttu-id="641ea-135">Caminho</span><span class="sxs-lookup"><span data-stu-id="641ea-135">Path</span></span>         | `<String[]>`       | <span data-ttu-id="641ea-136">Não</span><span class="sxs-lookup"><span data-stu-id="641ea-136">No</span></span>  |
| <span data-ttu-id="641ea-137">palavras-chave</span><span class="sxs-lookup"><span data-stu-id="641ea-137">Keywords</span></span>     | `<Long[]>`         | <span data-ttu-id="641ea-138">Não</span><span class="sxs-lookup"><span data-stu-id="641ea-138">No</span></span>  |
| <span data-ttu-id="641ea-139">ID</span><span class="sxs-lookup"><span data-stu-id="641ea-139">ID</span></span>           | `<Int32[]>`        | <span data-ttu-id="641ea-140">Não</span><span class="sxs-lookup"><span data-stu-id="641ea-140">No</span></span>  |
| <span data-ttu-id="641ea-141">Nível</span><span class="sxs-lookup"><span data-stu-id="641ea-141">Level</span></span>        | `<Int32[]>`        | <span data-ttu-id="641ea-142">Não</span><span class="sxs-lookup"><span data-stu-id="641ea-142">No</span></span>  |
| <span data-ttu-id="641ea-143">StartTime</span><span class="sxs-lookup"><span data-stu-id="641ea-143">StartTime</span></span>    | `<DateTime>`       | <span data-ttu-id="641ea-144">Não</span><span class="sxs-lookup"><span data-stu-id="641ea-144">No</span></span>  |
| <span data-ttu-id="641ea-145">endTime</span><span class="sxs-lookup"><span data-stu-id="641ea-145">EndTime</span></span>      | `<DateTime>`       | <span data-ttu-id="641ea-146">Não</span><span class="sxs-lookup"><span data-stu-id="641ea-146">No</span></span>  |
| <span data-ttu-id="641ea-147">ID de utilizador</span><span class="sxs-lookup"><span data-stu-id="641ea-147">UserID</span></span>       | `<SID>`            | <span data-ttu-id="641ea-148">Não</span><span class="sxs-lookup"><span data-stu-id="641ea-148">No</span></span>  |
| <span data-ttu-id="641ea-149">Dados</span><span class="sxs-lookup"><span data-stu-id="641ea-149">Data</span></span>         | `<String[]>`       | <span data-ttu-id="641ea-150">Não</span><span class="sxs-lookup"><span data-stu-id="641ea-150">No</span></span>  |
| *            | `<String[]>`       | <span data-ttu-id="641ea-151">Não</span><span class="sxs-lookup"><span data-stu-id="641ea-151">No</span></span>  |

## <a name="building-a-query-with-a-hash-table"></a><span data-ttu-id="641ea-152">Criação de uma consulta com uma tabela de hash</span><span class="sxs-lookup"><span data-stu-id="641ea-152">Building a query with a hash table</span></span>

<span data-ttu-id="641ea-153">Para verificar os resultados e resolução de problemas, ele ajuda a criar a tabela de hash uma **chave/valor** par de cada vez.</span><span class="sxs-lookup"><span data-stu-id="641ea-153">To verify results and troubleshoot problems, it helps to build the hash table one **key/value** pair at a time.</span></span> <span data-ttu-id="641ea-154">A consulta obtém dados a partir da **aplicativo** log.</span><span class="sxs-lookup"><span data-stu-id="641ea-154">The query gets data from the **Application** log.</span></span> <span data-ttu-id="641ea-155">A tabela de hash é equivalente a `Get-WinEvent –LogName Application`.</span><span class="sxs-lookup"><span data-stu-id="641ea-155">The hash table is equivalent to `Get-WinEvent –LogName Application`.</span></span>

<span data-ttu-id="641ea-156">Para começar, crie o `Get-WinEvent` consulta.</span><span class="sxs-lookup"><span data-stu-id="641ea-156">To begin, create the `Get-WinEvent` query.</span></span> <span data-ttu-id="641ea-157">Utilize o **FilterHashtable** do parâmetro **chave/valor** emparelhar com a chave **LogName**e o valor **aplicação**.</span><span class="sxs-lookup"><span data-stu-id="641ea-157">Use the **FilterHashtable** parameter's **key/value** pair with the key, **LogName**, and the value, **Application**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

<span data-ttu-id="641ea-158">Continuar a criar a tabela de hash com o **ProviderName** chave.</span><span class="sxs-lookup"><span data-stu-id="641ea-158">Continue to build the hash table with the **ProviderName** key.</span></span> <span data-ttu-id="641ea-159">O **ProviderName** é o nome que aparece no **origem** campo no **Visualizador de eventos do Windows**.</span><span class="sxs-lookup"><span data-stu-id="641ea-159">The **ProviderName** is the name that appears in the **Source** field in the **Windows Event Viewer**.</span></span> <span data-ttu-id="641ea-160">Por exemplo, **tempo de execução .NET** na captura de ecrã seguinte:</span><span class="sxs-lookup"><span data-stu-id="641ea-160">For example, **.NET Runtime** in the following screenshot:</span></span>

![Imagem das origens de Visualizador de eventos do Windows.](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

<span data-ttu-id="641ea-162">Atualizar a tabela de hash e incluir o **chave/valor** emparelhar com a chave, \* \* ProviderName e o valor **tempo de execução .NET**.</span><span class="sxs-lookup"><span data-stu-id="641ea-162">Update the hash table and include the **key/value** pair with the key, \*\*ProviderName, and the value, **.NET Runtime**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

<span data-ttu-id="641ea-163">Se a consulta tem de obter dados arquivados de logs de eventos, utilize o **caminho** chave.</span><span class="sxs-lookup"><span data-stu-id="641ea-163">If your query needs to get data from archived event logs, use the **Path** key.</span></span> <span data-ttu-id="641ea-164">O **caminho** valor Especifica o caminho completo para o ficheiro de registo.</span><span class="sxs-lookup"><span data-stu-id="641ea-164">The **Path** value specifies the full path to the log file.</span></span> <span data-ttu-id="641ea-165">Para obter mais informações, consulte a **da equipe de scripts** mensagem de blogue [utilize o PowerShell para analisar guardado registos de eventos para erros](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).</span><span class="sxs-lookup"><span data-stu-id="641ea-165">For more information, see the **Scripting Guy** blog post, [Use PowerShell to Parse Saved Event Logs for Errors](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).</span></span>

## <a name="using-enumerated-values-in-a-hash-table"></a><span data-ttu-id="641ea-166">Usando valores enumerados numa tabela de hash</span><span class="sxs-lookup"><span data-stu-id="641ea-166">Using enumerated values in a hash table</span></span>

<span data-ttu-id="641ea-167">**Palavras-chave** é a seguinte chave na tabela de hash.</span><span class="sxs-lookup"><span data-stu-id="641ea-167">**Keywords** is the next key in the hash table.</span></span> <span data-ttu-id="641ea-168">O **palavras-chave** tipo de dados é uma matriz do `[long]` tipo que contém um grande número de valor.</span><span class="sxs-lookup"><span data-stu-id="641ea-168">The **Keywords** data type is an array of the `[long]` value type that holds a large number.</span></span> <span data-ttu-id="641ea-169">Utilize o seguinte comando para encontrar o valor máximo de `[long]`:</span><span class="sxs-lookup"><span data-stu-id="641ea-169">Use the following command to find the maximum value of `[long]`:</span></span>

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

<span data-ttu-id="641ea-170">Para o **palavras-chave** chave, PowerShell usa um número, não uma cadeia de caracteres como **segurança**.</span><span class="sxs-lookup"><span data-stu-id="641ea-170">For the **Keywords** key, PowerShell uses a number, not a string such as **Security**.</span></span> <span data-ttu-id="641ea-171">**Visualizador de eventos do Windows** apresenta o **palavras-chave** como cadeias de caracteres, mas são valores enumerados.</span><span class="sxs-lookup"><span data-stu-id="641ea-171">**Windows Event Viewer** displays the **Keywords** as strings, but they are enumerated values.</span></span> <span data-ttu-id="641ea-172">Na tabela de hash, se utilizar o **palavras-chave** chave com um valor de cadeia de caracteres, é apresentada uma mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="641ea-172">In the hash table, if you use the **Keywords** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="641ea-173">Abra o **Visualizador de eventos do Windows** e para o **ações** painel, clique em **Filtrar registo atual**.</span><span class="sxs-lookup"><span data-stu-id="641ea-173">Open the **Windows Event Viewer** and from the **Actions** pane, click on **Filter current log**.</span></span>
<span data-ttu-id="641ea-174">O **palavras-chave** menu pendente apresenta as palavras-chave disponíveis, como mostrado na captura de ecrã seguinte:</span><span class="sxs-lookup"><span data-stu-id="641ea-174">The **Keywords** drop-down menu displays the available keywords, as shown in the following screenshot:</span></span>

![Imagem de palavras-chave do Visualizador de eventos do Windows.](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

<span data-ttu-id="641ea-176">Utilize o seguinte comando para apresentar o `StandardEventKeywords` nomes de propriedade.</span><span class="sxs-lookup"><span data-stu-id="641ea-176">Use the following command to display the `StandardEventKeywords` property names.</span></span>

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventKeywords] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventKeywords
Name             MemberType Definition
—-             ———- ———-
AuditFailure     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
AuditSuccess     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint2 Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
EventLogClassic  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
None             Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
ResponseTime     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
Sqm              Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiContext       Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiDiagnostic    Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
```

<span data-ttu-id="641ea-177">Os valores enumerados estão documentados no **.NET Framework**.</span><span class="sxs-lookup"><span data-stu-id="641ea-177">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="641ea-178">Para obter mais informações, consulte [StandardEventKeywords enumeração](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).</span><span class="sxs-lookup"><span data-stu-id="641ea-178">For more information, see [StandardEventKeywords Enumeration](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="641ea-179">O **palavras-chave** nomes e valores enumerados são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="641ea-179">The **Keywords** names and enumerated values are as follows:</span></span>

| <span data-ttu-id="641ea-180">Nome</span><span class="sxs-lookup"><span data-stu-id="641ea-180">Name</span></span>             |  <span data-ttu-id="641ea-181">Valor</span><span class="sxs-lookup"><span data-stu-id="641ea-181">Value</span></span>            |
| ---------------- | ------------------|
| <span data-ttu-id="641ea-182">AuditFailure</span><span class="sxs-lookup"><span data-stu-id="641ea-182">AuditFailure</span></span>     | <span data-ttu-id="641ea-183">4503599627370496</span><span class="sxs-lookup"><span data-stu-id="641ea-183">4503599627370496</span></span>  |
| <span data-ttu-id="641ea-184">AuditSuccess</span><span class="sxs-lookup"><span data-stu-id="641ea-184">AuditSuccess</span></span>     | <span data-ttu-id="641ea-185">9007199254740992</span><span class="sxs-lookup"><span data-stu-id="641ea-185">9007199254740992</span></span>  |
| <span data-ttu-id="641ea-186">CorrelationHint2</span><span class="sxs-lookup"><span data-stu-id="641ea-186">CorrelationHint2</span></span> | <span data-ttu-id="641ea-187">18014398509481984</span><span class="sxs-lookup"><span data-stu-id="641ea-187">18014398509481984</span></span> |
| <span data-ttu-id="641ea-188">EventLogClassic</span><span class="sxs-lookup"><span data-stu-id="641ea-188">EventLogClassic</span></span>  | <span data-ttu-id="641ea-189">36028797018963968</span><span class="sxs-lookup"><span data-stu-id="641ea-189">36028797018963968</span></span> |
| <span data-ttu-id="641ea-190">Sqm</span><span class="sxs-lookup"><span data-stu-id="641ea-190">Sqm</span></span>              | <span data-ttu-id="641ea-191">2251799813685248</span><span class="sxs-lookup"><span data-stu-id="641ea-191">2251799813685248</span></span>  |
| <span data-ttu-id="641ea-192">WdiDiagnostic</span><span class="sxs-lookup"><span data-stu-id="641ea-192">WdiDiagnostic</span></span>    | <span data-ttu-id="641ea-193">1125899906842624</span><span class="sxs-lookup"><span data-stu-id="641ea-193">1125899906842624</span></span>  |
| <span data-ttu-id="641ea-194">WdiContext</span><span class="sxs-lookup"><span data-stu-id="641ea-194">WdiContext</span></span>       | <span data-ttu-id="641ea-195">562949953421312</span><span class="sxs-lookup"><span data-stu-id="641ea-195">562949953421312</span></span>   |
| <span data-ttu-id="641ea-196">ResponseTime</span><span class="sxs-lookup"><span data-stu-id="641ea-196">ResponseTime</span></span>     | <span data-ttu-id="641ea-197">281474976710656</span><span class="sxs-lookup"><span data-stu-id="641ea-197">281474976710656</span></span>   |
| <span data-ttu-id="641ea-198">Nenhum</span><span class="sxs-lookup"><span data-stu-id="641ea-198">None</span></span>             | <span data-ttu-id="641ea-199">0</span><span class="sxs-lookup"><span data-stu-id="641ea-199">0</span></span>                 |

<span data-ttu-id="641ea-200">Atualizar a tabela de hash e incluir o **chave/valor** emparelhar com a chave **palavras-chave**e o **EventLogClassic** valor de enumeração, **36028797018963968** .</span><span class="sxs-lookup"><span data-stu-id="641ea-200">Update the hash table and include the **key/value** pair with the key, **Keywords**, and the **EventLogClassic** enumeration value, **36028797018963968**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

### <a name="keywords-static-property-value-optional"></a><span data-ttu-id="641ea-201">Valor de propriedade estática de palavras-chave (opcional)</span><span class="sxs-lookup"><span data-stu-id="641ea-201">Keywords static property value (optional)</span></span>

<span data-ttu-id="641ea-202">O **palavras-chave** chave é enumerada, mas pode utilizar um nome de propriedade estática na consulta de tabela de hash.</span><span class="sxs-lookup"><span data-stu-id="641ea-202">The **Keywords** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="641ea-203">Em vez de usar a cadeia de caracteres retornada, o nome da propriedade deve ser convertido para um valor com o **Value__** propriedade.</span><span class="sxs-lookup"><span data-stu-id="641ea-203">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="641ea-204">Por exemplo, o script seguinte utiliza a **Value__** propriedade.</span><span class="sxs-lookup"><span data-stu-id="641ea-204">For example, the following script uses the **Value__** property.</span></span>

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

## <a name="filtering-by-event-id"></a><span data-ttu-id="641ea-205">Filtragem por Id de evento</span><span class="sxs-lookup"><span data-stu-id="641ea-205">Filtering by Event Id</span></span>

<span data-ttu-id="641ea-206">Para obter os dados mais específicos, os resultados da consulta são filtrados pela **Id de evento**. O **Id de evento** é referenciada na tabela de hash, como a chave **ID** e o valor é um específico **Id de evento**. O **Visualizador de eventos do Windows** apresenta o **Id de evento**. Este exemplo utiliza **1023 de Id de evento**.</span><span class="sxs-lookup"><span data-stu-id="641ea-206">To get more specific data, the query's results are filtered by **Event Id**. The **Event Id** is referenced in the hash table as the key **ID** and the value is a specific **Event Id**. The **Windows Event Viewer** displays the **Event Id**. This example uses **Event Id 1023**.</span></span>

<span data-ttu-id="641ea-207">Atualizar a tabela de hash e incluir o **chave/valor** emparelhar com a chave **ID** e o valor **1023**.</span><span class="sxs-lookup"><span data-stu-id="641ea-207">Update the hash table and include the **key/value** pair with the key, **ID** and the value, **1023**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

## <a name="filtering-by-level"></a><span data-ttu-id="641ea-208">Filtragem por nível</span><span class="sxs-lookup"><span data-stu-id="641ea-208">Filtering by Level</span></span>

<span data-ttu-id="641ea-209">Para obter mais refinar os resultados e incluir apenas os eventos que são erros, utilize o **nível** chave.</span><span class="sxs-lookup"><span data-stu-id="641ea-209">To further refine the results and include only events that are errors, use the **Level** key.</span></span>
<span data-ttu-id="641ea-210">**Visualizador de eventos do Windows** apresenta o **nível** como valores de cadeias de caracteres, mas são valores enumerados.</span><span class="sxs-lookup"><span data-stu-id="641ea-210">**Windows Event Viewer** displays the **Level** as string values, but they are enumerated values.</span></span> <span data-ttu-id="641ea-211">Na tabela de hash, se utilizar o **nível** chave com um valor de cadeia de caracteres, é apresentada uma mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="641ea-211">In the hash table, if you use the **Level** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="641ea-212">**Nível** tem como valores **erro**, **aviso**, ou **informativo**.</span><span class="sxs-lookup"><span data-stu-id="641ea-212">**Level** has values such as **Error**, **Warning**, or **Informational**.</span></span> <span data-ttu-id="641ea-213">Utilize o seguinte comando para apresentar o `StandardEventLevel` nomes de propriedade.</span><span class="sxs-lookup"><span data-stu-id="641ea-213">Use the following command to display the `StandardEventLevel` property names.</span></span>

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventLevel] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventLevel

Name          MemberType Definition
----          ---------- ----------
Critical      Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Critical {get;}
Error         Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Error {get;}
Informational Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Informational {get;}
LogAlways     Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel LogAlways {get;}
Verbose       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Verbose {get;}
Warning       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Warning {get;}
```

<span data-ttu-id="641ea-214">Os valores enumerados estão documentados no **.NET Framework**.</span><span class="sxs-lookup"><span data-stu-id="641ea-214">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="641ea-215">Para obter mais informações, consulte [StandardEventLevel enumeração](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).</span><span class="sxs-lookup"><span data-stu-id="641ea-215">For more information, see [StandardEventLevel Enumeration](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="641ea-216">O **nível** da chave de nomes e valores enumerados são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="641ea-216">The **Level** key's names and enumerated values are as follows:</span></span>

| <span data-ttu-id="641ea-217">Nome</span><span class="sxs-lookup"><span data-stu-id="641ea-217">Name</span></span>           | <span data-ttu-id="641ea-218">Valor</span><span class="sxs-lookup"><span data-stu-id="641ea-218">Value</span></span> |
| -------------- | ----- |
| <span data-ttu-id="641ea-219">Verboso</span><span class="sxs-lookup"><span data-stu-id="641ea-219">Verbose</span></span>        |   <span data-ttu-id="641ea-220">5</span><span class="sxs-lookup"><span data-stu-id="641ea-220">5</span></span>   |
| <span data-ttu-id="641ea-221">Informativo</span><span class="sxs-lookup"><span data-stu-id="641ea-221">Informational</span></span>  |   <span data-ttu-id="641ea-222">4</span><span class="sxs-lookup"><span data-stu-id="641ea-222">4</span></span>   |
| <span data-ttu-id="641ea-223">Aviso</span><span class="sxs-lookup"><span data-stu-id="641ea-223">Warning</span></span>        |   <span data-ttu-id="641ea-224">3</span><span class="sxs-lookup"><span data-stu-id="641ea-224">3</span></span>   |
| <span data-ttu-id="641ea-225">Erro</span><span class="sxs-lookup"><span data-stu-id="641ea-225">Error</span></span>          |   <span data-ttu-id="641ea-226">2</span><span class="sxs-lookup"><span data-stu-id="641ea-226">2</span></span>   |
| <span data-ttu-id="641ea-227">Crítico</span><span class="sxs-lookup"><span data-stu-id="641ea-227">Critical</span></span>       |   <span data-ttu-id="641ea-228">1</span><span class="sxs-lookup"><span data-stu-id="641ea-228">1</span></span>   |
| <span data-ttu-id="641ea-229">LogAlways</span><span class="sxs-lookup"><span data-stu-id="641ea-229">LogAlways</span></span>      |   <span data-ttu-id="641ea-230">0</span><span class="sxs-lookup"><span data-stu-id="641ea-230">0</span></span>   |

<span data-ttu-id="641ea-231">A tabela de hash para a consulta concluída inclui a chave **nível**e o valor **2**.</span><span class="sxs-lookup"><span data-stu-id="641ea-231">The hash table for the completed query includes the key, **Level**, and the value, **2**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

### <a name="level-static-property-in-enumeration-optional"></a><span data-ttu-id="641ea-232">Nível propriedade estática na enumeração (opcional)</span><span class="sxs-lookup"><span data-stu-id="641ea-232">Level static property in enumeration (optional)</span></span>

<span data-ttu-id="641ea-233">O **nível** chave é enumerada, mas pode utilizar um nome de propriedade estática na consulta de tabela de hash.</span><span class="sxs-lookup"><span data-stu-id="641ea-233">The **Level** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="641ea-234">Em vez de usar a cadeia de caracteres retornada, o nome da propriedade deve ser convertido para um valor com o **Value__** propriedade.</span><span class="sxs-lookup"><span data-stu-id="641ea-234">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="641ea-235">Por exemplo, o script seguinte utiliza a **Value__** propriedade.</span><span class="sxs-lookup"><span data-stu-id="641ea-235">For example, the following script uses the **Value__** property.</span></span>

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventLevel]::Informational
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=$C.Value__
}
```