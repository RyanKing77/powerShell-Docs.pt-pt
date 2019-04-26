---
title: Associação de gestão OData entidades | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 947a3add-3593-400d-8144-8b44c8adbe5e
caps.latest.revision: 5
ms.openlocfilehash: 44b718e024eb98ac562edb50076287a31f5edc6b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080752"
---
# <a name="associating-management-odata-entities"></a><span data-ttu-id="10c2d-102">Associating Management OData Entities (Associar Entidades OData de Gestão)</span><span class="sxs-lookup"><span data-stu-id="10c2d-102">Associating Management OData Entities</span></span>

<span data-ttu-id="10c2d-103">Muitas vezes é útil criar uma associação entre duas entidades de OData de gestão diferentes.</span><span class="sxs-lookup"><span data-stu-id="10c2d-103">It is often useful to create an association between two different Management OData entities.</span></span> <span data-ttu-id="10c2d-104">Por exemplo, um serviço de gestão OData ter entidades que gerem um catálogo de produtos que estão organizados em categorias e definir as entidades `Product` e `Category`.</span><span class="sxs-lookup"><span data-stu-id="10c2d-104">For example, a Management OData service could have entities that manage a catalogue of products that are organized in categories, and define the entities `Product` and `Category`.</span></span> <span data-ttu-id="10c2d-105">Ao associar estas duas entidades, um cliente pode obter informações sobre todos os produtos numa categoria com um único pedido para o serviço web.</span><span class="sxs-lookup"><span data-stu-id="10c2d-105">By associating these two entities, a client can get information about all of the products in a category with a single request to the web service.</span></span>

<span data-ttu-id="10c2d-106">Um exemplo que mostra como criar associações entre entidades pode ser baixado do site [exemplo de associação](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).</span><span class="sxs-lookup"><span data-stu-id="10c2d-106">A sample that shows how to create associations between entities can be downloaded at [Association sample](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).</span></span>

## <a name="creating-the-association-in-the-resource-schema-file"></a><span data-ttu-id="10c2d-107">Criar a associação no arquivo de esquema de recursos</span><span class="sxs-lookup"><span data-stu-id="10c2d-107">Creating the Association in the resource schema file</span></span>

<span data-ttu-id="10c2d-108">O MOF seguinte define duas entidades.</span><span class="sxs-lookup"><span data-stu-id="10c2d-108">The following MOF defines two entities.</span></span> <span data-ttu-id="10c2d-109">Iremos criar uma associação entre elas.</span><span class="sxs-lookup"><span data-stu-id="10c2d-109">We will create an association between them.</span></span>

```csharp
class Product {

[key] string ProductName;

// other fields ...
};

class Category {

[key] string CategoryName;

string Products[];

// other fields
}
```

<span data-ttu-id="10c2d-110">O `Category` classe define uma propriedade que é uma matriz de nomes dos produtos que pertencem a essa categoria.</span><span class="sxs-lookup"><span data-stu-id="10c2d-110">The `Category` class defines a property that is an array of the names of the products that belong to that category.</span></span>

<span data-ttu-id="10c2d-111">Para associar as duas entidades, tem de definir uma classe com o `Association` atributos no arquivo MOF de esquema de recursos para o serviço.</span><span class="sxs-lookup"><span data-stu-id="10c2d-111">To associate two entities, you must define a class with the `Association` attribute in the resource schema MOF file for the service.</span></span> <span data-ttu-id="10c2d-112">A classe tem de definir as duas entidades para ser associado, chamado `ends` da association.</span><span class="sxs-lookup"><span data-stu-id="10c2d-112">The class must define the two entities to be associated, called `ends` of the association.</span></span> <span data-ttu-id="10c2d-113">O exemplo seguinte mostra uma definição de uma classe que define uma associação entre as entidades de categoria e produtos.</span><span class="sxs-lookup"><span data-stu-id="10c2d-113">The following example shows a definition of a class that defines an association between the Category and Products entities.</span></span>

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

<span data-ttu-id="10c2d-114">Também tem de alterar a declaração da propriedade de produtos na classe de categoria.</span><span class="sxs-lookup"><span data-stu-id="10c2d-114">You must also change the declaration of the Products property in the Category class.</span></span> <span data-ttu-id="10c2d-115">Utilizar o `AssociationClass` palavra-chave para especificar que a propriedade é uma extremidade da association.</span><span class="sxs-lookup"><span data-stu-id="10c2d-115">You use the `AssociationClass` keyword to specify that the property is one end of the association.</span></span> <span data-ttu-id="10c2d-116">A propriedade também tem de ser definida como uma referência a uma entidade separada, em vez de uma matriz de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="10c2d-116">The property must also be defined as a reference to a separate entity, rather than an array of strings.</span></span> <span data-ttu-id="10c2d-117">Fazer isso usando o `ref` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="10c2d-117">You do this by using the `ref` keyword.</span></span> <span data-ttu-id="10c2d-118">O exemplo seguinte mostra a definição de propriedade para a associação.</span><span class="sxs-lookup"><span data-stu-id="10c2d-118">The following example shows the property definition for the association.</span></span>

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

