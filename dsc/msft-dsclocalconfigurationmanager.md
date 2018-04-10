---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 598bd7490043975d9d965c12a7337fb3475b3ded
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="msftdsclocalconfigurationmanager-class"></a>Classe MSFT_DSCLocalConfigurationManager

O Local Configuration Manager (MMC) que controla os Estados dos ficheiros de configuração e utiliza o agente de configuração para aplicar as configurações.

A seguinte sintaxe é simplificada a partir do código de objeto formato MOF (Managed) e inclui todas as propriedades herdadas.

## <a name="syntax"></a>Sintaxe
------

``` syntax
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a>Membros
-------

O **MSFT_DSCLocalConfigurationManager** classe tem os seguintes membros:

-   [Métodos] []

### <a name="methods"></a>Métodos

O **MSFT_DSCLocalConfigurationManager** classe tem estes métodos.

|Método |Descrição |
|:--- |:---|
| [ApplyConfiguration](msft-dsclocalconfigurationmanager-applyconfiguration.md)| Utiliza o agente de configuração para aplicar a configuração que está pendente.|
| [DisableDebugConfiguration](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| Desativa a depuração de recursos de DSC.|
| [EnableDebugConfiguration](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| Ativa a depuração de recursos de DSC.|
| [GetConfiguration](msft-dsclocalconfigurationmanager-getconfiguration.md)| Envia o documento de configuração para o nó gerido e utiliza o **obter** método do agente de configuração para aplicar a configuração.|
| [GetConfigurationResultOutput](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| Obtém o resultado de agente de configuração relacionados com uma tarefa específica.|
| [GetConfigurationStatus](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| Obter o histórico do Estado de configuração.|
| [GetMetaConfiguration](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| Obtém as definições de MMC que são utilizadas para controlar o agente de configuração.|
| [PerformRequiredConfigurationChecks](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| Inicia a verificação de consistência.|
| [RemoveConfiguration](msft-dsclocalconfigurationmanager-removeconfiguration.md)| Remove os ficheiros de configuração.|
| [ResourceGet](msft-dsclocalconfigurationmanager-resourceget.md)| Chamadas diretamente a **obter** método de um recurso de DSC.|
| [ResourceSet](msft-dsclocalconfigurationmanager-resourceset.md)| Chamadas diretamente a **definir** método de um recurso de DSC.|
| [ResourceTest](msft-dsclocalconfigurationmanager-resourcetest.md)| Chamadas diretamente a **teste** método de um recurso de DSC.|
| [RollBack](msft-dsclocalconfigurationmanager-rollback.md)| Rolls novamente para uma configuração anterior.|
| [SendConfiguration](msft-dsclocalconfigurationmanager-sendconfiguration.md)| Envia o documento de configuração para o nó gerido e guarda-o como uma alteração pendente.|
| [SendConfigurationApply](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| Envia o documento de configuração para o nó gerido e utiliza o agente de configuração para aplicar a configuração.|
| [SendConfigurationApplyAsync](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| Enviar o documento de configuração para o nó gerido e começar a utilizar o agente de configuração para aplicar a configuração. Utilize GetConfigurationResultOutput para obter a saída de resultado.|
| [SendMetaConfigurationApply](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| Define as definições de MMC que são utilizadas para controlar o agente de configuração.|
| [StopConfiguration](msft-dsclocalconfigurationmanager-stopconfiguration.md)| Interrompe a configuração que está em curso.|
| [TestConfiguration](msft-dsclocalconfigurationmanager-testconfiguration.md)| Envia o documento de configuração para o nó gerido e verifica a configuração atual contra o documento.|





## <a name="requirements"></a>Requisitos
------------
>**MOF:** DscCore.mof

>**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration