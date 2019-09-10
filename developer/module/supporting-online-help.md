---
title: Suporte à ajuda online | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: 5c5707d1c533e0498c6794b60f4499e530e25813
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848088"
---
# <a name="supporting-online-help"></a><span data-ttu-id="4c1c0-102">Apoio Ajuda Online</span><span class="sxs-lookup"><span data-stu-id="4c1c0-102">Supporting Online Help</span></span>

<span data-ttu-id="4c1c0-103">A partir do Windows PowerShell 3,0, há duas maneiras de dar suporte `Get-Help` ao recurso online para comandos do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c1c0-103">Beginning in Windows PowerShell 3.0, there are two ways to support the `Get-Help` Online feature for Windows PowerShell commands.</span></span> <span data-ttu-id="4c1c0-104">Este tópico explica como implementar esse recurso para diferentes tipos de comando.</span><span class="sxs-lookup"><span data-stu-id="4c1c0-104">This topic explains how to implement this feature for different command types.</span></span>

## <a name="about-online-help"></a><span data-ttu-id="4c1c0-105">Sobre a ajuda online</span><span class="sxs-lookup"><span data-stu-id="4c1c0-105">About Online Help</span></span>

<span data-ttu-id="4c1c0-106">A ajuda online sempre foi uma parte vital do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c1c0-106">Online help has always been a vital part of Windows PowerShell.</span></span> <span data-ttu-id="4c1c0-107">Embora o `Get-Help` cmdlet exiba tópicos de ajuda no prompt de comando, muitos usuários preferem a experiência de leitura online, incluindo codificação por cores, hiperlinks e compartilhamento de ideias em conteúdo da Comunidade e documentos baseados em wiki.</span><span class="sxs-lookup"><span data-stu-id="4c1c0-107">Although the `Get-Help` cmdlet displays help topics at the command prompt, many users prefer the experience of reading online, including color-coding, hyperlinks, and sharing ideas in Community Content and wiki-based documents.</span></span> <span data-ttu-id="4c1c0-108">O mais importante é que, antes do advento da ajuda atualizável, a ajuda online forneceu a versão mais atualizada dos arquivos de ajuda.</span><span class="sxs-lookup"><span data-stu-id="4c1c0-108">Most importantly, before the advent of Updatable Help, online help provided the most up-to-date version of the help files.</span></span>

<span data-ttu-id="4c1c0-109">Com o advento da ajuda atualizável no Windows PowerShell 3,0, a ajuda online ainda exerce uma função vital.</span><span class="sxs-lookup"><span data-stu-id="4c1c0-109">With the advent of Updatable Help in Windows PowerShell 3.0, online help still plays a vital role.</span></span> <span data-ttu-id="4c1c0-110">Além da experiência do usuário flexível, a ajuda online fornece ajuda aos usuários que não ou que não podem usar a ajuda atualizável para baixar tópicos da ajuda.</span><span class="sxs-lookup"><span data-stu-id="4c1c0-110">In addition to the flexible user experience, online help provides help to users who do not or cannot use Updatable Help to download help topics.</span></span>

## <a name="how-get-help--online-works"></a><span data-ttu-id="4c1c0-111">Como o Get-Help-online funciona</span><span class="sxs-lookup"><span data-stu-id="4c1c0-111">How Get-Help -Online Works</span></span>

<span data-ttu-id="4c1c0-112">Para ajudar os usuários a encontrar os tópicos da ajuda online para `Get-Help` comandos, o comando tem um parâmetro online que abre a versão online do tópico da ajuda para um comando no navegador de Internet padrão do usuário.</span><span class="sxs-lookup"><span data-stu-id="4c1c0-112">To help users find the online help topics for commands, the `Get-Help` command has an Online parameter that opens the online version of help topic for a command in the user's default Internet browser.</span></span>

<span data-ttu-id="4c1c0-113">Por exemplo, o comando a seguir abre o tópico da ajuda online `Invoke-Command` para o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4c1c0-113">For example, the following command opens the online help topic for the `Invoke-Command` cmdlet.</span></span>

```powershell
Get-Help Invoke-Command -Online
```

<span data-ttu-id="4c1c0-114">Para implementar `Get-Help` -online, o `Get-Help` cmdlet procura um Uniform Resource Identifier (URI) para o tópico de ajuda da versão online nos locais a seguir.</span><span class="sxs-lookup"><span data-stu-id="4c1c0-114">To implement `Get-Help` -Online, the `Get-Help` cmdlet looks for a Uniform Resource Identifier (URI) for the online version help topic in the following locations.</span></span>

