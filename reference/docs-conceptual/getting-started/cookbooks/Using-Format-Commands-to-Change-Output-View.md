---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Utilizar Comandos de Formato para Alterar a Vista de Saída
ms.assetid: 63515a06-a6f7-4175-a45e-a0537f4f6d05
ms.openlocfilehash: 97d3a9e04abb61bb80a0b8c67d9fb9e885a0b91b
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952788"
---
# <a name="using-format-commands-to-change-output-view"></a>Utilizar Comandos de Formato para Alterar a Vista de Saída

Windows PowerShell tem um conjunto de cmdlets que lhe permitem controlar as propriedades que são apresentadas para objetos específicos. Os nomes de todos os cmdlets de começar com o verbo **formato**. Permitem-lhe selecionar um ou mais propriedades a mostrar.

O **formato** cmdlets estão **em todo o formato**, **formato-lista**, **Format-Table**, e **personalizada de formato**. Vamos apenas descreve o **em todo o formato**, **formato-lista**, e **Format-Table** cmdlets no Guia do utilizador.

Cada cmdlet de formato tem propriedades predefinidas que serão utilizadas se não especificar as propriedades específicas para apresentar. Cada cmdlet também utiliza o mesmo nome de parâmetro, **propriedade**, para especificar as propriedades que pretende apresentar. Porque **em todo o formato** mostra apenas uma única propriedade respetivo **propriedade** parâmetro só aceita um valor único, mas os parâmetros de propriedade de **formato-lista** e **Format-Table** aceitará uma lista de nomes de propriedade.

Se utilizar o comando **Get-Process - nome powershell** com duas instâncias da execução do Windows PowerShell, pode obter o resultado que tem este aspeto:

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    995       9    30308      27996   152     2.73   2760 powershell
    331       9    23284      29084   143     1.06   3448 powershell
```

No resto nesta secção, vamos explorar como utilizar **formato** cmdlets para alterar a forma como é apresentado o resultado deste comando.

### <a name="using-format-wide-for-single-item-output"></a>Utilizar em todo o formato de saída do Item único

O **em todo o formato** cmdlet, por predefinição, mostra apenas a propriedade predefinida de um objeto. As informações associadas a cada objeto são apresentadas numa única coluna:

```
PS> Get-Process -Name powershell | Format-Wide

powershell                              powershell
```

Também pode especificar uma propriedade não predefinido:

```
PS> Get-Process -Name powershell | Format-Wide -Property Id

2760                                    3448
```

#### <a name="controlling-format-wide-display-with-column"></a>Controlar em todo o formato de apresentação com a coluna

Com o **em todo o formato** cmdlet, só pode apresentar uma propriedade de único cada vez. Isto torna útil para apresentar listas simples que mostram apenas um elemento por linha. Para obter uma lista simple, defina o valor da **coluna** parâmetro como 1, escrevendo:

```powershell
Get-Command Format-Wide -Property Name -Column 1
```

### <a name="using-format-list-for-a-list-view"></a>Utilizando o formato-lista para uma vista de lista

O **formato-lista** cmdlet apresenta um objeto sob a forma de uma lista, com cada propriedade etiqueta e apresentado numa linha separada:

```
PS> Get-Process -Name powershell | Format-List

Id      : 2760
Handles : 1242
CPU     : 3.03125
Name    : powershell

Id      : 3448
Handles : 328
CPU     : 1.0625
Name    : powershell
```

Pode especificar como muitas das propriedades como pretender:

```
PS> Get-Process -Name powershell | Format-List -Property ProcessName,FileVersion
,StartTime,Id

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:42:00
Id          : 2760

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:54:28
Id          : 3448
```

#### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a>Ao obter informações detalhadas utilizando o formato de lista com carateres universais

O **formato-lista** cmdlet permite-lhe utilizar um caráter universal como o valor do respetivo **propriedade** parâmetro. Isto permite-lhe ver informações detalhadas. Muitas vezes, os objetos incluem mais informações que precisar, que é a razão do Windows PowerShell não mostra todos os valores de propriedade por predefinição. Para mostrar todas as propriedades de um objeto, utilize o **formato-lista-propriedade \&#42;** comando. O seguinte comando gera mais de 60 linhas de saída para um único processo:

```powershell
Get-Process -Name powershell | Format-List -Property *
```

Embora o **formato-lista** comando é útil para mostrar detalhes do, se pretender uma descrição geral de saída que inclui o número de itens, uma vista em tabela mais simples, muitas vezes, é mais útil.

### <a name="using-format-table-for-tabular-output"></a>Utilizando o formato de tabela para o resultado da tabela

Se utilizar o **Format-Table** cmdlet com sem nomes de propriedade especificado para formatar a saída do **Get-Process** comando, que obtém exatamente da mesma tal como sem efetuar qualquer formatação de saída. O motivo é que os processos são normalmente apresentados em formato tabular, dado que estão a maior parte dos objetos do Windows PowerShell.

```
PS> Get-Process -Name powershell | Format-Table

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1488       9    31568      29460   152     3.53   2760 powershell
    332       9    23140        632   141     1.06   3448 powershell
