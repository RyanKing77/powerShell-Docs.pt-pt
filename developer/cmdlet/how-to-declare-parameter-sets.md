---
title: Como declarar os conjuntos de parâmetros | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46905eb9-64d7-4c55-9c2a-7bc7bf04e14b
caps.latest.revision: 10
ms.openlocfilehash: 6c2e5891a8e3f24969c12a2e57dc5ae8caa68e41
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067897"
---
# <a name="how-to-declare-parameter-sets"></a>How to Declare Parameter Sets (Como Declarar Conjuntos de Parâmetros)

Este exemplo mostra como definir dois conjuntos de parâmetros ao declarar parâmetros para um cmdlet. Cada conjunto de parâmetros tem um parâmetro único e um parâmetro partilhado que é utilizado por ambos os conjuntos de parâmetros. Para obter mais informações sobre os conjuntos de parâmetros, incluindo como especificar o conjunto de parâmetros padrão, consulte [define o parâmetro de Cmdlet](./cmdlet-parameter-sets.md).

> [!IMPORTANT]
> Sempre que possível, defina o parâmetro exclusivo de um parâmetro definido como um parâmetro necessário. No entanto, se pretender que o seu cmdlet seja executado sem especificar quaisquer parâmetros, o único parâmetro pode ser um parâmetro opcional. Por exemplo, o único parâmetro do `Get-Command` cmdlet é opcional.

## <a name="how-to-define-two-parameter-sets"></a>Como definir dois conjuntos de parâmetros

1. Adicionar o `ParameterSet` palavra-chave para o atributo de parâmetro para o parâmetro único do primeiro conjunto de parâmetros.

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test01")]
   public string UserName
   {
     get { return userName; }
     set { userName = value; }
   }
   private string userName;
   ```

2. Adicionar o `ParameterSet` palavra-chave para o atributo de parâmetro para o parâmetro único do segundo conjunto de parâmetros.

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test02")]
   public string ComputerName
   {
     get { return computerName; }
     set { computerName = value; }
   }
   private string computerName;
   ```

3. Para o parâmetro que pertença a ambos os conjuntos de parâmetros, adicione um atributo de parâmetro para cada conjunto de parâmetros e, em seguida, adicione o `ParameterSet` palavra-chave para cada conjunto. Em cada atributo de parâmetro, pode especificar como esse parâmetro é definido. Um parâmetro pode ser opcional num conjunto e obrigatório em outro.

   ```csharp
   [Parameter(Mandatory= true, ParameterSetName = "Test01")]
   [Parameter(ParameterSetName = "Test02")]
   public string SharedParam
   {
       get { return sharedParam; }
       set { sharedParam = value; }
   }
   private string sharedParam;
   ```

## <a name="see-also"></a>Veja Também

[Conjuntos de parâmetros do cmdlet](./cmdlet-parameter-sets.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
