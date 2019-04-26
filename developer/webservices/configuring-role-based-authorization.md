---
title: Configurar a autorização baseada em funções | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2933a6ca-fe92-4ba2-97ee-ef0f0d5fdfcf
caps.latest.revision: 8
ms.openlocfilehash: b73284adb4bf228510bf8134aa4c6a10561b7ea2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080684"
---
# <a name="configuring-role-based-authorization"></a><span data-ttu-id="83baa-102">Configuring Role-based Authorization (Configurar a Autenticação Baseada em Funções)</span><span class="sxs-lookup"><span data-stu-id="83baa-102">Configuring Role-based Authorization</span></span>

<span data-ttu-id="83baa-103">Este tópico explica como configurar a política de autorização baseada em funções para a implementação de exemplo da [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) interface descrito em [implementação personalizada Autorização para a extensão de gestão do IIS de OData](./implementing-custom-authorization-for-a-management-odata-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="83baa-103">This topic demonstrates how to configure the role-based authorization policy for the sample implementation of the [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) interface described in [Implementing Custom Authorization for Management OData IIS Extension](./implementing-custom-authorization-for-a-management-odata-web-service.md).</span></span>

<span data-ttu-id="83baa-104">Neste exemplo, configurará um arquivo XML que é usado pelo aplicativo de OData da gestão de exemplo para definir a política de autorização.</span><span class="sxs-lookup"><span data-stu-id="83baa-104">In this example, you will configure an XML file that is used by the sample Management OData application to define the authorization policy.</span></span> <span data-ttu-id="83baa-105">Irá criar duas funções e associar diferentes módulos do Windows PowerShell que contêm os fluxos de trabalho com essas funções.</span><span class="sxs-lookup"><span data-stu-id="83baa-105">You will create two roles and associate different Windows PowerShell modules that contain workflows with those roles.</span></span> <span data-ttu-id="83baa-106">O esquema que define o arquivo XML está listado na [esquema de configuração de autorização baseada em funções](./role-based-authorization-configuration-schema.md).</span><span class="sxs-lookup"><span data-stu-id="83baa-106">The schema that defines the XML file is listed at [Role-Based Authorization Configuration Schema](./role-based-authorization-configuration-schema.md).</span></span>

## <a name="modifying-the-rbacconfigurationxml-file"></a><span data-ttu-id="83baa-107">Modificar o arquivo RBacConfiguration.xml</span><span class="sxs-lookup"><span data-stu-id="83baa-107">Modifying the RBacConfiguration.xml File</span></span>

<span data-ttu-id="83baa-108">Esse arquivo define a política de autorização da aplicação.</span><span class="sxs-lookup"><span data-stu-id="83baa-108">This file defines the authorization policy for the application.</span></span> <span data-ttu-id="83baa-109">As funções são definidas usando `Group` nós.</span><span class="sxs-lookup"><span data-stu-id="83baa-109">Roles are defined by using `Group` nodes.</span></span> <span data-ttu-id="83baa-110">A `Group` nó define os comandos do Windows PowerShell que os utilizadores atribuídos a esse grupo podem executar.</span><span class="sxs-lookup"><span data-stu-id="83baa-110">A `Group` node defines the Windows PowerShell commands that users assigned to that group can run.</span></span> <span data-ttu-id="83baa-111">Os utilizadores são atribuídos a grupos com o `User` nós.</span><span class="sxs-lookup"><span data-stu-id="83baa-111">Users are assigned to groups by using `User` nodes.</span></span>

<span data-ttu-id="83baa-112">Estes exemplos, vai adicionar um módulo para o administrador `Group` nó, e adicionar um utilizador a cada grupo.</span><span class="sxs-lookup"><span data-stu-id="83baa-112">In these examples, you will add a module to the Administrator `Group` node, and add a user to each group.</span></span>

#### <a name="adding-a-module-to-a-group-node"></a><span data-ttu-id="83baa-113">Adicionar um módulo para um nó do grupo</span><span class="sxs-lookup"><span data-stu-id="83baa-113">Adding a Module to a Group Node</span></span>

1. <span data-ttu-id="83baa-114">Crie um ficheiro denominado **RBacConfiguration.xml** num editor de texto.</span><span class="sxs-lookup"><span data-stu-id="83baa-114">Create a file named **RBacConfiguration.xml** in a text editor.</span></span> <span data-ttu-id="83baa-115">Esse arquivo deverá ser guardado no diretório do aplicativo principal para o seu serviço web.</span><span class="sxs-lookup"><span data-stu-id="83baa-115">This file should be saved to the main application directory for your web service.</span></span> <span data-ttu-id="83baa-116">Insira o seguinte texto no ficheiro.</span><span class="sxs-lookup"><span data-stu-id="83baa-116">Insert the following text in the file.</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <RbacConfiguration>
     <Groups>
       <!--Group consists of the following:
         Name:  Name of the group
         UserName (Optional): Windows Identity user name
         Password (Optional): Password of the Windows user name
         DomainName (Optional): Domain for the user. For local machine account either do not include them or give the machine name. Do not give empty string
         MapIncomingUser (Optional): Boolean value indicating whether to execute cmdlet in the context of network client.

         User credentials and MapIncomingUser=true are exclusive.
       -->
       <Group Name="NonAdminGroup" MapIncomingUser="true">
         <Cmdlets>
           <Cmdlet>Get-Service</Cmdlet>
           <Cmdlet>Set-Service</Cmdlet>
           <Cmdlet>Get-Process</Cmdlet>
           <Cmdlet>Get-Item</Cmdlet>
           <Cmdlet>New-Item</Cmdlet>
           <Cmdlet>Get-Command</Cmdlet>
           <Cmdlet>ConvertTo-Xml</Cmdlet>
           <Cmdlet>ConvertTo-Json</Cmdlet>
           <Cmdlet>ConvertFrom-Json</Cmdlet>
         </Cmdlets>
       </Group>
       <Group Name="AdminGroup" MapIncomingUser="true">
         <Cmdlets>
           <Cmdlet>Get-Service</Cmdlet>
           <Cmdlet>Get-Process</Cmdlet>
           <Cmdlet>Get-Item</Cmdlet>
           <Cmdlet>New-Item</Cmdlet>
           <Cmdlet>Get-Command</Cmdlet>
           <Cmdlet>ConvertTo-Xml</Cmdlet>
           <Cmdlet>ConvertTo-Json</Cmdlet>
           <Cmdlet>ConvertFrom-Json</Cmdlet>
         </Cmdlets>
         <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
       </Group>
     </Groups>
     <Users>
       <!-- User consists of the following :
         Name: Name of the user. If a user is from a cer
         AuthenticationType: Authentication type used.
         DomainName (Optional): Domain for the user
       -->
       <User Name="localNonAdmin" AuthenticationType="Basic" GroupName="NonAdminGroup" />
       <User Name="localAdmin" AuthenticationType="Basic" GroupName="AdminGroup" />
     </Users>
   </RbacConfiguration>
   ```

2. <span data-ttu-id="83baa-117">O ficheiro contém dois `Group` nós.</span><span class="sxs-lookup"><span data-stu-id="83baa-117">The file contains two `Group` nodes.</span></span> <span data-ttu-id="83baa-118">Representam as duas funções utilizadas neste exemplo, o `NonAdminGroup` e o `AdminGroup` funções.</span><span class="sxs-lookup"><span data-stu-id="83baa-118">These represent the two roles used in this example, the `NonAdminGroup` and the `AdminGroup` roles.</span></span>

   <span data-ttu-id="83baa-119">Imediatamente após o fecho `Cmdlets` marca na primeira `Group` nó, adicione o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="83baa-119">Directly after the closing `Cmdlets` tag in the first `Group` node, add the following XML:</span></span>

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a><span data-ttu-id="83baa-120">A adição de um utilizador a um nó do grupo</span><span class="sxs-lookup"><span data-stu-id="83baa-120">Adding a User to a Group Node</span></span>

1. <span data-ttu-id="83baa-121">Abra o **RBacConfiguration.xml** ficheiro num editor de texto.</span><span class="sxs-lookup"><span data-stu-id="83baa-121">Open the **RBacConfiguration.xml** file in a text editor.</span></span> <span data-ttu-id="83baa-122">Este ficheiro está localizado na pasta c:\\\inetpub\wwwroot\Modata caso não tenha alterado o nome do ponto final antes da instalação.</span><span class="sxs-lookup"><span data-stu-id="83baa-122">This file is located in the folder C:\\\inetpub\wwwroot\Modata  if you did not change the endpoint name before installation.</span></span>

2. <span data-ttu-id="83baa-123">Imediatamente após a marca de fechamento no `Users` nó, adicione o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="83baa-123">Directly after the closing tag in the `Users` node, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. <span data-ttu-id="83baa-124">Diretamente depois do XML é adicionado no passo anterior, adicione o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="83baa-124">Directly after the XML added in the previous step, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```