---
ms.date: 08/15/2019
keywords: DSC, PowerShell, configuração, instalação
title: Introdução à configuração de estado desejado (DSC) para Windows
ms.openlocfilehash: a4f9db481afda65fc4ac5e553230dbba3037ac9a
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988929"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-windows"></a>Introdução à configuração de estado desejado (DSC) para Windows

Este tópico explica como começar a usar a DSC (configuração de estado desejado) do PowerShell para Windows.
Para obter informações gerais sobre a DSC, consulte Introdução [à configuração de estado desejado do Windows PowerShell](../overview/overview.md).

## <a name="supported-windows-operation-system-versions"></a>Versões do sistema operacional Windows com suporte

Há suporte para as seguintes versões:

- Windows Server de 2019
- Windows Server 2016
- Windows Server 2012R2
- Windows Server 2012
- Windows Server 2008 R2 SP1
- Windows 10
- Windows 8.1
- Windows 7

O SKU do produto autônomo do [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) não contém uma implementação do estado desejado configuração, portanto, ele não pode ser gerenciado pela configuração do estado da automação do PowerShell ou da DSC do Azure.

## <a name="installing-dsc"></a>Instalando DSC

A configuração de estado desejado do PowerShell está incluída no Windows e atualizada por meio do Windows Management Framework.
A versão mais recente é o [Windows Management Framework 5,1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).

> [!NOTE]
> Você não precisa habilitar o recurso ' DSC-Service ' do Windows Server para gerenciar um computador usando o DSC.
> Esse recurso só é necessário ao criar uma instância de servidor de pull do Windows.

## <a name="using-dsc-for-windows"></a>Usando o DSC para Windows

As seções a seguir explicam como criar e executar configurações de DSC em computadores Windows.

### <a name="creating-a-configuration-mof-document"></a>Criando um documento MOF de configuração

A palavra-chave de configuração do Windows PowerShell é usada para criar uma configuração.
As etapas a seguir descrevem a criação de um documento de configuração usando o Windows PowerShell.

#### <a name="define-a-configuration-and-generate-the-configuration-document"></a>Defina uma configuração e gere o documento de configuração:

```powershell
Configuration EnvironmentVariable_Path
{
    param ()

    Import-DscResource -ModuleName 'PSDscResources'

    Node localhost
    {
        Environment CreatePathEnvironmentVariable
        {
            Name = 'TestPathEnvironmentVariable'
            Value = 'TestValue'
            Ensure = 'Present'
            Path = $true
            Target = @('Process', 'Machine')
        }
    }
}

EnvironmentVariable_Path -OutputPath:"C:\EnvironmentVariable_Path"
```
#### <a name="install-a-module-containing-dsc-resources"></a>Instalar um módulo que contém recursos de DSC

A configuração de estado desejado do Windows PowerShell inclui módulos internos que contêm recursos de DSC.
Você também pode carregar módulos de fontes externas, como o Galeria do PowerShell, usando os cmdlets do PowerShellGet.

`Install-Module 'PSDscResources' -Verbose`

#### <a name="apply-the-configuration-to-the-machine"></a>Aplicar a configuração ao computador

Os documentos de configuração (Arquivos MOF) podem ser aplicados ao computador usando o cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .

`Start-DscConfiguration -Path 'C:\EnvironmentVariable_Path' -Wait -Verbose`

#### <a name="get-the-current-state-of-the-configuration"></a>Obter o estado atual da configuração

O cmdlet [Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) consulta o status atual do computador e retorna os valores atuais para a configuração.

`Get-DscConfiguration`

O cmdlet [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) retorna a meta-configuração atual aplicada ao computador.

`Get-DscLocalConfigurationManager`

#### <a name="remove-the-current-configuration-from-a-machine"></a>Remover a configuração atual de um computador

O [Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)

`Remove-DscConfigurationDocument -Stage Current -Verbose`

#### <a name="configure-settings-in-local-configuration-manager"></a>Definir configurações no Configuration Manager local

Aplique um arquivo MOF de metaconfiguração ao computador usando o cmdlet [set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) .
Requer o caminho para o MOF de metaconfiguração.

`Set-DSCLocalConfigurationManager -Path 'c:\metaconfig\localhost.meta.mof' -Verbose`

## <a name="windows-powershell-desired-state-configuration-log-files"></a>Arquivos de log de configuração de estado desejado do Windows PowerShell

Os logs para DSC são gravados no log de eventos do `Microsoft-Windows-Dsc/Operational`Windows no caminho.
Logs adicionais para fins de depuração podem ser habilitados seguindo as etapas em [onde estão os logs de eventos de DSC](/powershell/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs).
