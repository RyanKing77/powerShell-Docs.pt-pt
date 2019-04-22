---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Trabalhar com Entradas do Registo
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: 667d17d0d62745a27ffef5f1912336b72f74c2a9
ms.sourcegitcommit: 17ce42f97e13e8b3286779dc3f583474b0357023
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/18/2019
ms.locfileid: "59293083"
---
# <a name="working-with-registry-entries"></a>Trabalhar com Entradas do Registo

Uma vez que as entradas do Registro são propriedades de chaves e, assim, a não é possível diretamente ser pesquisadas, é necessário usar uma abordagem ligeiramente diferente ao trabalhar com eles.

## <a name="listing-registry-entries"></a>Entradas de registro de listagem

Existem várias formas diferentes de examinar as entradas do Registro. A forma mais simples é obter os nomes de propriedade associados com uma chave. Por exemplo, para ver os nomes das entradas na chave do registo `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, utilize `Get-Item`. Chaves de registo de ter uma propriedade com o nome genérico de "Property", que é uma lista de entradas de registo na chave.
O seguinte comando seleciona a propriedade de propriedade e expande os itens para que eles são exibidos numa lista:

```powershell
Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion |
  Select-Object -ExpandProperty Property
```

```Output
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

Para ver as entradas de registro num formato mais legível, utilize `Get-ItemProperty`:

```powershell
Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

```Output
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

Pode utilizar o `*.*` notação que se refere a localização atual. Pode usar `Set-Location` para alterar para o **CurrentVersion** contentor de registo primeiro:

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Em alternativa, pode utilizar o PSDrive HKLM incorporadas com `Set-Location`:

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Em seguida, pode utilizar o `*.*` notação para a localização atual ver as propriedades sem especificar um caminho completo:

```powershell
Get-ItemProperty -Path .
```

```Output
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

Expansão de caminho funciona da mesma forma que funciona dentro do sistema de arquivos, para que a partir desta localização pode obter o **ItemProperty** para a listagem `HKLM:\SOFTWARE\Microsoft\Windows\Help` utilizando `Get-ItemProperty -Path ..\Help`.

## <a name="getting-a-single-registry-entry"></a>Obter uma entrada de registo único

Se quiser obter uma entrada específica numa chave de registo, pode utilizar uma das várias abordagens possíveis. Neste exemplo encontra o valor de **DevicePath** no `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.

Usando `Get-ItemProperty`, utilize o **caminho** parâmetro para especificar o nome da chave e o **nome** parâmetro para especificar o nome da **DevicePath** entrada.

```powershell
Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath
```

```Output
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
> Embora `Get-ItemProperty` tem **filtro**, **incluir**, e **excluir** parâmetros, não pode ser utilizados para filtrar por nome de propriedade. Consulte estes parâmetros para chaves de registro, que são os caminhos de item e não as entradas de Registro. Entradas de registo que são propriedades do item.

Outra opção é usar a ferramenta de linha de comandos Reg.exe. Para obter ajuda com reg.exe, escreva `reg.exe /?` no prompt de comando. Para localizar a entrada de DevicePath, utilize reg.exe, conforme mostrado no comando seguinte:

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

Também pode utilizar o **WshShell** objeto de COM também encontrar algumas entradas no Registro, embora esse método não funciona com dados binários grandes ou com os nomes de entrada do Registro que incluem caracteres como "\\"). Acrescentar o nome de propriedade para o caminho de item com um \\ separador:

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

## <a name="setting-a-single-registry-entry"></a>Definir uma entrada de registo único

Se quiser alterar uma entrada específica numa chave de registo, pode utilizar uma das várias abordagens possíveis. Neste exemplo modifica os **caminho** entrada sob `HKEY_CURRENT_USER\Environment`. O **caminho** entrada especifica onde encontrar arquivos executáveis.

1. Recuperar o valor atual do **caminho** usando entrada `Get-ItemProperty`.
2. Adicionar o novo valor, separá-lo com um `;`.
3. Utilize `Set-ItemProperty` com o nome da chave, o nome de entrada e o valor para modificar a entrada de registo.

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> Embora `Set-ItemProperty` tem **filtro**, **incluir**, e **excluir** parâmetros, não pode ser utilizados para filtrar por nome de propriedade. Estes parâmetros referir-se para chaves do Registro — que são os caminhos de item — e não as entradas de Registro — que são propriedades do item.

Outra opção é usar a ferramenta de linha de comandos Reg.exe. Para obter ajuda com reg.exe, escreva **reg.exe /?**
no prompt de comando.

As seguintes alterações de exemplo da **caminho** entrada ao remover o caminho adicionado no exemplo acima.
`Get-ItemProperty` ainda é usado para recuperar o valor atual para evitar ter de analisar a cadeia de caracteres retornada de `reg query`. O **subcadeia** e **LastIndexOf** métodos são usados para recuperar o caminho do último adicionado para o **caminho** entrada.

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

## <a name="creating-new-registry-entries"></a>Criar novas entradas de registo

Para adicionar uma nova entrada com o nome "PowerShellPath" para o **CurrentVersion** utilização de chaves, `New-ItemProperty` com o caminho para a chave, o nome de entrada e o valor da entrada. Neste exemplo, vamos o valor da variável do Windows PowerShell `$PSHome`, que armazena o caminho para o diretório de instalação para o Windows PowerShell.

Pode adicionar a nova entrada à chave, utilizando o comando seguinte e o comando também retorna informações sobre a nova entrada:

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

```Output
PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows
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
|Cadeia (de carateres)|qualquer valor de cadeia|
|QWord|8 bytes de dados binários|

> [!NOTE]
> Pode adicionar uma entrada de registo em várias localizações, especificando uma matriz de valores para o **caminho** parâmetro:

```powershell
New-ItemProperty -Name PowerShellPath -PropertyType String -Value $PSHome `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Também pode substituir um valor de entrada de registo já existentes ao adicionar o **força** parâmetro para qualquer `New-ItemProperty` comando.

## <a name="renaming-registry-entries"></a>Mudar o nome de entradas de registro

Para mudar o nome da **PowerShellPath** entrada de "PSHome", utilize `Rename-ItemProperty`:

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

Para apresentar o valor de nome mudado, adicione a **PassThru** parâmetro para o comando.

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

## <a name="deleting-registry-entries"></a>A eliminar entradas de registro

Para eliminar o PSHome e PowerShellPath entradas de registo, utilize `Remove-ItemProperty`:

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
