---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Método de TestConfiguration da classe MSFT_DSCLocalConfigurationManager"
ms.openlocfilehash: 04f0f3146473dc71f492086449d9dce5467c55db
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método de TestConfiguration da classe MSFT_DSCLocalConfigurationManager

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

*configurationData* \[in\]  
Dados de ambiente para o confuguration.

*InDesiredState* \[out\]  
No retorno, especifica se o nó gerido está num estado especificado pelo documento de configuração.

*ResourcesInDesiredState* \[out\]  
No retorno, contém uma instância do embedded o **MSFT_ResourceInDesiredState** classe que especifica os recursos que estão no estado pretendido.

*ResourcesNotInDesiredState* \[out\]  
No retorno, contém uma instância do embedded o **MSFT_ResourceNotInDesiredState** classe que especifica os recursos que não estão no estado pretendido.

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


 

 



