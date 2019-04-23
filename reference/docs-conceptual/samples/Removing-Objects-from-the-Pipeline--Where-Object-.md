---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Remover objetos do Pipeline Where-Object
ms.assetid: 01df8b22-2d22-4e2c-a18d-c004cd3cc284
ms.openlocfilehash: 1f7d064c7bf2dd551ea96b29762fbccad8174084
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984158"
---
# <a name="removing-objects-from-the-pipeline-where-object"></a>Remover objetos do Pipeline (Where-Object)

No Windows PowerShell, muitas vezes, gerar e passar mais objetos para um pipeline que desejar. Pode especificar as propriedades dos objetos específicos para apresentar ao utilizar o **formato** cmdlets, mas isso não ajuda com o problema da remoção de objetos inteiros na exibição. Pode querer filtrar objetos antes do final de um pipeline, pelo que pode executar ações em apenas um subconjunto dos objetos gerou inicialmente.

Windows PowerShell inclui um `Where-Object` cmdlet permite-lhe testar cada objeto no pipeline e apenas passá-lo ao longo do pipeline se ele cumpre uma condição de teste específico. Objetos que não passar no teste são removidos do pipeline. Fornecer a condição de teste como o valor do `Where-Object` **FilterScript** parâmetro.

## <a name="performing-simple-tests-with-where-object"></a>Executar testes simples com Where-Object

O valor de **FilterScript** é um *bloco de script* -uma ou mais comandos do Windows PowerShell rodeados por chavetas {} -que é avaliada como verdadeira ou falsa. Esses blocos de script podem ser muito simples, mas criá-las, precisa conhecer sobre outro conceito do Windows PowerShell, operadores de comparação. Um operador de comparação compara os itens que aparecem em cada lado dele. Operadores de comparação de começar com um "-" caráter e são seguidas por um nome. Operadores de comparação básicos funcionam em praticamente qualquer tipo de objeto. Os operadores de comparação mais avançados poderão funciona somente em texto ou matrizes.

> [!NOTE]
> Por predefinição, ao trabalhar com texto, os operadores de comparação do Windows PowerShell diferenciam maiúsculas de minúsculas.

Devido a considerações de análise, símbolos, como <>, e = não são usados como operadores de comparação. Em vez disso, operadores de comparação são constituídos por letras. Os operadores de comparação básicas estão listados na tabela seguinte.

|Operador de comparação|Significado|Exemplo (retorna verdadeiro)|
|-----------------------|-----------|--------------------------|
|-eq|é igual a|1 -eq 1|
|-ne|Não é igual a|1 - ne 2|
|-lt|É inferior a|1 -lt 2|
|-le|é menor ou igual a|1 - le 2|
|-gt|É maior do que|2 -gt 1|
|-ge|é maior que ou igual a|2 -ge 1|
|-como|É como (comparação de caráter universal para texto)|"file.doc" -like "f\*.do?"|
|-notlike|Não é como (comparação de caráter universal para texto)|"file.doc" -notlike "p\*.doc"|
|-contains|Contém|1,2,3 -contains 1|
|-notcontains|Não contém|1,2,3 - notcontains 4|

Blocos de script WHERE-Object utilizam a variável especial `$_` para fazer referência ao objeto atual no pipeline. Eis um exemplo de como ele funciona. Se tiver uma lista de números e só quiser retornar os que são menos de 3, pode utilizar Where-Object para filtrar os números ao escrever:

```
PS> 1,2,3,4 | Where-Object -FilterScript {$_ -lt 3}
1
2
```

## <a name="filtering-based-on-object-properties"></a>Filtragem com base nas propriedades do objeto

Uma vez que `$_` refere-se para o objeto de pipeline atual, pode aceder às respetivas propriedades para o nossos testes.

Por exemplo, podemos ver a classe Win32_SystemDriver no WMI. Pode haver centenas de drivers de sistema num determinado sistema, mas só poderá estar interessado num determinado conjunto de drivers de sistema, como aqueles que estão atualmente em execução. Se usar Get-Member para ver os membros de Win32_SystemDriver (**Get-WmiObject-classe Win32_SystemDriver | Get-Member - MemberType propriedade**), verá que a propriedade relevante é o estado e que tem um valor de "Execução" quando o controlador está em execução. Pode filtrar os controladores de sistema, selecionar apenas aqueles em execução digitando:

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq 'Running'}
```

Isso produz ainda uma longa lista. Pode querer filtrar para selecionar apenas os controladores definidos para iniciar automaticamente ao testar o valor de StartMode também:

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

Isso nos dá muitas informações que já não precisamos pois Sabemos que os controladores estão em execução. Na verdade, a única informação que, provavelmente precisamos neste momento é o nome e o nome a apresentar. O seguinte comando inclui apenas essas duas propriedades, resultando muito mais simples de dados de saída:

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

Existem dois elementos de Where-Object no comando acima, mas podem ser expressas num único elemento de Where-Object, utilizando a opção - e o operador lógico, como este:

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript { ($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual') } | Format-Table -Property Name,DisplayName
```

Os operadores lógicos padrão estão listados na tabela seguinte.

|Operador lógico|Significado|Exemplo (retorna verdadeiro)|
|--------------------|-----------|--------------------------|
|- e|Lógica e; VERDADEIRO se ambos os lados forem verdadeiros|(1 - eq 1) - e (2 - eq 2).|
|- ou|Lógica ou; VERDADEIRO se ambos os lados for VERDADEIRO|(1 -eq 1) -or (1 -eq 2)|
|-not|Não lógico; reverte true e false|-not (1 -eq 2)|
|\!|Não lógico; reverte true e false|\!(1 -eq 2)|
