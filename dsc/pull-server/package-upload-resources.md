---
ms.date: 12/12/2018
keywords: DSC, powershell, configuração, a configuração
title: Pacote e o carregamento de recursos para um servidor de solicitação
ms.openlocfilehash: 29a62f96393a53c9e7da57a5e51732dcb0937194
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079574"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a><span data-ttu-id="798f8-103">Pacote e o carregamento de recursos para um servidor de solicitação</span><span class="sxs-lookup"><span data-stu-id="798f8-103">Package and Upload Resources to a Pull Server</span></span>

<span data-ttu-id="798f8-104">As secções abaixo partem do princípio de que já configurou um servidor de solicitação.</span><span class="sxs-lookup"><span data-stu-id="798f8-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="798f8-105">Se não tiver configurado o servidor de solicitação, pode utilizar os seguintes guias:</span><span class="sxs-lookup"><span data-stu-id="798f8-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="798f8-106">Configurar um servidor de solicitação de SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="798f8-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="798f8-107">Configurar um servidor de solicitação de HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="798f8-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="798f8-108">Cada nó de destino pode ser configurado para transferir configurações, recursos e até mesmo comunicou o seu estado.</span><span class="sxs-lookup"><span data-stu-id="798f8-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="798f8-109">Este artigo irá mostrar como carregar recursos para que estejam disponíveis para transferir e configurar os clientes transfiram os recursos automaticamente.</span><span class="sxs-lookup"><span data-stu-id="798f8-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="798f8-110">Quando o nó recebe uma configuração atribuídos, por meio **extrair** ou **Push** (v5), é transferida automaticamente quaisquer recursos de que a configuração a partir da localização especificada no LCM.</span><span class="sxs-lookup"><span data-stu-id="798f8-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="package-resource-modules"></a><span data-ttu-id="798f8-111">Módulos de recursos de pacote</span><span class="sxs-lookup"><span data-stu-id="798f8-111">Package Resource Modules</span></span>

<span data-ttu-id="798f8-112">Cada recurso disponível para um cliente transferir deve ser armazenado num arquivo de ". zip".</span><span class="sxs-lookup"><span data-stu-id="798f8-112">Each resource available for a client to download must be stored in a ".zip" file.</span></span> <span data-ttu-id="798f8-113">O exemplo abaixo mostra os passos necessários para utilizar o [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) recursos.</span><span class="sxs-lookup"><span data-stu-id="798f8-113">The example below will show the required steps using the [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) resource.</span></span>

