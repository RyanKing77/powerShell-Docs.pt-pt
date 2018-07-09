---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método RemoveConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 03555cc73da1272bdebebc3d93b26aaf8fabc18e
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892689"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método RemoveConfiguration da classe MSFT_DSCLocalConfigurationManager

Remove os ficheiros de configuração.

## <a name="syntax"></a>Sintaxe

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a>Parâmetros

*Fase* \[no\] Especifica qual documento de configuração para remover. Os seguintes valores são válidos:

|Valor |Descrição |
|:--- |:---|
|**1** | O **atual** documento de configuração (current.mof). |
|**2** | O **pendente** documento de configuração (pending.mof).  |
|**4** | O **Previous** documento de configuração (previous.mof). |

*Forçar* \[na\] **verdadeiro** para forçar a remoção da configuração.

## <a name="return-value"></a>Valor de retorno

Devolve zero com êxito; caso contrário, devolve um código de erro.

## <a name="remarks"></a>Observações

Este é um método estático.

## <a name="requirements"></a>Requisitos

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Consulte também

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)