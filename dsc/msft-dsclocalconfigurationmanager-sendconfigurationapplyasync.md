---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de SendConfigurationApplyAsync da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: e680d510aaac097f4f0de80660274230e028ed45
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método de SendConfigurationApplyAsync da classe MSFT_DSCLocalConfigurationManager

Envia o documento de configuração no modo assíncrono para o nó gerido e utiliza o agente de configuração para aplicar a configuração.

<a name="syntax"></a>Sintaxe
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a>Parâmetros
----------

*ConfigurationData* \[in\]  
Os dados de ambiente para a configuração.

*force* \[in\]  
**Verdadeiro** para forçar a configuração para parar.

*jobId* \[in\]  
O ID da tarefa para o qual pretende enviar a configuração.

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


 

 



