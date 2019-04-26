---
title: Apoio Ajuda Online | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: b76f45299d11dc10c8b16ed80f87c7f1fcc5ed65
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082146"
---
# <a name="supporting-online-help"></a><span data-ttu-id="60384-102">Apoio Ajuda Online</span><span class="sxs-lookup"><span data-stu-id="60384-102">Supporting Online Help</span></span>

<span data-ttu-id="60384-103">A partir do Windows PowerShell 3.0, existem duas formas para apoiar o `Get-Help` recurso Online para comandos do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="60384-103">Beginning in Windows PowerShell 3.0, there are two ways to support the `Get-Help` Online feature for Windows PowerShell commands.</span></span> <span data-ttu-id="60384-104">Este tópico explica como implementar esta funcionalidade para tipos de comando diferentes.</span><span class="sxs-lookup"><span data-stu-id="60384-104">This topic explains how to implement this feature for different command types.</span></span>

## <a name="about-online-help"></a><span data-ttu-id="60384-105">Ajuda Online</span><span class="sxs-lookup"><span data-stu-id="60384-105">About Online Help</span></span>

<span data-ttu-id="60384-106">Ajuda online sempre foi uma parte essencial do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="60384-106">Online help has always been a vital part of Windows PowerShell.</span></span> <span data-ttu-id="60384-107">Embora o `Get-Help` cmdlet apresenta os tópicos de ajuda no prompt de comando, o número de utilizadores que prefere a experiência de leitura de online, incluindo codificação por cores, hiperlinks e compartilhamento de idéias no conteúdo da Comunidade e os documentos com base no wiki.</span><span class="sxs-lookup"><span data-stu-id="60384-107">Although the `Get-Help` cmdlet displays help topics at the command prompt, many users prefer the experience of reading online, including color-coding, hyperlinks, and sharing ideas in Community Content and wiki-based documents.</span></span> <span data-ttu-id="60384-108">Mais importante é que, antes do advento do ajuda Atualizável, ajuda online fornecidos a versão mais recente dos ficheiros de ajuda.</span><span class="sxs-lookup"><span data-stu-id="60384-108">Most importantly, before the advent of Updatable Help, online help provided the most up-to-date version of the help files.</span></span>

<span data-ttu-id="60384-109">Com o advento do ajuda Atualizável no Windows PowerShell 3.0, a ajuda online ainda desempenha um papel fundamental.</span><span class="sxs-lookup"><span data-stu-id="60384-109">With the advent of Updatable Help in Windows PowerShell 3.0, online help still plays a vital role.</span></span> <span data-ttu-id="60384-110">Além da experiência de usuário flexível, a ajuda online fornece ajuda aos utilizadores que não suportam ou não é possível utilizar ajuda Atualizável para transferir os tópicos de ajuda.</span><span class="sxs-lookup"><span data-stu-id="60384-110">In addition to the flexible user experience, online help provides help to users who do not or cannot use Updatable Help to download help topics.</span></span>

## <a name="how-get-help--online-works"></a><span data-ttu-id="60384-111">Como Get-Help-Online funciona</span><span class="sxs-lookup"><span data-stu-id="60384-111">How Get-Help -Online Works</span></span>

<span data-ttu-id="60384-112">Para ajudar os utilizadores a encontrar os tópicos de ajuda online para obter comandos, o `Get-Help` comando tem um parâmetro Online que abre a versão online de tópico de ajuda para um comando no browser de Internet predefinido do utilizador.</span><span class="sxs-lookup"><span data-stu-id="60384-112">To help users find the online help topics for commands, the `Get-Help` command has an Online parameter that opens the online version of help topic for a command in the user's default Internet browser.</span></span>

