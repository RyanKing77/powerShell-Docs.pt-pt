---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 7f6aaf209601e99b0120407eb301d32fcfda9eb8
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405226"
---
# <a name="msftdsclocalconfigurationmanager-class"></a>Classe MSFT_DSCLocalConfigurationManager

O Local Configuration Manager (LCM) que controla os Estados dos arquivos de configuração e utiliza o agente de configuração para aplicar as configurações.

A seguinte sintaxe é simplificada a partir do código de formato MOF (Managed Object) e inclui todas as propriedades herdadas.

## <a name="syntax"></a>Sintaxe

```
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a>Membros

O **MSFT_DSCLocalConfigurationManager** classe tem os seguintes membros:

- [Métodos] []

### <a name="methods"></a>Métodos

O **MSFT_DSCLocalConfigurationManager** classe tem esses métodos.

|Método |Descrição |
|:--- |:---|
| [ApplyConfiguration](msft-dsclocalconfigurationmanager-applyconfiguration.md)| Utiliza o agente de configuração para aplicar a configuração que está pendente.|
| [DisableDebugConfiguration](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| Desativa a depuração de recursos de DSC.|
| [EnableDebugConfiguration](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| Permite a depuração de recursos de DSC.|
| [GetConfiguration](msft-dsclocalconfigurationmanager-getconfiguration.md)| Envia o documento de configuração para o nó gerido e utiliza a **obter** método do agente de configuração para aplicar a configuração.|
| [GetConfigurationResultOutput](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| Obtém o resultado de agente de configuração relacionadas com uma tarefa específica.|
| [GetConfigurationStatus](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| Obter o histórico do Estado de configuração.|
| [Getconfigurationstatus](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| Obtém as definições de LCM que são utilizadas para controlar o agente de configuração.|
| [PerformRequiredConfigurationChecks](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| Inicia a verificação de consistência.|
| [RemoveConfiguration](msft-dsclocalconfigurationmanager-removeconfiguration.md)| Remove os ficheiros de configuração.|
| [ResourceGet](msft-dsclocalconfigurationmanager-resourceget.md)| Chama diretamente a **obter** método de um recurso de DSC.|
| [ResourceSet](msft-dsclocalconfigurationmanager-resourceset.md)| Chama diretamente a **definir** método de um recurso de DSC.|
| [ResourceTest](msft-dsclocalconfigurationmanager-resourcetest.md)| Chama diretamente a **teste** método de um recurso de DSC.|
| [Reversão](msft-dsclocalconfigurationmanager-rollback.md)| Rolls novamente para uma configuração anterior.|
| [SendConfiguration](msft-dsclocalconfigurationmanager-sendconfiguration.md)| Envia o documento de configuração para o nó gerido e o salva como uma alteração pendente.|
| [SendConfigurationApply](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| Envia o documento de configuração para o nó gerido e utiliza o agente de configuração para aplicar a configuração.|
| [SendConfigurationApplyAsync](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| Enviar o documento de configuração para o nó gerido e começar a utilizar o agente de configuração para aplicar a configuração. Utilize GetConfigurationResultOutput para obter a saída do resultado.|
| [SendMetaConfigurationApply](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| Define as definições de LCM que são utilizadas para controlar o agente de configuração.|
| [StopConfiguration](msft-dsclocalconfigurationmanager-stopconfiguration.md)| Interrompe a configuração que está em curso.|
| [TestConfiguration](msft-dsclocalconfigurationmanager-testconfiguration.md)| Envia o documento de configuração para o nó gerido e verifica a configuração atual contra o documento.|

## <a name="requirements"></a>Requisitos

**MOF:** DscCore.mof

**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration