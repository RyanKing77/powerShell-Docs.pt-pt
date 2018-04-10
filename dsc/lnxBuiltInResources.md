---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Incorporado pretendido recursos de configuração do Estado para Linux
ms.openlocfilehash: 77617b72584f39c46fc4b9eb67235378bbfc19aa
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="built-in-desired-state-configuration-resources-for-linux"></a>Incorporado pretendido recursos de configuração do Estado para Linux

Os recursos são os blocos modulares que pode utilizar para escrever um script de PowerShell pretendido Estado Configuration (DSC). DSC para Linux inclui um conjunto de uma funcionalidade incorporada para configurar os recursos, tais como ficheiros e pastas, os pacotes, variáveis de ambiente e os serviços e processos.

## <a name="built-in-resources"></a>Recursos incorporados

A tabela seguinte fornece uma lista destes recursos e ligações para tópicos que descrevem-los em detalhe.

* [nxArchive recursos](lnxArchiveResource.md)– fornece um mecanismo para descompactar os ficheiros de arquivo (. tar,. zip) de um caminho específico.
* [nxEnvironment recursos](lnxEnvironmentResource.md)– gere as variáveis de ambiente em nós de destino.
* [nxFile recursos](lnxFileResource.md)– Linux gere ficheiros e diretórios.
* [nxFileLine recursos](lnxFileLineResource.md)– gere individuais linhas num ficheiro de Linux.
* [nxGroup recursos](lnxGroupResource.md)– gere grupos locais do Linux.
* [nxPackage recursos](lnxPackageResource.md)– gere pacotes em nós do Linux.
* [nxScript recursos](lnxScriptResource.md)– executa scripts em nós de destino.
* [nxService recursos](lnxServiceResource.md)-serviços de Linux gere (daemons).
* [nxSshAuthorizedKeys recursos](lnxSshAuthorizedKeysResource.md)– gere pública ssh chaves para um utilizador de Linux.
* [nxUser recursos](lnxUserResource.md)– Gere utilizadores locais do Linux.