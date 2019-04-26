---
ms.date: 12/12/2018
keywords: DSC, powershell, configuração, a configuração
title: Publicar um servidor de solicitação com IDs de configuração (v4/v5)
ms.openlocfilehash: 0144fec43d7a8d65b79891567cc0dc3952175343
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079511"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a><span data-ttu-id="864f0-103">Publicar um servidor de solicitação com IDs de configuração (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="864f0-103">Publish to a Pull Server using Configuration IDs (v4/v5)</span></span>

<span data-ttu-id="864f0-104">As secções abaixo partem do princípio de que já configurou um servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="864f0-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="864f0-105">Se não tiver configurado o servidor de solicitação, pode utilizar os seguintes guias:</span><span class="sxs-lookup"><span data-stu-id="864f0-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="864f0-106">Configurar um servidor de solicitação de SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="864f0-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="864f0-107">Configurar um servidor de solicitação de HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="864f0-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="864f0-108">Cada nó de destino pode ser configurado para transferir configurações, recursos e até mesmo comunicou o seu estado.</span><span class="sxs-lookup"><span data-stu-id="864f0-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="864f0-109">Este artigo irá mostrar como carregar recursos para que estejam disponíveis para transferir e configurar os clientes transfiram os recursos automaticamente.</span><span class="sxs-lookup"><span data-stu-id="864f0-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="864f0-110">Quando o nó recebe uma configuração atribuídos, por meio **extrair** ou **Push** (v5), é transferida automaticamente quaisquer recursos de que a configuração a partir da localização especificada no LCM.</span><span class="sxs-lookup"><span data-stu-id="864f0-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="compile-configurations"></a><span data-ttu-id="864f0-111">Compilar configurações</span><span class="sxs-lookup"><span data-stu-id="864f0-111">Compile Configurations</span></span>

<span data-ttu-id="864f0-112">A primeira etapa para armazenar [configurações](../configurations/configurations.md) num servidor de solicitação é compilá-los na arquivos ". MOF".</span><span class="sxs-lookup"><span data-stu-id="864f0-112">The first step to storing [Configurations](../configurations/configurations.md) on a Pull Server, is to compile them into ".mof" files.</span></span> <span data-ttu-id="864f0-113">Para fazer uma configuração genérica e aplicáveis a mais clientes, use `localhost` em seu bloco de nó.</span><span class="sxs-lookup"><span data-stu-id="864f0-113">To make a configuration generic, and applicable to more clients, use `localhost` in your Node block.</span></span> <span data-ttu-id="864f0-114">O exemplo abaixo mostra um shell de configuração que utiliza `localhost` em vez de um nome de cliente específico.</span><span class="sxs-lookup"><span data-stu-id="864f0-114">The example below shows a Configuration shell that uses `localhost` instead of a specific client name.</span></span>

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

<span data-ttu-id="864f0-115">Após ter compilado seu configuração genérico, deve ter um ficheiro de "localhost.mof".</span><span class="sxs-lookup"><span data-stu-id="864f0-115">Once you have compiled your generic configuration, you should have a "localhost.mof" file.</span></span>

## <a name="renaming-the-mof-file"></a><span data-ttu-id="864f0-116">Mudar o nome de ficheiro MOF</span><span class="sxs-lookup"><span data-stu-id="864f0-116">Renaming the MOF file</span></span>

<span data-ttu-id="864f0-117">Pode armazenar ficheiros de ". MOF" de configuração num servidor de solicitação por **ConfigurationName** ou **ConfigurationID**.</span><span class="sxs-lookup"><span data-stu-id="864f0-117">You can store Configuration ".mof" files on a Pull Server by **ConfigurationName** or **ConfigurationID**.</span></span> <span data-ttu-id="864f0-118">Dependendo de como pretende configurar os clientes de solicitação, pode escolher uma secção abaixo para corretamente mudar o nome de seus arquivos compilados ". MOF".</span><span class="sxs-lookup"><span data-stu-id="864f0-118">Depending on how you plan to set up your pull clients, you can choose a section below to properly rename your compiled ".mof" files.</span></span>

