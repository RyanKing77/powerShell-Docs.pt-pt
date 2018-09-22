---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: Valores de manifestos de item que têm impacto sobre a interface do Usuário de galeria do PowerShell
ms.openlocfilehash: e7e9910504a665e464add0a83454cec64c1a0937
ms.sourcegitcommit: 601609575a3214ea7086a3bcb586ae0d1df3d418
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/21/2018
ms.locfileid: "46532975"
---
# <a name="item-manifest-values-that-impact-the-powershell-gallery-ui"></a>Valores de manifestos de item que têm impacto sobre a interface do Usuário de galeria do PowerShell

Este tópico fornece os publicadores com informações de resumo sobre como modificar o manifesto para suas publicações de galeria do PowerShell para que as funcionalidades de cmdlets do PowerShellGet e a interface do Usuário de galeria do PowerShell serão afetadas. Este conteúdo está organizado por onde a alteração será exibida, partida com a secção de center, em seguida, a área de navegação à esquerda. Existe uma secção de detalhes de etiquetas de abrangente, que identifica importante etiquetas, bem como alguns dos mais comumente usadas etiquetas. Existem dois tópicos que fornecem exemplos manifestos:

- Para módulos, consulte [manifesto de módulo de atualização](/powershell/module/powershellget/Update-ModuleManifest)
- Para scripts, consulte [criar ficheiro de Script com metadados](/powershell/module/powershellget/New-ScriptFileInfo)

## <a name="powershell-gallery-feature-elements-controlled-by-the-manifest"></a>Elementos de recurso de galeria do PowerShell controlados pelo manifesto

A tabela abaixo mostra os elementos da página de item de galeria do PowerShell da interface do Usuário que são controlados pelo editor. Cada item indica se ele pode ser controlado pelo manifesto do módulo ou script.

