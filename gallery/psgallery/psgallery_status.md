---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: cmdlet do powershell do galeria, psgallery
title: psgallery_status
ms.openlocfilehash: 08d09ce83b5133598152186e12fc8ced90c36a88
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
<a name="powershell-gallery-status"></a>Estado de galeria do PowerShell
=========================
## <a name="10102017---powershell-gallery-unavailable-for-2-hours-101017"></a>10/10/2017 - galeria do PowerShell disponível para 2 horas 10/10/17

__Resumo de impacto__: A Galeria do PowerShell teve um período de latência muito elevado, resultando em problemas de ligação intermitente, a partir, aproximadamente, as 17: 00 (PDT) 10/10/17. Ao resolver o problema, o site foi colocado offline para 2 horas iniciar aproximadamente as 22: 00 (PDT). O site foi restaurado pouco tempo antes de à meia-noite 10/10/2017.

__Causa raiz__: A causa raiz a latência elevada ainda está a ser investigada.

__Resolução__: os serviços web que tiveram de ser colocado offline e restaurado para resolver o problema principal.

__Próximos passos__: A causa de raiz para o problema original que está a ser investigada.

## <a name="06012017---deploy-to-azure-automation-currently-unavailable"></a>01/06/2017 - implementar para a automatização do Azure não está disponível

__Resumo de impacto__: implementar itens com as dependências de automatização do Azure da galeria do PowerShell está atualmente indisponível.  Importar itens da galeria do PowerShell de dentro da automatização do Azure ainda está disponível.

__Causa raiz__: itens que terem dependências de outros utilizadores e de ter sido implementadas anteriormente a automatização do Azure, não serão possível implementar a automatização do Azure. Engenheiros de tem identificado um problema com a forma como modelos ARM são gerados para itens com dependências para implementar a funcionalidade de automatização do Azure.

__Resolução__: engenheiros estiver a trabalhar para resolver o problema.  A solução atual para os utilizadores é para importar o item da galeria do PowerShell a partir de dentro da automatização do Azure.

__Próximos passos__: engenheiros de libertar a correção em breve.  Entretanto, utilize a solução recomendada.


## <a name="04112017---users-unable-to-log-in-with-azure-active-directory-aad-accounts"></a>04/11/2017 - os utilizadores não é possível iniciar sessão com contas do Azure Active Directory (AAD)

__Resumo de impacto__: alguns utilizadores não conseguiram iniciar sessão na galeria do PowerShell com contas do Azure AD.

__Causa raiz__: durante uma atualização para interagir com mais segurança no AAD, uma alteração da definição foi perdida.
O teste concluído para validar a alteração não incluiu determinados tipos de contas do AAD, pelo que a implementação proceeded.

__Resolução__: engenheiros identificou a definição em falta e corrigiu o problema.

__Próximos passos__: podemos irá modificar nosso teste para incluir um conjunto alargado de tipos de contas do AAD.

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a>27/03/2017 - RESOLVIDO: não é possível ver páginas individuais, módulo e scripts

__Resumo de impacto__: direcionar ligações para páginas individuais, módulo e script no https://www.powershellgallery.com foram interrompidas. Isto foi reportado em todas as regiões. Isto não afetar qualquer um dos PowerShellGet cmdlets ie., módulo de instalação, o Script de atualização, publicar-Module, de Script de instalação, atualização-Module, publicar-Scirpt continuou a trabalhar.

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



## <a name="7132016---download-items-failed"></a>13/7/2016 - transferir itens falhou

__Resumo de impacto__: entre 11/7/2016 e 13/7/2016, um subconjunto de clientes teve a problemas de transferência de itens da galeria do PowerShell. O problema provável apresentado próprio a seguinte mensagem de erro devolvido de instalação-módulo/Install-Script e guardar-módulo/Save-Script:

```powershell
PS C:\> Install-Module xStorage
PackageManagement\Install-Package : Package 'xStorage' failed to be installed because:
End of Central Directory record could not be found. At C:\Program
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1375 char:21 + ...
$null = PackageManagement\Install-Package @PSBoundParameters +
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + CategoryInfo : InvalidResult:
(xStorage:String) [Install-Package], Exception + FullyQualifiedErrorId : Package '{0}'
failed to be installed because: {1},Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage
```

__Causa raiz preliminar__: engenheiros identificado um problema com o Azure fornecer rede conteúdos (CDN), que foi implementada para a galeria do PowerShell em 11/7/2016.
__Mitigação__: engenheiros desativada CDN do Azure na galeria do PowerShell.
__Próximos passos__: investigue a causa raiz subjacente e a desenvolver uma solução para impedir futuras ocorrências.


## <a name="5192016---download-items-failed"></a>19/5/2016 - transferir itens falhou
__Resumo de impacto__: entre 17/5/2016 e 19/5/2016, um subconjunto de clientes teve a problemas de transferência de itens da galeria do PowerShell. O problema provável apresentado próprio a seguinte mensagem de erro devolvido de instalação-módulo/Install-Script e guardar-módulo/Save-Script:

```powershell
VERBOSE: Hash for package 'AzureRM.OperationalInsights' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='AzureRM.OperationalInsights', version='1.0.8',
destination='C:\Users\jbritt\AppData\Local\Temp\2\1741355729'
WARNING: Package 'AzureRM.OperationalInsights' failed to be installed because:
End of Central Directory record could not be found.
WARNING: Dependent Package 'AzureRM.OperationalInsights' failed to install.
WARNING: Package 'AzureRM' failed to install.
VERBOSE: Module 'AzureRM.Network' was saved successfully.
VERBOSE: Saving the dependency module 'AzureRM.NotificationHubs' with version '1.0.8' for the
module 'AzureRM'.
VERBOSE: Module 'AzureRM.NotificationHubs' was saved successfully.
PackageManagement\Save-Package : Unable to save the module 'AzureRM'. At C:\Program
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1187 char:21 +
$null = PackageManagement\Save-Package @PSBoundParameters +
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ +
CategoryInfo : InvalidOperation: (Microsoft.Power...ets.SavePackage:SavePackage)
[Save-Package], Exception + FullyQualifiedErrorId : ProviderFailToDownloadFile,
Microsoft.PowerShell.PackageManagement.Cmdlets.SavePackage
```

__Causa raiz preliminar__: engenheiros identificada uma falha no fornecedor subjacente do Azure fornecer rede conteúdos (CDN), que foi implementada para a galeria do PowerShell em 17/5/2016.
__Mitigação__: engenheiros desativada CDN do Azure na galeria do PowerShell.
__Próximos passos__: investigue a causa raiz subjacente e a desenvolver uma solução para impedir futuras ocorrências.