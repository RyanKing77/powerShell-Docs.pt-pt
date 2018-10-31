---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, o powershell, o cmdlet, o psgallery
title: Fornecer Feedback através de redes sociais ou dos comentários
ms.openlocfilehash: a7cdcc2ff2c18fb606d077adf0bdecf57c90703f
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004136"
---
# <a name="providing-feedback-via-social-media-or-comments"></a>Fornecer Feedback através de redes sociais ou dos comentários

A galeria do Powershell oferece suporte a duas abordagens para que os utilizadores forneçam comentários público num pacote:

- Utilize as ligações no limite esquerdo de um pacote em sites de redes sociais do Facebook, LinkedIn e Twitter; "compartilhar"
- Utilize a funcionalidade de comentário para publicar comentários de um pacote e para permitir que os autores para deteção de comentários nos pacotes publicam.

## <a name="social-media-feedback"></a>Comentários de mídia social

No lado esquerdo da página para cada pacote na galeria do PowerShell existem ligações para o Facebook, LinkedIn e Twitter.
Clique nesses links abrir o site de mídia social e permitir a partilha rapidamente de uma ligação para o pacote.

Os utilizadores devem iniciar sessão para o site que escolheu para compartilhar o pacote de galeria do PowerShell.

Os utilizadores são encorajados a fazer isso, se eles encontrarem um pacote é algo que recomendaria para outras pessoas.
A galeria do PowerShell irá verificar a cada site de redes sociais para "partilhas" do pacote e apresentar o número de vezes que o pacote tiver sido partilhado em cada um dos sites de redes sociais.
Uma vez que isso apresenta apenas o número de vezes que algo foi partilhado, será intepreted outros utilizadores como "liking" o pacote.


## <a name="comments"></a>Comentários

A galeria do PowerShell utiliza o serviço de LiveFyre para permitir que os utilizadores comentar pacotes.
Os utilizadores que tem as recomendações ou comentários podem utilizar esta funcionalidade para fornecer comentários que sejam visíveis para qualquer pessoa que visitar a página de pacote.
Os proprietários de pacote podem seguir estes comentários e ser notificados quando alguém publica um comentário.

O sistema de comentário baseia-se no livefyre, uma vez que é um serviço separado que não é gerido pela Microsoft e necessita de início de sessão exclusivo para utilizar.
Na primeira vez que optar por deixar um comentário ou siga comentários em um dos seus pacotes, será solicitado para criar uma conta LiveFyre.

Se tiver criado uma conta LiveFyre e iniciar sessão, pode criar um comentário que disponibiliza comentários sobre o pacote, em seguida, clique em "Publicar comentário..." O comentário não será visível imediatamente.
Comentários para pacotes de galeria são moderados pelos administradores de galeria do PowerShell e todas as mensagens são revisadas pelos moderadores antes de ser publicados e visíveis para outras pessoas.
Nosso objetivo no moderating os comentários é garantir que eles se alinham com o comportamento do público consistente com a galeria do PowerShell [termos de utilização](https://www.powershellgallery.com/policies/Terms).

Os proprietários do pacote são incentivados a seguir comentários que serão lançados LiveFyre.
É necessária uma conta LiveFyre e é recomendado que utilize o mesmo endereço de e-mail que utiliza para publicar o pacote no LiveFyre.
Para seguir comentários, inicie sessão no LiveFyre e navegue para qualquer pacote em que está listado como proprietário.
Abaixo da caixa comentário na parte inferior de cada pacote que irá ver "+ siga".
Depois de clicar nisso, LiveFyre enviará um e-mail para o endereço de e-mail registrado, quaisquer comentários novos de tempo feitos no pacote.
