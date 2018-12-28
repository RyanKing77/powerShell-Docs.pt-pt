---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Utilizar Comandos de Formato para Alterar a Vista de Saída
ms.assetid: 63515a06-a6f7-4175-a45e-a0537f4f6d05
ms.openlocfilehash: 97d3a9e04abb61bb80a0b8c67d9fb9e885a0b91b
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405376"
---
# <a name="using-format-commands-to-change-output-view"></a>Utilizar Comandos de Formato para Alterar a Vista de Saída

Windows PowerShell tem um conjunto de cmdlets que permitem controlar quais propriedades são apresentadas para objetos específicos. Os nomes de todos os cmdlets começam com o verbo **formato**. Eles permitem-lhe selecionar uma ou mais propriedades para mostrar.

O **formato** cmdlets são **Format-Wide**, **Format-List**, **Format-Table**, e **formato personalizado**. Descreveremos apenas a **Format-Wide**, **Format-List**, e **Format-Table** cmdlets no guia deste utilizador.

Cada cmdlet de formato tem propriedades predefinidas que serão utilizadas se não especificar as propriedades específicas para apresentar. Cada cmdlet também utiliza o mesmo nome de parâmetro, **propriedade**para especificar quais propriedades deseja exibir. Uma vez **Format-Wide** mostra apenas uma única propriedade, seu **propriedade** parâmetro leva apenas um único valor, mas os parâmetros de propriedade da **Format-List** e **Format-Table** aceitará uma lista de nomes de propriedade.

Se usar o comando **Get-Process - nome powershell** com duas instâncias da execução do Windows PowerShell, obtém uma saída como esta:

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    995       9    30308      27996   152     2.73   2760 powershell
    331       9    23284      29084   143     1.06   3448 powershell
```

No restante desta seção, Exploraremos como utilizar **formato** cmdlets para alterar a forma como é apresentado o resultado deste comando.

### <a name="using-format-wide-for-single-item-output"></a>Usando em todo o formato de saída de Item único

O **Format-Wide** cmdlet, por padrão, exibe a propriedade de padrão de um objeto. As informações associadas com cada objeto são apresentadas numa única coluna:

```
PS> Get-Process -Name powershell | Format-Wide

powershell                              powershell
```

Também pode especificar uma propriedade não predefinido:

```
PS> Get-Process -Name powershell | Format-Wide -Property Id

2760                                    3448
```

#### <a name="controlling-format-wide-display-with-column"></a>Controlar a exibição de todo o formato com coluna

Com o **Format-Wide** cmdlet, pode apresentar apenas uma única propriedade ao mesmo tempo. Assim, é útil para exibir listas simples que mostram apenas um elemento por linha. Para obter uma lista simple, defina o valor do **coluna** parâmetro 1 digitando:

```powershell
Get-Command Format-Wide -Property Name -Column 1
```

### <a name="using-format-list-for-a-list-view"></a>Usando o formato de lista para obter uma exibição de lista

O **Format-List** cmdlet apresenta um objeto na forma de obter uma lista, com cada propriedade com o nome e exibidos numa linha separada:

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

Pode especificar propriedades tantos quantos quiser:

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

#### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a>Ao obter as informações detalhadas com o formato de lista com carateres universais

O **Format-List** cmdlet permite-lhe utilizar um caráter universal como o valor do respetivo **propriedade** parâmetro. Isto permite-lhe apresentar informações detalhadas. Muitas vezes, os objetos incluem mais informações que precisa, razão pela qual o Windows PowerShell não mostra todos os valores de propriedade por predefinição. Para mostrar todas as propriedades de um objeto, utilize o **Format-List-propriedade \&#42;** comando. O comando seguinte gera mais de 60 linhas da saída para um único processo:

```powershell
Get-Process -Name powershell | Format-List -Property *
```

Embora o **Format-List** comando é útil para mostrar os detalhes, se desejar uma visão geral de saída que inclui o número de itens, uma exibição tabular mais simples, muitas vezes, é mais útil.

### <a name="using-format-table-for-tabular-output"></a>Usando o formato de tabela para saída Tabular

Se utilizar o **Format-Table** cmdlet com não nomes de propriedade especificado para formatar a saída da **Get-Process** de comando, obtém exatamente a mesma saída como acontece sem executar qualquer formatação. O motivo é que os processos são normalmente apresentados num formato tabular, assim como a maioria dos objetos do Windows PowerShell.

```
PS> Get-Process -Name powershell | Format-Table

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1488       9    31568      29460   152     3.53   2760 powershell
    332       9    23140        632   141     1.06   3448 powershell
