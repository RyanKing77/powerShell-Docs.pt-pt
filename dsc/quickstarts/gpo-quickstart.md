---
ms.date: 07/09/2019
keywords: DSC, gpo, powershell, configuração, a configuração
title: Início rápido - política de grupo de converter em DSC
ms.openlocfilehash: 8c89dbbce5b2b146194b799d7e36ecce3105bfeb
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67785139"
---
> <span data-ttu-id="b4088-103">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b4088-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="quickstart-convert-group-policy-into-dsc"></a><span data-ttu-id="b4088-104">Início rápido: Política de grupo de converter em DSC</span><span class="sxs-lookup"><span data-stu-id="b4088-104">Quickstart: Convert Group Policy into DSC</span></span>

<span data-ttu-id="b4088-105">Pode gerar uma configuração de DSC de uma linha de base da diretiva de grupo ou o Centro de segurança do Azure.</span><span class="sxs-lookup"><span data-stu-id="b4088-105">You can generate a DSC configuration from a Group Policy or Azure Security Center baseline.</span></span> <span data-ttu-id="b4088-106">O [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) módulo inclui os seguintes comandos para realizar essa tarefa.</span><span class="sxs-lookup"><span data-stu-id="b4088-106">The [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) module includes the following commands for accomplishing this task.</span></span>

- <span data-ttu-id="b4088-107">`ConvertFrom-GPO` -Grupo converte as políticas, armazenados como arquivos.</span><span class="sxs-lookup"><span data-stu-id="b4088-107">`ConvertFrom-GPO` - Converts Group Policies, stored as files.</span></span> <span data-ttu-id="b4088-108">Também pode especificar um diretório que contém várias políticas que serão combinadas numa configuração.</span><span class="sxs-lookup"><span data-stu-id="b4088-108">You can also specify a directory containing multiple policies that will be combined into one Configuration.</span></span>
  - <span data-ttu-id="b4088-109">Para exportar as políticas de grupo no seu ambiente, utilize o [cópia de segurança GPO](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) cmdlet, ou siga as instruções [exportar um GPO para um ficheiro](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).</span><span class="sxs-lookup"><span data-stu-id="b4088-109">To export Group Policies in your environment, use the [Backup-GPO](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) cmdlet, or follow the instructions in [Export a GPO to a File](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).</span></span>
- <span data-ttu-id="b4088-110">`ConvertFrom-SCM` -Converte linhas de base do Security Compliance Manager, armazenadas como `.xml` ficheiros.</span><span class="sxs-lookup"><span data-stu-id="b4088-110">`ConvertFrom-SCM` - Converts Security Compliance Manager baselines, stored as `.xml` files.</span></span>
- <span data-ttu-id="b4088-111">`ConvertFrom-ASC` -Linhas de base para o Centro de segurança do Azure converte, armazenadas como `.json` ficheiros.</span><span class="sxs-lookup"><span data-stu-id="b4088-111">`ConvertFrom-ASC` - Converts Azure Security Center baselines, stored as `.json` files.</span></span>
- <span data-ttu-id="b4088-112">`Merge-GPOs` -Grupo converte políticas aplicadas a um computador de destino.</span><span class="sxs-lookup"><span data-stu-id="b4088-112">`Merge-GPOs` - Converts Group Policies applied to a target computer.</span></span>

<span data-ttu-id="b4088-113">Os cmdlets listados acima converter uma linha de base num DSC `.mof` ficheiro.</span><span class="sxs-lookup"><span data-stu-id="b4088-113">The cmdlets listed above convert a baseline into a DSC `.mof` file.</span></span> <span data-ttu-id="b4088-114">Também pode optar por um script de configuração de saída (`.ps1`), que pode editar e recompilar.</span><span class="sxs-lookup"><span data-stu-id="b4088-114">You can also choose to output a Configuration script (`.ps1`), that you can edit and recompile.</span></span> <span data-ttu-id="b4088-115">Os cmdlets detetar erros de compilação para recursos em falta ou blocos de recurso duplicados.</span><span class="sxs-lookup"><span data-stu-id="b4088-115">The cmdlets detect compilation errors for missing resources, or duplicate resource blocks.</span></span> <span data-ttu-id="b4088-116">Blocos de recursos que podem causar erros de compilação são comentados.</span><span class="sxs-lookup"><span data-stu-id="b4088-116">Resource blocks that would cause compilation errors are commented out.</span></span>