<span data-ttu-id="60384-113">Por exemplo, o seguinte comando abre o tópico de ajuda online para o `Invoke-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="60384-113">For example, the following command opens the online help topic for the `Invoke-Command` cmdlet.</span></span>

```powershell
Get-Help Invoke-Command -Online
```

<span data-ttu-id="60384-114">Para implementar `Get-Help` -Online, o `Get-Help` cmdlet procura para um identificador URI (Uniform Resource) para o tópico de ajuda da versão online nas seguintes localizações.</span><span class="sxs-lookup"><span data-stu-id="60384-114">To implement `Get-Help` -Online, the `Get-Help` cmdlet looks for a Uniform Resource Identifier (URI) for the online version help topic in the following locations.</span></span>

- <span data-ttu-id="60384-115">Na primeira ligação na seção Links relacionados do tópico de ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="60384-115">The first link in the Related Links section of the help topic for the command.</span></span> <span data-ttu-id="60384-116">O tópico de ajuda deve ser instalado no computador do usuário.</span><span class="sxs-lookup"><span data-stu-id="60384-116">The help topic must be installed on the user's computer.</span></span> <span data-ttu-id="60384-117">Esta funcionalidade foi introduzida no Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="60384-117">This feature was introduced in Windows PowerShell 2.0.</span></span>

- <span data-ttu-id="60384-118">A propriedade HelpUri de todos os comandos.</span><span class="sxs-lookup"><span data-stu-id="60384-118">The HelpUri property of any command.</span></span> <span data-ttu-id="60384-119">A propriedade HelpUri está acessível, mesmo quando o tópico de ajuda para o comando não está instalado no computador do usuário.</span><span class="sxs-lookup"><span data-stu-id="60384-119">The HelpUri property is accessible even when the help topic for the command is not installed on the user's computer.</span></span> <span data-ttu-id="60384-120">Esta funcionalidade foi introduzida no Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="60384-120">This feature was introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="60384-121">`Get-Help` procura um URI na primeira entrada na seção Links relacionados antes de obter o valor da propriedade HelpUri.</span><span class="sxs-lookup"><span data-stu-id="60384-121">`Get-Help` looks for a URI in the first entry in the Related Links section before getting the HelpUri property value.</span></span> <span data-ttu-id="60384-122">Se o valor da propriedade está incorreto ou foi alterado, pode substitui-lo ao introduzir um valor diferente na primeira ligação relacionados.</span><span class="sxs-lookup"><span data-stu-id="60384-122">If the property value is incorrect or has changed, you can override it by entering a different value in the first Related Link.</span></span> <span data-ttu-id="60384-123">No entanto, na primeira ligação relacionados funciona apenas quando os tópicos de ajuda estão instalados no computador do usuário.</span><span class="sxs-lookup"><span data-stu-id="60384-123">However, the first Related Link works only when the help topics are installed on the user's computer.</span></span>

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a><span data-ttu-id="60384-124">Adicionar um URI na primeira ligação relacionada de um tópico de ajuda do comando</span><span class="sxs-lookup"><span data-stu-id="60384-124">Adding a URI to the first related link of a command help topic</span></span>

<span data-ttu-id="60384-125">Pode suportar `Get-Help` -Online para qualquer comando através da adição de um URI válido para a primeira entrada na seção Links relacionados do tópico de ajuda baseados em XML para o comando.</span><span class="sxs-lookup"><span data-stu-id="60384-125">You can support `Get-Help` -Online for any command by adding a valid URI to the first entry in the Related Links section of the XML-based help topic for the command.</span></span> <span data-ttu-id="60384-126">Esta opção é válida apenas em tópicos de ajuda baseados em XML e funciona apenas quando o tópico de ajuda está instalado no computador do usuário.</span><span class="sxs-lookup"><span data-stu-id="60384-126">This option is valid only in XML-based help topics and works only when the help topic is installed on the user's computer.</span></span> <span data-ttu-id="60384-127">Quando o tópico de ajuda está instalado e o URI é preenchido, este valor tem precedência sobre o **HelpUri** propriedade do comando.</span><span class="sxs-lookup"><span data-stu-id="60384-127">When the help topic is installed and the URI is populated, this value takes precedence over the **HelpUri** property of the command.</span></span> <span data-ttu-id="60384-128">Para obter informações sobre tópicos de ajuda baseados em XML para comandos, consulte [Writing XML-Based tópicos de ajuda para comandos](../help/writing-xml-based-help-topics-for-commands.md).</span><span class="sxs-lookup"><span data-stu-id="60384-128">For information about XML-based help topics for commands, see [Writing XML-Based Help Topics for Commands](../help/writing-xml-based-help-topics-for-commands.md).</span></span>

<span data-ttu-id="60384-129">Para suportar esta funcionalidade, o URI tem de aparecer no `maml:uri` elemento no primeiro `maml:relatedLinks/maml:navigationLink` elemento no `maml:relatedLinks` elemento.</span><span class="sxs-lookup"><span data-stu-id="60384-129">To support this feature, the URI must appear in the `maml:uri` element under the first `maml:relatedLinks/maml:navigationLink` element in the `maml:relatedLinks` element.</span></span>

<span data-ttu-id="60384-130">O XML a seguir mostra o posicionamento correto do URI.</span><span class="sxs-lookup"><span data-stu-id="60384-130">The following XML shows the correct placement of the URI.</span></span> <span data-ttu-id="60384-131">A "versão Online:" texto no `maml:linkText` elemento é uma prática recomendada, mas não é necessário.</span><span class="sxs-lookup"><span data-stu-id="60384-131">The "Online version:" text in the `maml:linkText` element is a best practice, but it is not required.</span></span>

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>http://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a><span data-ttu-id="60384-132">Adicionar a propriedade HelpUri a um comando</span><span class="sxs-lookup"><span data-stu-id="60384-132">Adding the HelpUri property to a command</span></span>

<span data-ttu-id="60384-133">Esta secção mostra como adicionar a propriedade HelpUri a comandos de diferentes tipos.</span><span class="sxs-lookup"><span data-stu-id="60384-133">This section shows how to add the HelpUri property to commands of different types.</span></span>

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a><span data-ttu-id="60384-134">Adicionar uma propriedade HelpUri a um Cmdlet</span><span class="sxs-lookup"><span data-stu-id="60384-134">Adding a HelpUri Property to a Cmdlet</span></span>

<span data-ttu-id="60384-135">Para cmdlets escritos em C#, adicione uma **HelpUri** atributo à classe Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="60384-135">For cmdlets written in C#, add a **HelpUri** attribute to the Cmdlet class.</span></span> <span data-ttu-id="60384-136">O valor do atributo tem de ser um URI que começa com "http" ou "https".</span><span class="sxs-lookup"><span data-stu-id="60384-136">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="60384-137">O código seguinte mostra o atributo HelpUri a `Get-History` classe cmdlet.</span><span class="sxs-lookup"><span data-stu-id="60384-137">The following code shows the HelpUri attribute of the `Get-History` cmdlet class.</span></span>

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a><span data-ttu-id="60384-138">Adicionar uma propriedade HelpUri a uma função avançada</span><span class="sxs-lookup"><span data-stu-id="60384-138">Adding a HelpUri Property to an Advanced Function</span></span>

<span data-ttu-id="60384-139">Para funções avançadas, adicione uma **HelpUri** propriedade para o **CmdletBinding** atributo.</span><span class="sxs-lookup"><span data-stu-id="60384-139">For advanced functions, add a **HelpUri** property to the **CmdletBinding** attribute.</span></span> <span data-ttu-id="60384-140">O valor da propriedade tem de ser um URI que começa com "http" ou "https".</span><span class="sxs-lookup"><span data-stu-id="60384-140">The value of the property must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="60384-141">O código seguinte mostra o atributo HelpUri da função New-calendário</span><span class="sxs-lookup"><span data-stu-id="60384-141">The following code shows the HelpUri attribute of the New-Calendar function</span></span>

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a><span data-ttu-id="60384-142">Adicionar um atributo HelpUri a um comando CIM</span><span class="sxs-lookup"><span data-stu-id="60384-142">Adding a HelpUri Attribute to a CIM Command</span></span>

<span data-ttu-id="60384-143">Para obter comandos CIM, adicione uma **HelpUri** atributo para o **CmdletMetadata** elemento no ficheiro CDXML.</span><span class="sxs-lookup"><span data-stu-id="60384-143">For CIM commands, add a **HelpUri** attribute to the **CmdletMetadata** element in the CDXML file.</span></span> <span data-ttu-id="60384-144">O valor do atributo tem de ser um URI que começa com "http" ou "https".</span><span class="sxs-lookup"><span data-stu-id="60384-144">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="60384-145">O código seguinte mostra o atributo HelpUri do comando de início-Debug CIM</span><span class="sxs-lookup"><span data-stu-id="60384-145">The following code shows the HelpUri attribute of the Start-Debug CIM command</span></span>

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a><span data-ttu-id="60384-146">Adicionar um atributo HelpUri a um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="60384-146">Adding a HelpUri Attribute to a Workflow</span></span>

<span data-ttu-id="60384-147">Para fluxos de trabalho que são escritos no idioma do Windows PowerShell, adicione um **. ExternalHelp** diretiva de comentário para o código de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="60384-147">For workflows that are written in the Windows PowerShell language, add an **.ExternalHelp** comment directive to the workflow code.</span></span> <span data-ttu-id="60384-148">O valor da diretiva tem de ser um URI que começa com "http" ou "https".</span><span class="sxs-lookup"><span data-stu-id="60384-148">The value of the directive must be a URI that begins with "http" or "https".</span></span>

> [!NOTE]
> <span data-ttu-id="60384-149">A propriedade HelpUri não é suportada para fluxos de trabalho baseados em XAML no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="60384-149">The HelpUri property is not supported for XAML-based workflows in Windows PowerShell.</span></span>

<span data-ttu-id="60384-150">O código seguinte mostra o. Diretiva de ExternalHelp num arquivo de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="60384-150">The following code shows the .ExternalHelp directive in a workflow file.</span></span>

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```