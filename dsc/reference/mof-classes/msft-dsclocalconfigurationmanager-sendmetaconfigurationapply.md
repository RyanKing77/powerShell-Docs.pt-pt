---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método SendMetaConfigurationApply da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b372a6c0ab9d4561dcf67026275e7d3ca6aa2584
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048798"
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método SendMetaConfigurationApply da classe MSFT_DSCLocalConfigurationManager

Define as definições do Gestor de configuração Local que são utilizadas para controlar o agente de configuração.

## <a name="syntax"></a>Sintaxe

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a>Parâmetros

*ConfigurationData* \[no\] os dados de ambiente para a configuração.

*Forçar* \[na\] **verdadeiro** para forçar a configuração para parar.

## <a name="return-value"></a>Valor de retorno

Devolve zero com êxito; caso contrário, devolve um código de erro.

## <a name="remarks"></a>Observações

Este é um método estático.

## <a name="requirements"></a>Requisitos

**MOF:** DscCore.mof

**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Consulte também

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)