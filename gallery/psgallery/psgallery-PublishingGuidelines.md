---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: cmdlet do powershell do galeria, psgallery
description: Diretrizes para publicadores
title: Galeria do PowerShell publicação orientações e melhores práticas
ms.openlocfilehash: ba9c02b07af85c02abad06f4c9141c4c425f80f3
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="powershellgallery-publishing-guidelines-and-best-practices"></a>PowerShellGallery publicação orientações e melhores práticas

Este tópico descreve os passos recomendados utilizados por equipas da Microsoft para garantir que os itens publicados para a galeria do PowerShell amplamente adotados e fornecem valor elevado aos utilizadores, com base na forma como a galeria do PowerShell processa dados manifesto e nos comentários de grandes quantidades de utilizadores de galeria do PowerShell.
Os itens que são publicados seguir estas diretrizes serão maior probabilidade de ser instalado, fidedignos e attract mais utilizadores.

Incluída abaixo, são as diretrizes para o que faz com que um item de galeria do PowerShell boa, as definições de manifesto opcionais são mais importantes, melhorando o seu código com comentários de revisores iniciais e [analisador de Script do Powershell](https://aka.ms/psscriptanalyzer), controlo de versões o módulo, documentação, testes e exemplos de como utilizar o que tenha partilhado.
Grande parte desta documentação segue-se as diretrizes para publicação [elevada módulos de recursos de DSC de qualidade](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md).

Para mechanics de publicação de um item de galeria do PowerShell, consulte [criar e publicar um Item](https://msdn.microsoft.com/powershell/gallery/psgallery/creating-and-publishing-an-item).

Comentários sobre estas diretrizes é welcomed. Se tiver comentários, abra os problemas no nosso [repositório do Github documentação](https://github.com/powershell/powershell-docs/).

## <a name="best-practices-for-publishing-items"></a>Melhores práticas para a publicação de itens

As seguintes melhores práticas são que os utilizadores de itens de galeria do PowerShell diga é importante e são listadas por ordem de prioridade nominal.
Os itens que siga estas diretrizes são muito maior probabilidade de ser transferidos e adotado uma larga maioria por outras pessoas.

* Utilizar PSScriptAnalyzer
* Incluir documentação e exemplos
* Estar a responder aos comentários
* Fornecer módulos em vez de scripts
* Fornecem ligações para um site do projeto
* Incluir testes com os módulos
* Incluir e/ou ligação termos de licenciamento
* Inicie o seu código
* Siga [SemVer](http://semver.org/) diretrizes para controlo de versões
* Utilize etiquetas comuns, conforme documentado na galeria do PowerShell comuns etiquetas
* Publicação de teste utilizando um repositório local

Cada um destes é descrita por breves instantes nas secções abaixo.

## <a name="use-psscriptanalyzer"></a>Utilizar PSScriptAnalyzer

[PSScriptAnalyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer) é uma ferramenta de análise de código estático livre funciona no código do PowerShell.
PSScriptAnalyzer vão identificar os problemas mais comuns vistos no código do PowerShell e, muitas vezes, uma recomendação para saber como corrigir o problema.
É fácil de utilizar a ferramenta e categoriza os problemas como erros (grave, têm de ser resolvidos), aviso (tem de ser revistas & deve ser tratada) e as informações (vale procurar melhores práticas de).
Todos os itens de itens publicados para a galeria do PowerShell serão analisados utilizando PSScriptAnalyzer e quaisquer erros serão comunicados novamente para o proprietário e têm de ser resolvidos.

A melhor prática consiste em executar `Invoke-ScriptAnalyzer` com `-Recurse` e `-Severity` aviso.

Reveja os resultados e certifique-se de que:

* Todos os erros são corrigidos ou constar da documentação
* Todos os avisos são revistos e resolvidos, quando aplicável

Os utilizadores que adquirir itens da galeria do PowerShell são vivamente recomendados para executar PSScriptAnalyzer e avaliar todos os erros e avisos.
Os utilizadores são muito prováveis contactar os proprietários do item se de que veem que existe um erro comunicado pelo PSScriptAnalyzer.
Se existir uma razão apelativa para o item manter o código que está assinalado como um erro, adicione essa informação para a documentação para evitar a necessidade que responder a mesma pergunta demasiadas vezes.

## <a name="include-documentation-and-examples"></a>Incluir documentação e exemplos

Documentação e exemplos são a melhor forma, certifique-se de que os utilizadores podem tirar partido de qualquer código partilhado.

Documentação é a coisa mais útil para incluir itens publicados para a galeria do PowerShell.
Os utilizadores, geralmente, irão ignorar itens sem documentação, como a alternativa é ler o código para compreender o que é o item e como utilizá-la.
Existem vários artigos disponíveis na MSDN sobre como fornecer documentação com itens de PowerShell, incluindo:

* São as diretrizes para fornecer ajuda na [como escrever ajuda do Cmdlet](https://go.microsoft.com/fwlink/?LinkID=123415)
* A criação de ajuda do cmdlet, que é a melhor abordagem para qualquer script do PowerShell, a função ou o cmdlet.
  Para obter informações sobre como criar a ajuda do cmdlet, começar a utilizar [como escrever ajuda do Cmdlet](https://go.microsoft.com/fwlink/?LinkID=123415) na biblioteca da MSDN.
  Para adicionar ajuda dentro de um script, consulte [sobre comentário com base em ajudar](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_comment_based_help).
* Muitos módulos também incluem documentação no formato de texto, tal como ficheiros MarkDown.
  Isto pode ser particularmente útil quando existe um site de projeto no Github, onde o Markdown é um formato muito utilizado.
  A melhor prática consiste em utilizar [Markdown característico do Github](https://help.github.com/categories/writing-on-github/)

Exemplos mostram os utilizadores como o item se destina a ser utilizado.
Os programadores muitos indicará que observe exemplos antes de documentação para compreender como utilizar algo.
O melhor exemplos mostram a utilização básica, e um caso de utilização realistas simulada e o código é comentado bem.
Exemplos de módulos publicados na galeria do PowerShell devem estar numa pasta exemplos na raiz de módulo.

Pode encontrar um boa padrão para obter exemplos a [PSDscResource módulo](https://www.powershellgallery.com/packages/PSDscResources) sob a pasta de Examples\RegistryResource.
Existem quatro casos de utilização de exemplo com uma breve descrição na parte superior de cada ficheiro nessa documentos que está a ser demonstrado.

## <a name="respond-to-feedback"></a>Responder a comentários

Os proprietários do item que respondem corretamente aos comentários são altamente valor pela Comunidade.
Os utilizadores que constructive comentários são importantes para responder a, conforme forem interessados no item de tentar ajudar a melhorar esta.

Existem dois métodos de comentários disponíveis na galeria do PowerShell:

* Proprietário do contacto: Isto permite que um utilizador enviar um e-mail para o item owner(s). Como proprietário do item, é importante para monitorizar o endereço de e-mail utilizado com os itens de galeria do PowerShell e responder a problemas que são gerados. A um desvantagem a este método é a que apenas o utilizador e o proprietário alguma vez Verão a comunicação, pelo que pode ter o proprietário para responder a mesma pergunta demasiadas vezes.
* Comentários: Na parte inferior da página item é um campo de comentário.
  A vantagem a este sistema é que outros utilizadores podem ver os seus comentários e respostas, que reduz o número de vezes que a qualquer pergunta único têm de ser respondida.
  Como proprietário do item, recomenda-se vivamente que seguem os comentários efetuados para cada item.
Consulte [fornecer comentários através de redes sociais ou comentários](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery-SocialMediaFeedback) para obter detalhes sobre como fazê-lo.

Os proprietários que respondem aos comentários constructively são appreciated pela Comunidade.
Utilize a oportunidade no relatório para obter mais informações de pedido, se necessário, fornecem uma solução ou identificar se uma atualização corrige um problema.

Se houver comportamento inadequado observado utilizando um estes canais de comunicação, utilize a funcionalidade de relatório abuso da galeria do PowerShell para contactar os administradores de galeria.

## <a name="modules-versus-scripts"></a>Módulos Versus Scripts

Um script de partilha com outros utilizadores é ótimo e fornece outras pessoas com exemplos sobre como resolver problemas que podem ter.
O problema é que os scripts na galeria do PowerShell são ficheiros único sem documentação separada, exemplos e testes.

Módulos do PowerShell têm uma estrutura de pasta que permite que várias pastas e ficheiros para ser incluída no pacote.
A estrutura do módulo permite, incluindo os outros itens que lista como as melhores práticas: cmdlet ajuda, documentação, exemplos e testes.
A desvantagem maior é que um script no interior de um módulo tem de ser exposto e utilizado como uma função.
Para obter informações sobre como criar um módulo, consulte [escrever um módulo do Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=144916).

Existem situações em que um script fornece uma melhor experiência para o utilizador, particularmente com configurações de DSC.
É recomendado para configurações de DSC publicar a configuração como um script com um módulo associado que contém os documentos, exemplos e testes.
O script apresenta o módulo associado utilizando RequiredModules = @(nome do módulo).
Esta abordagem pode ser utilizada com qualquer script.

Scripts de autónomo que se seguem outros procedimentos recomendados fornecem valor real para outros utilizadores.
Fornecer documentação baseada no comentário e uma hiperligação para um Site de projeto são altamente recomendados ao publicar um script para a galeria do PowerShell.

## <a name="provide-a-link-to-a-project-site"></a>Forneça uma ligação a um site do projeto

Um Site de projeto é onde um publicador pode interagir diretamente com os utilizadores com os seus itens de galeria do PowerShell.
Os utilizadores preferem itens que fornecem, como permite-los obter informações sobre o item mais facilmente.
Número de itens na galeria do PowerShell é desenvolvida no GitHub, outros são fornecidos por organizações com uma presença na web dedicado.
Cada um destes pode ser considerada um site de projeto.

Adicionar uma ligação é efetuada, incluindo ProjectURI na secção do manifesto PSData da seguinte forma:

        # A URL to the main website for this project.
        ProjectUri = 'https://github.com/powershell/powershell'

Quando é fornecido um ProjectURI, Galeria do PowerShell irá incluir uma ligação para o Site de projeto no lado esquerdo da página do item.

## <a name="include-tests"></a>Incluir testes

Incluindo testes com o código de open source é importante para os utilizadores, como lhes concede garantia sobre o que poderá valida e fornece informações sobre como funciona o seu código. Também permite que os utilizadores para se certificar de que não interromper a funcionalidade original se estes modificar o código para ajustar o respetivo ambiente.

É vivamente recomendado que os testes ser escrito para tirar partido da estrutura de teste Pester, que tem foi concebido especificamente para o PowerShell.
Pester está disponível no [GitHub](https://github.com/Pester/Pester), a [galeria do PowerShell](https://www.powershellgallery.com/packages/Pester/)e é incluído no Windows 10, Windows Server 2016, WMF 5.0 e WMF 5.1.

O [Pester site de projeto no GitHub](https://github.com/Pester/Pester) inclui boa documentação sobre como escrever Pester testes, de introdução para melhores práticas.

Os destinos da cobertura de teste são realçados no [documentação do módulo de recurso de qualidade elevada](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md), com a unidade de 70% de cobertura de código recomendada de teste.

## <a name="include-andor-link-to-license-terms"></a>Incluir e/ou ligação termos de licenciamento

Todos os itens publicados para a galeria do PowerShell tem de especificar os termos de licenciamento ou estar vinculados pela licença incluída no [os termos de utilização](https://www.powershellgallery.com/policies/Terms) em "A apresentem um".
É a melhor abordagem para especificar uma licença diferentes para fornecer uma ligação para a licença com o LicenseURI no PSData.
Pode encontrar um exemplo no tópico recomendado campos de manifesto.

```powershell
PrivateData = @{
    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        Tags = @('.net','acl','active-directory')

        # A URL to the license for this module.
        LicenseUri = 'http://www.apache.org/licenses/LICENSE-2.0'
```

## <a name="sign-your-code"></a>Inicie o seu código

Assinatura de código fornece aos utilizadores com o nível mais elevado de garantia para publicados quem o item e que a cópia do código adquirir é exatamente o que o publicador lançada.
Para saber mais sobre geralmente de assinatura de código, consulte o artigo [introdução à assinatura de código](http://go.microsoft.com/fwlink/?LinkId=106296).
PowerShell suporta a validação de através de duas abordagens primárias de assinatura de código:

* Assinatura de ficheiros de script
* Um módulo de assinatura de catálogo

Assinatura de ficheiros do PowerShell é uma abordagem bem estabelecida para se certificar de que o código que está a ser executado foram produzido por uma origem fiável e não foi modificado.
Detalhes sobre como assinar os ficheiros de script do PowerShell é abordada o [sobre assinatura](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_signing) tópico.
Na descrição geral, uma assinatura pode ser adicionada a nenhum. Ficheiro de PS1 PowerShell valida quando o script é carregado.
Pode ser restringido PowerShell utilizando o [política de execução](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_execution_policies) assinada de cmdlets para garantir a utilização de scripts.

Catálogo de módulos de assinatura é uma funcionalidade adicionada para o PowerShell na versão 5.1.
Como assinar um módulo é abordado o [catálogo Cmdlets](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/catalog-cmdlets) tópico.
Na descrição geral, a assinatura do catálogo é feito através da criação de um ficheiro de catálogo que contém um valor de hash para todos os ficheiros no módulo, e, em seguida, esse ficheiro de assinatura.
O módulo publicar PowerShellGet, install-module, guardar-module e os cmdlets do módulo de atualização irá verificar a assinatura para garantir que é válido, em seguida confirmar que o valor de hash para cada item corresponde ao que está no catálogo.
Se está instalada uma versão anterior do módulo no sistema, instale-module confirma que a autoridade de assinatura para a nova versão corresponde ao que foi anteriormente instalado.
Assinatura de catálogo funciona com, mas não substitui a assinatura de ficheiros de script. PowerShell não validam assinaturas de catálogo em tempo de carregamento do módulo.

## <a name="follow-semver-guidelines-for-versioning"></a>Siga as diretrizes de SemVer para controlo de versões

[SemVer](http://semver.org/) é uma convenção de pública que descreve como estruturar e alterar uma versão para permitir intepretation fácil das alterações.
A versão para o item tem de ser incluída nos dados de manifesto.

* A versão deve ser estruturada como 3 blocos numéricos separados por pontos, tal como em 0.1.1 ou 4.11.192
* Versões que iniciam com "0" indicam que o item ainda não está pronta de produção e o primeiro número só deve começar por "0", se o que é o número de apenas utilizado
* Alterações ao número primeiro (1.9.9999 para 2.0.0) indicam as alterações principais e de última hora entre as versões
* As alterações para o segundo número (1.01 para 1.02) indicam as alterações a nível de funcionalidade, como adicionar novos cmdlets para um módulo
* Alterações ao número terceiro indicam sem quebra alterações, como novos parâmetros, amostras atualizadas ou novos testes
* Quando listar as versões, PowerShell para ordenar as versões como cadeias, pelo que 1.01.0 serão tratados como maior 1.001.0

PowerShell foi criado antes de SemVer foi publicado, pelo que fornece suporte para a maioria das mas nem todos os elementos de SemVer, especificamente:

* Não suporta cadeias pré-lançamento números de versão. Isto é útil quando um publicador pretende fornecer uma versão de pré-visualização de uma nova versão principal depois de fornecer uma versão 1.0.0. Isto será suportado numa versão futura dos cmdlets galeria do PowerShell e PowerShellGet.
* PowerShell e galeria do PowerShell permitem cadeias de versão com 1, 2 e 4 segmentos. Muitos módulos antecipados não foi possível seguir as diretrizes e versões de produto da Microsoft incluem informações da compilação como bloquear uma 4 de números (por exemplo 5.1.14393.1066). A partir de um ponto de vista do controlo de versões, estas diferenças são ignoradas.

## <a name="test-using-a-local-repository"></a>Testar a utilizar um repositório local

A galeria do PowerShell não foi concebida para ser um destino para testar o processo de publicação.
É a melhor forma de testar o processo ponto a ponto da publicação para a galeria do PowerShell para configurar e utilizar o seus próprios repositório local.
Isto pode ser feito na algumas formas, incluindo:

* Configurar uma instância local da galeria do PowerShell, utilizando o [projeto PS privada galeria](https://github.com/PowerShell/PSPrivateGallery) no Github. Este projeto de pré-visualização ajudarão a configurar uma instância de galeria do PowerShell que pode controlar e utilização para os testes.
* Configurar um [interno Nuget repositório](https://blogs.msdn.microsoft.com/powershell/2014/05/20/setting-up-an-internal-powershellget-repository/). Irá necessitar mais tarefas para configurar, mas tem a vantagem de validar mais alguns requisitos, nomeadamente a validar a utilização de uma chave de API e se deve ou não as dependências estão presentes no destino quando publicar.
* Configure uma partilha de ficheiros como o teste "repositório". Isto é fácil de configurar, mas uma vez que é uma partilha de ficheiros, validações indicadas acima não ocorrerá. Neste caso, uma potencial vantagem é que a partilha de ficheiros não verifica se a chave de API (obrigatório), pelo que pode utilizar a mesma chave que faria para publicar a galeria do PowerShell.

Com qualquer uma destas soluções, utilize Register-PSRepository para definir um novo "repositório", que utilizar na propriedade - repositório para o módulo de publicar.

Um ponto adicional sobre a publicação de teste: não é possível eliminar qualquer item de publicar para a galeria do PowerShell da ajuda da equipa de operações, que confirma que nada está dependente do item que pretende publicar.
Por esse motivo, iremos não suportam a galeria do PowerShell como um destino de teste e irá contactar qualquer fabricante que é feito.

## <a name="recommended-workflow"></a>Fluxo de trabalho recomendado

A abordagem mais bem-sucedida que encontrámos para itens publicados para a galeria do PowerShell é:

* Inicial desenvolvimento num site de um projeto de fonte aberta. A equipa de PowerShell utiliza Github.
* Utilize a comentários de revisores e [analisador de Script do Powershell](https://aka.ms/psscriptanalyzer) para obter o código de estado de estável
* Incluir documentação, para que outros utilizadores sabem como utilizar o seu trabalho
* Testar a ação de publicação utilizando um repositório local.
* Publicar uma versão estável ou alfa galeria do PowerShell, certificar-se de que inclui a documentação e a ligação ao seu local de projeto
* Recolher comentários e iterar sobre o código no seu site de projeto, em seguida, publicar atualizações estáveis galeria do PowerShell
* Adicionar exemplos e testes Pester no seu projeto e o módulo
* Decida se pretende código assinar o item
* Quando sentir o projeto está preparado para utilização num ambiente de produção, publicar um 1.0.0 versão para a galeria do PowerShell
* Continuar a recolher comentários e reanalisa o seu código com base na entrada de utilizador