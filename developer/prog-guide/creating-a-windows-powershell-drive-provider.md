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
ms.openlocfilehash: d1546ab0b0e6b5502f35c92c01ce148211c53db2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846670"
---
# <a name="creating-a-windows-powershell-drive-provider"></a><span data-ttu-id="51a60-102">Creating a Windows PowerShell Drive Provider (Criar um Fornecedor de Unidades do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="51a60-102">Creating a Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="51a60-103">Este tópico descreve como criar um fornecedor de unidade do Windows PowerShell que fornece uma forma de acessar um arquivo de dados por meio de uma unidade do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="51a60-103">This topic describes how to create a Windows PowerShell drive provider that provides a way to access a data store through a Windows PowerShell drive.</span></span> <span data-ttu-id="51a60-104">Este tipo de fornecedor também é referido como fornecedores de unidade do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="51a60-104">This type of provider is also referred to as Windows PowerShell drive providers.</span></span> <span data-ttu-id="51a60-105">As unidades do Windows PowerShell utilizadas pelo fornecedor de fornecem os meios para ligar ao arquivo de dados.</span><span class="sxs-lookup"><span data-stu-id="51a60-105">The Windows PowerShell drives used by the provider provide the means to connect to the data store.</span></span>

<span data-ttu-id="51a60-106">O fornecedor de unidade do Windows PowerShell descrito aqui fornece acesso a uma base de dados do Microsoft Access.</span><span class="sxs-lookup"><span data-stu-id="51a60-106">The Windows PowerShell drive provider described here provides access to a Microsoft Access database.</span></span> <span data-ttu-id="51a60-107">Para este fornecedor, a unidade do Windows PowerShell representa a base de dados (é possível adicionar qualquer número de unidades para um fornecedor de unidade), os contentores de nível superior da unidade representam as tabelas na base de dados e os itens dos contentores representam as linhas as tabelas.</span><span class="sxs-lookup"><span data-stu-id="51a60-107">For this provider, the Windows PowerShell drive represents the database (it is possible to add any number of drives to a drive provider), the top-level containers of the drive represent the tables in the database, and the items of the containers represent the rows in the tables.</span></span>

<span data-ttu-id="51a60-108">Aqui está uma lista das secções seguintes deste tópico.</span><span class="sxs-lookup"><span data-stu-id="51a60-108">Here is a list of the sections in this topic.</span></span> <span data-ttu-id="51a60-109">Se não estiver familiarizado com a escrita de um fornecedor de unidade do Windows PowerShell, leia estas secções pela ordem em que aparecem.</span><span class="sxs-lookup"><span data-stu-id="51a60-109">If you are unfamiliar with writing a Windows PowerShell drive provider, read these sections in the order that they appear.</span></span> <span data-ttu-id="51a60-110">No entanto, se estiver familiarizado com a escrita de um fornecedor de unidade, vá diretamente para as informações de que precisa.</span><span class="sxs-lookup"><span data-stu-id="51a60-110">However, if you are familiar with writing a drive provider, please go directly to the information that you need.</span></span>

