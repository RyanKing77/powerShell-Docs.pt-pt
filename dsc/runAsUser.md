---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Executar o DSC com as credenciais do utilizador
ms.openlocfilehash: 37e6ff64c9c6d3960653d417e22a6c93c653230c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="running-dsc-with-user-credentials"></a><span data-ttu-id="fae84-103">Executar o DSC com as credenciais do utilizador</span><span class="sxs-lookup"><span data-stu-id="fae84-103">Running DSC with user credentials</span></span>

> <span data-ttu-id="fae84-104">Aplica-se a: O Windows PowerShell 5.0, 5.1 do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fae84-104">Applies To: Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="fae84-105">Pode executar um recurso de DSC sob um conjunto especificado de credenciais utilizando o automático **PsDscRunAsCredential** propriedade na configuração.</span><span class="sxs-lookup"><span data-stu-id="fae84-105">You can run a DSC resource under a specified set of credentials by using the automatic **PsDscRunAsCredential** property in the configuration.</span></span>
<span data-ttu-id="fae84-106">Por predefinição, o DSC executa cada recurso como conta do sistema.</span><span class="sxs-lookup"><span data-stu-id="fae84-106">By default, DSC runs each resource as the system account.</span></span>
<span data-ttu-id="fae84-107">Existem vezes quando em execução como um utilizador é necessário, tais como instalar pacotes MSI num contexto de utilizador específico, definir as chaves de registo de um utilizador, ao aceder ao diretório local específica de um utilizador ou aceder a uma rede de partilha.</span><span class="sxs-lookup"><span data-stu-id="fae84-107">There are times when running as a user is necessary, such as installing MSI packages in a specific user context, setting a user's registry keys, accessing a user's specific local directory, or accessing a network share.</span></span>

<span data-ttu-id="fae84-108">Todos os recursos de DSC tem um **PsDscRunAsCredential** propriedade que pode ser definida como as credenciais de utilizador (um [PSCredential](https://msdn.microsoft.com/library/ms572524(v=VS.85).aspx) objeto).</span><span class="sxs-lookup"><span data-stu-id="fae84-108">Every DSC resource has a **PsDscRunAsCredential** property that can be set to any user credentials (a [PSCredential](https://msdn.microsoft.com/library/ms572524(v=VS.85).aspx) object).</span></span>
<span data-ttu-id="fae84-109">A credencial pode ser codificados como o valor da propriedade na configuração ou pode definir o valor [Get-Credential](https://technet.microsoft.com/library/hh849815.aspx), que pedirá ao utilizador para uma credencial quando a configuração é compilada (para obter informações sobre Compilar configurações, consulte [configurações](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="fae84-109">The credential can be hard-coded as the value of the property in the configuration, or you can set the value to [Get-Credential](https://technet.microsoft.com/library/hh849815.aspx), which will prompt the user for a credential when the configuration is compiled (for information about compiling configurations, see [Configurations](configurations.md).</span></span>

><span data-ttu-id="fae84-110">**Nota:** no PowerShell 5.0, utilizando o **PsDscRunAsCredential** propriedade em configurações de chamar recursos compostos não era suportada.</span><span class="sxs-lookup"><span data-stu-id="fae84-110">**Note:** In PowerShell 5.0, using the **PsDscRunAsCredential** property in configurations calling composite resources was not supported.</span></span>
><span data-ttu-id="fae84-111">No PowerShell 5.1, o **PsDscRunAsCredential** propriedade é suportada em configurações de chamar recursos compostos.</span><span class="sxs-lookup"><span data-stu-id="fae84-111">In PowerShell 5.1, the **PsDscRunAsCredential** property is supported in configurations calling composite resources.</span></span>

><span data-ttu-id="fae84-112">**Nota:** o **PsDscRunAsCredential** propriedade não está disponível no PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="fae84-112">**Note:** The **PsDscRunAsCredential** property is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="fae84-113">No exemplo seguinte, **Get-Credential** é utilizado para pedir ao utilizador as credenciais.</span><span class="sxs-lookup"><span data-stu-id="fae84-113">In the following example, **Get-Credential** is used to prompt the user for credentials.</span></span>
<span data-ttu-id="fae84-114">O [registo](registryResource.md) recurso é utilizado para alterar a chave de registo que especifica a cor de fundo para a janela de linha de comandos do Windows.</span><span class="sxs-lookup"><span data-stu-id="fae84-114">The [Registry](registryResource.md) resource is used to change the registry key that specifies the background color for the Windows command prompt window.</span></span>

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
><span data-ttu-id="fae84-115">**Nota:** este exemplo assume que tem um certificado válido em `C:\publicKeys\targetNode.cer`, e que o thumbprint do certificado é o valor mostrado.</span><span class="sxs-lookup"><span data-stu-id="fae84-115">**Note:** This example assumes that you have a valid certificate at `C:\publicKeys\targetNode.cer`, and that the thumbprint of that certificate is the value shown.</span></span>
><span data-ttu-id="fae84-116">Para obter informações sobre a encriptação de credenciais nos ficheiros de MOF de configuração de DSC, consulte [proteger o ficheiro MOF](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="fae84-116">For information about encrypting credentials in DSC configuration MOF files, see [Securing the MOF file](secureMOF.md).</span></span>