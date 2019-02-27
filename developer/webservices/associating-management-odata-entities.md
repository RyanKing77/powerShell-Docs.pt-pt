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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850191"
---
# <a name="associating-management-odata-entities"></a>Associating Management OData Entities (Associar Entidades OData de Gestão)

Muitas vezes é útil criar uma associação entre duas entidades de OData de gestão diferentes. Por exemplo, um serviço de gestão OData ter entidades que gerem um catálogo de produtos que estão organizados em categorias e definir as entidades `Product` e `Category`. Ao associar estas duas entidades, um cliente pode obter informações sobre todos os produtos numa categoria com um único pedido para o serviço web.

Um exemplo que mostra como criar associações entre entidades pode ser baixado do site [exemplo de associação](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).

## <a name="creating-the-association-in-the-resource-schema-file"></a>Criar a associação no arquivo de esquema de recursos

O MOF seguinte define duas entidades. Iremos criar uma associação entre elas.

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

O `Category` classe define uma propriedade que é uma matriz de nomes dos produtos que pertencem a essa categoria.

Para associar as duas entidades, tem de definir uma classe com o `Association` atributos no arquivo MOF de esquema de recursos para o serviço. A classe tem de definir as duas entidades para ser associado, chamado `ends` da association. O exemplo seguinte mostra uma definição de uma classe que define uma associação entre as entidades de categoria e produtos.

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

Também tem de alterar a declaração da propriedade de produtos na classe de categoria. Utilizar o `AssociationClass` palavra-chave para especificar que a propriedade é uma extremidade da association. A propriedade também tem de ser definida como uma referência a uma entidade separada, em vez de uma matriz de cadeias de caracteres. Fazer isso usando o `ref` palavra-chave. O exemplo seguinte mostra a definição de propriedade para a associação.

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

Por fim, deve declarar outro extremo da associação ao adicionar uma definição de propriedade para o `Product` classe. Esta é uma referência a uma matriz ou a uma única entidade. Supondo que cada produto pertence a apenas uma categoria, a definição seria da seguinte forma.

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

As propriedades que representam as duas extremidades da associação são chamadas de propriedades de navegação.

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a>Passos para associar entidades no arquivo de esquema de recursos

- Definir a associação como uma classe com o `Association` palavra-chave.

- Defina as extremidades da associação com a palavra-chave de AssociationClass para qualificar propriedades das entidades associadas.

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a>Criar a associação no arquivo XML de mapeamento de recursos

Há três casos diferentes a serem considerados ao mapeamento de uma associação no arquivo XML de mapeamento de recursos.

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a>Determinar como associar entidades no arquivo de mapeamento de recursos

- Se a propriedade de navegação está presente no subjacentes. Tipo de .NET framework e essa propriedade contém chaves estrangeiras, nenhum mapeamento explícito é necessário.

- Se a propriedade de navegação não existe no tipo de .NET Framework subjacente, tem de especificar um cmdlet que obtém a lista de chaves das instâncias associadas. Faça isso adicionando um `Association` elemento aninhado a `CmdletImplementation` elemento, seguindo os elementos que definem o `cmdlets` para os outros comandos CRUD.

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

- Se a propriedade de navegação existe no tipo de .NET Framework subjacente, mas contém instâncias de objeto, em vez de chaves estrangeiras, então tem de criar um cmdlet (ao escrever um script ou função do Windows PowerShell) para obter as chaves estrangeiras. Em seguida, especifique esse cmdlet no arquivo de mapeamento de recursos. Por exemplo, o script para obter as chaves teria o aspeto semelhante ao seguinte.

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  E o XML no arquivo de mapeamento de recursos teria uma aparência semelhante ao seguinte.

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

- Além de especificar um cmdlet para obter as entidades associadas, também pode especificar cmdlets para adicionar e remover as referências da coleção. O exemplo a seguir supõe que os cmdlets Add ProductToCategory e Remove-ProductFromCategory existem (eles também podem ser definidos num script ou função do exemplo anterior).

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

## <a name="querying-associated-entities"></a>Consultar entidades associadas

O cliente pode obter uma lista das instâncias associadas com uma entidade com a criação de consultas específicas.

#### <a name="constructing-queries-for-associated-entities"></a>Construir consultas para entidades associadas

- Um cliente pode pedir os detalhes de uma categoria sem recuperar seus produtos associados. Por exemplo, o pedido seguinte obtém os detalhes do `food` categoria.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  Para obter os produtos associados da categoria (mas não os detalhes da categoria em si, o cliente especifica a propriedade de navegação no pedido.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- Para obter apenas os URLs dos produtos, utilize o `$links` qualificador no pedido.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- O cliente pode obter os detalhes de categoria e seus produtos associados com o `$expand` qualificador.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a>Consulte Também

[Criar um Web Service de gerenciamento IIS de OData extensão](./creating-a-management-odata-web-service.md)