<span data-ttu-id="10c2d-119">Por fim, deve declarar outro extremo da associação ao adicionar uma definição de propriedade para o `Product` classe.</span><span class="sxs-lookup"><span data-stu-id="10c2d-119">Finally, you must declare the other end of the association by adding a property definition to the `Product` class.</span></span> <span data-ttu-id="10c2d-120">Esta é uma referência a uma matriz ou a uma única entidade.</span><span class="sxs-lookup"><span data-stu-id="10c2d-120">This is a reference to either an array or to a single entity.</span></span> <span data-ttu-id="10c2d-121">Supondo que cada produto pertence a apenas uma categoria, a definição seria da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="10c2d-121">Assuming that each product belongs to only one category, the definition would be as follows.</span></span>

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

<span data-ttu-id="10c2d-122">As propriedades que representam as duas extremidades da associação são chamadas de propriedades de navegação.</span><span class="sxs-lookup"><span data-stu-id="10c2d-122">The properties that represent the two ends of the association are called navigation properties.</span></span>

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a><span data-ttu-id="10c2d-123">Passos para associar entidades no arquivo de esquema de recursos</span><span class="sxs-lookup"><span data-stu-id="10c2d-123">Steps for associating entities in the resource schema file</span></span>

- <span data-ttu-id="10c2d-124">Definir a associação como uma classe com o `Association` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="10c2d-124">Define the association as a class by using the `Association` keyword.</span></span>

- <span data-ttu-id="10c2d-125">Defina as extremidades da associação com a palavra-chave de AssociationClass para qualificar propriedades das entidades associadas.</span><span class="sxs-lookup"><span data-stu-id="10c2d-125">Define the ends of the association by using the AssociationClass keyword to qualify properties of the associated entities.</span></span>

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a><span data-ttu-id="10c2d-126">Criar a associação no arquivo XML de mapeamento de recursos</span><span class="sxs-lookup"><span data-stu-id="10c2d-126">Creating the association in the resource mapping XML file</span></span>

<span data-ttu-id="10c2d-127">Há três casos diferentes a serem considerados ao mapeamento de uma associação no arquivo XML de mapeamento de recursos.</span><span class="sxs-lookup"><span data-stu-id="10c2d-127">There are three different cases to consider when mapping an association in the resource mapping XML file.</span></span>

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a><span data-ttu-id="10c2d-128">Determinar como associar entidades no arquivo de mapeamento de recursos</span><span class="sxs-lookup"><span data-stu-id="10c2d-128">Determining how to associate entities in the resource mapping file</span></span>

- <span data-ttu-id="10c2d-129">Se a propriedade de navegação está presente no subjacentes.</span><span class="sxs-lookup"><span data-stu-id="10c2d-129">If the navigation property is present in the underlying.</span></span> <span data-ttu-id="10c2d-130">Tipo de .NET framework e essa propriedade contém chaves estrangeiras, nenhum mapeamento explícito é necessário.</span><span class="sxs-lookup"><span data-stu-id="10c2d-130">.NET Framework type, and that property contains foreign keys, no explicit mapping is necessary.</span></span>

- <span data-ttu-id="10c2d-131">Se a propriedade de navegação não existe no tipo de .NET Framework subjacente, tem de especificar um cmdlet que obtém a lista de chaves das instâncias associadas.</span><span class="sxs-lookup"><span data-stu-id="10c2d-131">If the navigation property does not exist in the underlying .NET Framework type, you must specify a cmdlet that retrieves the list of keys of the associated instances.</span></span> <span data-ttu-id="10c2d-132">Faça isso adicionando um `Association` elemento aninhado a `CmdletImplementation` elemento, seguindo os elementos que definem o `cmdlets` para os outros comandos CRUD.</span><span class="sxs-lookup"><span data-stu-id="10c2d-132">You do this by adding an `Association` element nested under the `CmdletImplementation` element, following the elements that define the `cmdlets` for the other CRUD commands.</span></span>

  ```xml
  Class Name=" Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
                 <Cmdlet>Get-ProductsInCategory</Cmdlet>
                 <ParameterForThisObject>Category</ParameterForThisObject>
              </GetReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

- <span data-ttu-id="10c2d-133">Se a propriedade de navegação existe no tipo de .NET Framework subjacente, mas contém instâncias de objeto, em vez de chaves estrangeiras, então tem de criar um cmdlet (ao escrever um script ou função do Windows PowerShell) para obter as chaves estrangeiras.</span><span class="sxs-lookup"><span data-stu-id="10c2d-133">If the navigation property does exist in the underlying .NET Framework type, but it contains object instances instead of foreign keys, then you must create a cmdlet (by writing a Windows PowerShell function or script) to retrieve the foreign keys.</span></span> <span data-ttu-id="10c2d-134">Em seguida, especifique esse cmdlet no arquivo de mapeamento de recursos.</span><span class="sxs-lookup"><span data-stu-id="10c2d-134">You then specify that cmdlet in the resource mapping file.</span></span> <span data-ttu-id="10c2d-135">Por exemplo, o script para obter as chaves teria o aspeto semelhante ao seguinte.</span><span class="sxs-lookup"><span data-stu-id="10c2d-135">For example, the script to retrieve the keys would look like the following.</span></span>

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  <span data-ttu-id="10c2d-136">E o XML no arquivo de mapeamento de recursos teria uma aparência semelhante ao seguinte.</span><span class="sxs-lookup"><span data-stu-id="10c2d-136">And the XML in the resource mapping file would look like the following.</span></span>

  ```xml
  Class Name=" Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
                 <Cmdlet>Get-ProductsInCategory.ps1</Cmdlet>
                 <ParameterForThisObject>Category</ParameterForThisObject>
              </GetReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

