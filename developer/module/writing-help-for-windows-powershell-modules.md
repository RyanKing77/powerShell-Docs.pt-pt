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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082041"
---
# <a name="writing-help-for-windows-powershell-modules"></a><span data-ttu-id="91ae4-102">Writing Help for Windows PowerShell Modules (Escrever Ajuda para Módulos do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="91ae4-102">Writing Help for Windows PowerShell Modules</span></span>

<span data-ttu-id="91ae4-103">Módulos do Windows PowerShell podem incluir os tópicos de ajuda sobre o módulo e sobre os membros de módulo, como cmdlets, provedores, funções e scripts.</span><span class="sxs-lookup"><span data-stu-id="91ae4-103">Windows PowerShell modules can include Help topics about the module and about the module members, such as cmdlets, providers, functions and scripts.</span></span> <span data-ttu-id="91ae4-104">O `Get-Help` cmdlet apresenta os tópicos de ajuda do módulo no mesmo formato, à medida que este apresenta a ajuda para outros itens do Windows PowerShell, e os utilizadores utilizam a norma `Get-Help` comandos para obter os tópicos de ajuda.</span><span class="sxs-lookup"><span data-stu-id="91ae4-104">The `Get-Help` cmdlet displays the module Help topics in the same format as it displays Help for other Windows PowerShell items, and users use standard `Get-Help` commands to get the Help topics.</span></span>

<span data-ttu-id="91ae4-105">Este documento explica o formato e a colocação correta dos tópicos de ajuda do módulo e sugere diretrizes para conteúdo de ajuda do módulo.</span><span class="sxs-lookup"><span data-stu-id="91ae4-105">This document explains the format and correct placement of module Help topics, and it suggests guidelines for module Help content.</span></span>

## <a name="types-of-module-help"></a><span data-ttu-id="91ae4-106">Tipos de ajuda do módulo</span><span class="sxs-lookup"><span data-stu-id="91ae4-106">Types of Module Help</span></span>

<span data-ttu-id="91ae4-107">Um módulo pode incluir os seguintes tipos de ajuda.</span><span class="sxs-lookup"><span data-stu-id="91ae4-107">A module can include the following types of Help.</span></span>

- <span data-ttu-id="91ae4-108">**Ajuda do cmdlet**.</span><span class="sxs-lookup"><span data-stu-id="91ae4-108">**Cmdlet Help**.</span></span> <span data-ttu-id="91ae4-109">Os tópicos de ajuda que descrevem cmdlets num módulo são arquivos XML que utilizam o comando ajudam esquema</span><span class="sxs-lookup"><span data-stu-id="91ae4-109">The Help topics that describe cmdlets in a module are XML files that use the command help schema</span></span>

- <span data-ttu-id="91ae4-110">**Ajuda do provedor**.</span><span class="sxs-lookup"><span data-stu-id="91ae4-110">**Provider Help**.</span></span> <span data-ttu-id="91ae4-111">Os tópicos de ajuda que descrevem os provedores num módulo são arquivos XML que utilizam o fornecedor de ajudam o esquema.</span><span class="sxs-lookup"><span data-stu-id="91ae4-111">The Help topics that describe providers in a module are XML files that use the provider help schema.</span></span>

- <span data-ttu-id="91ae4-112">**Função ajuda**.</span><span class="sxs-lookup"><span data-stu-id="91ae4-112">**Function Help**.</span></span> <span data-ttu-id="91ae4-113">Os tópicos de ajuda que descrevem as funções num módulo pode ser arquivos XML que utilizam o comando ajudam o esquema ou baseada no comentário tópicos de ajuda dentro da função, ou o script ou o módulo de script</span><span class="sxs-lookup"><span data-stu-id="91ae4-113">The Help topics that describe functions in a module can be XML files that use the command help schema or comment-based Help topics within the function, or the script or script module</span></span>

- <span data-ttu-id="91ae4-114">**Ajuda do script**.</span><span class="sxs-lookup"><span data-stu-id="91ae4-114">**Script Help**.</span></span> <span data-ttu-id="91ae4-115">Os tópicos de ajuda que descrevem os scripts num módulo pode ser arquivos XML que utilizam o comando ajudam o esquema ou baseada no comentário tópicos de ajuda no script ou o módulo de script.</span><span class="sxs-lookup"><span data-stu-id="91ae4-115">The Help topics that describe scripts in a module can be XML files that use the command help schema or comment-based Help topics in the script or script module.</span></span>

