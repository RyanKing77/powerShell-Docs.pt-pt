---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: "Gerir a localização atual"
ms.assetid: a9f9e7a7-3ea8-47d3-bbb4-6e437f6d4a4a
ms.openlocfilehash: cbdebb84b3191e3bd549a1cf344cbeefaa91a23c
ms.sourcegitcommit: c5251755c4442487f99ff74fadf7e37bbf039089
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/18/2017
---
# <a name="managing-current-location"></a>Gerir a localização atual
Quando navegar sistemas de pasta no Explorador de ficheiros, normalmente, têm de uma localização de trabalho específica - nomeadamente, abra pasta atual. Itens na pasta atual podem ser manipulados facilmente clicando-los. Para interfaces de linha de comandos como Cmd.exe, quando estão na mesma pasta que um ficheiro específico, pode acedê-lo ao especificar um nome de tempo relativamente curto, em vez de necessidade de especificar o caminho completo para o ficheiro. O diretório atual é denominado o diretório de trabalho.

O Windows PowerShell utiliza o substantivo **localização** para fazer referência ao diretório de trabalho e implementa uma família de cmdlets para examinar e manipular a sua localização.

### <a name="getting-your-current-location-get-location"></a>Obter a localização atual (Get-Location)
Para determinar o caminho da sua localização do diretório atual, introduza o **Get-Location** comando:

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> O cmdlet Get-Location é semelhante para o **pwd** comando na shell de DETEÇÃO. O cmdlet Set-Location é semelhante para o **cd** no Cmd.exe.

### <a name="setting-your-current-location-set-location"></a>Definir a sua localização atual (localização do conjunto)
O **Get-Location** comando é utilizado com o **Set-Location** comando. O **Set-Location** comando permite-lhe especificar a localização do diretório atual.

```
PS> Set-Location -Path C:\Windows
```

Depois de introduzir o comando, irá reparar que não receber quaisquer comentários sobre o efeito do comando direto. A maioria dos comandos do Windows PowerShell que efetue uma ação produzem resultados de pouca ou nenhuma porque o resultado nem sempre é útil. Para verificar que uma alteração de directório de êxito ocorreu ao introduzir o **localização do conjunto** comando, que incluem o **- PassThru** parâmetro ao introduzir o **-localização do conjunto**comando:

```
PS> Set-Location -Path C:\Windows -PassThru
Path
----
C:\WINDOWS
```

O **- PassThru** parâmetro pode ser utilizado com muitos de conjunto de comandos do Windows PowerShell para devolver informações sobre o resultado nos casos em que não há nenhuma saída predefinida.

Pode especificar caminhos relativamente à sua localização atual da mesma forma como os seria na maioria dos UNIX e o Windows comando shells. Na notação padrão para caminhos relativos, durante um período (**.**) representa a pasta atual e um período doubled (**..** ) representa o diretório principal da sua localização atual.

Por exemplo, se está a **c:\\Windows** pasta, um período (**.**) representa **c:\\Windows** e faça duplo períodos (**..** ) representam **c:**. Pode alterar da sua localização atual para a raiz da unidade c:, escrevendo:

```powershell
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

A mesma técnica funciona em unidades do Windows PowerShell que não estão unidades do sistema de ficheiros, tais como **HKLM:**. Pode definir a sua localização para o HKLM\\chave de Software no registo, escrevendo:

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

Em seguida, pode alterar a localização do diretório para o diretório principal, qual é a raiz da HKLM de PowerShell Windows: unidade, utilizando um caminho relativo:

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

Pode introduzir localização do conjunto ou utilizar qualquer um dos aliases incorporados do Windows PowerShell para Set-Location (cd, chdir, sl). Por exemplo:

```
cd -Path C:\Windows
```

```
chdir -Path .. -PassThru
```

```
sl -Path HKLM:\SOFTWARE -PassThru
```

### <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a>Guardar e recupera um recentes localizações (localização de Push e Pop-Location)
Quando alterar as localizações, é útil para manter um registo de onde foram e conseguir regressar à sua localização anterior. O **Push-Location** cmdlet no Windows PowerShell cria um histórico ordenado (um "pilha") de caminhos de diretório em que foi e pode seguir novamente o histórico de caminhos de diretório, utilizando o complementares  **POP-Location** cmdlet.

Por exemplo, do Windows PowerShell, normalmente, é iniciada no diretório raiz do utilizador.

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> A palavra *pilha* tem um significado especial nos muitas definições de programação, incluindo o .NET Framework. Como uma pilha física de itens, o último item que colocar na pilha é o primeiro item que pode solicitar a desativar a pilha. A adição de um item a uma pilha colloquially é conhecida como "emitir" item na pilha. Extrair um item desativado a pilha colloquially é conhecido como "popping" item fora da pilha.

Push a localização atual na pilha e, em seguida, mova para a pasta de definições do Local, escreva:

```
PS> Push-Location -Path "Local Settings"
```

Em seguida, pode emitir a localização de definições locais na pilha e e mover para a pasta Temp escrevendo:

```
PS> Push-Location -Path Temp
```

Pode verificar que alterou diretórios introduzindo o **Get-Location** comando:

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

Pode extrair, em seguida, volta para o diretório mais recentemente visitado introduzindo o **Pop-Location** comando e certifique-se a alteração ao introduzir o **Get-Location** comando:

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

Apenas como com a **Set-Location** cmdlet, pode incluir o **- PassThru** parâmetro ao introduzir o **Pop-Location** cmdlet para ver o diretório que introduziu:

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

Também pode utilizar os cmdlets de localização com caminhos de rede. Se tiver um servidor com o nome FS01 com uma partilha com o nome público, pode alterar a localização, escrevendo

```
Set-Location \\FS01\Public
```

ou

```
Push-Location \\FS01\Public
```

Pode utilizar o **Push-Location** e **Set-Location** comandos para alterar a localização para qualquer unidade disponível. Por exemplo, se tiver uma unidade de CD-ROM local com letra de unidade D que contém um CD de dados, pode alterar a localização para a unidade de CD introduzindo o **D: de localização do conjunto** comando.

Se a unidade está vazia, obterá a seguinte mensagem de erro:

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

Quando estiver a utilizar uma interface de linha de comandos, não é conveniente utilizar o Explorador de ficheiros para examinar as unidades físicas disponíveis. Além disso, Explorador de ficheiros iria não mostram-lhe a todas as unidades do Windows PowerShell. O Windows PowerShell oferece um conjunto de comandos para manipular unidades do Windows PowerShell e serão abordadas estes seguinte.

