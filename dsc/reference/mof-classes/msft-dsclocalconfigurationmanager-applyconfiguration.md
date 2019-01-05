---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método ApplyConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 559ff1793a18e28dad2f176bdb20eb53bc08630d
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048367"
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método ApplyConfiguration da classe MSFT_DSCLocalConfigurationManager

Utiliza o agente de configuração para aplicar a configuração que está pendente.

Se não houver nenhuma configuração pendentes, este método de volta a aplicar a configuração atual.

## <a name="syntax"></a>Sintaxe

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>Parâmetros

*Forçar* \[na\] se se tratar de **verdadeiro**, a configuração atual é reaplicada, mesmo que haja uma configuração pendentes.

## <a name="return-value"></a>Valor de retorno

Devolve zero com êxito; caso contrário, devolve um código de erro.

## <a name="remarks"></a>Observações

Este é um método estático.

## <a name="requirements"></a>Requisitos

**MOF:** DscCore.mof

**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Consulte também

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)