- <span data-ttu-id="91ae4-116">**Conceitual ("sobre") ajuda**.</span><span class="sxs-lookup"><span data-stu-id="91ae4-116">**Conceptual ("About") Help**.</span></span> <span data-ttu-id="91ae4-117">Pode utilizar um conceitual ("sobre") tópico de ajuda para descrever o módulo e seus membros e explicar como os membros podem ser utilizados em conjunto para realizar tarefas.</span><span class="sxs-lookup"><span data-stu-id="91ae4-117">You can use a conceptual ("about") Help topic to describe the module and its members and to explain how the members can be used together to perform tasks.</span></span> <span data-ttu-id="91ae4-118">Tópicos de ajuda conceituais são ficheiros de texto com codificação Unicode (UTF-8).</span><span class="sxs-lookup"><span data-stu-id="91ae4-118">Conceptual Help topics are text files with Unicode (UTF-8) encoding.</span></span> <span data-ttu-id="91ae4-119">O nome do ficheiro tem de utilizar o `about_<name>.help.txt` formato, como about_MyModule.help.txt.</span><span class="sxs-lookup"><span data-stu-id="91ae4-119">The file name must use the `about_<name>.help.txt` format, such as about_MyModule.help.txt.</span></span> <span data-ttu-id="91ae4-120">Por predefinição, o Windows PowerShell inclui mais de 100 destes tópicos sobre ajudar conceitual, e são formatados semelhante ao seguinte exemplo.</span><span class="sxs-lookup"><span data-stu-id="91ae4-120">By default, Windows PowerShell includes over 100 of these conceptual About Help topics, and they are formatted like the following example.</span></span>

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

## <a name="placement-of-module-help"></a><span data-ttu-id="91ae4-121">Colocação de ajuda do módulo</span><span class="sxs-lookup"><span data-stu-id="91ae4-121">Placement of Module Help</span></span>

<span data-ttu-id="91ae4-122">O `Get-Help` cmdlet procura por ficheiros de tópico de ajuda do módulo em subdiretórios específicos de idiomas do diretório de módulo.</span><span class="sxs-lookup"><span data-stu-id="91ae4-122">The `Get-Help` cmdlet looks for module Help topic files in language-specific subdirectories of the module directory.</span></span>

<span data-ttu-id="91ae4-123">Por exemplo, o diagrama de estrutura de diretório seguinte mostra a localização dos tópicos de ajuda para o módulo de SampleModule.</span><span class="sxs-lookup"><span data-stu-id="91ae4-123">For example, the following directory structure diagram shows the location of the Help topics for the SampleModule module.</span></span>

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
> <span data-ttu-id="91ae4-124">No exemplo, o  *\<ModulePath >* marcador de posição representa um dos caminhos no `PSModulePath` variável de ambiente, como $home\Documents\Modules, $pshome\Modules ou um caminho personalizado que o utilizador Especifica.</span><span class="sxs-lookup"><span data-stu-id="91ae4-124">In the example, the *\<ModulePath>* placeholder represents one of the paths in the `PSModulePath` environment variable, such as $home\Documents\Modules, $pshome\Modules, or a custom path that the user specifies.</span></span>

## <a name="getting-module-help"></a><span data-ttu-id="91ae4-125">Obter ajuda do módulo</span><span class="sxs-lookup"><span data-stu-id="91ae4-125">Getting Module Help</span></span>

<span data-ttu-id="91ae4-126">Quando um utilizador importa um módulo para uma sessão, os tópicos de ajuda para aquele módulo são importados para a sessão, juntamente com o módulo.</span><span class="sxs-lookup"><span data-stu-id="91ae4-126">When a user imports a module into a session, the Help topics for that module are imported into the session along with the module.</span></span> <span data-ttu-id="91ae4-127">Pode listar os ficheiros de tópico de ajuda no valor da chave de lista de ficheiros no manifesto do módulo, mas tópicos de ajuda não são afetadas pelo `Export-ModuleMember` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="91ae4-127">You can list the Help topic files in the value of the FileList key in the module manifest, but Help topics are not affected by the `Export-ModuleMember` cmdlet.</span></span>

<span data-ttu-id="91ae4-128">Pode fornecer tópicos de ajuda do módulo em idiomas diferentes.</span><span class="sxs-lookup"><span data-stu-id="91ae4-128">You can provide module Help topics in different languages.</span></span> <span data-ttu-id="91ae4-129">O `Get-Help` cmdlet apresenta automaticamente tópicos de ajuda do módulo no idioma que é especificado para o utilizador atual no idioma opções regionais e de item no painel de controlo.</span><span class="sxs-lookup"><span data-stu-id="91ae4-129">The `Get-Help` cmdlet automatically displays module Help topics in the language that is specified for the current user in the Regional and Language Options item in Control Panel.</span></span> <span data-ttu-id="91ae4-130">No Windows Vista e versões posteriores do Windows, `Get-Help` procura os tópicos de ajuda em subdiretórios específicos de idiomas do diretório de módulo em conformidade com as normas de contingência de idioma estabelecido para Windows.</span><span class="sxs-lookup"><span data-stu-id="91ae4-130">In Windows Vista and later versions of Windows, `Get-Help` searches for the Help topics in language-specific subdirectories of the module directory in accordance with the language fallback standards established for Windows.</span></span>