<span data-ttu-id="b4088-117">O exemplo a seguir converte um [Microsoft Security Baseline](https://www.microsoft.com/en-us/download/details.aspx?id=55319) num script de configuração do DSC (`.ps1`) e `.mof` ficheiro.</span><span class="sxs-lookup"><span data-stu-id="b4088-117">The following example converts a [Microsoft Security Baseline](https://www.microsoft.com/en-us/download/details.aspx?id=55319) into a DSC configuration script (`.ps1`) and `.mof` file.</span></span>

```powershell
Install-Module BaselineManagement
Import-Module BaselineManagement
ConvertFrom-GPO -Path '.\Windows 10 Version 1903 and Windows Server Version 1903 Security Baseline\GPOs\' -OutputConfigurationScript
```

<span data-ttu-id="b4088-118">Depois de executar os comandos, verá dois arquivos no diretório de "Saída" padrão criado no seu caminho atual.</span><span class="sxs-lookup"><span data-stu-id="b4088-118">After running the commands, you see two files in the default "Output" directory created under your current path.</span></span>

```powershell
Get-ChildItem -Path .\Output
```

```Output
    Directory:  C:\Temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----         7/9/2019   9:35 AM   227.37KB DSCFromGPO.ps1
-a----         7/9/2019   9:35 AM   410.03KB localhost.mof
```

<span data-ttu-id="b4088-119">Cada nó gerido também terá dos seguintes dois módulos:</span><span class="sxs-lookup"><span data-stu-id="b4088-119">Each managed node will also need the following two modules:</span></span>

- [<span data-ttu-id="b4088-120">SecurityPolicyDSC</span><span class="sxs-lookup"><span data-stu-id="b4088-120">SecurityPolicyDSC</span></span>](https://www.powershellgallery.com/packages/SecurityPolicyDsc)
- [<span data-ttu-id="b4088-121">AuditPolicyDSC</span><span class="sxs-lookup"><span data-stu-id="b4088-121">AuditPolicyDSC</span></span>](https://www.powershellgallery.com/packages/AuditPolicyDsc)

> [!NOTE]
> <span data-ttu-id="b4088-122">**BaselineManagement** é uma solução desenvolvida pela Comunidade para fazer o DSC mais detectáveis para o suporte para soluções de Comunidade vêm de maintainers o projeto e não da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b4088-122">**BaselineManagement** is a solution developed by the community to make DSC more discoverable for Support for community solutions come from the project maintainers and not from Microsoft.</span></span> <span data-ttu-id="b4088-123">Pode abrir um novo problema para **BaselineManagement** nos [GitHub](https://github.com/microsoft/BaselineManagement).</span><span class="sxs-lookup"><span data-stu-id="b4088-123">You can open a new issue for **BaselineManagement** on [GitHub](https://github.com/microsoft/BaselineManagement).</span></span>

## <a name="next-steps"></a><span data-ttu-id="b4088-124">Passos Seguintes</span><span class="sxs-lookup"><span data-stu-id="b4088-124">Next steps</span></span>

- <span data-ttu-id="b4088-125">Para carregar o script de configuração para configuração de estado de automatização do Azure, veja [introdução ao](/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).</span><span class="sxs-lookup"><span data-stu-id="b4088-125">To upload your configuration script into Azure Automation State Configuration, see [Getting Started](/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).</span></span>
- <span data-ttu-id="b4088-126">Adicionar a **SecurityPolicyDSC** e **AuditPolicyDSC** módulos para seu [conta de automatização](/azure/automation/shared-resources/modules).</span><span class="sxs-lookup"><span data-stu-id="b4088-126">Add the **SecurityPolicyDSC** and **AuditPolicyDSC** modules to your [Automation Account](/azure/automation/shared-resources/modules).</span></span>
- <span data-ttu-id="b4088-127">Localizar as configurações de DSC e os recursos a [galeria do PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="b4088-127">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