- <span data-ttu-id="10c2d-137">Além de especificar um cmdlet para obter as entidades associadas, também pode especificar cmdlets para adicionar e remover as referências da coleção.</span><span class="sxs-lookup"><span data-stu-id="10c2d-137">In addition to specifying a cmdlet to retrieve the associated entities, you can also specify cmdlets to add and remove references from the collection.</span></span> <span data-ttu-id="10c2d-138">O exemplo a seguir supõe que os cmdlets Add ProductToCategory e Remove-ProductFromCategory existem (eles também podem ser definidos num script ou função do exemplo anterior).</span><span class="sxs-lookup"><span data-stu-id="10c2d-138">The following example assumes that the Add-ProductToCategory and Remove-ProductFromCategory cmdlets exist (they can also be defined in a script or function as in the previous example).</span></span>

  ```xml
  Class Name="Sample.Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
  ...
              </GetReference>
        <AddReference>
     <CmdletName>"Add-ProductToCategory"</>
     <ParameterForThisObject>"Product"</>
     <ParameterForReferredObject>"Category"</>
        </AddReference>
        <RemoveReference>
     <CmdletName="Remove-ProductFromCategory"/>
     <ParameterForThisObject >"Product"</>
     <ParameterForReferredObject >"Category"</>
        </RemoveReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

## <a name="querying-associated-entities"></a><span data-ttu-id="10c2d-139">Consultar entidades associadas</span><span class="sxs-lookup"><span data-stu-id="10c2d-139">Querying associated entities</span></span>

<span data-ttu-id="10c2d-140">O cliente pode obter uma lista das instâncias associadas com uma entidade com a criação de consultas específicas.</span><span class="sxs-lookup"><span data-stu-id="10c2d-140">The client can retrieve a list of the instances associated with an entity by creating specific queries.</span></span>

#### <a name="constructing-queries-for-associated-entities"></a><span data-ttu-id="10c2d-141">Construir consultas para entidades associadas</span><span class="sxs-lookup"><span data-stu-id="10c2d-141">Constructing queries for associated entities</span></span>

- <span data-ttu-id="10c2d-142">Um cliente pode pedir os detalhes de uma categoria sem recuperar seus produtos associados.</span><span class="sxs-lookup"><span data-stu-id="10c2d-142">A client can request the details of a category without retrieving its associated products.</span></span> <span data-ttu-id="10c2d-143">Por exemplo, o pedido seguinte obtém os detalhes do `food` categoria.</span><span class="sxs-lookup"><span data-stu-id="10c2d-143">For example, the following request gets details of the `food` category.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  <span data-ttu-id="10c2d-144">Para obter os produtos associados da categoria (mas não os detalhes da categoria em si, o cliente especifica a propriedade de navegação no pedido.</span><span class="sxs-lookup"><span data-stu-id="10c2d-144">To get the associated products of the category (but not details of the category itself, the client specifies the navigation property in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- <span data-ttu-id="10c2d-145">Para obter apenas os URLs dos produtos, utilize o `$links` qualificador no pedido.</span><span class="sxs-lookup"><span data-stu-id="10c2d-145">To retrieve only URLs of the products, use the `$links` qualifier in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- <span data-ttu-id="10c2d-146">O cliente pode obter os detalhes de categoria e seus produtos associados com o `$expand` qualificador.</span><span class="sxs-lookup"><span data-stu-id="10c2d-146">The client can get both the category details and its associated products by using the `$expand` qualifier.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a><span data-ttu-id="10c2d-147">Veja Também</span><span class="sxs-lookup"><span data-stu-id="10c2d-147">See Also</span></span>

[<span data-ttu-id="10c2d-148">Criar um Web Service de gerenciamento IIS de OData extensão</span><span class="sxs-lookup"><span data-stu-id="10c2d-148">Creating a Management OData IIS Extension Web Service</span></span>](./creating-a-management-odata-web-service.md)