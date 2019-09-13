---
title: Conjuntos de parâmetros de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: d8c00c7ffd369a32af151836785a2c5f47b05a68
ms.sourcegitcommit: 889b93d170aeb3d444288e7ccf67e62ce822cb7c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/12/2019
ms.locfileid: "70936191"
---
# <a name="cmdlet-parameter-sets"></a>Conjuntos de parâmetros de cmdlet

O PowerShell usa conjuntos de parâmetros para permitir que você escreva um único cmdlet que possa realizar ações diferentes para cenários diferentes. Os conjuntos de parâmetros permitem que você exponha parâmetros diferentes para o usuário. E, para retornar informações diferentes com base nos parâmetros especificados pelo usuário.

## <a name="examples-of-parameter-sets"></a>Exemplos de conjuntos de parâmetros

Por exemplo, o cmdlet `Get-EventLog` do PowerShell retorna informações diferentes dependendo se o usuário especifica a **lista** ou o parâmetro **LogName** . Se o parâmetro **list** for especificado, o cmdlet retornará informações sobre os próprios arquivos de log, mas não as informações de evento que eles contêm. Se o parâmetro **LogName** for especificado, o cmdlet retornará informações sobre os eventos em um log de eventos específico. Os parâmetros **list** e **LogName** identificam dois conjuntos de parâmetros separados.

## <a name="unique-parameter"></a>Parâmetro exclusivo

Cada conjunto de parâmetros deve ter um parâmetro exclusivo que o tempo de execução do PowerShell usa para expor o conjunto de parâmetros apropriado. Se possível, o parâmetro exclusivo deve ser um parâmetro obrigatório. Quando um parâmetro é obrigatório, o usuário deve especificar o parâmetro e o tempo de execução do PowerShell usa esse parâmetro para identificar o conjunto de parâmetros. O parâmetro exclusivo não poderá ser obrigatório se o cmdlet for projetado para ser executado sem especificar parâmetros.

## <a name="multiple-parameter-sets"></a>Vários conjuntos de parâmetros

Na ilustração a seguir, a coluna à esquerda mostra três conjuntos de parâmetros válidos. O **parâmetro A** é exclusivo para o primeiro conjunto de parâmetros, o **parâmetro B** é exclusivo para o segundo conjunto de parâmetros, e o **parâmetro C** é exclusivo para o terceiro conjunto de parâmetros. Na coluna à direita, os conjuntos de parâmetros não têm um parâmetro exclusivo.

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a>Requisitos do conjunto de parâmetros

Os requisitos a seguir se aplicam a todos os conjuntos de parâmetros.

- Cada conjunto de parâmetros deve ter pelo menos um parâmetro exclusivo. Se possível, torne esse parâmetro um parâmetro obrigatório.

- Um conjunto de parâmetros que contém vários parâmetros posicionais deve definir posições exclusivas para cada parâmetro. Dois parâmetros posicionais não podem especificar a mesma posição.

- Somente um parâmetro em um conjunto pode declarar a `ValueFromPipeline` palavra-chave com um `true`valor de.
  Vários parâmetros podem definir a `ValueFromPipelineByPropertyName` palavra-chave com um `true`valor de.

- Se nenhum conjunto de parâmetros for especificado para um parâmetro, o parâmetro pertencerá a todos os conjuntos de parâmetros.

> [!NOTE]
> Para um cmdlet ou uma função, há um limite de conjuntos de parâmetros 32.

## <a name="default-parameter-sets"></a>Conjuntos de parâmetros padrão

Quando vários conjuntos de parâmetros são definidos, você pode usar `DefaultParameterSetName` a palavra-chave do atributo **cmdlet** para especificar o conjunto de parâmetros padrão. O PowerShell usará o conjunto de parâmetros padrão se não puder determinar o conjunto de parâmetros a ser usado com base nas informações fornecidas pelo comando. Para obter mais informações sobre o atributo **cmdlet** , consulte [declaração de atributo de cmdlet](./cmdlet-attribute-declaration.md).

## <a name="declaring-parameter-sets"></a>Declarando conjuntos de parâmetros

Para criar um conjunto de parâmetros, você deve especificar `ParameterSetName` a palavra-chave ao declarar o atributo de **parâmetro** para cada parâmetro no conjunto de parâmetros. Para parâmetros que pertencem a vários conjuntos de parâmetros, adicione um atributo de **parâmetro** para cada conjunto de parâmetros. Esse atributo permite que você defina o parâmetro de forma diferente para cada conjunto de parâmetros. Por exemplo, você pode definir um parâmetro como obrigatório em um conjunto e opcional em outro. No entanto, cada conjunto de parâmetros deve conter um parâmetro exclusivo. Para obter mais informações, consulte [declaração de atributo de parâmetro](parameter-attribute-declaration.md).

No exemplo a seguir, o parâmetro **username** é o parâmetro exclusivo do conjunto `Test01` de parâmetros e o parâmetro **ComputerName** `Test02` é o parâmetro exclusivo do conjunto de parâmetros. O parâmetro **SharedParam** pertence a ambos os conjuntos e é obrigatório para `Test01` o conjunto de parâmetros, mas `Test02` opcional para o conjunto de parâmetros.

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
private string sharedParam;
```
