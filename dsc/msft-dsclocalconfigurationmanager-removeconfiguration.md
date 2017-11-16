---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de RemoveConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: faa113c442b80eea3ac474220b098b7d80ec50a8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método de RemoveConfiguration da classe MSFT_DSCLocalConfigurationManager

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

*Fase* \[no\]  
Especifica o documento de configuração para remover. Os seguintes valores são válidos:

|Valor |Descrição |
|:--- |:---|
|**1** | O **atual** documento de configuração (current.mof). |
|**2** | O **pendente** documento de configuração (pending.mof).  |
|**4** | O **anterior** documento de configuração (previous.mof). |

*Force* \[no\]  
**Verdadeiro** para forçar a remoção da configuração.

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


 

 



