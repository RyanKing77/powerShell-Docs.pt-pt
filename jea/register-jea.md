---
ms.date: 06/12/2017
keywords: jea, powershell, segurança
title: Registar JEA configurações
ms.openlocfilehash: cda899b20378b0183a3d88ecfd593aaf7356e967
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188518"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="395c1-103">Registar JEA configurações</span><span class="sxs-lookup"><span data-stu-id="395c1-103">Registering JEA Configurations</span></span>

> <span data-ttu-id="395c1-104">Aplica-se a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="395c1-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="395c1-105">O último passo antes de poder utilizar JEA assim que tiver o [capacidades de função](role-capabilities.md) e [ficheiro de configuração de sessão](session-configurations.md) criado é para registar o ponto final JEA.</span><span class="sxs-lookup"><span data-stu-id="395c1-105">The last step before you can use JEA once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created is to register the JEA endpoint.</span></span>
<span data-ttu-id="395c1-106">Este processo aplica-se as informações de configuração de sessão para o sistema e disponibiliza o ponto final para utilização por utilizadores e de motores de automatização.</span><span class="sxs-lookup"><span data-stu-id="395c1-106">This process applies the session configuration information to the system and makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="395c1-107">Configuração da máquina único</span><span class="sxs-lookup"><span data-stu-id="395c1-107">Single machine configuration</span></span>

