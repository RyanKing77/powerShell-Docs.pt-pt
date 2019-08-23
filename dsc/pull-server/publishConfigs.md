---
ms.date: 12/12/2018
keywords: DSC, PowerShell, configuração, instalação
title: Publicar em um servidor de pull usando IDs de configuração (v4/V5)
ms.openlocfilehash: c258814f480b91eba75c7ce9abf70c558f1f469e
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986567"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a><span data-ttu-id="9ece4-103">Publicar em um servidor de pull usando IDs de configuração (v4/V5)</span><span class="sxs-lookup"><span data-stu-id="9ece4-103">Publish to a Pull Server using Configuration IDs (v4/v5)</span></span>

<span data-ttu-id="9ece4-104">As seções a seguir pressupõem que você já configurou um servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="9ece4-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="9ece4-105">Se você ainda não configurou o servidor de pull, poderá usar os seguintes guias:</span><span class="sxs-lookup"><span data-stu-id="9ece4-105">If you haven't set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="9ece4-106">Configurar um servidor de pull de SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="9ece4-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="9ece4-107">Configurar um servidor de pull HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="9ece4-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="9ece4-108">Cada nó de destino pode ser configurado para baixar configurações, recursos e até mesmo relatar seu status.</span><span class="sxs-lookup"><span data-stu-id="9ece4-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="9ece4-109">Este artigo mostra como carregar recursos para que eles fiquem disponíveis para download e configurar clientes para baixar automaticamente os recursos.</span><span class="sxs-lookup"><span data-stu-id="9ece4-109">This article shows you how to upload resources so they're available to be downloaded, and configure clients to automatically download resources.</span></span> <span data-ttu-id="9ece4-110">Quando o nó recebe uma configuração atribuída, por **pull** ou **Push** (V5), ele baixa automaticamente todos os recursos exigidos pela configuração do local especificado no Configuration Manager local (LCM).</span><span class="sxs-lookup"><span data-stu-id="9ece4-110">When the node receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the Local Configuration Manager (LCM).</span></span>

## <a name="compile-configurations"></a><span data-ttu-id="9ece4-111">Compilar configurações</span><span class="sxs-lookup"><span data-stu-id="9ece4-111">Compile configurations</span></span>

<span data-ttu-id="9ece4-112">A primeira etapa para armazenar [as configurações](../configurations/configurations.md) em um servidor de pull é compilá-las `.mof` em arquivos.</span><span class="sxs-lookup"><span data-stu-id="9ece4-112">The first step to storing [Configurations](../configurations/configurations.md) on a Pull Server, is to compile them into `.mof` files.</span></span> <span data-ttu-id="9ece4-113">Para tornar uma configuração genérica e aplicável a mais clientes, use `localhost` em seu bloco de nó.</span><span class="sxs-lookup"><span data-stu-id="9ece4-113">To make a configuration generic, and applicable to more clients, use `localhost` in your Node block.</span></span> <span data-ttu-id="9ece4-114">O exemplo a seguir mostra um shell de configuração `localhost` que usa em vez de um nome de cliente específico.</span><span class="sxs-lookup"><span data-stu-id="9ece4-114">The example below shows a Configuration shell that uses `localhost` instead of a specific client name.</span></span>

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

<span data-ttu-id="9ece4-115">Depois de Compilar sua configuração genérica, você deve ter um `localhost.mof` arquivo.</span><span class="sxs-lookup"><span data-stu-id="9ece4-115">Once you've compiled your generic configuration, you should have a `localhost.mof` file.</span></span>

## <a name="renaming-the-mof-file"></a><span data-ttu-id="9ece4-116">Renomeando o arquivo MOF</span><span class="sxs-lookup"><span data-stu-id="9ece4-116">Renaming the MOF file</span></span>

<span data-ttu-id="9ece4-117">Você pode armazenar arquivos `.mof` de configuração em um servidor de pull por **ConfigurationName** ou **ConfigurationId**.</span><span class="sxs-lookup"><span data-stu-id="9ece4-117">You can store Configuration `.mof` files on a Pull Server by **ConfigurationName** or **ConfigurationID**.</span></span> <span data-ttu-id="9ece4-118">Dependendo de como você planeja configurar seus clientes de pull, você pode escolher uma seção abaixo para renomear corretamente os arquivos `.mof` compilados.</span><span class="sxs-lookup"><span data-stu-id="9ece4-118">Depending on how you plan to set up your pull clients, you can choose a section below to properly rename your compiled `.mof` files.</span></span>