```

#### <a name="improving-format-table-output-autosize"></a>Melhorando a saída do Format-Table (AutoSize)

Embora uma exibição tabular é útil para a exibição muita informação comparável, poderá ser difícil de interpretar se a exibição é demasiado pequena para os dados. Por exemplo, se tentar exibir o caminho do processo, o ID, nome e empresa, receberá saída truncada para o caminho de processo e a coluna de empresa:

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company

Path                Name                                 Id Company
----                ----                                 -- -------
C:\Program Files... powershell                         2836 Microsoft Corpor...
```

Se especificar a **AutoSize** parâmetro ao executar o **Format-Table** comando, o Windows PowerShell irá calcular a largura das colunas com base em dados reais, pretende apresentar. Isso faz com que o **caminho** coluna legível, mas a coluna de empresa permanece truncado:

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company -
AutoSize

Path                                                    Name         Id Company
----                                                    ----         -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe powershell 2836 Micr...
```

O **Format-Table** cmdlet ainda pode truncar a dados, mas isso apenas será feito isso no final do ecrã. Propriedades, diferente do apresentado, último recebem tanto tamanho à medida que necessitam para o elemento de dados mais longo apresentar corretamente. Pode ver que o nome da empresa está visível mas caminho será truncado se alternar os locais dos **caminho** e **empresa** no **propriedade** lista de valores:

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Name,Id,Path -
AutoSize

Company               Name         Id Path
-------               ----         -- ----
Microsoft Corporation powershell 2836 C:\Program Files\Windows PowerShell\v1...
```

O **Format-Table** comando assume que o nearer é uma propriedade para o início da lista de propriedades, é mais importante. Portanto, ele tenta exibir as propriedades mais próximo início completamente. Se o **Format-Table** comando não é possível apresentar todas as propriedades, irá remover algumas colunas na exibição e fornecer um aviso. Pode ver este comportamento se fizer **nome** a última propriedade na lista:

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Path,Id,Name -
AutoSize

WARNING: column "Name" does not fit into the display and was removed.

Company               Path                                                    I
                                                                              d
-------               ----                                                    -
Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\powershell.exe 6
```

No resultado acima, a coluna ID é truncada para torná-lo a se adaptam a listagem e os cabeçalhos de coluna são empilhados a cópia de segurança. Redimensionar automaticamente as colunas não sempre faz o que deseja.

#### <a name="wrapping-format-table-output-in-columns-wrap"></a>Saída do Format-Table de encapsulamento de aplicações nas colunas (moldagem)

Pode forçar longas **Format-Table** dados para encapsular dentro de sua coluna de apresentação com o **encapsular** parâmetro. Utilizar o **encapsular** parâmetro sozinho não necessariamente fará o que esperar, uma vez que utiliza as predefinições se não especificar também **AutoSize**:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -Property Name,Id,Company,
Path

Name                                 Id Company             Path
----                                 -- -------             ----
powershell                         2836 Microsoft Corporati C:\Program Files\Wi
                                        on                  ndows PowerShell\v1
                                                            .0\powershell.exe
```

Uma vantagem de utilizar o **encapsular** parâmetro por si só, é que ele não abrandar processamento muito. Se efetuar uma listagem de arquivos recursiva de um sistema de diretório grandes, poderá demorar muito tempo e utilizar muita memória antes de exibir os primeiros itens de saída, se usar **AutoSize**.

Se não estiver preocupado com carga de sistema, em seguida, **AutoSize** funciona bem com o **encapsular** parâmetro. As colunas iniciais são sempre que poderá máximo da largura que precisam para exibir itens numa linha, tal como quando especificar **AutoSize** sem o **encapsular** parâmetro. A única diferença é que a coluna final será moldada se necessário:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Company,Path

Name         Id Company               Path
----         -- -------               ----
powershell 2836 Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\
                                      powershell.exe
```

Algumas colunas poderão, não, ser apresentadas se especificar as colunas mais amplas em primeiro lugar, portanto, é mais segura especificar os elementos de dados mais pequenas primeiro. No exemplo seguinte, especificamos o elemento de caminho extremamente grande primeiro e, mesmo com o encapsulamento de aplicações, perdemos ainda o último **nome** coluna:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Path,I
d,Company,Name

WARNING: column "Name" does not fit into the display and was removed.

Path                                                      Id Company
----                                                      -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe 2836 Microsoft Corporat
                                                             ion
```

#### <a name="organizing-table-output--groupby"></a>Organizar a saída da tabela (-GroupBy)

É o outro parâmetro útil para controle de saída tabular **GroupBy**. Em particular já listagens de tabela podem ser difíceis de comparar. O **GroupBy** resultado com base num valor de propriedade de grupos de parâmetro. Por exemplo, podemos pode agrupar processos pela empresa para a inspeção mais fácil, omitindo o valor da empresa a partir da lista de propriedade:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Path -GroupBy Company

   Company: Microsoft Corporation

Name         Id Path
----         -- ----
powershell 1956 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
powershell 2656 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
```