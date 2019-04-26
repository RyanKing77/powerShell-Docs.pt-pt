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
# <a name="configuring-role-based-authorization"></a>Configuring Role-based Authorization (Configurar a Autenticação Baseada em Funções)

Este tópico explica como configurar a política de autorização baseada em funções para a implementação de exemplo da [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) interface descrito em [implementação personalizada Autorização para a extensão de gestão do IIS de OData](./implementing-custom-authorization-for-a-management-odata-web-service.md).

Neste exemplo, configurará um arquivo XML que é usado pelo aplicativo de OData da gestão de exemplo para definir a política de autorização. Irá criar duas funções e associar diferentes módulos do Windows PowerShell que contêm os fluxos de trabalho com essas funções. O esquema que define o arquivo XML está listado na [esquema de configuração de autorização baseada em funções](./role-based-authorization-configuration-schema.md).

## <a name="modifying-the-rbacconfigurationxml-file"></a>Modificar o arquivo RBacConfiguration.xml

Esse arquivo define a política de autorização da aplicação. As funções são definidas usando `Group` nós. A `Group` nó define os comandos do Windows PowerShell que os utilizadores atribuídos a esse grupo podem executar. Os utilizadores são atribuídos a grupos com o `User` nós.

Estes exemplos, vai adicionar um módulo para o administrador `Group` nó, e adicionar um utilizador a cada grupo.

#### <a name="adding-a-module-to-a-group-node"></a>Adicionar um módulo para um nó do grupo

1. Crie um ficheiro denominado **RBacConfiguration.xml** num editor de texto. Esse arquivo deverá ser guardado no diretório do aplicativo principal para o seu serviço web. Insira o seguinte texto no ficheiro.

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

2. O ficheiro contém dois `Group` nós. Representam as duas funções utilizadas neste exemplo, o `NonAdminGroup` e o `AdminGroup` funções.

   Imediatamente após o fecho `Cmdlets` marca na primeira `Group` nó, adicione o seguinte XML:

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a>A adição de um utilizador a um nó do grupo

1. Abra o **RBacConfiguration.xml** ficheiro num editor de texto. Este ficheiro está localizado na pasta c:\\\inetpub\wwwroot\Modata caso não tenha alterado o nome do ponto final antes da instalação.

2. Imediatamente após a marca de fechamento no `Users` nó, adicione o seguinte XML:

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. Diretamente depois do XML é adicionado no passo anterior, adicione o seguinte XML:

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```