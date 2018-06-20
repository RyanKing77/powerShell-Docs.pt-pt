---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Método ResourceGet da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 30cbaa907d4dc3a921c9e5fe61ffddc5d61c2347
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187872"
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método ResourceGet da classe MSFT_DSCLocalConfigurationManager

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

*ResourceType* \[no\] o nome do recurso para chamar.

*ModuleName* \[no\] o nome do módulo que contém o recurso a chamada.

*resourceProperty* \[no\] Especifica o nome de propriedade de recursos e o respetivo valor numa tabela hash como chave e valor, respetivamente. Utilize o [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet para detetar as propriedades de recurso e os respetivos tipos.

*configurações* \[saída\] no retorno, contém uma instância incorporada das configurações.

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