---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 28f4f8ae2bbddc8fb5ef9d95d3061a91fcc8ffe2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058731"
---
# <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a><span data-ttu-id="3e9ba-102">Permitindo para recursos duplicados idênticos numa configuração</span><span class="sxs-lookup"><span data-stu-id="3e9ba-102">Allowing for Identical Duplicate Resources in a Configuration</span></span>

<span data-ttu-id="3e9ba-103">DSC não permitir nem lidar com definições em conflito de recursos dentro de uma configuração.</span><span class="sxs-lookup"><span data-stu-id="3e9ba-103">DSC does not allow or handle conflicting resource definitions within a configuration.</span></span> <span data-ttu-id="3e9ba-104">Em vez de tentar resolver o conflito, simplesmente falhará.</span><span class="sxs-lookup"><span data-stu-id="3e9ba-104">Instead of trying to resolve the conflict, it simply fails.</span></span> <span data-ttu-id="3e9ba-105">Como a reutilização de configuração se torna mais utilizada por meio de recursos compostos, conflitos etc. ocorrerá com mais frequência.</span><span class="sxs-lookup"><span data-stu-id="3e9ba-105">As configuration reuse becomes more utilized through composite resources, etc. conflicts will occur more often.</span></span> <span data-ttu-id="3e9ba-106">Quando as definições de recursos em conflito são idênticas, DSC deve ser inteligente e permitir isso.</span><span class="sxs-lookup"><span data-stu-id="3e9ba-106">When conflicting resource definitions are identical, DSC should be smart and allow this.</span></span> <span data-ttu-id="3e9ba-107">Com esta versão, oferecemos suporte a ter várias instâncias de recursos que têm definições idênticas:</span><span class="sxs-lookup"><span data-stu-id="3e9ba-107">With this release, we support having multiple resource instances that have identical definitions:</span></span>

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

<span data-ttu-id="3e9ba-108">Em versões anteriores, o resultado seria uma compilação com falhas devido a um conflito entre o WindowsFeature FE_IIS e instâncias de WindowsFeature Worker_IIS tentando Certifique-se a função de "servidor Web está instalada.</span><span class="sxs-lookup"><span data-stu-id="3e9ba-108">In previous releases, the result would be a failed compilation due to a conflict between the WindowsFeature FE_IIS and WindowsFeature Worker_IIS instances trying to ensure the 'Web-Server' role is installed.</span></span> <span data-ttu-id="3e9ba-109">Tenha em atenção que *todos os* das propriedades que estão a ser configuradas são idênticos nessas duas configurações.</span><span class="sxs-lookup"><span data-stu-id="3e9ba-109">Notice that *all* of the properties that are being configured are identical in these two configurations.</span></span> <span data-ttu-id="3e9ba-110">Uma vez que *todos os* as propriedades desses dois recursos são idênticos, tal resultará numa compilação bem-sucedida agora.</span><span class="sxs-lookup"><span data-stu-id="3e9ba-110">Since *all* of the properties in these two resources are identical, this will result in a successful compilation now.</span></span>

<span data-ttu-id="3e9ba-111">Se qualquer uma das propriedades são diferentes entre os dois recursos, eles não serão considerados idênticos e compilação irá falhar:</span><span class="sxs-lookup"><span data-stu-id="3e9ba-111">If any of the properties are different between the two resources, they will not be considered identical and compilation will fail:</span></span>

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS
    {
        Ensure = 'Present'     # Ensure is Present here
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS
    {
        Ensure = 'Absent'      # Ensure property is Absent instead of Present
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

<span data-ttu-id="3e9ba-112">Esta configuração muito semelhante irá falhar porque o FE_IIS WindowsFeature e os recursos de WindowsFeature Worker_IIS já não são idênticos e, portanto, entram em conflito.</span><span class="sxs-lookup"><span data-stu-id="3e9ba-112">This very similar configuration will fail because the WindowsFeature FE_IIS and the WindowsFeature Worker_IIS resources are no longer identical and therefore conflict.</span></span>
