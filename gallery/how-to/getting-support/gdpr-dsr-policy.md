---
ms.date: 03/27/2018
contributor: JKeithB
keywords: Galeria, powershell, psgallery, GDPR
title: Conformidade GDPR de galeria do PowerShell
ms.openlocfilehash: dca1a82952c284980a84caafa13b2807e47e25a0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189759"
---
# <a name="powershell-gallery-gdpr-compliance"></a>Conformidade GDPR de galeria do PowerShell

## <a name="overview"></a>Descrição geral

Na Maio de 2018, uma lei da privacidade Europa, o geral dados proteção Regulamento (GDPR), entra em vigor.
O GDPR impõe novas regras em empresas, agências governamentais, não lucros e outras organizações que oferta bens serviços e para as pessoas da União Europeia (EU) ou que recolher e analisam dados associados ao residentes de EU.
O GDPR aplica-se, independentemente de onde estão localizadas.

> [!NOTE]
> Este artigo fornece os passos sobre como eliminar os dados pessoais da galeria do PowerShell e pode ser utilizado para suportar as obrigações sob o GDPR. Se estiver à procura de informações gerais sobre GDPR, consulte o [secção GDPR do portal do serviço de confiança](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

## <a name="personally-identifiable-data"></a>Dados de identificação pessoal

A galeria do PowerShell armazena as seguintes informações que podem ser fornecidas por utilizadores, que podem conter informações pessoais:

* Conta de galeria do PowerShell
* Itens publicados para a galeria do PowerShell
* Correspondência de e-mail de e-mail com a equipa de galeria do PowerShell

A maioria dos utilizadores não criar uma conta de galeria do PowerShell.
Não é necessária uma conta, exceto se publicar um item ou utilizar a funcionalidade de "Proprietário contacte" na galeria do PowerShell.
Além de correspondência de e-mail de correio eletrónico iniciada pelo utilizador, Galeria do PowerShell não armazena dados pessoalmente identificáveis para os utilizadores que não criou uma conta.

Os utilizadores que criar uma conta de galeria do PowerShell podem publicar itens de galeria do PowerShell.
Esses itens deverão estar código do PowerShell, mas podem conter outras informações, incluindo informações pessoais.
As informações abaixo mostram como obter todos os itens tiver publicado a galeria do PowerShell.

## <a name="dsr-export-of-powershell-gallery-data"></a>Exportação DSR dos dados de galeria do PowerShell

As secções seguintes descrevem como galeria do PowerShell suporta pedidos de assunto de dados (DSR), por explicar como exportar informações armazenadas na galeria do PowerShell e como a eliminação destas informações do pedido.

### <a name="email"></a>Correio Eletrónico

Correspondência de e-mail de correio eletrónico pode incluir qualquer um dos seguintes procedimentos:

* E-mail enviado para os proprietários de galeria do PowerShell itens, se a análise de código analisa detetou um problema com qualquer item que tem publicado a galeria do PowerShell
* E-mail enviado por qualquer pessoa para a equipa de galeria do PowerShell utilizando o endereço de e-mail na página "Contacte-na" (cgadmin@microsoft.com)
* Registar utilizadores utilizam a funcionalidade de "Proprietário contacte" na galeria do PowerShell para enviar correio eletrónico para o proprietário de um item na galeria do PowerShell

Mensagens de correio eletrónico enviadas pelo ou a galeria do PowerShell tem uma política de retenção de 90 dias para suportar as investigações de segurança possível deverão ser detetado código malicioso na galeria do PowerShell.
Os e-mails são eliminados pela política após 90 dias.

Pode pedir cópias de todas as mensagens de correio eletrónico enviadas para ou a partir do seu endereço de e-mail e a galeria do PowerShell nos últimos 90 dias.
Para pedir esta correspondência de e-mail, envie um e-mail para cgadmin@microsoft.com, com o título: "DSR pedido para e-mails relacionadas com esta conta".
No corpo da mensagem de estado as informações que estão a pedir (por exemplo: Envie todas as mensagens de correio eletrónico enviado para ou recebeu este endereço de e-mail.) Todos os e-mails que envolvem o seu endereço de e-mail no prazo de 90 dias do pedido serão enviadas dentro de 7 dias úteis.

### <a name="powershell-gallery-account-information"></a>Informações de conta de galeria do PowerShell

Se tiver criado uma conta de galeria do PowerShell, pode encontrar todas as informações pessoais que tenham sido armazenadas na galeria do PowerShell, efetuando os seguintes passos:

1. Inicie sessão na galeria do PowerShell, em seguida, clique no nome de utilizador
2. A seguinte página apresentada é a página de conta, que mostra o endereço de e-mail utilizado para a conta de galeria do PowerShell

Se tiver criado mais do que uma conta na galeria do PowerShell, terá de repetir estes passos para cada conta.

### <a name="items-in-the-powershell-gallery"></a>Itens de galeria do PowerShell

Para facilitar a exportar itens publicados para a galeria do PowerShell, iremos tiver publicado o script "GetPSGalleryItemsForAuthor" para a galeria do PowerShell.
Este script exporta uma cópia de cada versão de todos os itens a colocar na galeria do PowerShell com base nas informações de autor armazenadas no item.

> [!NOTE]
> O autor é armazenado no manifesto item quando publicar o item.
> Não há nenhuma garantia de que o autor é a mesma identidade que a conta que utiliza na galeria do PowerShell.
> Se utilizar outro valor no campo autor, terá de fornecer esse valor quando utilizar este script.

Pode transferir o script utilizando o seguinte comando do PowerShell:

```powershell
Save-Script GetPSGalleryItemsForAuthor -path <local folder location> -repository psgallery
```

Em seguida, pode executar o script diretamente, executando os seguintes comandos do PowerShell:

```powershell
cd <local folder location >
.\GetPSGalleryItemsForAuthor.ps1
```

Será solicitado para fornecer o autor e uma pasta no seu sistema onde pretende que os itens sejam guardados.

## <a name="deleting-personal-data-from-the-powershell-gallery"></a>Eliminar dados pessoais da galeria do PowerShell

Para eliminar a conta de galeria do PowerShell ou de qualquer item proprietário na galeria do PowerShell, enviar correio eletrónico para cgadmin@microsoft.com com o título: "GDPR pedido para itens relacionados com esta conta".
No corpo da mensagem de estado as informações que pretende que foi eliminado. Por exemplo:

* Elimine x.y.z de versão do meu item "nome do item de"
* Elimine todas as versões do meu item "nome do item de"
* Elimine a minha conta de galeria do PowerShell

Os administradores de galeria do PowerShell irão responder dentro de 7 dias úteis.
Os itens especificados serão eliminados dentro de 30 dias após o pedido é enviado.
