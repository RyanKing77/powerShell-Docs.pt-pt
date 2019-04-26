---
ms.date: 06/12/2017
keywords: jea, powershell, segurança
title: Registar a JEA configurações
ms.openlocfilehash: 6fa0ce434c8e70eb718545e99417bfe034cda6bf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084832"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="7d05f-103">Registar a JEA configurações</span><span class="sxs-lookup"><span data-stu-id="7d05f-103">Registering JEA Configurations</span></span>

> <span data-ttu-id="7d05f-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7d05f-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="7d05f-105">Depois de ter sua [funcionalidades de função](role-capabilities.md) e [o ficheiro de configuração de sessão](session-configurations.md) criado, a última etapa antes de poder utilizar o JEA é registar o ponto final JEA.</span><span class="sxs-lookup"><span data-stu-id="7d05f-105">Once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created, the last step before you can use JEA is to register the JEA endpoint.</span></span>
<span data-ttu-id="7d05f-106">Registar o ponto final da JEA com o sistema faz com que o ponto final disponíveis para utilização por utilizadores e os mecanismos de automatização.</span><span class="sxs-lookup"><span data-stu-id="7d05f-106">Registering the JEA endpoint with the system makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="7d05f-107">Configuração de máquina única</span><span class="sxs-lookup"><span data-stu-id="7d05f-107">Single machine configuration</span></span>

