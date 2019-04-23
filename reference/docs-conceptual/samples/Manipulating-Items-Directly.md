---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Manipular Itens Diretamente
ms.assetid: 8cbd4867-917d-41ea-9ff0-b8e765509735
ms.openlocfilehash: 4caa7d2e0eecff9783556062d8503fe10e616fe5
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984379"
---
# <a name="manipulating-items-directly"></a>Manipular Itens Diretamente

Os elementos que vê em unidades do Windows PowerShell, por exemplo, os ficheiros e pastas em unidades de sistema de ficheiros e as chaves de registo em unidades de registo do Windows PowerShell, são chamados *itens* no Windows PowerShell. Os cmdlets para trabalhar com eles item têm o substantivo **Item** nos respetivos nomes.

A saída do **Get-Command - Item substantivo** comando mostra que há nove cmdlets de item do Windows PowerShell.

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

## <a name="creating-new-items-new-item"></a>Criação de novos itens (Novo Item)

Para criar um novo item no sistema de ficheiros, utilize o **New Item** cmdlet. Incluir o **caminho** parâmetro com o caminho para o item e o **ItemType** parâmetro com um valor de "arquivo" ou "diretório".

Por exemplo, para criar um novo diretório com o nome "New.Directory"in a unidade c:\\diretório Temp, escreva:

```
PS> New-Item -Path c:\temp\New.Directory -ItemType Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  11:29 AM            New.Directory
```

Para criar um ficheiro, altere o valor do **ItemType** parâmetro para "arquivo". Por exemplo, para criar um arquivo chamado "file1.txt" no diretório New.Directory, escreva:

```
PS> New-Item -Path C:\temp\New.Directory\file1.txt -ItemType file

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

Pode utilizar a mesma técnica para criar uma nova chave de registo. Na verdade, uma chave de registo é mais fácil criar porque o único tipo de item no registo do Windows é uma chave. (As entradas do Registro são item *propriedades*.) Por exemplo, para criar uma chave denominada Testar"na subchave CurrentVersion, escreva:

```
PS> New-Item -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion_Test

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 _Test                          {}
```

Ao digitar um caminho de registo, certifique-se de que inclui os dois pontos (**:**) no Windows PowerShell unidade nomes, HKLM: e HKCU:. Sem os dois pontos, o Windows PowerShell não reconhece o nome da unidade no caminho.

## <a name="why-registry-values-are-not-items"></a>Por que os valores de registo não são itens

Quando utiliza a **Get-ChildItem** cmdlet para localizar os itens numa chave de registo nunca verá as entradas do Registro atual ou os respetivos valores.

Por exemplo, a chave de registo **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\executar** geralmente contém várias entradas de registo que representam aplicações que são executadas quando o sistema é iniciado.

No entanto, quando utiliza **Get-ChildItem** para procurar itens subordinados na chave, tudo o que verá é o **OptionalComponents** subchave da chave:

```
PS> Get-ChildItem HKLM:\Software\Microsoft\Windows\CurrentVersion\Run

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Micros
oft\Windows\CurrentVersion\Run
SKC  VC Name                           Property
---  -- ----                           --------
  3   0 OptionalComponents             {}
