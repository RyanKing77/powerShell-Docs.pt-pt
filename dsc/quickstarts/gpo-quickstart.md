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
> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="quickstart-convert-group-policy-into-dsc"></a>Início rápido: Política de grupo de converter em DSC

Pode gerar uma configuração de DSC de uma linha de base da diretiva de grupo ou o Centro de segurança do Azure. O [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) módulo inclui os seguintes comandos para realizar essa tarefa.

- `ConvertFrom-GPO` -Grupo converte as políticas, armazenados como arquivos. Também pode especificar um diretório que contém várias políticas que serão combinadas numa configuração.
  - Para exportar as políticas de grupo no seu ambiente, utilize o [cópia de segurança GPO](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) cmdlet, ou siga as instruções [exportar um GPO para um ficheiro](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).
- `ConvertFrom-SCM` -Converte linhas de base do Security Compliance Manager, armazenadas como `.xml` ficheiros.
- `ConvertFrom-ASC` -Linhas de base para o Centro de segurança do Azure converte, armazenadas como `.json` ficheiros.
- `Merge-GPOs` -Grupo converte políticas aplicadas a um computador de destino.

Os cmdlets listados acima converter uma linha de base num DSC `.mof` ficheiro. Também pode optar por um script de configuração de saída (`.ps1`), que pode editar e recompilar. Os cmdlets detetar erros de compilação para recursos em falta ou blocos de recurso duplicados. Blocos de recursos que podem causar erros de compilação são comentados.

O exemplo a seguir converte um [Microsoft Security Baseline](https://www.microsoft.com/en-us/download/details.aspx?id=55319) num script de configuração do DSC (`.ps1`) e `.mof` ficheiro.

```powershell
Install-Module BaselineManagement
Import-Module BaselineManagement
ConvertFrom-GPO -Path '.\Windows 10 Version 1903 and Windows Server Version 1903 Security Baseline\GPOs\' -OutputConfigurationScript
```

Depois de executar os comandos, verá dois arquivos no diretório de "Saída" padrão criado no seu caminho atual.

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

Cada nó gerido também terá dos seguintes dois módulos:

- [SecurityPolicyDSC](https://www.powershellgallery.com/packages/SecurityPolicyDsc)
- [AuditPolicyDSC](https://www.powershellgallery.com/packages/AuditPolicyDsc)

> [!NOTE]
> **BaselineManagement** é uma solução desenvolvida pela Comunidade para fazer o DSC mais detectáveis para o suporte para soluções de Comunidade vêm de maintainers o projeto e não da Microsoft. Pode abrir um novo problema para **BaselineManagement** nos [GitHub](https://github.com/microsoft/BaselineManagement).

## <a name="next-steps"></a>Passos Seguintes

- Para carregar o script de configuração para configuração de estado de automatização do Azure, veja [introdução ao](/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).
- Adicionar a **SecurityPolicyDSC** e **AuditPolicyDSC** módulos para seu [conta de automatização](/azure/automation/shared-resources/modules).
- Localizar as configurações de DSC e os recursos a [galeria do PowerShell](https://www.powershellgallery.com/).
