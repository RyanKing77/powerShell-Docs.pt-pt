---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: d3a625d05eaf4e7448b4abf90499f6a94e2f7718
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a>Permite a recursos duplicados idênticos numa configuração

O DSC não permitir ou lidar com definições em conflito de recursos dentro de uma configuração. Em vez de tentar resolver o conflito, basta falhará. Como a reutilização de configuração torna-se mais utilizada através dos recursos compostos, serão mais frequentemente ocorrer conflitos de etc.. Quando as definições de recursos em conflito são idênticas, DSC deve ser inteligente e permitir esta. Com esta versão, suportamos a ter várias instâncias de recursos que têm definições idênticas:

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

Em versões anteriores, o resultado seria uma compilação falhou devido a um conflito entre a WindowsFeature FE_IIS e instâncias de WindowsFeature Worker_IIS tentar Certifique-se a função 'servidor Web está instalada. Repare que *todos os* das propriedades que estão a ser configuradas são idênticos nestas duas configurações. Uma vez que *todos os* as propriedades destes dois recursos são idênticos, tal resultará em agora uma compilação efetuada com êxito. 

Se alguma das propriedades for diferente entre os dois recursos, estes não serão considerados idênticas e falhará a compilação:

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

Esta configuração muito semelhante irá falhar porque o FE_IIS WindowsFeature e os recursos de WindowsFeature Worker_IIS já não são idênticos e, por conseguinte, estão em conflito.

