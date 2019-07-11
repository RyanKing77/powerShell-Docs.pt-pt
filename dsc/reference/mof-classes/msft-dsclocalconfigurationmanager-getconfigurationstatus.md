---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método GetConfigurationStatus
ms.openlocfilehash: 83b30ba2612d962fcf2fa658d07d18fb2d91ccc7
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734504"
---
# <a name="getconfigurationstatus-method"></a>Método GetConfigurationStatus

Obter o histórico do Estado de configuração.

## <a name="syntax"></a>Sintaxe

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a>Parâmetros

*Todos os* \[na\] **verdadeiro** se esse método deve retornar informações sobre todas a configuração é executada na máquina, incluindo o aplicativo de configuração e a verificação de consistência.

*configurationStatus* \[horizontalmente\] no retorno, contém uma instância incorporada do **MSFT_DSCConfigurationStatus** classe que define as definições.

## <a name="return-value"></a>Valor de retorno

Devolve zero com êxito; caso contrário, devolve um código de erro.

## <a name="remarks"></a>Observações

Este é um método estático.

## <a name="requirements"></a>Requisitos

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Consulte também

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
