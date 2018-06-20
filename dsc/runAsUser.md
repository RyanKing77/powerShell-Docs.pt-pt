---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Executar o DSC com as credenciais do utilizador
ms.openlocfilehash: b2992ad562dea375aba980611312c7b96a23189c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189708"
---
# <a name="running-dsc-with-user-credentials"></a>Executar o DSC com as credenciais do utilizador

> Aplica-se a: O Windows PowerShell 5.0, 5.1 do Windows PowerShell

Pode executar um recurso de DSC sob um conjunto especificado de credenciais utilizando o automático **PsDscRunAsCredential** propriedade na configuração.
Por predefinição, o DSC executa cada recurso como conta do sistema.
Existem vezes quando em execução como um utilizador é necessário, tais como instalar pacotes MSI num contexto de utilizador específico, definir as chaves de registo de um utilizador, ao aceder ao diretório local específica de um utilizador ou aceder a uma rede de partilha.

Todos os recursos de DSC tem um **PsDscRunAsCredential** propriedade que pode ser definida como as credenciais de utilizador (um [PSCredential](https://msdn.microsoft.com/library/ms572524(v=VS.85).aspx) objeto).
A credencial pode ser codificados como o valor da propriedade na configuração ou pode definir o valor [Get-Credential](https://technet.microsoft.com/library/hh849815.aspx), que pedirá ao utilizador para uma credencial quando a configuração é compilada (para obter informações sobre Compilar configurações, consulte [configurações](configurations.md).

>**Nota:** no PowerShell 5.0, utilizando o **PsDscRunAsCredential** propriedade em configurações de chamar recursos compostos não era suportada.
>No PowerShell 5.1, o **PsDscRunAsCredential** propriedade é suportada em configurações de chamar recursos compostos.

>**Nota:** o **PsDscRunAsCredential** propriedade não está disponível no PowerShell 4.0.

No exemplo seguinte, **Get-Credential** é utilizado para pedir ao utilizador as credenciais.
O [registo](registryResource.md) recurso é utilizado para alterar a chave de registo que especifica a cor de fundo para a janela de linha de comandos do Windows.

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
>**Nota:** este exemplo assume que tem um certificado válido em `C:\publicKeys\targetNode.cer`, e que o thumbprint do certificado é o valor mostrado.
>Para obter informações sobre a encriptação de credenciais nos ficheiros de MOF de configuração de DSC, consulte [proteger o ficheiro MOF](secureMOF.md).