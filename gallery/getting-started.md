---
ms.date: 06/12/2017
contributor: JKeithB
keywords: cmdlet do powershell do galeria, psgallery
title: Introdução à galeria do PowerShell
ms.openlocfilehash: 83974698152e75efac66ea725a9c220486676d6f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190167"
---
# <a name="get-started-with-the-powershell-gallery"></a>Introdução à galeria do PowerShell

Transferência de itens da galeria do PowerShell para o sistema necessita de [PowerShellGet](/powershell/module/powershellget) módulo. Pode encontrar o módulo de PowerShellGet em qualquer um dos seguintes procedimentos. Não é necessário iniciar sessão transferir os itens da galeria do PowerShell.

## <a name="discovering-items-from-the-powershell-gallery"></a>Deteção de itens da galeria do PowerShell

Pode encontrar itens na galeria do PowerShell, utilizando o **pesquisa** controlo neste Web site ou pela navegação nas páginas de módulos e Scripts. Também pode encontrar itens da galeria do PowerShell, executando o [encontrar o módulo][] e [localizar Script][] cmdlets, consoante o tipo de item com `-Repository PSGallery`.

Filtrar os resultados da galeria do pode ser feito utilizando os seguintes parâmetros:

- Nome
- AllVersions
- MinimumVersion
- RequiredVersion
- Sinalizador
- Inclui
- DscResource
- RoleCapability
- Comando
- filtro

Se apenas estiver interessado em detetar recursos de DSC específicos na galeria, pode executar o [localizar DscResource] cmdlet. Localizar DscResource devolve dados contidos na Galeria de recursos de DSC.
Porque os recursos de DSC são sempre fornecidos como parte de um módulo, é preciso executar [Instalar módulo][] para instalar esses recursos de DSC.

## <a name="learning-about-items-in-the-powershell-gallery"></a>Saber mais sobre itens de galeria do PowerShell

Depois de ter identificado um item que está interessado em, poderá querer saber mais acerca do mesmo. Pode fazê-lo, examinando página específica desse item na galeria. Nessa página, poderá ver todos os metadados carregados com do item. Estes metadados de um item é fornecido pelo autor do item e não é verificado pela Microsoft. O proprietário do item vivamente está associado à conta de galeria utilizada para publicar o item e é mais fidedigno que o campo autor.

Se detetar um item que sentir não está publicado em boa fé, clique em **relatório abuso** na página esse item.

Se estiver a executar [encontrar o módulo][] ou [localizar Script][], pode ver estes dados no objeto PSGetModuleInfo devolvido. Por exemplo, executar `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member` devolve dados no módulo PSReadLine na galeria.

## <a name="downloading-items-from-the-powershell-gallery"></a>Transferência de itens da galeria do PowerShell

Aconselhamo-o seguinte processo quando a transferência de itens da galeria do PowerShell:

### <a name="inspect"></a>Inspecione

Para transferir um item da Galeria para inspecção, execute o [guardar-Module][] ou [Guardar Script][] cmdlet, consoante o tipo de item. Isto permite-lhe guardar o item localmente sem instalá-lo e inspecionar os conteúdos do item. Lembre-se ao eliminar o item guardado manualmente.

Alguns destes itens são criados pela Microsoft e outros são criados pela Comunidade do PowerShell.
A Microsoft recomenda que reveja o conteúdo e o código de itens nesta galeria antes da instalação.

Se detetar um item que sentir não está publicado em boa fé, clique em **relatório abuso** na página esse item.

### <a name="install"></a>Instalar

Para instalar um item da Galeria para utilização, execute o [Instalar módulo][] ou [Script de instalação][] cmdlet, consoante o tipo de item.

[Instalar módulo][] instala o módulo para `$env:ProgramFiles\WindowsPowerShell\Modules` por predefinição.
Isto requer uma conta de administrador. Se adicionar o `-Scope CurrentUser` parâmetro, o módulo está instalado para `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .

[Script de instalação][] instala o script para `$env:ProgramFiles\WindowsPowerShell\Scripts` por predefinição.
Isto requer uma conta de administrador. Se adicionar o `-Scope CurrentUser` parâmetro, o script está instalado o `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .

Por predefinição, [Instalar módulo][] e [Script de instalação][] instala a versão mais recente de um item.
Para instalar uma versão mais antiga do item, adicione o `-RequiredVersion` parâmetro.

### <a name="deploy"></a>Implementar

Para implementar um item da galeria do PowerShell a automatização do Azure, clique em **implementar a automatização do Azure** na página de detalhes do item. Será redirecionado para o Portal de gestão do Azure, onde poderá iniciar sessão com as suas credenciais de conta do Azure. Tenha em atenção que implementar itens com dependências irá implementar todas as dependências da automatização do Azure. O botão 'Implementar a automatização do Azure' pode ser desativado através da adição de **AzureAutomationNotSupported** etiquetas para os seus metadados do item.

Para saber mais sobre a automatização do Azure, consulte o [da automatização do Azure](/azure/automation) documentação.

## <a name="updating-items-from-the-powershell-gallery"></a>Atualizar itens da galeria do PowerShell

Para atualizar itens instalados a partir da galeria do PowerShell, execute [atualização-Module] [-] ou [Script de atualização] [] cmdlet. Quando executar sem quaisquer parâmetros adicionais, [atualização-Module] [-] tenta atualizar cada módulo instalado, executando [Instalar módulo][]. Para atualizar seletivamente módulos, adicione o `-Name` parâmetro.

Da mesma forma, quando executada sem quaisquer parâmetros adicionais, [Script de atualização] [-] também tentar atualizar cada script instalada através da execução [Script de instalação][]. Para atualizar seletivamente scripts, adicione o `-Name` parâmetro.

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a>Itens de lista que tenha instalado da galeria do PowerShell

Para saber quais os módulos que instalou da galeria do PowerShell, execute o [Get-InstalledModule][] cmdlet. Este comando lista todos os módulos tem no seu sistema, que foram instalados diretamente a partir da galeria do PowerShell.

Da mesma forma, para saber quais os scripts que instalou da galeria do PowerShell, execute o [Get-InstalledScript][] cmdlet. Este comando lista todos os scripts que tem no seu sistema, que foram instalados diretamente a partir da galeria do PowerShell.

[localizar DscResource]: /powershell/module/powershellget/Find-DscResource
[encontrar o módulo]: /powershell/module/powershellget/Find-Module
[localizar Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Instalar módulo]: /powershell/module/powershellget/Install-Module
[Script de instalação]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[guardar-Module]: /powershell/module/powershellget/Save-Module
[Guardar Script]: /powershell/module/powershellget/Save-Script