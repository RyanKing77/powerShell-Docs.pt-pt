---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Incorporado Desired State Configuration recursos para Linux
ms.openlocfilehash: ea700d24c7ff4377af671944184abb3f201852e8
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048478"
---
# <a name="built-in-desired-state-configuration-resources-for-linux"></a><span data-ttu-id="bfff6-103">Incorporado Desired State Configuration recursos para Linux</span><span class="sxs-lookup"><span data-stu-id="bfff6-103">Built-In Desired State Configuration Resources for Linux</span></span>

<span data-ttu-id="bfff6-104">Os recursos são blocos de construção que pode utilizar para criar um script do PowerShell Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="bfff6-104">Resources are building blocks that you can use to write a PowerShell Desired State Configuration (DSC) script.</span></span> <span data-ttu-id="bfff6-105">DSC para Linux inclui um conjunto de uma funcionalidade incorporada para configurar recursos como arquivos e pastas, pacotes, variáveis de ambiente e os serviços e processos.</span><span class="sxs-lookup"><span data-stu-id="bfff6-105">DSC for Linux comes with a set of built-in functionality for configuring resources such as files and folders, packages, environment variables, and services and processes.</span></span>

## <a name="built-in-resources"></a><span data-ttu-id="bfff6-106">Recursos incorporados</span><span class="sxs-lookup"><span data-stu-id="bfff6-106">Built-in resources</span></span>

<span data-ttu-id="bfff6-107">A tabela seguinte fornece uma lista destes recursos e ligações para tópicos que descrevem-las detalhadamente.</span><span class="sxs-lookup"><span data-stu-id="bfff6-107">The following table provides a list of these resources and links to topics that describe them in detail.</span></span>

* <span data-ttu-id="bfff6-108">[Recurso nxArchive](lnxArchiveResource.md)– fornece um mecanismo para descompactar os ficheiros de arquivo (. tar,. zip) num caminho específico.</span><span class="sxs-lookup"><span data-stu-id="bfff6-108">[nxArchive Resource](lnxArchiveResource.md)--Provides a mechanism to unpack archive (.tar, .zip) files at a specific path.</span></span>
* <span data-ttu-id="bfff6-109">[Recurso nxEnvironment](lnxEnvironmentResource.md)– gere as variáveis de ambiente em nós de destino.</span><span class="sxs-lookup"><span data-stu-id="bfff6-109">[nxEnvironment Resource](lnxEnvironmentResource.md)--Manages environment variables on target nodes.</span></span>
* <span data-ttu-id="bfff6-110">[Recurso nxFile](lnxFileResource.md)– Linux gere arquivos e diretórios.</span><span class="sxs-lookup"><span data-stu-id="bfff6-110">[nxFile Resource](lnxFileResource.md)--Manages Linux files and directories.</span></span>
* <span data-ttu-id="bfff6-111">[Recurso nxFileLine](lnxFileLineResource.md)– gere linhas individuais num arquivo de Linux.</span><span class="sxs-lookup"><span data-stu-id="bfff6-111">[nxFileLine Resource](lnxFileLineResource.md)--Manages individual lines in a Linux file.</span></span>
* <span data-ttu-id="bfff6-112">[Recurso nxGroup](lnxGroupResource.md)– gere os grupos locais do Linux.</span><span class="sxs-lookup"><span data-stu-id="bfff6-112">[nxGroup Resource](lnxGroupResource.md)--Manages local Linux groups.</span></span>
* <span data-ttu-id="bfff6-113">[Recurso nxPackage](lnxPackageResource.md)– gere pacotes em nós do Linux.</span><span class="sxs-lookup"><span data-stu-id="bfff6-113">[nxPackage Resource](lnxPackageResource.md)--Manages packages on Linux nodes.</span></span>
* <span data-ttu-id="bfff6-114">[nxScript recursos](lnxScriptResource.md)– executa scripts em nós de destino.</span><span class="sxs-lookup"><span data-stu-id="bfff6-114">[nxScript Resource](lnxScriptResource.md)--Runs scripts on target nodes.</span></span>
* <span data-ttu-id="bfff6-115">[Recurso nxService](lnxServiceResource.md)– Linux gerencia serviços (daemons).</span><span class="sxs-lookup"><span data-stu-id="bfff6-115">[nxService Resource](lnxServiceResource.md)--Manages Linux services (daemons).</span></span>
* <span data-ttu-id="bfff6-116">[Recurso nxSshAuthorizedKeys](lnxSshAuthorizedKeysResource.md)– gere público ssh chaves para um utilizador do Linux.</span><span class="sxs-lookup"><span data-stu-id="bfff6-116">[nxSshAuthorizedKeys Resource](lnxSshAuthorizedKeysResource.md)--Manages public ssh keys for a Linux user.</span></span>
* <span data-ttu-id="bfff6-117">[Recurso nxUser](lnxUserResource.md)– Gere utilizadores locais do Linux.</span><span class="sxs-lookup"><span data-stu-id="bfff6-117">[nxUser Resource](lnxUserResource.md)--Manages local Linux users.</span></span>