<span data-ttu-id="91ae4-131">A partir do Windows PowerShell 3.0, executar um `Get-Help` comando para um cmdlet ou uma função aciona a importação automática do módulo.</span><span class="sxs-lookup"><span data-stu-id="91ae4-131">Beginning in Windows PowerShell 3.0, running a `Get-Help` command for a cmdlet or function triggers automatic importing of the module.</span></span> <span data-ttu-id="91ae4-132">O `Get-Help` cmdlet apresenta imediatamente os conteúdos dos tópicos de ajuda no módulo.</span><span class="sxs-lookup"><span data-stu-id="91ae4-132">The `Get-Help` cmdlet immediately displays the contents of the help topics in the module.</span></span>

<span data-ttu-id="91ae4-133">Se o módulo não contém tópicos de ajuda e não há nenhum tópicos de ajuda para os comandos no módulo no computador do usuário, `Get-Help` apresenta ajuda gerado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="91ae4-133">If the module does not contain help topics and there are no help topics for the commands in the module on the user's computer, `Get-Help` displays auto-generated help.</span></span> <span data-ttu-id="91ae4-134">A ajuda de gerado automaticamente inclui a sintaxe de comando, parâmetros e tipos de entrada e saídos, mas não inclui quaisquer descrições.</span><span class="sxs-lookup"><span data-stu-id="91ae4-134">The auto-generated help includes the command syntax, parameters, and input and output types, but does not include any descriptions.</span></span> <span data-ttu-id="91ae4-135">A ajuda de gerado automaticamente inclui o texto que direciona o utilizador tentar utilizar o `Update-Help` cmdlet para transferir a ajuda para o comando a partir da Internet ou uma partilha de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="91ae4-135">The auto-generated help includes text that directs the user to try to use the `Update-Help` cmdlet to download help for the command from the Internet or a file share.</span></span> <span data-ttu-id="91ae4-136">Ele também recomenda utilizar o **Online** parâmetro do `Get-Help` cmdlet para obter a versão online do tópico de ajuda.</span><span class="sxs-lookup"><span data-stu-id="91ae4-136">It also recommends using the **Online** parameter of the `Get-Help` cmdlet to get the online version of the help topic.</span></span>

## <a name="supporting-updatable-help"></a><span data-ttu-id="91ae4-137">Apoio ajuda Atualizável</span><span class="sxs-lookup"><span data-stu-id="91ae4-137">Supporting Updatable Help</span></span>

<span data-ttu-id="91ae4-138">Os utilizadores do Windows PowerShell 3.0 e versões posteriores do Windows PowerShell, podem transferir e instalar ficheiros de ajuda atualizada para um módulo da Internet ou a partir de uma partilha de ficheiros local.</span><span class="sxs-lookup"><span data-stu-id="91ae4-138">Users of Windows PowerShell 3.0 and later versions of Windows PowerShell can download and install updated help files for a module from the Internet or from a local file share.</span></span> <span data-ttu-id="91ae4-139">O `Update-Help` e `Save-Help` cmdlets ocultar os detalhes de gerenciamento do usuário.</span><span class="sxs-lookup"><span data-stu-id="91ae4-139">The `Update-Help` and `Save-Help` cmdlets hide the management details from the user.</span></span> <span data-ttu-id="91ae4-140">Os usuários executem o `Update-Help` cmdlet e, em seguida, utilizar o `Get-Help` cmdlet para ler os ficheiros de ajuda mais recentes para o módulo de linha de comandos do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="91ae4-140">Users run the `Update-Help` cmdlet and then use the `Get-Help` cmdlet to read the newest help files for the module at the Windows PowerShell command prompt.</span></span> <span data-ttu-id="91ae4-141">Os utilizadores não é necessário reiniciar o Windows ou Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="91ae4-141">Users do not need to restart Windows or Windows PowerShell.</span></span>

