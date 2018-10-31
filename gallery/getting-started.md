---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, o powershell, o cmdlet, o psgallery
title: Comece com a galeria do PowerShell
ms.openlocfilehash: 85b0a754aba25d850dc918024419318554f92b33
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225680"
---
# <a name="getting-started-with-the-powershell-gallery"></a>Guia de introdução da galeria do PowerShell

O modo adequado para instalar pacotes a partir da galeria do PowerShell é usar os cmdlets do [PowerShellGet](/powershell/module/powershellget) módulo. Não é necessário iniciar sessão para transferir os itens da galeria do PowerShell.

> [!NOTE]
> É possível transferir um pacote a partir da galeria do PowerShell diretamente, mas não se trata de uma abordagem recomendada.
> Para obter mais detalhes, consulte [transferir o pacote Manual](/powershell/gallery/how-to/working-with-packages/manual-download).

## <a name="discovering-packages-from-the-powershell-gallery"></a>Descoberta de pacotes a partir da galeria do PowerShell

Pode encontrar pacotes na galeria do PowerShell com o **pesquisa** controle neste site, ou ao navegar por meio das páginas de Scripts e módulos. Também pode encontrar pacotes a partir da galeria do PowerShell ao executar o [Find-Module][] e [Find-Script][] cmdlets, dependendo do tipo de item, com `-Repository PSGallery`.

Filtragem de resultados a partir da galeria pode ser feito utilizando os seguintes parâmetros:

- Nome
- AllVersions
- MinimumVersion
- RequiredVersion
- Sinalizador
- Inclui
- DscResource
- RoleCapability
- Comando
- Filtro

Se só estiver interessado em detetar recursos de DSC específicos na galeria, pode executar o [Find-DscResource] cmdlet. Find-DscResource devolve dados nos recursos de DSC contidos na galeria.
Como recursos de DSC sempre são fornecidos como parte de um módulo, ainda precisa executar [Install-Module][] para instalar esses recursos de DSC.

## <a name="learning-about-packages-in-the-powershell-gallery"></a>Saber mais sobre pacotes na galeria do PowerShell

Depois de identificar um pacote que está interessado, pode querer saber mais sobre ele. Pode fazê-lo, examinando a página específica desse pacote na galeria. Nessa página, poderá ver todos os metadados carregados com o pacote. Estes metadados é fornecido pelo autor do pacote e não é verificado pela Microsoft. O proprietário do pacote está intimamente ligado à conta utilizada para publicar o pacote de galeria e é mais confiável do que o campo de autor.

Se detetar um pacote que se sentir não está publicado em boa fé, clique em **relatar abuso** na página de tal pacote.

Se estiver a executar [Find-Module][] ou [Find-Script][], pode ver estes dados no objeto PSGetModuleInfo retornado. Por exemplo, executar `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`
Devolve os dados no módulo PSReadLine na galeria.

## <a name="downloading-packages-from-the-powershell-gallery"></a>Transferir pacotes a partir da galeria do PowerShell

Recomendamos o seguinte processo ao transferir pacotes a partir da galeria do PowerShell:

### <a name="inspect"></a>Inspecionar

Para transferir um pacote a partir da Galeria para inspeção, execute o [Save-Module][] ou [Save-Script][] cmdlet, dependendo do tipo de pacote. Isto permite-lhe guardar o pacote localmente sem instalá-lo e inspecionar o conteúdo do pacote. Não se esqueça de eliminar manualmente o pacote guardado.

Alguns desses pacotes são criados pela Microsoft e outros são criados pela Comunidade do PowerShell.
A Microsoft recomenda que reveja o conteúdo e o código de pacotes nesta galeria antes da instalação.

Se detetar um pacote que se sentir não está publicado em boa fé, clique em **relatar abuso** na página de tal pacote.

### <a name="install"></a>Instalar

Para instalar um pacote a partir da Galeria para uso, execute o [Install-Module][] ou [Script de instalação][] cmdlet, dependendo do tipo de pacote.

[Install-Module][] instala o módulo para `$env:ProgramFiles\WindowsPowerShell\Modules` por predefinição.
Isto requer uma conta de administrador. Se adicionar o `-Scope CurrentUser` parâmetro, o módulo é instalado `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .

[Script de instalação][] instala o script para `$env:ProgramFiles\WindowsPowerShell\Scripts` por predefinição.
Isto requer uma conta de administrador. Se adicionar o `-Scope CurrentUser` parâmetro, o script está instalado para `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .

Por predefinição, [Install-Module][] e [Script de instalação][] instala a versão mais atual de um pacote.
Para instalar uma versão mais antiga do pacote, adicione o `-RequiredVersion` parâmetro.

### <a name="deploy"></a>Implementar

Para implementar um pacote a partir da galeria do PowerShell para a automatização do Azure, clique em **implementar a automatização do Azure** na página de detalhes do pacote. Será redirecionado para o Portal de gestão do Azure em que inicie sessão com as credenciais da conta do Azure. Tenha em atenção que a implantação de pacotes com dependências será a implementar todas as dependências para automatização do Azure. O botão "Implementar a automatização do Azure" pode ser desativado ao adicionar o **AzureAutomationNotSupported** etiqueta para os metadados do pacote.

Para saber mais sobre a automatização do Azure, veja a [automatização do Azure](/azure/automation) documentação.

## <a name="updating-packages-from-the-powershell-gallery"></a>Atualizar pacotes da galeria do PowerShell

Para atualizar os pacotes instalados a partir da galeria do PowerShell, execute o [Update-Module] [-] ou [Script de atualização] [] cmdlet. Quando executado sem quaisquer parâmetros adicionais, [Update-Module] [-] tenta atualizar cada módulo instalado, executando [Install-Module][]. Para atualizar seletivamente módulos, adicione o `-Name` parâmetro.

Da mesma forma, quando executado sem quaisquer parâmetros adicionais, [Script de atualização] [-] também tenta atualizar cada script instalado, executando [Script de instalação][]. Para atualizar os scripts seletivamente, adicione o `-Name` parâmetro.

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a>Listar os pacotes que tiver instalado a partir da galeria do PowerShell

Para saber quais os módulos tiver instalado a partir da galeria do PowerShell, execute o [Get-InstalledModule][] cmdlet. Este comando lista todos os módulos que tem no seu sistema que foram instalados diretamente a partir da galeria do PowerShell.

Da mesma forma, para saber quais os scripts tiver instalado a partir da galeria do PowerShell, execute o [Get-InstalledScript][] cmdlet. Este comando lista todos os scripts que tem no seu sistema que foram instalados diretamente a partir da galeria do PowerShell.

[Find-DscResource]: /powershell/module/powershellget/Find-DscResource
[Find-Module]: /powershell/module/powershellget/Find-Module
[Find-Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Install-Module]: /powershell/module/powershellget/Install-Module
[Script de instalação]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[Save-Module]: /powershell/module/powershellget/Save-Module
[Save-Script]: /powershell/module/powershellget/Save-Script