| Elemento de interface do Usuário | Descrição | Módulo | Script |
| --- | --- | --- | --- |
| **Título** | Este é o nome do item que é publicado na Galeria  | Não | Não |
| **Versão** | A versão apresentada é a cadeia de versão dos metadados e um pré-lançamento se for especificado. A parte principal da versão num manifesto de módulo é o ModuleVersion. Para obter um script, é identificado como. VERSÃO. Se for especificada uma cadeia de versão de pré-lançamento, ele será acrescentado ao ModuleVersion para módulos, ou especificado como parte da. VERSÃO de scripts. Há documentação para especificar cadeias de caracteres de pré-lançamento no [módulos](module-prerelease-support.md)e, em [scripts](script-prerelease-support.md) | Sim | Sim |
| **Descrição** | Esta é a descrição no manifesto do módulo e, num manifesto do arquivo de script é. DESCRIÇÃO | Sim | Sim |
| **Exigir a aceitação da licença** | Um módulo pode exigir que o utilizador aceitar uma licença, ao modificar o manifesto de módulo com RequireLicenseAcceptance = $true, fornecendo um LicenseURI e fornecer um ficheiro de license.txt na raiz da pasta do módulo. Estão disponíveis informações adicionais no [exigem a aceitação da licença](../how-to/working-with-items/items-that-require-license-acceptance.md) tópico. | Sim | Não |
| **Notas de versão** | Para módulos, estas informações são retiradas da secção de ReleaseNotes, sob PSData\PrivateData. Nos manifestos de script, é o. Elemento RELEASENOTES. | Sim | Sim |
| **Proprietários** | Os proprietários são a lista de utilizadores na galeria do PowerShell que pode atualizar um item. A lista de proprietários não está incluída no manifesto de item. Documentação adicional descreve como [gerir os proprietários de itens](../how-to/publishing-items/managing-item-owners.md). | Não | Não |
| **Autor** | Isso está incluído no manifesto do módulo como autor e, num manifesto de script como. AUTOR. O campo de autor, muitas vezes, é utilizado para especificar uma empresa ou organização associada um item. | Sim | Sim |
| **Direitos de autor** | Este é o campo de direitos de autor no manifesto do módulo, e. COPYRIGHT num manifesto de script. | Sim | Sim |
| **FileList** | A lista de ficheiros é desenhada do pacote quando é publicado na galeria do PowerShell. Não é controlável pelas informações de manifesto. Nota: existe um ficheiro de .nuspec adicionais listado com cada item da galeria do PowerShell que não está presente depois de instalar o item num sistema. Isso é o manifesto de pacote Nuget para o item e pode ser ignorado. | Não | Não |
| **Etiquetas** | Para módulos, as etiquetas estão incluídas no PSData\PrivateData. Para scripts, a seção é assinaladas como. AS ETIQUETAS. Tenha em atenção que as etiquetas não pode conter espaços, mesmo quando estão aspas. Etiquetas têm requisitos adicionais e os significados, que são descritos posteriormente neste tópico na seção Detalhes da etiqueta. | Sim | Sim |
| **Cmdlets** | Isto é fornecido no manifesto do módulo CmdletsToExport a utilizar. Tenha em atenção que a melhor prática é explicitamente os itens de lista, em vez de utilizar o caráter universal "*", uma vez que irá melhorar o desempenho de carga-module para os utilizadores. | Sim | Não |
| **Funções** | Isto é fornecido no manifesto do módulo FunctionsToExport a utilizar. Tenha em atenção que a melhor prática é explicitamente os itens de lista, em vez de utilizar o caráter universal "*", uma vez que irá melhorar o desempenho de carga-module para os utilizadores. | Sim | Não |
| **Recursos de DSC** | Para os módulos que serão utilizados no PowerShell versão 5.0 e posteriores, isto é fornecido no manifesto usando DscResourcesToExport. Se o módulo está a ser utilizado no PowerShell 4, o DSCResourcesToExport não deve ser utilizada porque não é uma chave de manifesto suportada. (O DSC não estava disponível antes de PowerShell 4). | Sim | Não |
| **Fluxos de Trabalho** | Fluxos de trabalho são publicados na galeria do PowerShell, como scripts e identificados como fluxos de trabalho (consulte [Connect-AzureVM](https://www.powershellgallery.com/packages/Connect-AzureVM/1.0/Content/Connect-AzureVM.ps1) para obter um exemplo) no código. Não é controlada pelo manifesto. | Não | Não |
| **Funcionalidades de função** | Isto irá ser apresentado quando o módulo publicado na galeria do PowerShell contém um ou mais arquivos de recurso (.psrc) de função, que são utilizados pelo JEA. Veja a documentação de JEA para obter mais detalhes sobre [funcionalidades de função](/powershell/jea/role-capabilities). | Sim | Não |
| **Edições do PowerShell** | Isto é especificado num manifesto de módulo ou script. Para os módulos devem ser utilizadas com o PowerShell 5.0 e abaixo, isso são controlados utilizando etiquetas. Para o Desktop, usar a marca PSEdition_Desktop e para o núcleo, usar a marca PSEdition_Core. Para os módulos que serão utilizados apenas no PowerShell 5.1 e versões posteriores, existe uma chave de CompatiblePSEditions no manifesto do principal. Para obter detalhes adicionais, reveja a funcionalidade de edição de PS no [a documentação do PowerShell Get](module-psedition-support.md). | Sim | Sim |
| **Dependências** | As dependências são os módulos na galeria do PowerShell que são declarados no módulo como RequiredModules ou no manifesto do script como #Requires – módulo (nome). | Sim | Sim |
| **Versão mínima do Powershell** | Isto pode ser especificado num manifesto de módulo como PowerShellVersion | Sim | Não |
| **Histórico de versões** | O histórico de versões reflete as atualizações feitas a um módulo na galeria do PowerShell. Se uma versão de um item está oculta a utilizar a funcionalidade de eliminação, ele não será apresentado no histórico de versões, exceto para os proprietários do item. | Não | Não |
| **Site do projeto** | O site do projeto é fornecido para módulos na seção Privatedata\PSData do manifesto do módulo especificando um ProjectURI. No manifesto do script, ele é controlado através da especificação. PROJECTURI. | Sim | Sim |
| **Licença** | É fornecida uma ligação de licença para os módulos na seção Privatedata\PSData do manifesto do módulo especificando um LicenseURI. No manifesto do script, ele é controlado através da especificação. LICENSEURI. É importante observar que, se uma licença não é fornecida através do LicenseURI ou dentro de um módulo, em seguida, os termos de utilização para a galeria do PowerShell especifique os termos de utilização para o item. Consulte os termos de utilização para obter detalhes. | Sim | Sim |
| **Ícone** | Um ícone pode ser especificado para qualquer item da galeria do PowerShell, fornecendo o sinalizador de definição de IconURI no manifesto do script ou na seção Privatedata PSData do manifesto do módulo. A definição de IconURI deve apontar para uma imagem de 32 x 32 com plano de fundo de transparência. O URI **tem** ser um URL de imagem direta e **não podem** aceda a uma página da web que contém a imagem ou um ficheiro do pacote de galeria do PowerShell. | Sim | Sim |


## <a name="editing-item-details"></a>Editar detalhes do item

A página de item editar de galeria do PowerShell permite aos editores alterar vários dos campos apresentados para um item, especificamente:

- Título
- Descrição
- Resumo
- URL de ícone
- URL da home page de projeto
- Autores
- Copyright
- Etiquetas
- Notas de versão
- Necessita de licença

Essa abordagem não é normalmente recomendada, exceto quando for necessário para corrigir o que é apresentado para uma versão mais antiga de um módulo. Os utilizadores que adquirir o módulo irão ver que os metadados não coincide com o que é apresentado na galeria do PowerShell, o que gera preocupações sobre o item. Com freqüência isso resultará em consultas que vão para os proprietários de item para confirmar a alteração. É vivamente recomendado que sempre que esta abordagem é utilizada, uma nova versão do item deve ser publicada com as mesmas alterações.

## <a name="tag-details"></a>Detalhes da etiqueta

As etiquetas são a utilização de consumidores de cadeias de caracteres simples para localizar itens. As etiquetas são mais importantes quando são utilizadas consistentemente em muitos itens relacionados com o mesmo tópico. Word (por exemplo da base de dados e bases de dados, ou teste e teste), normalmente, com diversas versões do mesmo fornece poucas vantagens. As etiquetas são cadeias de caracteres de maiúsculas e minúsculas de palavra única e não podem incluir espaços em branco. Se houver uma frase que acreditar que irão procurar utilizadores, adicioná-la para a descrição do item e ele será encontrado nos resultados da pesquisa. Utilize Pascal casing, hífen, caráter de sublinhado ou período, se estiver a tentar melhorar a legibilidade.
Tenha cuidado ao criar etiquetas de longo, complexas e incomuns, como eles são, muitas vezes, um erro ortográfico.

Existem etiquetas que são importantes para tenha em atenção, como a galeria do PowerShell e o PowerShellGet cmdlets tratá-los com exclusividade. PSEdition_Desktop PSEdition_Core são os exemplos específicos e são descritos acima.

Conforme indicado acima, etiquetas fornecem o máximo valor quando eles estão específico e é utilizado consistentemente em vários itens. Como um publicador tentar localizar as melhores marcas usar, a abordagem mais fácil é procurar na galeria do PowerShell para etiquetas que estiver a considerar. O ideal é que haverá muitos itens retornados e as descrições de item serão alinhado com a utilização dessa palavra-chave.

Para referência, eis algumas marcas mais comumente usadas a partir de 12/14/2017. Em alguns casos, há semelhante, mas talvez menos opções ideais listadas ao lado da marca. É a melhor prática para utilizar a marca preferencial, como, que irá resultar em menos ruído e os resultados da pesquisa melhor para os consumidores.

| Etiqueta preferencial | Alternativas e notas |
| --- | --- |
| Azure |  |
| DSC | DesiredStateConfiguration é menos desejável, é demasiado longo |
| ResourceManager | É usado para descrever o grupo de processadores ARM e não deve ser utilizada para o Azure Resource Manager |
| DSCResourceKit |  |
| SQL |  |
| AWS |  |
| DSCResource |  |
| Automatização |  |
| REST |  |
| ActiveDirectory | AD não é atualmente utilizado por si só  |
| SQLServer |  |
| DBA |  |
| Segurança | Defesa é menos precisa |
| Base de Dados | Bases de dados (plural) é menos desejável |
| DevOps |  |
| Windows |  |
| Compilação |  |
| Implementação | Implementar é utilizado um pouco menos frequência |
| Na cloud |  |
| GIT |  |
| Teste | O teste é menos desejável |
| VersionControl | Versão é menos preciso, embora usado com mais frequência  |
| Registo | Uso preferencial de Registro em log como uma ação |
| Registo | Uso preferencial de Log como uma coisa |
| Telefone Alternativo |  |
| IaaS |  |
| Linux |  |
| IIS |  |
| AzureAutomation |  |
| Armazenamento |  |
| GitHub |  |
| JSON |  |
| Exchange |  |
| Rede | Funcionamento em rede é semelhante, com menos frequência utilizada |
| SharePoint |  |
| Relatórios | Geração de relatórios é uma ação, o relatório é uma coisa |
| Relatório | Relatório é uma coisa |
| WinRM |  |
| Monitorização |  |
| VSTS |  |
| Excel |  |
| Google |  |
| Cor |  |
| DNS |  |
| Office 365 | O Office de ortografia é preferível. Office 365 é menos usados, embora mais curto |
| Gitlab |  |
| Pester |  |
| AzureAD |  |
| HTML |  |
| Hyper-V | Hyper-v é menos comum como uma etiqueta |
| Configuração |  |
| ChatOps |  |
| PackageManagement |  |
| WMI |  |
| Firewall |  |
| Docker |  |
| Appveyor |  |
| AzureRm | Utilizado principalmente para os módulos AzureRM |
| Zip |  |
| MSI |  |
| Mac |  |
| PoshBot |  |