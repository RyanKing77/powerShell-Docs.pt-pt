---
ms.date: 07/10/2019
keywords: Jea, PowerShell, segurança
title: Registrando configurações do JEA
ms.openlocfilehash: c85eddea2196e4db4bbeea54bde11074f3d1c927
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017868"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="962cb-103">Registrando configurações do JEA</span><span class="sxs-lookup"><span data-stu-id="962cb-103">Registering JEA Configurations</span></span>

<span data-ttu-id="962cb-104">Depois que você tiver os [recursos de função](role-capabilities.md) e o arquivo de configuração de [sessão](session-configurations.md) criados, a última etapa será registrar o ponto de extremidade Jea.</span><span class="sxs-lookup"><span data-stu-id="962cb-104">Once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created, the last step is to register the JEA endpoint.</span></span> <span data-ttu-id="962cb-105">Registrar o ponto de extremidade JEA com o sistema torna o ponto de extremidade disponível para uso por usuários e mecanismos de automação.</span><span class="sxs-lookup"><span data-stu-id="962cb-105">Registering the JEA endpoint with the system makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="962cb-106">Configuração de computador único</span><span class="sxs-lookup"><span data-stu-id="962cb-106">Single machine configuration</span></span>

<span data-ttu-id="962cb-107">Para ambientes pequenos, você pode implantar o JEA registrando o arquivo de configuração de sessão usando o cmdlet [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) .</span><span class="sxs-lookup"><span data-stu-id="962cb-107">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="962cb-108">Antes de começar, verifique se os seguintes pré-requisitos foram atendidos:</span><span class="sxs-lookup"><span data-stu-id="962cb-108">Before you begin, ensure that the following prerequisites have been met:</span></span>

- <span data-ttu-id="962cb-109">Uma ou mais funções foram criadas e colocadas na pasta **RoleCapabilities** de um módulo do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="962cb-109">One or more roles has been created and placed in the **RoleCapabilities** folder of a PowerShell module.</span></span>
- <span data-ttu-id="962cb-110">Um arquivo de configuração de sessão foi criado e testado.</span><span class="sxs-lookup"><span data-stu-id="962cb-110">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="962cb-111">O usuário que está registrando a configuração JEA tem direitos de administrador no sistema.</span><span class="sxs-lookup"><span data-stu-id="962cb-111">The user registering the JEA configuration has administrator rights on the system.</span></span>
- <span data-ttu-id="962cb-112">Você selecionou um nome para o ponto de extremidade JEA.</span><span class="sxs-lookup"><span data-stu-id="962cb-112">You've selected a name for your JEA endpoint.</span></span>

