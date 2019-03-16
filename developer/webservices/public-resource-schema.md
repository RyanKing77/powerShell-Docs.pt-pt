---
title: Esquema de recurso público | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e67298ee-a773-4402-8afb-d97ad0e030e5
caps.latest.revision: 4
ms.openlocfilehash: c7e20ff0f36e8cab2d414ff2e5924b3359ad9c60
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057251"
---
# <a name="public-resource-schema"></a><span data-ttu-id="3e649-102">Public Resource Schema (Esquema de Recursos Públicos)</span><span class="sxs-lookup"><span data-stu-id="3e649-102">Public Resource Schema</span></span>

<span data-ttu-id="3e649-103">Gestão OData usa o MOF para definir recursos e as respetivas propriedades.</span><span class="sxs-lookup"><span data-stu-id="3e649-103">Management OData uses MOF to define resources and their properties.</span></span> <span data-ttu-id="3e649-104">As propriedades de uma entidade do OData da gestão correspondem diretamente às propriedades do tipo gerenciado devolvido pelo cmdlet subjacente.</span><span class="sxs-lookup"><span data-stu-id="3e649-104">The properties of a Management OData entity correspond directly to the properties of the managed type returned by the underlying cmdlet.</span></span>

## <a name="defining-a-resource"></a><span data-ttu-id="3e649-105">Definir um recurso</span><span class="sxs-lookup"><span data-stu-id="3e649-105">Defining a resource</span></span>

<span data-ttu-id="3e649-106">Cada recurso corresponde a um objeto retornado por um cmdlet do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3e649-106">Each resource corresponds to an object returned by a Windows PowerShell cmdlet.</span></span> <span data-ttu-id="3e649-107">O ficheiro MOF de recurso público, vai definir um recurso ao declarar uma classe.</span><span class="sxs-lookup"><span data-stu-id="3e649-107">In the public resource MOF file, you define a resource by declaring a class.</span></span> <span data-ttu-id="3e649-108">A classe consiste em propriedades que correspondem às propriedades do objeto.</span><span class="sxs-lookup"><span data-stu-id="3e649-108">The class consists of properties that correspond to the properties of the object.</span></span> <span data-ttu-id="3e649-109">Por exemplo, no exemplo a seguir, o [Diagnostics](/dotnet/api/System.Diagnostics.Process) classe é representada pela seguinte MOF.</span><span class="sxs-lookup"><span data-stu-id="3e649-109">For example, in the following example, the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) class is represented by the following MOF.</span></span>

```csharp
class PswsTest_Process
{
    [Key] SInt32 Id;
    [Required] SInt32 BasePriority;
    [Required] SInt32 HandleCount;
    [Required] string MachineName;
    [Required] SInt32 MainWindowHandle;

    ...
};
```

<span data-ttu-id="3e649-110">Cada nome de propriedade é precedida por um tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="3e649-110">Each property name is preceded by a data type.</span></span> <span data-ttu-id="3e649-111">Os tipos de dados neste exemplo correspondem aos tipos de dados CLR primitivos nas estruturas de .NET, mas as propriedades também podem ser referências a outros recursos ou tipos complexos, ambos descritas mais tarde.</span><span class="sxs-lookup"><span data-stu-id="3e649-111">The data types in this example correspond to primitive CLR data types in the .NET Frameworks, but properties can also be references to other resources or complex types, which are both described later.</span></span>

<span data-ttu-id="3e649-112">O `Key` qualificador indica que uma propriedade é utilizada para identificar exclusivamente uma instância de recurso.</span><span class="sxs-lookup"><span data-stu-id="3e649-112">The `Key` qualifier indicates that a property is used to uniquely identify a resource instance.</span></span> <span data-ttu-id="3e649-113">Um recurso pode ter mais de uma chave.</span><span class="sxs-lookup"><span data-stu-id="3e649-113">A resource can have more than one key.</span></span>

