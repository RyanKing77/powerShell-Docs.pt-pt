---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de ResourceGet da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 7d8b185c49778253dcb4e983ad948775c4cb0842
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método de ResourceGet da classe MSFT_DSCLocalConfigurationManager

Chamadas diretamente a **obter** método de um recurso de DSC.

<a name="syntax"></a>Sintaxe
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a>Parâmetros
----------

*ResourceType* \[no\]  
O nome do recurso para chamar.

*ModuleName* \[no\]  
O nome do módulo que contém o recurso a chamada.

*resourceProperty* \[no\]  
Especifica o nome de propriedade de recursos e o respetivo valor numa tabela hash como chave e valor, respetivamente. Utilize o [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet para detetar as propriedades de recurso e os respetivos tipos.

*configurações* \[enviados\]  
No retorno, contém uma instância incorporada das configurações.

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


 

 



