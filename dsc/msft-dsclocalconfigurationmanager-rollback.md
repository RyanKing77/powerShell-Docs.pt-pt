---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Método RollBack da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: d2f9b7025d611912e119800408e25fcb66bc0228
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219883"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método RollBack da classe MSFT_DSCLocalConfigurationManager

Reverte a configuração para uma versão anterior.

<a name="syntax"></a>Sintaxe
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a>Parâmetros
----------

*configurationNumber* \[no\] Especifica a configuração solicitada.

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