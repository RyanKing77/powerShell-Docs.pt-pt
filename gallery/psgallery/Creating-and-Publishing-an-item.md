---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: cmdlet do powershell do galeria, psgallery
title: Criar e publicar um item
ms.openlocfilehash: bbe9095b438e2ddb72a04055d1f05fbf20d4404a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="creating-and-publishing-an-item"></a>Criar e publicar um Item
A galeria do PowerShell é o local para publicar e partilhar estáveis módulos do PowerShell, scripts e recursos de DSC com a Comunidade de utilizadores mais abrangente do PowerShell.

Este artigo aborda as mechanics e passos importantes para preparar um script ou um módulo e publicar a galeria do PowerShell.
Aconselhamo vivamente que reveja o [diretrizes publicação](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery-PublishingGuidelines) para compreender como Certifique-se de que os itens a publicar mais amplamente aceitará utilizadores de galeria do PowerShell.

Se os requisitos mínimos para publicar um item de galeria do PowerShell:

* Ter uma conta de galeria do PowerShell e a chave de API associada
* Certifique-se de que está a ser o item de metadados necessários
* Utilizar as ferramentas de validação de pré-lançamento para garantir que o item está pronto para publicar
* Publicar o item de galeria do PowerShell com os comandos do módulo de publicar e publicar Script
* Está a responder à pergunta ou preocupação sobre o item

A galeria do PowerShell aceita módulos do PowerShell e scripts do PowerShell.
Quando é se refiram ao scripts, iremos significar um script do PowerShell que é um ficheiro único e não faz parte de um módulo maior.

## <a name="powershell-gallery-account-and-api-key"></a>Conta de galeria do PowerShell e a chave de API
Consulte [criar uma conta de galeria do PowerShell](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery_creating_an_account) para saber como configurar a conta de galeria do PowerShell.

Assim que tiver criado uma conta, pode obter a chave de API necessária para publicar um item.
Depois de iniciar sessão com a conta, o nome de utilizador será apresentado na parte superior das páginas da galeria do PowerShell em vez de registo.
Ao clicar no nome de utilizador leva-o para a página da minha conta, onde encontrará a chave de API.

Nota: A chave de API têm de ser tratada forma o início de sessão e palavra-passe mais segura.
Com esta chave, ou qualquer outra forma, pode atualizar qualquer item que proprietário na galeria do PowerShell.
Recomendamos que atualizar a chave de regularmente, que pode ser efetuada utilizando a chave de reposição da página da minha conta.

## <a name="required-metadata-for-items-published-to-the-powershell-gallery"></a>Metadados necessários para itens publicados para a galeria do PowerShell

A galeria do PowerShell fornece informações para utilizadores de galeria desenhados a partir de campos de metadados que estão incluídos no manifesto de módulo ou script.
Criar ou modificar itens para a publicação para a galeria do PowerShell tem um pequeno conjunto de requisitos para as informações fornecidas no manifesto de item.
Aconselhamo vivamente que reveja a secção de metadados do Item do [diretrizes publicação](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery-PublishingGuidelines) para saber como fornecer as informações sobre procedimentos a utilizadores com os itens.

