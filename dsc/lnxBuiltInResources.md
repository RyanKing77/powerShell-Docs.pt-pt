---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Incorporado pretendido recursos de configuração do Estado para Linux"
ms.openlocfilehash: b85f32f7559d89bda566d35462cc613d73424c50
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="built-in-desired-state-configuration-resources-for-linux"></a><span data-ttu-id="d000f-103">Incorporado pretendido recursos de configuração do Estado para Linux</span><span class="sxs-lookup"><span data-stu-id="d000f-103">Built-In Desired State Configuration Resources for Linux</span></span>

<span data-ttu-id="d000f-104">Os recursos são os blocos modulares que pode utilizar para escrever um script de PowerShell pretendido Estado Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="d000f-104">Resources are building blocks that you can use to write a PowerShell Desired State Configuration (DSC) script.</span></span> <span data-ttu-id="d000f-105">DSC para Linux inclui um conjunto de uma funcionalidade incorporada para configurar os recursos, tais como ficheiros e pastas, os pacotes, variáveis de ambiente e os serviços e processos.</span><span class="sxs-lookup"><span data-stu-id="d000f-105">DSC for Linux comes with a set of built-in functionality for configuring resources such as files and folders, packages, environment variables, and services and processes.</span></span>

## <a name="built-in-resources"></a><span data-ttu-id="d000f-106">Recursos incorporados</span><span class="sxs-lookup"><span data-stu-id="d000f-106">Built-in resources</span></span> 

<span data-ttu-id="d000f-107">A tabela seguinte fornece uma lista destes recursos e ligações para tópicos que descrevem-los em detalhe.</span><span class="sxs-lookup"><span data-stu-id="d000f-107">The following table provides a list of these resources and links to topics that describe them in detail.</span></span>

* <span data-ttu-id="d000f-108">[nxArchive recursos](lnxArchiveResource.md)– fornece um mecanismo para descompactar os ficheiros de arquivo (. tar,. zip) de um caminho específico.</span><span class="sxs-lookup"><span data-stu-id="d000f-108">[nxArchive Resource](lnxArchiveResource.md)--Provides a mechanism to unpack archive (.tar, .zip) files at a specific path.</span></span>
* <span data-ttu-id="d000f-109">[nxEnvironment recursos](lnxEnvironmentResource.md)– gere as variáveis de ambiente em nós de destino.</span><span class="sxs-lookup"><span data-stu-id="d000f-109">[nxEnvironment Resource](lnxEnvironmentResource.md)--Manages environment variables on target nodes.</span></span> 
* <span data-ttu-id="d000f-110">[nxFile recursos](lnxFileResource.md)– Linux gere ficheiros e diretórios.</span><span class="sxs-lookup"><span data-stu-id="d000f-110">[nxFile Resource](lnxFileResource.md)--Manages Linux files and directories.</span></span> 
* <span data-ttu-id="d000f-111">[nxFileLine recursos](lnxFileLineResource.md)– gere individuais linhas num ficheiro de Linux.</span><span class="sxs-lookup"><span data-stu-id="d000f-111">[nxFileLine Resource](lnxFileLineResource.md)--Manages individual lines in a Linux file.</span></span> 
* <span data-ttu-id="d000f-112">[nxGroup recursos](lnxGroupResource.md)– gere grupos locais do Linux.</span><span class="sxs-lookup"><span data-stu-id="d000f-112">[nxGroup Resource](lnxGroupResource.md)--Manages local Linux groups.</span></span> 
* <span data-ttu-id="d000f-113">[nxPackage recursos](lnxPackageResource.md)– gere pacotes em nós do Linux.</span><span class="sxs-lookup"><span data-stu-id="d000f-113">[nxPackage Resource](lnxPackageResource.md)--Manages packages on Linux nodes.</span></span>
* <span data-ttu-id="d000f-114">[nxScript recursos](lnxScriptResource.md)– executa scripts em nós de destino.</span><span class="sxs-lookup"><span data-stu-id="d000f-114">[nxScript Resource](lnxScriptResource.md)--Runs scripts on target nodes.</span></span>
* <span data-ttu-id="d000f-115">[nxService recursos](lnxServiceResource.md)-serviços de Linux gere (daemons).</span><span class="sxs-lookup"><span data-stu-id="d000f-115">[nxService Resource](lnxServiceResource.md)--Manages Linux services (daemons).</span></span>
* <span data-ttu-id="d000f-116">[nxSshAuthorizedKeys recursos](lnxSshAuthorizedKeysResource.md)– gere pública ssh chaves para um utilizador de Linux.</span><span class="sxs-lookup"><span data-stu-id="d000f-116">[nxSshAuthorizedKeys Resource](lnxSshAuthorizedKeysResource.md)--Manages public ssh keys for a Linux user.</span></span> 
* <span data-ttu-id="d000f-117">[nxUser recursos](lnxUserResource.md)– Gere utilizadores locais do Linux.</span><span class="sxs-lookup"><span data-stu-id="d000f-117">[nxUser Resource](lnxUserResource.md)--Manages local Linux users.</span></span> 
  
