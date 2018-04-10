---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: cmdlet do powershell do galeria, psgallery
title: psgalleryint_status
ms.openlocfilehash: 4f7d300bb07fcbdb100c2fb029f8f66ab260fe7a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
<a name="powershell-gallery-status"></a>Estado de galeria do PowerShell
=========================

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a>27/03/2017 - RESOLVIDO: não é possível ver páginas individuais, módulo e scripts

__Resumo de impacto__: direcionar ligações para páginas individuais, módulo e script no https://www.powershellgallery.com foram interrompidas. Isto foi reportado em todas as regiões. Isto não afetar qualquer um dos PowerShellGet cmdlets ie., instale-Module, Script de atualização, publicar-Module, de Script de instalação, atualização-Module, publicar-Script continuou a trabalhar.

__Causa raiz__: engenheiros de identificar a causa como um problema ao chamar botões como o Facebook para a página de redes sociais.

__Resolução__: engenheiros de corrigido o problema, desativando as informações de contagem do Facebook.

__Próximos passos__: foi aberto um problema de controlo interno para corrigir o nosso utilização da API do Facebook.

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a>15/12/2016 - não é possível enviar mensagens de correio eletrónico através do Web site de PowerShellGallery

__Resumo de impacto__: entre 13/12/2016 e 15/12/2016, as mensagens enviadas por proprietários de contacto, Gerir proprietários, contacte o suporte ou abuso do relatório não foram recebidas por administradores de galeria do PowerShell.
__Causa raiz__: engenheiros de identificar a causa como um problema de autenticação com o servidor de SMTP.
__Resolução__: engenheiros foram capazes de resolver o problema de autenticação e restaurar a ligação ao servidor SMTP.
__Próximos passos__: Se utilizou as ligações de proprietários de contacto, Gerir proprietários, contacte o suporte ou relatório abuso para enviar correio para cgadmin@microsoft.com durante este tempo e não tenham respondeu, volte a tentar. Pedimos desculpa pelo incómodo.


## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a>8/10/2016 - resolvido: não é possível enviar e-mails para cgadmin@microsoft.com
__Resumo de impacto__: entre 8/5/2016 e 8/10/2016, os clientes não conseguiram enviar e-mails para cgadmin@microsoft.com, ou utilizar a funcionalidade contacte-nos.
__Causa raiz__: engenheiros de identificar a causa como uma alteração da configuração da conta de e-mail.
__Resolução__: engenheiros trabalhado para resolver o problema de configuração.
__Próximos passos__: se utilizado na ligação contacte-nos ou enviar correio para cgadmin@microsoft.com durante este tempo e não tenham respondeu, volte a tentar. Agradecemos-lhe por sua paciência.