<span data-ttu-id="3e649-114">O `Required` qualificador indica que a propriedade é necessária.</span><span class="sxs-lookup"><span data-stu-id="3e649-114">The `Required` qualifier indicates that the property is required.</span></span> <span data-ttu-id="3e649-115">Se uma propriedade é o nome com o `Key` qualificador, é considerado como seja necessário e o `Required` qualificador não é necessário.</span><span class="sxs-lookup"><span data-stu-id="3e649-115">If a property is labeled with the `Key` qualifier, it is considered to be required, and the `Required` qualifier is not necessary.</span></span>

### <a name="complex-data-types"></a><span data-ttu-id="3e649-116">Tipos de dados complexos</span><span class="sxs-lookup"><span data-stu-id="3e649-116">Complex data types</span></span>

<span data-ttu-id="3e649-117">Propriedades de entidades podem ter tipos de dados complexos.</span><span class="sxs-lookup"><span data-stu-id="3e649-117">Properties of entities can have complex data types.</span></span> <span data-ttu-id="3e649-118">Tipos de dados complexos são tipos que são constituídos por outros tipos, semelhantes a estruturas na linguagem de programação de C.</span><span class="sxs-lookup"><span data-stu-id="3e649-118">Complex data types are types that are made up of other types, similar to structs in the C programming language.</span></span> <span data-ttu-id="3e649-119">Um tipo complexo é declarado no ficheiro MOF como uma classe com o `ComplexType` qualificador, como no exemplo seguinte.</span><span class="sxs-lookup"><span data-stu-id="3e649-119">A complex type is declared in the MOF file as a class with the `ComplexType` qualifier, as in the following example.</span></span>

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

<span data-ttu-id="3e649-120">Para declarar uma propriedade de entidade como um tipo complexo, declará-lo como um `string` que escreve o `EmbeddedInstance` qualificador, incluindo o nome do tipo complexo.</span><span class="sxs-lookup"><span data-stu-id="3e649-120">To declare an entity property as a complex type, you declare it as a `string` type with the `EmbeddedInstance` qualifier, including the name of the complex type.</span></span> <span data-ttu-id="3e649-121">O exemplo seguinte mostra a declaração de uma propriedade do `PswsTest_ProcessModule` tipo declarado no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="3e649-121">The following example shows the declaration of a property of the `PswsTest_ProcessModule` type declared in the previous example.</span></span>

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a><span data-ttu-id="3e649-122">Associação de entidades</span><span class="sxs-lookup"><span data-stu-id="3e649-122">Associating entities</span></span>

<span data-ttu-id="3e649-123">Pode associar duas entidades usando os qualificadores de associação e AssociationClass.</span><span class="sxs-lookup"><span data-stu-id="3e649-123">You can associate two entities by using the Association and AssociationClass qualifiers.</span></span> <span data-ttu-id="3e649-124">Para obter mais informações, consulte [associação de entidades do Management OData](./associating-management-odata-entities.md).</span><span class="sxs-lookup"><span data-stu-id="3e649-124">For more information, see [Associating Management OData Entities](./associating-management-odata-entities.md).</span></span>

### <a name="derived-types"></a><span data-ttu-id="3e649-125">Tipos derivados</span><span class="sxs-lookup"><span data-stu-id="3e649-125">Derived types</span></span>

<span data-ttu-id="3e649-126">Pode derivar um tipo de outro tipo.</span><span class="sxs-lookup"><span data-stu-id="3e649-126">You can derive a type from another type.</span></span> <span data-ttu-id="3e649-127">O tipo derivado herda todas as propriedades do tipo da qual deriva, além de quaisquer propriedades explicitamente derivadas.</span><span class="sxs-lookup"><span data-stu-id="3e649-127">The derived type inherits all of the properties of the type from which it derives in addition to any properties explicitly derived.</span></span> <span data-ttu-id="3e649-128">O exemplo seguinte mostra uma declaração de tipo e, em seguida, uma declaração de dois tipos derivados desse tipo.</span><span class="sxs-lookup"><span data-stu-id="3e649-128">The following example shows a type declaration and then a declaration of two types derived from that type.</span></span>

```csharp
Class Product {

    [Key] String ProductName;

};

Class DairyProduct : Product {

    Uint16 PercentFat;
};
Class POPProduct : Product {

    Boolean IsCarbonated;
};
```