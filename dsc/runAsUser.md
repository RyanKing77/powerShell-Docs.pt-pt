---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Executar o DSC com as credenciais do utilizador
ms.openlocfilehash: 4a6c3d8b561cd0a27be07a68f1b577f7bf764254
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893914"
---
# <a name="running-dsc-with-user-credentials"></a><span data-ttu-id="4fa22-103">Executar o DSC com as credenciais do utilizador</span><span class="sxs-lookup"><span data-stu-id="4fa22-103">Running DSC with user credentials</span></span>

> <span data-ttu-id="4fa22-104">Aplica-se a: O Windows PowerShell 5.0, 5.1 do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4fa22-104">Applies To: Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="4fa22-105">Pode executar um recurso de DSC num conjunto especificado de credenciais utilizando o automatic **PsDscRunAsCredential** propriedade na configuração.</span><span class="sxs-lookup"><span data-stu-id="4fa22-105">You can run a DSC resource under a specified set of credentials by using the automatic **PsDscRunAsCredential** property in the configuration.</span></span>
<span data-ttu-id="4fa22-106">Por predefinição, o DSC executa cada recurso que a conta de sistema.</span><span class="sxs-lookup"><span data-stu-id="4fa22-106">By default, DSC runs each resource as the system account.</span></span>
<span data-ttu-id="4fa22-107">Há momentos quando em execução como um utilizador é necessário, por exemplo, instalar pacotes MSI num contexto de utilizador específico, definir chaves de registo de um utilizador, aceder ao diretório local específico de um utilizador ou aceder a uma rede de partilhar.</span><span class="sxs-lookup"><span data-stu-id="4fa22-107">There are times when running as a user is necessary, such as installing MSI packages in a specific user context, setting a user's registry keys, accessing a user's specific local directory, or accessing a network share.</span></span>

<span data-ttu-id="4fa22-108">Cada recurso de DSC tem um **PsDscRunAsCredential** propriedade que pode ser definida para quaisquer credenciais de utilizador (um [PSCredential](/dotnet/api/system.management.automation.pscredential) objeto).</span><span class="sxs-lookup"><span data-stu-id="4fa22-108">Every DSC resource has a **PsDscRunAsCredential** property that can be set to any user credentials (a [PSCredential](/dotnet/api/system.management.automation.pscredential) object).</span></span>
<span data-ttu-id="4fa22-109">A credencial pode ser codificada como o valor da propriedade na configuração ou pode definir o valor [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), que pedirá ao utilizador para uma credencial quando a configuração é compilada (para obter informações sobre Compilar configurações, consulte [configurações](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="4fa22-109">The credential can be hard-coded as the value of the property in the configuration, or you can set the value to [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), which will prompt the user for a credential when the configuration is compiled (for information about compiling configurations, see [Configurations](configurations.md).</span></span>

> [!NOTE] 
> <span data-ttu-id="4fa22-110">No PowerShell 5.0, utilizando o **PsDscRunAsCredential** propriedade em configurações de chamar recursos compostos não era suportada.</span><span class="sxs-lookup"><span data-stu-id="4fa22-110">In PowerShell 5.0, using the **PsDscRunAsCredential** property in configurations calling composite resources was not supported.</span></span>
> <span data-ttu-id="4fa22-111">No PowerShell 5.1, o **PsDscRunAsCredential** propriedade é suportada em configurações de chamar recursos compostos.</span><span class="sxs-lookup"><span data-stu-id="4fa22-111">In PowerShell 5.1, the **PsDscRunAsCredential** property is supported in configurations calling composite resources.</span></span>
> <span data-ttu-id="4fa22-112">O **PsDscRunAsCredential** propriedade não está disponível no PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="4fa22-112">The **PsDscRunAsCredential** property is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="4fa22-113">No exemplo a seguir, `Get-Credential` é usado para avisar o utilizador as credenciais.</span><span class="sxs-lookup"><span data-stu-id="4fa22-113">In the following example, `Get-Credential` is used to prompt the user for credentials.</span></span>
<span data-ttu-id="4fa22-114">O [Registro](registryResource.md) recurso é utilizado para alterar a chave de registo que especifica a cor de fundo da janela de linha de comandos do Windows.</span><span class="sxs-lookup"><span data-stu-id="4fa22-114">The [Registry](registryResource.md) resource is used to change the registry key that specifies the background color for the Windows command prompt window.</span></span>

```powershell
Configuration ChangeCmdBackGroundColor
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        Registry CmdPath
        {
            Key                  = 'HKEY_CURRENT_USER\SOFTWARE\Microsoft\Command Processor'
            ValueName            = 'DefaultColor'
            ValueData            = '1F'
            ValueType            = 'DWORD'
            Ensure               = 'Present'
            Force                = $true
            Hex                  = $true
            PsDscRunAsCredential = Get-Credential
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost';
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}

ChangeCmdBackGroundColor -ConfigurationData $configData
```

> [!NOTE]
> <span data-ttu-id="4fa22-115">Este exemplo assume que tem um certificado válido em `C:\publicKeys\targetNode.cer`, e que o thumbprint do certificado é o valor mostrado.</span><span class="sxs-lookup"><span data-stu-id="4fa22-115">This example assumes that you have a valid certificate at `C:\publicKeys\targetNode.cer`, and that the thumbprint of that certificate is the value shown.</span></span>
> <span data-ttu-id="4fa22-116">Para obter informações sobre a encriptação de credenciais nos arquivos de MOF de configuração de DSC, veja [proteger o ficheiro MOF](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="4fa22-116">For information about encrypting credentials in DSC configuration MOF files, see [Securing the MOF file](secureMOF.md).</span></span>
