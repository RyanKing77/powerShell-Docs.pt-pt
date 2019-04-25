---
ms.date: 3/18/2019
title: Criar consultas do Get-WinEvent com o FilterHashtable
ms.openlocfilehash: 28ba3c99a297944003a28eaba7de34b77d9df536
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058833"
---
# <a name="creating-get-winevent-queries-with-filterhashtable"></a>Criar consultas do Get-WinEvent com o FilterHashtable

Para ler o original 3 de Junho de 2014 **da equipe de scripts** blog post, consulte [utilização FilterHashTable filtro o registo de eventos com o PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).

Este artigo é um extrato de postagem original do blog e explica como utilizar o `Get-WinEvent` do cmdlet **FilterHashtable** parâmetro para filtrar registos de eventos. Do PowerShell `Get-WinEvent` cmdlet é um método poderoso para filtrar eventos do Windows e registos de diagnóstico. Melhora o desempenho quando um `Get-WinEvent` consultar utiliza o **FilterHashtable** parâmetro.

Ao trabalhar com registos de eventos de grandes, não é eficiente para enviar objetos pelo pipeline para um `Where-Object` comando. Antes do PowerShell 6, o `Get-EventLog` cmdlet foi outra opção para obter dados de registo. Por exemplo, os comandos seguintes são ineficazes ao filtro da **Microsoft-Windows-executa a desfragmentação** registos:

`Get-EventLog -LogName Application | Where-Object Source -Match defrag`

`Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }`

O comando seguinte utiliza uma tabela de hash que melhora o desempenho:

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

## <a name="blog-posts-about-enumeration"></a>Mensagens do Blogue acerca da enumeração