### <a name="configuration-ids-guid"></a><span data-ttu-id="864f0-119">IDs de configuração (GUID)</span><span class="sxs-lookup"><span data-stu-id="864f0-119">Configuration IDs (GUID)</span></span>

<span data-ttu-id="864f0-120">Terá de mudar o nome do seu arquivo de "localhost.mof" para "<GUID>. MOF" ficheiro.</span><span class="sxs-lookup"><span data-stu-id="864f0-120">You will need to rename your "localhost.mof" file to "<GUID>.mof" file.</span></span> <span data-ttu-id="864f0-121">Pode criar um aleatório **Guid** usando o exemplo abaixo, ou utilizando o [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="864f0-121">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="864f0-122">Saída de exemplo</span><span class="sxs-lookup"><span data-stu-id="864f0-122">Sample Output</span></span>

```output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

<span data-ttu-id="864f0-123">Em seguida, pode mudar o nome do arquivo de ". MOF" usando qualquer método aceitável.</span><span class="sxs-lookup"><span data-stu-id="864f0-123">You can then rename your ".mof" file using any acceptable method.</span></span> <span data-ttu-id="864f0-124">O exemplo abaixo, utiliza a [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="864f0-124">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

<span data-ttu-id="864f0-125">Para obter mais informações sobre como utilizar **Guids** no seu ambiente, consulte [planear Guids](/powershell/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="864f0-125">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

### <a name="configuration-names"></a><span data-ttu-id="864f0-126">Nomes de configuração</span><span class="sxs-lookup"><span data-stu-id="864f0-126">Configuration Names</span></span>

<span data-ttu-id="864f0-127">Terá de mudar o nome do seu arquivo de "localhost.mof" para "<Configuration Name>. MOF" ficheiro.</span><span class="sxs-lookup"><span data-stu-id="864f0-127">You will need to rename your "localhost.mof" file to "<Configuration Name>.mof" file.</span></span> <span data-ttu-id="864f0-128">No exemplo a seguir, é utilizado o nome da configuração da secção anterior.</span><span class="sxs-lookup"><span data-stu-id="864f0-128">In the following example, the configuration name from the previous section is used.</span></span> <span data-ttu-id="864f0-129">Em seguida, pode mudar o nome do arquivo de ". MOF" usando qualquer método aceitável.</span><span class="sxs-lookup"><span data-stu-id="864f0-129">You can then rename your ".mof" file using any acceptable method.</span></span> <span data-ttu-id="864f0-130">O exemplo abaixo, utiliza a [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="864f0-130">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a><span data-ttu-id="864f0-131">Criar a soma de verificação</span><span class="sxs-lookup"><span data-stu-id="864f0-131">Create the CheckSum</span></span>

<span data-ttu-id="864f0-132">Cada arquivo de ". MOF" armazenados num servidor de solicitação ou partilha SMB tem de ter um ficheiro associado ".checksum".</span><span class="sxs-lookup"><span data-stu-id="864f0-132">Each ".mof" file stored on a Pull Server, or SMB share needs to have an associated ".checksum" file.</span></span> <span data-ttu-id="864f0-133">Este ficheiro permite que os clientes a saber quando o ficheiro associado ". MOF" foi alterado e deve ser transferido novamente.</span><span class="sxs-lookup"><span data-stu-id="864f0-133">This file lets clients know when the associated ".mof" file has changed and should be downloaded again.</span></span>

<span data-ttu-id="864f0-134">Pode criar uma **soma de verificação** com o [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="864f0-134">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span></span> <span data-ttu-id="864f0-135">Também pode executar `New-DSCCheckSum` com um diretório de arquivos usando o `-Path` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="864f0-135">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="864f0-136">Se já existir uma soma de verificação, pode forçá-lo de ser recriadas com o `-Force` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="864f0-136">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span> <span data-ttu-id="864f0-137">O exemplo seguinte especificado um diretório que contém o ficheiro ". MOF" da secção anterior e utiliza o `-Force` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="864f0-137">The following example specified a directory containing the ".mof" file from the previous section, and uses the `-Force` parameter.</span></span>

```powershell
New-DscChecksum -Path '.\' -Force
```

<span data-ttu-id="864f0-138">Não será apresentada nenhuma saída, mas agora, deverá ver um "<GUID or Configuration Name>. mof.checksum" ficheiro.</span><span class="sxs-lookup"><span data-stu-id="864f0-138">No output will be shown, but you should now see a "<GUID or Configuration Name>.mof.checksum" file.</span></span>

## <a name="where-to-store-mof-files-and-checksums"></a><span data-ttu-id="864f0-139">Onde pretende armazenar os arquivos MOF e somas de verificação</span><span class="sxs-lookup"><span data-stu-id="864f0-139">Where to store MOF files and CheckSums</span></span>

### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="864f0-140">Num servidor de solicitação de HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="864f0-140">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="864f0-141">Quando configurar seu servidor de solicitação de HTTP, conforme explicado na [configurar um servidor de solicitação de HTTP para DSC](pullServer.md), que especificar diretórios para o **ModulePath** e **ConfigurationPath** chaves.</span><span class="sxs-lookup"><span data-stu-id="864f0-141">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="864f0-142">O **ConfigurationPath** key indica onde devem ser armazenados ficheiros ". MOF".</span><span class="sxs-lookup"><span data-stu-id="864f0-142">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="864f0-143">O **ConfigurationPath** indica onde todos os arquivos ". MOF" e ".checksum" arquivos devem ser armazenados.</span><span class="sxs-lookup"><span data-stu-id="864f0-143">The **ConfigurationPath** indicates where any ".mof" files and ".checksum" files should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a><span data-ttu-id="864f0-144">Numa partilha SMB</span><span class="sxs-lookup"><span data-stu-id="864f0-144">On an SMB Share</span></span>

<span data-ttu-id="864f0-145">Quando configurar um cliente solicitar a utilizar uma partilha de SMB, especifique um **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="864f0-145">When you set up a Pull Client to use an SMB share, you specify a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="864f0-146">Todos os arquivos de ". MOF" e ".checksum", em seguida, devem ser armazenados na **SourcePath** diretório da **ConfigurationRepositoryShare** bloco.</span><span class="sxs-lookup"><span data-stu-id="864f0-146">All ".mof" files and ".checksum" files should then be stored in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a><span data-ttu-id="864f0-147">Próximos Passos</span><span class="sxs-lookup"><span data-stu-id="864f0-147">Next Steps</span></span>

<span data-ttu-id="864f0-148">Em seguida, desejará configurar clientes de Pull para extrair a configuração especificada.</span><span class="sxs-lookup"><span data-stu-id="864f0-148">Next, you will want to configure Pull Clients to pull the specified configuration.</span></span> <span data-ttu-id="864f0-149">Para obter mais informações, consulte um dos seguintes guias:</span><span class="sxs-lookup"><span data-stu-id="864f0-149">For more information, see one of the following guides:</span></span>

- [<span data-ttu-id="864f0-150">Configurar um cliente de solicitação através de IDs de configuração (v4)</span><span class="sxs-lookup"><span data-stu-id="864f0-150">Set up a Pull Client using Configuration IDs (v4)</span></span>](pullClientConfigId4.md)
- [<span data-ttu-id="864f0-151">Configurar um cliente de solicitação através de IDs de configuração (v5)</span><span class="sxs-lookup"><span data-stu-id="864f0-151">Set up a Pull Client using Configuration IDs (v5)</span></span>](pullClientConfigId.md)
- [<span data-ttu-id="864f0-152">Configurar um cliente de solicitação através de nomes de configuração (v5)</span><span class="sxs-lookup"><span data-stu-id="864f0-152">Set up a Pull Client using Configuration Names (v5)</span></span>](pullClientConfigNames.md)

## <a name="see-also"></a><span data-ttu-id="864f0-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="864f0-153">See also</span></span>

- [<span data-ttu-id="864f0-154">Configurar um servidor de solicitação de SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="864f0-154">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="864f0-155">Configurar um servidor de solicitação de HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="864f0-155">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
- [<span data-ttu-id="864f0-156">Pacote e o carregamento de recursos para um servidor de solicitação</span><span class="sxs-lookup"><span data-stu-id="864f0-156">Package and Upload Resources to a Pull Server</span></span>](package-upload-resources.md)
