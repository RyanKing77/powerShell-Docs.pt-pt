---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Trabalhar com Entradas do Registo
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: bffdf80931fc4dc570b584623487077dc5d449dc
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952380"
---
# <a name="working-with-registry-entries"></a>Trabalhar com Entradas do Registo

Uma vez que as entradas de registo são propriedades de chaves e, como tal, a não é possível diretamente ser navegadas, precisamos de adotar uma abordagem ligeiramente diferente, ao trabalhar com eles.

### <a name="listing-registry-entries"></a>Listar as entradas de registo

Existem muitas formas diferentes de examinar as entradas de registo. É a forma mais simples para obter os nomes de propriedade associados uma chave. Por exemplo, para ver os nomes de entradas na chave do registo **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion**, utilize **Get-Item** . As chaves de registo tem uma propriedade com o nome genérico "Property" de que é uma lista de entradas de registo na chave. O seguinte comando seleciona a propriedade de propriedade e expande os itens de modo a que são apresentadas numa lista:

```
PS> Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion | Select-Object -ExpandProperty Property
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

Para ver as entradas do registo num formato mais legível, utilize **Get-ItemProperty**:

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

As propriedades relacionadas com o Windows PowerShell para a chave estão todos o prefixo "PS", tal como **PSPath**, **PSParentPath**, **PSChildName**, e **PSProvider** .

Pode utilizar o "**.**" notação para referir-se para a localização atual. Pode utilizar **Set-Location** para alterar para o **CurrentVersion** contentor registo primeiro:

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Em alternativa, pode utilizar o PSDrive HKLM incorporada com **Set-Location**:

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

Expansão de caminho funciona da mesma, como sistema de ficheiros, pelo que a partir desta localização pode obter o **ItemProperty** listagem para **HKLM:\\SOFTWARE\\Microsoft\\Windows \\Ajudar** utilizando **Get ItemProperty-caminho... \\Ajudar**.

### <a name="getting-a-single-registry-entry"></a>Obter uma entrada de registo único

Se pretender obter uma entrada específica uma chave de registo, pode utilizar uma das várias abordagens possíveis. Neste exemplo localiza o valor de **DevicePath** no **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.

Utilizando **Get-ItemProperty**, utilize o **caminho** parâmetro para especificar o nome da chave e o **nome** parâmetro para especificar o nome do **DevicePath** entrada.

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

Este comando devolve as propriedades padrão do Windows PowerShell, bem como o **DevicePath** propriedade.

> [!NOTE]
> Embora **Get-ItemProperty** tem **filtro**, **incluir**, e **excluir** parâmetros, não pode ser utilizados para filtrar por nome de propriedade. Estes parâmetros, consulte a chaves de registo-que são caminhos de item — e não as entradas de registo — que são propriedades do item.

Outra opção consiste em utilizar a ferramenta de linha de comandos Reg.exe. Para obter ajuda com reg.exe, escreva **reg.exe /?** numa linha de comandos. Para localizar a entrada de DevicePath, utilize reg.exe conforme mostrado no comando seguinte:

```
PS> reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath

! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

Também pode utilizar o **WshShell COM** objeto, bem como ao localizar algumas entradas de registo, apesar deste método não funciona com grandes dados binários ou com os nomes de entradas de registo que incluam carateres como "\\"). Acrescentar o nome de propriedade para o caminho de item com um \\ separador:

```
PS> (New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
%SystemRoot%\inf
```

### <a name="creating-new-registry-entries"></a>Criar novas entradas de registo

Para adicionar uma nova entrada com o nome "PowerShellPath" para o **CurrentVersion** utilização da chave, **New-ItemProperty** com o caminho para a chave, o nome de entrada e o valor da entrada. Neste exemplo, iremos irá demorar o valor da variável do Windows PowerShell **$PSHome**, que armazena o caminho para o diretório de instalação para o Windows PowerShell.

Pode adicionar a nova entrada para a chave, utilizando o seguinte comando e o comando também devolve informações sobre a nova entrada:

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

O **PropertyType** tem de ser o nome de um **Microsoft.Win32.RegistryValueKind** membro de enumeração da tabela seguinte:

|PropertyType valor|Significado|
|----------------------|-----------|
|Binário|Dados binários|
|DWord|Um número que é um UInt32 válido|
|ExpandString|Uma cadeia que pode conter variáveis de ambiente que são expandidas dinamicamente|
|FixedLength|Uma cadeia com várias linhas|
|Cadeia|Qualquer valor de cadeia|
|QWord|8 bytes de dados binários|

> [!NOTE]
> Pode adicionar uma entrada de registo em várias localizações, especificando uma matriz de valores para o **caminho** parâmetro:

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

Também pode substituir um valor de entrada de registo pré-existente adicionando o **Force** parâmetro a qualquer **New-ItemProperty** comando.

### <a name="renaming-registry-entries"></a>Mudar o nome de entradas de registo

Para mudar o nome de **PowerShellPath** entrada para "PSHome", utilize **ItemProperty de mudança de nome**:

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

Para apresentar o valor cujo nome foi alterado, adicione o **PassThru** parâmetro para o comando.

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a>Eliminar entradas de registo

Para eliminar as entradas de registo PSHome tanto PowerShellPath, utilize **remover ItemProperty**:

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```