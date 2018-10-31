---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, o powershell, o cmdlet, o psgallery
title: FAQs da galeria do PowerShell
ms.openlocfilehash: 3fa52892ce50491c040251baae8b4ae4ee3dcba0
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002877"
---
# <a name="frequently-asked-questions"></a>Perguntas Mais Frequentes

## <a name="what-is-a-powershell-module"></a>O que é um módulo do PowerShell?

Um módulo do PowerShell é um pacote reutilizável que contém algumas funcionalidades do PowerShell. Tudo no PowerShell (funções, variáveis, recursos de DSC, etc.) pode ser empacotado em módulos. Normalmente, os módulos são pastas que contêm tipos específicos de ficheiros armazenados num caminho específico. Existem alguns tipos diferentes de módulos do PowerShell por aí.

## <a name="what-is-a-powershell-script"></a>O que é um script do PowerShell?

Um script do PowerShell é uma série de comandos que estão armazenados num arquivo. ps1 para ativar a partilha e reutilização. Fluxos de trabalho do PowerShell também são scripts do PowerShell, que descrevem um conjunto de tarefas e fornecem o sequenciamento para essas tarefas. Para obter mais informações, visite [introdução ao fluxo de trabalho do PowerShell](https://technet.microsoft.com/library/jj134242.aspx).

## <a name="how-are-powershell-scripts-different-from-powershell-modules"></a>Como os Scripts do PowerShell são diferentes dos módulos do PowerShell?

Módulos são geralmente melhores para a partilha, mas estamos a ativar a partilha de script para torná-lo mais fácil para que possa contribuir com fluxos de trabalho e scripts para a Comunidade. Para obter mais informações, consulte os seguintes blogues:

- [Não escrever Scripts, módulos do PowerShell de escrita](https://blogs.technet.microsoft.com/heyscriptingguy/2011/06/27/dont-write-scripts-write-powershell-modules/)
- [Compreender os módulos do PowerShell](https://blogs.technet.microsoft.com/heyscriptingguy/2015/07/10/understanding-powershell-modules/)

## <a name="how-can-i-publish-to-the-powershell-gallery"></a>Como posso publicar a galeria do PowerShell?

Tem de registar uma conta da galeria do PowerShell antes de poder publicar pacotes na galeria. Isto acontece porque a publicação de pacotes requer um NuGetApiKey, que é fornecido no registo. Para registar, utilize o seu trabalho pessoal, conta escolar ou iniciar sessão na galeria do PowerShell. Um processo de registo único é necessário quando iniciar sessão pela primeira vez. Depois disso, a sua NuGetApiKey está disponível na página de perfil.

Assim que se registrou na galeria, utilize o [Publish-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) ou [Publish-Script](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlets para publicar o pacote na galeria. Para obter mais detalhes sobre como executar estes cmdlets, visite a guia Publish ou ler os [Publish-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) e [Publish-Script](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) documentação.

**Não é necessário registrar ou iniciar sessão na Galeria para instalar ou guardar pacotes.**

## <a name="i-received-failed-to-process-request-the-specified-api-key-is-invalid-or-does-not-have-permission-to-access-the-specified-package-the-remote-server-returned-an-error-403-forbidden-error-when-i-tried-to-publish-a-package-to-the-powershell-gallery-what-does-that-mean"></a>Recebi "Falha ao processar o pedido. "A chave de API especificada é inválida ou não tem permissão para aceder ao pacote especificado.". O servidor remoto devolveu um erro: (403) proibido. " Erro ao tentar publicar um pacote para a galeria do PowerShell. O que isso significa?

Este erro pode ocorrer pelos seguintes motivos:

- **A chave de API especificada é inválida.**
     Certifique-se de que especificou a chave de API válida da sua conta. Para obter a chave de API, exiba sua página de perfil.
- **O nome do pacote especificado não é possuído por si.**
     Se tiver confirmado que a chave de API está correta, em seguida, pode já existir um pacote com o mesmo nome que aquela que está a tentar utilizar. O pacote pode ter sido não listado pelo proprietário, caso em que não irá aparecer nos resultados da pesquisa. Para determinar se um pacote com o mesmo nome já existe, abra um browser e navegue até à página de detalhes do pacote: `https://www.powershellgallery.com/packages/<packageName>`. Por exemplo, ao navegar diretamente para `https://www.powershellgallery.com/packages/pester` levará à página de detalhes do módulo Pester, independentemente de ser não listado ou não. Se um pacote com um nome em conflito já existe e é não listado, pode:
    - Selecione outro nome para o seu pacote.
    - Entre em contato com os proprietários do pacote existente.

## <a name="why-cant-i-sign-in-with-my-personal-account-but-i-could-sign-in-yesterday"></a>Por que não consigo iniciar sessão com a minha conta pessoal, mas pode iniciar sessão ontem?

. Lembre-se de que a sua conta de Galeria não acomoda as alterações ao seu alias de e-mail principal. Para obter mais informações, consulte [Aliases de Email da Microsoft](https://windows.microsoft.com/windows/outlook/add-alias-account).

## <a name="why-dont-i-see-all-the-gallery-packages-when-i-select-all-the-category-checkboxes-on-the-packages-tab"></a>Por que motivo não vejo todos os pacotes de galeria quando seleciono todas as categorias caixas de seleção na guia pacotes?

Ao selecionar uma caixa de seleção de categoria, são a indicar "Gostaria de ver todos os pacotes nesta categoria." Apenas os pacotes nas categorias selecionadas serão exibidos. Então, da mesma forma, ao selecionar todas as caixas de seleção de categoria, é que diz "Eu gostaria de ver todos os pacotes de qualquer categoria." Mas alguns pacotes na Galeria não pertencer a nenhuma das categorias listadas, pelo que não serão apresentados nos resultados. Para ver todos os pacotes na galeria, desmarque todas as categorias ou selecione o separador de pacotes novamente.

## <a name="what-are-the-requirements-to-publish-a-module-to-the-powershell-gallery"></a>Quais são os requisitos para publicar um módulo da galeria do PowerShell?

Qualquer tipo de módulo do PowerShell (módulos de script, módulos binários ou módulos de manifestos) pode ser publicado na galeria. Para publicar um módulo, PowerShellGet precisa saber algumas coisas sobre ele - a versão, descrição, autor e como é licenciado. Estas informações é de leitura como parte do processo de publicação do *manifesto de módulo* ficheiro (. psd1), ou do valor dos [ **Publish-Module** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) do cmdlet **LicenseUri** parâmetro. Todos os módulos publicados na Galeria tem de ter os manifestos de módulo. Qualquer módulo que inclui as seguintes informações em seu manifesto pode ser publicado na galeria:

- Versão
- Descrição
- Autor
- Um URI para os termos de licenciamento do módulo, como parte do **PrivateData** secção de manifesto, ou no **LicenseUri** parâmetro do [ **Publish-Module** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

## <a name="how-do-i-create-a-correctly-formatted-module-manifest"></a>Como posso criar um manifesto de módulo formatadas corretamente?

A maneira mais fácil para criar um manifesto de módulo está a executar o [ **New-ModuleManifest** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet. No PowerShell 5.0 ou mais recente, New-ModuleManifest gera um manifesto de módulo formatado corretamente com campos em branco para metadados úteis, como **ProjectUri**, **LicenseUri**, e **etiquetas**. Simplesmente preencha os espaços em branco ou utilize o manifesto gerado como um exemplo de formato correto.

Para verificar-se de que todas as necessárias campos de metadados tem sido preenchidos adequadamente, utilize o [ **teste ModuleManifest** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

Para atualizar os campos do ficheiro de manifesto de módulo, utilize o [ **atualização ModuleManifest** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

## <a name="what-are-the-requirements-to-publish-a-script-to-the-gallery"></a>Quais são os requisitos para publicar um script para a Galeria?

Qualquer tipo de script do PowerShell (scripts ou fluxos de trabalho) pode ser publicado na galeria. Para publicar um script, o PowerShellGet tem de saber algumas coisas sobre ele - a versão, descrição, autor e como é licenciado. Estas informações é de leitura como parte do processo de publicação do ficheiro de script *PSScriptInfo* secção, ou a partir do valor da [ **Publish-Script** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) do cmdlet  **LicenseUri** parâmetro. Todos os scripts publicados na Galeria tem de ter informações de metadados. Qualquer script que inclui as seguintes informações na respetiva secção PSScriptInfo pode ser publicado na galeria:

- Versão
- Descrição
- Autor
- Um URI para os termos de licenciamento do script, como parte do **PSScriptInfo** secção do script ou na **LicenseUri** parâmetro do [ **Publish-Script** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

## <a name="how-do-i-search"></a>Como faço para pesquisar?

Escreva o que precisa na caixa de texto. Por exemplo, se quiser encontrar módulos que estão relacionados ao SQL do Azure, basta digite "sql do azure". Nosso motor de pesquisa irá procurar essas palavras-chave em todos os pacotes publicados, incluindo títulos, descrições e em todos os metadados. Em seguida, com base numa pontuação de qualidade ponderada, apresentará as correspondências mais próximas. Também pode pesquisar por campo específico usando o campo: "valor" sintaxe na consulta de pesquisa para os seguintes campos:

- Etiquetas
- Funções
- Cmdlets
- DscResources
- PowerShellVersion

Assim, por exemplo, quando pesquisa na PowerShellVersion: "2.0" apenas os resultados que são compatíveis com 2.0 PowerShellVersion (com base no respetivo manifesto de módulo/script) serão exibidos.

## <a name="how-do-i-create-a-correctly-formatted-script-file"></a>Como posso criar um ficheiro de script formatadas corretamente?

A maneira mais fácil para criar um ficheiro de script formatado corretamente é executar o [ **New-ScriptFileInfo** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet. No PowerShell 5.0, New-ScriptFileInfo gera um ficheiro de script formatado corretamente com campos em branco para metadados úteis, como **ProjectUri**, **LicenseUri**, e **etiquetas** . Simplesmente preencha os espaços em branco ou utilize o ficheiro de script gerado como um exemplo de formato correto.

Para verificar-se de que todas as necessárias campos de metadados tem sido preenchidos adequadamente, utilize o [ **teste ScriptFileInfo** ](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

Para atualizar os campos de metadados do script, utilize o [ **atualização ScriptFileInfo** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

## <a name="what-other-types-of-powershell-modules-exist"></a>O que existem outros tipos de módulos do PowerShell?

O módulo do PowerShell do termo refere-se também para os ficheiros que implementam a funcionalidade real. Ficheiros de módulo de script (. psm1) contêm código do PowerShell. Ficheiros de módulo binário (. dll) contêm código compilado.

Aqui está uma forma de pensar sobre ele: a pasta que encapsula o módulo é a pasta de módulo. A pasta de módulo pode conter um manifesto de módulo (. psd1) que descreve o conteúdo da pasta. Os ficheiros que, na verdade, fazem o trabalho são os arquivos de módulo de script (. psm1) e os ficheiros de módulo binário (. dll). Recursos de DSC estão localizados numa subpasta específica e são implementados como arquivos de módulo de script ou binária do módulo.

Contenham todos os módulos da galeria do módulo manifestos e a maioria destes módulos contém arquivos de módulo de script ou binária do módulo. O módulo de condição pode ser confuso devido a esses diferentes significados. A menos que explicitamente indicação em contrário, todas as utilizações do módulo do word nesta página referem-se para a pasta de módulo que contém estes ficheiros.

## <a name="how-does-packagemanagement-relate-to-powershellget-high-level-answer"></a>Como é que PackageManagement se relaciona com o PowerShellGet? (Resposta de nível alta)

PackageManagement é uma interface comum para trabalhar com qualquer gestor de pacotes. Eventualmente, se estiver lidando com módulos do PowerShell, MSIs, pedras preciosas de Ruby, pacotes de NuGet ou módulos do Perl, deverá conseguir utilizar comandos do PackageManagement (pacote de localizar e Install-Package) para localizar e instalá-los. PackageManagement faz isso, fazendo com que um fornecedor do pacote para cada gestor de pacotes que se vincula ao PackageManagement. Fornecedores de fazer todo o trabalho real; obter conteúdo de repositórios e instalar o conteúdo localmente. Muitas vezes, os fornecedores de pacote simplesmente encapsular as ferramentas do Gestor de pacote existente para um tipo de dado pacote.

O PowerShellGet é o Gestor de pacotes para pacotes do PowerShell. Existe um fornecedor do pacote de PSModule que expõe a funcionalidade do PowerShellGet através do PackageManagement. Por este motivo, pode execute [Install-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) ou Install-Package-PSModule de fornecedor para instalar um módulo da galeria do PowerShell. Determinadas funcionalidades do PowerShellGet, incluindo [Update-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) e [Publish-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), não pode ser acedido através do PackageManagement comandos.

Em resumo, o PowerShellGet unicamente se concentra em ter uma experiência de gestão do pacote de premium para o conteúdo do PowerShell. PackageManagement se concentra em expor todas as experiências de gestão de pacote por meio de um conjunto geral de ferramentas. Se encontrar esta resposta unsatisfying, há uma resposta longa na parte inferior deste documento, na **como o PackageManagement, na verdade, se relaciona com o PowerShellGet?** secção.

Para obter mais informações, visite o [página do projeto PackageManagement](https://oneget.org/).

## <a name="how-does-nuget-relate-to-powershellget"></a>Como é que NuGet se relaciona com o PowerShellGet?

A galeria do PowerShell é uma versão modificada dos [galeria do NuGet](https://www.nuget.org/). O PowerShellGet usa o provedor de NuGet para trabalhar com repositórios de NuGet com base em como a galeria do PowerShell.

Pode usar o PowerShellGet contra qualquer partilha de ficheiro ou de repositório NuGet válido. Basta adicionar o repositório ao executar o [ **Register-PSRepository** ](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) cmdlet.

## <a name="does-that-mean-i-can-use-nugetexe-to-work-with-the-gallery"></a>Significa que posso usar NuGet.exe para trabalhar com a Galeria?

Sim.

## <a name="how-does-packagemanagement-actually-relate-to-powershellget-technical-details"></a>Como o PackageManagement, na verdade, se relaciona com o PowerShellGet? (Detalhes técnicos)

Nos bastidores, o PowerShellGet intensamente tira partido da infraestrutura de PackageManagement.

Na camada de cmdlet do PowerShell, [Install-Module](https://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) é, na verdade, um wrapper estreito em torno de Install-Package-PSModule de fornecedor.

Na camada de fornecedor do pacote do PackageManagement, o fornecedor do pacote de PSModule chama, na verdade, outros fornecedores de serviços do pacote PackageManagement. Por exemplo, quando estiver a trabalhar com base em NuGet galerias (por exemplo, a galeria do PowerShell), o fornecedor do pacote de PSModule utiliza o fornecedor do pacote NuGet para trabalhar com o repositório.

![Arquitetura do PowerShellGet](Images/powershellgetArchitecture.png)

Figura 1: Arquitetura de PowerShellGet

## <a name="what-is-required-to-run-powershellget"></a>O que é necessário para executar o PowerShellGet?

Em geral, recomendamos que escolha a versão mais recente do módulo PowerShellGet (Observe que ela requer o .NET 4.5).

O **PowerShellGet** requer o módulo **PowerShell 3.0 ou mais recente**.

Por conseguinte, **PowerShellGet** requer um dos seguintes sistemas operativos:

- 10 do Windows
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- O Windows 7 SP1
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

**O PowerShellGet** também requer o .NET Framework 4.5 ou superior. Pode instalar o .NET Framework 4.5 ou superior partir [aqui](https://msdn.microsoft.com/library/5a4x27ek.aspx).

## <a name="is-it-possible-to-reserve-names-for-packages-that-will-be-published-in-future"></a>É possível reservar os nomes dos pacotes que serão publicados no futuro?

Não é possível para nomes de pacotes gorda. Se sentir que um pacote existente apresentou o nome que lhe seja conveniente seu pacote mais, tente [contactar o proprietário do pacote](./how-to/working-with-packages/contacting-package-owners.md). Se não tiver resposta dentro de duas semanas, pode contactar o suporte e a equipe de galeria do PowerShell irá procurar em ao mesmo.

## <a name="how-do-i-claim-ownership-for-packages"></a>Como posso usufruir a propriedade pacotes?

Confira [proprietários de pacote de gestão na PowerShellGallery.com](./how-to/publishing-packages/managing-package-owners.md) para obter detalhes.

## <a name="how-do-i-deal-with-a-package-owner-who-is-violating-my-package-license"></a>Como faço para lidar com um proprietário do pacote que é a minha licença do pacote de violação?

Nós o encorajamos a Comunidade do PowerShell para trabalhar em conjunto para resolver a resolução de eventuais litígios que pode surgir entre os proprietários de pacote e os proprietários de outros pacotes.  Podemos ter elaborado uma [processo de resolução de litígios](./how-to/getting-support/dispute-resolution.md) que pedimos que siga antes dos administradores de PowerShellGallery.com intercede.
