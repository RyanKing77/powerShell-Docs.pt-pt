---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Método TestConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 2df04d317bd5e7a5c2a713d92be57c5c9a9f5e8c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219016"
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método TestConfiguration da classe MSFT_DSCLocalConfigurationManager

Envia o documento de configuração para o nó gerido e verifica a configuração atual contra o documento.

<a name="syntax"></a>Sintaxe
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a>Parâmetros
----------

*configurationData* \[no\] dados de ambiente para o confuguration.

*InDesiredState* \[saída\] no retorno, especifica se o nó gerido está num estado especificado pelo documento de configuração.

*ResourcesInDesiredState* \[saída\] no retorno, contém uma instância do embedded o **MSFT_ResourceInDesiredState** classe que especifica os recursos que estão no estado pretendido.

*ResourcesNotInDesiredState* \[saída\] no retorno, contém uma instância do embedded o **MSFT_ResourceNotInDesiredState** classe que especifica os recursos que não estão no estado pretendido.

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