```

#### <a name="improving-format-table-output-autosize"></a>Melhorar a tabela de formato de saída (AutoSize)

Embora seja útil para apresentar uma grande quantidade de informações comparáveis uma vista em tabela, poderá ser difícil interpretar esteja demasiado restritas para os dados a apresentar. Por exemplo, se tentar apresentar o caminho do processo, o ID, o nome e empresa, pode obter saída truncada para o caminho de processo e a coluna da empresa:

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company

Path                Name                                 Id Company
----                ----                                 -- -------
C:\Program Files... powershell                         2836 Microsoft Corpor...
```

Se especificar o **AutoSize** parâmetro ao executar o **Format-Table** comando do Windows PowerShell irá calcular larguras de coluna com base nos dados reais que vai apresentar. Isto torna o **caminho** coluna legível, mas a coluna de empresa permanece truncada:

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company -
AutoSize

Path                                                    Name         Id Company
----                                                    ----         -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe powershell 2836 Micr...
```

O **Format-Table** cmdlet ainda poderá truncar os dados, mas só executará, pelo que, no final do ecrã. Propriedades, que não seja o último apresentada, recebem o mesmo tamanho que precisam para o respetivo elemento de dados mais longo para serem apresentadas corretamente. Pode ver que o nome da empresa está visível mas caminho será truncado se trocar as localizações de **caminho** e **empresa** no **propriedade** lista de valores:

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Name,Id,Path -
AutoSize

Company               Name         Id Path
-------               ----         -- ----
Microsoft Corporation powershell 2836 C:\Program Files\Windows PowerShell\v1...
```

O **Format-Table** comando assume que o nearer é uma propriedade para o início da lista de propriedades, é mais importante. Para o mesmo tenta a apresentar as propriedades mais próximo início completamente. Se o **Format-Table** comando não é possível apresentar todas as propriedades, irá remover algumas colunas a apresentar e fornecer um aviso. Pode ver este comportamento se fizer **nome** a última propriedade na lista:

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Path,Id,Name -
AutoSize

WARNING: column "Name" does not fit into the display and was removed.

Company               Path                                                    I
                                                                              d
-------               ----                                                    -
Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\powershell.exe 6
```

No resultado acima, a coluna ID é truncada para torná-lo ajustar a listagem e de cabeçalhos de coluna são empilhados cópias de segurança. Redimensionar automaticamente as colunas sempre que não o que pretende.

#### <a name="wrapping-format-table-output-in-columns-wrap"></a>Saída do tabela do formato de encapsulamento de aplicações nas colunas (moldagem)

Pode forçar demorado **Format-Table** dados moldar dentro da respetiva coluna de apresentação, utilizando o **moldar** parâmetro. Utilizar o **moldar** parâmetro individualmente não necessariamente executará o que esperar, uma vez que utiliza as predefinições se não especificar também **AutoSize**:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -Property Name,Id,Company,
Path

Name                                 Id Company             Path
----                                 -- -------             ----
powershell                         2836 Microsoft Corporati C:\Program Files\Wi
                                        on                  ndows PowerShell\v1
                                                            .0\powershell.exe
```

Uma vantagem de utilizar o **moldar** parâmetro por si só é que que não lentos processamento muito grande. Se efetuar uma listagem de ficheiros recursiva de um sistema de diretório de grandes dimensões, poderá demorar muito tempo e utilizar uma grande quantidade de memória antes de apresentar os itens de resultado primeiro se utilizar **AutoSize**.

Se não tiver preocupados com a carga de sistema, em seguida, **AutoSize** funciona bem com o **moldar** parâmetro. As colunas iniciais são sempre atribuídas o mesmo largura como que precisam para apresentar os itens numa linha, tal como quando especificar **AutoSize** sem o **moldar** parâmetro. A única diferença é que a coluna final irá ser moldada, se necessário:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Company,Path

Name         Id Company               Path
----         -- -------               ----
powershell 2836 Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\
                                      powershell.exe
```

Algumas colunas poderão não apresentadas se especificar as colunas ser em primeiro lugar, pelo que é esta a especificar os elementos de dados mais pequeno primeiro. No exemplo seguinte, especificamos o elemento de caminho extremamente wide primeiro e, mesmo com encapsulamento de aplicações, iremos ainda perder o final **nome** coluna:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Path,I
d,Company,Name

WARNING: column "Name" does not fit into the display and was removed.

Path                                                      Id Company
----                                                      -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe 2836 Microsoft Corporat
                                                             ion
```

#### <a name="organizing-table-output--groupby"></a>Organizar a tabela de saída (-GroupBy)

Outro parâmetro útil para controlo de tabela de saída é **GroupBy**. Em particular já listagens de tabela podem ser difícil de comparar. O **GroupBy** grupos de parâmetro de saída com base no valor de propriedade. Por exemplo, vamos pode agrupar os processos pela empresa para inspecção mais fácil, omitindo o valor da empresa a listagem de propriedade:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Path -GroupBy Company

   Company: Microsoft Corporation

Name         Id Path
----         -- ----
powershell 1956 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
powershell 2656 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
```