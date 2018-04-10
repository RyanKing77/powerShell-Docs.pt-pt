---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: cmdlet do powershell do galeria, psgallery
title: psgallery_gettingstarted
ms.openlocfilehash: 599b148e141ba4205a7c774581e737a5d54bfae1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="get-started-with-the-powershell-gallery"></a>Introdução à galeria do PowerShell

## <a name="what-is-the-powershell-gallery"></a>O que é a galeria do PowerShell?

A galeria do PowerShell consiste no repositório central para o conteúdo do PowerShell.
Aqui, pode encontrar útil módulos do PowerShell que contém os comandos do PowerShell e recursos de configuração de estado pretendido (DSC). Também pode encontrar scripts do PowerShell, algumas das quais podem conter fluxos de trabalho do PowerShell e que descrevem um conjunto de tarefas e fornecer a sequenciação para essas tarefas.
Alguns destes itens são criados pela Microsoft e outros são criados pela Comunidade do PowerShell.

## <a name="requirements"></a>Requisitos

Transferência de itens da galeria do PowerShell para o sistema necessita de [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) módulo. Pode encontrar o módulo de PowerShellGet em qualquer um dos seguintes procedimentos. Não é necessário iniciar sessão transferir os itens da galeria do PowerShell.

-   [Windows 10](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)
-   [Windows Management Framework 5.0](http://go.microsoft.com/fwlink/?LinkId=398175)
-   [Instalador do MSI (para o PowerShell 3 e 4)](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

PowerShellGet também requer o [NuGet fornecedor](http://go.microsoft.com/fwlink/?LinkId=722208) para trabalhar com a galeria do PowerShell. Será solicitado para instalar o fornecedor de NuGet automaticamente após a primeira utilização da PowerShellGet se o fornecedor do NuGet não é uma das seguintes localizações:

- `$env:ProgramFiles\PackageManagement\ProviderAssemblies`
- `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies`

Em alternativa, pode executar `Install-PackageProvider -Name NuGet -Force` para automatizar a transferência e instalação do fornecedor do NuGet.


Se tiver uma versão mais antiga do que 2.8.5.201 do NuGet, terá de chamar os seguintes cmdlets do PowerShell para instalar e mudar para a versão mais recente do NuGet.

1.  `Install-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force`
2.  `Import-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force`
3.  Elimine a versão mais antiga do NuGet da localização instalada acima.

Para obter mais informações, consulte <http://oneget.org/> .


Nota: Devido a alterações em formatos de empacotamento, recomendamos que Atualize para a versão mais recente do PowerShellGet e PackageManagement para instalar os itens que tenham sido atualizados recentemente. PowerShellGet está incluído no Windows 10, pode saber mais sobre [aqui](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409).
PowerShellGet também faz parte do Windows Management Framework (WMF) 5.0, que pode transferir [aqui](http://go.microsoft.com/fwlink/?LinkId=398175).

## <a name="discovering-items-from-the-powershell-gallery"></a>Deteção de itens da galeria do PowerShell

Pode encontrar itens na galeria do PowerShell, utilizando o **pesquisa** controlo neste Web site ou pela navegação nas páginas de módulos e Scripts. Também pode encontrar itens da galeria do PowerShell, executando o [encontrar o módulo](https://go.microsoft.com/fwlink/?LinkId=821658) e [localizar Script](https://go.microsoft.com/fwlink/?LinkId=822322) cmdlets, consoante o tipo de item com `-Repository PSGallery`.

Filtrar os resultados da galeria do pode ser feito utilizando os seguintes parâmetros de [encontrar o módulo](https://go.microsoft.com/fwlink/?LinkId=821658) e [localizar Script](https://go.microsoft.com/fwlink/?LinkId=822322)

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

Se apenas estiver interessado em detetar recursos de DSC específicos na galeria, pode executar o [localizar DscResource](https://go.microsoft.com/fwlink/?LinkId=517196) cmdlet.
[Localizar DscResource](https://go.microsoft.com/fwlink/?LinkId=517196) devolve dados contidos na Galeria de recursos de DSC. Porque os recursos de DSC são sempre fornecidos como parte de um módulo, é preciso executar [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) para instalar esses recursos de DSC.

## <a name="learning-about-items-in-the-powershell-gallery"></a>Saber mais sobre itens de galeria do PowerShell

Depois de ter identificado um item que está interessado em, poderá querer saber mais acerca do mesmo. Pode fazê-lo, examinando página específica desse item na galeria. Nessa página, poderá ver todos os metadados carregados com do item. Estes metadados de um item é fornecido pelo autor do item e não é verificado pela Microsoft. O proprietário do item vivamente está associado à conta de galeria utilizada para publicar o item e é mais fidedigno que o campo autor.

Se detetar um item que sentir não está publicado em boa fé, clique em **relatório abuso** na página esse item.

Se estiver a executar [encontrar o módulo](https://go.microsoft.com/fwlink/?LinkId=821658) ou [localizar Script](https://go.microsoft.com/fwlink/?LinkId=822322), pode ver estes dados no objeto PSGetModuleInfo devolvido.
Por exemplo, executar `Find-Module -Name PSReadLine -Repository PSGallery | Get-Member` devolve dados no módulo PSReadLine na galeria.

## <a name="downloading-items-from-the-powershell-gallery"></a>Transferência de itens da galeria do PowerShell

Aconselhamo-o seguinte processo quando a transferência de itens da galeria do PowerShell:

### <a name="inspect"></a>Inspecione

Para transferir um item da Galeria para inspecção, execute o [guardar-Module](https://go.microsoft.com/fwlink/?LinkId=821669) ou [Guardar Script](https://go.microsoft.com/fwlink/?LinkId=822334) cmdlet, consoante o tipo de item. Isto permite-lhe guardar o item localmente sem instalá-lo e inspecionar os conteúdos do item. Lembre-se ao eliminar o item guardado manualmente.

Alguns destes itens são criados pela Microsoft e outros são criados pela Comunidade do PowerShell. A Microsoft recomenda que reveja o conteúdo e o código de itens nesta galeria antes da instalação.

Se detetar um item que sentir não está publicado em boa fé, clique em **relatório abuso** na página esse item.

### <a name="install"></a>Instalar

Para instalar um item da Galeria para utilização, execute o [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) ou [Script de instalação](https://go.microsoft.com/fwlink/?LinkId=822327) cmdlet, consoante o tipo de item.

[Instalar módulo](https://go.microsoft.com/fwlink/?LinkId=821663) instala o módulo para `$env:ProgramFiles\WindowsPowerShell\Modules` por predefinição. Isto requer uma conta de administrador. Se adicionar o `-Scope
CurrentUser` parâmetro, o módulo está instalado para `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .

[Script de instalação](https://go.microsoft.com/fwlink/?LinkId=822327) instala o script para `$env:ProgramFiles\WindowsPowerShell\Scripts` por predefinição. Isto requer uma conta de administrador. Se adicionar o `-Scope
CurrentUser` parâmetro, o script está instalado o `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .

Por predefinição, [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) e [Script de instalação](https://go.microsoft.com/fwlink/?LinkId=822327) instala a versão mais recente de um item. Para instalar uma versão mais antiga do item, adicione o `-RequiredVersion` parâmetro.

### <a name="deploy"></a>Implementar

Para implementar um item da galeria do PowerShell a automatização do Azure, clique em **implementar a automatização do Azure** na página de detalhes do item. Será redirecionado para o Portal de gestão do Azure, onde poderá iniciar sessão com as suas credenciais de conta do Azure. Tenha em atenção que implementar itens com dependências irá implementar todas as dependências da automatização do Azure. O botão 'Implementar a automatização do Azure' pode ser desativado através da adição de **AzureAutomationNotSupported** etiquetas para os seus metadados do item.

Para saber mais sobre a automatização do Azure, consulte o [Web site da automatização do Azure](http://azure.microsoft.com/services/automation/).

## <a name="updating-items-from-the-powershell-gallery"></a>Atualizar itens da galeria do PowerShell

Para atualizar itens instalados a partir da galeria do PowerShell, execute o [Update-Module](https://go.microsoft.com/fwlink/?LinkID=398576) ou [Script de atualização](http://go.microsoft.com/fwlink/?LinkId=619787) cmdlet. Quando executar sem quaisquer parâmetros adicionais, [Update-Module](https://go.microsoft.com/fwlink/?LinkID=398576) tentar atualizar cada módulo instalado, executando [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663).
Para atualizar seletivamente módulos, adicione o `-Name` parâmetro.

Da mesma forma, quando executada sem quaisquer parâmetros adicionais, [Script de atualização](http://go.microsoft.com/fwlink/?LinkId=619787) também tentar atualizar cada script instalada através da execução [Script de instalação](https://go.microsoft.com/fwlink/?LinkId=822327).
Para atualizar seletivamente scripts, adicione o `-Name` parâmetro.

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a>Itens de lista que tenha instalado da galeria do PowerShell

Para saber quais os módulos que instalou da galeria do PowerShell, execute o [Get-InstalledModule](https://go.microsoft.com/fwlink/?LinkId=526863) cmdlet. Este comando lista todos os módulos tem no seu sistema, que foram instalados diretamente a partir da galeria do PowerShell.

Da mesma forma, para saber quais os scripts que instalou da galeria do PowerShell, execute o [Get-InstalledScript](https://go.microsoft.com/fwlink/?LinkId=619790) cmdlet. Este comando lista todos os scripts que tem no seu sistema, que foram instalados diretamente a partir da galeria do PowerShell.