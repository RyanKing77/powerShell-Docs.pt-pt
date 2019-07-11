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
# <a name="registering-jea-configurations"></a>Registar a JEA configurações

Depois de ter sua [funcionalidades de função](role-capabilities.md) e [o ficheiro de configuração de sessão](session-configurations.md) criado, a última etapa é registar o ponto final JEA. Registar o ponto final da JEA com o sistema faz com que o ponto final disponíveis para utilização por utilizadores e os mecanismos de automatização.

## <a name="single-machine-configuration"></a>Configuração de máquina única

Em ambientes pequenos, pode implementar a JEA registrando-se a configuração de sessão ficheiro com o [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.

Antes de começar, certifique-se de que os seguintes pré-requisitos foram cumpridos:

- Foi criado e colocado numa ou mais funções do **RoleCapabilities** pasta de um módulo do PowerShell.
- Um ficheiro de configuração de sessão tem de ser criado e testado.
- O utilizador a que se registe a configuração de JEA tem direitos de administrador no sistema.
- Selecionar um nome para o ponto de final JEA.

É necessário o nome do ponto final JEA quando os utilizadores ligam ao sistema de utilizar a JEA. O [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet apresenta uma lista os nomes dos pontos de extremidade num sistema. Pontos finais que iniciam com `microsoft` normalmente são fornecidos com o Windows. O `microsoft.powershell` ponto final é o ponto final predefinido utilizado ao ligar a um ponto de extremidade remoto do PowerShell.

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

Execute o seguinte comando para registar o ponto final.

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> O comando anterior reinicia o serviço de WinRM no sistema. Isso encerra a todas as sessões de comunicação remota do PowerShell e quaisquer configurações de DSC em curso. Recomendamos que colocar máquinas de produção offline antes de executar o comando para evitar interromper as operações de negócio.

Após o registo, está pronto para [utilizar a JEA](using-jea.md). Pode eliminar o ficheiro de configuração de sessão em qualquer altura. O ficheiro de configuração não é usado após o registo do ponto de extremidade.

## <a name="multi-machine-configuration-with-dsc"></a>Configuração de várias máquinas com DSC

Ao implementar a JEA em várias máquinas, o modelo de implementação mais simples, usa o JEA [Desired State Configuration (DSC)](/powershell/dsc/overview) recursos para implementar rápida e consistentemente JEA em cada máquina.

Para implementar a JEA com DSC, certifique-se de que são cumpridos os seguintes pré-requisitos:

- Um ou mais funcionalidades de função foram criadas e adicionadas a um módulo do PowerShell.
- O módulo do PowerShell que contém as funções é armazenado numa partilha de ficheiros (só de leitura) acessível por cada máquina.
- Definições para a configuração de sessão foram identificadas. Não precisa de criar um ficheiro de configuração de sessão ao usar o recurso de DSC de JEA.
- Tem as credenciais que permitem que as ações administrativas em cada máquina ou o acesso ao servidor de solicitação do DSC utilizado para gerir as máquinas.
- Baixar o [recursos de DSC de JEA](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource).

Crie uma configuração de DSC para o ponto de final JEA num servidor de destino máquina ou pull. Nesta configuração, o **JustEnoughAdministration** recursos de DSC define o ficheiro de configuração de sessão e a **ficheiro** recurso copia as capacidades de função da partilha de ficheiros.

As seguintes propriedades são configuráveis com o recurso de DSC:

- Definições de funções
- Grupos de conta virtual
- Nome da conta de serviço gerida de grupo
- Diretório de transcrição
- Unidade de utilizador
- Regras de acesso condicional
- Scripts de inicialização para a sessão JEA

A sintaxe para cada uma dessas propriedades numa configuração de DSC é consistente com o ficheiro de configuração de sessão do PowerShell.

Segue-se um exemplo de configuração de DSC para um módulo de manutenção geral do servidor. Parte do princípio de que um módulo do PowerShell válido que contém funcionalidades de função está localizado no `\\myfileshare\JEA` partilha de ficheiros.

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

Em seguida, a configuração é aplicada num sistema invocando diretamente o [Gestor de configuração Local](/powershell/dsc/managing-nodes/metaConfig) ou a atualizar a [configuração de servidor pull](/powershell/dsc/pull-server/pullServer).

O recurso de DSC também permite-lhe substituir a predefinição **Microsoft** ponto final. Quando substituído, o recurso regista automaticamente um ponto de final de cópia de segurança com o nome **Microsoft.PowerShell.Restricted**. O ponto de final de cópia de segurança tem a ACL de WinRM que permite que utilizadores de gestão remota e os administradores locais membros do grupo para aceder ao mesmo padrão.

## <a name="unregistering-jea-configurations"></a>A anular o registo configurações de JEA

O [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet Remove um ponto final JEA. Anular o registo de um ponto final JEA impede que novos usuários a criação de novas sessões JEA no sistema. Ele também permite-lhe atualizar uma configuração de JEA registando novamente um arquivo de configuração de sessão atualizadas utilizando o mesmo nome de ponto final.

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> Ponto final de anular o registo de um JEA faz com que o serviço WinRM seja reiniciado. Isso interrompe remotas mais operações de gestão em curso, incluindo outras sessões do PowerShell, invocações do WMI e algumas ferramentas de gerenciamento. Anular o registo apenas pontos finais do PowerShell durante as janelas de manutenção planeada.

## <a name="next-steps"></a>Passos Seguintes

[Testar o ponto final da JEA](using-jea.md)
