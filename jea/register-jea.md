---
ms.date: 07/10/2019
keywords: jea, powershell, segurança
title: Registar a JEA configurações
ms.openlocfilehash: c85eddea2196e4db4bbeea54bde11074f3d1c927
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726626"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="40c0a-103">Registar a JEA configurações</span><span class="sxs-lookup"><span data-stu-id="40c0a-103">Registering JEA Configurations</span></span>

<span data-ttu-id="40c0a-104">Depois de ter sua [funcionalidades de função](role-capabilities.md) e [o ficheiro de configuração de sessão](session-configurations.md) criado, a última etapa é registar o ponto final JEA.</span><span class="sxs-lookup"><span data-stu-id="40c0a-104">Once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created, the last step is to register the JEA endpoint.</span></span> <span data-ttu-id="40c0a-105">Registar o ponto final da JEA com o sistema faz com que o ponto final disponíveis para utilização por utilizadores e os mecanismos de automatização.</span><span class="sxs-lookup"><span data-stu-id="40c0a-105">Registering the JEA endpoint with the system makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="40c0a-106">Configuração de máquina única</span><span class="sxs-lookup"><span data-stu-id="40c0a-106">Single machine configuration</span></span>

<span data-ttu-id="40c0a-107">Em ambientes pequenos, pode implementar a JEA registrando-se a configuração de sessão ficheiro com o [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="40c0a-107">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="40c0a-108">Antes de começar, certifique-se de que os seguintes pré-requisitos foram cumpridos:</span><span class="sxs-lookup"><span data-stu-id="40c0a-108">Before you begin, ensure that the following prerequisites have been met:</span></span>

- <span data-ttu-id="40c0a-109">Foi criado e colocado numa ou mais funções do **RoleCapabilities** pasta de um módulo do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="40c0a-109">One or more roles has been created and placed in the **RoleCapabilities** folder of a PowerShell module.</span></span>
- <span data-ttu-id="40c0a-110">Um ficheiro de configuração de sessão tem de ser criado e testado.</span><span class="sxs-lookup"><span data-stu-id="40c0a-110">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="40c0a-111">O utilizador a que se registe a configuração de JEA tem direitos de administrador no sistema.</span><span class="sxs-lookup"><span data-stu-id="40c0a-111">The user registering the JEA configuration has administrator rights on the system.</span></span>
- <span data-ttu-id="40c0a-112">Selecionar um nome para o ponto de final JEA.</span><span class="sxs-lookup"><span data-stu-id="40c0a-112">You've selected a name for your JEA endpoint.</span></span>

<span data-ttu-id="40c0a-113">É necessário o nome do ponto final JEA quando os utilizadores ligam ao sistema de utilizar a JEA.</span><span class="sxs-lookup"><span data-stu-id="40c0a-113">The name of the JEA endpoint is required when users connect to the system using JEA.</span></span> <span data-ttu-id="40c0a-114">O [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet apresenta uma lista os nomes dos pontos de extremidade num sistema.</span><span class="sxs-lookup"><span data-stu-id="40c0a-114">The [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet lists the names of the endpoints on a system.</span></span> <span data-ttu-id="40c0a-115">Pontos finais que iniciam com `microsoft` normalmente são fornecidos com o Windows.</span><span class="sxs-lookup"><span data-stu-id="40c0a-115">Endpoints that start with `microsoft` are typically shipped with Windows.</span></span> <span data-ttu-id="40c0a-116">O `microsoft.powershell` ponto final é o ponto final predefinido utilizado ao ligar a um ponto de extremidade remoto do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="40c0a-116">The `microsoft.powershell` endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

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

<span data-ttu-id="40c0a-117">Execute o seguinte comando para registar o ponto final.</span><span class="sxs-lookup"><span data-stu-id="40c0a-117">Run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="40c0a-118">O comando anterior reinicia o serviço de WinRM no sistema.</span><span class="sxs-lookup"><span data-stu-id="40c0a-118">The previous command restarts the WinRM service on the system.</span></span> <span data-ttu-id="40c0a-119">Isso encerra a todas as sessões de comunicação remota do PowerShell e quaisquer configurações de DSC em curso.</span><span class="sxs-lookup"><span data-stu-id="40c0a-119">This terminates all PowerShell remoting sessions and any ongoing DSC configurations.</span></span> <span data-ttu-id="40c0a-120">Recomendamos que colocar máquinas de produção offline antes de executar o comando para evitar interromper as operações de negócio.</span><span class="sxs-lookup"><span data-stu-id="40c0a-120">We recommended you take production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="40c0a-121">Após o registo, está pronto para [utilizar a JEA](using-jea.md).</span><span class="sxs-lookup"><span data-stu-id="40c0a-121">After registration, you're ready to [use JEA](using-jea.md).</span></span> <span data-ttu-id="40c0a-122">Pode eliminar o ficheiro de configuração de sessão em qualquer altura.</span><span class="sxs-lookup"><span data-stu-id="40c0a-122">You may delete the session configuration file at any time.</span></span> <span data-ttu-id="40c0a-123">O ficheiro de configuração não é usado após o registo do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="40c0a-123">The configuration file isn't used after registration of the endpoint.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="40c0a-124">Configuração de várias máquinas com DSC</span><span class="sxs-lookup"><span data-stu-id="40c0a-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="40c0a-125">Ao implementar a JEA em várias máquinas, o modelo de implementação mais simples, usa o JEA [Desired State Configuration (DSC)](/powershell/dsc/overview) recursos para implementar rápida e consistentemente JEA em cada máquina.</span><span class="sxs-lookup"><span data-stu-id="40c0a-125">When deploying JEA on multiple machines, the simplest deployment model uses the JEA [Desired State Configuration (DSC)](/powershell/dsc/overview) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="40c0a-126">Para implementar a JEA com DSC, certifique-se de que são cumpridos os seguintes pré-requisitos:</span><span class="sxs-lookup"><span data-stu-id="40c0a-126">To deploy JEA with DSC, ensure the following prerequisites are met:</span></span>

- <span data-ttu-id="40c0a-127">Um ou mais funcionalidades de função foram criadas e adicionadas a um módulo do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="40c0a-127">One or more role capabilities have been authored and added to a PowerShell module.</span></span>
- <span data-ttu-id="40c0a-128">O módulo do PowerShell que contém as funções é armazenado numa partilha de ficheiros (só de leitura) acessível por cada máquina.</span><span class="sxs-lookup"><span data-stu-id="40c0a-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="40c0a-129">Definições para a configuração de sessão foram identificadas.</span><span class="sxs-lookup"><span data-stu-id="40c0a-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="40c0a-130">Não precisa de criar um ficheiro de configuração de sessão ao usar o recurso de DSC de JEA.</span><span class="sxs-lookup"><span data-stu-id="40c0a-130">You don't need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="40c0a-131">Tem as credenciais que permitem que as ações administrativas em cada máquina ou o acesso ao servidor de solicitação do DSC utilizado para gerir as máquinas.</span><span class="sxs-lookup"><span data-stu-id="40c0a-131">You have credentials that allow administrative actions on each machine or access to the DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="40c0a-132">Baixar o [recursos de DSC de JEA](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource).</span><span class="sxs-lookup"><span data-stu-id="40c0a-132">You've downloaded the [JEA DSC resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource).</span></span>

<span data-ttu-id="40c0a-133">Crie uma configuração de DSC para o ponto de final JEA num servidor de destino máquina ou pull.</span><span class="sxs-lookup"><span data-stu-id="40c0a-133">Create a DSC configuration for your JEA endpoint on a target machine or pull server.</span></span> <span data-ttu-id="40c0a-134">Nesta configuração, o **JustEnoughAdministration** recursos de DSC define o ficheiro de configuração de sessão e a **ficheiro** recurso copia as capacidades de função da partilha de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="40c0a-134">In this configuration, the **JustEnoughAdministration** DSC resource defines the session configuration file and the **File** resource copies the role capabilities from the file share.</span></span>

<span data-ttu-id="40c0a-135">As seguintes propriedades são configuráveis com o recurso de DSC:</span><span class="sxs-lookup"><span data-stu-id="40c0a-135">The following properties are configurable using the DSC resource:</span></span>

- <span data-ttu-id="40c0a-136">Definições de funções</span><span class="sxs-lookup"><span data-stu-id="40c0a-136">Role Definitions</span></span>
- <span data-ttu-id="40c0a-137">Grupos de conta virtual</span><span class="sxs-lookup"><span data-stu-id="40c0a-137">Virtual account groups</span></span>
- <span data-ttu-id="40c0a-138">Nome da conta de serviço gerida de grupo</span><span class="sxs-lookup"><span data-stu-id="40c0a-138">Group-managed service account name</span></span>
- <span data-ttu-id="40c0a-139">Diretório de transcrição</span><span class="sxs-lookup"><span data-stu-id="40c0a-139">Transcript directory</span></span>
- <span data-ttu-id="40c0a-140">Unidade de utilizador</span><span class="sxs-lookup"><span data-stu-id="40c0a-140">User drive</span></span>
- <span data-ttu-id="40c0a-141">Regras de acesso condicional</span><span class="sxs-lookup"><span data-stu-id="40c0a-141">Conditional access rules</span></span>
- <span data-ttu-id="40c0a-142">Scripts de inicialização para a sessão JEA</span><span class="sxs-lookup"><span data-stu-id="40c0a-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="40c0a-143">A sintaxe para cada uma dessas propriedades numa configuração de DSC é consistente com o ficheiro de configuração de sessão do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="40c0a-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="40c0a-144">Segue-se um exemplo de configuração de DSC para um módulo de manutenção geral do servidor.</span><span class="sxs-lookup"><span data-stu-id="40c0a-144">Below is a sample DSC configuration for a general server maintenance module.</span></span> <span data-ttu-id="40c0a-145">Parte do princípio de que um módulo do PowerShell válido que contém funcionalidades de função está localizado no `\\myfileshare\JEA` partilha de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="40c0a-145">It assumes that a valid PowerShell module containing role capabilities is located on the `\\myfileshare\JEA` file share.</span></span>

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

<span data-ttu-id="40c0a-146">Em seguida, a configuração é aplicada num sistema invocando diretamente o [Gestor de configuração Local](/powershell/dsc/managing-nodes/metaConfig) ou a atualizar a [configuração de servidor pull](/powershell/dsc/pull-server/pullServer).</span><span class="sxs-lookup"><span data-stu-id="40c0a-146">Next, the configuration is applied on a system by directly invoking the [Local Configuration Manager](/powershell/dsc/managing-nodes/metaConfig) or updating the [pull server configuration](/powershell/dsc/pull-server/pullServer).</span></span>

<span data-ttu-id="40c0a-147">O recurso de DSC também permite-lhe substituir a predefinição **Microsoft** ponto final.</span><span class="sxs-lookup"><span data-stu-id="40c0a-147">The DSC resource also allows you to replace the default **Microsoft.PowerShell** endpoint.</span></span> <span data-ttu-id="40c0a-148">Quando substituído, o recurso regista automaticamente um ponto de final de cópia de segurança com o nome **Microsoft.PowerShell.Restricted**.</span><span class="sxs-lookup"><span data-stu-id="40c0a-148">When replaced, the resource automatically registers a backup endpoint named **Microsoft.PowerShell.Restricted**.</span></span> <span data-ttu-id="40c0a-149">O ponto de final de cópia de segurança tem a ACL de WinRM que permite que utilizadores de gestão remota e os administradores locais membros do grupo para aceder ao mesmo padrão.</span><span class="sxs-lookup"><span data-stu-id="40c0a-149">The backup endpoint has the default WinRM ACL that allows Remote Management Users and local Administrators group members to access it.</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="40c0a-150">A anular o registo configurações de JEA</span><span class="sxs-lookup"><span data-stu-id="40c0a-150">Unregistering JEA configurations</span></span>

<span data-ttu-id="40c0a-151">O [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet Remove um ponto final JEA.</span><span class="sxs-lookup"><span data-stu-id="40c0a-151">The [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet removes a JEA endpoint.</span></span> <span data-ttu-id="40c0a-152">Anular o registo de um ponto final JEA impede que novos usuários a criação de novas sessões JEA no sistema.</span><span class="sxs-lookup"><span data-stu-id="40c0a-152">Unregistering a JEA endpoint prevents new users from creating new JEA sessions on the system.</span></span> <span data-ttu-id="40c0a-153">Ele também permite-lhe atualizar uma configuração de JEA registando novamente um arquivo de configuração de sessão atualizadas utilizando o mesmo nome de ponto final.</span><span class="sxs-lookup"><span data-stu-id="40c0a-153">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="40c0a-154">Ponto final de anular o registo de um JEA faz com que o serviço WinRM seja reiniciado.</span><span class="sxs-lookup"><span data-stu-id="40c0a-154">Unregistering a JEA endpoint causes the WinRM service to restart.</span></span> <span data-ttu-id="40c0a-155">Isso interrompe remotas mais operações de gestão em curso, incluindo outras sessões do PowerShell, invocações do WMI e algumas ferramentas de gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="40c0a-155">This interrupts most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span> <span data-ttu-id="40c0a-156">Anular o registo apenas pontos finais do PowerShell durante as janelas de manutenção planeada.</span><span class="sxs-lookup"><span data-stu-id="40c0a-156">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="40c0a-157">Passos Seguintes</span><span class="sxs-lookup"><span data-stu-id="40c0a-157">Next steps</span></span>

[<span data-ttu-id="40c0a-158">Testar o ponto final da JEA</span><span class="sxs-lookup"><span data-stu-id="40c0a-158">Test the JEA endpoint</span></span>](using-jea.md)
