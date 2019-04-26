---
ms.date: 09/10/2018
contributor: JKeithB
keywords: Galeria, o powershell, o cmdlet, o psgallery
title: Gerir chaves de API
ms.openlocfilehash: 954eb27c25babdb8efe50c13caf5f2d287c6b3e3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084367"
---
# <a name="managing-api-keys"></a>Gerir chaves de API

A galeria do PowerShell suportam a criação de várias chaves de API para suportar uma gama de requisitos de publicação. Uma chave de API pode aplicar a um ou mais pacotes, concede privilégios específicos e tem uma data de expiração.

> [!IMPORTANT]
> Os utilizadores que publicado na galeria do PowerShell antes da introdução das chaves de API âmbito terão uma "chave de API de acesso total". As chaves de acesso total não têm os aperfeiçoamentos de segurança incorporados no âmbito chaves de API. As chaves de acesso total para nunca expirar e aplicar a tudo o que propriedade do utilizador. Se eliminar esta chave, não pode ser recriada.

A imagem seguinte mostra as opções disponíveis durante a criação de uma chave de API de âmbito.

![Criação de chaves de API](../../Images/PSGallery_KeyScoped.png)

Neste exemplo, criámos uma chave de API com o nome **AzureRMDataFactory**. Este valor de chave pode ser utilizado para enviar pacotes com nomes que começam com "AzureRM.DataFactory" e é válido durante 365 dias. Este é um cenário típico quando equipas diferentes dentro da mesma organização trabalham em diferentes pacotes. Os membros da Equipe tem uma chave que lhe concede privilégios para o pacote específico funcionam no.
O valor de expiração impede a utilização de chaves esquecidas ou obsoletas.

## <a name="using-glob-patterns"></a>Usando padrões de blob

Se trabalha em vários pacotes, pode utilizar padrões de globbing para corresponder a vários pacotes como um grupo. Permissões da chave de API que se aplicam a todos os novos pacotes de correspondência entre o padrão de blob. Por exemplo, o exemplo anterior utiliza um **padrão de blob** valor de 'AzureRM.DataFactory*'. Pode enviar um pacote designado "AzureRm.DataFactoryV2.Netcore' usando esta chave, uma vez que o pacote corresponde ao padrão blob.

## <a name="create-api-keys-securely"></a>Criar chaves de API de forma segura

Para segurança, um valor de chave recentemente criado nunca é mostrado no ecrã e só está disponível com o botão de copiar, conforme mostrado abaixo.

![Obter novo valor de chave de API](../../Images/PSGallery_CopyCreatedKey.png)

> [!IMPORTANT]
> Só pode copiar o valor da chave de API imediatamente depois de criar ou atualizá-lo. Ele não será apresentado e não estará acessível novamente depois da página é atualizada. Se perder o valor da chave, tem de utilizar a voltar a gerar e copie a chave depois é regenerado.

## <a name="key-permissions-and-expiration"></a>Permissões da chave e de expiração

Âmbito de chaves de API podem atribuir qualquer uma das seguintes permissões:

- Novos pacotes de push
- Push novo ou pacotes de atualização
- Unlist pacotes

Cada nova chave tem uma expiração. O valor de expiração é medido em dias. Os valores possíveis de expiração são:

- 1 dia
- 90 dias
- 180 dias
- 270 dias
- 365 dias (predefinição)

Estas definições não podem ser alteradas depois da chave é criada. Não é possível criar uma nova chave que nunca expira.

## <a name="editing-and-deleting-existing-api-keys"></a>Editar e excluir as chaves de API existentes

Pode alterar algumas definições de uma chave existente. Como mencionado anteriormente, não é possível modificar o âmbito de segurança para uma chave de API existente ou alterar a expiração. As opções alteráveis são mostradas na captura de ecrã seguinte:

![Obter novo valor de chave de API](../../Images/PSGallery_EditAPIKey.png)

Para alterar os pacotes controlados por uma chave, pode selecionar pacotes individuais na lista ou alterar o padrão de blob.

Clicar **regenerar** cria um novo valor de chave. Tal como quando o criou inicialmente a chave, deve **cópia** o valor da chave imediatamente após a atualizá-los. O **cópia** opção não está disponível depois de sair desta página.

Clicar **eliminar** exibe uma mensagem de confirmação. Depois de uma chave é eliminada, ficará inutilizável.

## <a name="key-expiration"></a>Expiração da chave

Dez dias antes da expiração, a galeria do PowerShell envia um e-mail de aviso o titular da conta da chave de API. Após a expiração, a chave não é utilizável. É apresentada uma mensagem de aviso na parte superior da página de gestão de chaves de API que mostra as chaves já não são válidas. Pode gerar um novo valor de chave.
