---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Método SendConfiguration da classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 3529bc56ecba19ed0fbbf070a4e86d0692824d39
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404650"
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="8d928-103">Método SendConfiguration da classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="8d928-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="8d928-104">Envia o documento de configuração para o nó gerido e o salva como uma alteração pendente.</span><span class="sxs-lookup"><span data-stu-id="8d928-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="8d928-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8d928-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="8d928-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8d928-106">Parameters</span></span>

<span data-ttu-id="8d928-107">*ConfigurationData* \[no\] os dados de ambiente para a configuração.</span><span class="sxs-lookup"><span data-stu-id="8d928-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="8d928-108">*Forçar* \[na\] **verdadeiro** para forçar a configuração para parar.</span><span class="sxs-lookup"><span data-stu-id="8d928-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="8d928-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8d928-109">Return value</span></span>

<span data-ttu-id="8d928-110">Devolve zero com êxito; caso contrário, devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="8d928-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8d928-111">Observações</span><span class="sxs-lookup"><span data-stu-id="8d928-111">Remarks</span></span>

<span data-ttu-id="8d928-112">Este é um método estático.</span><span class="sxs-lookup"><span data-stu-id="8d928-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8d928-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8d928-113">Requirements</span></span>

<span data-ttu-id="8d928-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="8d928-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="8d928-115">**Espaço de nomes**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="8d928-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="8d928-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d928-116">See also</span></span>

[<span data-ttu-id="8d928-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="8d928-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)