---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Método RemoveConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e0ae8a50212b70841d210d7b2d666a2855218d1a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método RemoveConfiguration da classe MSFT_DSCLocalConfigurationManager

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

*Fase* \[no\] Especifica o documento de configuração para remover. Os seguintes valores são válidos:

|Valor |Descrição |
|:--- |:---|
|**1** | O **atual** documento de configuração (current.mof). |
|**2** | O **pendente** documento de configuração (pending.mof).  |
|**4** | O **anterior** documento de configuração (previous.mof). |

*Forçar* \[no\] **verdadeiro** para forçar a remoção da configuração.

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