- [<span data-ttu-id="51a60-111">Definir a classe de fornecedor do PowerShell do Windows</span><span class="sxs-lookup"><span data-stu-id="51a60-111">Defining the Windows PowerShell Provider Class</span></span>](#Defining-the-Windows-PowerShell-Provider-Class)

- [<span data-ttu-id="51a60-112">Definir funcionalidade de Base</span><span class="sxs-lookup"><span data-stu-id="51a60-112">Defining Base Functionality</span></span>](#Defining-Base-Functionality)

- [<span data-ttu-id="51a60-113">A criar informações de estado de unidade</span><span class="sxs-lookup"><span data-stu-id="51a60-113">Creating Drive State Information</span></span>](#Creating-Drive-State-Information)

- [<span data-ttu-id="51a60-114">Criar uma unidade</span><span class="sxs-lookup"><span data-stu-id="51a60-114">Creating a Drive</span></span>](#Creating-a-Drive)

- [<span data-ttu-id="51a60-115">Anexar parâmetros dinâmicos para NewDrive</span><span class="sxs-lookup"><span data-stu-id="51a60-115">Attaching Dynamic Parameters to NewDrive</span></span>](#Attaching-Dynamic-Parameters-to-NewDrive)

- [<span data-ttu-id="51a60-116">Remover uma unidade</span><span class="sxs-lookup"><span data-stu-id="51a60-116">Removing a Drive</span></span>](#Removing-a-Drive)

- [<span data-ttu-id="51a60-117">Unidades de inicialização padrão</span><span class="sxs-lookup"><span data-stu-id="51a60-117">Initializing Default Drives</span></span>](#Initializing-Default-Drives)

- [<span data-ttu-id="51a60-118">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="51a60-118">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="51a60-119">Teste o fornecedor de unidade do PowerShell do Windows</span><span class="sxs-lookup"><span data-stu-id="51a60-119">Testing the Windows PowerShell Drive Provider</span></span>](#Testing-the-Windows-PowerShell-Drive-Provider)

## <a name="defining-the-windows-powershell-provider-class"></a><span data-ttu-id="51a60-120">Definir a classe de fornecedor do PowerShell do Windows</span><span class="sxs-lookup"><span data-stu-id="51a60-120">Defining the Windows PowerShell Provider Class</span></span>

<span data-ttu-id="51a60-121">O fornecedor de unidade tem de definir uma classe do .NET que deriva de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe base.</span><span class="sxs-lookup"><span data-stu-id="51a60-121">Your drive provider must define a .NET class that derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="51a60-122">Segue-se a definição de classe para este fornecedor de unidade:</span><span class="sxs-lookup"><span data-stu-id="51a60-122">Here is the class definition for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

<span data-ttu-id="51a60-123">Tenha em atenção que neste exemplo, o [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atributo especifica um nome amigável para o fornecedor e as capacidades específicas do Windows PowerShell que o fornecedor expõe o tempo de execução do Windows PowerShell durante o processamento do comando.</span><span class="sxs-lookup"><span data-stu-id="51a60-123">Notice that in this example, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute specifies a user-friendly name for the provider and the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="51a60-124">Os valores possíveis para as funcionalidades de fornecedor são definidos pelos [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeração.</span><span class="sxs-lookup"><span data-stu-id="51a60-124">The possible values for the provider capabilities are defined by the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="51a60-125">Este fornecedor de unidade não suporta qualquer um desses recursos.</span><span class="sxs-lookup"><span data-stu-id="51a60-125">This drive provider does not support any of these capabilities.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="51a60-126">Definir funcionalidade de Base</span><span class="sxs-lookup"><span data-stu-id="51a60-126">Defining Base Functionality</span></span>

<span data-ttu-id="51a60-127">Conforme descrito em [Design Windows PowerShell Fornecedor_de_e](./designing-your-windows-powershell-provider.md), o [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe deriva a [ System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe que define os métodos necessários para inicializar e uninitializing o fornecedor de base.</span><span class="sxs-lookup"><span data-stu-id="51a60-127">As described in [Design Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class derives from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class that defines the methods needed for initializing and uninitializing the provider.</span></span> <span data-ttu-id="51a60-128">Para implementar a funcionalidade para adicionar informações de inicialização de específico da sessão e para liberar os recursos que são utilizados pelo fornecedor, veja [criar um fornecedor de PowerShell básica do Windows](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="51a60-128">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="51a60-129">No entanto, a maioria dos provedores de (incluindo o fornecedor descrito aqui) pode utilizar a implementação padrão dessa funcionalidade fornecida pelo Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="51a60-129">However, most providers (including the provider described here) can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

## <a name="creating-drive-state-information"></a><span data-ttu-id="51a60-130">A criar informações de estado de unidade</span><span class="sxs-lookup"><span data-stu-id="51a60-130">Creating Drive State Information</span></span>

<span data-ttu-id="51a60-131">Todos os fornecedores de Windows PowerShell são considerados sem monitoração de estado, que significa que o seu fornecedor de unidade necessita criar qualquer informação de estado que é necessária para o tempo de execução do Windows PowerShell ao chamar o fornecedor.</span><span class="sxs-lookup"><span data-stu-id="51a60-131">All Windows PowerShell providers are considered stateless, which means that your drive provider needs to create any state information that is needed by the Windows PowerShell runtime when it calls your provider.</span></span>

<span data-ttu-id="51a60-132">Para este fornecedor de unidade, informações de estado incluem a ligação à base de dados que é mantido como parte das informações da unidade.</span><span class="sxs-lookup"><span data-stu-id="51a60-132">For this drive provider, state information includes the connection to the database that is kept as part of the drive information.</span></span> <span data-ttu-id="51a60-133">Eis o código que mostra como essas informações são armazenadas no [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) objeto que descreve a unidade:</span><span class="sxs-lookup"><span data-stu-id="51a60-133">Here is code that shows how this information is stored in the [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a><span data-ttu-id="51a60-134">Criar uma unidade</span><span class="sxs-lookup"><span data-stu-id="51a60-134">Creating a Drive</span></span>

<span data-ttu-id="51a60-135">Para permitir que o tempo de execução do Windows PowerShell criar uma unidade, o fornecedor de unidade tem de implementar o [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) método.</span><span class="sxs-lookup"><span data-stu-id="51a60-135">To allow the Windows PowerShell runtime to create a drive, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method.</span></span> <span data-ttu-id="51a60-136">O código a seguir mostra a implementação do [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) método para este fornecedor de unidade:</span><span class="sxs-lookup"><span data-stu-id="51a60-136">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

<span data-ttu-id="51a60-137">A substituição deste método deve fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="51a60-137">Your override of this method should do the following:</span></span>

- <span data-ttu-id="51a60-138">Certifique-se de que o [System.Management.Automation.Psdriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) membro existe e que pode ser feita uma conexão ao arquivo de dados.</span><span class="sxs-lookup"><span data-stu-id="51a60-138">Verify that the [System.Management.Automation.Psdriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) member exists and that a connection to the data store can be made.</span></span>

- <span data-ttu-id="51a60-139">Criar uma unidade e preencher o membro de ligação, no support do `New-PSDrive` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="51a60-139">Create a drive and populate the connection member, in support of the `New-PSDrive` cmdlet.</span></span>

- <span data-ttu-id="51a60-140">Validar a [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) objeto para a unidade proposto.</span><span class="sxs-lookup"><span data-stu-id="51a60-140">Validate the [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object for the proposed drive.</span></span>

- <span data-ttu-id="51a60-141">Modificar a [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) de objeto que descreve a unidade com quaisquer informações de fiabilidade ou desempenho obrigatório ou fornecer dados adicionais para chamadores com a unidade.</span><span class="sxs-lookup"><span data-stu-id="51a60-141">Modify the [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive with any required performance or reliability information, or provide extra data for callers using the drive.</span></span>

- <span data-ttu-id="51a60-142">Processar falhas utilizando o [System.Management.Automation.Provider.Cmdletprovider.Writeerror\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) método e em seguida, regresse `null`.</span><span class="sxs-lookup"><span data-stu-id="51a60-142">Handle failures using the [System.Management.Automation.Provider.Cmdletprovider.Writeerror\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) method and then return `null`.</span></span>

  <span data-ttu-id="51a60-143">Este método devolve a informação da unidade que foi passada para o método ou uma versão específica do fornecedor do mesmo.</span><span class="sxs-lookup"><span data-stu-id="51a60-143">This method returns either the drive information that was passed to the method or a provider-specific version of it.</span></span>

## <a name="attaching-dynamic-parameters-to-newdrive"></a><span data-ttu-id="51a60-144">Anexar parâmetros dinâmicos para NewDrive</span><span class="sxs-lookup"><span data-stu-id="51a60-144">Attaching Dynamic Parameters to NewDrive</span></span>

<span data-ttu-id="51a60-145">O `New-PSDrive` cmdlet suportado pelo seu fornecedor de unidade pode exigir parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="51a60-145">The `New-PSDrive` cmdlet supported by your drive provider might require additional parameters.</span></span> <span data-ttu-id="51a60-146">Para anexar estes parâmetros dinâmicos para o cmdlet, o provedor implementa a [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) método.</span><span class="sxs-lookup"><span data-stu-id="51a60-146">To attach these dynamic parameters to the cmdlet, the provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) method.</span></span> <span data-ttu-id="51a60-147">Esse método retorna um objeto com propriedades e campos com análise atributos semelhantes a uma classe cmdlet ou uma [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto.</span><span class="sxs-lookup"><span data-stu-id="51a60-147">This method returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="51a60-148">Este fornecedor de unidade não substitui este método.</span><span class="sxs-lookup"><span data-stu-id="51a60-148">This drive provider does not override this method.</span></span> <span data-ttu-id="51a60-149">No entanto, o código seguinte mostra a implementação padrão deste método:</span><span class="sxs-lookup"><span data-stu-id="51a60-149">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a><span data-ttu-id="51a60-150">Remover uma unidade</span><span class="sxs-lookup"><span data-stu-id="51a60-150">Removing a Drive</span></span>

<span data-ttu-id="51a60-151">Para fechar a ligação de base de dados, o fornecedor de unidade tem de implementar o [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) método.</span><span class="sxs-lookup"><span data-stu-id="51a60-151">To close the database connection, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method.</span></span> <span data-ttu-id="51a60-152">Este método fecha a ligação para a unidade depois de limpar qualquer informação específica do fornecedor.</span><span class="sxs-lookup"><span data-stu-id="51a60-152">This method closes the connection to the drive after cleaning up any provider-specific information.</span></span>

<span data-ttu-id="51a60-153">O código a seguir mostra a implementação do [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) método para este fornecedor de unidade:</span><span class="sxs-lookup"><span data-stu-id="51a60-153">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

<span data-ttu-id="51a60-154">Se a unidade pode ser removida, o método deve retornar as informações transmitidas para o método por meio do `drive` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="51a60-154">If the drive can be removed, the method should return the information passed to the method through the `drive` parameter.</span></span> <span data-ttu-id="51a60-155">Se não é possível remover a unidade, o método deve escrever uma exceção e, em seguida, retornar `null`.</span><span class="sxs-lookup"><span data-stu-id="51a60-155">If the drive cannot be removed, the method should write an exception and then return `null`.</span></span> <span data-ttu-id="51a60-156">Se o seu fornecedor não substitui este método, a implementação padrão deste método devolve apenas as informações da unidade passadas como entrada.</span><span class="sxs-lookup"><span data-stu-id="51a60-156">If your provider does not override this method, the default implementation of this method just returns the drive information passed as input.</span></span>

## <a name="initializing-default-drives"></a><span data-ttu-id="51a60-157">Unidades de inicialização padrão</span><span class="sxs-lookup"><span data-stu-id="51a60-157">Initializing Default Drives</span></span>

<span data-ttu-id="51a60-158">Sua implementa de fornecedor de unidade a [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) método para montar unidades.</span><span class="sxs-lookup"><span data-stu-id="51a60-158">Your drive provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method to mount drives.</span></span> <span data-ttu-id="51a60-159">Por exemplo, o fornecedor do Active Directory pode montar uma unidade de disco para o contexto de nomenclatura, se o computador estiver associado a um domínio predefinido.</span><span class="sxs-lookup"><span data-stu-id="51a60-159">For example, the Active Directory provider might mount a drive for the default naming context if the computer is joined to a domain.</span></span>

<span data-ttu-id="51a60-160">Esse método retorna uma coleção de informações da unidade sobre as unidades de inicializado, ou uma coleção vazia.</span><span class="sxs-lookup"><span data-stu-id="51a60-160">This method returns a collection of drive information about the initialized drives, or an empty collection.</span></span> <span data-ttu-id="51a60-161">A chamada para esse método é feita após as chamadas de tempo de execução do Windows PowerShell a [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) método para inicializar o fornecedor.</span><span class="sxs-lookup"><span data-stu-id="51a60-161">The call to this method is made after the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to initialize the provider.</span></span>

<span data-ttu-id="51a60-162">Este fornecedor de unidade não substitui a [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) método.</span><span class="sxs-lookup"><span data-stu-id="51a60-162">This drive provider does not override the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method.</span></span> <span data-ttu-id="51a60-163">No entanto, o código seguinte mostra a implementação padrão, que retorna uma coleção de unidade vazio:</span><span class="sxs-lookup"><span data-stu-id="51a60-163">However, the following code shows the default implementation, which returns an empty drive collection:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a><span data-ttu-id="51a60-164">Coisas a serem lembrados sobre a implementação InitializeDefaultDrives</span><span class="sxs-lookup"><span data-stu-id="51a60-164">Things to Remember About Implementing InitializeDefaultDrives</span></span>

<span data-ttu-id="51a60-165">Todos os fornecedores de unidade devem montar uma unidade de raiz para ajudar o utilizador com a capacidade de deteção.</span><span class="sxs-lookup"><span data-stu-id="51a60-165">All drive providers should mount a root drive to help the user with discoverability.</span></span> <span data-ttu-id="51a60-166">Na unidade raiz pode listar localizações que servem como raízes para outras unidades montadas.</span><span class="sxs-lookup"><span data-stu-id="51a60-166">The root drive might list locations that serve as roots for other mounted drives.</span></span> <span data-ttu-id="51a60-167">Por exemplo, o fornecedor do Active Directory pode criar uma unidade que lista os contextos de nomenclatura encontrados no `namingContext` atributos na raiz do ambiente do sistema distribuído (DSE).</span><span class="sxs-lookup"><span data-stu-id="51a60-167">For example, the Active Directory provider might create a drive that lists the naming contexts found in the `namingContext` attributes on the root Distributed System Environment (DSE).</span></span> <span data-ttu-id="51a60-168">Isto ajuda os utilizadores a descobrir os pontos de montagem para outras unidades.</span><span class="sxs-lookup"><span data-stu-id="51a60-168">This helps users discover mount points for other drives.</span></span>

## <a name="code-sample"></a><span data-ttu-id="51a60-169">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="51a60-169">Code Sample</span></span>

<span data-ttu-id="51a60-170">Para o código de exemplo completo, consulte [exemplo de código AccessDbProviderSample02](./accessdbprovidersample02-code-sample.md).</span><span class="sxs-lookup"><span data-stu-id="51a60-170">For complete sample code, see [AccessDbProviderSample02 Code Sample](./accessdbprovidersample02-code-sample.md).</span></span>

## <a name="testing-the-windows-powershell-drive-provider"></a><span data-ttu-id="51a60-171">Teste o fornecedor de unidade do PowerShell do Windows</span><span class="sxs-lookup"><span data-stu-id="51a60-171">Testing the Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="51a60-172">Quando o seu fornecedor de Windows PowerShell foi registado com o Windows PowerShell, pode testá-lo ao executar os cmdlets suportados na linha de comando, incluindo quaisquer cmdlets disponibilizados pela derivação.</span><span class="sxs-lookup"><span data-stu-id="51a60-172">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line, including any cmdlets made available by derivation.</span></span> <span data-ttu-id="51a60-173">Vamos testar o fornecedor de unidade de exemplo.</span><span class="sxs-lookup"><span data-stu-id="51a60-173">Let's test the sample drive provider.</span></span>

1. <span data-ttu-id="51a60-174">Execute o `Get-PSProvider` cmdlet para obter a lista de fornecedores para garantir que o fornecedor de unidade AccessDB está presente:</span><span class="sxs-lookup"><span data-stu-id="51a60-174">Run the `Get-PSProvider` cmdlet to retrieve the list of providers to ensure that the AccessDB drive provider is present:</span></span>

   <span data-ttu-id="51a60-175">**PS> `Get-PSProvider`**</span><span class="sxs-lookup"><span data-stu-id="51a60-175">**PS> `Get-PSProvider`**</span></span>

   <span data-ttu-id="51a60-176">É apresentado o seguinte resultado:</span><span class="sxs-lookup"><span data-stu-id="51a60-176">The following output appears:</span></span>

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

2. <span data-ttu-id="51a60-177">Certifique-se de que um nome de servidor de base de dados (DSN) existe para a base de dados ao aceder a **origens de dados** parte a **ferramentas administrativas** para o sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="51a60-177">Ensure that a database server name (DSN) exists for the database by accessing the **Data Sources** portion of the **Administrative Tools** for the operating system.</span></span> <span data-ttu-id="51a60-178">Na **DSN de utilizador** tabela, faça duplo clique em **base de dados do MS Access** e adicionar o caminho de unidade C:\ps\northwind.mdb.</span><span class="sxs-lookup"><span data-stu-id="51a60-178">In the **User DSN** table, double-click **MS Access Database** and add the drive path C:\ps\northwind.mdb.</span></span>

3. <span data-ttu-id="51a60-179">Crie uma nova unidade usando o provedor de unidade de exemplo:</span><span class="sxs-lookup"><span data-stu-id="51a60-179">Create a new drive using the sample drive provider:</span></span>

   <span data-ttu-id="51a60-180">**PS > novo psdrive-nome mydb-raiz c:\ps\northwind.mdb - psprovider AccessDb**</span><span class="sxs-lookup"><span data-stu-id="51a60-180">**PS> new-psdrive -name mydb -root c:\ps\northwind.mdb -psprovider AccessDb**</span></span>

   <span data-ttu-id="51a60-181">É apresentado o seguinte resultado:</span><span class="sxs-lookup"><span data-stu-id="51a60-181">The following output appears:</span></span>

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. <span data-ttu-id="51a60-182">Valide a ligação.</span><span class="sxs-lookup"><span data-stu-id="51a60-182">Validate the connection.</span></span> <span data-ttu-id="51a60-183">Como a ligação é definida como um membro da unidade, pode verificar com o cmdlet Get-PDDrive.</span><span class="sxs-lookup"><span data-stu-id="51a60-183">Because the connection is defined as a member of the drive, you can check it using the Get-PDDrive cmdlet.</span></span>

   > [!NOTE]
   > <span data-ttu-id="51a60-184">O utilizador ainda não é possível interagir com o provedor como uma unidade, como o fornecedor tem de funcionalidade de contentor para a interação.</span><span class="sxs-lookup"><span data-stu-id="51a60-184">The user cannot yet interact with the provider as a drive, as the provider needs container functionality for that interaction.</span></span> <span data-ttu-id="51a60-185">Para obter mais informações, consulte [criar um fornecedor de contentor do Windows PowerShell](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="51a60-185">For more information, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

   <span data-ttu-id="51a60-186">**PS > .connection (get-psdrive mydb)**</span><span class="sxs-lookup"><span data-stu-id="51a60-186">**PS> (get-psdrive mydb).connection**</span></span>

   <span data-ttu-id="51a60-187">É apresentado o seguinte resultado:</span><span class="sxs-lookup"><span data-stu-id="51a60-187">The following output appears:</span></span>

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

5. <span data-ttu-id="51a60-188">Remover a unidade e sair da shell:</span><span class="sxs-lookup"><span data-stu-id="51a60-188">Remove the drive and exit the shell:</span></span>

   <span data-ttu-id="51a60-189">**PS > remove-psdrive mydb**</span><span class="sxs-lookup"><span data-stu-id="51a60-189">**PS> remove-psdrive mydb**</span></span>

   <span data-ttu-id="51a60-190">**PS > Sair**</span><span class="sxs-lookup"><span data-stu-id="51a60-190">**PS> exit**</span></span>

## <a name="see-also"></a><span data-ttu-id="51a60-191">Veja Também</span><span class="sxs-lookup"><span data-stu-id="51a60-191">See Also</span></span>

[<span data-ttu-id="51a60-192">Criar provedores do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="51a60-192">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="51a60-193">Estruturar o seu fornecedor do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="51a60-193">Design Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="51a60-194">Criar um fornecedor de PowerShell do Windows básica</span><span class="sxs-lookup"><span data-stu-id="51a60-194">Creating a Basic Windows PowerShell Provider</span></span>](./creating-a-basic-windows-powershell-provider.md)