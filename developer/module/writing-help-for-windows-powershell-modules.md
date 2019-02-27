---
title: Escrever ajuda para módulos do Windows PowerShell | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b58fa5-01bc-426c-a043-5c700d6578e9
caps.latest.revision: 16
ms.openlocfilehash: 443bf5f693d2ab161668de25a1097347826cb5c2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845459"
---
# <a name="writing-help-for-windows-powershell-modules"></a>Writing Help for Windows PowerShell Modules (Escrever Ajuda para Módulos do Windows PowerShell)

Módulos do Windows PowerShell podem incluir os tópicos de ajuda sobre o módulo e sobre os membros de módulo, como cmdlets, provedores, funções e scripts. O `Get-Help` cmdlet apresenta os tópicos de ajuda do módulo no mesmo formato, à medida que este apresenta a ajuda para outros itens do Windows PowerShell, e os utilizadores utilizam a norma `Get-Help` comandos para obter os tópicos de ajuda.

Este documento explica o formato e a colocação correta dos tópicos de ajuda do módulo e sugere diretrizes para conteúdo de ajuda do módulo.

## <a name="types-of-module-help"></a>Tipos de ajuda do módulo

Um módulo pode incluir os seguintes tipos de ajuda.

- **Ajuda do cmdlet**. Os tópicos de ajuda que descrevem cmdlets num módulo são arquivos XML que utilizam o comando ajudam esquema

- **Ajuda do provedor**. Os tópicos de ajuda que descrevem os provedores num módulo são arquivos XML que utilizam o fornecedor de ajudam o esquema.

- **Função ajuda**. Os tópicos de ajuda que descrevem as funções num módulo pode ser arquivos XML que utilizam o comando ajudam o esquema ou baseada no comentário tópicos de ajuda dentro da função, ou o script ou o módulo de script

- **Ajuda do script**. Os tópicos de ajuda que descrevem os scripts num módulo pode ser arquivos XML que utilizam o comando ajudam o esquema ou baseada no comentário tópicos de ajuda no script ou o módulo de script.

- **Conceitual ("sobre") ajuda**. Pode utilizar um conceitual ("sobre") tópico de ajuda para descrever o módulo e seus membros e explicar como os membros podem ser utilizados em conjunto para realizar tarefas. Tópicos de ajuda conceituais são ficheiros de texto com codificação Unicode (UTF-8). O nome do ficheiro tem de utilizar o `about_<name>.help.txt` formato, como about_MyModule.help.txt. Por predefinição, o Windows PowerShell inclui mais de 100 destes tópicos sobre ajudar conceitual, e são formatados semelhante ao seguinte exemplo.

  ```
  TOPIC
      about_<subject or module name>

  SHORT DESCRIPTION
      A short, one-line description of the topic contents.

  LONG DESCRIPTION
      A detailed, full description of the subject or purpose of the module.

  EXAMPLES
      Examples of how to use the module or how the subject feature works in practice.

  KEYWORDS
      Terms or titles on which you might expect your users to search for the information in this topic.

  SEE ALSO
      Text-only references for further reading. Hyperlinks cannot work in the Windows PowerShell console.

  ```

## <a name="placement-of-module-help"></a>Colocação de ajuda do módulo

O `Get-Help` cmdlet procura por ficheiros de tópico de ajuda do módulo em subdiretórios específicos de idiomas do diretório de módulo.

Por exemplo, o diagrama de estrutura de diretório seguinte mostra a localização dos tópicos de ajuda para o módulo de SampleModule.

```
<ModulePath>
         \SampleModule
               \<en-US>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml
               \<fr-FR>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml

```

> [!NOTE]
> No exemplo, o  *\<ModulePath >* marcador de posição representa um dos caminhos no `PSModulePath` variável de ambiente, como $home\Documents\Modules, $pshome\Modules ou um caminho personalizado que o utilizador Especifica.

## <a name="getting-module-help"></a>Obter ajuda do módulo

Quando um utilizador importa um módulo para uma sessão, os tópicos de ajuda para aquele módulo são importados para a sessão, juntamente com o módulo. Pode listar os ficheiros de tópico de ajuda no valor da chave de lista de ficheiros no manifesto do módulo, mas tópicos de ajuda não são afetadas pelo `Export-ModuleMember` cmdlet.