```

Embora seria conveniente tratar as entradas do Registro como itens, não é possível especificar um caminho para uma entrada de registo de uma forma que garante que é exclusivo. A notação de caminho não faz distinção entre a subchave de registo com o nome **execute** e o **(predefinida)** entrada de registo no **executar** subchave. Além disso, uma vez que os nomes de entrada de registo podem conter o caráter de barra invertida (**\\**), se as entradas do Registro foram itens, em seguida, não podia usar a notação de caminho para uma entrada de registo com o nome de distinguir  **Windows\\CurrentVersion\\executar** da subchave que está localizada em que o caminho.

## <a name="renaming-existing-items-rename-item"></a>Mudar o nome de itens existentes (Rename-Item)

Para alterar o nome de um ficheiro ou pasta, utilize o **Rename-Item** cmdlet. O comando seguinte altera o nome da **file1.txt** do ficheiro para **fileOne.txt**.

```powershell
Rename-Item -Path C:\temp\New.Directory\file1.txt fileOne.txt
```

O **Rename-Item** cmdlet pode alterar o nome de um arquivo ou uma pasta, mas ele não é possível mover um item. O seguinte comando falha porque ele tenta mover o ficheiro a partir do diretório New.Directory para o diretório Temp.

```
PS> Rename-Item -Path C:\temp\New.Directory\fileOne.txt c:\temp\fileOne.txt
Rename-Item : Cannot rename because the target specified is not a path.
At line:1 char:12
+ Rename-Item  <<<< -Path C:\temp\New.Directory\fileOne c:\temp\fileOne.txt
```

## <a name="moving-items-move-item"></a>Mover itens (Move-Item)

Para mover um ficheiro ou pasta, utilize o **Move-Item** cmdlet.

Por exemplo, o seguinte comando move o diretório de New.Directory da unidade c:\\diretório temporário para a raiz da unidade c:. Para verificar que o item foi movido, inclua o **PassThru** parâmetro do **Move-Item** cmdlet. Sem **Passthru**, o **Move-Item** cmdlet não apresenta quaisquer resultados.

```
PS> Move-Item -Path C:\temp\New.Directory -Destination C:\ -PassThru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  12:14 PM            New.Directory
```

## <a name="copying-items-copy-item"></a>Copiar itens (Copy-Item)

Se estiver familiarizado com as operações de cópia de outros shells, talvez o comportamento do **Copy-Item** cmdlet no Windows PowerShell para ser invulgar. Quando copiar um item de uma localização para outra, Copy-Item não copia o conteúdo por predefinição.

Por exemplo, se copiar os **New.Directory** diretório da unidade c: à unidade c:\\diretório temporário, o comando for concluída com êxito, mas os ficheiros no diretório New.Directory não são copiados.

```powershell
Copy-Item -Path C:\New.Directory -Destination C:\temp
```

Se exibir o conteúdo do **c:\\temp\\New.Directory**, descobrirá que não contém ficheiros:

```
PS> Get-ChildItem -Path C:\temp\New.Directory
PS>
```

Por que não a **Copy-Item** cmdlet copie o conteúdo para a nova localização?

O **Copy-Item** cmdlet foi projetado para ser genérico; não é apenas para copiar ficheiros e pastas. Além disso, mesmo quando a copiar ficheiros e pastas, talvez queira copiar apenas o contentor e não os itens dentro do mesmo.

Para copiar o conteúdo inteiro de uma pasta, inclua o **Recurse** parâmetro do **Copy-Item** cmdlet no comando. Se já tiver copiado o diretório sem o seu conteúdo, adicione a **força** parâmetro, que permite-lhe substituir a pasta vazia.

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

## <a name="deleting-items-remove-item"></a>A eliminar itens (Remove-Item)

Para eliminar ficheiros e pastas, utilize o **Remove-Item** cmdlet. Cmdlets do Windows PowerShell, tal como **Remove-Item**, que pode tornar significativo, muitas vezes, irão pedir alterações irreversível confirmação quando inserir seus comandos. Por exemplo, se tentar remover a **New.Directory** pasta, será solicitado a confirmar o comando, porque a pasta contém arquivos:

```
PS> Remove-Item C:\New.Directory

Confirm
The item at C:\temp\New.Directory has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
 sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Uma vez **Sim** é a resposta padrão, para eliminar a pasta e os respetivos ficheiros, prima a **Enter** chave. Para remover a pasta sem confirmar, utilize o **-Recurse** parâmetro.

```powershell
Remove-Item C:\temp\New.Directory -Recurse
```

## <a name="executing-items-invoke-item"></a>Itens em execução (Invoke-Item)

Windows PowerShell utiliza a **Invoke-Item** cmdlet para efetuar uma ação padrão para um ficheiro ou pasta. Esta ação de predefinição é determinada pelo manipulador de aplicativo padrão no Registro; o efeito é o mesmo como se clicar duas vezes o item no Explorador de ficheiros.

Por exemplo, suponha que execute o seguinte comando:

```powershell
Invoke-Item C:\WINDOWS
```

Uma janela do Explorer que está localizada na unidade c:\\Windows é apresentada, tal como se tivesse clicar duas vezes a unidade c:\\pasta Windows.

Se invoca o **Boot. ini** arquivo num sistema antes do Windows Vista:

```powershell
Invoke-Item C:\boot.ini
```

Se o tipo de ficheiro. ini está associado com o bloco de notas, abre o ficheiro Boot. ini no bloco de notas.
