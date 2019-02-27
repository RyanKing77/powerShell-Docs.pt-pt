---
title: O ficheiro de esquema XML para um serviço da web de OData da gestão de criação | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e83c9d9-6d06-4247-94d9-e3bfd4013b11
caps.latest.revision: 4
ms.openlocfilehash: a806d012097d107b6cc35710b9a93f2b27dd1ace
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848196"
---
# <a name="authoring-the-xml-schema-file-for-a-management-odata-web-service"></a><span data-ttu-id="243bc-102">Authoring the XML schema file for a Management OData web service (Autorizar o ficheiro de esquema XML para um serviço Web OData de Gestão)</span><span class="sxs-lookup"><span data-stu-id="243bc-102">Authoring the XML schema file for a Management OData web service</span></span>

<span data-ttu-id="243bc-103">Depois de definir os recursos de seu serviço web irá expor (veja [o ficheiro de esquema do MOF para um serviço da web de OData da gestão de criação](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), mapear esses recursos para os cmdlets do Windows PowerShell subjacentes que implementam o suportados operações para cada recurso através da criação de um arquivo XML que está em conformidade com o [esquema de mapeamento de recursos](./resource-mapping-schema.md).</span><span class="sxs-lookup"><span data-stu-id="243bc-103">After you define the resources your web service will expose (see [Authoring the MOF schema file for a Management OData web service](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), you map those resources to the underlying Windows PowerShell cmdlets that implement the supported operations for each resource by creating an XML file that conforms to the [Resource Mapping Schema](./resource-mapping-schema.md).</span></span> <span data-ttu-id="243bc-104">O arquivo XML também especifica os URLs que são utilizados pelo cliente para acessar os recursos.</span><span class="sxs-lookup"><span data-stu-id="243bc-104">The XML file also specifies the URLs that are used by the client to access the resources.</span></span>

## <a name="mappng-resources-to-urls"></a><span data-ttu-id="243bc-105">Recursos de Mappng para URLs</span><span class="sxs-lookup"><span data-stu-id="243bc-105">Mappng resources to URLs</span></span>

<span data-ttu-id="243bc-106">A primeira parte do arquivo XML mapeia os recursos definidos no ficheiro MOF de esquema para os URLs que são utilizados para aceder aos mesmos.</span><span class="sxs-lookup"><span data-stu-id="243bc-106">The first part of the XML file maps the resources defined in the MOF schema file to the URLs that are used to access them.</span></span> <span data-ttu-id="243bc-107">O exemplo seguinte mostra esse mapeamento.</span><span class="sxs-lookup"><span data-stu-id="243bc-107">The following example shows that mapping.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<ResourceMetadata xmlns="http://schemas.microsoft.com/powershell-web-services/2010/09">
    <SchemaNamespace>PswsTest</SchemaNamespace>
    <ContainerName>PSWSEntityContainer</ContainerName>
    <Resources>
        <Resource>
            <RelativeUrl>Service</RelativeUrl>
            <Class>PswsTest_Service</Class>
        </Resource>
        <Resource>
            <RelativeUrl>Process</RelativeUrl>
            <Class>PswsTest_Process</Class>
        </Resource>
    </Resources>
```

## <a name="mapping-cmdlets-to-crud-operations"></a><span data-ttu-id="243bc-108">Cmdlets de mapeamento para operações CRUD</span><span class="sxs-lookup"><span data-stu-id="243bc-108">Mapping cmdlets to CRUD operations</span></span>

<span data-ttu-id="243bc-109">Em seguida, especificar os cmdlets que correspondem do CRUD (criar, ler, atualizar e eliminar) operações que os recursos de suporte.</span><span class="sxs-lookup"><span data-stu-id="243bc-109">You then specify the cmdlets that correspond to the CRUD (create, read, update, and delete) operations that the resources support.</span></span> <span data-ttu-id="243bc-110">Na gestão OData [esquema de mapeamento de recursos](./resource-mapping-schema.md), as operações CRUD estão mapeadas da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="243bc-110">In the Management OData [Resource Mapping Schema](./resource-mapping-schema.md), the CRUD operations are mapped as follows.</span></span>

|<span data-ttu-id="243bc-111">Comando CRUD</span><span class="sxs-lookup"><span data-stu-id="243bc-111">CRUD command</span></span>|<span data-ttu-id="243bc-112">Elemento XML</span><span class="sxs-lookup"><span data-stu-id="243bc-112">XML element</span></span>|
|------------------|-----------------|
|<span data-ttu-id="243bc-113">Criar</span><span class="sxs-lookup"><span data-stu-id="243bc-113">Create</span></span>|<span data-ttu-id="243bc-114">Criar</span><span class="sxs-lookup"><span data-stu-id="243bc-114">Create</span></span>|
|<span data-ttu-id="243bc-115">Leitura</span><span class="sxs-lookup"><span data-stu-id="243bc-115">Read</span></span>|<span data-ttu-id="243bc-116">Consulta</span><span class="sxs-lookup"><span data-stu-id="243bc-116">Query</span></span>|
|<span data-ttu-id="243bc-117">Atualizar</span><span class="sxs-lookup"><span data-stu-id="243bc-117">Update</span></span>|<span data-ttu-id="243bc-118">Atualizar</span><span class="sxs-lookup"><span data-stu-id="243bc-118">Update</span></span>|
|<span data-ttu-id="243bc-119">Eliminar</span><span class="sxs-lookup"><span data-stu-id="243bc-119">Delete</span></span>|<span data-ttu-id="243bc-120">Eliminar</span><span class="sxs-lookup"><span data-stu-id="243bc-120">Delete</span></span>|

<span data-ttu-id="243bc-121">O exemplo seguinte mostra os mapeamentos para as operações de criação, leitura e Update no `Service` recursos.</span><span class="sxs-lookup"><span data-stu-id="243bc-121">The following example shows the mappings for the Create, Read, and Update operations on the `Service` resource.</span></span>

```xml
<ClassImplementations>
        <Class>
            <Name>PswsTest_Service</Name>
            <CmdletImplementation>
                <Query>
                    <Cmdlet>Get-Service</Cmdlet>
                        <FieldParameterMap>
                            <Field>
                                <FieldName>ServiceName</FieldName>
                                <ParameterName>Name</ParameterName>
                            </Field>
                        </FieldParameterMap>
                        <ParameterSets>
                            <ParameterSet>
                                <Name>Default</Name>
                                <Parameter><Name>Name</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                            </ParameterSet>
                            <ParameterSet>
                                <Name>DisplayName</Name>
                                <Parameter><Name>DisplayName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                            </ParameterSet>
                            <ParameterSet>
                                <Name>InputObject</Name>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Query>
                <Update>
                    <Cmdlet>Set-Service</Cmdlet>
                    <FieldParameterMap>
                        <Field>
                            <FieldName>ServiceName</FieldName>
                            <ParameterName>Name</ParameterName>
                        </Field>
                    </FieldParameterMap>
                    <ParameterSets>
                        <ParameterSet>
                            <Name>Name</Name>
                            <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                            <Parameter><Name>Name</Name></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                            <Parameter><Name>Status</Name></Parameter>
                            <Parameter><Name>ErrorVariable</Name></Parameter>
                            <Parameter><Name>WarningVariable</Name></Parameter>
                            <Parameter><Name>OutVariable</Name></Parameter>
                            <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                        <ParameterSet>
                            <Name>InputObject</Name>
                            <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Update>
                <Create>
                    <Cmdlet>New-Service</Cmdlet>
                    <FieldParameterMap>
                        <Field>
                            <FieldName>ServiceName</FieldName>
                            <ParameterName>Name</ParameterName>
                        </Field>
                    </FieldParameterMap>
                    <ParameterSets>
                        <ParameterSet>
                            <Name>__AllParameterSets</Name>
                            <Parameter><Name>BinaryPathName</Name></Parameter>
                            <Parameter><Name>Name</Name></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                            <Parameter><Name>DependsOn</Name></Parameter>
                            <Parameter><Name>ErrorVariable</Name></Parameter>
                            <Parameter><Name>WarningVariable</Name></Parameter>
                            <Parameter><Name>OutVariable</Name></Parameter>
                            <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Create>
            </CmdletImplementation>
        </Class>
```

## <a name="see-also"></a><span data-ttu-id="243bc-122">Veja Também</span><span class="sxs-lookup"><span data-stu-id="243bc-122">See Also</span></span>

[<span data-ttu-id="243bc-123">O ficheiro de esquema do MOF para um serviço da web de OData da gestão de criação</span><span class="sxs-lookup"><span data-stu-id="243bc-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[<span data-ttu-id="243bc-124">Esquema de mapeamento de recursos</span><span class="sxs-lookup"><span data-stu-id="243bc-124">Resource Mapping Schema</span></span>](./resource-mapping-schema.md)

[<span data-ttu-id="243bc-125">Criação de um serviço da Web de OData de gestão</span><span class="sxs-lookup"><span data-stu-id="243bc-125">Creating a Management OData Web Service</span></span>](./creating-a-management-odata-web-service.md)