- <span data-ttu-id="4c1c0-115">O primeiro link na seção links relacionados do tópico da ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="4c1c0-115">The first link in the Related Links section of the help topic for the command.</span></span> <span data-ttu-id="4c1c0-116">O tópico da ajuda deve ser instalado no computador do usuário.</span><span class="sxs-lookup"><span data-stu-id="4c1c0-116">The help topic must be installed on the user's computer.</span></span> <span data-ttu-id="4c1c0-117">Esse recurso foi introduzido no Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="4c1c0-117">This feature was introduced in Windows PowerShell 2.0.</span></span>

- <span data-ttu-id="4c1c0-118">A propriedade HelpUri de qualquer comando.</span><span class="sxs-lookup"><span data-stu-id="4c1c0-118">The HelpUri property of any command.</span></span> <span data-ttu-id="4c1c0-119">A propriedade HelpUri é acessível mesmo quando o tópico da ajuda do comando não está instalado no computador do usuário.</span><span class="sxs-lookup"><span data-stu-id="4c1c0-119">The HelpUri property is accessible even when the help topic for the command is not installed on the user's computer.</span></span> <span data-ttu-id="4c1c0-120">Esse recurso foi introduzido no Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="4c1c0-120">This feature was introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="4c1c0-121">`Get-Help`procura um URI na primeira entrada da seção links relacionados antes de obter o valor da propriedade HelpUri.</span><span class="sxs-lookup"><span data-stu-id="4c1c0-121">`Get-Help` looks for a URI in the first entry in the Related Links section before getting the HelpUri property value.</span></span> <span data-ttu-id="4c1c0-122">Se o valor da propriedade estiver incorreto ou alterado, você poderá substituí-lo inserindo um valor diferente no primeiro link relacionado.</span><span class="sxs-lookup"><span data-stu-id="4c1c0-122">If the property value is incorrect or has changed, you can override it by entering a different value in the first Related Link.</span></span> <span data-ttu-id="4c1c0-123">No entanto, o primeiro link relacionado funciona somente quando os tópicos da ajuda são instalados no computador do usuário.</span><span class="sxs-lookup"><span data-stu-id="4c1c0-123">However, the first Related Link works only when the help topics are installed on the user's computer.</span></span>

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a><span data-ttu-id="4c1c0-124">Adicionando um URI ao primeiro link relacionado de um tópico de ajuda de comando</span><span class="sxs-lookup"><span data-stu-id="4c1c0-124">Adding a URI to the first related link of a command help topic</span></span>

<span data-ttu-id="4c1c0-125">Você pode oferecer `Get-Help` suporte-online para qualquer comando, adicionando um URI válido à primeira entrada na seção links relacionados do tópico da ajuda baseada em XML para o comando.</span><span class="sxs-lookup"><span data-stu-id="4c1c0-125">You can support `Get-Help` -Online for any command by adding a valid URI to the first entry in the Related Links section of the XML-based help topic for the command.</span></span> <span data-ttu-id="4c1c0-126">Essa opção só é válida em tópicos de ajuda baseados em XML e funciona somente quando o tópico da ajuda está instalado no computador do usuário.</span><span class="sxs-lookup"><span data-stu-id="4c1c0-126">This option is valid only in XML-based help topics and works only when the help topic is installed on the user's computer.</span></span> <span data-ttu-id="4c1c0-127">Quando o tópico da ajuda é instalado e o URI é populado, esse valor tem precedência sobre a propriedade **HelpUri** do comando.</span><span class="sxs-lookup"><span data-stu-id="4c1c0-127">When the help topic is installed and the URI is populated, this value takes precedence over the **HelpUri** property of the command.</span></span>

<span data-ttu-id="4c1c0-128">Para dar suporte a esse recurso, o URI deve aparecer `maml:uri` no elemento sob o `maml:relatedLinks/maml:navigationLink` primeiro elemento no `maml:relatedLinks` elemento.</span><span class="sxs-lookup"><span data-stu-id="4c1c0-128">To support this feature, the URI must appear in the `maml:uri` element under the first `maml:relatedLinks/maml:navigationLink` element in the `maml:relatedLinks` element.</span></span>

<span data-ttu-id="4c1c0-129">O XML a seguir mostra o posicionamento correto do URI.</span><span class="sxs-lookup"><span data-stu-id="4c1c0-129">The following XML shows the correct placement of the URI.</span></span> <span data-ttu-id="4c1c0-130">O texto "versão online:" no `maml:linkText` elemento é uma prática recomendada, mas não é necessário.</span><span class="sxs-lookup"><span data-stu-id="4c1c0-130">The "Online version:" text in the `maml:linkText` element is a best practice, but it is not required.</span></span>

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

