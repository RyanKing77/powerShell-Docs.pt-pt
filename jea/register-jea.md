---
ms.date: 06/12/2017
keywords: jea, powershell, segurança
title: Registar a JEA configurações
ms.openlocfilehash: 160aa95283da57a10aad5fdd4043adb1354a5db5
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002911"
---
# <a name="registering-jea-configurations"></a>Registar a JEA configurações

> Aplica-se a: Windows PowerShell 5.0

Depois de ter sua [funcionalidades de função](role-capabilities.md) e [o ficheiro de configuração de sessão](session-configurations.md) criado, a última etapa antes de poder utilizar o JEA é registar o ponto final JEA.
Registar o ponto final da JEA com o sistema faz com que o ponto final disponíveis para utilização por utilizadores e os mecanismos de automatização.

## <a name="single-machine-configuration"></a>Configuração de máquina única

Em ambientes pequenos, pode implementar a JEA registrando-se a configuração de sessão ficheiro com o [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.

Antes de começar, certifique-se de que os seguintes pré-requisitos foram cumpridos:
- Uma ou mais funções foi criado e colocado na pasta "RoleCapabilities" de um módulo do PowerShell válida.
- Um ficheiro de configuração de sessão tem de ser criado e testado.
- O utilizador a que se registe a configuração de JEA tem direitos de administrador sobre os sistemas.

Também tem de selecionar um nome para o ponto de final JEA.
É necessário o nome do ponto final JEA quando os utilizadores se quer ligar ao sistema através de JEA.
Pode utilizar o [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet para verificar os nomes dos pontos finais existentes no sistema.
Pontos de extremidade que começam por "microsoft", normalmente, são fornecidos com o Windows.
O ponto final de "Microsoft" é o ponto final predefinido utilizado ao ligar a um ponto de extremidade remoto do PowerShell.

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

Quando determinar um nome apropriado para seu ponto final da JEA, execute o seguinte comando para registar o ponto final.

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> O comando acima reinicia o serviço de WinRM no sistema.
> Isso encerra a todas as sessões de comunicação remota do PowerShell, bem como quaisquer configurações de DSC em curso.
> Recomenda-se que colocar qualquer máquinas de produção offline antes de executar o comando para evitar interromper as operações de negócio.

Se o registo é concluída com êxito, está pronto para [utilizar a JEA](using-jea.md).
Pode eliminar o ficheiro de configuração de sessão em qualquer altura; Não é utilizado após o registo do ponto final.

## <a name="multi-machine-configuration-with-dsc"></a>Configuração de várias máquinas com DSC

Se estiver implantando JEA em várias máquinas, o modelo de implementação mais simples consiste em utilizar a JEA [Desired State Configuration do](https://msdn.microsoft.com/powershell/dsc/overview) recursos para implementar rápida e consistentemente JEA em cada máquina.

Para implementar a JEA com DSC, terá de garantir que são cumpridos os seguintes pré-requisitos:
- Um ou mais funcionalidades de função foram criadas e adicionadas a um módulo do PowerShell válido.
- O módulo do PowerShell que contém as funções é armazenado numa partilha de ficheiros (só de leitura) acessível por cada máquina.
- Definições para a configuração de sessão foram identificadas. Não é necessário criar um ficheiro de configuração de sessão ao usar o recurso de DSC de JEA.
- Tem as credenciais que permitem-lhe efetuar ações administrativas em cada máquina ou ter acesso a um servidor de solicitação de DSC utilizado para gerir as máquinas.
- Transferir o [recursos de DSC de JEA](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)

Num destino máquina (ou servidor de solicitação, se estiver a utilizar um), crie uma configuração de DSC para o ponto de final JEA.
Nesta configuração, utilize o recurso de DSC JustEnoughAdministration para configurar o ficheiro de configuração de sessão e o recurso de ficheiro para copiar em relação aos recursos de função da partilha de ficheiros.

As seguintes propriedades são configuráveis com o recurso de DSC:
- Definições de funções
- Grupos de conta virtual
- Nome de conta de serviço gerida de grupo
- Diretório de transcrição
- Unidade de utilizador
- Regras de acesso condicional
- Scripts de inicialização para a sessão JEA

A sintaxe para cada uma dessas propriedades numa configuração de DSC é consistente com o ficheiro de configuração de sessão do PowerShell.

Segue-se um exemplo de configuração de DSC para um módulo de manutenção geral do servidor.

Parte do princípio de que um módulo do PowerShell válido que contém as funcionalidades de função numa subpasta do 'RoleCapabilities' está localizado no '\\\\myfileshare\\JEA "partilha de ficheiros.


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

Esta configuração, em seguida, pode ser aplicada num sistema pelo [invocando diretamente o Gestor de configuração Local](https://msdn.microsoft.com/powershell/dsc/metaconfig) ou a atualizar a [configuração de servidor de solicitação](https://msdn.microsoft.com/powershell/dsc/pullserver).

O recurso de DSC também permite que substitua o ponto de extremidade padrão da comunicação remota do Microsoft.
Se fizer isso, o recurso registra automaticamente um ponto de extremidade unconstrainted cópia de segurança com o nome "Microsoft.PowerShell.Restricted" que tem a ACL de WinRM (permitindo que os utilizadores de gestão remota e os administradores locais membros do grupo para aceder ao mesmo) padrão.

## <a name="unregistering-jea-configurations"></a>A anular o registo configurações de JEA

Para remover um ponto final JEA num sistema, utilize o [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet.
Anular o registo de um ponto final JEA impede que novos usuários a criação de novas sessões JEA no sistema.
Ele também permite-lhe atualizar uma configuração de JEA registando novamente um arquivo de configuração de sessão atualizadas utilizando o mesmo nome de ponto final.

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> Ponto final de anular o registo de um JEA faz com que o serviço WinRM seja reiniciado.
> Isso interrompe remotas mais operações de gestão em curso, incluindo outras sessões do PowerShell, invocações do WMI e algumas ferramentas de gerenciamento.
> Anular o registo apenas pontos finais do PowerShell durante as janelas de manutenção planeada.

## <a name="next-steps"></a>Próximos passos

- [Testar o ponto final da JEA](using-jea.md)
