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
# <a name="reboot-a-node"></a>Reboot a Node (Reiniciar um Nó)

> [!NOTE]
> Este tópico discute como um nó de reinício. Para que a reinicialização seja concluída com êxito a **ActionAfterReboot** e **RebootNodeIfNeeded** definições do LCM precisam ser configurados corretamente.
> Para ler mais sobre as definições do Gestor de configuração Local, veja [configurar o Gestor de configuração Local](../managing-nodes/metaConfig.md), ou [configurar o Gestor de configuração Local (v4)](../managing-nodes/metaConfig4.md).

Nós podem ser reiniciados de dentro de um recurso, utilizando o `$global:DSCMachineStatus` sinalizador. Definir este sinalizador `1` no `Set-TargetResource` função força o LCM para reiniciar o nó diretamente após o **definir** método do recurso atual. Usando este sinalizador, o **xPendingReboot** recursos Deteta se está pendente um reinício fora de DSC.

Sua [configurações](configurations.md) pode efetuar os passos que exigem o nó reiniciar o computador. Isso pode incluir coisas como:

- Atualizações do Windows
- Instalação de software
- Muda o nome de ficheiro
- A mudança de nome de computador

O **xPendingReboot** recursos verifica localizações específicas de computador para determinar se está pendente um reinício. Se o nó requer um reinício fora de DSC, o **xPendingReboot** conjuntos de recursos a `$global:DSCMachineStatus` sinalizador para `1` forçar um reinício e como resolver a condição pendente.

> [!NOTE]
> Qualquer recurso de DSC pode instruir o LCM para reiniciar o nó ao definir este sinalizador `Set-TargetResource` função. Para obter mais informações, consulte [escrever um recurso personalizado do DSC com o MOF](../resources/authoringResourceMOF.md).

## <a name="syntax"></a>Sintaxe

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

## <a name="properties"></a>Propriedades

| Propriedade | Descrição |
| --- | --- |
| Nome| Parâmetro necessário, tem de ser exclusivo por instância do recurso dentro de uma configuração.|
| SkipComponentBasedServicing | Reinícios de ignorar acionados pelo componente de serviço baseado no componente. |
| SkipWindowsUpdate | Reinícios de ignorar acionados pelo Windows Update.|
| SkipPendingFileRename | Ignore reinicializações de mudança de nome de ficheiro pendente. |
| SkipCcmClientSDK | Reinícios de ignorar acionados pelo cliente do ConfigMgr. |
| SkipComputerRename | Muda o nome de reinicializações de ignorar acionadas pelo computador. |
| PSDSCRunAsCredential | Suportado no v5. Executa o recurso como o utilizador especificado. |
| DependsOn | Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será **ResourceName** e seu tipo é **ResourceType**, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`. Para obter mais informações, consulte [usando DependsOn](resource-depends-on.md)|

## <a name="example"></a>Exemplo

O exemplo seguinte instala o Microsoft Exchange utilizando o [xExchange](https://github.com/PowerShell/xExchange) recursos.
Durante a instalação, o **xPendingReboot** recurso é utilizado para reiniciar o nó.

> [!NOTE]
> Este exemplo requer a credencial de uma conta que tenha direitos para adicionar um servidor Exchange para a floresta. Para obter mais informações sobre como utilizar as credenciais no DSC, consulte [credenciais de manipulação de mensagens em fila no DSC](../configurations/configDataCredentials.md)

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
> Este exemplo assume que configurou o seu Gestor de configuração de Local para permitir reinícios e continuar a configuração após um reinício.

## <a name="where-to-download"></a>Onde pode transferir

Pode transferir os recursos utilizados neste tópico nas seguintes localizações ou através da galeria do PowerShell.

- [xPendingReboot](https://github.com/PowerShell/xPendingReboot)
- [xExchange](https://github.com/PowerShell/xExchange)
