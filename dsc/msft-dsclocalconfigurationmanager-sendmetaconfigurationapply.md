---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Método SendMetaConfigurationApply da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 46acd86ac52b7b6b39f06fc65af2498b4f5348ed
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218846"
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método SendMetaConfigurationApply da classe MSFT_DSCLocalConfigurationManager

Define as definições do Gestor de configuração locais que são utilizadas para controlar o agente de configuração.

<a name="syntax"></a>Sintaxe
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a>Parâmetros
----------

*ConfigurationData* \[no\] os dados de ambiente para a configuração.

*Forçar* \[no\] **verdadeiro** para forçar a configuração para parar.

## <a name="return-value"></a>Valor devolvido
------------

Devolve zero com êxito; caso contrário, devolve um código de erro.

## <a name="remarks"></a>Observações

Este é um método estático.

## <a name="requirements"></a>Requisitos
------------
>**MOF:** DscCore.mof

>**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration


## <a name="see-also"></a>Consulte também


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)