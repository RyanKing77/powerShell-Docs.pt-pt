---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: Manipular diretamente itens
ms.assetid: 8cbd4867-917d-41ea-9ff0-b8e765509735
ms.openlocfilehash: d9aa95dcb0da2e8203cbe32d64b95bf33d914166
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2017
---
# <a name="manipulating-items-directly"></a>Manipular diretamente itens
Os elementos que visualiza no Windows PowerShell unidades, tais como os ficheiros e pastas nas unidades de sistema de ficheiros e as chaves do registo em unidades de registo do Windows PowerShell, são denominados *itens* no Windows PowerShell. Os cmdlets para trabalhar com os mesmos item tem o substantivo **Item** nos respetivos nomes.

O resultado a **Get-Command - substantivo Item** comando mostra que existem nove cmdlets de item do Windows PowerShell.

```
PS> Get-Command -Noun Item

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Clear-Item                      Clear-Item [-Path] <String[]...
Cmdlet          Copy-Item                       Copy-Item [-Path] <String[]>...
Cmdlet          Get-Item                        Get-Item [-Path] <String[]> ...
Cmdlet          Invoke-Item                     Invoke-Item [-Path] <String[...
Cmdlet          Move-Item                       Move-Item [-Path] <String[]>...
Cmdlet          New-Item                        New-Item [-Path] <String[]> ...
Cmdlet          Remove-Item                     Remove-Item [-Path] <String[...
Cmdlet          Rename-Item                     Rename-Item [-Path] <String>...
Cmdlet          Set-Item                        Set-Item [-Path] <String[]> ...
```

### <a name="creating-new-items-new-item"></a>Criar novos itens (Novo Item)
Para criar um novo item no sistema de ficheiros, utilize o **Novo Item** cmdlet. Incluir o **caminho** parâmetro com o caminho para o item e o **ItemType** parâmetro com um valor de "ficheiro" ou "diretório".

Por exemplo, para criar um novo diretório denominado "New.Directory"in unidade c:\\diretório Temp, escreva:

```
PS> New-Item -Path c:\temp\New.Directory -ItemType Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  11:29 AM            New.Directory
```

Para criar um ficheiro, altere o valor da **ItemType** parâmetro "ficheiro". Por exemplo, para criar um ficheiro com o nome "file1.txt" no diretório New.Directory, escreva:

```
PS> New-Item -Path C:\temp\New.Directory\file1.txt -ItemType file

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

Pode utilizar a mesma técnica para criar uma nova chave de registo. Na verdade, uma chave de registo é mais fácil criar porque o tipo de item apenas no registo do Windows é uma chave. (Entradas do registo são item *propriedades*.) Por exemplo, para criar uma chave denominada "_Test" na subchave CurrentVersion, escreva:

```
PS> New-Item -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion_Test

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 _Test                          {}
```

Quando escrever um caminho de registo, lembre-se de que inclui os dois pontos (**:**) no Windows PowerShell unidade nomes, HKLM: e HKCU:. Sem vírgula, o Windows PowerShell não reconhece o nome da unidade do caminho.

### <a name="why-registry-values-are-not-items"></a>Por que razão os valores de registo não são itens
Quando utiliza o **Get-ChildItem** cmdlet para determinar os itens existentes na chave de registo, nunca verá as entradas de registo real ou os respetivos valores.

Por exemplo, a chave de registo **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\executar** geralmente contém várias entradas do registo que representam aplicações que são executadas quando inicia o sistema.

No entanto, quando utilizar **Get-ChildItem** para procurar itens subordinados na chave, tudo verá é o **OptionalComponents** subchave da chave:

```
PS> Get-ChildItem HKLM:\Software\Microsoft\Windows\CurrentVersion\Run
   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Micros
oft\Windows\CurrentVersion\Run
SKC  VC Name                           Property
---  -- ----                           --------
  3   0 OptionalComponents             {}
```

Embora seja conveniente tratar as entradas de registo como itens, não é possível especificar um caminho para uma entrada de registo de uma forma que garante que é exclusivo. A notação de caminho não distinguir entre a subchave de registo com o nome **executar** e **(predefinida)** entrada de registo no **executar** subchave. Além disso, porque os nomes de entradas de registo podem conter o caráter de barra invertida (**\\**), se regsitry entradas foram itens, em seguida, não foi possível utilizar a notação de caminho para uma entrada de registo com o nome de distinguir  **Windows\\CurrentVersion\\executar** da subchave que é localizada nesse caminho.

### <a name="renaming-existing-items-rename-item"></a>Mudar o nome de itens existentes (Item de mudança de nome)
Para alterar o nome de um ficheiro ou pasta, utilize o **Item de mudança de nome** cmdlet. O comando seguinte altera o nome do **file1.txt** do ficheiro para **fileOne.txt**.

```
PS> Rename-Item -Path C:\temp\New.Directory\file1.txt fileOne.txt
```

O **Item de mudança de nome** cmdlet pode alterar o nome de um ficheiro ou pasta, mas não é possível mover um item. O seguinte comando falha porque este tenta mover o ficheiro a partir do diretório New.Directory para o diretório Temp.

```
PS> Rename-Item -Path C:\temp\New.Directory\fileOne.txt c:\temp\fileOne.txt
Rename-Item : Cannot rename because the target specified is not a path.
At line:1 char:12
+ Rename-Item  <<<< -Path C:\temp\New.Directory\fileOne c:\temp\fileOne.txt
```

### <a name="moving-items-move-item"></a>Mover itens (Mover Item)
Para mover um ficheiro ou pasta, utilize o **Mover Item** cmdlet.

Por exemplo, o seguinte comando move o diretório de New.Directory da unidade c:\\diretório temp na raiz da unidade c:. Para verificar que o item foi movido, inclua o **PassThru** parâmetro o **Mover Item** cmdlet. Sem **Passthru**, a **Mover Item** cmdlet não apresenta os resultados.

```
PS> Move-Item -Path C:\temp\New.Directory -Destination C:\ -PassThru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  12:14 PM            New.Directory
```

### <a name="copying-items-copy-item"></a>Copiar itens (Copy-Item)
Se estiver familiarizado com as operações de cópia em outros shells, poderá encontrar o comportamento de **Copy-Item** cmdlet no Windows PowerShell para ser invulgar. Quando copiar um item de uma localização para outro, Item de cópia não copia o respetivo conteúdo por predefinição.

Por exemplo, se copiar o **New.Directory** diretório a partir da unidade c: a unidade c:\\no diretório temporário, o comando for bem sucedida, mas os ficheiros no diretório New.Directory não são copiados.

```
PS> Copy-Item -Path C:\New.Directory -Destination C:\temp
```

Se a apresentar o conteúdo da **c:\\temp\\New.Directory**, encontrará que não contém ficheiros:

```
PS> Get-ChildItem -Path C:\temp\New.Directory
PS>
```

Por que motivo não o **Copy-Item** cmdlet copie o conteúdo para a nova localização?

O **Copy-Item** cmdlet foi concebido para ser genéricos; não é apenas para copiar ficheiros e pastas. Além disso, mesmo quando copiar ficheiros e pastas, pode querer copiar apenas o contentor e não os itens nele.

Para copiar todo o conteúdo de uma pasta, inclua o **Recurse** parâmetro o **Copy-Item** cmdlet no comando. Se tiver sido ainda copiado do diretório sem o respetivo conteúdo, adicione o **Force** parâmetro, que permite-lhe substituir a pasta vazia.

```
PS> Copy-Item -Path C:\New.Directory -Destination C:\temp -Recurse -Force -Passthru
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18   1:53 PM            New.Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

### <a name="deleting-items-remove-item"></a>Eliminar itens (Remover-Item)
Para eliminar ficheiros e pastas, utilize o **Remove-Item** cmdlet. Cmdlets do Windows PowerShell, tais como **Remove-Item**, que pode efetuar significativos, alterações irreversível, muitas vezes, irão pedir confirmação ao introduzir o respetivos comandos. Por exemplo, se tentar remover o **New.Directory** pasta, será solicitado para confirmar o comando, porque a pasta contém os ficheiros:

```
PS> Remove-Item C:\New.Directory

Confirm
The item at C:\temp\New.Directory has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
 sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Porque **Sim** resposta predefinido, para eliminar a pasta e os respetivos ficheiros, prima a **Enter** chave. Para remover a pasta sem confirmar, utilize o **-Recurse** parâmetro.

```
PS> Remove-Item C:\temp\New.Directory -Recurse
```

### <a name="executing-items-invoke-item"></a>Executar itens (Item invocar)
O Windows PowerShell utiliza o **Invoke-Item** cmdlet para efetuar uma ação predefinido para um ficheiro ou pasta. Esta ação predefinida é determinada pelo processador de aplicação predefinida no registo; o efeito é o mesmo como se fizer duplo clique no item do Explorador de ficheiros.

Por exemplo, suponha que execute o seguinte comando:

```
PS> Invoke-Item C:\WINDOWS
```

Uma janela do Explorador do que está localizada na c:\\Windows for apresentada, tal como se tivesse double-clicked unidade c:\\pasta do Windows.

Se é a invocar o **Boot.ini** ficheiro num sistema ao Windows Vista:

```
PS> Invoke-Item C:\boot.ini
```

Se o tipo de ficheiro. ini está associado a bloco de notas, o ficheiro boot.ini abre-se no bloco de notas.