> [!NOTE]
> <span data-ttu-id="798f8-114">Se tiver quaisquer clientes usando o PowerShell 4.0, será preciso flaten a estrutura de pastas de recursos e remover quaisquer pastas de versão.</span><span class="sxs-lookup"><span data-stu-id="798f8-114">If you have any clients using PowerShell 4.0, you will need to flaten the resource folder structure and remove any version folders.</span></span> <span data-ttu-id="798f8-115">Para obter mais informações, consulte [várias versões de recursos](../configurations/import-dscresource.md#multiple-resource-versions).</span><span class="sxs-lookup"><span data-stu-id="798f8-115">For more information, see [Multiple Resource Versions](../configurations/import-dscresource.md#multiple-resource-versions).</span></span>

<span data-ttu-id="798f8-116">É possível compactar o diretório de recursos em qualquer utilitário, um script ou um método que preferir.</span><span class="sxs-lookup"><span data-stu-id="798f8-116">You can compress the resource directory using any utility, script, or method that you prefer.</span></span> <span data-ttu-id="798f8-117">No Windows, pode *com o botão direito* no diretório de "xPSDesiredStateConfiguration" e selecione "Enviar para", em seguida, "Pasta comprimida".</span><span class="sxs-lookup"><span data-stu-id="798f8-117">In Windows, you can *right-click* on the "xPSDesiredStateConfiguration" directory, and select "Send To", then "Compressed Folder".</span></span>

![Clique com botão direito](../media/right-click.gif)

### <a name="naming-the-resource-archive"></a><span data-ttu-id="798f8-119">O arquivo de recursos de atribuição de nomes</span><span class="sxs-lookup"><span data-stu-id="798f8-119">Naming the Resource Archive</span></span>

<span data-ttu-id="798f8-120">O arquivo de recursos tem de ser chamado com o seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="798f8-120">The Resource archive needs to be named with the following format:</span></span>

```
{ModuleName}_{Version}.zip
```

<span data-ttu-id="798f8-121">No exemplo acima, "xPSDesiredStateConfiguration.zip" deve ser o nome mudado "xPSDesiredStateConfiguration_8.4.4.0.zip".</span><span class="sxs-lookup"><span data-stu-id="798f8-121">In the example above, "xPSDesiredStateConfiguration.zip" should be renamed "xPSDesiredStateConfiguration_8.4.4.0.zip".</span></span>

### <a name="create-checksums"></a><span data-ttu-id="798f8-122">Crie somas de verificação</span><span class="sxs-lookup"><span data-stu-id="798f8-122">Create CheckSums</span></span>

<span data-ttu-id="798f8-123">Assim que o módulo de recursos foi compactado e mudar o nome, tem de criar uma **soma de verificação**.</span><span class="sxs-lookup"><span data-stu-id="798f8-123">Once the Resource module has been compressed and renamed, you need to create a **CheckSum**.</span></span>  <span data-ttu-id="798f8-124">O **soma de verificação** é utilizada, pelo LCM no cliente, para determinar se o recurso foi alterado e tem de ser transferida novamente.</span><span class="sxs-lookup"><span data-stu-id="798f8-124">The **CheckSum** is used, by the LCM on the client, to determine if the resource has been changed, and needs to be downloaded again.</span></span> <span data-ttu-id="798f8-125">Pode criar uma **soma de verificação** com o [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, conforme mostrado no exemplo abaixo.</span><span class="sxs-lookup"><span data-stu-id="798f8-125">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet, as shown in the example below.</span></span>

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

<span data-ttu-id="798f8-126">Não será apresentada nenhuma saída, mas agora, deverá ver um "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum".</span><span class="sxs-lookup"><span data-stu-id="798f8-126">No output will be shown, but you should now see a "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum".</span></span> <span data-ttu-id="798f8-127">Também pode executar `New-DSCCheckSum` com um diretório de arquivos usando o `-Path` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="798f8-127">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span> <span data-ttu-id="798f8-128">Se já existir uma soma de verificação, pode forçá-lo de ser recriadas com o `-Force` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="798f8-128">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span>

### <a name="where-to-store-resource-archives"></a><span data-ttu-id="798f8-129">Onde pretende armazenar os arquivos de recursos</span><span class="sxs-lookup"><span data-stu-id="798f8-129">Where to store Resource Archives</span></span>

#### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="798f8-130">Num servidor de solicitação de HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="798f8-130">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="798f8-131">Quando configurar seu servidor de solicitação de HTTP, conforme explicado na [configurar um servidor de solicitação de HTTP para DSC](pullServer.md), que especificar diretórios para o **ModulePath** e **ConfigurationPath** chaves.</span><span class="sxs-lookup"><span data-stu-id="798f8-131">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="798f8-132">O **ConfigurationPath** key indica onde devem ser armazenados ficheiros ". MOF".</span><span class="sxs-lookup"><span data-stu-id="798f8-132">The **ConfigurationPath** key indicates where any ".mof" files should be stored.</span></span> <span data-ttu-id="798f8-133">O **ModulePath** indica onde quaisquer módulos de recursos de DSC devem ser armazenados.</span><span class="sxs-lookup"><span data-stu-id="798f8-133">The **ModulePath** indicates where any DSC Resource Modules should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a><span data-ttu-id="798f8-134">Numa partilha SMB</span><span class="sxs-lookup"><span data-stu-id="798f8-134">On an SMB Share</span></span>

<span data-ttu-id="798f8-135">Se tiver especificado um **ResourceRepositoryShare**, quando configurar o seu cliente de solicitação, armazenar arquivos e as somas de verificação no **SourcePath** diretório da **ResourceRepositoryShare** bloco.</span><span class="sxs-lookup"><span data-stu-id="798f8-135">If you specified a **ResourceRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ResourceRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Configurations'
}

ResourceRepositoryShare SMBResourceServer
{
    SourcePath = '\\SMBPullServer\Resources'
}
```

<span data-ttu-id="798f8-136">Se tiver especificado apenas uma **ConfigurationRepositoryShare**, quando configurar o seu cliente de solicitação, armazenar arquivos e as somas de verificação no **SourcePath** diretório da  **ConfigurationRepositoryShare** bloco.</span><span class="sxs-lookup"><span data-stu-id="798f8-136">If you specified only a **ConfigurationRepositoryShare**, when setting up your Pull Client, store archives and checksums in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a><span data-ttu-id="798f8-137">A atualizar os recursos</span><span class="sxs-lookup"><span data-stu-id="798f8-137">Updating resources</span></span>

<span data-ttu-id="798f8-138">Pode forçar um nó para atualizar os seus recursos ao alterar o número de versão no nome do arquivo, ou ao criar uma nova soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="798f8-138">You can force a Node to update its resources by changing the version number in the archive's name, or by creating a new checksum.</span></span> <span data-ttu-id="798f8-139">O cliente de solicitação irá verificar as versões mais recentes dos recursos necessários, bem como atualizadas as somas de verificação, quando atualiza o LCM.</span><span class="sxs-lookup"><span data-stu-id="798f8-139">The Pull Client will check for newer versions of required resources, as well as updated checksums, when its LCM refreshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="798f8-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="798f8-140">See also</span></span>

- [<span data-ttu-id="798f8-141">Configurar um servidor de solicitação de SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="798f8-141">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="798f8-142">Configurar um servidor de solicitação de HTTP de DSC</span><span class="sxs-lookup"><span data-stu-id="798f8-142">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
