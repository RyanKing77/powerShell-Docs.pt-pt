---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: cmdlet do powershell do galeria, psget
title: "Módulo de guardar"
ms.openlocfilehash: 296c5c5ffc6f1e12da0162237e562b13b3679110
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="save-module"></a><span data-ttu-id="2243e-103">Módulo de guardar</span><span class="sxs-lookup"><span data-stu-id="2243e-103">Save-Module</span></span>

<span data-ttu-id="2243e-104">Guarda um módulo localmente sem instalá-lo.</span><span class="sxs-lookup"><span data-stu-id="2243e-104">Saves a module locally without installing it.</span></span>

## <a name="description"></a><span data-ttu-id="2243e-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="2243e-105">Description</span></span>

<span data-ttu-id="2243e-106">O cmdlet do módulo de guardar guarda um módulo localmente do repositório especificado para inspecção.</span><span class="sxs-lookup"><span data-stu-id="2243e-106">The Save-Module cmdlet saves a module locally from the specified repository for inspection.</span></span> <span data-ttu-id="2243e-107">O módulo não está instalado.</span><span class="sxs-lookup"><span data-stu-id="2243e-107">The module is not installed.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="2243e-108">Sintaxe de cmdlet</span><span class="sxs-lookup"><span data-stu-id="2243e-108">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Save-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="2243e-109">Referência de ajuda online do cmdlet</span><span class="sxs-lookup"><span data-stu-id="2243e-109">Cmdlet online help reference</span></span>

[<span data-ttu-id="2243e-110">Módulo de guardar</span><span class="sxs-lookup"><span data-stu-id="2243e-110">Save-Module</span></span>](http://go.microsoft.com/fwlink/?LinkId=531351)

## <a name="example-commands"></a><span data-ttu-id="2243e-111">Comandos de exemplo</span><span class="sxs-lookup"><span data-stu-id="2243e-111">Example commands</span></span>

```powershell
Save-Module -Repository MSPSGallery -Name ModuleWithDependencies2 -Path C:\MySavedModuleLocation
dir C:\MySavedModuleLocation

Directory: C:\MySavedModuleLocation

Mode LastWriteTime Length Name
---- ------------- ------ ----
d----- 4/21/2015 5:40 PM ModuleWithDependencies2
d----- 4/21/2015 5:40 PM NestedRequiredModule1
d----- 4/21/2015 5:40 PM NestedRequiredModule2
d----- 4/21/2015 5:40 PM NestedRequiredModule3
d----- 4/21/2015 5:40 PM RequiredModule1
d----- 4/21/2015 5:40 PM RequiredModule2
d----- 4/21/2015 5:40 PM RequiredModule3


# Find a command and save its module
# This command finds the specified command, and then passes it to Save-Module to save it to the C:\temp folder.
Find-Command -Name "Get-NestedRequiredModule4" -Repository "INT" | Save-Module -Path "C:\temp\" -Verbose


# Save the role capability modules by piping the Find-RoleCapability output to Save-Module cmdlet.
Find-RoleCapability -Name Maintenance,MyJeaRole | Save-Module -Path C:\MyModulesPath

```

