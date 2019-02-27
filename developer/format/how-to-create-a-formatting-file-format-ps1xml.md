---
title: Como criar um ficheiro de formatação (. format.ps1xml) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851689"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a>How to Create a Formatting File (.format.ps1xml) (Como Criar um Ficheiro de Formatação [.format.ps1xml])

Este tópico descreve como criar um ficheiro de formatação (. format.ps1xml).

> [!NOTE]
> Também pode criar um ficheiro de formatação fazendo uma cópia de um dos ficheiros fornecidos pelo Windows PowerShell. Se fizer uma cópia de um arquivo existente, elimine a assinatura digital existente e adicionar sua própria assinatura para o novo ficheiro.

### <a name="to-create-a-formatps1xml-file"></a>Para criar um. format.ps1xml ficheiro.

1. Crie um ficheiro de texto (. txt) com um texto editor como o bloco de notas.

2. Copie as seguintes linhas no arquivo de formatação.

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - O \<configuração >\</Configuration > etiquetas definem raiz `Configuration` nó. Este nó irão estar entre todas as outras etiquetas XML.

   - O <ViewDefinitions> </ViewDefinitions> definem etiquetas a `ViewDefinitions` nó. Todas as vistas são definidas dentro deste nó.

3. Guarde o ficheiro para a pasta de instalação do Windows PowerShell, para a pasta do módulo ou para uma subpasta da pasta de módulo. Utilize o seguinte formato de nome quando guardar o ficheiro: `MyFile.format.ps1xml`. Formatação de ficheiros tem de utilizar o `.format.ps1xml` extensão.

   Agora está pronto para adicionar vistas para o ficheiro de formatação. Não existe nenhum limite para o número de visualizações que podem ser definidos num arquivo de formatação. Pode adicionar uma vista única para cada objeto, várias exibições para o mesmo objeto ou uma vista única que é utilizada por vários objetos.

## <a name="see-also"></a>Veja Também

[Escrever do Windows PowerShell, formatação e os tipos de ficheiro](./writing-a-powershell-formatting-file.md)