<span data-ttu-id="91ae4-142">Os utilizadores atrás de firewalls e pessoas sem acesso à Internet podem utilizar a ajuda Atualizável, também.</span><span class="sxs-lookup"><span data-stu-id="91ae4-142">Users behind firewalls and those without Internet access can use Updatable Help, as well.</span></span> <span data-ttu-id="91ae4-143">Os administradores com Internet aceder a utilizar o `Save-Help` cmdlet para transferir e instalar os ficheiros de ajuda mais recentes para uma partilha de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="91ae4-143">Administrators with Internet access use the `Save-Help` cmdlet to download and install the newest help files to a file share.</span></span> <span data-ttu-id="91ae4-144">Em seguida, os utilizadores utilizam o **caminho** parâmetro do `Update-Help` cmdlet para obter os ficheiros de ajuda mais recentes da partilha de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="91ae4-144">Then, users use the **Path** parameter of the `Update-Help` cmdlet to get the newest help files from the file share.</span></span>

<span data-ttu-id="91ae4-145">Os autores de módulo podem incluir arquivos de ajuda no módulo e utilizar a ajuda Atualizável de mensagens em fila para atualizar os arquivos de ajuda ou omitir os arquivos de ajuda do módulo e utilizar a ajuda Atualizável para instalar e atualizá-los.</span><span class="sxs-lookup"><span data-stu-id="91ae4-145">Module authors can include help files in the module and use Updatable Help to update the help files, or omit help files from the module and use Updatable Help both to install and to update them.</span></span>

<span data-ttu-id="91ae4-146">Para obter mais informações sobre Ajuda Atualizável, consulte [apoio ajuda Atualizável](./supporting-updatable-help.md).</span><span class="sxs-lookup"><span data-stu-id="91ae4-146">For more information about Updatable Help, see [Supporting Updatable Help](./supporting-updatable-help.md).</span></span>

## <a name="supporting-online-help"></a><span data-ttu-id="91ae4-147">Apoio Ajuda Online</span><span class="sxs-lookup"><span data-stu-id="91ae4-147">Supporting Online Help</span></span>

<span data-ttu-id="91ae4-148">Os utilizadores que não podem ou não instalar atualizados ajuda arquivos em seus computadores frequentemente contam com a versão online dos tópicos de ajuda do módulo.</span><span class="sxs-lookup"><span data-stu-id="91ae4-148">Users who cannot or do not install updated help files on their computers often rely on the online version of module help topics.</span></span> <span data-ttu-id="91ae4-149">O **Online** parâmetro do `Get-Help` cmdlet abre a versão online de um cmdlet ou uma função avançada de tópico de ajuda para o utilizador no seu browser predefinido.</span><span class="sxs-lookup"><span data-stu-id="91ae4-149">The **Online** parameter of the `Get-Help` cmdlet opens the online version of a cmdlet or advanced function help topic for the user in their default Internet browser.</span></span>

<span data-ttu-id="91ae4-150">O `Get-Help` cmdlet utiliza o valor da **HelpUri** propriedade do cmdlet ou função para localizar a versão online do tópico de ajuda.</span><span class="sxs-lookup"><span data-stu-id="91ae4-150">The `Get-Help` cmdlet uses the value of the **HelpUri** property of the cmdlet or function to find the online version of the help topic.</span></span>

<span data-ttu-id="91ae4-151">A partir do Windows PowerShell 3.0, pode ajudar os utilizadores a encontrar a versão online dos tópicos de ajuda do cmdlet e função definindo o atributo HelpUri na classe cmdlet ou o **HelpUri** propriedade do **CmdletBinding** atributo.</span><span class="sxs-lookup"><span data-stu-id="91ae4-151">Beginning in Windows PowerShell 3.0, you can help users find the online version of cmdlet and function help topics by defining the HelpUri attribute on the cmdlet class or the **HelpUri** property of the **CmdletBinding** attribute.</span></span> <span data-ttu-id="91ae4-152">O valor do atributo é o valor do **HelpUri** propriedade da função ou cmdlet.</span><span class="sxs-lookup"><span data-stu-id="91ae4-152">The value of the attribute is the value of the **HelpUri** property of the cmdlet or function.</span></span>

<span data-ttu-id="91ae4-153">Para obter mais informações, consulte [apoio Ajuda Online](./supporting-online-help.md).</span><span class="sxs-lookup"><span data-stu-id="91ae4-153">For more information, see [Supporting Online Help](./supporting-online-help.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="91ae4-154">Veja Também</span><span class="sxs-lookup"><span data-stu-id="91ae4-154">See Also</span></span>

[<span data-ttu-id="91ae4-155">Escrever um módulo do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="91ae4-155">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

[<span data-ttu-id="91ae4-156">Apoio ajuda Atualizável</span><span class="sxs-lookup"><span data-stu-id="91ae4-156">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)

[<span data-ttu-id="91ae4-157">Apoio Ajuda Online</span><span class="sxs-lookup"><span data-stu-id="91ae4-157">Supporting Online Help</span></span>](./supporting-online-help.md)