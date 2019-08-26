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
# <a name="registering-jea-configurations"></a>Registrando configurações do JEA

Depois que você tiver os [recursos de função](role-capabilities.md) e o arquivo de configuração de [sessão](session-configurations.md) criados, a última etapa será registrar o ponto de extremidade Jea. Registrar o ponto de extremidade JEA com o sistema torna o ponto de extremidade disponível para uso por usuários e mecanismos de automação.

## <a name="single-machine-configuration"></a>Configuração de computador único

Para ambientes pequenos, você pode implantar o JEA registrando o arquivo de configuração de sessão usando o cmdlet [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) .

Antes de começar, verifique se os seguintes pré-requisitos foram atendidos:

- Uma ou mais funções foram criadas e colocadas na pasta **RoleCapabilities** de um módulo do PowerShell.
- Um arquivo de configuração de sessão foi criado e testado.
- O usuário que está registrando a configuração JEA tem direitos de administrador no sistema.
- Você selecionou um nome para o ponto de extremidade JEA.

O nome do ponto de extremidade JEA é necessário quando os usuários se conectam ao sistema usando o JEA. O cmdlet [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) lista os nomes dos pontos de extremidade em um sistema. Os pontos de extremidade que começam `microsoft` com o normalmente são fornecidos com o Windows. O `microsoft.powershell` ponto de extremidade é o ponto de extremidade padrão usado ao se conectar a um ponto de extremidade do PowerShell remoto.

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

Execute o comando a seguir para registrar o ponto de extremidade.

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> O comando anterior reinicia o serviço WinRM no sistema. Isso encerra todas as sessões de comunicação remota do PowerShell e todas as configurações de DSC em andamento. Recomendamos que você coloque as máquinas de produção offline antes de executar o comando para evitar a interrupção das operações de negócios.

Após o registro, você estará pronto para [usar o Jea](using-jea.md). Você pode excluir o arquivo de configuração de sessão a qualquer momento. O arquivo de configuração não é usado após o registro do ponto de extremidade.

## <a name="multi-machine-configuration-with-dsc"></a>Configuração de vários computadores com DSC

Ao implantar o JEA em vários computadores, o modelo de implantação mais simples usa o recurso de [configuração de estado desejado (DSC)](/powershell/dsc/overview) do Jea para implantar de forma rápida e consistente o Jea em cada computador.

Para implantar o JEA com o DSC, verifique se os seguintes pré-requisitos foram atendidos:

- Um ou mais recursos de função foram criados e adicionados a um módulo do PowerShell.
- O módulo do PowerShell que contém as funções é armazenado em um compartilhamento de arquivos (somente leitura) acessível por cada computador.
- As configurações para a configuração de sessão foram determinadas. Você não precisa criar um arquivo de configuração de sessão ao usar o recurso DSC JEA.
- Você tem credenciais que permitem ações administrativas em cada computador ou acesso ao servidor de pull de DSC usado para gerenciar os computadores.
- Você baixou o [recurso DSC Jea](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource).

Crie uma configuração DSC para o ponto de extremidade do JEA em um computador de destino ou servidor de pull. Nessa configuração, o recurso DSC **JustEnoughAdministration** define o arquivo de configuração de sessão e o recurso de **arquivo** copia os recursos de função do compartilhamento de arquivos.

As propriedades a seguir são configuráveis usando o recurso de DSC:

- Definições de função
- Grupos de contas virtuais
- Grupo-nome da conta de serviço gerenciado
- Diretório de transcrição
- Unidade do usuário
- Regras de acesso condicional
- Scripts de inicialização para a sessão JEA

A sintaxe para cada uma dessas propriedades em uma configuração DSC é consistente com o arquivo de configuração de sessão do PowerShell.

Veja abaixo uma configuração de DSC de exemplo para um módulo de manutenção geral do servidor. Ele assume que um módulo válido do PowerShell contendo recursos de função está localizado `\\myfileshare\JEA` no compartilhamento de arquivos.

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

Em seguida, a configuração é aplicada em um sistema invocando diretamente o [Configuration Manager local](/powershell/dsc/managing-nodes/metaConfig) ou atualizando a [configuração do servidor de pull](/powershell/dsc/pull-server/pullServer).

O recurso DSC também permite que você substitua o ponto de extremidade do **Microsoft. PowerShell** padrão. Quando substituído, o recurso registra automaticamente um ponto de extremidade de backup chamado **Microsoft. PowerShell. Restricted**. O ponto de extremidade de backup tem a ACL padrão do WinRM que permite que usuários de gerenciamento remoto e membros do grupo de administradores locais o acessem.

## <a name="unregistering-jea-configurations"></a>Cancelando o registro de configurações do JEA

O cmdlet [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) remove um ponto de extremidade Jea. Cancelar o registro de um ponto de extremidade JEA impede que novos usuários criem novas sessões do JEA no sistema. Ele também permite que você atualize uma configuração do JEA registrando novamente um arquivo de configuração de sessão atualizado usando o mesmo nome de ponto de extremidade.

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> Cancelar o registro de um ponto de extremidade JEA faz com que o serviço WinRM seja reiniciado. Isso interrompe a maioria das operações de gerenciamento remoto em andamento, incluindo outras sessões do PowerShell, invocações de WMI e algumas ferramentas de gerenciamento. Cancele o registro somente dos pontos de extremidade do PowerShell durante as janelas de manutenção planejadas.

## <a name="next-steps"></a>Passos Seguintes

[Testar o ponto de extremidade JEA](using-jea.md)
