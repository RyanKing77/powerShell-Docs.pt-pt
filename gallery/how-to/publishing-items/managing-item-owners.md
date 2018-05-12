---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: cmdlet do powershell do galeria, psgallery
title: Gerir os proprietários de itens
ms.openlocfilehash: 20380972ffe365ec9a479073fdf7e7f0eb1ee34e
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/10/2018
---
# <a name="managing-item-owners"></a>Gerir os proprietários de itens

Propriedade de um item na galeria do PowerShell é definida pela que publicado o item da galeria.
Por vezes, estes metadados tem de ser geridos fora a publicação de item inicial, o que significa que os metadados de proprietário tem de ser mutável enquanto o próprio item não é.

Todos os proprietários do item são elementos.
Isto significa que qualquer proprietário do item de pode publicar uma nova versão de um item. Também significa que qualquer proprietário do item pode remover quaisquer outro proprietário do item.
Não existe nenhum proprietário tem autoridade mais que outros proprietários.

## <a name="setting-an-items-initial-owner"></a>Definir o proprietário inicial de um Item

Quando um novo item é publicado na galeria do PowerShell, o proprietário inicial é definido pelo utilizador que publicou o item. É determinado pela cujo API chave foi utilizada o cmdlet do módulo de publicar.

## <a name="adding-owners"></a>A adição de proprietários

Depois de publicar um item a galeria do PowerShell, é fácil convidar utilizadores adicionais para se tornar os proprietários de um item.

1. [Inicie sessão no](https://powershellgallery.com/users/account/LogOn) a galeria do PowerShell com a conta que é o proprietário atual de um item.
2. Navegue para uma página do item utilizando o separador "Itens", procure-os ou clicando em seu nome de utilizador e, em seguida, [ **gerir os meus itens**](https://www.powershellgallery.com/account/Packages).
3. Quando tem sessão iniciada como proprietário de um item, há uma ligação 'Gerir proprietários' no lado esquerdo, clique em.
4. Introduza o nome de utilizador da pessoa a adicionar como um proprietário e clique em 'Add'.
5. Mensagens de correio eletrónico é enviada para o novo proprietário conjunta, como um convite para se tornar um proprietário de um item.
6. Uma vez que o utilizador clica na ligação, são um coproprietário completo, com controlo total sobre um item, incluindo a capacidade de remover a outros utilizadores como proprietários.

**Tenha em atenção**: até que o novo proprietário confirma a propriedade, estes *não* estar listado como um proprietário de um item.
Ao visualizar o **Gerir proprietários** página, verá uma entrada para "pendente aprovação" os proprietários atuais.
Que pode ser removido convite; tal como outros proprietários podem ser removidos.
Este processo de convites para impede que os utilizadores falsely adicionar outros utilizadores como proprietários dos respetivos itens.

Tenha em atenção que os metadados de "Autores" são o texto puramente livres superior; apenas os proprietários"" são controlados.


## <a name="removing-owners"></a>Remover os proprietários

Quando um item tem vários proprietários e um tem de ser removido, o processo é simple:

1. [Inicie sessão no](https://powershellgallery.com/users/account/LogOn) a galeria do PowerShell com a conta que é o proprietário atual de um item;
2. Navegue para uma página do item utilizando o separador de itens, procurar ou clicar em seu nome de utilizador e, em seguida, [ **gerir os meus itens**](https://www.powershellgallery.com/account/Packages).
3. Quando a sessão iniciada como proprietário de um item, há uma ligação 'Gerir proprietários' no lado esquerdo de clicar em;
4. Clique na ligação "Remover" junto ao proprietário a serem removidos.



## <a name="transferring-item-ownership"></a>Transferir a propriedade do Item

Por vezes, obtemos os pedidos de suporte para a transferência de item propriedade de um utilizador para outro, mas pode realizar quase sempre-la manualmente.
Transferir a propriedade de um utilizador para outra é simplesmente uma combinação de duas funcionalidades acima.

1. O proprietário atual invites o novo utilizador para se tornar um coproprietário e o utilizador novo aceitar o convite a;
2. O utilizador novo remove o utilizador antigo da lista de proprietários.

Este pedido ficar em alguns formulários, mas o processo funciona da mesma.

- A propriedade do item está a mudar de um programador para outro
- Publicar o item foi acidentalmente utilizando a conta de errado


## <a name="orphaned-items"></a>Itens órfãos

Ocorreu um último cenário, mas não demasiadas vezes.
Itens ficou órfãos e a única conta de proprietário do item não pode ser utilizada para adicionar os proprietários de novo.
Seguem-se alguns exemplos deste cenário:

- A conta do proprietário está associada um endereço de correio eletrónico que já não existe e o utilizador tenha esquecido a palavra-passe
- O proprietário registado tiver saído da empresa que produz o item e não é possível aceder ao atualizar a propriedade do item
- Resultam de erros que afetou apenas alguns dos itens, o item é examinar ownerless na Galeria

Os administradores de galeria do PowerShell podem aceder a ligação 'Gerir proprietários' para qualquer item.
Se for o proprietário de um item rightful e não é possível contactar o proprietário atual para obter permissões de propriedade, utilize a ligação 'Relatório abuso' na Galeria para contactar os administradores de galeria do PowerShell.
Em seguida, iremos segui um processo para verificar a sua propriedade do item.
Se determinar que deve ser um proprietário do item, iremos utilizar na ligação 'Gerir proprietários' para o item ourselves e enviar-lhe o convite para se tornar um proprietário.
Só será efetuado esta depois de verificar que deve ser um proprietário e o processo para este varia consoante o circunstâncias.
Muitas vezes, iremos utilizar o URL de projeto do item para encontrar uma forma de contactar o proprietário do projeto, mas podem também utilizamos Twitter, o E-Mail ou outros meios para contactar o proprietário do projeto.