### <a name="configuration-ids-guid"></a><span data-ttu-id="9ece4-119">IDs de configuração (GUID)</span><span class="sxs-lookup"><span data-stu-id="9ece4-119">Configuration IDs (GUID)</span></span>

<span data-ttu-id="9ece4-120">Você precisará renomear `localhost.mof` o arquivo `<GUID>.mof` para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="9ece4-120">You'll need to rename your `localhost.mof` file to `<GUID>.mof` file.</span></span> <span data-ttu-id="9ece4-121">Você pode criar um **GUID** aleatório usando o exemplo abaixo ou usando o cmdlet [New-GUID](/powershell/module/microsoft.powershell.utility/new-guid) .</span><span class="sxs-lookup"><span data-stu-id="9ece4-121">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="9ece4-122">Saída de exemplo</span><span class="sxs-lookup"><span data-stu-id="9ece4-122">Sample Output</span></span>

```Output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

<span data-ttu-id="9ece4-123">Em seguida, você pode `.mof` renomear o arquivo usando qualquer método aceitável.</span><span class="sxs-lookup"><span data-stu-id="9ece4-123">You can then rename your `.mof` file using any acceptable method.</span></span> <span data-ttu-id="9ece4-124">O exemplo a seguir usa o cmdlet [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) .</span><span class="sxs-lookup"><span data-stu-id="9ece4-124">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

<span data-ttu-id="9ece4-125">Para obter mais informações sobre como usar GUIDs em seu ambiente, consulte [planejar GUIDs](/powershell/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="9ece4-125">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

### <a name="configuration-names"></a><span data-ttu-id="9ece4-126">Nomes de configuração</span><span class="sxs-lookup"><span data-stu-id="9ece4-126">Configuration names</span></span>

<span data-ttu-id="9ece4-127">Você precisará renomear `localhost.mof` o arquivo `<Configuration Name>.mof` para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="9ece4-127">You'll need to rename your `localhost.mof` file to `<Configuration Name>.mof` file.</span></span> <span data-ttu-id="9ece4-128">No exemplo a seguir, o nome da configuração da seção anterior é usado.</span><span class="sxs-lookup"><span data-stu-id="9ece4-128">In the following example, the configuration name from the previous section is used.</span></span> <span data-ttu-id="9ece4-129">Em seguida, você pode `.mof` renomear o arquivo usando qualquer método aceitável.</span><span class="sxs-lookup"><span data-stu-id="9ece4-129">You can then rename your `.mof` file using any acceptable method.</span></span> <span data-ttu-id="9ece4-130">O exemplo a seguir usa o cmdlet [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) .</span><span class="sxs-lookup"><span data-stu-id="9ece4-130">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a><span data-ttu-id="9ece4-131">Criar a soma de verificação</span><span class="sxs-lookup"><span data-stu-id="9ece4-131">Create the checkSum</span></span>

<span data-ttu-id="9ece4-132">Cada `.mof` arquivo armazenado em um servidor de pull ou compartilhamento SMB precisa ter um arquivo associado `.checksum` .</span><span class="sxs-lookup"><span data-stu-id="9ece4-132">Each `.mof` file stored on a Pull Server, or SMB share needs to have an associated `.checksum` file.</span></span>
<span data-ttu-id="9ece4-133">Esse arquivo permite que os clientes saibam quando `.mof` o arquivo associado foi alterado e devem ser baixados novamente.</span><span class="sxs-lookup"><span data-stu-id="9ece4-133">This file lets clients know when the associated `.mof` file has changed and should be downloaded again.</span></span>

<span data-ttu-id="9ece4-134">Você pode criar uma **soma de verificação** com o cmdlet [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) .</span><span class="sxs-lookup"><span data-stu-id="9ece4-134">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span></span> <span data-ttu-id="9ece4-135">Você também pode executar `New-DSCCheckSum` em um diretório de arquivos usando o `-Path` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="9ece4-135">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span>
<span data-ttu-id="9ece4-136">Se já existir uma soma de verificação, você poderá forçá-la a ser recriada com o `-Force` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="9ece4-136">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span> <span data-ttu-id="9ece4-137">O exemplo a seguir especificou um diretório `.mof` que contém o arquivo da seção anterior e usa `-Force` o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="9ece4-137">The following example specified a directory containing the `.mof` file from the previous section, and uses the `-Force` parameter.</span></span>

```powershell
New-DscChecksum -Path '.\' -Force
```

<span data-ttu-id="9ece4-138">Nenhuma saída será mostrada, mas agora você verá um `<GUID or Configuration Name>.mof.checksum` arquivo.</span><span class="sxs-lookup"><span data-stu-id="9ece4-138">No output will be shown, but you should now see a `<GUID or Configuration Name>.mof.checksum` file.</span></span>

## <a name="where-to-store-mof-files-and-checksums"></a><span data-ttu-id="9ece4-139">Onde armazenar os arquivos MOF e as somas de verificação</span><span class="sxs-lookup"><span data-stu-id="9ece4-139">Where to store MOF files and checkSums</span></span>

### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="9ece4-140">Em um servidor de pull HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="9ece4-140">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="9ece4-141">Quando você configura seu servidor de pull HTTP, conforme explicado em [configurar um servidor de pull http de DSC](pullServer.md), você especifica diretórios para as chaves **ModulePath** e **ConfigurationPath** .</span><span class="sxs-lookup"><span data-stu-id="9ece4-141">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="9ece4-142">A chave **ModulePath** indica onde os `.zip` arquivos empacotados de um módulo devem ser armazenados.</span><span class="sxs-lookup"><span data-stu-id="9ece4-142">The **ModulePath** key indicates where a module's packaged `.zip` files should be stored.</span></span> <span data-ttu-id="9ece4-143">O **ConfigurationPath** indica onde os `.mof` arquivos e `.checksum` arquivos devem ser armazenados.</span><span class="sxs-lookup"><span data-stu-id="9ece4-143">The **ConfigurationPath** indicates where any `.mof` files and `.checksum` files should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a><span data-ttu-id="9ece4-144">Em um compartilhamento SMB</span><span class="sxs-lookup"><span data-stu-id="9ece4-144">On an SMB share</span></span>

<span data-ttu-id="9ece4-145">Ao configurar um cliente de pull para usar um compartilhamento SMB, você especifica um **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="9ece4-145">When you set up a Pull Client to use an SMB share, you specify a **ConfigurationRepositoryShare**.</span></span>
<span data-ttu-id="9ece4-146">Todos `.mof` os arquivos `.checksum` e arquivos devem ser armazenados no diretório **SourcePath** do bloco **ConfigurationRepositoryShare** .</span><span class="sxs-lookup"><span data-stu-id="9ece4-146">All `.mof` files and `.checksum` files should be stored in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a><span data-ttu-id="9ece4-147">Passos Seguintes</span><span class="sxs-lookup"><span data-stu-id="9ece4-147">Next steps</span></span>

<span data-ttu-id="9ece4-148">Em seguida, você desejará configurar clientes de pull para efetuar pull da configuração especificada.</span><span class="sxs-lookup"><span data-stu-id="9ece4-148">Next, you'll want to configure Pull Clients to pull the specified configuration.</span></span> <span data-ttu-id="9ece4-149">Para obter mais informações, consulte um dos seguintes guias:</span><span class="sxs-lookup"><span data-stu-id="9ece4-149">For more information, see one of the following guides:</span></span>

- [<span data-ttu-id="9ece4-150">Configurar um cliente de pull usando IDs de configuração (v4)</span><span class="sxs-lookup"><span data-stu-id="9ece4-150">Set up a Pull Client using Configuration IDs (v4)</span></span>](pullClientConfigId4.md)
- [<span data-ttu-id="9ece4-151">Configurar um cliente de pull usando IDs de configuração (V5)</span><span class="sxs-lookup"><span data-stu-id="9ece4-151">Set up a Pull Client using Configuration IDs (v5)</span></span>](pullClientConfigId.md)
- [<span data-ttu-id="9ece4-152">Configurar um cliente de pull usando nomes de configuração (V5)</span><span class="sxs-lookup"><span data-stu-id="9ece4-152">Set up a Pull Client using Configuration Names (v5)</span></span>](pullClientConfigNames.md)

## <a name="see-also"></a><span data-ttu-id="9ece4-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ece4-153">See also</span></span>

- [<span data-ttu-id="9ece4-154">Configurar um servidor de pull de SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="9ece4-154">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="9ece4-155">Configurar um servidor de pull HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="9ece4-155">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
- [<span data-ttu-id="9ece4-156">Empacotar e carregar recursos para um servidor de pull</span><span class="sxs-lookup"><span data-stu-id="9ece4-156">Package and Upload Resources to a Pull Server</span></span>](package-upload-resources.md)
