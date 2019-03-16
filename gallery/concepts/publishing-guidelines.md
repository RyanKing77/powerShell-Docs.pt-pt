---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galeria, o powershell, o cmdlet, o psgallery
description: Diretrizes para editores
title: Galeria do PowerShell orientações e melhores práticas de publicação
ms.openlocfilehash: 25c359c7acbe7430762a275d8cc4a28f527ec57a
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056503"
---
# <a name="powershellgallery-publishing-guidelines-and-best-practices"></a>PowerShellGallery orientações e melhores práticas de publicação

Este tópico descreve os passos recomendados usados pelas equipes da Microsoft para garantir que os pacotes publicados na galeria do PowerShell irão ser amplamente adotados e fornecem valor elevado aos utilizadores, com base na forma como o da galeria do PowerShell processa dados manifestos e nos comentários dos grandes números de utilizadores da galeria do PowerShell.
Pacotes que são publicados a seguir essas diretrizes serão mais probabilidade de ser instalado, confiável e atrair mais usuários.

Incluída abaixo são diretrizes para o que faz um bom pacote de galeria do PowerShell, quais configurações de manifestos opcionais são mais importantes, melhorar o seu código com comentários dos revisores iniciais e [analisador de Script do Powershell](https://aka.ms/psscriptanalyzer), controlo de versões do seu módulo, documentação, testes e exemplos para saber como utilizar o que tenha partilhado.
Grande parte desta documentação segue as diretrizes de publicação [módulos de recursos de DSC de qualidade elevada](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md).

Para o mecanismo de publicação de um pacote da galeria do PowerShell, consulte [criar e publicar um pacote](/powershell/gallery/how-to/publishing-packages/publishing-a-package).

Comentários sobre essas diretrizes é welcomed. Se tiver comentários, abra questões no nosso [repositório de documentação do Github](https://github.com/powershell/powershell-docs/issues).

## <a name="best-practices-for-publishing-packages"></a>Melhores práticas para a publicação de pacotes

As seguintes melhores práticas são o que dizer que os utilizadores de itens de galeria do PowerShell é importante e estão listadas por ordem de prioridade nominal.
Os pacotes que siga estas diretrizes são muito mais probabilidade de ser transferidos e adotado por outras pessoas.

- Utilizar PSScriptAnalyzer
- Incluir a documentação e exemplos
- Ser reativos para com comentários
- Fornecer módulos em vez de scripts
- Fornecem ligações para um site de projeto
- Marcar seu pacote com as plataformas e PSEdition(s) compatível
- Incluir testes com seus módulos
- Incluir e/ou ligar a termos de licenciamento
- Inicie o seu código
- Siga [SemVer](http://semver.org/) diretrizes para controlo de versões
- Utilizar etiquetas comuns, conforme documentado no etiquetas da galeria do PowerShell comum
- Testar a publicação utilizar um repositório local
- Utilizar o PowerShellGet para publicar

Cada um deles está abrangida resumidamente nas secções abaixo.

## <a name="use-psscriptanalyzer"></a>Utilizar PSScriptAnalyzer

[PSScriptAnalyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer) é uma ferramenta de análise de código estático gratuito que funciona no código do PowerShell.
PSScriptAnalyzer irá identificar os problemas mais comuns vistos no código do PowerShell e, muitas vezes, uma recomendação para saber como corrigir o problema.
A ferramenta é fácil de usar e categoriza os problemas como erros (graves, devem ser resolvidos), aviso (precisam ser examinadas e deve ser resolvido) e as informações (que vale a pena dar uma olhada para práticas recomendadas).
Publicado na galeria do PowerShell de todos os pacotes serão analisados usando PSScriptAnalyzer e todos os erros serão comunicados volta para o proprietário e devem ser resolvidos.

A prática recomendada é executar `Invoke-ScriptAnalyzer` com `-Recurse` e `-Severity` aviso.

Reveja os resultados e certifique-se de que:

- Todos os erros são corrigidos ou resolvidos na documentação do
- Todos os avisos são revistos e tratados quando se aplica

Os utilizadores que adquirir pacotes a partir da galeria do PowerShell são fortemente encorajados a executar PSScriptAnalyzer e avaliar todos os erros e avisos.
Os utilizadores são muito provável que entre em contato com os proprietários de pacote se Verão que existe um erro comunicado pelo PSScriptAnalyzer.
Se houver um motivo convincente para seu pacote manter o código que é sinalizado como um erro, adicione essas informações para a documentação para evitar ter de responder a muitas vezes a mesma pergunta.

## <a name="include-documentation-and-examples"></a>Incluir a documentação e exemplos

Documentação e exemplos são a melhor forma de garantir que os utilizadores podem tirar partido de qualquer código compartilhado.

Documentação é a coisa mais úteis para incluir em pacotes publicados na galeria do PowerShell.
Os usuários geralmente irão ignorar pacotes sem a documentação, como a alternativa é ler o código para compreender o que é o pacote e como usá-lo.
Há vários artigos disponíveis sobre como fornecer documentação com os pacotes do PowerShell, incluindo:

- Diretrizes para o fornecimento de ajuda estão em [como escrever ajuda do Cmdlet](https://go.microsoft.com/fwlink/?LinkID=123415)
- A criação de ajuda do cmdlet, que é a melhor abordagem para qualquer script do PowerShell, a função ou o cmdlet.
  Para obter informações sobre como criar a ajuda do cmdlet, começar com [como escrever ajuda do Cmdlet](https://go.microsoft.com/fwlink/?LinkID=123415).
  Para adicionar o ajuda num script, consulte [sobre o comentário com base em ajudar](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).
- Muitos módulos também incluem a documentação do formato de texto, como ficheiros MarkDown.
  Isso pode ser particularmente útil quando existe um site de projeto no Github, onde o Markdown é um formato muito utilizado.
  A prática recomendada é usar [Markdown característico do Github](https://help.github.com/categories/writing-on-github/)

Exemplos mostram aos utilizadores como o pacote deve ser usado.
Muitos desenvolvedores dirá que elas ver exemplos antes de documentação para compreender como usar algo.
O melhor tipo de exemplos mostram a utilização básica, mais um caso de uso realista simulado e o código é bem comentado.
Exemplos de módulos publicados na galeria do PowerShell devem estar numa pasta de exemplos sob a raiz do módulo.

Um bom padrão para obter exemplos pode ser encontrado no [PSDscResource módulo](https://www.powershellgallery.com/packages/PSDscResources) sob a pasta de Examples\RegistryResource.
Existem quatro casos de utilização de exemplo com uma breve descrição na parte superior de cada arquivo que documenta o que está a ser demonstrado.

## <a name="respond-to-feedback"></a>Responder a comentários

Proprietários de pacote que respondem corretamente a comentários altamente são valiosos para a Comunidade.
Os utilizadores que fornecem comentários construtivos são importantes para responder a, à medida que está interessado no pacote de forma a ajudar melhorá-la.

Existem dois métodos de comentários disponíveis na galeria do PowerShell:

- Contacte o proprietário: Isso permite que um usuário envia um e-mail para proprietários que o pacote se. Como proprietário de um pacote, é importante monitorizar o endereço de e-mail utilizado com os pacotes de galeria do PowerShell e responder a problemas que são gerados. Uma desvantagem desse método é que apenas o utilizador e o proprietário nunca Verão a comunicação, para que o proprietário poderá ter de responder a muitas vezes a mesma pergunta.
- Comentários: Na parte inferior do pacote de página é um campo de comentário.
  A vantagem para este sistema é que outros utilizadores possam ver os comentários e respostas, que reduz o número de vezes que qualquer pergunta têm de ser respondida.
  Como proprietário de um pacote, recomenda-se vivamente que siga os comentários feitos para cada pacote.
Ver [fornecer Feedback através de redes sociais ou dos comentários](../how-to/working-with-packages/social-media-feedback.md) para obter detalhes sobre como fazer isso.

Proprietários que respondem a comentários de crítica são bem-vindos pela Comunidade.
Usar a oportunidade no relatório para pedir mais informações, se necessário, forneça uma solução alternativa ou identificar se uma atualização corrige um problema.

Se houver comportamento inadequado observado em qualquer um desses canais de comunicação, utilize a funcionalidade de relatar abuso da galeria do PowerShell para contactar os administradores de galeria.

## <a name="modules-versus-scripts"></a>Módulos em comparação com Scripts

Um script de partilha com outros utilizadores é ótimo e fornece exemplos de como resolver problemas que podem ter a outras pessoas.
O problema é que os scripts na galeria do PowerShell são ficheiros únicos sem separado de documentação, exemplos e testes.

Módulos do PowerShell têm uma estrutura de pasta que permite que várias pastas e arquivos a serem incluídos no pacote.
A estrutura do módulo permite incluindo os outros pacotes listados melhor práticas: cmdlet ajuda, documentação, exemplos e testes.
A maior desvantagem é que um script dentro de um módulo tem de ser exposto e utilizado como uma função.
Para obter informações sobre como criar um módulo, consulte [escrever um módulo do Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=144916).

Existem situações em que um script fornece uma melhor experiência para o usuário, particularmente com configurações de DSC.
É a melhor prática para configurações de DSC publicar a configuração como um script com um módulo que acompanha este artigo, que contém os documentos, exemplos e testes.
O script lista o módulo que acompanha este artigo utilizar RequiredModules = @(nome do módulo).
Essa abordagem pode ser usada com qualquer script.

Scripts de autónomo que se seguem as outras práticas recomendadas fornecem valor real para outros utilizadores.
Fornecer documentação baseada no comentário e uma ligação para um Site de projeto são altamente recomendados ao publicar um script para a galeria do PowerShell.

## <a name="provide-a-link-to-a-project-site"></a>Forneça uma ligação para um site de projeto

Um Site de projeto é onde um publicador pode interagir diretamente com os usuários de seus pacotes de galeria do PowerShell.
Os usuários prefiram pacotes que fornecem isso, pois ele permite-los obter informações sobre o pacote mais facilmente.
Muitos pacotes na galeria do PowerShell são desenvolvidos no GitHub, outras são fornecidas por organizações com uma presença na web dedicado.
Cada um deles pode ser considerada um site de projeto.

Adicionar uma ligação é feita, incluindo ProjectURI na secção PSData do manifesto, da seguinte forma:

        # A URL to the main website for this project.
        ProjectUri = 'https://github.com/powershell/powershell'

Quando é fornecido um ProjectURI, a galeria do PowerShell incluirá uma ligação para o Site do projeto no lado esquerdo da página do pacote.

## <a name="tag-your-package-with-the-compatible-pseditions-and-platforms"></a>Marcar seu pacote com as plataformas e PSEdition(s) compatível

Utilize as seguintes etiquetas para demonstrar a utilizadores que pacotes funcionará bem com o seu ambiente:

- PSEdition_Desktop : Pacotes que são compatíveis com o Windows PowerShell
- PSEdition_Core: Pacotes que são compatíveis com o PowerShell Core
- Windows : Pacotes que são compatíveis com o sistema de operativo do Windows
- Linux : Pacotes que são compatíveis com sistemas de operativos do Linux
- MacOS : Pacotes que são compatíveis com o sistema de operativo do Mac

## <a name="include-tests"></a>Incluir testes

Incluindo testes com o código-fonte é importante para os utilizadores, como ele fornece assurance sobre o que valida e fornece informações sobre como funciona o seu código. Também permite que os utilizadores para garantir que eles não são interrompidas sua funcionalidade original se eles modificam seu código para se ajustar ao seu ambiente.

É altamente recomendável que os testes escritos para tirar partido da estrutura de teste Pester, que foi concebido especificamente para o PowerShell.
Pester está disponível no [GitHub](https://github.com/Pester/Pester), o [galeria do PowerShell](https://www.powershellgallery.com/packages/Pester/)e é fornecido no Windows 10, o Windows Server 2016, o WMF 5.0 e o WMF 5.1.

O [Pester o site de projeto no GitHub](https://github.com/Pester/Pester) inclui a boa documentação sobre como escrever testes de Pester, desde a introdução para as melhores práticas.

Os destinos para cobertura de teste são realçados [documentação do módulo de recursos de qualidade elevada](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md), com a unidade de 70% recomendada de cobertura de código de teste.

## <a name="include-andor-link-to-license-terms"></a>Incluir e/ou ligar a termos de licenciamento

Todos os pacotes publicados na galeria do PowerShell tem de especificar os termos de licenciamento ou estar vinculados pela licença incluída no [termos de utilização](https://www.powershellgallery.com/policies/Terms) em "Anexo A".
É a melhor abordagem para especificar uma licença diferente fornecer uma ligação para a licença com o LicenseURI no PSData.
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

Assinatura de código fornece aos usuários o mais alto nível de garantia de que publicou o pacote e que a cópia do código adquirido é exatamente o que o Editor liberados.
Para saber mais sobre geralmente de assinatura de código, consulte [introdução à assinatura de código](http://go.microsoft.com/fwlink/?LinkId=106296).
PowerShell oferece suporte a validação de assinatura por meio de duas abordagens primárias de código:

- Arquivos de script de assinatura
- Catálogo de um módulo de assinatura

A assinatura de ficheiros do PowerShell é uma abordagem bem estabelecida para garantir que o código a ser executado foi produzido por uma origem confiável e não foi modificado.
Detalhes sobre como assinar os arquivos de script do PowerShell é abordado o [sobre assinatura](/powershell/module/microsoft.powershell.core/about/about_signing) tópico.
Descrição geral, uma assinatura pode ser adicionada a qualquer. Arquivo PS1 que valida a PowerShell quando o script é carregado.
PowerShell pode ser limitado a utilizar o [política de execução](/powershell/module/microsoft.powershell.core/about/about_execution_policies) assinado de cmdlets para garantir o uso de scripts.

O catálogo de módulos de assinatura é uma funcionalidade adicionada ao PowerShell na versão 5.1.
Como assinar um módulo é abordado o [Cmdlets de catálogo](/powershell/wmf/5.1/catalog-cmdlets) tópico.
Na descrição geral, a assinatura do catálogo é feito ao criar um arquivo de catálogo, que contém um valor de hash para todos os ficheiros no módulo, e, em seguida, iniciar esse ficheiro.
A publicar-module PowerShellGet, install-module, save-module e cmdlets do módulo de atualização irá verificar a assinatura para garantir que é válido, em seguida, confirmar que o valor de hash para cada pacote corresponde ao que se encontra no catálogo.
Se está instalada uma versão anterior do módulo do sistema, install-module confirma que a autoridade de assinatura para a nova versão corresponde ao que foi anteriormente instalado.
Catálogo de assinatura funciona com, mas não substitui os ficheiros de script de assinatura. PowerShell não valida as assinaturas de catálogo no tempo de carregamento de módulo.

## <a name="follow-semver-guidelines-for-versioning"></a>Siga as diretrizes de SemVer para controlo de versões

[SemVer](http://semver.org/) é uma convenção de pública que descreve como estruturar e alterar uma versão para permitir uma interpretação fácil de alterações.
A versão para o seu pacote deve ser incluída nos dados de manifestos.

- A versão deve ser estruturada como 3 blocos numérico separados por pontos, como no 0.1.1 ou 4.11.192
- Versões que iniciam com "0" indicam que o pacote ainda não está pronto para produção e o primeiro número só deve começar com "0", se esse for o número único utilizado
- As alterações no primeiro número (1.9.9999 a 2.0.0) indicam alterações principais e de última hora entre as versões
- Alterações ao nível da funcionalidade, por exemplo, adicionar novos cmdlets para um módulo de indicar as alterações para o segundo número (1.1 para 1.2)
- As alterações para o número de terceiro indicam alterações sem interrupções, como novos parâmetros, exemplos atualizados ou novos testes
- Quando lista as versões, PowerShell para ordenar as versões como cadeias de caracteres, para que 1.01.0 serão tratados como superior a 1.001.0

PowerShell foi criado antes de SemVer foi publicada, pelo que oferece suporte para a maioria dos mas nem todos os elementos de SemVer, especificamente:

- Não suporta pré-lançamento cadeias de caracteres em números de versão. Isto é útil quando um publicador deseja fornecer uma versão de pré-visualização de uma versão principal nova depois de fornecer uma versão 1.0.0. Isso será suportado numa versão futura do cmdlets de galeria do PowerShell e o PowerShellGet.
- PowerShell e da galeria do PowerShell permitem que as cadeias de caracteres de versão com 1, 2 e 4 segmentos. Muitos módulos antecipados não seguia as diretrizes e as versões de produtos da Microsoft incluem informações de compilação como um 4th bloquear de números (por exemplo 5.1.14393.1066). Do ponto de vista do controle de versão, essas diferenças são ignoradas.

## <a name="test-using-a-local-repository"></a>Testar a utilização de um repositório local

A galeria do PowerShell não foi concebida para ser um destino para testar o processo de publicação.
É a melhor forma de testar o processo de ponto-a-ponto de publicação na galeria do PowerShell configurar e utilizar o seu próprio repositório local.
Isso pode ser feito de diversas formas, incluindo:

- Configurar uma instância local da galeria do PowerShell, utilizando o [projeto de galeria privada de PS](https://github.com/PowerShell/PSPrivateGallery) no Github. Este projeto de pré-visualização irá ajudá-lo a configurar uma instância da galeria do PowerShell que pode controlar e utilização para seus testes.
- Configurar uma [repositório interno do Nuget](https://blogs.msdn.microsoft.com/powershell/2014/05/20/setting-up-an-internal-powershellget-repository/). Isso exigirá mais trabalho para configurar, mas terá a vantagem de validação de mais alguns dos requisitos, notavelmente a validar a utilização de uma chave de API e se deve ou não as dependências estão presentes no destino quando publica.
- Configure uma partilha de ficheiros como o teste de "repositório". Isso é fácil de configurar, mas uma vez que é uma partilha de ficheiros, as validações indicadas acima não ocorrerá. Nesse caso, a principal vantagem é que a partilha de ficheiros não verifica se a chave de API (obrigatória), pelo que pode utilizar a mesma chave que faria para publicar a galeria do PowerShell.

Com qualquer uma destas soluções, use Register-PSRepository para definir um novo "repositório de", que são utilizados na propriedade - repositório para Publish-Module.

Um ponto adicional sobre a publicação de teste: não é possível eliminar a qualquer pacote publicar na galeria do PowerShell sem a ajuda de que a equipe de operações, que confirma que nada é dependente do pacote que pretende publicar.
Por esse motivo, nós não suportam a galeria do PowerShell como um destino de teste e entrará em contacto qualquer fabricante que faz isso.

## <a name="use-powershellget-to-publish"></a>Utilizar o PowerShellGet para publicar

É altamente recomendável que os publicadores utilizam os cmdlets Publish-Module e Publish-Script, ao trabalhar com a galeria do PowerShell.
O PowerShellGet foi criado para ajudar a evitar a lembrar-se detalhes importantes sobre a instalação do e publicação na galeria do PowerShell.
Ocasionalmente, os publicadores optar por ignorar o PowerShellGet e utilizar o cliente NuGet ou os PackageManagement cmdlets, em vez de Publish-Module.
Há um número de detalhes que são facilmente perdida, o que resulta numa variedade de pedidos de suporte.

Se houver um motivo que não é possível utilizar Publish-Module ou Publish-Script, contacte-nos informar.
Enviar um problema no repositório GitHub do PowerShellGet e forneça os detalhes que fazem com que escolha o NuGet ou PackageManagement.

## <a name="recommended-workflow"></a>Fluxo de trabalho recomendado

A abordagem mais bem-sucedidas que encontramos para pacotes publicados na galeria do PowerShell é o seguinte:

- A inicial de desenvolvimento num site de um projeto de código aberto. A equipe de PowerShell usa o Github.
- Utilize os comentários dos revisores e [analisador de Script do Powershell](https://aka.ms/psscriptanalyzer) para obter o código de estado estável
- Inclui documentação, para que outras pessoas saibam como utilizar o seu trabalho
- Testar a ação de publicação com um repositório local.
- Publicar uma versão estável ou alfa da galeria do PowerShell, certificar-se de que inclui a documentação e a ligação para o site do projeto
- Recolher comentários e iterar sobre o código no site do projeto, em seguida, publicar atualizações estáveis da galeria do PowerShell
- Adicione exemplos e os testes de Pester no seu projeto e seu módulo
- Decida se pretende código assinar seu pacote
- Quando considerar que o projeto está pronto para usar num ambiente de produção, publicar um 1.0.0 versão na galeria do PowerShell
- Continuar a recolher comentários e reanalisa o seu código com base na entrada do usuário