O [New-ModuleManifest](https://msdn.microsoft.com/en-us/powershell/gallery/psget/module/ModuleManifest-Reference) e [New-ScriptFileInfo](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_new-scriptfileinfo) cmdlets criará o modelo de manifesto para si, com marcadores de posição para todos os elementos manifesto.

Os manifestos tem duas secções que são importantes para publicação, a área de dados de chave primária e PSData do PrivateData os dados de chave primários num manifesto de módulo do PowerShell está tudo fora da secção de PrivateData.
O conjunto de chaves primárias é associado à versão do PowerShell em utilização e não definido não são suportadas.
PrivateData suporta a adição de novas chaves, para que os elementos específicos para a galeria do PowerShell no PSData.


Elementos de manifesto que são mais importantes para preencher para item que publicar para a galeria do PowerShell são:

* Script ou o nome do módulo - aqueles são desenhados dos nomes da. PS1 para um script, ou o. PSD1 para um módulo.
* Versão - esta é uma chave primária necessária, formato deve seguir as diretrizes de SemVer (consulte as melhores práticas para obter detalhes)
* Autor - esta é uma chave primária necessária e contém o nome para estar associada com do item (consulte autores e proprietários, abaixo)
* Descrição - Esta é uma chave primária necessária, utilizada para explicar o que faz este item e os requisitos para utilizá-lo brevemente
* ProjectURI - este é um campo URI vivamente recomendado no PSData que fornece uma ligação para um repositório do Github ou semelhante localização onde o que fazer desenvolvimento no item

Autores e proprietários de galeria do PowerShell itens são conceitos relacionados, mas não corresponder sempre.
Os proprietários do item são utilizadores com contas de galeria do PowerShell que têm permissão para manter o item. Podem existir muitas proprietários quem podem atualizar qualquer item.
O proprietário só está disponível na galeria do PowerShell e não se tenha perdido, se o item é copiado a partir de um sistema para outro.
Autor é uma cadeia que está incorporada no manifesto dados, pelo que é sempre parte do item.
As recomendações para itens de produtos da Microsoft são:

* Tem várias proprietários, com pelo menos a ser o nome do agrupamento que produz o item;
* Ter o autor ser um nome de agrupamento reconhecido (por exemplo, a equipa do Azure SDK) ou Microsoft Corporation.


## <a name="pre-validate-your-item"></a>Pré-validar o Item

Existem algumas ferramentas que necessárias para executar no seu código antes de publicar o item de galeria do PowerShell:

* [Analisador de Script do PowerShell](https://www.powershellgallery.com/packages/PSScriptAnalyzer/), que se encontra na galeria do PowerShell
* Para módulos, teste-ModuleManifest que faz parte do PowerShell
* Para scripts, teste-ScriptFileInfo vem com o PowerShell Get

[Analisador de Script do PowerShell](https://www.powershellgallery.com/packages/PSScriptAnalyzer/) é uma ferramenta de análise de código estático que irá analisar o código para se certificar de que cumpre PowerShell básico codificação diretrizes. Esta ferramenta identificar problemas comuns e críticos no seu código e deve ser executada regularmente durante o desenvolvimento para o ajudar a preparar-se publicar o item.
Analisador de Script do PowerShell irá fornecer a lista de problemas identificados como informação, aviso e erros.
Todos os erros têm de ser resolvidos antes de publicar para a galeria do PowerShell. Tem de ser revistas avisos e, mais devem ser resolvido.
Analisador de Script do PowerShell é executado sempre que um item é publicado ou atualizado na galeria do PowerShell.
A equipa de operações de galeria irá contactar os proprietários de item erros de endereço que sejam encontrados.

Se as informações de manifesto do item não não possível ler a infraestrutura de galeria do PowerShell, não será capaz de publicar.
[Teste ModuleManifest](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-modulemanifest) irá detetar problemas comuns que faria com que o módulo não ser utilizável quando é instalado. Tem de ser executado para cada módulo antes de publicar para a galeria do PowerShell.

Da mesma forma, [teste ScriptFileInfo](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_test-scriptfileinfo) valida os metadados de um script e tem de ser executado em cada script (publicado separado a partir de um módulo) antes de publicar para a galeria do Powershell.


## <a name="publishing-items"></a>Itens de publicação

Tem de utilizar o [publicar Script](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_publish-script) ou [publicar-Module](https://msdn.microsoft.com/en-us/powershell/gallery/psget/module/psget_publish-module) para publicar itens de galeria do PowerShell.
Estes comandos que requerem ambos

* O caminho para o item, vai publicar. Para um módulo, utilize a pasta com o nome para o módulo. Se especificar uma pasta que contém várias versões do mesmo módulo, tem de especificar RequiredVersion.
* Uma chave de API do Nuget. Esta é a chave de API foi encontrada na página da minha conta na galeria do PowerShell.

A maioria das outras opções de linha de comandos deve ser nos dados de manifesto para o item que está a publicar, pelo que não será necessário especificá-los no comando.

Para evitar erros, é vivamente recomendado que tente os comandos utilizando - Whatif-Verbose, antes de publicar.
Isto irá poupar tempo considerável, desde sempre publicar para a galeria do PowerShell, tem de atualizar o número de versão na secção do manifesto do item.

Exemplos seriam: ' Publish-Module-caminho ". \MyModule" - RequiredVersion "0.0.1" - NugetAPIKey "GUID" - Whatif-Verbose' ' Publicar Script-caminho ".\MyScriptFile.PS1" - NugetAPIKey "GUID" - Whatif-Verbose'

Reveja cuidadosamente a saída e, se vir sem erros ou avisos, repita o comando sem - Whatif.

Todos os itens que são publicados galeria do PowerShell serão analisados antivírus e irão ser analisados utilizando o analisador de Script do PowerShell.
Quaisquer problemas que surgir nessa altura serão enviados para o publicador para a resolução.

Assim que tiver publicado um item a galeria do PowerShell, terá de procurar comentários sobre o item.

* Certifique-se de monitorizar o endereço de e-mail associado à conta utilizada para publicar.
Os utilizadores e a equipa de operações de galeria do PowerShell irão fornecer comentários através dessa conta, incluindo problemas do PSSA ou análises de antivírus.
Se a conta de correio eletrónico é inválida ou se forem reportados problemas graves para a conta e à esquerda não pode estar resolvido durante muito tempo, os itens podem ser considerados abandonado e serão removidos da galeria do PowerShell conforme descrito no nosso [os termos de utilização](https://www.powershellgallery.com/policies/Terms).
* Recomendamos que subscreve comentários para cada item de galeria do PowerShell que publicar.
Isto permite-lhe notificado se qualquer pessoa comentários no seus itens de galeria do PowerShell.
Isto é opcional, porque requer a criação de uma conta com LiveFyre.