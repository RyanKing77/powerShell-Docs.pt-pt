---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de RemoveConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: fed45836293adedbce18f01cfe53cdfa1a474975
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método de RemoveConfiguration da classe MSFT_DSCLocalConfigurationManager

Remove os ficheiros de configuração.

<a name="syntax"></a>Sintaxe
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a>Parâmetros
----------

*Stage* \[in\]  
Especifica o documento de configuração para remover. Os seguintes valores são válidos:

|Valor |Descrição |
|:--- |:---|
|**1** | O **atual** documento de configuração (current.mof). |
|**2** | O **pendente** documento de configuração (pending.mof).  |
|**4** | O **anterior** documento de configuração (previous.mof). |

*Force* \[in\]  
**Verdadeiro** para forçar a remoção da configuração.

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


 

 



