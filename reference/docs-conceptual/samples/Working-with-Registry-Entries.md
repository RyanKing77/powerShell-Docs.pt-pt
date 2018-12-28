---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Trabalhar com Entradas do Registo
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: bffdf80931fc4dc570b584623487077dc5d449dc
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405373"
---
# <a name="working-with-registry-entries"></a>Trabalhar com Entradas do Registo

Uma vez que as entradas do Registro são propriedades de chaves e, assim, a não é possível diretamente ser pesquisadas, é necessário usar uma abordagem ligeiramente diferente ao trabalhar com eles.

### <a name="listing-registry-entries"></a>Entradas de registro de listagem

Existem várias formas diferentes de examinar as entradas do Registro. A forma mais simples é obter os nomes de propriedade associados com uma chave. Por exemplo, para ver os nomes das entradas na chave do registo **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion**, utilize **Get-Item** . Chaves de registo de ter uma propriedade com o nome genérico de "Property", que é uma lista de entradas de registo na chave. O seguinte comando seleciona a propriedade de propriedade e expande os itens para que eles são exibidos numa lista:

```
PS> Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion | Select-Object -ExpandProperty Property
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

Para ver as entradas de registro num formato mais legível, utilize **Get-ItemProperty**:

```
PS> Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion

PSPath              : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows\CurrentVersion
PSParentPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows
PSChildName         : CurrentVersion
PSDrive             : HKLM
PSProvider          : Microsoft.PowerShell.Core\Registry
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
CommonFilesDir      : C:\Program Files\Common Files
ProductId           : 76487-338-1167776-22465
WallPaperDir        : C:\WINDOWS\Web\Wallpaper
MediaPath           : C:\WINDOWS\Media
ProgramFilesPath    : C:\Program Files
PF_AccessoriesName  : Accessories
(default)           :
```

As propriedades relacionadas com o Windows PowerShell para a chave são todas o prefixo "PS", tal como **se PSPath**, **PSParentPath**, **PSChildName**, e **PSProvider** .

Pode usar a "**.**" notação que se refere a localização atual. Pode usar **Set-Location** para alterar para o **CurrentVersion** contentor de registo primeiro:

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Em alternativa, pode utilizar o PSDrive HKLM incorporadas com **Set-Location**:

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Em seguida, pode utilizar o "**.**" notação para a localização atual ver as propriedades sem especificar um caminho completo:

```
PS> Get-ItemProperty -Path .
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

Expansão de caminho funciona da mesma forma que funciona dentro do sistema de arquivos, para que a partir desta localização pode obter o **ItemProperty** para a listagem **HKLM:\\SOFTWARE\\Microsoft\\Windows \\Ajudar** utilizando **Get ItemProperty-caminho.... \\Ajudar**.

### <a name="getting-a-single-registry-entry"></a>Obter uma entrada de registo único

Se quiser obter uma entrada específica numa chave de registo, pode utilizar uma das várias abordagens possíveis. Neste exemplo encontra o valor de **DevicePath** na **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.

Usando **Get-ItemProperty**, utilize o **caminho** parâmetro para especificar o nome da chave e o **nome** parâmetro para especificar o nome do **DevicePath** entrada.

```
PS> Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath

PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

Este comando devolve as propriedades padrão do Windows PowerShell, bem como a **DevicePath** propriedade.

> [!NOTE]
> Embora **Get-ItemProperty** tem **filtro**, **incluir**, e **excluir** parâmetros, não pode ser utilizados para filtrar por nome de propriedade. Estes parâmetros referir-se para chaves do Registro — que são os caminhos de item — e não as entradas de Registro — que são propriedades do item.

Outra opção é usar a ferramenta de linha de comandos Reg.exe. Para obter ajuda com reg.exe, escreva **reg.exe /?** no prompt de comando. Para localizar a entrada de DevicePath, utilize reg.exe, conforme mostrado no comando seguinte:

```
PS> reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath

! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

Também pode utilizar o **WshShell COM** objeto também para encontrar algumas entradas no Registro, embora esse método não funciona com dados binários grandes ou com os nomes de entrada do Registro que incluem caracteres como "\\"). Acrescentar o nome de propriedade para o caminho de item com um \\ separador:

```
PS> (New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
%SystemRoot%\inf
```

### <a name="creating-new-registry-entries"></a>Criar novas entradas de registo

Para adicionar uma nova entrada com o nome "PowerShellPath" para o **CurrentVersion** chave, use **New-ItemProperty** com o caminho para a chave, o nome de entrada e o valor da entrada. Neste exemplo, vamos o valor da variável do Windows PowerShell **$PSHome**, que armazena o caminho para o diretório de instalação para o Windows PowerShell.

Pode adicionar a nova entrada à chave, utilizando o comando seguinte e o comando também retorna informações sobre a nova entrada:

```
PS> New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome

PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

O **PropertyType** tem de ser o nome de um **Microsoft.Win32.RegistryValueKind** membro da enumeração da tabela seguinte:

|Valor de PropertyType|Significado|
|----------------------|-----------|
|Binário|Dados binários|
|DWord|Um número que é um UInt32 válido|
|ExpandString|Uma cadeia de caracteres que pode conter variáveis de ambiente que são expandidas dinamicamente|
|MultiString|Uma cadeia de caracteres com várias linhas|
|Cadeia|Qualquer valor de cadeia|
|QWord|8 bytes de dados binários|

> [!NOTE]
> Pode adicionar uma entrada de registo em várias localizações, especificando uma matriz de valores para o **caminho** parâmetro:

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

Também pode substituir um valor de entrada de registo já existentes ao adicionar o **força** parâmetro para qualquer **New-ItemProperty** comando.

### <a name="renaming-registry-entries"></a>Mudar o nome de entradas de registro

Para mudar o nome a **PowerShellPath** entrada de "PSHome", utilize **Rename-ItemProperty**:

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

Para apresentar o valor de nome mudado, adicione a **PassThru** parâmetro para o comando.

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a>A eliminar entradas de registro

Para eliminar o PSHome e PowerShellPath entradas de registo, utilize **Remove-ItemProperty**:

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```