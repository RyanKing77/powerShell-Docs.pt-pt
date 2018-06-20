---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 3f73b7cf0cdf033cbd561b3412734692bb7decd7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187546"
---
# <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a><span data-ttu-id="20245-102">Permite a recursos duplicados idênticos numa configuração</span><span class="sxs-lookup"><span data-stu-id="20245-102">Allowing for Identical Duplicate Resources in a Configuration</span></span>

<span data-ttu-id="20245-103">O DSC não permitir ou lidar com definições em conflito de recursos dentro de uma configuração.</span><span class="sxs-lookup"><span data-stu-id="20245-103">DSC does not allow or handle conflicting resource definitions within a configuration.</span></span> <span data-ttu-id="20245-104">Em vez de tentar resolver o conflito, basta falhará.</span><span class="sxs-lookup"><span data-stu-id="20245-104">Instead of trying to resolve the conflict, it simply fails.</span></span> <span data-ttu-id="20245-105">Como a reutilização de configuração torna-se mais utilizada através dos recursos compostos, serão mais frequentemente ocorrer conflitos de etc.</span><span class="sxs-lookup"><span data-stu-id="20245-105">As configuration reuse becomes more utilized through composite resources, etc. conflicts will occur more often.</span></span> <span data-ttu-id="20245-106">Quando as definições de recursos em conflito são idênticas, DSC deve ser inteligente e permitir esta.</span><span class="sxs-lookup"><span data-stu-id="20245-106">When conflicting resource definitions are identical, DSC should be smart and allow this.</span></span> <span data-ttu-id="20245-107">Com esta versão, suportamos a ter várias instâncias de recursos que têm definições idênticas:</span><span class="sxs-lookup"><span data-stu-id="20245-107">With this release, we support having multiple resource instances that have identical definitions:</span></span>

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

<span data-ttu-id="20245-108">Em versões anteriores, o resultado seria uma compilação falhou devido a um conflito entre a WindowsFeature FE_IIS e instâncias de WindowsFeature Worker_IIS tentar Certifique-se a função 'servidor Web está instalada.</span><span class="sxs-lookup"><span data-stu-id="20245-108">In previous releases, the result would be a failed compilation due to a conflict between the WindowsFeature FE_IIS and WindowsFeature Worker_IIS instances trying to ensure the 'Web-Server' role is installed.</span></span> <span data-ttu-id="20245-109">Repare que *todos os* das propriedades que estão a ser configuradas são idênticos nestas duas configurações.</span><span class="sxs-lookup"><span data-stu-id="20245-109">Notice that *all* of the properties that are being configured are identical in these two configurations.</span></span> <span data-ttu-id="20245-110">Uma vez que *todos os* as propriedades destes dois recursos são idênticos, tal resultará em agora uma compilação efetuada com êxito.</span><span class="sxs-lookup"><span data-stu-id="20245-110">Since *all* of the properties in these two resources are identical, this will result in a successful compilation now.</span></span>

<span data-ttu-id="20245-111">Se alguma das propriedades for diferente entre os dois recursos, estes não serão considerados idênticas e falhará a compilação:</span><span class="sxs-lookup"><span data-stu-id="20245-111">If any of the properties are different between the two resources, they will not be considered identical and compilation will fail:</span></span>

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

<span data-ttu-id="20245-112">Esta configuração muito semelhante irá falhar porque o FE_IIS WindowsFeature e os recursos de WindowsFeature Worker_IIS já não são idênticos e, por conseguinte, estão em conflito.</span><span class="sxs-lookup"><span data-stu-id="20245-112">This very similar configuration will fail because the WindowsFeature FE_IIS and the WindowsFeature Worker_IIS resources are no longer identical and therefore conflict.</span></span>
