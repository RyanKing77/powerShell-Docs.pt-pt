---
ms.date: 06/12/2017
contributor: JKeithB
keywords: cmdlet do powershell do galeria, psgallery
title: Perguntas mais frequentes de galeria do PowerShell
ms.openlocfilehash: e377e71cf5eeb1f8b73430cc0b97527eac970cff
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="frequently-asked-questions"></a>Perguntas Mais Frequentes

## <a name="what-is-a-powershell-module"></a>O que é um módulo do PowerShell?

Um módulo do PowerShell é um pacote de reutilizável com algumas funcionalidades do PowerShell. Tudo no PowerShell (funções, variáveis, recursos de DSC, etc.) pode ser compactado nos módulos. Normalmente, os módulos são pastas que contêm tipos específicos de ficheiros armazenados num caminho específico. Existem alguns diferentes tipos de módulos do PowerShell horizontalmente.

## <a name="what-is-a-powershell-script"></a>O que é um script do PowerShell?

Um script do PowerShell é uma série de comandos que são armazenadas num ficheiro. ps1 para ativar a partilha e reutilização. Fluxos de trabalho do PowerShell também são scripts do PowerShell, que descrevem um conjunto de tarefas e fornecem a sequenciação para essas tarefas. Para obter mais informações, visite [introdução ao fluxo de trabalho do PowerShell](https://technet.microsoft.com/library/jj134242.aspx).

## <a name="how-are-powershell-scripts-different-from-powershell-modules"></a>Como Scripts do PowerShell são diferentes dos módulos do PowerShell?

Módulos são, geralmente, é melhores para a partilha, mas iremos ativar script partilha tornar mais fácil para que possa contribuir scripts e fluxos de trabalho para a Comunidade. Para obter mais informações, consulte os seguintes blogues:

- [Não escrever Scripts de módulos do PowerShell de escrita](https://blogs.technet.microsoft.com/heyscriptingguy/2011/06/27/dont-write-scripts-write-powershell-modules/)
- [Compreender os módulos do PowerShell](https://blogs.technet.microsoft.com/heyscriptingguy/2015/07/10/understanding-powershell-modules/)

## <a name="how-can-i-publish-to-the-powershell-gallery"></a>Como publicar para a galeria do PowerShell

Tem de registar uma conta na galeria do PowerShell antes de poder publicar itens para a galeria. Isto acontece porque a publicação de itens requer um NuGetApiKey, que é fornecido no registo. Para registar, utilize o seu trabalho pessoal, conta escolar ou profissional para iniciar sessão galeria do PowerShell. É necessário um processo de registo única quando iniciarem sessão pela primeira vez. Em seguida, o NuGetApiKey não está disponível na página do seu perfil.

Assim que registou na galeria, utilize o [publicar-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) ou [publicar Script](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlets para publicar o item da galeria. Para obter mais detalhes sobre como executar estes cmdlets, visite o separador de publicar, ou ler o [publicar-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) e [publicar Script](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) documentação.

**Não é necessário registar ou iniciar sessão na Galeria para instalar ou guardar itens.**

## <a name="i-received-failed-to-process-request-the-specified-api-key-is-invalid-or-does-not-have-permission-to-access-the-specified-package-the-remote-server-returned-an-error-403-forbidden-error-when-i-tried-to-publish-an-item-to-the-powershell-gallery-what-does-that-mean"></a>Foi recebido "Falha ao processar o pedido. 'A chave de API especificada é inválida ou não tem permissão para aceder ao pacote especificado.'. O servidor remoto devolveu um erro: proibido (403). " erro quando estava a publicar um item de galeria do PowerShell. O que significa?

Este erro pode ocorrer pelos seguintes motivos:

- **A chave de API especificada é inválida.**
     Certifique-se de que especificou a chave de API válida da sua conta. Para obter a chave de API, ver a página do seu perfil.
- **O nome do item especificado não é possuído por si.**
     Se tiver confirmado que a chave de API está correta, em seguida, pode já existir um item com o mesmo nome que está a tentar utilizar. O item pode ter sido não listado pelo proprietário, nesse caso não irão aparecer em qualquer os resultados da pesquisa. Para determinar se já existe um item com o mesmo nome, abra um browser e navegue até à página de detalhes do item: `https://www.powershellgallery.com/packages/<itemName>`. Por exemplo, ao navegar diretamente para `https://www.powershellgallery.com/packages/pester` leva-o para a página de detalhes do módulo Pester, quer seja não listado ou não. Se um item com um nome em conflito já existe e não listado, pode:
    - Selecione outro nome para o item.
    - Contacte os proprietários do item existente.

## <a name="why-cant-i-sign-in-with-my-personal-account-but-i-could-sign-in-yesterday"></a>Razão pela qual não é possível iniciar sessão com a minha conta pessoal, mas como posso foi possível iniciar sessão ontem?

. Lembre-se de que a conta de Galeria não acomodar as alterações ao seu alias de correio eletrónico principal. Para obter mais informações, consulte [Aliases de E-Mail do Microsoft](https://windows.microsoft.com/windows/outlook/add-alias-account).

## <a name="why-dont-i-see-all-the-gallery-items-when-i-select-all-the-category-checkboxes-on-the-items-tab"></a>Por que motivo não vejo todos os itens de galeria quando todas as caixas de categoria no separador itens selecionados?

Ao selecionar a caixa de verificação de categoria, são a indicar "Gostaria de ver todos os itens nesta categoria." Apenas os itens nas categorias selecionadas serão apresentados. Por isso, da mesma forma, ao selecionar todas as caixas de verificação de categoria, a é a indicar "Gostaria de ver todos os itens de qualquer categoria." Mas alguns itens na Galeria não pertencer a nenhuma das categorias listadas, pelo que não serão apresentados nos resultados. Para ver todos os itens de galeria, desmarque todas as categorias ou selecione o separador itens novamente.

## <a name="what-are-the-requirements-to-publish-a-module-to-the-powershell-gallery"></a>Quais são os requisitos para publicar um módulo para a galeria do PowerShell?

Qualquer tipo de módulo do PowerShell (módulos de script, módulos binários ou módulos de manifesto) pode ser publicado para a galeria. Para publicar um módulo, PowerShellGet precisa de saber alguns aspetos sobre o assunto - a versão, a descrição, autor e como é licenciado. Esta informação é lido como parte do processo de publicação do *manifesto de módulo* ficheiro (. psd1), ou do valor de [ **publicar-Module** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet **LicenseUri** parâmetro. Todos os módulos publicados na Galeria tem de ter manifestos de módulo. Qualquer módulo que inclui as seguintes informações no respetivo manifesto pode ser publicado para a galeria:

- Versão
- Descrição
- autor
- Um URI para os termos de licenciamento do módulo, como parte do **PrivateData** secção do manifesto ou no **LicenseUri** parâmetro do [ **publicar-Module** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

## <a name="how-do-i-create-a-correctly-formatted-module-manifest"></a>Como crio um manifesto de módulo formatado corretamente?

A forma mais fácil de criar um manifesto de módulo está a ser executado o [ **New-ModuleManifest** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet. No PowerShell 5.0 ou mais recente, New-ModuleManifest gera um manifesto de módulo corretamente formatado com campos em branco para metadados útil como **ProjectUri**, **LicenseUri**, e **etiquetas**. Basta preencher os espaços em branco ou utilize o manifesto gerado como um exemplo de formatação correto.

Para verificar se todas as necessárias campos de metadados tem sido preenchidos corretamente, utilize o [ **teste ModuleManifest** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

Para atualizar os campos de ficheiro de manifesto de módulo, utilize o [ **atualização ModuleManifest** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

## <a name="what-are-the-requirements-to-publish-a-script-to-the-gallery"></a>Quais são os requisitos para publicar um script para a Galeria?

Qualquer tipo de script do PowerShell (scripts ou fluxos de trabalho) pode ser publicado para a galeria. Para publicar um script, PowerShellGet precisa de saber alguns aspetos sobre o assunto - a versão, a descrição, autor e como é licenciado. Esta informação é lido como parte do processo de publicação do ficheiro de script *PSScriptInfo* secção, ou do valor de [ **publicar Script** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet  **LicenseUri** parâmetro. Todos os scripts publicados para a Galeria tem de ter as informações de metadados. Qualquer script que inclui as seguintes informações na respetiva secção de PSScriptInfo pode ser publicado para a galeria:

- Versão
- Descrição
- autor
- Um URI para os termos de licenciamento do script, como parte do **PSScriptInfo** secção do script, ou no **LicenseUri** parâmetro do [ **publicar-Script** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

## <a name="how-do-i-search"></a>Como procurar

Escreva aquilo procura na caixa de texto. Por exemplo, se pretender localizar módulos que estão relacionados com o SQL do Azure, basta escrevê "sql do azure". A nossa motor de busca irá procurar esses palavras-chave em todos os itens publicados, incluindo títulos, descrições e através de metadados. Em seguida, com base numa pontuação de qualidade ponderado, apresentará correspondências mais próximos. Poderá também pesquisar por campo específico utilizando o campo: "valor" sintaxe da consulta de pesquisa para os seguintes campos:

- Etiquetas
- Funções
- Cmdlets
- DscResources
- PowerShellVersion

Sim, por exemplo, quando procurar PowerShellVersion: "2.0" apenas os resultados que são compatíveis com 2.0 PowerShellVersion (com base no respetivo manifesto de módulo/script) serão apresentados.

## <a name="how-do-i-create-a-correctly-formatted-script-file"></a>Como criar um ficheiro de script formatado corretamente?

A forma mais fácil para criar um ficheiro de script formatado corretamente está a ser executado o [ **New-ScriptFileInfo** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet. No PowerShell 5.0, New-ScriptFileInfo gera um ficheiro de script corretamente formatado com campos em branco para metadados útil como **ProjectUri**, **LicenseUri**, e **etiquetas** . Basta preencher os espaços em branco ou utilize o ficheiro de script gerado como um exemplo de formatação correto.

Para verificar se todas as necessárias campos de metadados tem sido preenchidos corretamente, utilize o [ **teste ScriptFileInfo** ](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

Para atualizar os campos de metadados do script, utilize o [ **atualização ScriptFileInfo** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

## <a name="what-other-types-of-powershell-modules-exist"></a>O que outros tipos de módulos do PowerShell existem?

O módulo do PowerShell prazo refere-se também aos ficheiros que implementa a funcionalidade real. Ficheiros de módulo de script (. psm1) contêm código do PowerShell. Ficheiros de módulo binários (. dll) contêm código compilado.

Eis uma forma de pensar em: a pasta que contém o módulo é a pasta do módulo. A pasta do módulo pode conter um módulo de manifesto (. psd1) que descreve o conteúdo da pasta. Os ficheiros que, na verdade, faça o trabalho são os ficheiros de módulo de script (. psm1) e os ficheiros de módulo binários (. dll). Recursos de DSC estão localizados na pasta secundárias específica e são implementados como ficheiros de script de módulo ou os ficheiros de módulo binário.

Todos os módulos na Galeria contêm manifestos de módulo e a maioria destes módulos contêm ficheiros do módulo de script ou ficheiros de módulo binário. O módulo de termo pode ser confuso devido a estas significados diferentes. Salvo indicação em contrário, consulte todas as utilizações do módulo do word nesta página para a pasta de módulo que contêm esses ficheiros.

## <a name="how-does-packagemanagement-relate-to-powershellget-high-level-answer"></a>PackageManagement a inter-relação PowerShellGet? (Resposta de nível elevada)

PackageManagement é uma interface comum para trabalhar com qualquer gestor de pacotes. Eventualmente, se estiver a lidar com os módulos do PowerShell, MSIs, Ruby gems, pacotes de NuGet ou módulos Perl, deverá conseguir utilizar comandos do PackageManagement (pacote de localizar e Install-Package) para localizar e instalá-los. PackageManagement efetua este procedimento, fazendo com que um fornecedor do pacote para cada gestor de pacotes que plugs para PackageManagement. Fornecedores de fazer o trabalho real; obter o conteúdo do repositórios e instalar o conteúdo localmente. Muitas vezes, os fornecedores de pacote simplesmente são moldados à volta das ferramentas do Gestor de pacote existente para um tipo de pacote especificado.

PowerShellGet é o Gestor de pacote para os itens do PowerShell. Não há um fornecedor do pacote de PSModule que expõe uma funcionalidade de PowerShellGet através de PackageManagement. Por este motivo, é possível a execução [Install-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) ou Install-Package-PSModule de fornecedor para instalar um módulo da galeria do PowerShell. Algumas funcionalidades PowerShellGet, incluindo [Update-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) e [publicar-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), não pode ser acedido através de comandos PackageManagement.

Em resumo, PowerShellGet unicamente concentra-se de ter um uma experiência de gestão premium pacote para o conteúdo do PowerShell. PackageManagement concentra-se no exposição de todas as experiências de gestão de pacote através de um conjunto geral de ferramentas. Se encontrar esta resposta unsatisfying, há uma resposta longa na parte inferior deste documento, com o **does PackageManagement efetivamente a inter-relação PowerShellGet?** secção.

Para obter mais informações, visite o [página de projeto PackageManagement](https://oneget.org/).

## <a name="how-does-nuget-relate-to-powershellget"></a>NuGet a inter-relação PowerShellGet?

A galeria do PowerShell é uma versão modificada do [Galeria NuGet](https://www.nuget.org/). PowerShellGet utiliza o fornecedor do NuGet para trabalhar com os repositórios de NuGet com base como a galeria do PowerShell.

Pode utilizar PowerShellGet em relação a qualquer partilha de ficheiro ou de repositório NuGet válido. Apenas terá de adicionar o repositório executando o [ **Register-PSRepository** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

## <a name="does-that-mean-i-can-use-nugetexe-to-work-with-the-gallery"></a>Significa que pode utilizar o NuGet.exe para trabalhar com a Galeria?

Sim.

## <a name="how-does-packagemanagement-actually-relate-to-powershellget-technical-details"></a>PackageManagement efetivamente a inter-relação PowerShellGet? (Detalhes técnicos)

Os bastidores, PowerShellGet descontos elevados tira partido da infraestrutura de PackageManagement.

Na camada de cmdlet do PowerShell, [Install-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) é realmente um dinâmico wrapper em torno de Install-Package-PSModule do fornecedor.

Na camada de fornecedor do pacote de PackageManagement, o fornecedor do pacote de PSModule, na verdade, as chamadas para outros fornecedores de pacote PackageManagement. Por exemplo, quando estiver a trabalhar com baseado no NuGet galleries (tais como a galeria do PowerShell), o fornecedor do pacote de PSModule utiliza o fornecedor do pacote NuGet para trabalhar com o repositório.

![Arquitetura de PowerShellGet](Images/powershellgetArchitecture.png)

Figura 1: PowerShellGet arquitetura

## <a name="what-is-required-to-run-powershellget"></a>O que é necessário executar PowerShellGet?

Em geral, recomendamos que escolha a versão mais recente do módulo de PowerShellGet (tenha em atenção que requer o .NET 4.5).

O **PowerShellGet** módulo requer **PowerShell 3.0 ou mais recente**.

Por conseguinte, **PowerShellGet** necessita de um dos seguintes sistemas operativos:

- 10 do Windows
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

**PowerShellGet** também requer o .NET Framework 4.5 ou superior. Pode instalar o .NET Framework 4.5 ou superior do [aqui](https://msdn.microsoft.com/library/5a4x27ek.aspx).

## <a name="is-it-possible-to-reserve-names-for-items-that-will-be-published-in-future"></a>É possível reservar nomes de itens que serão publicados no futuro?

Não é possível os nomes de itens squat. Se sentir que um item existente realizou o nome que se adequa aos seus item mais, tente [contactar o proprietário do item](./how-to/working-with-items/contacting-item-owners.md). Se não obtiver resposta dentro de duas semanas, pode contactar o suporte e a equipa de galeria do PowerShell irá procurar ao mesmo.

## <a name="how-do-i-claim-ownership-for-items-"></a>Como posso reclamar a propriedade para itens?

Veja [Gerir proprietários do Item no PowerShellGallery.com](./how-to/publishing-items/managing-item-owners.md) para obter mais detalhes.

## <a name="how-do-i-deal-with-an-item-owner-who-is-violating-my-item-license"></a>Como lidar com um proprietário do item que está a violar meu licenciamento do item

Aconselhamo-Comunidade do PowerShell para funcionarem em conjunto para resolver quaisquer disputes que podem surgir entre os proprietários do item e os proprietários de outros itens.  Podemos ter crafted um [dispute o processo de resolução](./how-to/getting-support/dispute-resolution.md) que vamos pedir seguir antes dos administradores de PowerShellGallery.com intercede.