<span data-ttu-id="7d05f-108">Em ambientes pequenos, pode implementar a JEA registrando-se a configuração de sessão ficheiro com o [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7d05f-108">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="7d05f-109">Antes de começar, certifique-se de que os seguintes pré-requisitos foram cumpridos:</span><span class="sxs-lookup"><span data-stu-id="7d05f-109">Before you begin, ensure that the following prerequisites have been met:</span></span>
- <span data-ttu-id="7d05f-110">Uma ou mais funções foi criado e colocado na pasta "RoleCapabilities" de um módulo do PowerShell válida.</span><span class="sxs-lookup"><span data-stu-id="7d05f-110">One or more roles has been created and placed in the 'RoleCapabilities' folder of a valid PowerShell module.</span></span>
- <span data-ttu-id="7d05f-111">Um ficheiro de configuração de sessão tem de ser criado e testado.</span><span class="sxs-lookup"><span data-stu-id="7d05f-111">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="7d05f-112">O utilizador a que se registe a configuração de JEA tem direitos de administrador sobre os sistemas.</span><span class="sxs-lookup"><span data-stu-id="7d05f-112">The user registering the JEA configuration has administrator rights on the system(s).</span></span>

<span data-ttu-id="7d05f-113">Também tem de selecionar um nome para o ponto de final JEA.</span><span class="sxs-lookup"><span data-stu-id="7d05f-113">You also need to select a name for your JEA endpoint.</span></span>
<span data-ttu-id="7d05f-114">É necessário o nome do ponto final JEA quando os utilizadores se quer ligar ao sistema através de JEA.</span><span class="sxs-lookup"><span data-stu-id="7d05f-114">The name of the JEA endpoint is required when users want to connect to the system using JEA.</span></span>
<span data-ttu-id="7d05f-115">Pode utilizar o [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet para verificar os nomes dos pontos finais existentes no sistema.</span><span class="sxs-lookup"><span data-stu-id="7d05f-115">You can use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet to check the names of existing endpoints on the system.</span></span>
<span data-ttu-id="7d05f-116">Pontos de extremidade que começam por "microsoft", normalmente, são fornecidos com o Windows.</span><span class="sxs-lookup"><span data-stu-id="7d05f-116">Endpoints that start with 'microsoft' are typically shipped with Windows.</span></span>
<span data-ttu-id="7d05f-117">O ponto final de "Microsoft" é o ponto final predefinido utilizado ao ligar a um ponto de extremidade remoto do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7d05f-117">The 'microsoft.powershell' endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

<span data-ttu-id="7d05f-118">Quando determinar um nome apropriado para seu ponto final da JEA, execute o seguinte comando para registar o ponto final.</span><span class="sxs-lookup"><span data-stu-id="7d05f-118">When you have determined an appropriate name for your JEA endpoint, run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="7d05f-119">O comando acima reinicia o serviço de WinRM no sistema.</span><span class="sxs-lookup"><span data-stu-id="7d05f-119">The above command restarts the WinRM service on the system.</span></span>
> <span data-ttu-id="7d05f-120">Isso encerra a todas as sessões de comunicação remota do PowerShell, bem como quaisquer configurações de DSC em curso.</span><span class="sxs-lookup"><span data-stu-id="7d05f-120">This terminates all PowerShell remoting sessions as well as any ongoing DSC configurations.</span></span>
> <span data-ttu-id="7d05f-121">Recomenda-se que colocar qualquer máquinas de produção offline antes de executar o comando para evitar interromper as operações de negócio.</span><span class="sxs-lookup"><span data-stu-id="7d05f-121">It is recommended that you take any production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="7d05f-122">Se o registo é concluída com êxito, está pronto para [utilizar a JEA](using-jea.md).</span><span class="sxs-lookup"><span data-stu-id="7d05f-122">If registration is successful, you are ready to [use JEA](using-jea.md).</span></span>
<span data-ttu-id="7d05f-123">Pode eliminar o ficheiro de configuração de sessão em qualquer altura; Não é utilizado após o registo do ponto final.</span><span class="sxs-lookup"><span data-stu-id="7d05f-123">You may delete the session configuration file at any time; it is not used after registration of the end point.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="7d05f-124">Configuração de várias máquinas com DSC</span><span class="sxs-lookup"><span data-stu-id="7d05f-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="7d05f-125">Se estiver implantando JEA em várias máquinas, o modelo de implementação mais simples consiste em utilizar a JEA [Desired State Configuration do](https://msdn.microsoft.com/powershell/dsc/overview) recursos para implementar rápida e consistentemente JEA em cada máquina.</span><span class="sxs-lookup"><span data-stu-id="7d05f-125">If you are deploying JEA on multiple machines, the simplest deployment model is to use the JEA [Desired State Configuration](https://msdn.microsoft.com/powershell/dsc/overview) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="7d05f-126">Para implementar a JEA com DSC, terá de garantir que são cumpridos os seguintes pré-requisitos:</span><span class="sxs-lookup"><span data-stu-id="7d05f-126">To deploy JEA with DSC, you need to ensure the following prerequisites are met:</span></span>
- <span data-ttu-id="7d05f-127">Um ou mais funcionalidades de função foram criadas e adicionadas a um módulo do PowerShell válido.</span><span class="sxs-lookup"><span data-stu-id="7d05f-127">One or more role capabilities have been authored and added to a valid PowerShell module.</span></span>
- <span data-ttu-id="7d05f-128">O módulo do PowerShell que contém as funções é armazenado numa partilha de ficheiros (só de leitura) acessível por cada máquina.</span><span class="sxs-lookup"><span data-stu-id="7d05f-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="7d05f-129">Definições para a configuração de sessão foram identificadas.</span><span class="sxs-lookup"><span data-stu-id="7d05f-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="7d05f-130">Não é necessário criar um ficheiro de configuração de sessão ao usar o recurso de DSC de JEA.</span><span class="sxs-lookup"><span data-stu-id="7d05f-130">You do not need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="7d05f-131">Tem as credenciais que permitem-lhe efetuar ações administrativas em cada máquina ou ter acesso a um servidor de solicitação de DSC utilizado para gerir as máquinas.</span><span class="sxs-lookup"><span data-stu-id="7d05f-131">You have credentials that allow you to perform administrative actions on each machine, or have access to a DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="7d05f-132">Transferir o [recursos de DSC de JEA](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span><span class="sxs-lookup"><span data-stu-id="7d05f-132">You have downloaded the [JEA DSC resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span></span>

<span data-ttu-id="7d05f-133">Num destino máquina (ou servidor de solicitação, se estiver a utilizar um), crie uma configuração de DSC para o ponto de final JEA.</span><span class="sxs-lookup"><span data-stu-id="7d05f-133">On a target machine (or pull server, if you are using one), create a DSC configuration for your JEA endpoint.</span></span>
<span data-ttu-id="7d05f-134">Nesta configuração, utilize o recurso de DSC JustEnoughAdministration para configurar o ficheiro de configuração de sessão e o recurso de ficheiro para copiar em relação aos recursos de função da partilha de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="7d05f-134">In this configuration, you use the JustEnoughAdministration DSC resource to set up the session configuration file and the File resource to copy over the role capabilities from the file share.</span></span>

<span data-ttu-id="7d05f-135">As seguintes propriedades são configuráveis com o recurso de DSC:</span><span class="sxs-lookup"><span data-stu-id="7d05f-135">The following properties are configurable using the DSC resource:</span></span>
- <span data-ttu-id="7d05f-136">Definições de funções</span><span class="sxs-lookup"><span data-stu-id="7d05f-136">Role Definitions</span></span>
- <span data-ttu-id="7d05f-137">Grupos de conta virtual</span><span class="sxs-lookup"><span data-stu-id="7d05f-137">Virtual Account groups</span></span>
- <span data-ttu-id="7d05f-138">Nome de conta de serviço gerida de grupo</span><span class="sxs-lookup"><span data-stu-id="7d05f-138">Group Managed Service Account name</span></span>
- <span data-ttu-id="7d05f-139">Diretório de transcrição</span><span class="sxs-lookup"><span data-stu-id="7d05f-139">Transcript directory</span></span>
- <span data-ttu-id="7d05f-140">Unidade de utilizador</span><span class="sxs-lookup"><span data-stu-id="7d05f-140">User drive</span></span>
- <span data-ttu-id="7d05f-141">Regras de acesso condicional</span><span class="sxs-lookup"><span data-stu-id="7d05f-141">Conditional access rules</span></span>
- <span data-ttu-id="7d05f-142">Scripts de inicialização para a sessão JEA</span><span class="sxs-lookup"><span data-stu-id="7d05f-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="7d05f-143">A sintaxe para cada uma dessas propriedades numa configuração de DSC é consistente com o ficheiro de configuração de sessão do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7d05f-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="7d05f-144">Segue-se um exemplo de configuração de DSC para um módulo de manutenção geral do servidor.</span><span class="sxs-lookup"><span data-stu-id="7d05f-144">Below is a sample DSC configuration for a general server maintenance module.</span></span>

<span data-ttu-id="7d05f-145">Parte do princípio de que um módulo do PowerShell válido que contém as funcionalidades de função numa subpasta do 'RoleCapabilities' está localizado no '\\\\myfileshare\\JEA "partilha de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="7d05f-145">It assumes that a valid PowerShell module containing role capabilities in a 'RoleCapabilities' subfolder is located on the '\\\\myfileshare\\JEA' file share.</span></span>


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

<span data-ttu-id="7d05f-146">Esta configuração, em seguida, pode ser aplicada num sistema pelo [invocando diretamente o Gestor de configuração Local](https://msdn.microsoft.com/powershell/dsc/metaconfig) ou a atualizar a [configuração de servidor de solicitação](https://msdn.microsoft.com/powershell/dsc/pullserver).</span><span class="sxs-lookup"><span data-stu-id="7d05f-146">This configuration can then be applied on a system by [directly invoking the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig) or updating the [pull server configuration](https://msdn.microsoft.com/powershell/dsc/pullserver).</span></span>

<span data-ttu-id="7d05f-147">O recurso de DSC também permite que substitua o ponto de extremidade padrão da comunicação remota do Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7d05f-147">The DSC resource also allows you to replace the default Microsoft.PowerShell remoting endpoint.</span></span>
<span data-ttu-id="7d05f-148">Se fizer isso, o recurso registra automaticamente um ponto de extremidade irrestrita cópia de segurança com o nome "Microsoft.PowerShell.Restricted" que tem a ACL de WinRM (permitindo que os utilizadores de gestão remota e os administradores locais membros do grupo para aceder ao mesmo) padrão.</span><span class="sxs-lookup"><span data-stu-id="7d05f-148">If you do this, the resource automatically registers a backup unconstrained endpoint named "Microsoft.PowerShell.Restricted" which has the default WinRM ACL (allowing Remote Management Users and local Administrators group members to access it).</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="7d05f-149">A anular o registo configurações de JEA</span><span class="sxs-lookup"><span data-stu-id="7d05f-149">Unregistering JEA configurations</span></span>

<span data-ttu-id="7d05f-150">Para remover um ponto final JEA num sistema, utilize o [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7d05f-150">To remove a JEA endpoint on a system, use the [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet.</span></span>
<span data-ttu-id="7d05f-151">Anular o registo de um ponto final JEA impede que novos usuários a criação de novas sessões JEA no sistema.</span><span class="sxs-lookup"><span data-stu-id="7d05f-151">Unregistering a JEA endpoint prevents new users from creating new JEA sessions on the system.</span></span>
<span data-ttu-id="7d05f-152">Ele também permite-lhe atualizar uma configuração de JEA registando novamente um arquivo de configuração de sessão atualizadas utilizando o mesmo nome de ponto final.</span><span class="sxs-lookup"><span data-stu-id="7d05f-152">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="7d05f-153">Ponto final de anular o registo de um JEA faz com que o serviço WinRM seja reiniciado.</span><span class="sxs-lookup"><span data-stu-id="7d05f-153">Unregistering a JEA endpoint causes the WinRM service to restart.</span></span>
> <span data-ttu-id="7d05f-154">Isso interrompe remotas mais operações de gestão em curso, incluindo outras sessões do PowerShell, invocações do WMI e algumas ferramentas de gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="7d05f-154">This interrupts most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span>
> <span data-ttu-id="7d05f-155">Anular o registo apenas pontos finais do PowerShell durante as janelas de manutenção planeada.</span><span class="sxs-lookup"><span data-stu-id="7d05f-155">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7d05f-156">Próximos passos</span><span class="sxs-lookup"><span data-stu-id="7d05f-156">Next steps</span></span>

- [<span data-ttu-id="7d05f-157">Testar o ponto final da JEA</span><span class="sxs-lookup"><span data-stu-id="7d05f-157">Test the JEA endpoint</span></span>](using-jea.md)
