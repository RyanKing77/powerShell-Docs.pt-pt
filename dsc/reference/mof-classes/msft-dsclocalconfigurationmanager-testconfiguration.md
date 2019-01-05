---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método TestConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: d746832b01310f43a7aae33dd0fa70c0928bb3e0
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048396"
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método TestConfiguration da classe MSFT_DSCLocalConfigurationManager

Envia o documento de configuração para o nó gerido e verifica a configuração atual contra o documento.

## <a name="syntax"></a>Sintaxe

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a>Parâmetros

*configurationData* \[no\] dados de ambiente para o confuguration.

*InDesiredState* \[horizontalmente\] no retorno, especifica se o nó gerido está num estado especificado pelo documento de configuração.

*ResourcesInDesiredState* \[horizontalmente\] no retorno, contém uma instância incorporada do **MSFT_ResourceInDesiredState** classe que especifica os recursos que estão no estado pretendido.

*ResourcesNotInDesiredState* \[horizontalmente\] no retorno, contém uma instância incorporada do **MSFT_ResourceNotInDesiredState** classe que especifica os recursos que não estão no estado pretendido.

## <a name="return-value"></a>Valor de retorno

Devolve zero com êxito; caso contrário, devolve um código de erro.

## <a name="remarks"></a>Observações

Este é um método estático.

## <a name="requirements"></a>Requisitos

**MOF:** DscCore.mof

**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Consulte também

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)