---
title: Como criar o ficheiro de ajuda do Cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 08e05939f8aee42f2cd502a3da7a528d8460dec1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848896"
---
# <a name="how-to-create-the-cmdlet-help-file"></a>How to Create the Cmdlet Help File (Como Criar um Ficheiro de Ajuda de Cmdlet)

Esta secção descreve como criar um ficheiro XML válido, que contém conteúdos para tópicos de ajuda do cmdlet Windows PowerShell. Esta secção descreve como nomear o arquivo de ajuda, como adicionar os cabeçalhos XML apropriados e como adicionar nós que irão conter as diferentes seções do conteúdo da ajuda cmdlet.

> [!NOTE]
> Para obter uma visão completa de um arquivo de ajuda, abra de um dos ficheiros dll Help.xml localizado no diretório de instalação do Windows PowerShell. Por exemplo, o ficheiro de Microsoft.PowerShell.Commands.Management.dll Help.xml contém conteúdo para vários dos cmdlets do Windows PowerShell.

### <a name="how-to-create-a-cmdlet-help-file"></a>Como criar um ficheiro de ajuda do Cmdlet

1. Crie um arquivo de texto e guarde-o com codificação UTF8. O nome do ficheiro tem de ter o seguinte formato para que o Windows PowerShell pode detetá-lo como um arquivo de ajuda do cmdlet.

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. Adicione os seguintes cabeçalhos XML para o arquivo de texto. Lembre-se de que o ficheiro vai ser validado no esquema de linguagem de modelagem de agente multi (MAML). Atualmente, o Windows PowerShell não fornece quaisquer ferramentas para validar o ficheiro.

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. Adicione um nó de comando para o ficheiro de ajuda do cmdlet para cada cmdlet no assembly. Cada nó no nó de comando está relacionado com as diferentes secções do tópico de ajuda do cmdlet.

   A tabela seguinte lista o elemento XML para cada nó, seguido de uma descrição de cada nó.

   |Nó|Descrição|
   |----------|-----------------|
   |`<details>`|Adiciona o conteúdo para as secções de nome e uma sinopse do tópico de ajuda do cmdlet. Para obter mais informações, consulte [como adicionar o nome do Cmdlet e sinopse](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).|
   |`<maml:description>`|Adiciona o conteúdo para a seção de descrição do tópico de ajuda do cmdlet. Para obter mais informações, consulte [como adicionar a descrição detalhada para um tópico de ajuda do Cmdlet](./how-to-add-a-cmdlet-description.md).|
   |`<command:syntax>`|Adiciona o conteúdo para a secção de sintaxe do tópico de ajuda do cmdlet. Para obter mais informações, consulte [como a sintaxe adicionar um tópico de ajuda do Cmdlet](./how-to-add-syntax-to-a-cmdlet-help-topic.md).|
   |`<command:parameters>`|Adiciona o conteúdo para a secção de parâmetros do tópico de ajuda do cmdlet. Para obter mais informações, consulte [como adicionar parâmetros para um tópico de ajuda do Cmdlet](./how-to-add-parameter-information.md).|
   |`<command:inputTypes>`|Adiciona o conteúdo para a secção de entradas do tópico de ajuda do cmdlet. Para obter mais informações, consulte [como adicionar tipos de entrada para um tópico de ajuda do Cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md).|
   |`<command:returnValues>`|Adiciona o conteúdo para a secção de saídas do tópico de ajuda do cmdlet. Para obter mais informações, consulte [como adicionar retornar valores para um tópico de ajuda do Cmdlet](./how-to-add-return-values-to-a-cmdlet-help-topic.md).|
   |`<maml:alertset>`|Adiciona o conteúdo para a secção de notas do tópico de ajuda do cmdlet. Para obter mais informações, consulte [notas de como adicionar um tópico de ajuda do Cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md).|
   |`<command:examples>`|Adiciona o conteúdo para a secção de exemplos do tópico de ajuda do cmdlet. Para obter mais informações, consulte [como adicionar exemplos para um tópico de ajuda do Cmdlet](./how-to-add-examples-to-a-cmdlet-help-topic.md).|
   |`<maml:relatedLinks>`|Adiciona o conteúdo para a secção de LINKS relacionados do tópico de ajuda do cmdlet. Para obter mais informações, consulte [como adicionar Links relacionados para um tópico de ajuda do Cmdlet](./how-to-add-related-links-to-a-cmdlet-help-topic.md).|

## <a name="example"></a>Exemplo

 Eis um exemplo de um nó de comando que inclui os nós para as diversas secções do tópico de ajuda do cmdlet.

```xml
<command:command
  xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
  xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
  <command:details>
    <!--Add name an synopsis here-->
  </command:details>
  <maml:description>
    <!--Add detailed description here-->
  </maml:description>
  <command:syntax>
    <!--Add syntax information here-->
  </command:syntax>
  <command:parameters>
    <!--Add parameter information here-->
  </command:parameters>
  <command:inputTypes>
    <!--Add input type information here-->
  </command:inputTypes>
  <command:returnValues>
    <!--Add return value information here-->
  </command:returnValues>
  <maml:alertSet>
    <!--Add Note information here-->
  </maml:alertSet>
  <command:examples>
    <!--Add cmdlet examples here-->
  </command:examples>
  <maml:relatedLinks>
    <!--Add links to related content here-->
  </maml:relatedLinks>
</command:command>
```

## <a name="see-also"></a>Veja Também

 [Como adicionar o nome do Cmdlet e sinopse](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [Como adicionar a descrição detalhada para um tópico de ajuda do Cmdlet](./how-to-add-a-cmdlet-description.md)

 [Como adicionar a sintaxe para um tópico de ajuda do Cmdlet](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Como adicionar parâmetros a um tópico de ajuda do Cmdlet](./how-to-add-parameter-information.md)

 [Como adicionar tipos de entrada para um tópico de ajuda do Cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Como adicionar valores de retorno para um tópico de ajuda do Cmdlet](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Como adicionar notas para um tópico de ajuda do Cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Como adicionar exemplos para um tópico de ajuda do Cmdlet](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Como adicionar Links relacionados a um tópico de ajuda do Cmdlet](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [SDK do Windows PowerShell](../windows-powershell-reference.md)