---
title: Atributos de cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [PowerShell SDK]
- attributes [PowerShell SDK], described
ms.assetid: d3f4f652-d929-4c27-9358-9baa390a094c
caps.latest.revision: 14
ms.openlocfilehash: b06faf7204213b383b25685837941ad63dcb225b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845354"
---
# <a name="cmdlet-attributes"></a><span data-ttu-id="dbe99-102">Cmdlet Attributes (Atributos de Cmdlet)</span><span class="sxs-lookup"><span data-stu-id="dbe99-102">Cmdlet Attributes</span></span>

<span data-ttu-id="dbe99-103">Windows PowerShell define vários atributos que pode usar para adicionar funcionalidade comum a seus cmdlets sem implementar essa funcionalidade dentro de seu próprio código.</span><span class="sxs-lookup"><span data-stu-id="dbe99-103">Windows PowerShell defines several attributes that you can use to add common functionality to your cmdlets without implementing that functionality within your own code.</span></span> <span data-ttu-id="dbe99-104">Isto inclui o atributo de Cmdlet que identifica uma classe de Microsoft .NET Framework como uma classe cmdlet, o atributo OutputType que especifica os tipos do .NET Framework devolvidos pelo cmdlet, o atributo de parâmetro que identifica as propriedades públicas como cmdlet parâmetros e muito mais.</span><span class="sxs-lookup"><span data-stu-id="dbe99-104">This includes the Cmdlet attribute that identifies a Microsoft .NET Framework class as a cmdlet class, the OutputType attribute that specifies the .NET Framework types returned by the cmdlet, the Parameter attribute that identifies public properties as cmdlet parameters, and more.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="dbe99-105">Nesta Secção</span><span class="sxs-lookup"><span data-stu-id="dbe99-105">In This Section</span></span>

<span data-ttu-id="dbe99-106">[Atributos no código de Cmdlet](./attributes-in-cmdlet-code.md) descreve a vantagem de usar atributos no código de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dbe99-106">[Attributes in Cmdlet Code](./attributes-in-cmdlet-code.md) Describes the benefit of using attributes in cmdlet code.</span></span>

<span data-ttu-id="dbe99-107">[Os tipos de atributo](./attribute-types.md) descreve os atributos diferentes que podem decorar uma classe cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dbe99-107">[Attribute Types](./attribute-types.md) Describes the different attributes that can decorate a cmdlet class.</span></span>

<span data-ttu-id="dbe99-108">[Declaração de atributo de alias](./alias-attribute-declaration.md) descreve como definir aliases para um nome de parâmetro de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dbe99-108">[Alias Attribute Declaration](./alias-attribute-declaration.md) Describes how to define aliases for a cmdlet parameter name.</span></span>

<span data-ttu-id="dbe99-109">[Declaração de atributo do cmdlet](./cmdlet-attribute-declaration.md) descreve como definir uma classe do .NET Framework como um cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dbe99-109">[Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md) Describes how to define a .NET Framework class as a cmdlet.</span></span>

<span data-ttu-id="dbe99-110">[Declaração de atributo de credenciais](./credential-attribute-declaration.md) descreve como adicionar suporte para a conversão de entrada de cadeia de caracteres num [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto.</span><span class="sxs-lookup"><span data-stu-id="dbe99-110">[Credential Attribute Declaration](./credential-attribute-declaration.md) Describes how to add support for converting string input into a [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span>

<span data-ttu-id="dbe99-111">[Atributo OutputType declaração](./outputtype-attribute-declaration.md) descreve como especificar os tipos do .NET Framework devolvidos pelo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dbe99-111">[OutputType attribute Declaration](./outputtype-attribute-declaration.md) Describes how to specify the .NET Framework types returned by the cmdlet.</span></span>

<span data-ttu-id="dbe99-112">[Declaração de atributo de parâmetro](./parameter-attribute-declaration.md) descreve como definir os parâmetros de um cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dbe99-112">[Parameter Attribute Declaration](./parameter-attribute-declaration.md) Describes how to define the parameters of a cmdlet.</span></span>

<span data-ttu-id="dbe99-113">[Declaração de atributo ValidateCount](./validatecount-attribute-declaration.md) descreve como definir o número de argumentos são permitidos para um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="dbe99-113">[ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md) Describes how to define how many arguments are allowed for a parameter.</span></span>

<span data-ttu-id="dbe99-114">[Declaração de atributo ValidateLength](./validatelength-attribute-declaration.md) descreve como definir o comprimento (em carateres) de um argumento do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="dbe99-114">[ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md) Describes how to define the length (in characters) of a parameter argument.</span></span>

<span data-ttu-id="dbe99-115">[Declaração de atributo ValidatePattern](./validatepattern-attribute-declaration.md) descreve como definir os padrões válidos para um argumento do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="dbe99-115">[ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md) Describes how to define the valid patterns for a parameter argument.</span></span>

<span data-ttu-id="dbe99-116">[Declaração de atributo ValidateRange](./validaterange-attribute-declaration.md) descreve como definir o intervalo válido de um argumento do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="dbe99-116">[ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md) Describes how to define the valid range for a parameter argument.</span></span>

<span data-ttu-id="dbe99-117">[Declaração de atributo ValidateSet](./validateset-attribute-declaration.md) descreve como definir os valores possíveis para um argumento do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="dbe99-117">[ValidateSet Attribute Declaration](./validateset-attribute-declaration.md) Describes how to define the possible values for a parameter argument.</span></span>

## <a name="reference"></a><span data-ttu-id="dbe99-118">Referência</span><span class="sxs-lookup"><span data-stu-id="dbe99-118">Reference</span></span>

[<span data-ttu-id="dbe99-119">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="dbe99-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)