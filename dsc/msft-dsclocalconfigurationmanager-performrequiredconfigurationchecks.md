---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método PerformRequiredConfigurationChecks da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b92eefb7fbea6d96afa31f6b802ba10fe20d4103
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893234"
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método PerformRequiredConfigurationChecks da classe MSFT_DSCLocalConfigurationManager

Inicia uma verificação de consistência, utilizando o agendador de tarefas.

## <a name="syntax"></a>Sintaxe

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

## <a name="parameters"></a>Parâmetros

*Sinalizadores* \[no\] uma máscara de bits que especifica o tipo de verificação de consistência para ser executado. Os seguintes valores são válidos e podem ser combinados com o bit a bit **ou** operação:

|Valor |Descrição |
|:--- |:---|
|**1** | Uma verificação de consistência normal. |
|**2** | Uma continuação de uma verificação de consistência após um reinício. Este valor não deve ser combinado com outros valores. |
|**4** | A configuração deve ser puxada do servidor pull especificado no metaconfiguration para o nó. Este valor deve sempre ser combinado com **1**, para um valor de **5**. |
|**8** | Envie estado para o servidor de relatórios. |

## <a name="return-value"></a>Valor de retorno

Devolve zero com êxito; caso contrário, devolve um código de erro.

## <a name="remarks"></a>Observações

Este é um método estático.

## <a name="requirements"></a>Requisitos

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Consulte também

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)