<span data-ttu-id="962cb-113">O nome do ponto de extremidade JEA é necessário quando os usuários se conectam ao sistema usando o JEA.</span><span class="sxs-lookup"><span data-stu-id="962cb-113">The name of the JEA endpoint is required when users connect to the system using JEA.</span></span> <span data-ttu-id="962cb-114">O cmdlet [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) lista os nomes dos pontos de extremidade em um sistema.</span><span class="sxs-lookup"><span data-stu-id="962cb-114">The [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet lists the names of the endpoints on a system.</span></span> <span data-ttu-id="962cb-115">Os pontos de extremidade que começam `microsoft` com o normalmente são fornecidos com o Windows.</span><span class="sxs-lookup"><span data-stu-id="962cb-115">Endpoints that start with `microsoft` are typically shipped with Windows.</span></span> <span data-ttu-id="962cb-116">O `microsoft.powershell` ponto de extremidade é o ponto de extremidade padrão usado ao se conectar a um ponto de extremidade do PowerShell remoto.</span><span class="sxs-lookup"><span data-stu-id="962cb-116">The `microsoft.powershell` endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

```powershell
Get-PSSessionConfiguration | Select-Object Name
```

```Output
Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

<span data-ttu-id="962cb-117">Execute o comando a seguir para registrar o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="962cb-117">Run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="962cb-118">O comando anterior reinicia o serviço WinRM no sistema.</span><span class="sxs-lookup"><span data-stu-id="962cb-118">The previous command restarts the WinRM service on the system.</span></span> <span data-ttu-id="962cb-119">Isso encerra todas as sessões de comunicação remota do PowerShell e todas as configurações de DSC em andamento.</span><span class="sxs-lookup"><span data-stu-id="962cb-119">This terminates all PowerShell remoting sessions and any ongoing DSC configurations.</span></span> <span data-ttu-id="962cb-120">Recomendamos que você coloque as máquinas de produção offline antes de executar o comando para evitar a interrupção das operações de negócios.</span><span class="sxs-lookup"><span data-stu-id="962cb-120">We recommended you take production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="962cb-121">Após o registro, você estará pronto para [usar o Jea](using-jea.md).</span><span class="sxs-lookup"><span data-stu-id="962cb-121">After registration, you're ready to [use JEA](using-jea.md).</span></span> <span data-ttu-id="962cb-122">Você pode excluir o arquivo de configuração de sessão a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="962cb-122">You may delete the session configuration file at any time.</span></span> <span data-ttu-id="962cb-123">O arquivo de configuração não é usado após o registro do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="962cb-123">The configuration file isn't used after registration of the endpoint.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="962cb-124">Configuração de vários computadores com DSC</span><span class="sxs-lookup"><span data-stu-id="962cb-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="962cb-125">Ao implantar o JEA em vários computadores, o modelo de implantação mais simples usa o recurso de [configuração de estado desejado (DSC)](/powershell/dsc/overview) do Jea para implantar de forma rápida e consistente o Jea em cada computador.</span><span class="sxs-lookup"><span data-stu-id="962cb-125">When deploying JEA on multiple machines, the simplest deployment model uses the JEA [Desired State Configuration (DSC)](/powershell/dsc/overview) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="962cb-126">Para implantar o JEA com o DSC, verifique se os seguintes pré-requisitos foram atendidos:</span><span class="sxs-lookup"><span data-stu-id="962cb-126">To deploy JEA with DSC, ensure the following prerequisites are met:</span></span>

- <span data-ttu-id="962cb-127">Um ou mais recursos de função foram criados e adicionados a um módulo do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="962cb-127">One or more role capabilities have been authored and added to a PowerShell module.</span></span>
- <span data-ttu-id="962cb-128">O módulo do PowerShell que contém as funções é armazenado em um compartilhamento de arquivos (somente leitura) acessível por cada computador.</span><span class="sxs-lookup"><span data-stu-id="962cb-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="962cb-129">As configurações para a configuração de sessão foram determinadas.</span><span class="sxs-lookup"><span data-stu-id="962cb-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="962cb-130">Você não precisa criar um arquivo de configuração de sessão ao usar o recurso DSC JEA.</span><span class="sxs-lookup"><span data-stu-id="962cb-130">You don't need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="962cb-131">Você tem credenciais que permitem ações administrativas em cada computador ou acesso ao servidor de pull de DSC usado para gerenciar os computadores.</span><span class="sxs-lookup"><span data-stu-id="962cb-131">You have credentials that allow administrative actions on each machine or access to the DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="962cb-132">Você baixou o [recurso DSC Jea](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource).</span><span class="sxs-lookup"><span data-stu-id="962cb-132">You've downloaded the [JEA DSC resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource).</span></span>

<span data-ttu-id="962cb-133">Crie uma configuração DSC para o ponto de extremidade do JEA em um computador de destino ou servidor de pull.</span><span class="sxs-lookup"><span data-stu-id="962cb-133">Create a DSC configuration for your JEA endpoint on a target machine or pull server.</span></span> <span data-ttu-id="962cb-134">Nessa configuração, o recurso DSC **JustEnoughAdministration** define o arquivo de configuração de sessão e o recurso de **arquivo** copia os recursos de função do compartilhamento de arquivos.</span><span class="sxs-lookup"><span data-stu-id="962cb-134">In this configuration, the **JustEnoughAdministration** DSC resource defines the session configuration file and the **File** resource copies the role capabilities from the file share.</span></span>

<span data-ttu-id="962cb-135">As propriedades a seguir são configuráveis usando o recurso de DSC:</span><span class="sxs-lookup"><span data-stu-id="962cb-135">The following properties are configurable using the DSC resource:</span></span>

- <span data-ttu-id="962cb-136">Definições de função</span><span class="sxs-lookup"><span data-stu-id="962cb-136">Role Definitions</span></span>
- <span data-ttu-id="962cb-137">Grupos de contas virtuais</span><span class="sxs-lookup"><span data-stu-id="962cb-137">Virtual account groups</span></span>
- <span data-ttu-id="962cb-138">Grupo-nome da conta de serviço gerenciado</span><span class="sxs-lookup"><span data-stu-id="962cb-138">Group-managed service account name</span></span>
- <span data-ttu-id="962cb-139">Diretório de transcrição</span><span class="sxs-lookup"><span data-stu-id="962cb-139">Transcript directory</span></span>
- <span data-ttu-id="962cb-140">Unidade do usuário</span><span class="sxs-lookup"><span data-stu-id="962cb-140">User drive</span></span>
- <span data-ttu-id="962cb-141">Regras de acesso condicional</span><span class="sxs-lookup"><span data-stu-id="962cb-141">Conditional access rules</span></span>
- <span data-ttu-id="962cb-142">Scripts de inicialização para a sessão JEA</span><span class="sxs-lookup"><span data-stu-id="962cb-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="962cb-143">A sintaxe para cada uma dessas propriedades em uma configuração DSC é consistente com o arquivo de configuração de sessão do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="962cb-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="962cb-144">Veja abaixo uma configuração de DSC de exemplo para um módulo de manutenção geral do servidor.</span><span class="sxs-lookup"><span data-stu-id="962cb-144">Below is a sample DSC configuration for a general server maintenance module.</span></span> <span data-ttu-id="962cb-145">Ele assume que um módulo válido do PowerShell contendo recursos de função está localizado `\\myfileshare\JEA` no compartilhamento de arquivos.</span><span class="sxs-lookup"><span data-stu-id="962cb-145">It assumes that a valid PowerShell module containing role capabilities is located on the `\\myfileshare\JEA` file share.</span></span>

```powershell
Configuration JEAMaintenance
{
    Import-DscResource -Module JustEnoughAdministration, PSDesiredStateConfiguration

    File MaintenanceModule
    {
        SourcePath = "\\myfileshare\JEA\ContosoMaintenance"
        DestinationPath = "C:\Program Files\WindowsPowerShell\Modules\ContosoMaintenance"
        Checksum = "SHA-256"
        Ensure = "Present"
        Type = "Directory"
        Recurse = $true
    }

    JeaEndpoint JEAMaintenanceEndpoint
    {
        EndpointName = "JEAMaintenance"
        RoleDefinitions = "@{ 'CONTOSO\JEAMaintenanceAuditors' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit' }; 'CONTOSO\JEAMaintenanceAdmins' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit', 'GeneralServerMaintenance-Admin' } }"
        TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
        DependsOn = '[File]MaintenanceModule'
    }
}
```

<span data-ttu-id="962cb-146">Em seguida, a configuração é aplicada em um sistema invocando diretamente o [Configuration Manager local](/powershell/dsc/managing-nodes/metaConfig) ou atualizando a [configuração do servidor de pull](/powershell/dsc/pull-server/pullServer).</span><span class="sxs-lookup"><span data-stu-id="962cb-146">Next, the configuration is applied on a system by directly invoking the [Local Configuration Manager](/powershell/dsc/managing-nodes/metaConfig) or updating the [pull server configuration](/powershell/dsc/pull-server/pullServer).</span></span>

<span data-ttu-id="962cb-147">O recurso DSC também permite que você substitua o ponto de extremidade do **Microsoft. PowerShell** padrão.</span><span class="sxs-lookup"><span data-stu-id="962cb-147">The DSC resource also allows you to replace the default **Microsoft.PowerShell** endpoint.</span></span> <span data-ttu-id="962cb-148">Quando substituído, o recurso registra automaticamente um ponto de extremidade de backup chamado **Microsoft. PowerShell. Restricted**.</span><span class="sxs-lookup"><span data-stu-id="962cb-148">When replaced, the resource automatically registers a backup endpoint named **Microsoft.PowerShell.Restricted**.</span></span> <span data-ttu-id="962cb-149">O ponto de extremidade de backup tem a ACL padrão do WinRM que permite que usuários de gerenciamento remoto e membros do grupo de administradores locais o acessem.</span><span class="sxs-lookup"><span data-stu-id="962cb-149">The backup endpoint has the default WinRM ACL that allows Remote Management Users and local Administrators group members to access it.</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="962cb-150">Cancelando o registro de configurações do JEA</span><span class="sxs-lookup"><span data-stu-id="962cb-150">Unregistering JEA configurations</span></span>

<span data-ttu-id="962cb-151">O cmdlet [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) remove um ponto de extremidade Jea.</span><span class="sxs-lookup"><span data-stu-id="962cb-151">The [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet removes a JEA endpoint.</span></span> <span data-ttu-id="962cb-152">Cancelar o registro de um ponto de extremidade JEA impede que novos usuários criem novas sessões do JEA no sistema.</span><span class="sxs-lookup"><span data-stu-id="962cb-152">Unregistering a JEA endpoint prevents new users from creating new JEA sessions on the system.</span></span> <span data-ttu-id="962cb-153">Ele também permite que você atualize uma configuração do JEA registrando novamente um arquivo de configuração de sessão atualizado usando o mesmo nome de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="962cb-153">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="962cb-154">Cancelar o registro de um ponto de extremidade JEA faz com que o serviço WinRM seja reiniciado.</span><span class="sxs-lookup"><span data-stu-id="962cb-154">Unregistering a JEA endpoint causes the WinRM service to restart.</span></span> <span data-ttu-id="962cb-155">Isso interrompe a maioria das operações de gerenciamento remoto em andamento, incluindo outras sessões do PowerShell, invocações de WMI e algumas ferramentas de gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="962cb-155">This interrupts most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span> <span data-ttu-id="962cb-156">Cancele o registro somente dos pontos de extremidade do PowerShell durante as janelas de manutenção planejadas.</span><span class="sxs-lookup"><span data-stu-id="962cb-156">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="962cb-157">Passos Seguintes</span><span class="sxs-lookup"><span data-stu-id="962cb-157">Next steps</span></span>

[<span data-ttu-id="962cb-158">Testar o ponto de extremidade JEA</span><span class="sxs-lookup"><span data-stu-id="962cb-158">Test the JEA endpoint</span></span>](using-jea.md)
