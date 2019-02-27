---
title: Define o parâmetro de cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: a5822ef1ed3c9efb5957c20255783d515de8957a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847699"
---
# <a name="cmdlet-parameter-sets"></a>Cmdlet Parameter Sets (Conjuntos de Parâmetros de Cmdlets)

Windows PowerShell utiliza conjuntos de parâmetros que lhe permite escrever um único cmdlet que pode realizar ações diferentes para diferentes cenários. Conjuntos de parâmetros permitem expor diferentes parâmetros para o usuário e retorne informações distintas com base nos parâmetros especificados pelo utilizador.

## <a name="examples-of-parameter-sets"></a>Exemplos de conjuntos de parâmetros

Por exemplo, o `Get-EventLog` cmdlet (fornecido pelo Windows PowerShell) retorna informações diferentes, dependendo se o utilizador Especifica os `List` ou `LogName` parâmetro. Se o `List` parâmetro for especificado, o cmdlet retorna informações sobre os ficheiros de registo próprios, mas não as informações de eventos que contêm. Se o `LogName` parâmetro for especificado, o cmdlet retorna informações sobre os eventos no registo de eventos específico. O `List` e `LogName` parâmetros identificam dois conjuntos de parâmetros separados.

## <a name="unique-parameter"></a>Parâmetro exclusivo

Cada conjunto de parâmetros tem de ter um parâmetro único que o tempo de execução do Windows PowerShell pode utilizar para expor o conjunto de parâmetros adequada. Se possível, o único parâmetro deve ser um parâmetro obrigatório. Quando um parâmetro for obrigatório, o utilizador é forçado a especificar o parâmetro e o tempo de execução do Windows PowerShell pode usar esse parâmetro para identificar o parâmetro definido para utilizar. O único parâmetro não pode ser obrigatório se o seu cmdlet foi concebido para ser executado sem especificar quaisquer parâmetros.

## <a name="multiple-parameter-sets"></a>Vários conjuntos de parâmetros

Na ilustração seguinte, a coluna da esquerda mostra três conjuntos de parâmetros válido. O parâmetro A é exclusivo para o primeiro conjunto de parâmetros, parâmetro B é exclusivo para o segundo conjunto de parâmetros e parâmetro C é exclusivo para o terceiro conjunto de parâmetros. No entanto, na coluna da direita, os conjuntos de parâmetros não tem um parâmetro exclusivo.

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a>Requisitos do conjunto de parâmetros

Os seguintes requisitos se aplicam a todos os conjuntos de parâmetros.

- Cada conjunto de parâmetros tem de ter, pelo menos, um parâmetro exclusivo. Se possível, fazer este parâmetro um parâmetro obrigatório.

- Um conjunto de parâmetros que contém vários parâmetros posicionais tem de definir as posições exclusivas para cada parâmetro. Não existem dois parâmetros posicionais podem especificar a mesma posição.

- Apenas um parâmetro de um conjunto pode declarar o `ValueFromPipeline` palavra-chave com um valor de `true`. Podem definir vários parâmetros a `ValueFromPipelineByPropertyName` palavra-chave com um valor de `true`.

- Se não for especificado nenhum conjunto de parâmetros para um parâmetro, o parâmetro pertence a todos os conjuntos de parâmetros.

## <a name="default-parameter-sets"></a>Conjuntos de parâmetros padrão

Quando vários conjuntos de parâmetros são definidos, pode utilizar o `DefaultParameterSetName` palavra-chave do atributo Cmdlet para especificar o conjunto de parâmetros padrão. Windows PowerShell utiliza o parâmetro de padrão definido se ele não é possível determinar o parâmetro definido para utilizar com base nas informações fornecidas pelo comando. Para obter mais informações sobre o atributo de Cmdlet, consulte [declaração de atributo do Cmdlet](./cmdlet-attribute-declaration.md).

## <a name="declaring-parameter-sets"></a>Declaração de conjuntos de parâmetros

Para criar um conjunto de parâmetros, tem de especificar o `ParameterSetName` palavra-chave quando declara o atributo de parâmetro para cada parâmetro no conjunto de parâmetros. Para os parâmetros que pertencem a vários conjuntos de parâmetros, adicione um atributo de parâmetro para cada conjunto de parâmetros. Isto permite-lhe definir o parâmetro de forma diferente para cada conjunto de parâmetros. Por exemplo, pode definir um parâmetro como obrigatórios num conjunto e opcionais em outro. No entanto, cada conjunto de parâmetros tem de conter um parâmetro exclusivo.

No exemplo a seguir, o `UserName` parâmetro é o único parâmetro de conjunto de parâmetros Test01 e o `ComputerName` parâmetro é o parâmetro único do conjunto de parâmetros Test02. O `SharedParam` parâmetro pertence a ambos os conjuntos e é obrigatório para o parâmetro de Test01 definido, mas é opcional para o conjunto de parâmetros Test02.

```csharp
[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test02")]
public string ComputerName
{
  get { return computerName; }
  set { computerName = value; }
}
private string computerName;

[Parameter(Mandatory= true, ParameterSetName = "Test01")]
[Parameter(ParameterSetName = "Test02")]
public string SharedParam
{
    get { return sharedParam; }
    set { sharedParam = value; }
}
private string sharedParam;    [Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```