<span data-ttu-id="395c1-108">Para ambientes pequenos, pode implementar o JEA registando a configuração de sessão ficheiros com o [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="395c1-108">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="395c1-109">Antes de começar, certifique-se de que os seguintes pré-requisitos foram cumpridos:</span><span class="sxs-lookup"><span data-stu-id="395c1-109">Before you begin, ensure that the following prerequisites have been met:</span></span>
- <span data-ttu-id="395c1-110">Uma ou mais funções foi criado e colocado na pasta 'RoleCapabilities' de um módulo do PowerShell válida.</span><span class="sxs-lookup"><span data-stu-id="395c1-110">One or more roles has been created and placed in the 'RoleCapabilities' folder of a valid PowerShell module.</span></span>
- <span data-ttu-id="395c1-111">Foi criado e testado um ficheiro de configuração de sessão.</span><span class="sxs-lookup"><span data-stu-id="395c1-111">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="395c1-112">O utilizador ao registar a configuração de JEA tem direitos de administrador sobre os sistemas.</span><span class="sxs-lookup"><span data-stu-id="395c1-112">The user registering the JEA configuration has administrator rights on the system(s).</span></span>

<span data-ttu-id="395c1-113">Também terá de selecionar um nome para o ponto final JEA.</span><span class="sxs-lookup"><span data-stu-id="395c1-113">You will also need to select a name for your JEA endpoint.</span></span>
<span data-ttu-id="395c1-114">O nome do ponto final JEA serão necessário quando os utilizadores que pretende estabelecer ligação ao sistema através da JEA.</span><span class="sxs-lookup"><span data-stu-id="395c1-114">The name of the JEA endpoint will be required when users want to connect to the system using JEA.</span></span>
<span data-ttu-id="395c1-115">Pode utilizar o [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet para verificar os nomes dos pontos finais existentes no sistema.</span><span class="sxs-lookup"><span data-stu-id="395c1-115">You can use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet to check the names of existing endpoints on the system.</span></span>
<span data-ttu-id="395c1-116">Pontos finais que começam por 'microsoft', normalmente, são fornecidos com o Windows.</span><span class="sxs-lookup"><span data-stu-id="395c1-116">Endpoints that start with 'microsoft' are typically shipped with Windows.</span></span>
<span data-ttu-id="395c1-117">O ponto final 'Microsoft' é o ponto final predefinido utilizado ao ligar a um ponto final de PowerShell remoto.</span><span class="sxs-lookup"><span data-stu-id="395c1-117">The 'microsoft.powershell' endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

<span data-ttu-id="395c1-118">Quando determinar um nome adequado para o ponto final JEA, execute o seguinte comando para registar o ponto final.</span><span class="sxs-lookup"><span data-stu-id="395c1-118">When you have determined an appropriate name for your JEA endpoint, run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="395c1-119">O comando acima irá reiniciar o serviço WinRM no sistema.</span><span class="sxs-lookup"><span data-stu-id="395c1-119">The above command will restart the WinRM service on the system.</span></span>
> <span data-ttu-id="395c1-120">Isto irá terminar todas as sessões de comunicação remota do PowerShell, bem como quaisquer configurações de DSC em curso.</span><span class="sxs-lookup"><span data-stu-id="395c1-120">This will terminate all PowerShell remoting sessions as well as any ongoing DSC configurations.</span></span>
> <span data-ttu-id="395c1-121">Recomenda-se que colocar as máquinas de produção offline antes de executar o comando para evitar perturbar operações de negócio.</span><span class="sxs-lookup"><span data-stu-id="395c1-121">It is recommended that you take any production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="395c1-122">Se o registo foi efetuado com êxito, está pronto para [utilizar JEA](using-jea.md).</span><span class="sxs-lookup"><span data-stu-id="395c1-122">If registration was successful, you are ready to [use JEA](using-jea.md).</span></span>
<span data-ttu-id="395c1-123">Pode eliminar o ficheiro de configuração de sessão em qualquer altura; Não é utilizado após o registo.</span><span class="sxs-lookup"><span data-stu-id="395c1-123">You may delete the session configuration file at any time; it is not used after registration.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="395c1-124">Configuração de múltiplos computador com o DSC</span><span class="sxs-lookup"><span data-stu-id="395c1-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="395c1-125">Se estiver a implementar o JEA em várias máquinas, o modelo de implementação mais simples consiste em utilizar o JEA [configuração de estado pretendido](https://msdn.microsoft.com/en-us/powershell/dsc/overview) recursos para implementar rápida e consistentemente JEA em cada máquina.</span><span class="sxs-lookup"><span data-stu-id="395c1-125">If you are deploying JEA on multiple machines, the simplest deployment model is to use the JEA [Desired State Configuration](https://msdn.microsoft.com/en-us/powershell/dsc/overview) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="395c1-126">Para implementar JEA com DSC, terá de Certifique-se de que são cumpridos os seguintes pré-requisitos:</span><span class="sxs-lookup"><span data-stu-id="395c1-126">To deploy JEA with DSC, you will need to ensure the following prerequisites are met:</span></span>
- <span data-ttu-id="395c1-127">Um ou mais capacidades de função tenham sido criadas e adicionadas a um módulo do PowerShell válido.</span><span class="sxs-lookup"><span data-stu-id="395c1-127">One or more role capabilities have been authored and added to a valid PowerShell module.</span></span>
- <span data-ttu-id="395c1-128">O módulo do PowerShell que contém as funções é armazenado numa partilha de ficheiros (só de leitura) acessível por cada máquina.</span><span class="sxs-lookup"><span data-stu-id="395c1-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="395c1-129">Definições para a configuração de sessão foram identificadas.</span><span class="sxs-lookup"><span data-stu-id="395c1-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="395c1-130">Não é necessário criar um ficheiro de configuração de sessão ao utilizar o recurso de JEA DSC.</span><span class="sxs-lookup"><span data-stu-id="395c1-130">You do not need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="395c1-131">Tem de ter credenciais que permitem-lhe efetuar ações administrativas em cada máquina ou ter acesso a um servidor de solicitação do DSC utilizado para gerir as máquinas.</span><span class="sxs-lookup"><span data-stu-id="395c1-131">You have credentials that will allow you to perform administrative actions on each machine, or have access to a DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="395c1-132">Transferiu o [recursos de JEA DSC](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span><span class="sxs-lookup"><span data-stu-id="395c1-132">You have downloaded the [JEA DSC resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span></span>

<span data-ttu-id="395c1-133">Num destino máquina (ou servidor de solicitação, se estiver a utilizar um), crie uma configuração de DSC para o ponto final JEA.</span><span class="sxs-lookup"><span data-stu-id="395c1-133">On a target machine (or pull server, if you are using one), create a DSC configuration for your JEA endpoint.</span></span>
<span data-ttu-id="395c1-134">Nesta configuração, irá utilizar os recursos de JustEnoughAdministration DSC para configurar o ficheiro de configuração de sessão e o recurso de ficheiros a copiar sobre as capacidades de função da partilha de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="395c1-134">In this configuration, you will use the JustEnoughAdministration DSC resource to set up the session configuration file and the File resource to copy over the role capabilities from the file share.</span></span>

<span data-ttu-id="395c1-135">As seguintes propriedades são configuráveis com os recursos de DSC:</span><span class="sxs-lookup"><span data-stu-id="395c1-135">The following properties are configurable using the DSC resource:</span></span>
- <span data-ttu-id="395c1-136">Definições de função</span><span class="sxs-lookup"><span data-stu-id="395c1-136">Role Definitions</span></span>
- <span data-ttu-id="395c1-137">Grupos de conta virtuais</span><span class="sxs-lookup"><span data-stu-id="395c1-137">Virtual Account groups</span></span>
- <span data-ttu-id="395c1-138">Nome de conta de serviço gerida de grupo</span><span class="sxs-lookup"><span data-stu-id="395c1-138">Group Managed Service Account name</span></span>
- <span data-ttu-id="395c1-139">Diretório de transcript</span><span class="sxs-lookup"><span data-stu-id="395c1-139">Transcript directory</span></span>
- <span data-ttu-id="395c1-140">Unidade de utilizador</span><span class="sxs-lookup"><span data-stu-id="395c1-140">User drive</span></span>
- <span data-ttu-id="395c1-141">Regras de acesso condicional</span><span class="sxs-lookup"><span data-stu-id="395c1-141">Conditional access rules</span></span>
- <span data-ttu-id="395c1-142">Scripts de arranque para a sessão JEA</span><span class="sxs-lookup"><span data-stu-id="395c1-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="395c1-143">A sintaxe para cada uma destas propriedades numa configuração de DSC é consistente com o ficheiro de configuração de sessão do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="395c1-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="395c1-144">Segue-se uma configuração de DSC de exemplo para um módulo de manutenção gerais do servidor.</span><span class="sxs-lookup"><span data-stu-id="395c1-144">Below is a sample DSC configuration for a general server maintenance module.</span></span>

<span data-ttu-id="395c1-145">Parte do pressuposto de que um módulo do PowerShell válido que contém as capacidades de função numa subpasta 'RoleCapabilities' se encontra localizado no '\\\\myfileshare\\JEA' Partilha de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="395c1-145">It assumes that a valid PowerShell module containing role capabilities in a 'RoleCapabilities' subfolder is located on the '\\\\myfileshare\\JEA' file share.</span></span>


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

<span data-ttu-id="395c1-146">Esta configuração, em seguida, pode ser aplicada num sistema por [diretamente invocar o Gestor de configuração Local](https://msdn.microsoft.com/en-us/powershell/dsc/metaconfig) ou atualizar o [configuração do servidor de solicitação](https://msdn.microsoft.com/en-us/powershell/dsc/pullserver).</span><span class="sxs-lookup"><span data-stu-id="395c1-146">This configuration can then be applied on a system by [directly invoking the Local Configuration Manager](https://msdn.microsoft.com/en-us/powershell/dsc/metaconfig) or updating the [pull server configuration](https://msdn.microsoft.com/en-us/powershell/dsc/pullserver).</span></span>

<span data-ttu-id="395c1-147">O recurso de DSC também permite-lhe substituir o ponto de final predefinido da gestão remota do Microsoft.</span><span class="sxs-lookup"><span data-stu-id="395c1-147">The DSC resource also allows you to replace the default Microsoft.PowerShell remoting endpoint.</span></span>
<span data-ttu-id="395c1-148">Se o fizer, o recurso será registado automaticamente um ponto final de cópia de segurança unconstrainted com o nome "Microsoft.PowerShell.Restricted" que tem a predefinição de ACL de WinRM (permitir que utilizadores de gestão remota e os administradores locais membros do grupo para aceder ao mesmo).</span><span class="sxs-lookup"><span data-stu-id="395c1-148">If you do this, the resource will automatically register a backup unconstrainted endpoint named "Microsoft.PowerShell.Restricted" which has the default WinRM ACL (allowing Remote Management Users and local Administrators group members to access it).</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="395c1-149">A anular registo configurações de JEA</span><span class="sxs-lookup"><span data-stu-id="395c1-149">Unregistering JEA configurations</span></span>

<span data-ttu-id="395c1-150">Para remover um ponto final de JEA num sistema, utilize o [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="395c1-150">To remove a JEA endpoint on a system, use the [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet.</span></span>
<span data-ttu-id="395c1-151">A anulação do registo um ponto final JEA irá impedir que os novos utilizadores da criação de novas sessões JEA no sistema.</span><span class="sxs-lookup"><span data-stu-id="395c1-151">Unregistering a JEA endpoint will prevent new users from creating new JEA sessions on the system.</span></span>
<span data-ttu-id="395c1-152">Também permite-lhe atualizar uma configuração de JEA registando novamente um ficheiro de configuração de sessão atualizadas com o mesmo nome de ponto final.</span><span class="sxs-lookup"><span data-stu-id="395c1-152">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="395c1-153">A anulação do registo um JEA endpoint fará com que o serviço WinRM para reiniciar.</span><span class="sxs-lookup"><span data-stu-id="395c1-153">Unregistering a JEA endpoint will cause the WinRM service to restart.</span></span>
> <span data-ttu-id="395c1-154">Isto irá interromper a operações de gestão mais remotas em curso, incluindo outras sessões de PowerShell, invocações de WMI e algumas ferramentas de gestão.</span><span class="sxs-lookup"><span data-stu-id="395c1-154">This will interrupt most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span>
> <span data-ttu-id="395c1-155">Anular o registo apenas pontos finais de PowerShell durante as janelas de manutenção planeada.</span><span class="sxs-lookup"><span data-stu-id="395c1-155">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="395c1-156">Próximos passos</span><span class="sxs-lookup"><span data-stu-id="395c1-156">Next steps</span></span>

- [<span data-ttu-id="395c1-157">O ponto final JEA de teste</span><span class="sxs-lookup"><span data-stu-id="395c1-157">Test the JEA endpoint</span></span>](using-jea.md)