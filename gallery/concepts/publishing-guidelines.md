---
ms.date: 06/12/2017
contributor: JKeithB, SydneyhSmith
keywords: Galeria, PowerShell, cmdlet, psgallery
description: Diretrizes para Publicadores
title: Diretrizes de publicação de Galeria do PowerShell e práticas recomendadas
ms.openlocfilehash: b470dbd81e79d2a6a228b8c89f85e57c03803ede
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986497"
---
# <a name="powershellgallery-publishing-guidelines-and-best-practices"></a>Diretrizes e práticas recomendadas de publicação do PowerShellGallery

Este tópico descreve as etapas recomendadas usadas pelas equipes da Microsoft para garantir que os pacotes publicados no Galeria do PowerShell sejam amplamente adotados e forneçam alto valor aos usuários, com base em como o Galeria do PowerShell lida com dados de manifesto e comentários de grandes números de Galeria do PowerShell usuários.
Os pacotes publicados seguindo essas diretrizes terão maior probabilidade de serem instalados, confiáveis e atrair mais usuários.

Veja abaixo as diretrizes para o que faz um bom pacote de Galeria do PowerShell, quais configurações opcionais de manifesto são mais importantes, melhorando seu código com os comentários dos revisores iniciais e do [PowerShell script Analyzer](https://aka.ms/psscriptanalyzer), versionando seu módulo, documentação, testes & exemplos de como usar o que você compartilhou.
Grande parte desta documentação segue as diretrizes para publicar [módulos de recursos de DSC de alta qualidade](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md).

Para obter a mecânica de publicação de um pacote no Galeria do PowerShell, consulte [criando e publicando um pacote](/powershell/gallery/how-to/publishing-packages/publishing-a-package).

Comentários sobre essas diretrizes são bem-vindos. Se você tiver comentários, abra problemas em nosso repositório de [documentação do GitHub](https://github.com/powershell/powershell-docs/issues).

## <a name="best-practices-for-publishing-packages"></a>Práticas recomendadas para publicação de pacotes

As seguintes práticas recomendadas são o que os usuários de Galeria do PowerShell itens dizem são importantes e estão listados em ordem de prioridade nominal.
Os pacotes que seguem essas diretrizes têm muito mais probabilidade de serem baixados e adotados por outras pessoas.

- Usar PSScriptAnalyzer
- Incluir documentação e exemplos
- Responder a comentários
- Fornecer módulos em vez de scripts
- Fornecer links para um site do projeto
- Marcar seu pacote com as PSEdition e plataformas compatíveis
- Incluir testes com seus módulos
- Incluir e/ou vincular aos termos de licença
- Assinar seu código
- Siga as diretrizes de [SemVer](http://semver.org/) para controle de versão
- Use marcas comuns, conforme documentado em marcas de Galeria do PowerShell comuns
- Testar a publicação usando um repositório local
- Usar o PowerShellGet para publicar

Cada um deles é abordado brevemente nas seções a seguir.

## <a name="use-psscriptanalyzer"></a>Usar PSScriptAnalyzer

[PSScriptAnalyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer) é uma ferramenta de análise de código estático gratuita que funciona no código do PowerShell.
O PSScriptAnalyzer identificará os problemas mais comuns vistos no código do PowerShell e, muitas vezes, uma recomendação de como corrigir o problema.
A ferramenta é fácil de usar e categoriza os problemas como erros (grave, deve ser resolvido), aviso (é necessário revisar & deve ser resolvido) e informações (vale a pena verificar as práticas recomendadas).
Todos os pacotes publicados no Galeria do PowerShell serão verificados usando PSScriptAnalyzer e todos os erros serão relatados para o proprietário e deverão ser resolvidos.

A prática recomendada é executar `Invoke-ScriptAnalyzer` com `-Recurse` e `-Severity` aviso.

Examine os resultados e verifique se:

- Todos os erros são corrigidos ou resolvidos em sua documentação
- Todos os avisos são revisados e tratados quando aplicável

Os usuários que adquirem pacotes da Galeria do PowerShell são altamente incentivados a executar PSScriptAnalyzer e avaliar todos os erros e avisos.
É muito provável que os usuários entrem em contato com os proprietários do pacote se perceberem que há um erro relatado pelo PSScriptAnalyzer.
Se houver um motivo convincente para o seu pacote manter o código sinalizado como um erro, adicione essas informações à sua documentação para evitar ter que responder à mesma pergunta muitas vezes.

## <a name="include-documentation-and-examples"></a>Incluir documentação e exemplos

A documentação e os exemplos são a melhor maneira de garantir que os usuários possam tirar proveito de qualquer código compartilhado.

A documentação é a coisa mais útil para incluir em pacotes publicados no Galeria do PowerShell.
Os usuários geralmente ignoram os pacotes sem documentação, pois a alternativa é ler o código para entender o que é o pacote e como usá-lo.
Há vários artigos disponíveis sobre como fornecer documentação com pacotes do PowerShell, incluindo:

- Diretrizes para fornecer ajuda sobre [como escrever ajuda de cmdlet](https://go.microsoft.com/fwlink/?LinkID=123415)
- Criando a ajuda do cmdlet, que é a melhor abordagem para qualquer script, função ou cmdlet do PowerShell.
  Para obter informações sobre como criar a ajuda do cmdlet, comece com [como escrever a ajuda do cmdlet](https://go.microsoft.com/fwlink/?LinkID=123415).
  Para adicionar ajuda em um script, consulte [a ajuda baseada em comentários](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).
- Muitos módulos também incluem documentação em formato de texto, como arquivos de redução.
  Isso pode ser particularmente útil quando há um site de projeto no GitHub, onde a redução é um formato muito usado.
  A prática recomendada é usar a [redução do tipo GitHub](https://help.github.com/categories/writing-on-github/)

Os exemplos mostram aos usuários como o pacote deve ser usado.
Muitos desenvolvedores dizem que eles analisam exemplos antes da documentação para entender como usar algo.
O melhor tipo de exemplos mostra o uso básico, além de um caso de uso realista simulado, e o código é bem comentado.
Exemplos de módulos publicados no Galeria do PowerShell devem estar em uma pasta de exemplos na raiz do módulo.

Um bom padrão para exemplos pode ser encontrado no [módulo PSDscResource](https://www.powershellgallery.com/packages/PSDscResources) na pasta Examples\RegistryResource.
Há quatro casos de uso de exemplo com uma breve descrição na parte superior de cada arquivo que documenta o que está sendo demonstrado.

## <a name="manage-dependencies"></a>Gerenciar dependências

É importante especificar os módulos dos quais seu módulo depende no manifesto do módulo.
Isso permite que o usuário final não precise se preocupar com a instalação das versões apropriadas dos módulos nos quais sua dependência se baseia.
Para especificar módulos dependentes, você deve usar o campo módulo necessário no manifesto do módulo.
Isso carregará todos os módulos listados no ambiente global antes de importar seu módulo, a menos que eles já tenham sido carregados. (Por exemplo, alguns módulos podem já estar carregados por um módulo diferente.).
Também é possível especificar uma versão específica para carregar usando o campo RequiredVersion em vez do campo ModuleVersion. Ao usar o ModuleVersion, ele carregará a versão mais recente disponível com, no mínimo, a versão especificada.
Quando não estiver usando o campo RequiredVersion para especificar uma versão específica, é importante monitorar as atualizações de versão para o módulo necessário.
É especialmente importante estar ciente de quaisquer alterações significativas que possam afetar a experiência do usuário com seu módulo.

```powershell
Example: RequiredModules = @(@{ModuleName="myDependentModule"; ModuleVersion="2.0"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})

Example: RequiredModules = @(@{ModuleName="myDependentModule"; RequiredVersion="1.5"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})
```

## <a name="respond-to-feedback"></a>Responder a comentários

Os proprietários do pacote que respondem corretamente aos comentários são altamente valorizados pela Comunidade.
Os usuários que fornecem comentários de construtivas são importantes para responder, pois eles estão interessados suficientes no pacote para tentar ajudá-lo a melhorá-lo.

Há dois métodos de comentários disponíveis no Galeria do PowerShell:

- Proprietário do contato: Isso permite que um usuário envie um email para os proprietários do pacote. Como proprietário do pacote, é importante monitorar o endereço de email usado com os pacotes de Galeria do PowerShell e responder a problemas que são gerados. A desvantagem desse método é que apenas o usuário e o proprietário verão a comunicação, de modo que o proprietário talvez tenha que responder à mesma pergunta muitas vezes.
- Feitos Na parte inferior da página pacote há um campo de comentário.
  A vantagem desse sistema é que outros usuários podem ver os comentários e as respostas, o que reduz o número de vezes que uma única pergunta deve ser respondida.
  Como proprietário do pacote, é altamente recomendável que você siga os comentários feitos para cada pacote.
Consulte [fornecendo comentários por meio de mídia social ou comentários](../how-to/working-with-packages/social-media-feedback.md) para obter detalhes sobre como fazer isso.

Os proprietários que respondem a crítica de comentários são apreciados pela Comunidade.
Use a oportunidade no relatório para solicitar mais informações, se necessário, fornecer uma solução alternativa ou identificar se uma atualização corrige um problema.

Se houver um comportamento inadequado observado de qualquer um desses canais de comunicação, use o recurso relatar abuso do Galeria do PowerShell para entrar em contato com os administradores da galeria.

## <a name="modules-versus-scripts"></a>Módulos versus scripts

Compartilhar um script com outros usuários é ótimo e fornece aos outros exemplos de como solucionar os problemas que eles podem ter.
O problema é que os scripts na Galeria do PowerShell são arquivos únicos sem documentação, exemplos e testes separados.

Os módulos do PowerShell têm uma estrutura de pastas que permite que várias pastas e arquivos sejam incluídos no pacote.
A estrutura do módulo permite incluir os outros pacotes que listamos como práticas recomendadas: ajuda do cmdlet, documentação, exemplos e testes.
A maior desvantagem é que um script dentro de um módulo deve ser exposto e usado como uma função.
Para obter informações sobre como criar um módulo, consulte [escrevendo um módulo do Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=144916).

Há situações em que um script fornece uma experiência melhor para o usuário, especialmente com configurações de DSC.
A prática recomendada para as configurações de DSC é publicar a configuração como um script com um módulo que o acompanha, que contém documentos, exemplos e testes.
O script lista o módulo que o acompanha usando RequiredModules = @ (nome do módulo).
Essa abordagem pode ser usada com qualquer script.

Os scripts autônomos que seguem as outras práticas recomendadas fornecem valor real para outros usuários.
O fornecimento de documentação baseada em comentários e um link para um site de projeto são altamente recomendados ao publicar um script no Galeria do PowerShell.

## <a name="provide-a-link-to-a-project-site"></a>Forneça um link para um site do projeto

Um site do projeto é onde um Publicador pode interagir diretamente com os usuários de seus pacotes de Galeria do PowerShell.
Os usuários preferem pacotes que fornecem isso, pois eles permitem obter informações sobre o pacote mais facilmente.
Muitos pacotes na Galeria do PowerShell são desenvolvidos no GitHub, outros são fornecidos por organizações com uma presença Web dedicada.
Cada um deles pode ser considerado um site do projeto.

A adição de um link é feita com a inclusão de ProjectURI na seção PSData do manifesto da seguinte maneira:

        # A URL to the main website for this project.
        ProjectUri = 'https://github.com/powershell/powershell'

Quando um ProjectURI é fornecido, o Galeria do PowerShell incluirá um link para o site do projeto no lado esquerdo da página do pacote.

## <a name="tag-your-package-with-the-compatible-pseditions-and-platforms"></a>Marcar seu pacote com as PSEdition e plataformas compatíveis

Use as seguintes marcas para demonstrar aos usuários quais pacotes funcionarão bem com seu ambiente:

- PSEdition_Desktop : Pacotes que são compatíveis com o Windows PowerShell
- PSEdition_Core : Pacotes que são compatíveis com o PowerShell Core
- Windows Pacotes que são compatíveis com o sistema operacional Windows
- Linux Pacotes compatíveis com sistemas operacionais Linux
- MacOS Pacotes que são compatíveis com o sistema operacional Mac

Ao marcar seu pacote com as plataformas compatíveis, ele será incluído nos filtros de pesquisa da galeria no painel esquerdo dos resultados da pesquisa. Se você hospedar seu pacote no GitHub, ao marcar seu pacote, você também poderá tirar proveito de nossa proteção](https://img.shields.io/powershellgallery/p/CosmosDB.svg)de![compatibilidade de [Galeria do PowerShell de proteção](https://img.shields.io/powershellgallery/p/:packageName.svg) 
de conformidade.  

## <a name="include-tests"></a>Incluir testes

Incluir testes com código de software livre é importante para os usuários, pois ele fornece garantia sobre o que você valida e fornece informações sobre como o seu código funciona. Ele também permite aos usuários garantir que eles não quebrem sua funcionalidade original se modificarem seu código para se ajustarem ao seu ambiente.

É altamente recomendável que os testes sejam escritos para tirar proveito da estrutura de teste do Pester, que foi projetada especificamente para o PowerShell.
O Pester está disponível no [GitHub](https://github.com/Pester/Pester), o [Galeria do PowerShell](https://www.powershellgallery.com/packages/Pester/)e é fornecido no Windows 10, no Windows Server 2016, no WMF 5,0 e no WMF 5,1.

O [site do projeto Pester no GitHub](https://github.com/Pester/Pester) inclui uma boa documentação sobre como escrever testes Pester, desde a introdução até as práticas recomendadas.

Os destinos para cobertura de teste são chamados na [documentação do módulo de recursos de alta qualidade](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md), com 70% de cobertura de código de teste de unidade recomendado.

## <a name="include-andor-link-to-license-terms"></a>Incluir e/ou vincular aos termos de licença

Todos os pacotes publicados no Galeria do PowerShell devem especificar os termos de licença ou ser associados à licença incluída nos [termos de uso](https://www.powershellgallery.com/policies/Terms) em "anexo A".
A melhor abordagem para especificar uma licença diferente é fornecer um link para a licença usando o LicenseURI em PSData.
Você pode encontrar um exemplo no tópico campos de manifesto recomendados.

```powershell
PrivateData = @{
    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        Tags = @('.net','acl','active-directory')

        # A URL to the license for this module.
        LicenseUri = 'http://www.apache.org/licenses/LICENSE-2.0'
```

## <a name="sign-your-code"></a>Assinar seu código

A assinatura de código fornece aos usuários o nível mais alto de garantia para quem publicou o pacote e que a cópia do código adquirido é exatamente o que o Publicador liberou.
Para saber mais sobre a assinatura de código em geral, consulte [introdução à assinatura de código](http://go.microsoft.com/fwlink/?LinkId=106296).
O PowerShell dá suporte à validação da assinatura de código por meio de duas abordagens principais:

- Assinando arquivos de script
- Assinatura de catálogo de um módulo

A assinatura de arquivos do PowerShell é uma abordagem bem estabelecida para garantir que o código que está sendo executado foi produzido por uma fonte confiável e não foi modificado.
Detalhes sobre como assinar arquivos de script do PowerShell são abordados no tópico [sobre assinatura](/powershell/module/microsoft.powershell.core/about/about_signing) .
Em visão geral, uma assinatura pode ser adicionada a qualquer. Arquivo PS1 que o PowerShell valida quando o script é carregado.
O PowerShell pode ser restrito usando os cmdlets de [política de execução](/powershell/module/microsoft.powershell.core/about/about_execution_policies) para garantir o uso de scripts assinados.

Os módulos de assinatura de catálogo são um recurso adicionado ao PowerShell na versão 5,1.
Como assinar um módulo é abordado no tópico [cmdlets de catálogo](/powershell/wmf/5.1/catalog-cmdlets) .
Em visão geral, a assinatura de catálogo é feita criando um arquivo de catálogo, que contém um valor de hash para cada arquivo no módulo e, em seguida, assinando esse arquivo.
Os cmdlets Publish-Module, install-Module, Save-Module e Update-Module do PowerShellGet verificarão a assinatura para garantir que ela seja válida e, em seguida, confirmar que o valor de hash de cada pacote corresponde ao que está no catálogo.
Se uma versão anterior do módulo estiver instalada no sistema, o Install-Module confirmará que a autoridade de assinatura da nova versão corresponde ao que foi instalado anteriormente.
A assinatura do catálogo funciona com o, mas não substitui os arquivos de script de assinatura. O PowerShell não valida assinaturas de catálogo no tempo de carregamento do módulo.

## <a name="follow-semver-guidelines-for-versioning"></a>Siga as diretrizes de SemVer para controle de versão

[SemVer](http://semver.org/) é uma convenção pública que descreve como estruturar e alterar uma versão para permitir uma fácil interpretação das alterações.
A versão do pacote deve ser incluída nos dados do manifesto.

- A versão deve ser estruturada como três blocos numéricos separados por pontos, como em 0.1.1 ou 4.11.192
- As versões que começam com "0" indicam que o pacote ainda não está pronto para produção e o primeiro número deve começar com "0" se esse for o único número usado
- Alterações no primeiro número (1.9.9999 para 2.0.0) indicam alterações principais e significativas entre as versões
- Alterações no segundo número (1,1 a 1,2) indicam alterações no nível do recurso, como adicionar novos cmdlets a um módulo
- As alterações no terceiro número indicam alterações não significativas, como novos parâmetros, amostras atualizadas ou novos testes
- Ao listar versões, o PowerShell classificará as versões como cadeias de caracteres; portanto, 1.01.0 será tratado como maior que 1.001.0

O PowerShell foi criado antes de o SemVer ter sido publicado, portanto, ele fornece suporte para a maioria dos elementos do SemVer, especificamente:

- Ele não oferece suporte a cadeias de caracteres de pré-lançamento em números de versão. Isso é útil quando um editor deseja fornecer uma versão de visualização de uma nova versão principal depois de fornecer uma versão 1.0.0. Isso terá suporte em uma versão futura dos cmdlets Galeria do PowerShell e PowerShellGet.
- O PowerShell e o Galeria do PowerShell permitem cadeias de caracteres de versão com 1, 2 e 4 segmentos. Muitos módulos iniciais não seguiram as diretrizes e as versões do produto da Microsoft incluem informações de compilação como um 4º bloco de números (por exemplo, 5.1.14393.1066). Do ponto de vista do controle de versão, essas diferenças são ignoradas.

## <a name="test-using-a-local-repository"></a>Testar usando um repositório local

O Galeria do PowerShell não foi projetado para ser um destino para testar o processo de publicação.
A melhor maneira de testar o processo de ponta a ponta de publicação no Galeria do PowerShell é configurar e usar seu próprio repositório local.
Isso pode ser feito de algumas maneiras, incluindo:

- Configure uma instância de Galeria do PowerShell local usando o [projeto da galeria privada do PS](https://github.com/PowerShell/PSPrivateGallery) no github. Este projeto de visualização ajudará você a configurar uma instância do Galeria do PowerShell que você pode controlar e usar para seus testes.
- Configure um [repositório do NuGet interno](https://blogs.msdn.microsoft.com/powershell/2014/05/20/setting-up-an-internal-powershellget-repository/). Isso exigirá mais trabalho a ser configurado, mas terá a vantagem de validar alguns dos requisitos, particularmente a validação do uso de uma chave de API e se as dependências estão presentes ou não no destino quando você publica.
- Configure um compartilhamento de arquivos como o "repositório" de teste. Isso é fácil de configurar, mas como é um compartilhamento de arquivos, as validações indicadas acima não ocorrerão. Uma vantagem potencial nesse caso é que o compartilhamento de arquivos não verifica a chave de API (necessária), para que você possa usar a mesma chave que você deseja publicar na Galeria do PowerShell.

Com qualquer uma dessas soluções, use Register-PSRepository para definir um novo "Repository", que você usa na propriedade-Repository para publish-Module.

Um ponto adicional sobre a publicação de teste: qualquer pacote que você publicar na Galeria do PowerShell não poderá ser excluído sem ajuda da equipe de operações, que confirmará que nada depende do pacote que você deseja publicar.
Por esse motivo, não damos suporte à Galeria do PowerShell como um destino de teste e entraremos em contato com qualquer editor que faça isso.

## <a name="use-powershellget-to-publish"></a>Usar o PowerShellGet para publicar

É altamente recomendável que os editores usem os cmdlets Public-Module e Publish-script ao trabalhar com o Galeria do PowerShell.
O PowerShellGet foi criado para ajudá-lo a evitar a memorização de detalhes importantes sobre a instalação e a publicação no Galeria do PowerShell.
Na ocasião, os editores optaram por ignorar o PowerShellGet e usar os cmdlets cliente NuGet, ou PackageManagement, em vez de Publish-Module.
Há vários detalhes que são facilmente perdidos, o que resulta em uma variedade de solicitações de suporte.

Se houver um motivo pelo qual você não pode usar Publish-module ou Publish-script, informe-nos.
Execute um problema no repositório GitHub do PowerShellGet e forneça os detalhes que fazem com que você escolha NuGet ou PackageManagement.

## <a name="recommended-workflow"></a>Fluxo de trabalho recomendado

A abordagem mais bem-sucedida encontrada para os pacotes publicados no Galeria do PowerShell é a seguinte:

- Faça o desenvolvimento inicial em um site de projeto de código-fonte aberto. A equipe do PowerShell usa o github.
- Use comentários dos revisores e do [PowerShell script Analyzer](https://aka.ms/psscriptanalyzer) para obter o código para o estado estável
- Incluir documentação, para que outras pessoas saibam como usar seu trabalho
- Teste a ação de publicação usando um repositório local.
- Publicar uma versão estável ou alfa para o Galeria do PowerShell, conferindo-se a incluir a documentação e o link para o site do projeto
- Reúna comentários e itere no código do site do projeto e publique atualizações estáveis no Galeria do PowerShell
- Adicionar exemplos e testes de Pester em seu projeto e seu módulo
- Decida se deseja assinar o código do seu pacote
- Quando você sentir que o projeto está pronto para uso em um ambiente de produção, publique uma versão 1.0.0 no Galeria do PowerShell
- Continue a coletar comentários e iterar em seu código com base na entrada do usuário
