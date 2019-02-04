---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, o powershell, o cmdlet, o psgallery
title: Criar e publicar um item
ms.openlocfilehash: 70696535a3bf540ff75a2dc43bca80cb1adf8f45
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684361"
---
# <a name="creating-and-publishing-an-item"></a>Criar e publicar um item

A galeria do PowerShell é o local para publicar e partilhar estáveis módulos do PowerShell, scripts e recursos de DSC com a mais ampla Comunidade de usuários do PowerShell.

Este artigo aborda a mecânica e os passos importantes para preparar um script ou um módulo e publicá-la na galeria do PowerShell. Recomendamos que reveja os [diretrizes de publicação](../../concepts/publishing-guidelines.md) para compreender como Certifique-se de que os itens a publicar mais amplamente aceitará por utilizadores da galeria do PowerShell.

Os requisitos mínimos para publicar um item da galeria do PowerShell são:

- Tem uma conta de galeria do PowerShell e a chave de API associado ao mesmo
- Certifique-se de que os metadados necessários está no seu item
- Utilizar as ferramentas de pré-validação para garantir que o item está pronto para publicar
- Publicar o item da galeria do PowerShell com os comandos de Publish-Module e Publish-Script
- Responder a perguntas ou preocupações sobre seu item

A galeria do PowerShell aceita módulos do PowerShell e scripts do PowerShell. Quando fazemos referência a scripts, queremos dizer um script do PowerShell que é um único arquivo e não faz parte de um módulo maior.

## <a name="powershell-gallery-account-and-api-key"></a>Conta da galeria do PowerShell e a chave de API

Ver [criar uma conta de galeria do PowerShell](/powershell/gallery/how-to/publishing-packages/creating-an-account) para saber como configurar a sua conta da galeria do PowerShell.

Assim que tiver criado uma conta, pode obter a chave de API necessária para publicar um item. Depois de iniciar sessão com a conta, seu nome de utilizador será apresentado na parte superior das páginas da galeria do PowerShell, em vez de Registro. Clicar no nome de utilizador leva-o para a página minha conta, onde encontrará a chave de API.

Nota: A chave de API deve ser tratada de forma mais segura do início de sessão e palavra-passe.
Com esta chave,, ou de qualquer outra, pode atualizar qualquer item que é proprietário na galeria do PowerShell.
Recomendamos que Atualize a chave regularmente, que pode ser feita com a chave de repor a sua página minha conta.

## <a name="required-metadata-for-items-published-to-the-powershell-gallery"></a>Metadados necessários para itens publicado na galeria do PowerShell

A galeria do PowerShell fornece informações para utilizadores de galeria obtidos dos campos de metadados que estão incluídos no manifesto do módulo ou script. Criação ou modificação de itens para a publicação na galeria do PowerShell tem um pequeno conjunto de requisitos para as informações fornecidas no manifesto de item.
Recomendamos que reveja a secção de metadados do Item do [diretrizes de publicação](../../concepts/publishing-guidelines.md) para saber como fornecer as melhores informações para os usuários com seus itens.

O [New-ModuleManifest](/powershell/module/microsoft.powershell.core/new-modulemanifest) e [New-ScriptFileInfo](/powershell/module/PowerShellGet/New-ScriptFileInfo) cmdlets, irá criar o modelo de manifesto para si, com marcadores de posição para todos os elementos de manifestos.

Ambos os manifestos tem duas secções que são importantes para a publicação, a área de dados de chave primária e PSData do PrivateData. Os dados de chave primários num manifesto de módulo do PowerShell são tudo o que fora de secção PrivateData. O conjunto de chaves primárias é vinculado à versão do PowerShell em uso e não definido não são suportadas. PrivateData suporta a adição de novas chaves, para que os elementos específicos na galeria do PowerShell são no PSData.


Manifestos elementos que são mais importantes para preencher para item que publicar na galeria do PowerShell são:

