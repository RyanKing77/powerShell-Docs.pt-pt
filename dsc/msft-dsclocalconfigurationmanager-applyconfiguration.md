---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Método ApplyConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ef8488246b2c8614452d32009e45535f0ff2e184
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222144"
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método ApplyConfiguration da classe MSFT_DSCLocalConfigurationManager

Utiliza o agente de configuração para aplicar a configuração que está pendente.

Se não houver nenhuma configuração pendentes, este método volta a configuração atual.


## <a name="syntax"></a>Sintaxe
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>Parâmetros
----------

*Forçar* \[no\] se este for **verdadeiro**, a configuração atual é reaplicada, mesmo se houver uma configuração pendentes.

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