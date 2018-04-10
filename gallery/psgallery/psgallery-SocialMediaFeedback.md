---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: cmdlet do powershell do galeria, psgallery
title: Fornecer Comentários através das Redes Sociais ou dos Comentários
ms.openlocfilehash: 9e2a5a246b1caa37ad7b03e20c8f543b9e5cf530
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="providing-feedback-via-social-media-or-comments"></a>Fornecer Comentários através das Redes Sociais ou dos Comentários

A galeria do Powershell suporta duas abordagens para os utilizadores enviar comentários público no item:

* Utilize as ligações na margem esquerda "partilhar" um item em sites de redes sociais Facebook, LinkedIn ou Twitter;
* Utilize a funcionalidade de comentário para publicar comentários no item e para permitir autores a observar comentários sobre itens publicam.

## <a name="social-media-feedback"></a>Comentários de redes sociais
No lado esquerdo da página para cada item na galeria do PowerShell existem ligações para o Facebook, Twitter e LinkedIn.
Clicar nestas ligações abrir o site de redes sociais e permitir rapidamente partilha uma ligação para o item.

Os utilizadores tem de iniciar sessão para o site que escolheu para partilhar o item da galeria do PowerShell.

Os utilizadores são encouraged para efetuar este procedimento se encontrarem um item é algo que recomendamos para outras pessoas.
A galeria do PowerShell irá verificar cada local de redes sociais "partilhas" do item e apresentar como número de vezes que item foi partilhado em cada um dos sites de redes sociais.
Uma vez que esta ação mostra apenas o número de vezes que algo foi partilhado, será intepreted outros utilizadores como "liking" o item.


## <a name="comments"></a>Comentários
Galeria do PowerShell utiliza o serviço de LiveFyre para permitir que os utilizadores comentar itens.
Os utilizadores que têm as recomendações ou comentários podem utilizar esta funcionalidade para fornecer comentários que estejam visíveis para qualquer pessoa que aceder a página de item.
Os proprietários do item podem seguir estes comentários e ser notificados quando alguém mensagens um comentário.

O sistema de comentário baseia LiveFyre, que é um serviço separado que não é gerido pela Microsoft e necessita de início de sessão único para utilizar.
Na primeira vez que optar por deixar um comentário ou siga comentários dos seus itens, será solicitado para criar uma conta de LiveFyre.

Se criou uma conta de LiveFyre e tem sessão iniciada, pode craft um comentário que disponibiliza comentários sobre o item, em seguida, clique em "Comment Post..." O comentário não serão visível imediatamente.
Comentários para itens de galeria são moderated por administradores da galeria do PowerShell e todas as mensagens são revistas pelos moderators antes de ser publicados e estão visíveis para outros utilizadores.
Nosso objetivo no moderating os comentários é certificar-se de que estes estão alinhados com público comportamento consistente com a galeria do PowerShell [os termos de utilização](https://www.powershellgallery.com/policies/Terms).

Os proprietários do item são encorajados a seguir os comentários são publicados no LiveFyre.
É necessária uma conta de LiveFyre e recomenda-se para utilizar o mesmo endereço de e-mail que utiliza para publicar o item no LiveFyre.
Para seguir os comentários, inicie sessão no LiveFyre e navegue para qualquer item onde estão apresentados como um proprietário.
Abaixo a caixa de comentário na parte inferior de cada item, irá ver "+ siga".
Assim que clicar nisto, LiveFyre irá enviar um e-mail para o endereço de e-mail registado quaisquer comentários de nova hora efetuados no item.