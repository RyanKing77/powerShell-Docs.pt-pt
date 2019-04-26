---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Chave de registo DSCAutomationHostEnabled
ms.openlocfilehash: 2bccd2738b9f61efd656fdf0f98cf71affdbe781
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076498"
---
><span data-ttu-id="eb948-103">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="eb948-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="eb948-104">Chave de registo DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="eb948-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="eb948-105">DSC utiliza a **DSCAutomationHostEnabled** chave de Registro em **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** para ativar a configuração da máquina em inicial arranque-up.</span><span class="sxs-lookup"><span data-stu-id="eb948-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="eb948-106">**DSCAutomationHostEnabled** suporta três modos:</span><span class="sxs-lookup"><span data-stu-id="eb948-106">**DSCAutomationHostEnabled** supports three modes:</span></span>

|  <span data-ttu-id="eb948-107">Valor de DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="eb948-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="eb948-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="eb948-108">Description</span></span>   |
|---|---|
<span data-ttu-id="eb948-109">0</span><span class="sxs-lookup"><span data-stu-id="eb948-109">0</span></span> | <span data-ttu-id="eb948-110">Desative a configuração da máquina no arranque.</span><span class="sxs-lookup"><span data-stu-id="eb948-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="eb948-111">1</span><span class="sxs-lookup"><span data-stu-id="eb948-111">1</span></span> | <span data-ttu-id="eb948-112">Ative a configuração da máquina no arranque.</span><span class="sxs-lookup"><span data-stu-id="eb948-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="eb948-113">2</span><span class="sxs-lookup"><span data-stu-id="eb948-113">2</span></span> | <span data-ttu-id="eb948-114">Ativar a configurar a máquina apenas se DSC está no estado atual ou pendente.</span><span class="sxs-lookup"><span data-stu-id="eb948-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="eb948-115">Este é o valor predefinido.</span><span class="sxs-lookup"><span data-stu-id="eb948-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="eb948-116">Veja Também</span><span class="sxs-lookup"><span data-stu-id="eb948-116">See Also</span></span>

<span data-ttu-id="eb948-117">Para obter um exemplo de como utilizar esta funcionalidade para executar configurações no arranque inicial, consulte [configurar uma máquina virtual no arranque inicial com o DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="eb948-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>
