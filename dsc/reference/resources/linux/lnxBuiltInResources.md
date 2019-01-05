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
# <a name="built-in-desired-state-configuration-resources-for-linux"></a>Incorporado Desired State Configuration recursos para Linux

Os recursos são blocos de construção que pode utilizar para criar um script do PowerShell Desired State Configuration (DSC). DSC para Linux inclui um conjunto de uma funcionalidade incorporada para configurar recursos como arquivos e pastas, pacotes, variáveis de ambiente e os serviços e processos.

## <a name="built-in-resources"></a>Recursos incorporados

A tabela seguinte fornece uma lista destes recursos e ligações para tópicos que descrevem-las detalhadamente.

* [Recurso nxArchive](lnxArchiveResource.md)– fornece um mecanismo para descompactar os ficheiros de arquivo (. tar,. zip) num caminho específico.
* [Recurso nxEnvironment](lnxEnvironmentResource.md)– gere as variáveis de ambiente em nós de destino.
* [Recurso nxFile](lnxFileResource.md)– Linux gere arquivos e diretórios.
* [Recurso nxFileLine](lnxFileLineResource.md)– gere linhas individuais num arquivo de Linux.
* [Recurso nxGroup](lnxGroupResource.md)– gere os grupos locais do Linux.
* [Recurso nxPackage](lnxPackageResource.md)– gere pacotes em nós do Linux.
* [nxScript recursos](lnxScriptResource.md)– executa scripts em nós de destino.
* [Recurso nxService](lnxServiceResource.md)– Linux gerencia serviços (daemons).
* [Recurso nxSshAuthorizedKeys](lnxSshAuthorizedKeysResource.md)– gere público ssh chaves para um utilizador do Linux.
* [Recurso nxUser](lnxUserResource.md)– Gere utilizadores locais do Linux.