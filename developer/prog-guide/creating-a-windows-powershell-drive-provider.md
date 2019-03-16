---
title: Criar um fornecedor de unidade do PowerShell do Windows | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- drive providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], drive provider
- drives [PowerShell Programmer's Guide]
ms.assetid: 2b446841-6616-4720-9ff8-50801d7576ed
caps.latest.revision: 6
ms.openlocfilehash: 174d3a6860790295e1b73f32d9c1bad46b653917
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055655"
---
# <a name="creating-a-windows-powershell-drive-provider"></a>Creating a Windows PowerShell Drive Provider (Criar um Fornecedor de Unidades do Windows PowerShell)

Este tópico descreve como criar um fornecedor de unidade do Windows PowerShell que fornece uma forma de acessar um arquivo de dados por meio de uma unidade do Windows PowerShell. Este tipo de fornecedor também é referido como fornecedores de unidade do Windows PowerShell. As unidades do Windows PowerShell utilizadas pelo fornecedor de fornecem os meios para ligar ao arquivo de dados.

O fornecedor de unidade do Windows PowerShell descrito aqui fornece acesso a uma base de dados do Microsoft Access. Para este fornecedor, a unidade do Windows PowerShell representa a base de dados (é possível adicionar qualquer número de unidades para um fornecedor de unidade), os contentores de nível superior da unidade representam as tabelas na base de dados e os itens dos contentores representam as linhas as tabelas.

Aqui está uma lista das secções seguintes deste tópico. Se não estiver familiarizado com a escrita de um fornecedor de unidade do Windows PowerShell, leia estas secções pela ordem em que aparecem. No entanto, se estiver familiarizado com a escrita de um fornecedor de unidade, vá diretamente para as informações de que precisa.

- [Definir a classe de fornecedor do PowerShell do Windows](#Defining-the-Windows-PowerShell-Provider-Class)

- [Definir funcionalidade de Base](#Defining-Base-Functionality)

- [A criar informações de estado de unidade](#Creating-Drive-State-Information)

- [Criar uma unidade](#Creating-a-Drive)

- [Anexar parâmetros dinâmicos para NewDrive](#Attaching-Dynamic-Parameters-to-NewDrive)

- [Remover uma unidade](#Removing-a-Drive)

- [Unidades de inicialização padrão](#Initializing-Default-Drives)

- [Exemplo de código](#Code-Sample)

- [Teste o fornecedor de unidade do PowerShell do Windows](#Testing-the-Windows-PowerShell-Drive-Provider)

## <a name="defining-the-windows-powershell-provider-class"></a>Definir a classe de fornecedor do PowerShell do Windows

O fornecedor de unidade tem de definir uma classe do .NET que deriva de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe base. Segue-se a definição de classe para este fornecedor de unidade:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

Tenha em atenção que neste exemplo, o [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atributo especifica um nome amigável para o fornecedor e as capacidades específicas do Windows PowerShell que o fornecedor expõe o tempo de execução do Windows PowerShell durante o processamento do comando. Os valores possíveis para as funcionalidades de fornecedor são definidos pelos [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeração. Este fornecedor de unidade não suporta qualquer um desses recursos.

## <a name="defining-base-functionality"></a>Definir funcionalidade de Base

Conforme descrito em [Design Windows PowerShell Fornecedor_de_e](./designing-your-windows-powershell-provider.md), o [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe deriva a [ System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe que define os métodos necessários para inicializar e uninitializing o fornecedor de base. Para implementar a funcionalidade para adicionar informações de inicialização de específico da sessão e para liberar os recursos que são utilizados pelo fornecedor, veja [criar um fornecedor de PowerShell básica do Windows](./creating-a-basic-windows-powershell-provider.md). No entanto, a maioria dos provedores de (incluindo o fornecedor descrito aqui) pode utilizar a implementação padrão dessa funcionalidade fornecida pelo Windows PowerShell.

## <a name="creating-drive-state-information"></a>A criar informações de estado de unidade

Todos os fornecedores de Windows PowerShell são considerados sem monitoração de estado, que significa que o seu fornecedor de unidade necessita criar qualquer informação de estado que é necessária para o tempo de execução do Windows PowerShell ao chamar o fornecedor.

Para este fornecedor de unidade, informações de estado incluem a ligação à base de dados que é mantido como parte das informações da unidade. Eis o código que mostra como essas informações são armazenadas no [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) objeto que descreve a unidade:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a>Criar uma unidade

Para permitir que o tempo de execução do Windows PowerShell criar uma unidade, o fornecedor de unidade tem de implementar o [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) método. O código a seguir mostra a implementação do [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) método para este fornecedor de unidade:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

A substituição deste método deve fazer o seguinte:

- Certifique-se de que o [System.Management.Automation.PSDriveinfo.Root*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) membro existe e que pode ser feita uma conexão ao arquivo de dados.

- Criar uma unidade e preencher o membro de ligação, no support do `New-PSDrive` cmdlet.

- Validar a [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) objeto para a unidade proposto.

- Modificar a [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) de objeto que descreve a unidade com quaisquer informações de fiabilidade ou desempenho obrigatório ou fornecer dados adicionais para chamadores com a unidade.

- Processar falhas utilizando o [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) método e em seguida, regresse `null`.

  Este método devolve a informação da unidade que foi passada para o método ou uma versão específica do fornecedor do mesmo.

## <a name="attaching-dynamic-parameters-to-newdrive"></a>Anexar parâmetros dinâmicos para NewDrive

O `New-PSDrive` cmdlet suportado pelo seu fornecedor de unidade pode exigir parâmetros adicionais. Para anexar estes parâmetros dinâmicos para o cmdlet, o provedor implementa a [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) método. Esse método retorna um objeto com propriedades e campos com análise atributos semelhantes a uma classe cmdlet ou uma [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto.

Este fornecedor de unidade não substitui este método. No entanto, o código seguinte mostra a implementação padrão deste método:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a>Remover uma unidade

Para fechar a ligação de base de dados, o fornecedor de unidade tem de implementar o [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) método. Este método fecha a ligação para a unidade depois de limpar qualquer informação específica do fornecedor.

O código a seguir mostra a implementação do [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) método para este fornecedor de unidade:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

Se a unidade pode ser removida, o método deve retornar as informações transmitidas para o método por meio do `drive` parâmetro. Se não é possível remover a unidade, o método deve escrever uma exceção e, em seguida, retornar `null`. Se o seu fornecedor não substitui este método, a implementação padrão deste método devolve apenas as informações da unidade passadas como entrada.

## <a name="initializing-default-drives"></a>Unidades de inicialização padrão

Sua implementa de fornecedor de unidade a [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) método para montar unidades. Por exemplo, o fornecedor do Active Directory pode montar uma unidade de disco para o contexto de nomenclatura, se o computador estiver associado a um domínio predefinido.

Esse método retorna uma coleção de informações da unidade sobre as unidades de inicializado, ou uma coleção vazia. A chamada para esse método é feita após as chamadas de tempo de execução do Windows PowerShell a [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) método para inicializar o fornecedor.

Este fornecedor de unidade não substitui a [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) método. No entanto, o código seguinte mostra a implementação padrão, que retorna uma coleção de unidade vazio:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a>Coisas a serem lembrados sobre a implementação InitializeDefaultDrives

Todos os fornecedores de unidade devem montar uma unidade de raiz para ajudar o utilizador com a capacidade de deteção. Na unidade raiz pode listar localizações que servem como raízes para outras unidades montadas. Por exemplo, o fornecedor do Active Directory pode criar uma unidade que lista os contextos de nomenclatura encontrados no `namingContext` atributos na raiz do ambiente do sistema distribuído (DSE). Isto ajuda os utilizadores a descobrir os pontos de montagem para outras unidades.

## <a name="code-sample"></a>Exemplo de código

Para o código de exemplo completo, consulte [exemplo de código AccessDbProviderSample02](./accessdbprovidersample02-code-sample.md).

## <a name="testing-the-windows-powershell-drive-provider"></a>Teste o fornecedor de unidade do PowerShell do Windows

Quando o seu fornecedor de Windows PowerShell foi registado com o Windows PowerShell, pode testá-lo ao executar os cmdlets suportados na linha de comando, incluindo quaisquer cmdlets disponibilizados pela derivação. Vamos testar o fornecedor de unidade de exemplo.

1. Execute o `Get-PSProvider` cmdlet para obter a lista de fornecedores para garantir que o fornecedor de unidade AccessDB está presente:

   **PS> `Get-PSProvider`**

   É apresentado o seguinte resultado:

   ```output
   Name                 Capabilities                  Drives
   ----                 ------------                  ------
   AccessDB             None                          {}
   Alias                ShouldProcess                 {Alias}
   Environment          ShouldProcess                 {Env}
   FileSystem           Filter, ShouldProcess         {C, Z}
   Function             ShouldProcess                 {function}
   Registry             ShouldProcess                 {HKLM, HKCU}
   ```

2. Certifique-se de que um nome de servidor de base de dados (DSN) existe para a base de dados ao aceder a **origens de dados** parte a **ferramentas administrativas** para o sistema operativo. Na **DSN de utilizador** tabela, faça duplo clique em **base de dados do MS Access** e adicionar o caminho de unidade C:\ps\northwind.mdb.

3. Crie uma nova unidade usando o provedor de unidade de exemplo:

   **PS > novo psdrive-nome mydb-raiz c:\ps\northwind.mdb - psprovider AccessDb**

   É apresentado o seguinte resultado:

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. Valide a ligação. Como a ligação é definida como um membro da unidade, pode verificar com o cmdlet Get-PDDrive.

   > [!NOTE]
   > O utilizador ainda não é possível interagir com o provedor como uma unidade, como o fornecedor tem de funcionalidade de contentor para a interação. Para obter mais informações, consulte [criar um fornecedor de contentor do Windows PowerShell](./creating-a-windows-powershell-container-provider.md).

   **PS > .connection (get-psdrive mydb)**

   É apresentado o seguinte resultado:

   ```output
   ConnectionString  : Driver={Microsoft Access Driver (*.mdb)};DBQ=c:\ps\northwind.mdb
   ConnectionTimeout : 15
   Database          : c:\ps\northwind
   DataSource        : ACCESS
   ServerVersion     : 04.00.0000
   Driver            : odbcjt32.dll
   State             : Open
   Site              :
   Container         :
   ```

5. Remover a unidade e sair da shell:

   **PS > remove-psdrive mydb**

   **PS > Sair**

## <a name="see-also"></a>Veja Também

[Criar provedores do Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Estruturar o seu fornecedor do Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Criar um fornecedor de PowerShell do Windows básica](./creating-a-basic-windows-powershell-provider.md)