Este artigo apresenta informações sobre como utilizar os valores enumerados numa tabela de hash. Para obter mais informações sobre a enumeração, leia estas **da equipe de scripts** postagens no blog. Para criar uma função que retorna os valores enumerados, veja [enumerações e valores](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).
Para obter mais informações, consulte a [mensagens de série da equipe de scripts do Blogue acerca da enumeração](https://devblogs.microsoft.com/scripting/?s=about+enumeration).

## <a name="hash-table-keyvalue-pairs"></a>Pares de chave/valor de tabela de hash

Para criar consultas eficientes, utilize o `Get-WinEvent` cmdlet com o **FilterHashtable** parâmetro.
**FilterHashtable** aceita uma tabela de hash como um filtro para obter informações específicas de registos de eventos do Windows. Utiliza uma tabela de hash **chave/valor** pares. Para obter mais informações sobre as tabelas hash, consulte [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).

Se o **chave/valor** pares estão na mesma linha, eles devem ser separados por ponto e vírgula. Se cada **chave/valor** par é numa linha separada, não é necessária o ponto e vírgula. Por exemplo, este artigo coloca **chave/valor** pares em linhas separadas e não utilize ponto e vírgula.

Este exemplo utiliza várias da **FilterHashtable** do parâmetro **chave/valor** pares. A consulta concluída inclui **LogName**, **ProviderName**, **palavras-chave**, **ID**, e **nível**.

O aceites **chave/valor** pares são mostrados na tabela seguinte e estão incluídos na documentação para o [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** parâmetro.

A tabela seguinte apresenta os nomes de chaves, os tipos de dados, e se os carateres universais são considerados aceites para um valor de dados.

| Nome da chave     | Tipo de dados de valor    | Aceita carateres universais? |
|------------- | ------------------ | ---------------------------- |
| LogName      | `<String[]>`       | Sim |
| ProviderName | `<String[]>`       | Sim |
| Caminho         | `<String[]>`       | Não  |
| palavras-chave     | `<Long[]>`         | Não  |
| ID           | `<Int32[]>`        | Não  |
| Nível        | `<Int32[]>`        | Não  |
| StartTime    | `<DateTime>`       | Não  |
| endTime      | `<DateTime>`       | Não  |
| ID de utilizador       | `<SID>`            | Não  |
| Dados         | `<String[]>`       | Não  |
| *            | `<String[]>`       | Não  |

## <a name="building-a-query-with-a-hash-table"></a>Criação de uma consulta com uma tabela de hash

Para verificar os resultados e resolução de problemas, ele ajuda a criar a tabela de hash uma **chave/valor** par de cada vez. A consulta obtém dados a partir da **aplicativo** log. A tabela de hash é equivalente a `Get-WinEvent –LogName Application`.

Para começar, crie o `Get-WinEvent` consulta. Utilize o **FilterHashtable** do parâmetro **chave/valor** emparelhar com a chave **LogName**e o valor **aplicação**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

Continuar a criar a tabela de hash com o **ProviderName** chave. O **ProviderName** é o nome que aparece no **origem** campo no **Visualizador de eventos do Windows**. Por exemplo, **tempo de execução .NET** na captura de ecrã seguinte:

![Imagem das origens de Visualizador de eventos do Windows.](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

Atualizar a tabela de hash e incluir o **chave/valor** emparelhar com a chave, * * ProviderName e o valor **tempo de execução .NET**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

Se a consulta tem de obter dados arquivados de logs de eventos, utilize o **caminho** chave. O **caminho** valor Especifica o caminho completo para o ficheiro de registo. Para obter mais informações, consulte a **da equipe de scripts** mensagem de blogue [utilize o PowerShell para analisar guardado registos de eventos para erros](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).

## <a name="using-enumerated-values-in-a-hash-table"></a>Usando valores enumerados numa tabela de hash

**Palavras-chave** é a seguinte chave na tabela de hash. O **palavras-chave** tipo de dados é uma matriz do `[long]` tipo que contém um grande número de valor. Utilize o seguinte comando para encontrar o valor máximo de `[long]`:

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

Para o **palavras-chave** chave, PowerShell usa um número, não uma cadeia de caracteres como **segurança**. **Visualizador de eventos do Windows** apresenta o **palavras-chave** como cadeias de caracteres, mas são valores enumerados. Na tabela de hash, se utilizar o **palavras-chave** chave com um valor de cadeia de caracteres, é apresentada uma mensagem de erro.

Abra o **Visualizador de eventos do Windows** e para o **ações** painel, clique em **Filtrar registo atual**.
O **palavras-chave** menu pendente apresenta as palavras-chave disponíveis, como mostrado na captura de ecrã seguinte:

![Imagem de palavras-chave do Visualizador de eventos do Windows.](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

Utilize o seguinte comando para apresentar o `StandardEventKeywords` nomes de propriedade.

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

Os valores enumerados estão documentados no **.NET Framework**. Para obter mais informações, consulte [StandardEventKeywords enumeração](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).

O **palavras-chave** nomes e valores enumerados são os seguintes:

| Nome             |  Valor            |
| ---------------- | ------------------|
| AuditFailure     | 4503599627370496  |
| AuditSuccess     | 9007199254740992  |
| CorrelationHint2 | 18014398509481984 |
| EventLogClassic  | 36028797018963968 |
| Sqm              | 2251799813685248  |
| WdiDiagnostic    | 1125899906842624  |
| WdiContext       | 562949953421312   |
| ResponseTime     | 281474976710656   |
| Nenhum             | 0                 |

Atualizar a tabela de hash e incluir o **chave/valor** emparelhar com a chave **palavras-chave**e o **EventLogClassic** valor de enumeração, **36028797018963968** .

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

### <a name="keywords-static-property-value-optional"></a>Valor de propriedade estática de palavras-chave (opcional)

O **palavras-chave** chave é enumerada, mas pode utilizar um nome de propriedade estática na consulta de tabela de hash.
Em vez de usar a cadeia de caracteres retornada, o nome da propriedade deve ser convertido para um valor com o **Value__** propriedade.

Por exemplo, o script seguinte utiliza a **Value__** propriedade.

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

## <a name="filtering-by-event-id"></a>Filtragem por Id de evento

Para obter os dados mais específicos, os resultados da consulta são filtrados pela **Id de evento**. O **Id de evento** é referenciada na tabela de hash, como a chave **ID** e o valor é um específico **Id de evento**. O **Visualizador de eventos do Windows** apresenta o **Id de evento**. Este exemplo utiliza **1023 de Id de evento**.

Atualizar a tabela de hash e incluir o **chave/valor** emparelhar com a chave **ID** e o valor **1023**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

## <a name="filtering-by-level"></a>Filtragem por nível

Para obter mais refinar os resultados e incluir apenas os eventos que são erros, utilize o **nível** chave.
**Visualizador de eventos do Windows** apresenta o **nível** como valores de cadeias de caracteres, mas são valores enumerados. Na tabela de hash, se utilizar o **nível** chave com um valor de cadeia de caracteres, é apresentada uma mensagem de erro.

**Nível** tem como valores **erro**, **aviso**, ou **informativo**. Utilize o seguinte comando para apresentar o `StandardEventLevel` nomes de propriedade.

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

Os valores enumerados estão documentados no **.NET Framework**. Para obter mais informações, consulte [StandardEventLevel enumeração](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).

O **nível** da chave de nomes e valores enumerados são os seguintes:

| Nome           | Valor |
| -------------- | ----- |
| Verboso        |   5   |
| Informativo  |   4   |
| Aviso        |   3   |
| Erro          |   2   |
| Crítico       |   1   |
| LogAlways      |   0   |

A tabela de hash para a consulta concluída inclui a chave **nível**e o valor **2**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

### <a name="level-static-property-in-enumeration-optional"></a>Nível propriedade estática na enumeração (opcional)

O **nível** chave é enumerada, mas pode utilizar um nome de propriedade estática na consulta de tabela de hash.
Em vez de usar a cadeia de caracteres retornada, o nome da propriedade deve ser convertido para um valor com o **Value__** propriedade.

Por exemplo, o script seguinte utiliza a **Value__** propriedade.

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