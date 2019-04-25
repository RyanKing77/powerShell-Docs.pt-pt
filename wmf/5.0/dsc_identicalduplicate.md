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
# <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a>Permitindo para recursos duplicados idênticos numa configuração

DSC não permitir nem lidar com definições em conflito de recursos dentro de uma configuração. Em vez de tentar resolver o conflito, simplesmente falhará. Como a reutilização de configuração se torna mais utilizada por meio de recursos compostos, conflitos etc. ocorrerá com mais frequência. Quando as definições de recursos em conflito são idênticas, DSC deve ser inteligente e permitir isso. Com esta versão, oferecemos suporte a ter várias instâncias de recursos que têm definições idênticas:

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

Em versões anteriores, o resultado seria uma compilação com falhas devido a um conflito entre o WindowsFeature FE_IIS e instâncias de WindowsFeature Worker_IIS tentando Certifique-se a função de "servidor Web está instalada. Tenha em atenção que *todos os* das propriedades que estão a ser configuradas são idênticos nessas duas configurações. Uma vez que *todos os* as propriedades desses dois recursos são idênticos, tal resultará numa compilação bem-sucedida agora.

Se qualquer uma das propriedades são diferentes entre os dois recursos, eles não serão considerados idênticos e compilação irá falhar:

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

Esta configuração muito semelhante irá falhar porque o FE_IIS WindowsFeature e os recursos de WindowsFeature Worker_IIS já não são idênticos e, portanto, entram em conflito.
