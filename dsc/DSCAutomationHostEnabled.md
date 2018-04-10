---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Chave de registo DSCAutomationHostEnabled
ms.openlocfilehash: 9fd71120b4959a7b14094922b453b05b217f3736
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
><span data-ttu-id="9fd66-103">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9fd66-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="9fd66-104">Chave de registo DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="9fd66-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="9fd66-105">DSC utiliza o **DSCAutomationHostEnabled** chave de registo em **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** para ativar a configuração da máquina em cima de arranque inicial.</span><span class="sxs-lookup"><span data-stu-id="9fd66-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="9fd66-106">DSCAutomationHostEnabled suporta três modos de:</span><span class="sxs-lookup"><span data-stu-id="9fd66-106">DSCAutomationHostEnabled supports three modes:</span></span>

|  <span data-ttu-id="9fd66-107">Valor de DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="9fd66-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="9fd66-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="9fd66-108">Description</span></span>   |
|---|---|
<span data-ttu-id="9fd66-109">0</span><span class="sxs-lookup"><span data-stu-id="9fd66-109">0</span></span> | <span data-ttu-id="9fd66-110">Desative a configurar a máquina em cima de arranque.</span><span class="sxs-lookup"><span data-stu-id="9fd66-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="9fd66-111">1</span><span class="sxs-lookup"><span data-stu-id="9fd66-111">1</span></span> | <span data-ttu-id="9fd66-112">Ative a configurar a máquina em cima de arranque.</span><span class="sxs-lookup"><span data-stu-id="9fd66-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="9fd66-113">2</span><span class="sxs-lookup"><span data-stu-id="9fd66-113">2</span></span> | <span data-ttu-id="9fd66-114">Ativar a configurar a máquina apenas se DSC está no estado pendente ou atual.</span><span class="sxs-lookup"><span data-stu-id="9fd66-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="9fd66-115">Este é o valor predefinido.</span><span class="sxs-lookup"><span data-stu-id="9fd66-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="9fd66-116">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="9fd66-116">See Also</span></span>

<span data-ttu-id="9fd66-117">Para obter um exemplo de como utilizar esta funcionalidade para executar as configurações inicial de segurança de arranque, consulte [configurar uma máquinas virtuais em cima de arranque inicial através da utilização de DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="9fd66-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>