---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Método ResourceTest da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: f03a034329a9cde5cd44dbaf42ba1789c2b8f4f9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método ResourceTest da classe MSFT_DSCLocalConfigurationManager

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

*ResourceType* \[no\] o nome do recurso para chamar.

*ModuleName* \[no\] o nome do módulo que contém o recurso a chamada.

*resourceProperty* \[no\] Especifica o nome de propriedade de recursos e o respetivo valor numa tabela hash como chave e valor, respetivamente. Utilize o [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet para detetar as propriedades de recurso e os respetivos tipos.

*InDesiredState* \[saída\] no retorno, esta propriedade está definida como **verdadeiro** se o nó de destino estiver no estado pretendido.

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