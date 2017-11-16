---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: cmdlet do powershell do galeria, psget
title: Script de guardar
ms.openlocfilehash: 7b692d33e3f86a89505b8d37c0da4177f3dff2c2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="save-script"></a>Script de guardar

Script de guardar cmdlet permite-lhe para rever o ficheiro de script ao guardá-lo numa localização especificada.

## <a name="description"></a>Descrição

O cmdlet de Script de guardar guarda o script especificado.

## <a name="cmdlet-syntax"></a>Sintaxe de cmdlet

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a>Referência de ajuda online do cmdlet

[Script de guardar](http://go.microsoft.com/fwlink/?LinkId=619786)

## <a name="example-commands"></a>Comandos de exemplo

### <a name="example-1-save-a-script-from-a-repository"></a>Exemplo 1: Guardar um script de um repositório
Este comando guarda a versão mais recente do script Fabrikam-ClientScript GalleryINT repositório para a pasta local C:\ScriptSharingDemo

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### <a name="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet"></a>Exemplo 2: Guardar uma versão de um script por piping a partir do cmdlet localizar Script

O primeiro comando localiza a versão 1.5 da Fabrikam-ClientScript do repositório GalleryINT e guarda-o para a pasta C:\ScriptSharingDemo

O segundo comando valida os metadados de script guardado.

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

