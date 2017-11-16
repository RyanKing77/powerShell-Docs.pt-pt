---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de ResourceTest da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 73d7d543505a3768a0660084345d3858e055514f
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método de ResourceTest da classe MSFT_DSCLocalConfigurationManager

Chamadas diretamente a **teste** método de um recurso de DSC.

<a name="syntax"></a>Sintaxe
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
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

*InDesiredState* \[enviados\]  
No retorno, esta propriedade está definida como **verdadeiro** se o nó de destino estiver no estado pretendido.

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


 

 