- Script ou o nome do módulo - aqueles são desenhados dos nomes da. PS1 para um script, ou o. PSD1 para um módulo.
- Versão - esta é uma chave primária necessária, o formato deve seguir as diretrizes de SemVer. Veja as práticas recomendadas para obter detalhes.
- Autor - esta é uma chave primária necessária e contém o nome a ser associado com o item.
Veja os autores e proprietários abaixo.
- Descrição - Esta é uma chave primária necessária, utilizado para explique brevemente o que faz este item e os requisitos para utilizá-lo
- ProjectURI - este é um campo URI vivamente recomendado num PSData que fornece uma ligação para um repositório do Github ou localização semelhante em que fizer o desenvolvimento no item
- Etiquetas - é uma recomendação veemente para etiquetar o pacote com base na respetiva compatibilidade com plataformas e edições do PowerShell. Para obter detalhes, consulte a [diretrizes de publicação](../../concepts/publishing-guidelines.md#tag-your-package-with-the-compatible-pseditions-and-platforms).

Itens de autores e proprietários de galeria do PowerShell são conceitos relacionados, mas sempre não correspondem. Os proprietários de itens são os utilizadores com contas de galeria do PowerShell que têm permissão para manter o item. Pode haver muitos proprietários que podem atualizar qualquer item. O proprietário está apenas disponível a partir da galeria do PowerShell e se perdem se o item é copiado a partir de um sistema para outro. Autor é uma cadeia que está incorporada no manifestos dados, pelo que sempre é parte do item. As recomendações para itens de produtos da Microsoft são:

- Ter vários proprietários, com, pelo menos, um ser o nome da Equipe que produz o item
- Ter o autor de ser um nome de equipa bem conhecidos (por exemplo, a equipe do SDK do Azure) ou Microsoft Corporation


## <a name="pre-validate-your-item"></a>Pré-validar seu Item

Existem algumas ferramentas que precisa para executar no seu código antes de publicar seu item da galeria do PowerShell:

- [PowerShell Script Analyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer/), que se encontra na galeria do PowerShell
- Para módulos, teste-ModuleManifest que faz parte do PowerShell
- Para scripts, teste-ScriptFileInfo que vem com o PowerShell Get

[PowerShell Script Analyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer/) é uma ferramenta de análise estática de código que irá analisar seu código para se certificar de que cumpre básico do PowerShell de diretrizes de codificação. Essa ferramenta irá identificar problemas comuns e críticos no seu código e deve ser executada regularmente durante o desenvolvimento para o ajudar a obter o seu item pronto para publicar. Analisador de Script do PowerShell irá fornecer a lista de problemas identificados como erros, avisos e informações. Todos os erros devem ser resolvidos antes de publicar a galeria do PowerShell. Avisos precisam ser examinadas e maioria deve ser resolvida. Analisador de Script do PowerShell é executado sempre que um item é publicado ou atualizado na galeria do PowerShell. A equipe de operações de galeria irá contactar os proprietários de itens para abordar erros encontrados.

Se as informações de manifesto no seu item não não possível ler a infraestrutura de galeria do PowerShell, não será capaz de publicar.
[Teste ModuleManifest](/powershell/module/microsoft.powershell.core/test-modulemanifest) capturará problemas comuns que faria com que o módulo a só ser utilizado quando é instalado. Tem de ser executado para cada módulo antes de publicá-la na galeria do PowerShell.

Da mesma forma, [teste ScriptFileInfo](/powershell/module/PowerShellGet/test-scriptfileinfo) valida os metadados num script e tem de ser executado em todos os scripts (publicado separado a partir de um módulo) antes de publicá-la na galeria do Powershell.


## <a name="publishing-items"></a>Itens de publicação

Tem de utilizar o [Publish-Script](/powershell/module/PowerShellGet/publish-script) ou [Publish-Module](/powershell/module/PowerShellGet/publish-module) para publicar itens da galeria do PowerShell. Estes comandos que requerem ambos:

- O caminho para o item que irá publicar. Para um módulo, utilize a pasta com o nome para seu módulo. Se especificar uma pasta que contém várias versões do módulo do mesmo, tem de especificar RequiredVersion.
- Uma chave de API do Nuget. Esta é a chave de API encontrada na página minha conta na galeria do PowerShell.

A maioria das outras opções na linha de comandos deve ser nos dados de manifestos para o item que está a publicar, para que não deve especificá-los no comando.

Para evitar erros, é altamente recomendável que experimente os comandos usando - Whatif-Verbose, antes da publicação. Esta ação irá guardar um tempo considerável, desde sempre que publicar na galeria do PowerShell, tem de atualizar o número de versão na secção de manifesto do item.

Exemplos seriam:

* `Publish-Module -Path ".\MyModule" -NugetAPIKey "GUID" -Whatif -Verbose`
* `Publish-Script -Path ".\MyScriptFile.PS1" -NugetAPIKey "GUID" -Whatif -Verbose`

Reveja o resultado com cuidado e, se vir há erros nem avisos, repita o comando sem o parâmetro-Whatif.

Todos os itens que são publicados na galeria do PowerShell serão analisados relativamente a vírus e serão ser analisados com o analisador de Script do PowerShell. As questões que surjam nesse momento serão enviadas para o publicador para a resolução.

Assim que tiver publicado um item na galeria do PowerShell, terá de ver para comentários no seu item.

- Certifique-se de que a monitorizar o endereço de e-mail associado à conta utilizada para publicar. Os utilizadores e a equipe de operações de galeria do PowerShell irão fornecer feedback através dessa conta, incluindo problemas do PSSA ou análises antivírus. Se a conta de e-mail é inválida ou se forem reportados problemas graves para a conta e esquerda durante muito tempo, os itens podem ser considerados abandonado e será removida da galeria do PowerShell, conforme descrito em nosso [termos de utilização](https://www.powershellgallery.com/policies/Terms).
- Recomendamos que subscreve comentários para cada item da galeria do PowerShell que publicar. Isto permite-lhe receber avisos caso alguém comentários nos seus itens na galeria do PowerShell. Isto é opcional, porque requer a criação de uma conta com a LiveFyre.