Pode fornecer tópicos de ajuda do módulo em idiomas diferentes. O `Get-Help` cmdlet apresenta automaticamente tópicos de ajuda do módulo no idioma que é especificado para o utilizador atual no idioma opções regionais e de item no painel de controlo. No Windows Vista e versões posteriores do Windows, `Get-Help` procura os tópicos de ajuda em subdiretórios específicos de idiomas do diretório de módulo em conformidade com as normas de contingência de idioma estabelecido para Windows.

A partir do Windows PowerShell 3.0, executar um `Get-Help` comando para um cmdlet ou uma função aciona a importação automática do módulo. O `Get-Help` cmdlet apresenta imediatamente os conteúdos dos tópicos de ajuda no módulo.

Se o módulo não contém tópicos de ajuda e não há nenhum tópicos de ajuda para os comandos no módulo no computador do usuário, `Get-Help` apresenta ajuda gerado automaticamente. A ajuda de gerado automaticamente inclui a sintaxe de comando, parâmetros e tipos de entrada e saídos, mas não inclui quaisquer descrições. A ajuda de gerado automaticamente inclui o texto que direciona o utilizador tentar utilizar o `Update-Help` cmdlet para transferir a ajuda para o comando a partir da Internet ou uma partilha de ficheiros. Ele também recomenda utilizar o **Online** parâmetro do `Get-Help` cmdlet para obter a versão online do tópico de ajuda.

## <a name="supporting-updatable-help"></a>Apoio Ajuda Atualizável

Os utilizadores do Windows PowerShell 3.0 e versões posteriores do Windows PowerShell, podem transferir e instalar ficheiros de ajuda atualizada para um módulo da Internet ou a partir de uma partilha de ficheiros local. O `Update-Help` e `Save-Help` cmdlets ocultar os detalhes de gerenciamento do usuário. Os usuários executem o `Update-Help` cmdlet e, em seguida, utilizar o `Get-Help` cmdlet para ler os ficheiros de ajuda mais recentes para o módulo de linha de comandos do Windows PowerShell. Os utilizadores não é necessário reiniciar o Windows ou Windows PowerShell.

Os utilizadores atrás de firewalls e pessoas sem acesso à Internet podem utilizar a ajuda Atualizável, também. Os administradores com Internet aceder a utilizar o `Save-Help` cmdlet para transferir e instalar os ficheiros de ajuda mais recentes para uma partilha de ficheiros. Em seguida, os utilizadores utilizam o **caminho** parâmetro do `Update-Help` cmdlet para obter os ficheiros de ajuda mais recentes da partilha de ficheiros.

Os autores de módulo podem incluir arquivos de ajuda no módulo e utilizar a ajuda Atualizável de mensagens em fila para atualizar os arquivos de ajuda ou omitir os arquivos de ajuda do módulo e utilizar a ajuda Atualizável para instalar e atualizá-los.

Para obter mais informações sobre Ajuda Atualizável, consulte [apoio ajuda Atualizável](./supporting-updatable-help.md).

## <a name="supporting-online-help"></a>Apoio Ajuda Online

Os utilizadores que não podem ou não instalar atualizados ajuda arquivos em seus computadores frequentemente contam com a versão online dos tópicos de ajuda do módulo. O **Online** parâmetro do `Get-Help` cmdlet abre a versão online de um cmdlet ou uma função avançada de tópico de ajuda para o utilizador no seu browser predefinido.

O `Get-Help` cmdlet utiliza o valor da **HelpUri** propriedade do cmdlet ou função para localizar a versão online do tópico de ajuda.

A partir do Windows PowerShell 3.0, pode ajudar os utilizadores a encontrar a versão online dos tópicos de ajuda do cmdlet e função definindo o atributo HelpUri na classe cmdlet ou o **HelpUri** propriedade do **CmdletBinding** atributo. O valor do atributo é o valor do **HelpUri** propriedade da função ou cmdlet.

Para obter mais informações, consulte [apoio Ajuda Online](./supporting-online-help.md).

## <a name="see-also"></a>Veja Também

[Escrever um módulo do Windows PowerShell](./writing-a-windows-powershell-module.md)

[Apoio ajuda Atualizável](./supporting-updatable-help.md)

[Apoio Ajuda Online](./supporting-online-help.md)