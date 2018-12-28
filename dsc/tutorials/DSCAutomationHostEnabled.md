---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Chave de registo DSCAutomationHostEnabled
ms.openlocfilehash: 38e3189323c39a522b2ccad89f5cfcadf5e45616
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404710"
---
><span data-ttu-id="55c8a-103">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="55c8a-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="55c8a-104">Chave de registo DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="55c8a-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="55c8a-105">DSC utiliza a **DSCAutomationHostEnabled** chave de Registro em **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** para ativar a configuração da máquina no arranque inicial.</span><span class="sxs-lookup"><span data-stu-id="55c8a-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="55c8a-106">DSCAutomationHostEnabled suporta três modos:</span><span class="sxs-lookup"><span data-stu-id="55c8a-106">DSCAutomationHostEnabled supports three modes:</span></span>

|  <span data-ttu-id="55c8a-107">Valor de DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="55c8a-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="55c8a-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="55c8a-108">Description</span></span>   |
|---|---|
<span data-ttu-id="55c8a-109">0</span><span class="sxs-lookup"><span data-stu-id="55c8a-109">0</span></span> | <span data-ttu-id="55c8a-110">Desative a configuração da máquina no arranque.</span><span class="sxs-lookup"><span data-stu-id="55c8a-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="55c8a-111">1</span><span class="sxs-lookup"><span data-stu-id="55c8a-111">1</span></span> | <span data-ttu-id="55c8a-112">Ative a configuração da máquina no arranque.</span><span class="sxs-lookup"><span data-stu-id="55c8a-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="55c8a-113">2</span><span class="sxs-lookup"><span data-stu-id="55c8a-113">2</span></span> | <span data-ttu-id="55c8a-114">Ativar a configurar a máquina apenas se DSC está no estado atual ou pendente.</span><span class="sxs-lookup"><span data-stu-id="55c8a-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="55c8a-115">Este é o valor predefinido.</span><span class="sxs-lookup"><span data-stu-id="55c8a-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="55c8a-116">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="55c8a-116">See Also</span></span>

<span data-ttu-id="55c8a-117">Para obter um exemplo de como utilizar esta funcionalidade para executar configurações no arranque inicial, consulte [configurar uma máquina virtual no arranque inicial com o DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="55c8a-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>