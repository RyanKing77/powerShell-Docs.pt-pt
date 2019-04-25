---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Utilizar Credenciais com Recursos do DSC
ms.openlocfilehash: af54c286ce744cd7db0b0e2d05087f60cdf1a33c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080055"
---
# <a name="use-credentials-with-dsc-resources"></a>Utilizar Credenciais com Recursos do DSC

> Aplica-se a: Windows PowerShell 5.0, Windows PowerShell 5.1

Pode executar um recurso de DSC num conjunto especificado de credenciais utilizando o automatic **PsDscRunAsCredential** propriedade na configuração.
Por predefinição, o DSC executa cada recurso que a conta de sistema.
Há momentos quando em execução como um utilizador é necessário, por exemplo, instalar pacotes MSI num contexto de utilizador específico, definir chaves de registo de um utilizador, aceder ao diretório local específico de um utilizador ou aceder a uma rede de partilhar.

Cada recurso de DSC tem um **PsDscRunAsCredential** propriedade que pode ser definida para quaisquer credenciais de utilizador (um [PSCredential](/dotnet/api/system.management.automation.pscredential) objeto).
A credencial pode ser codificada como o valor da propriedade na configuração ou pode definir o valor [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), que pedirá ao utilizador para uma credencial quando a configuração é compilada (para obter informações sobre Compilar configurações, consulte [configurações](configurations.md).

> [!NOTE]
> No PowerShell 5.0, utilizando o **PsDscRunAsCredential** propriedade em configurações de chamar recursos compostos não era suportada.
> No PowerShell 5.1, o **PsDscRunAsCredential** propriedade é suportada em configurações de chamar recursos compostos.
> O **PsDscRunAsCredential** propriedade não está disponível no PowerShell 4.0.

No exemplo a seguir, `Get-Credential` é usado para avisar o utilizador as credenciais.
O **Registro** recurso é utilizado para alterar a chave de registo que especifica a cor de fundo da janela de linha de comandos do Windows.

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
> Este exemplo assume que tem um certificado válido em `C:\publicKeys\targetNode.cer`, e que o thumbprint do certificado é o valor mostrado.
> Para obter informações sobre a encriptação de credenciais nos arquivos de MOF de configuração de DSC, veja [proteger o ficheiro MOF](../pull-server/secureMOF.md).
