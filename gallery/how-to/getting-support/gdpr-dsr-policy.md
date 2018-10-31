---
ms.date: 03/27/2018
contributor: JKeithB
keywords: Galeria, powershell, psgallery, com o GDPR
title: Conformidade do GDPR de galeria do PowerShell
ms.openlocfilehash: fb1191d8a1cd12d5994e41238c384eb504d0c261
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002655"
---
# <a name="powershell-gallery-gdpr-compliance"></a>Conformidade do GDPR de galeria do PowerShell

## <a name="overview"></a>Descrição geral

Em Maio de 2018, uma lei de privacidade na Europa, os dados de proteção Regulamento geral (GDPR), que demorou o efeito.
O GDPR impõe as regras de novo em empresas, organismos públicos, sem fins lucrativos e outras organizações que oferta bens e serviços a pessoas localizadas na União Europeia (UE), ou que recolhem e analisam os dados associados a residentes da UE.
O GDPR aplica-se, independentemente de onde estão localizados.

> [!NOTE]
> Este artigo fornece os passos para saber como eliminar os dados pessoais da galeria do PowerShell e pode ser utilizado para suportar as suas obrigações sob o GDPR. Se estiver procurando por informações gerais sobre o GDPR, consulte a [secção GDPR para o portal de confiança do serviço](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

## <a name="personally-identifiable-data"></a>Dados pessoalmente identificáveis

A galeria do PowerShell armazena as seguintes informações que possam ser fornecidas por utilizadores, que podem conter informações pessoais:

- Conta da galeria do PowerShell
- Pacotes publicados na galeria do PowerShell
- Correspondência de e-mail com a equipe de galeria do PowerShell

A maioria dos usuários não crie uma conta de galeria do PowerShell.
Não é necessária uma conta, a menos que pretende publicar um pacote ou utilizar a funcionalidade de "Contacte o proprietário" na galeria do PowerShell.
Diferente de correspondência de e-mail iniciada pelo utilizador, a galeria do PowerShell não armazena dados pessoalmente identificáveis para os utilizadores que não criou uma conta.

Os utilizadores que criam uma conta de galeria do PowerShell podem publicar pacotes da galeria do PowerShell.
Esses pacotes são esperados que seja o código do PowerShell, mas poderão conter outras informações incluindo informações pessoais.
As informações abaixo irão mostrar como pode obter todos os pacotes de ter publicado na galeria do PowerShell.

## <a name="dsr-export-of-powershell-gallery-data"></a>Exportação DSR de dados da galeria do PowerShell

As secções seguintes descrevem como a galeria do PowerShell suporta pedidos de dados (DSR), explicando como exportar informações armazenadas na galeria do PowerShell e como solicitar a eliminação dessas informações.

### <a name="email"></a>Correio Eletrónico

Correspondência de e-mail pode incluir qualquer um dos seguintes procedimentos:

- E-mail enviado para os proprietários de galeria do PowerShell pacotes se a análise de código analisa detetou um problema com qualquer pacote que tiverem publicado na galeria do PowerShell
- E-mail enviado por qualquer pessoa para o agrupamento de galeria do PowerShell com o endereço de e-mail na página "Fale Conosco" [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)
- Registado utilizadores que utilizam a funcionalidade de "Contacte o proprietário" na galeria do PowerShell para enviar um e-mail para o proprietário de um pacote na galeria do PowerShell

Mensagens de e-mail enviadas por ou para a galeria do PowerShell têm uma política de retenção de 90 dias para suportar as investigações de segurança possível de código malicioso deverão ser detetado na galeria do PowerShell.
Mensagens de correio eletrónico são eliminadas por política após 90 dias.

Pode solicitar cópias de todas as mensagens de e-mail enviadas ou recebidas por seu endereço de e-mail e a galeria do PowerShell dentro os últimos 90 dias.
Para pedir essa correspondência, envie um e-mail para [ cgadmin@microsoft.com ](mailto:cgadmin@microsoft.com), com o título: "Pedido DSR para e-mails relacionadas a esta conta".
No corpo da mensagem, que está a solicitar de informações de estado (por exemplo: Envie todas as mensagens de correio eletrónico enviadas ou recebidas a partir deste endereço de e-mail.) Todos os e-mails que envolvem o seu endereço de e-mail no prazo de 90 dias do pedido serão enviados dentro de 7 dias de negócios.

### <a name="powershell-gallery-account-information"></a>Informações de conta da galeria do PowerShell

Se tiver criado uma conta de galeria do PowerShell, pode encontrar todas as informações pessoais que tenham sido armazenadas na galeria do PowerShell, efetuando os seguintes passos:

1. Entrar para a galeria do PowerShell, em seguida, clique em seu nome de utilizador
2. A próxima página apresentada é a página de conta, que mostra o endereço de e-mail utilizado para a conta de galeria do PowerShell

Se tiver criado mais de uma conta na galeria do PowerShell, terá de repetir essas etapas para cada conta.

### <a name="packages-in-the-powershell-gallery"></a>Pacotes na galeria do PowerShell

Para facilitar a exportar pacotes publicados na galeria do PowerShell, publicamos o script "GetPSGalleryItemsForAuthor" para a galeria do PowerShell.
Este script exporta uma cópia de cada versão de cada pacote inserida na galeria do PowerShell com base nas informações de autor, armazenadas no pacote.

> [!NOTE]
> O autor é armazenado no manifesto do pacote quando publica o seu pacote.
> Não é garantido que o autor é a mesma identidade que a conta que utiliza na galeria do PowerShell.
> Se usar algum outro valor no campo de autor, terá de fornecer esse valor ao utilizar este script.

Pode transferir o script usando o seguinte comando do PowerShell:

```powershell
Save-Script Get-repository psgallery
```

Em seguida, pode executar o script diretamente, executando os seguintes comandos do PowerShell:

```powershell
# cd <local folder location>
.\GetPSGalleryItemsForAuthor.ps1
```

Será solicitado a fornecer o autor e uma pasta no seu sistema onde pretende que os pacotes a serem salvos.

## <a name="deleting-personal-data-from-the-powershell-gallery"></a>A eliminar os dados pessoais da galeria do PowerShell

Para eliminar a sua conta da galeria do PowerShell ou de qualquer pacote que é proprietário na galeria do PowerShell, envie um e-mail para cgadmin@microsoft.com com o título: "Pedido de GDPR para itens relacionados a esta conta".
No corpo da mensagem de estado as informações que pretende que foi eliminada. Por exemplo:

- Elimine x.y. z da versão de meu pacote do "nome do pacote"
- Elimine todas as versões do meu pacote do "nome do pacote"
- Elimine a minha conta da galeria do PowerShell

Os administradores de galeria do PowerShell irão responder dentro de 7 dias de negócios.
Os pacotes especificados serão eliminados dentro de 30 dias após a solicitação é enviada.
