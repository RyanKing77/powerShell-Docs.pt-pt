---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Método GetConfigurationStatus da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ebf2b65f152c622ccf42e12545b0048a0b96d963
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método GetConfigurationStatus da classe MSFT_DSCLocalConfigurationManager

Obtém as definições de Configuration Manager local que são utilizadas para controlar o agente de configuração.

<a name="syntax"></a>Sintaxe
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a>Parâmetros
----------

*Configuração meta do* \[saída\] no retorno, contém uma instância do embedded o **MSFT_DSCMetaConfiguration** classe que define as definições.

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