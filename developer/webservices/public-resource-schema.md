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
ms.openlocfilehash: a9204ca7b28fc5792ef9bd18f6b0b24964de7386
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849295"
---
# <a name="public-resource-schema"></a>Public Resource Schema (Esquema de Recursos Públicos)

Gestão OData usa o MOF para definir recursos e as respetivas propriedades. As propriedades de uma entidade do OData da gestão correspondem diretamente às propriedades do tipo gerenciado devolvido pelo cmdlet subjacente.

## <a name="defining-a-resource"></a>Definir um recurso

Cada recurso corresponde a um objeto retornado por um cmdlet do Windows PowerShell. O ficheiro MOF do recurso de publc, vai definir um recurso ao declarar uma classe. A classe consiste em propriedades que correspondem às propriedades do objeto. Por exemplo, no exemplo a seguir, o [Diagnostics](/dotnet/api/System.Diagnostics.Process) classe é representada pela seguinte MOF.

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

Cada nome de propriedade é precedida por um tipo de dados. Os tipos de dados neste exemplo correspondem aos tipos de dados CLR primitivos nas estruturas de .NET, mas as propriedades também podem ser referências a outros recursos ou tipos complexos, ambos descritas mais tarde.

O `Key` qualificador indica que uma propriedade é utilizada para identificar exclusivamente uma instância de recurso. Um recurso pode ter mais de uma chave.

O `Required` qualificador indica que a propriedade é necessária. Se uma propriedade é o nome com o `Key` qualificador, é considerado como seja necessário e o `Required` qualificador não é necessário.

### <a name="complex-data-types"></a>Tipos de dados complexos

Propriedades de entidades podem ter tipos de dados complexos. Tipos de dados complexos são tipos que são constituídos por outros tipos, semelhantes a estruturas na linguagem de programação de C. Um tipo complexo é declarado no ficheiro MOF como uma classe com o `ComplexType` qualificador, como no exemplo seguinte.

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

Para declarar uma propriedade de entidade como um tipo complexo, declará-lo como um `string` que escreve o `EmbeddedInstance` qualificador, incluindo o nome do tipo complexo. A seguinte hshows de exemplo da declaração de uma propriedade do `PswsTest_ProcessModule` tipo declarado no exemplo anterior.

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a>Associação de entidades

Pode associar duas entidades usando os qualificadores de associação e AssocationClass. Para obter mais informações, consulte [associação de entidades do Management OData](./associating-management-odata-entities.md).

### <a name="derived-types"></a>Tipos derivados

Pode derivar um tipo de outro tipo. O tipo derivado herda todas as propriedades do tipo da qual deriva, além de quaisquer propriedades explicitamente derivadas. O exemplo seguinte mostra uma declaração de tipo e, em seguida, uma declaração de dois tipos derivados desse tipo.

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