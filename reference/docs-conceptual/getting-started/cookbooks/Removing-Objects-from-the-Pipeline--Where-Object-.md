---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Remover objetos a partir do Pipeline onde-objeto
ms.assetid: 01df8b22-2d22-4e2c-a18d-c004cd3cc284
ms.openlocfilehash: 46f210e1418098f4809174cd975ab8d783580285
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753843"
---
# <a name="removing-objects-from-the-pipeline-where-object"></a>Remover objetos a partir do Pipeline (onde-objeto)

No Windows PowerShell, muitas vezes gerar e transferem mais objetos para um pipeline que quiser. Pode especificar as propriedades de objetos específicos para apresentar, utilizando o **formato** cmdlets, mas isto não ajuda com o problema de remover objetos de todos a partir do ecrã. Poderá filtrar objetos antes do fim de um pipeline, pelo que pode realizar ações em apenas um subconjunto dos objetos gerou inicialmente.

O Windows PowerShell inclui um `Where-Object` cmdlet permite-lhe testar cada objeto no pipeline e transmita-apenas pelo pipeline se cumpre uma condição de teste específica. Objetos que não são transmitidas o teste são removidos a partir do pipeline. Forneça a condição de teste como o valor de `Where-Object` **FilterScript** parâmetro.

### <a name="performing-simple-tests-with-where-object"></a>Efetuar testes simples com Where-Object

O valor de **FilterScript** é um *bloco de script* -um ou mais comandos do Windows PowerShell rodeados por chavetas {} -que avalia como VERDADEIRO ou FALSO. Estes blocos de script podem ser muito simples, mas a criação de-los requer saber sobre outro conceito de Windows PowerShell, operadores de comparação. Um operador de comparação compara os itens que são apresentados em cada lado do mesmo. Operadores de comparação de começar com um '-' caráter e seguido de um nome. Operadores de comparação básica funcionam em praticamente qualquer tipo de objeto. Os operadores de comparação mais avançados só poderão funcionar em texto ou de matrizes.

> [!NOTE]
> Por predefinição, quando trabalhar com o texto, operadores de comparação do Windows PowerShell são sensível.

Devido a considerações de análise, símbolos, tais como <>, e = não são utilizadas como operadores de comparação. Em vez disso, operadores de comparação são compostos por letras. Os operadores de comparação básica estão listados na seguinte tabela.

|Operador de comparação|Significado|Exemplo (devolve true)|
|-----------------------|-----------|--------------------------|
|-eq|é igual a|1 - eq 1|
|-ne|Não é igual a|1 - ne 2|
|-lt|É inferior a|1 - lt 2|
|-le|é menor ou igual a|1 - le 2|
|-gt|É maior do que|2 - gt 1|
|-ge|é maior que ou igual a|2 -ge 1|
|-como|É semelhante (comparação de caráter universal para texto)|"file.doc"-como "f\*.do?"|
|-notlike|Não é como (comparação de caráter universal para texto)|"file.doc"-notlike "p\*. doc"|
|-contém|contém|1,2,3 - contém 1|
|-notcontains|não contém|1,2,3 - notcontains 4|

Blocos de script WHERE-Object utilizam a variável especial '$_' referir-se para o objeto atual no pipeline. Eis um exemplo de como funciona. Se tiver uma lista de números e apenas pretende devolver aqueles que são inferior a 3, pode utilizar Where-Object para filtrar os números, escrevendo:

```
PS> 1,2,3,4 | Where-Object -FilterScript {$_ -lt 3}
1
2
```

### <a name="filtering-based-on-object-properties"></a>Filtragem baseada nas propriedades do objeto

Uma vez que $_ refere-se para o objeto de pipeline atual, mas pode aceder a respetivas propriedades para o nossos testes.

Por exemplo, vamos pode ver a classe de Win32_SystemDriver no WMI. Podem existir centenas de controladores do sistema num sistema específico, mas só poderá estar interessado num conjunto específico dos controladores do sistema, tais como as que estão atualmente em execução. Se utilizar o Get-membro para ver os membros de Win32_SystemDriver (**Get-WmiObject-classe Win32_SystemDriver | Get-Member - MemberType propriedade**), verá que a propriedade relevante está no Estado e de que tem um valor de "Em execução" quando o controlador está em execução. Pode filtrar os controladores do sistema, selecionar apenas aqueles em execução, escrevendo:

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq 'Running'}
```

Isto ainda produz uma longa lista. Pode querer de filtro para selecionar apenas os controladores definidos para iniciar automaticamente ao testar o valor de StartMode, bem como:

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

Isto dá-numa grande quantidade de informações que já não é necessário porque Sabemos que os controladores estão em execução. Na verdade, as únicas informações provavelmente precisamos neste momento são o nome e o nome a apresentar. O seguinte comando inclui apenas essas duas propriedades, resultando na saída muito mais simples:

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

Existem dois elementos Where-Object no comando acima, mas podem ser expressas num único elemento Where-Object utilizando- e um operador lógico, como esta:

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript { ($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual') } | Format-Table -Property Name,DisplayName
```

Os padrão operadores lógicos estão listados na seguinte tabela.

|Operador lógico|Significado|Exemplo (devolve true)|
|--------------------|-----------|--------------------------|
|- e|Lógica e; TRUE se ambos os lados forem verdadeiros|(1 - eq 1) - e (2 - eq 2).|
|- ou|Lógico ou; TRUE se ambos os lados for VERDADEIRO|(1 - eq 1) - ou (1 - eq 2).|
|-não|Não lógico; Inverte true e false|-não (1 - eq 2)|
|\!|Não lógico; Inverte true e false|\!(1 - eq 2)|