## <a name="adding-the-helpuri-property-to-a-command"></a><span data-ttu-id="4c1c0-131">Adicionando a propriedade HelpUri a um comando</span><span class="sxs-lookup"><span data-stu-id="4c1c0-131">Adding the HelpUri property to a command</span></span>

<span data-ttu-id="4c1c0-132">Esta seção mostra como adicionar a propriedade HelpUri a comandos de tipos diferentes.</span><span class="sxs-lookup"><span data-stu-id="4c1c0-132">This section shows how to add the HelpUri property to commands of different types.</span></span>

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a><span data-ttu-id="4c1c0-133">Adicionando uma propriedade HelpUri a um cmdlet</span><span class="sxs-lookup"><span data-stu-id="4c1c0-133">Adding a HelpUri Property to a Cmdlet</span></span>

<span data-ttu-id="4c1c0-134">Para os cmdlets escritos C#em, adicione um atributo **HelpUri** à classe cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4c1c0-134">For cmdlets written in C#, add a **HelpUri** attribute to the Cmdlet class.</span></span> <span data-ttu-id="4c1c0-135">O valor do atributo deve ser um URI que comece com "http" ou "https".</span><span class="sxs-lookup"><span data-stu-id="4c1c0-135">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="4c1c0-136">O código a seguir mostra o atributo HelpUri da `Get-History` classe cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4c1c0-136">The following code shows the HelpUri attribute of the `Get-History` cmdlet class.</span></span>

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a><span data-ttu-id="4c1c0-137">Adicionando uma propriedade HelpUri a uma função avançada</span><span class="sxs-lookup"><span data-stu-id="4c1c0-137">Adding a HelpUri Property to an Advanced Function</span></span>

<span data-ttu-id="4c1c0-138">Para funções avançadas, adicione uma propriedade **HelpUri** ao atributo **CmdletBinding** .</span><span class="sxs-lookup"><span data-stu-id="4c1c0-138">For advanced functions, add a **HelpUri** property to the **CmdletBinding** attribute.</span></span> <span data-ttu-id="4c1c0-139">O valor da propriedade deve ser um URI que comece com "http" ou "https".</span><span class="sxs-lookup"><span data-stu-id="4c1c0-139">The value of the property must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="4c1c0-140">O código a seguir mostra o atributo HelpUri da função New-Calendar</span><span class="sxs-lookup"><span data-stu-id="4c1c0-140">The following code shows the HelpUri attribute of the New-Calendar function</span></span>

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a><span data-ttu-id="4c1c0-141">Adicionando um atributo HelpUri a um comando CIM</span><span class="sxs-lookup"><span data-stu-id="4c1c0-141">Adding a HelpUri Attribute to a CIM Command</span></span>

<span data-ttu-id="4c1c0-142">Para comandos CIM, adicione um atributo **HelpUri** ao elemento **CMDLETMETADATA** no arquivo CDXML.</span><span class="sxs-lookup"><span data-stu-id="4c1c0-142">For CIM commands, add a **HelpUri** attribute to the **CmdletMetadata** element in the CDXML file.</span></span> <span data-ttu-id="4c1c0-143">O valor do atributo deve ser um URI que comece com "http" ou "https".</span><span class="sxs-lookup"><span data-stu-id="4c1c0-143">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="4c1c0-144">O código a seguir mostra o atributo HelpUri do comando Start-Debug CIM</span><span class="sxs-lookup"><span data-stu-id="4c1c0-144">The following code shows the HelpUri attribute of the Start-Debug CIM command</span></span>

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a><span data-ttu-id="4c1c0-145">Adicionando um atributo HelpUri a um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="4c1c0-145">Adding a HelpUri Attribute to a Workflow</span></span>

<span data-ttu-id="4c1c0-146">Para fluxos de trabalho que são gravados na linguagem do Windows PowerShell, adicione um **. ExternalHelp** a diretiva de comentário para o código do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4c1c0-146">For workflows that are written in the Windows PowerShell language, add an **.ExternalHelp** comment directive to the workflow code.</span></span> <span data-ttu-id="4c1c0-147">O valor da diretiva deve ser um URI que comece com "http" ou "https".</span><span class="sxs-lookup"><span data-stu-id="4c1c0-147">The value of the directive must be a URI that begins with "http" or "https".</span></span>

> [!NOTE]
> <span data-ttu-id="4c1c0-148">A propriedade HelpUri não tem suporte para fluxos de trabalho baseados em XAML no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c1c0-148">The HelpUri property is not supported for XAML-based workflows in Windows PowerShell.</span></span>

<span data-ttu-id="4c1c0-149">O código a seguir mostra o. Diretiva ExternalHelp em um arquivo de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4c1c0-149">The following code shows the .ExternalHelp directive in a workflow file.</span></span>

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```