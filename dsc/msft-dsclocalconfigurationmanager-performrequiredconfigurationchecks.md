---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de PerformRequiredConfigurationChecks da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 26110b3920104da7343b8d55cf63440c12accbbc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método de PerformRequiredConfigurationChecks da classe MSFT_DSCLocalConfigurationManager

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

*Sinalizadores* \[no\]  
Uma máscara de bits que especifica o tipo de verificação de consistência para ser executada. Os seguintes valores são válidos e podem ser combinados utilizando um bit a bit **ou** operação:

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

>**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration


## <a name="see-also"></a>Consulte também


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)


 

 



