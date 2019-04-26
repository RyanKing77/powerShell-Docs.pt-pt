---
title: 'Updatable Help Authoring: Passo a passo | Documentos da Microsoft'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082129"
---
# <a name="updatable-help-authoring-step-by-step"></a><span data-ttu-id="6bea8-102">Updatable Help Authoring: Step-by-Step (Criação de Ajuda Atualizável: Passo a Passo)</span><span class="sxs-lookup"><span data-stu-id="6bea8-102">Updatable Help Authoring: Step-by-Step</span></span>

<span data-ttu-id="6bea8-103">Este documentos, lista os passos no processo de criação ajuda Atualizável.</span><span class="sxs-lookup"><span data-stu-id="6bea8-103">This documents lists the steps in the process of authoring Updatable Help.</span></span>

## <a name="authoring-updatable-help-step-by-step"></a><span data-ttu-id="6bea8-104">Ajuda Atualizável de criação: Step-by-Step (Criação de Ajuda Atualizável: Passo a Passo)</span><span class="sxs-lookup"><span data-stu-id="6bea8-104">Authoring Updatable Help: Step-by-Step</span></span>

<span data-ttu-id="6bea8-105">Ajuda atualizável foi concebida para utilizadores finais, mas também proporciona significativos benefícios para os autores de módulo e gravadores de ajuda, incluindo a capacidade de adicionar conteúdo, corrija os erros, fornecem em várias culturas de interface do Usuário e respondem a comentários de utilizador e de pedidos, há muito tempo após o módulo foi enviada.</span><span class="sxs-lookup"><span data-stu-id="6bea8-105">Updatable Help is designed for end-users, but it also provides significant benefits to module authors and help writers, including the ability to add content, fix errors, deliver in multiple UI cultures, and respond to user comments and requests, long after the module has shipped.</span></span> <span data-ttu-id="6bea8-106">Este tópico explica como empacotar e arquivos de ajuda de carregamento para que os utilizadores podem transferir e instalá-los utilizando o [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span><span class="sxs-lookup"><span data-stu-id="6bea8-106">This topic explains how you package and upload help files so that users can download and install them by using the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="6bea8-107">Os passos seguintes fornecem uma visão geral do processo de apoio ajuda Atualizável.</span><span class="sxs-lookup"><span data-stu-id="6bea8-107">The following steps provide an overview of the process of supporting Updatable Help.</span></span>

### <a name="step-1-find-an-internet-site-for-your-help-files"></a><span data-ttu-id="6bea8-108">Passo 1: Localizar um site da Internet para os seus ficheiros de ajuda</span><span class="sxs-lookup"><span data-stu-id="6bea8-108">Step 1: Find an Internet site for your help files</span></span>

<span data-ttu-id="6bea8-109">A primeira etapa na criação de ajuda atualizável é encontrar uma localização de Internet para arquivos de ajuda do seu módulo.</span><span class="sxs-lookup"><span data-stu-id="6bea8-109">The first step in creating updatable help is to find an Internet location for your module's help files.</span></span> <span data-ttu-id="6bea8-110">Na verdade, pode usar duas localizações diferentes.</span><span class="sxs-lookup"><span data-stu-id="6bea8-110">Actually, you can use two different locations.</span></span> <span data-ttu-id="6bea8-111">Pode manter o arquivo de informações de ajuda do seu módulo (HelpInfo XML - descritos abaixo) num local de Internet e os arquivos CAB conteúdos da ajuda em outro local de Internet.</span><span class="sxs-lookup"><span data-stu-id="6bea8-111">You can keep your module's help information file (HelpInfo XML - described below) at one Internet location and the help content CAB files at another Internet location.</span></span> <span data-ttu-id="6bea8-112">Todos os conteúdos CAB arquivos de ajuda para um módulo tem de ser na mesma localização.</span><span class="sxs-lookup"><span data-stu-id="6bea8-112">All help content CAB files for a module must be in the same location.</span></span> <span data-ttu-id="6bea8-113">Pode colocar arquivos CAB conteúdos de ajuda para módulos diferentes na mesma localização.</span><span class="sxs-lookup"><span data-stu-id="6bea8-113">You can place help content CAB files for different modules in the same location.</span></span>

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a><span data-ttu-id="6bea8-114">Passo 2: Adicionar uma chave de HelpInfoURI a seu manifesto de módulo</span><span class="sxs-lookup"><span data-stu-id="6bea8-114">Step 2: Add a HelpInfoURI key to your module manifest</span></span>

<span data-ttu-id="6bea8-115">Adicionar uma **HelpInfoURI** chave para o manifesto de módulo.</span><span class="sxs-lookup"><span data-stu-id="6bea8-115">Add a **HelpInfoURI** key to your module manifest.</span></span> <span data-ttu-id="6bea8-116">O valor da chave é o identificador URI (Uniform Resource) da localização do ficheiro de informações HelpInfo XML para seu módulo.</span><span class="sxs-lookup"><span data-stu-id="6bea8-116">The value of the key is the Uniform Resource Identifier (URI) of the location of the HelpInfo XML information file for your module.</span></span> <span data-ttu-id="6bea8-117">Para segurança, o endereço tem de começar com "http" ou "https".</span><span class="sxs-lookup"><span data-stu-id="6bea8-117">For security, the address must begin with "http" or "https".</span></span> <span data-ttu-id="6bea8-118">O URI deve especificar uma localização de Internet, mas não tem de incluir o nome do ficheiro XML de HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="6bea8-118">The URI should specify an Internet location, but must not include the HelpInfo XML file name.</span></span>

<span data-ttu-id="6bea8-119">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="6bea8-119">For example:</span></span>

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a><span data-ttu-id="6bea8-120">Passo 3: Crie um ficheiro XML de HelpInfo</span><span class="sxs-lookup"><span data-stu-id="6bea8-120">Step 3: Create a HelpInfo XML file</span></span>

<span data-ttu-id="6bea8-121">O ficheiro de informações HelpInfo XML contém o URI da localização de Internet de seus arquivos de ajuda e números de versão dos arquivos de ajuda mais recentes para seu módulo em cada cultura da interface do Usuário suportado.</span><span class="sxs-lookup"><span data-stu-id="6bea8-121">The HelpInfo XML information file contains the URI of the Internet location of your help files and the version numbers of the newest help files for your module in each supported UI culture.</span></span> <span data-ttu-id="6bea8-122">Cada módulo Windows PowerShell possui um arquivo XML de HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="6bea8-122">Every Windows PowerShell module has one HelpInfo XML file.</span></span> <span data-ttu-id="6bea8-123">Quando atualizar seus arquivos de ajuda, editar ou substituir o ficheiro XML de HelpInfo; não adicionar outro.</span><span class="sxs-lookup"><span data-stu-id="6bea8-123">When you update your help files, you edit or replace the HelpInfo XML file; you do not add another one.</span></span> <span data-ttu-id="6bea8-124">Para obter mais informações, consulte [como criar um ficheiro XML de HelpInfo](./how-to-create-a-helpinfo-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="6bea8-124">For more information, see [How to Create a HelpInfo XML File](./how-to-create-a-helpinfo-xml-file.md).</span></span>

### <a name="step-4-sign-your-help-files"></a><span data-ttu-id="6bea8-125">Passo 4: Assinar seus arquivos de ajuda</span><span class="sxs-lookup"><span data-stu-id="6bea8-125">Step 4: Sign your help files</span></span>

<span data-ttu-id="6bea8-126">Assinaturas digitais não são necessárias, mas eles são uma recomendação de melhores práticas, sempre que estão a partilhar ficheiros.</span><span class="sxs-lookup"><span data-stu-id="6bea8-126">Digital signatures are not required, but they are a best-practice recommendation whenever you are sharing files.</span></span>

### <a name="step-5-create-cab-files"></a><span data-ttu-id="6bea8-127">Passo 5: Criar ficheiros CAB</span><span class="sxs-lookup"><span data-stu-id="6bea8-127">Step 5: Create CAB files</span></span>

<span data-ttu-id="6bea8-128">Utilizar uma ferramenta que cria arquivos de Gabinete (. cab), como MakeCab.exe, para criar um. Arquivo CAB que contém os ficheiros de ajuda para seu módulo.</span><span class="sxs-lookup"><span data-stu-id="6bea8-128">Use a tool that creates cabinet (.cab) files, such as MakeCab.exe, to create a .CAB file that contains the help files for your module.</span></span> <span data-ttu-id="6bea8-129">Crie um arquivo CAB separado para os arquivos da ajuda em cada cultura da interface do Usuário suportada.</span><span class="sxs-lookup"><span data-stu-id="6bea8-129">Create a separate CAB file for the help files in each supported UI culture.</span></span> <span data-ttu-id="6bea8-130">Para obter mais informações, consulte [como preparar Atualizável CAB arquivos de ajuda do](./how-to-prepare-updatable-help-cab-files.md).</span><span class="sxs-lookup"><span data-stu-id="6bea8-130">For more information, see [How to Prepare Updatable Help CAB Files](./how-to-prepare-updatable-help-cab-files.md).</span></span>

### <a name="step-6-upload-your-files"></a><span data-ttu-id="6bea8-131">Passo 6: Carregar os ficheiros</span><span class="sxs-lookup"><span data-stu-id="6bea8-131">Step 6: Upload your files</span></span>

<span data-ttu-id="6bea8-132">Para publicar os arquivos de ajuda de novos ou atualizados, carregue os ficheiros CAB para a localização de Internet que é especificada pela **HelpContentUri** elemento no arquivo XML de HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="6bea8-132">To publish new or updated help files, upload the CAB files to the Internet location that is specified by the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="6bea8-133">Em seguida, carregue o ficheiro XML de HelpInfo para a localização de Internet que é especificada pelo valor da **HelpInfoUri** chave no manifesto do módulo.</span><span class="sxs-lookup"><span data-stu-id="6bea8-133">Then, upload the HelpInfo XML file to the Internet location that is specified by the value of the **HelpInfoUri** key in the module manifest.</span></span>
