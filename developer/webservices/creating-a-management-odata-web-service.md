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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847251"
---
# <a name="creating-a-management-odata-web-service"></a><span data-ttu-id="ae265-102">Creating a Management OData Web Service (Criar um Serviço Web OData de Gestão)</span><span class="sxs-lookup"><span data-stu-id="ae265-102">Creating a Management OData Web Service</span></span>

<span data-ttu-id="ae265-103">Extensão de gestão de IIS de ODATA é uma infraestrutura para a criação de um ponto de final de serviço da web ASP.NET que expõe os seus dados de gestão, acedidos através de cmdlets do Windows PowerShell e scripts, como as entidades do service Web de OData.</span><span class="sxs-lookup"><span data-stu-id="ae265-103">Management ODATA IIS Extension is an infrastructure for creating an ASP.NET web service end point that exposes your management data, accessed through Windows PowerShell cmdlets and scripts, as OData Web service entities.</span></span> <span data-ttu-id="ae265-104">Ele faz isso ao processamento de pedidos de OData e convertê-los numa invocação de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ae265-104">It does that by processing OData requests and converting them into a Windows PowerShell invocation.</span></span> <span data-ttu-id="ae265-105">As equipes de produto podem se basear nessa infra-estrutura para criar pontos finais que expõem determinados conjuntos de dados de gestão.</span><span class="sxs-lookup"><span data-stu-id="ae265-105">Product teams can build on top of this infrastructure to create endpoints that expose specific sets of management data.</span></span>

<span data-ttu-id="ae265-106">Transferir e instalar o [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) exemplo.</span><span class="sxs-lookup"><span data-stu-id="ae265-106">Download and install the [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) sample.</span></span> <span data-ttu-id="ae265-107">Siga as instruções para implementar o serviço web.</span><span class="sxs-lookup"><span data-stu-id="ae265-107">Follow the instructions to deploy the web service.</span></span> <span data-ttu-id="ae265-108">Esse web service expõe serviços e processos através de operações de criação, leitura, atualização e exclusão (CRUD).</span><span class="sxs-lookup"><span data-stu-id="ae265-108">This web service exposes Services and Processes through Create, Read, Update, and Delete (CRUD) operations.</span></span> <span data-ttu-id="ae265-109">Pedidos CRUD efetuados para o serviço web invocam comandos do Windows PowerShell que realizar as operações necessárias.</span><span class="sxs-lookup"><span data-stu-id="ae265-109">CRUD requests made to the web service invoke  Windows PowerShell commands that perform the requested operations.</span></span> <span data-ttu-id="ae265-110">Um mapeamento entre as operações CRUD e os comandos do Windows PowerShell subjacentes é implementado por arquivos de esquema de dois, schema.mof e Schema.</span><span class="sxs-lookup"><span data-stu-id="ae265-110">A mapping between the CRUD operations and the underlying Windows PowerShell commands is implemented by two schema files, schema.mof and schema.xml.</span></span> <span data-ttu-id="ae265-111">O ficheiro de schema.mof utiliza a [Distributed Management Task Force](https://www.dmtf.org/) standard (DMTF) MOF (Managed Object).</span><span class="sxs-lookup"><span data-stu-id="ae265-111">The schema.mof file uses the [Distributed Management  Task Force](https://www.dmtf.org/) (DMTF) Managed Object (MOF) standard.</span></span> <span data-ttu-id="ae265-112">O arquivo Schema utiliza um esquema XML que está descrito em [esquema de mapeamento de recursos](./resource-mapping-schema.md).</span><span class="sxs-lookup"><span data-stu-id="ae265-112">The schema.xml file uses an XML schema that is described in [Resource Mapping Schema](./resource-mapping-schema.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ae265-113">Antes de ativar a extensão IIS de ODATA de gerenciamento no Windows Server 2008 R2 SP1, as seguintes funcionalidades tem de estar ativadas.</span><span class="sxs-lookup"><span data-stu-id="ae265-113">Before you enabling Management ODATA IIS Extension on Windows Server 2008 R2 SP1, the following features must be enabled.</span></span>
>
> 1.  <span data-ttu-id="ae265-114">IIS-WebServerRole</span><span class="sxs-lookup"><span data-stu-id="ae265-114">IIS-WebServerRole</span></span>
> 2.  <span data-ttu-id="ae265-115">IIS-WebServer</span><span class="sxs-lookup"><span data-stu-id="ae265-115">IIS-WebServer</span></span>
> 3.  <span data-ttu-id="ae265-116">IIS-HttpTracing</span><span class="sxs-lookup"><span data-stu-id="ae265-116">IIS-HttpTracing</span></span>
> 4.  <span data-ttu-id="ae265-117">IIS-ManagementOData</span><span class="sxs-lookup"><span data-stu-id="ae265-117">IIS-ManagementOData</span></span>

## <a name="steps-for-creating-a-management-odata-web-service"></a><span data-ttu-id="ae265-118">Passos para criar um serviço da web de OData de gestão</span><span class="sxs-lookup"><span data-stu-id="ae265-118">Steps for creating a Management OData web service</span></span>

<span data-ttu-id="ae265-119">Os tópicos seguintes descrevem como criar e implementar um serviço da web de OData de gestão.</span><span class="sxs-lookup"><span data-stu-id="ae265-119">The following topics describe how to create and deploy a Management OData web service.</span></span>

- [<span data-ttu-id="ae265-120">A adição de recursos para um serviço da Web de OData de gestão</span><span class="sxs-lookup"><span data-stu-id="ae265-120">Adding Resources to a Management OData Web Service</span></span>](./adding-resources-to-a-management-odata-web-service.md)

- [<span data-ttu-id="ae265-121">Implementar a autorização de personalizado para um serviço da web de OData de gestão</span><span class="sxs-lookup"><span data-stu-id="ae265-121">Implementing Custom Authorization for a Management OData web service</span></span>](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [<span data-ttu-id="ae265-122">Implementando SessionConfiguration para um serviço da web de OData de gestão</span><span class="sxs-lookup"><span data-stu-id="ae265-122">Implementing SessionConfiguration for a Management OData web service</span></span>](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [<span data-ttu-id="ae265-123">O ficheiro de esquema do MOF para um serviço da web de OData da gestão de criação</span><span class="sxs-lookup"><span data-stu-id="ae265-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="ae265-124">O ficheiro de esquema XML para um serviço da web de OData da gestão de criação</span><span class="sxs-lookup"><span data-stu-id="ae265-124">Authoring the XML schema file for a Management OData web service</span></span>](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="ae265-125">O ficheiro Web. config para um serviço da web de OData da gestão de criação</span><span class="sxs-lookup"><span data-stu-id="ae265-125">Authoring the Web.config file for a Management OData web service</span></span>](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="ae265-126">Implementar um serviço da web de OData de gestão</span><span class="sxs-lookup"><span data-stu-id="ae265-126">Deploying a Management OData web service</span></span>](./deploying-a-management-odata-web-service.md)

- [<span data-ttu-id="ae265-127">Associação de entidades de OData da gestão</span><span class="sxs-lookup"><span data-stu-id="ae265-127">Associating Management OData Entities</span></span>](./associating-management-odata-entities.md)

## <a name="see-also"></a><span data-ttu-id="ae265-128">Veja Também</span><span class="sxs-lookup"><span data-stu-id="ae265-128">See Also</span></span>

[<span data-ttu-id="ae265-129">Arquivos de esquema da extensão de IIS de ODATA de gestão</span><span class="sxs-lookup"><span data-stu-id="ae265-129">Management ODATA IIS Extension Schema Files</span></span>](./management-odata-iis-extension-schema-files.md)
