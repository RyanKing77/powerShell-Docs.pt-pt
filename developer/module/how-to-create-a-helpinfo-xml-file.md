---
title: Como criar um arquivo XML de HelpInfo | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3971ce1f-271c-4938-a9d3-47ff3aaf7219
caps.latest.revision: 9
ms.openlocfilehash: 7df9764fd573b75f285fec592448a550e481bea3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844899"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a>How to Create a HelpInfo XML File (Como Criar um Ficheiro XML HelpInfo)

Este tópico nesta secção explica como criar e preencher um arquivo de informações de ajuda, comumente conhecido como um "HelpInfo arquivo XML," para a funcionalidade de ajuda Atualizável do Windows PowerShell.

## <a name="helpinfo-xml-file-overview"></a>Visão geral de arquivos HelpInfo XML

O ficheiro XML de HelpInfo é a principal fonte de informações sobre Ajuda Atualizável para o módulo. Ele inclui a localização dos ficheiros de ajuda para os módulos, as culturas suportadas da interface do Usuário e os números de versão que ajuda Atualizável utiliza para determinar se o utilizador tem os ficheiros de ajuda mais recentes.

Cada módulo tem apenas um arquivo de XML de HelpInfo, mesmo que o módulo inclui vários arquivos de ajuda para várias culturas de interface do Usuário. O autor de módulos cria o arquivo XML de HelpInfo e o coloca na localização de Internet que é especificada pela **HelpInfoUri** chave no manifesto do módulo. Quando os arquivos de ajuda do módulo são atualizados e carregados, o autor do módulo atualiza o ficheiro XML de HelpInfo e substitui o ficheiro XML de HelpInfo original com a nova versão.

É fundamental que o ficheiro XML de HelpInfo cuidadosamente é mantido. Se carregar novos ficheiros, mas se esqueça de incrementar os números de versão, ajuda Atualizável não transferirá os novos ficheiros nos computadores dos usuários. Se adicionar arquivos de ajuda para uma nova cultura da interface do Usuário, mas não atualizar o ficheiro XML de HelpInfo ou coloque-o na localização correta, a ajuda Atualizável não irá transferir os ficheiros novos.

## <a name="in-this-section"></a>Nesta secção

Esta secção inclui os tópicos seguintes:

- [Esquema HelpInfo XML](./helpinfo-xml-schema.md)

- [Ficheiro de exemplo do XML de HelpInfo](./helpinfo-xml-sample-file.md)

- [Como atribuir um nome um arquivo XML de HelpInfo](./how-to-name-a-helpinfo-xml-file.md)

- [Como configurar números de versão HelpInfo XML](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a>Consulte Também

[Apoio ajuda Atualizável](./supporting-updatable-help.md)