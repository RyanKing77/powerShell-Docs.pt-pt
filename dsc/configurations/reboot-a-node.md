---
ms.date: 1/17/2019
keywords: DSC, powershell, configuração, a configuração
title: Reboot a Node (Reiniciar um Nó)
ms.openlocfilehash: 015b82a32caefc420973651c72e272fd85baf880
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054735"
---
# <a name="reboot-a-node"></a><span data-ttu-id="a49df-103">Reboot a Node (Reiniciar um Nó)</span><span class="sxs-lookup"><span data-stu-id="a49df-103">Reboot a Node</span></span>

> [!NOTE]
> <span data-ttu-id="a49df-104">Este tópico discute como um nó de reinício.</span><span class="sxs-lookup"><span data-stu-id="a49df-104">This topic talks about how to reboot a Node.</span></span> <span data-ttu-id="a49df-105">Para que a reinicialização seja concluída com êxito a **ActionAfterReboot** e **RebootNodeIfNeeded** definições do LCM precisam ser configurados corretamente.</span><span class="sxs-lookup"><span data-stu-id="a49df-105">In order for the reboot to be successful the **ActionAfterReboot** and **RebootNodeIfNeeded** LCM settings need to be configured properly.</span></span>
> <span data-ttu-id="a49df-106">Para ler mais sobre as definições do Gestor de configuração Local, veja [configurar o Gestor de configuração Local](../managing-nodes/metaConfig.md), ou [configurar o Gestor de configuração Local (v4)](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="a49df-106">To read about Local Configuration Manager settings, see [Configure the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configure the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>

<span data-ttu-id="a49df-107">Nós podem ser reiniciados de dentro de um recurso, utilizando o `$global:DSCMachineStatus` sinalizador.</span><span class="sxs-lookup"><span data-stu-id="a49df-107">Nodes can be rebooted from within a resource, by using the `$global:DSCMachineStatus` flag.</span></span> <span data-ttu-id="a49df-108">Definir este sinalizador `1` no `Set-TargetResource` função força o LCM para reiniciar o nó diretamente após o **definir** método do recurso atual.</span><span class="sxs-lookup"><span data-stu-id="a49df-108">Setting this flag to `1` in the `Set-TargetResource` function forces the LCM to reboot the Node directly after the **Set** method of the current resource.</span></span> <span data-ttu-id="a49df-109">Usando este sinalizador, o **xPendingReboot** recursos Deteta se está pendente um reinício fora de DSC.</span><span class="sxs-lookup"><span data-stu-id="a49df-109">Using this flag, the **xPendingReboot** resource detects if a reboot is pending outside of DSC.</span></span>

<span data-ttu-id="a49df-110">Sua [configurações](configurations.md) pode efetuar os passos que exigem o nó reiniciar o computador.</span><span class="sxs-lookup"><span data-stu-id="a49df-110">Your [configurations](configurations.md) may perform steps that require the Node to reboot.</span></span> <span data-ttu-id="a49df-111">Isso pode incluir coisas como:</span><span class="sxs-lookup"><span data-stu-id="a49df-111">This could include things such as:</span></span>

- <span data-ttu-id="a49df-112">Atualizações do Windows</span><span class="sxs-lookup"><span data-stu-id="a49df-112">Windows updates</span></span>
- <span data-ttu-id="a49df-113">Instalação de software</span><span class="sxs-lookup"><span data-stu-id="a49df-113">Software install</span></span>
- <span data-ttu-id="a49df-114">Muda o nome de ficheiro</span><span class="sxs-lookup"><span data-stu-id="a49df-114">File renames</span></span>
- <span data-ttu-id="a49df-115">A mudança de nome de computador</span><span class="sxs-lookup"><span data-stu-id="a49df-115">Computer rename</span></span>

<span data-ttu-id="a49df-116">O **xPendingReboot** recursos verifica localizações específicas de computador para determinar se está pendente um reinício.</span><span class="sxs-lookup"><span data-stu-id="a49df-116">The **xPendingReboot** resource checks specific computer locations to determine if a reboot is pending.</span></span> <span data-ttu-id="a49df-117">Se o nó requer um reinício fora de DSC, o **xPendingReboot** conjuntos de recursos a `$global:DSCMachineStatus` sinalizador para `1` forçar um reinício e como resolver a condição pendente.</span><span class="sxs-lookup"><span data-stu-id="a49df-117">If the Node requires a reboot outside of DSC, the **xPendingReboot** resource sets the `$global:DSCMachineStatus` flag to `1` forcing a reboot and resolving the pending condition.</span></span>

> [!NOTE]
> <span data-ttu-id="a49df-118">Qualquer recurso de DSC pode instruir o LCM para reiniciar o nó ao definir este sinalizador `Set-TargetResource` função.</span><span class="sxs-lookup"><span data-stu-id="a49df-118">Any DSC resource can instruct the LCM to reboot the node by setting this flag in the `Set-TargetResource` function.</span></span> <span data-ttu-id="a49df-119">Para obter mais informações, consulte [escrever um recurso personalizado do DSC com o MOF](../resources/authoringResourceMOF.md).</span><span class="sxs-lookup"><span data-stu-id="a49df-119">For more information, see [Writing a custom DSC resource with MOF](../resources/authoringResourceMOF.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="a49df-120">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a49df-120">Syntax</span></span>

```
xPendingReboot [String] #ResourceName
{
    Name = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [SkipCcmClientSDK = [bool]]
    [SkipComponentBasedServicing = [bool]]
    [SkipPendingComputerRename = [bool]]
    [SkipPendingFileRename = [bool]]
    [SkipWindowsUpdate = [bool]]
}
```

## <a name="properties"></a><span data-ttu-id="a49df-121">Propriedades</span><span class="sxs-lookup"><span data-stu-id="a49df-121">Properties</span></span>

| <span data-ttu-id="a49df-122">Propriedade</span><span class="sxs-lookup"><span data-stu-id="a49df-122">Property</span></span> | <span data-ttu-id="a49df-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="a49df-123">Description</span></span> |
| --- | --- |
| <span data-ttu-id="a49df-124">Nome</span><span class="sxs-lookup"><span data-stu-id="a49df-124">Name</span></span>| <span data-ttu-id="a49df-125">Parâmetro necessário, tem de ser exclusivo por instância do recurso dentro de uma configuração.</span><span class="sxs-lookup"><span data-stu-id="a49df-125">Required parameter that must be unique per instance of the resource within a configuration.</span></span>|
| <span data-ttu-id="a49df-126">SkipComponentBasedServicing</span><span class="sxs-lookup"><span data-stu-id="a49df-126">SkipComponentBasedServicing</span></span> | <span data-ttu-id="a49df-127">Reinícios de ignorar acionados pelo componente de serviço baseado no componente.</span><span class="sxs-lookup"><span data-stu-id="a49df-127">Skip reboots triggered by the Component-Based Servicing component.</span></span> |
| <span data-ttu-id="a49df-128">SkipWindowsUpdate</span><span class="sxs-lookup"><span data-stu-id="a49df-128">SkipWindowsUpdate</span></span> | <span data-ttu-id="a49df-129">Reinícios de ignorar acionados pelo Windows Update.</span><span class="sxs-lookup"><span data-stu-id="a49df-129">Skip reboots triggered by Windows Update.</span></span>|
| <span data-ttu-id="a49df-130">SkipPendingFileRename</span><span class="sxs-lookup"><span data-stu-id="a49df-130">SkipPendingFileRename</span></span> | <span data-ttu-id="a49df-131">Ignore reinicializações de mudança de nome de ficheiro pendente.</span><span class="sxs-lookup"><span data-stu-id="a49df-131">Skip pending file rename reboots.</span></span> |
| <span data-ttu-id="a49df-132">SkipCcmClientSDK</span><span class="sxs-lookup"><span data-stu-id="a49df-132">SkipCcmClientSDK</span></span> | <span data-ttu-id="a49df-133">Reinícios de ignorar acionados pelo cliente do ConfigMgr.</span><span class="sxs-lookup"><span data-stu-id="a49df-133">Skip reboots triggered by the ConfigMgr client.</span></span> |
| <span data-ttu-id="a49df-134">SkipComputerRename</span><span class="sxs-lookup"><span data-stu-id="a49df-134">SkipComputerRename</span></span> | <span data-ttu-id="a49df-135">Muda o nome de reinicializações de ignorar acionadas pelo computador.</span><span class="sxs-lookup"><span data-stu-id="a49df-135">Skip reboots triggered by Computer renames.</span></span> |
| <span data-ttu-id="a49df-136">PSDSCRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="a49df-136">PSDSCRunAsCredential</span></span> | <span data-ttu-id="a49df-137">Suportado no v5.</span><span class="sxs-lookup"><span data-stu-id="a49df-137">Supported in v5.</span></span> <span data-ttu-id="a49df-138">Executa o recurso como o utilizador especificado.</span><span class="sxs-lookup"><span data-stu-id="a49df-138">Executes the resource as the specified user.</span></span> |
| <span data-ttu-id="a49df-139">DependsOn</span><span class="sxs-lookup"><span data-stu-id="a49df-139">DependsOn</span></span> | <span data-ttu-id="a49df-140">Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="a49df-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a49df-141">Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será **ResourceName** e seu tipo é **ResourceType**, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="a49df-141">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> <span data-ttu-id="a49df-142">Para obter mais informações, consulte [usando DependsOn](resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="a49df-142">For more information, see [Using DependsOn](resource-depends-on.md)</span></span>|

## <a name="example"></a><span data-ttu-id="a49df-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a49df-143">Example</span></span>

<span data-ttu-id="a49df-144">O exemplo seguinte instala o Microsoft Exchange utilizando o [xExchange](https://github.com/PowerShell/xExchange) recursos.</span><span class="sxs-lookup"><span data-stu-id="a49df-144">The following example installs Microsoft Exchange using the [xExchange](https://github.com/PowerShell/xExchange) resource.</span></span>
<span data-ttu-id="a49df-145">Durante a instalação, o **xPendingReboot** recurso é utilizado para reiniciar o nó.</span><span class="sxs-lookup"><span data-stu-id="a49df-145">Throughout the install, the **xPendingReboot** resource is used to reboot the Node.</span></span>

> [!NOTE]
> <span data-ttu-id="a49df-146">Este exemplo requer a credencial de uma conta que tenha direitos para adicionar um servidor Exchange para a floresta.</span><span class="sxs-lookup"><span data-stu-id="a49df-146">This example requires the credential of an account that has rights to add an Exchange server to the forest.</span></span> <span data-ttu-id="a49df-147">Para obter mais informações sobre como utilizar as credenciais no DSC, consulte [credenciais de manipulação de mensagens em fila no DSC](../configurations/configDataCredentials.md)</span><span class="sxs-lookup"><span data-stu-id="a49df-147">For more information on using credentials in DSC, see [Handling Credentials in DSC](../configurations/configDataCredentials.md)</span></span>

```powershell
$ConfigurationData = @{
    AllNodes = @(
        @{
            NodeName                    = '*'
            PSDSCAllowPlainTextPassword = $true
        },
        @{
            NodeName = 'DSCPULL-1'
        }
    )
}

Configuration Example
{
    param
    (
        [Parameter(Mandatory = $true)]
        [System.Management.Automation.PSCredential]
        $ExchangeAdminCredential
    )

    Import-DscResource -Module xExchange
    Import-DscResource -Module xPendingReboot

    Node $AllNodes.NodeName
    {
        # Copy the Exchange setup files locally
        File ExchangeBinaries
        {
            Ensure          = 'Present'
            Type            = 'Directory'
            Recurse         = $true
            SourcePath      = '\\rras-1\Binaries\E15CU6'
            DestinationPath = 'C:\Binaries\E15CU6'
        }

        # Check if a reboot is needed before installing Exchange
        xPendingReboot BeforeExchangeInstall
        {
            Name       = 'BeforeExchangeInstall'
            DependsOn  = '[File]ExchangeBinaries'
        }

        # Do the Exchange install
        xExchInstall InstallExchange
        {
            Path       = 'C:\Binaries\E15CU6\Setup.exe'
            Arguments  = '/mode:Install /role:Mailbox /Iacceptexchangeserverlicenseterms'
            Credential = $ExchangeAdminCredential
            DependsOn  = '[xPendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        xPendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="a49df-148">Este exemplo assume que configurou o seu Gestor de configuração de Local para permitir reinícios e continuar a configuração após um reinício.</span><span class="sxs-lookup"><span data-stu-id="a49df-148">This example assumes that you have configured your Local Configuration Manager to allow reboots and continue the configuration after a reboot.</span></span>

## <a name="where-to-download"></a><span data-ttu-id="a49df-149">Onde pode transferir</span><span class="sxs-lookup"><span data-stu-id="a49df-149">Where to Download</span></span>

<span data-ttu-id="a49df-150">Pode transferir os recursos utilizados neste tópico nas seguintes localizações ou através da galeria do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a49df-150">You can download the resources used in this topic at the following locations, or by using the PowerShell gallery.</span></span>

- [<span data-ttu-id="a49df-151">xPendingReboot</span><span class="sxs-lookup"><span data-stu-id="a49df-151">xPendingReboot</span></span>](https://github.com/PowerShell/xPendingReboot)
- [<span data-ttu-id="a49df-152">xExchange</span><span class="sxs-lookup"><span data-stu-id="a49df-152">xExchange</span></span>](https://github.com/PowerShell/xExchange)
