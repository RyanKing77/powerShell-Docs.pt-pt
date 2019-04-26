---
title: Criar um serviço da Web de OData gestão | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06b1b050-0bf7-48f5-ba05-43f489d597c0
caps.latest.revision: 10
ms.openlocfilehash: 476fce9fc087b870bad93a9204a820c5a84df99e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080701"
---
# <a name="creating-a-management-odata-web-service"></a>Creating a Management OData Web Service (Criar um Serviço Web OData de Gestão)

Extensão de gestão de IIS de ODATA é uma infraestrutura para a criação de um ponto de final de serviço da web ASP.NET que expõe os seus dados de gestão, acedidos através de cmdlets do Windows PowerShell e scripts, como as entidades do service Web de OData. Ele faz isso ao processamento de pedidos de OData e convertê-los numa invocação de Windows PowerShell. As equipes de produto podem se basear nessa infra-estrutura para criar pontos finais que expõem determinados conjuntos de dados de gestão.

Transferir e instalar o [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) exemplo. Siga as instruções para implementar o serviço web. Esse web service expõe serviços e processos através de operações de criação, leitura, atualização e exclusão (CRUD). Pedidos CRUD efetuados para o serviço web invocam comandos do Windows PowerShell que realizar as operações necessárias. Um mapeamento entre as operações CRUD e os comandos do Windows PowerShell subjacentes é implementado por arquivos de esquema de dois, schema.mof e Schema. O ficheiro de schema.mof utiliza a [Distributed Management Task Force](https://www.dmtf.org/) standard (DMTF) MOF (Managed Object). O arquivo Schema utiliza um esquema XML que está descrito em [esquema de mapeamento de recursos](./resource-mapping-schema.md).

> [!IMPORTANT]
> Antes de ativar a extensão IIS de ODATA de gerenciamento no Windows Server 2008 R2 SP1, as seguintes funcionalidades tem de estar ativadas.
>
> 1.  IIS-WebServerRole
> 2.  IIS-WebServer
> 3.  IIS-HttpTracing
> 4.  IIS-ManagementOData

## <a name="steps-for-creating-a-management-odata-web-service"></a>Passos para criar um serviço da web de OData de gestão

Os tópicos seguintes descrevem como criar e implementar um serviço da web de OData de gestão.

- [A adição de recursos para um serviço da Web de OData de gestão](./adding-resources-to-a-management-odata-web-service.md)

- [Implementar a autorização de personalizado para um serviço da web de OData de gestão](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [Implementando SessionConfiguration para um serviço da web de OData de gestão](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [O ficheiro de esquema do MOF para um serviço da web de OData da gestão de criação](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [O ficheiro de esquema XML para um serviço da web de OData da gestão de criação](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [O ficheiro Web. config para um serviço da web de OData da gestão de criação](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [Implementar um serviço da web de OData de gestão](./deploying-a-management-odata-web-service.md)

- [Associação de entidades de OData da gestão](./associating-management-odata-entities.md)

## <a name="see-also"></a>Veja Também

[Arquivos de esquema da extensão de IIS de ODATA de gestão](./management-odata-iis-extension-schema-files.md)
