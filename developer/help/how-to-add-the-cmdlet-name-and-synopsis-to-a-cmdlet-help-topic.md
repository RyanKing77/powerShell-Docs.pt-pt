---
title: Como adicionar o nome do Cmdlet e o resumo para um tópico de ajuda do Cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083342"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a>How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic (Como Adicionar o Nome e Sinopse do Cmdlet a um Tópico de Ajuda de Cmdlet)

Esta secção descreve como adicionar o conteúdo que é apresentado nas secções nome e o resumo da ajuda do cmdlet. No ficheiro de ajuda, este conteúdo é adicionado ao nó de comando para cada cmdlet.

> [!NOTE]
> Para obter uma visão completa de um arquivo de ajuda, abra de um dos ficheiros dll Help.xml localizado no diretório de instalação do Windows PowerShell. Por exemplo, o ficheiro de Microsoft.PowerShell.Commands.Management.dll Help.xml contém conteúdo para vários dos cmdlets do Windows PowerShell.

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a>Para adicionar o nome do Cmdlet e uma sinopse

- O ajuda do cmdlet pode exibir duas descrições para o cmdlet. A descrição primeiro é uma breve descrição que é conhecida como o resumo. A segunda descrição é uma descrição mais detalhada que será discutida [adicionando a descrição detalhada para um tópico de ajuda do Cmdlet](./how-to-add-a-cmdlet-description.md). Ambas as descrições dessas devem ser gravadas como um único parágrafo.

- Na sinopse não repita o nome do cmdlet. Informar o utilizador que o cmdlet Get-Server obtém um servidor é breve, mas não informativos. Em vez disso, utilize sinónimos e adicione detalhes para a descrição.

  Exemplo: "Obtém um objeto que representa um computador local ou remoto."

- Utilize verbos simples, como "get", "Criar" e "alterar" no resumo. Evite utilizar "set", porque são vaga e palavras bonitas como "modificar."

  Exemplo: "Obtém informações sobre a assinatura Authenticode num ficheiro."

- Escreva na voz ativa. Por exemplo, "usar o objeto TimeSpan..." é bem mais claro que o "ao objeto TimeSpan pode ser utilizado para..."

- Evite o verbo "apresentação" ao descrever a cmdlets que obter objetos. Embora o Windows PowerShell apresenta os dados de cmdlet, é importante apresentar os utilizadores ao conceito de que o cmdlet devolve objetos do .NET Framework cujos dados podem não ser apresentados. Se enfatizar a exibição, o utilizador pode não perceber que o cmdlet poderá ter devolvido muitas outras propriedades úteis e métodos que não seja exibidos.

## <a name="see-also"></a>Veja Também

 [SDK do Windows PowerShell](../windows-powershell-reference.md)