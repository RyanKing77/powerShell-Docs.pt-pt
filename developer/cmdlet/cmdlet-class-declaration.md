---
title: Declaração de classe cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], declaring
- declaring cmdlets [PowerShell SDK]
ms.assetid: 1fcc4c5e-0c75-496c-a712-5f844e310576
caps.latest.revision: 14
ms.openlocfilehash: 3e410087438ac99526049f99e5c768c017a29848
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845725"
---
# <a name="cmdlet-class-declaration"></a>Cmdlet Class Declaration (Declaração da Classe de Cmdlets)

Uma classe de Microsoft .NET Framework está declarada como um cmdlet, especificando o **Cmdlet** atributo como metadados para a classe. (A **Cmdlet** atributo é o único atributo obrigatório para todos os cmdlets). Quando especificar a **Cmdlet** atributo, tem de especificar o par de verbo e substantivo que identifica o cmdlet para o utilizador. Além disso, tem de descrever a funcionalidade do Windows PowerShell que suporta o cmdlet. Para obter mais informações sobre a sintaxe de declaração é utilizada para especificar a **Cmdlet** de atributos, consulte [declaração de atributo do Cmdlet](./cmdlet-attribute-declaration.md).

> [!NOTE]
> O **Cmdlet** atributo é definido pela [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) classe. As propriedades dessa classe correspondem aos parâmetros de declaração que são utilizados quando declara o atributo.

## <a name="nouns"></a>Substantivos

O substantivo do cmdlet Especifica os recursos no qual o cmdlet atua. O substantivo diferencia os seus cmdlets de outros cmdlets.

Substantivos em nomes de cmdlet tem de ser específico e, no caso de substantivos genéricos, tal como *servidor*, é melhor adicionar um prefixo curto que diferencia o recurso a partir de outros recursos semelhantes. Por exemplo, é um nome de cmdlet que inclui um substantivo com um prefixo `Get-SQLServer`. A combinação de um substantivo específico com um verbo mais geral permite ao utilizador localizar rapidamente o cmdlet por sua ação e, em seguida, identifique o cmdlet ao seu recurso, evitando duplicação de nome do cmdlet desnecessários.

Para obter uma lista de carateres especiais que não pode ser utilizado em nomes de cmdlet, consulte [diretrizes de desenvolvimento necessário](./required-development-guidelines.md).

## <a name="verbs"></a>Verbos

Quando especificar um verbo, as diretrizes de desenvolvimento exigem que utilize um dos verbos predefinidos fornecidos pelo Windows PowerShell. Ao utilizar um desses verbos predefinidos, irá garantir a consistência entre os cmdlets que escreve e os cmdlets que são escritos pela Microsoft e por outras pessoas. Por exemplo, o verbo "Get" é utilizado para cmdlets que obtêm dados.

Para obter mais informações sobre as diretrizes para verbos, consulte [nomes de verbo do Cmdlet](./approved-verbs-for-windows-powershell-commands.md). Para obter uma lista de carateres especiais que não pode ser utilizado em nomes de cmdlet, consulte [diretrizes de desenvolvimento necessário](./required-development-guidelines.md).

## <a name="supporting-windows-powershell-functionality"></a>Suporte a funcionalidade do Windows PowerShell

O **Cmdlet** atributo também permite que especifique de que seu cmdlet oferece suporte a algumas das funcionalidades comuns que é fornecida pelo Windows PowerShell. Isto inclui suporte para funcionalidades comuns, tais como a confirmação de comentários do utilizador (referida como suporte para a funcionalidade de ShouldProcess) e suporte para transações. (Suporte para transações foi introduzido no Windows PowerShell 2.0).

Para obter mais informações sobre a sintaxe de declaração é utilizada para especificar a **Cmdlet** de atributos, consulte [declaração de atributo do Cmdlet](./cmdlet-attribute-declaration.md).

## <a name="cmdlet-class-definition"></a>Definição de classe do cmdlet

O código a seguir é a definição de uma classe de cmdlet GetProc. Observe que esse Pascal casing é utilizado e que o nome da classe inclui o verbo e substantivo do cmdlet.

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a>Letras maiúsculas e minúsculas de Pascal

Ao atribuir um nome de cmdlets, utilize Pascal casing. Por exemplo, o `Get-Item` e `Get-ItemProperty` cmdlets Mostrar a forma correta para utilizar a capitalização quando atribuir nomes a cmdlets.

## <a name="see-also"></a>Veja Também

[System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute)

[Declaração CmdletAttribute](./cmdlet-attribute-declaration.md)

[Nomes de verbo do cmdlet](./approved-verbs-for-windows-powershell-commands.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
