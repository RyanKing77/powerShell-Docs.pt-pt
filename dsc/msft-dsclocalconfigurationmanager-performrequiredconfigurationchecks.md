---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Método PerformRequiredConfigurationChecks da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: c3fdaa23875815b1cf5cbf0b6e21c633e00664aa
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método PerformRequiredConfigurationChecks da classe MSFT_DSCLocalConfigurationManager

Inicia uma verificação de consistência utilizando o Programador de tarefas.

<a name="syntax"></a>Sintaxe
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a>Parâmetros
----------

*Sinalizadores* \[no\] uma máscara de bits que especifica o tipo de verificação de consistência para ser executada. Os seguintes valores são válidos e podem ser combinados utilizando um bit a bit **ou** operação:

|Valor |Descrição |
|:--- |:---|
|**1** | Uma verificação de consistência normal. |
|**2** | Uma continuação de uma verificação de consistência após um reinício. Este valor não deve ser combinado com outros valores. |
|**4** | A configuração deve ser solicitada a partir do servidor de solicitação especificado na configuração meta da para o nó. Este valor deve sempre ser combinado com **1**, para um valor de **5**. |
|**8** | Envie estado para o servidor de relatórios. |

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