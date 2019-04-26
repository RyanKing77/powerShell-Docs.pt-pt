---
title: Como adicionar uma descrição de Cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083523"
---
# <a name="how-to-add-a-cmdlet-description"></a>How to Add a Cmdlet Description (Como Adicionar a Descrição de um Cmdlet)

Esta secção descreve como adicionar o conteúdo que é apresentado na secção Descrição do cmdlet ajuda. No ficheiro de ajuda, este conteúdo é adicionado ao nó de comando para cada cmdlet.

> [!NOTE]
> Para obter uma visão completa de um arquivo de ajuda, abra de um dos ficheiros dll Help.xml localizado no diretório de instalação do Windows PowerShell. Por exemplo, o ficheiro de Microsoft.PowerShell.Commands.Management.dll Help.xml contém conteúdo para vários dos cmdlets do Windows PowerShell.

### <a name="to-add-a-description"></a>Para adicionar uma descrição

- Começar explicando as funcionalidades básicas do cmdlet em mais detalhes. Em muitos casos, pode explicar os termos utilizados no nome do cmdlet e ilustrar os conceitos familiarizados com um exemplo. Por exemplo, se o cmdlet acrescenta dados a um ficheiro, explique que ele adiciona dados ao final de um arquivo existente.

- Para localizar todas as funcionalidades do cmdlet, reveja a lista de parâmetros. Descrever a função principal do cmdlet e, em seguida, inclua outras funções e funcionalidades. Por exemplo, se a principal função do cmdlet é alterar uma propriedade, mas o cmdlet pode alterar todas as propriedades, diria isso na descrição detalhada. Se os parâmetros do cmdlet permitir que os utilizadores solicitam informações de maneiras diferentes, explicá-lo.

- Inclua informações sobre as formas que os utilizadores podem utilizar o cmdlet, além das utilizações óbvias. Por exemplo, pode usar o objeto que o `Get-Host` cmdlet obtém para alterar a cor do texto na janela de comando do Windows PowerShell.

  Exemplo:  "O `Get-Acl` cmdlet obtém objetos que representam o descritor de segurança de um ficheiro ou recurso. O descritor de segurança contém as listas de controlo de acesso (ACLs) do recurso. A ACL Especifica as permissões que os utilizadores e grupos de utilizadores têm de aceder ao recurso."

- A descrição detalhada deve descrever o cmdlet, mas ele deve descreve conceitos que utiliza o cmdlet. Colocar definições de conceito nas notas adicionais.

## <a name="see-also"></a>Veja Também

[SDK do Windows PowerShell](../windows-powershell-reference.md)
