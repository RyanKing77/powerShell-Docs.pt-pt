---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, o powershell, o cmdlet, o psgallery
title: Gerir os proprietários de pacote
ms.openlocfilehash: 5cf26a7195ac446177cbb7f3a055e8e0a78569cc
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004215"
---
# <a name="managing-package-owners"></a>Gerir os proprietários de pacote

Propriedade de um pacote na galeria do PowerShell é definida pelo pacote que publicado na galeria.
Por vezes, estes metadados precisam ser gerenciada para além de publicação do pacote inicial, o que significa que os metadados de proprietário tem de ser mutáveis, enquanto o pacote propriamente dito não é.

Todos os proprietários de pacote são elementos.
Isso significa que qualquer proprietário do pacote pode publicar uma nova versão de um pacote. Isso também significa que qualquer proprietário do pacote pode remover qualquer proprietário do pacote.
Nenhum proprietário tem autoridade mais do que outros proprietários.

## <a name="setting-a-packages-initial-owner"></a>Definir o proprietário de um pacote inicial

Quando um novo pacote for publicado na galeria do PowerShell, o proprietário inicial é definido pelo utilizador que publicou o pacote. Tal é determinado pela cuja API chave foi utilizada no cmdlet Publish-Module.

## <a name="adding-owners"></a>Adicionar proprietários

Quando um pacote foi publicado na galeria do PowerShell, é fácil convidar utilizadores adicionais para se tornar os proprietários de um pacote.

1. [Inicie sessão no](https://powershellgallery.com/users/account/LogOn) na galeria do PowerShell com a conta que seja o proprietário atual de um pacote.
2. Navegar para uma página de pacote usando a guia "Itens", pesquisa ou ao clicar em seu nome de utilizador e, em seguida [ **Manage My Packages**](https://www.powershellgallery.com/account/Packages).
3. Quando a sessão iniciada como proprietário de um pacote, existe uma ligação de "Gerir proprietários" no lado esquerdo, clique em.
4. Introduza o nome de utilizador da pessoa a adicionar como proprietário e clique em "Adicionar".
5. Uma mensagem de e-mail, em seguida, é enviada para o novo proprietário conjunta, como um convite para se tornar um proprietário de um pacote.
6. Uma vez que o utilizador clica na ligação, são coproprietário completo com controlo total sobre um pacote, incluindo a capacidade de remover outros utilizadores como proprietários.

**Tenha em atenção**: até que o novo proprietário confirma a propriedade, eles *não* listado como proprietário de um pacote.
Ao visualizar o **gerir os proprietários** página, verá uma entrada pendente"aprovação" nos proprietários atuais.
Esse convite pode ser removida; assim como outros proprietários podem ser removidos.
Esse processo de convites impede os utilizadores de outros utilizadores a adicionar incorretamente como proprietários dos seus pacotes.

Tenha em atenção que os metadados de "Autores" são puramente de forma livre texto; apenas "proprietários" são controlados.


## <a name="removing-owners"></a>Remover proprietários

Quando um pacote tem vários proprietários e um tem de ser removido, o processo é simple:

1. [Inicie sessão no](https://powershellgallery.com/users/account/LogOn) galeria do PowerShell com a conta que seja o proprietário atual de um pacote;
2. Navegar para uma página de pacote usando a guia de pacotes, pesquisa ou ao clicar em seu nome de utilizador e, em seguida [ **Manage My Packages**](https://www.powershellgallery.com/account/Packages).
3. Quando a sessão iniciada como proprietário de um pacote, existe uma ligação de "Gerir proprietários" no lado esquerdo clique;
4. Clique na ligação "Remover" junto ao proprietário a ser removido.



## <a name="transferring-package-ownership"></a>Transferir a propriedade de pacote

Por vezes, recebemos pedidos de suporte para transferir a propriedade de pacote de um usuário para outro, mas quase sempre é possível fazê-la manualmente.
Transferir a propriedade de um usuário para outro é simplesmente uma combinação de dois recursos acima.

1. O proprietário atual convida o novo utilizador para se tornar um coproprietário e o novo utilizador aceita o convite;
2. O novo utilizador remove o utilizador antigo da lista de proprietários.

Este pedido aparecer em dois formulários, mas o processo funciona da mesma.

- A propriedade de pacote está mudando de um desenvolvedor para outro
- O pacote foi acidentalmente publicado a utilização da conta errada


## <a name="orphaned-packages"></a>Pacotes órfãos

Um último cenário ocorreu, mas não várias vezes.
Pacotes se tornaram órfãos e a única conta de proprietário do pacote não pode ser utilizada para adicionar novos proprietários.
Aqui estão alguns exemplos deste cenário:

- A conta do proprietário está associada um endereço de e-mail que já não existe e o utilizador esqueceu a palavra-passe
- O proprietário registado saiu da empresa que produz o pacote e não é possível aceder ao atualizar a propriedade de pacote
- Devido a um erro que afetou apenas um punhado de pacotes, o pacote é de alguma maneira ownerless na Galeria

Os administradores de galeria do PowerShell pode acessar o link "Gerenciar proprietários" para qualquer pacote.
Se for o proprietário legítimo de um pacote e não é possível contactar o proprietário atual para obter permissões de propriedade, utilize a ligação de "Relatar Abuso" na Galeria para alcançar os administradores de galeria do PowerShell.
Podemos, em seguida, seguirá um processo para verificar a sua propriedade do pacote.
Se determinarmos que deve ser um proprietário do pacote, iremos utilizar a ligação de "Gerir proprietários" para o pacote, nós mesmos e enviar-lhe o convite para se tornar um proprietário.
Podemos fará isso apenas depois de verificar que deve ser um proprietário e o processo varia por circunstâncias.
Muitas vezes, utilizaremos o URL do projeto do pacote para encontrar uma forma de contactar o proprietário do projeto, mas podemos também utilizar, Twitter, E-Mail ou outro meio para contactar o proprietário do projeto.
