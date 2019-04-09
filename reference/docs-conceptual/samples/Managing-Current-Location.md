---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Gerir a Localização Atual
ms.assetid: a9f9e7a7-3ea8-47d3-bbb4-6e437f6d4a4a
ms.openlocfilehash: f5e0653b2c3bbc9d2526c7a1c2ff88a8a6641695
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293191"
---
# <a name="managing-current-location"></a>Gerir a Localização Atual

Ao navegar sistemas de pasta no Explorador de ficheiros, normalmente, têm um local de trabalho específico - ou seja, a abrir pasta atual. Itens na pasta atual podem ser manipulados facilmente ao clicar nas mesmas. Para interfaces de linha de comandos como Cmd.exe, quando estiver na mesma pasta que um determinado arquivo, pode acessá-lo, especificando um nome relativamente curto, em vez de necessidade de especificar o caminho completo para o ficheiro. O diretório atual é chamado o diretório de trabalho.

Windows PowerShell utiliza o substantivo **localização** referir-se para o diretório de trabalho e implementa uma família de cmdlets para examinar e manipular a sua localização.

## <a name="getting-your-current-location-get-location"></a>Obtenção da localização atual (Get-Location)

Para determinar o caminho da localização do seu diretório atual, introduza o **Get-Location** comando:

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> O cmdlet Get-Location é semelhante para o **pwd** comando no shell do BASH. O cmdlet Set-Location é semelhante para o **cd** no Cmd.exe.

## <a name="setting-your-current-location-set-location"></a>Definir a sua localização atual (Set-Location)

O **Get-Location** comando é utilizado com o **Set-Location** comando. O **Set-Location** comando permite que especifique a localização do diretório atual.

```powershell
Set-Location -Path C:\Windows
```

Depois de introduzir o comando, notará que não recebem qualquer direto de comentários sobre o efeito do comando. A maioria dos comandos do Windows PowerShell que executam uma ação produzem resultados de pouca ou nenhuma porque a saída não é sempre útil. Para verificar que uma alteração de diretório concluída com êxito ocorreu ao introduzir o **Set-Location** comando, inclua o **- PassThru** parâmetro ao introduzir o **Set-Location**comando:

```
PS> Set-Location -Path C:\Windows -PassThru

Path
----
C:\WINDOWS
```

O **- PassThru** parâmetro pode ser utilizado com muitos de conjunto de comandos no Windows PowerShell para devolver informações sobre o resultado em casos em que não há nenhuma saída padrão.

É possível especificar caminhos relativo à sua localização atual da mesma forma como faria na maioria dos UNIX e Windows comando shells. Na notação padrão para caminhos relativos, um período (**.**) representa a pasta atual e um período doubled (**...** ) representa o diretório principal da sua localização atual.

Por exemplo, se estiver da **c:\\Windows** pasta, um período (**.**) representa **c:\\Windows** e o dobro períodos (**...** ) representam **c:**. Pode alterar de sua localização atual na raiz da unidade c:, digitando:

```
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

A mesma técnica funciona em unidades do Windows PowerShell que não são unidades de sistema de ficheiros, tal como **HKLM:**. Pode definir sua localização como o HKLM\\chave de Software no registo ao escrever:

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

Em seguida, pode alterar a localização do diretório para o diretório principal, que é a raiz do HKLM de PowerShell Windows: unidade, ao utilizar um caminho relativo:

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

Pode escrever Set-Location ou utilizar qualquer um dos aliases de Windows PowerShell incorporados para Set-Location (cd, chdir, sl). Por exemplo:

```powershell
cd -Path C:\Windows
```

```powershell
chdir -Path .. -PassThru
```

```powershell
sl -Path HKLM:\SOFTWARE -PassThru
```

## <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a>A guardar e recupera um localizações recentes (localização de Push e Pop-Location)

Localizações de alteração, é útil para manter o controle sobre onde tenham sido e ser capaz de retornar para a sua localização anterior. O **Push-Location** cmdlet no Windows PowerShell cria um histórico ordenado (uma "pilha") de caminhos de diretório em que lhe foram, e pode percorrer novamente o histórico de caminhos de diretório utilizando o complementares  **POP-Location** cmdlet.

Por exemplo, Windows PowerShell, normalmente, é iniciada no diretório raiz do utilizador.

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> A palavra *stack* tem um significado especial em muitas configurações de programação, incluindo o .NET Framework. Como uma pilha física de itens, o último item colocado na pilha é o primeiro item que pode extrair na pilha. Adicionar um item a uma pilha colloquially é conhecido como "emitir" o item na pilha. Extrair um item na pilha colloquially é conhecido como "popping" o item na pilha.

Para enviar por push a localização atual para a pilha e, em seguida, mova para a pasta de configurações locais, escreva:

```powershell
Push-Location -Path "Local Settings"
```

Pode, em seguida, enviar por push o local de configurações locais para a pilha e mover para a pasta Temp digitando:

```powershell
Push-Location -Path Temp
```

Pode verificar que alterados diretórios, introduzindo os **Get-Location** comando:

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

Em seguida, pode inserir volta para o diretório mais recentemente visitado, introduzindo os **Pop-Location** de comandos e verificar a alteração ao introduzir o **Get-Location** comando:

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

Tal como sucede com as **Set-Location** cmdlet, pode incluir a **- PassThru** parâmetro ao introduzir o **Pop-Location** cmdlet para ver o diretório que introduziu:

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

Também pode utilizar os cmdlets de localização com caminhos de rede. Se tiver um servidor com o nome FS01 com uma partilha com o nome público, pode alterar a localização, escrevendo

```powershell
Set-Location \\FS01\Public
```

ou

```powershell
Push-Location \\FS01\Public
```

Pode utilizar o **Push-Location** e **Set-Location** comandos para alterar a localização para qualquer unidade disponível. Por exemplo, se tiver uma unidade de CD-ROM local com a letra de unidade D que contém um CD de dados, pode alterar a localização para a unidade de CD, introduzindo os **Set-Location D:** comando.

Se a unidade está vazia, obterá a seguinte mensagem de erro:

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

Quando estiver a utilizar uma interface de linha de comandos, não é prático é utilizar o Explorador de ficheiros para examinar as unidades de físicas disponíveis. Além disso, Explorador de ficheiros não mostrar todas as unidades do Windows PowerShell. Windows PowerShell fornece um conjunto de comandos para a manipulação de unidades do Windows PowerShell, e vamos falar sobre isso em seguida.
