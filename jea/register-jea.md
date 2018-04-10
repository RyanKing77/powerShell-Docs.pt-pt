---
ms.date: 06/12/2017
author: rpsqrd
ms.topic: conceptual
keywords: jea, powershell, segurança
title: Registar JEA configurações
ms.openlocfilehash: 7b0a3f0bac26bf62989fecdf60388bbebd6fa756
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="registering-jea-configurations"></a>Registar JEA configurações

> Aplica-se a: Windows PowerShell 5.0

O último passo antes de poder utilizar JEA assim que tiver o [capacidades de função](role-capabilities.md) e [ficheiro de configuração de sessão](session-configurations.md) criado é para registar o ponto final JEA.
Este processo aplica-se as informações de configuração de sessão para o sistema e disponibiliza o ponto final para utilização por utilizadores e de motores de automatização.

## <a name="single-machine-configuration"></a>Configuração da máquina único

Para ambientes pequenos, pode implementar o JEA registando a configuração de sessão ficheiros com o [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.

Antes de começar, certifique-se de que os seguintes pré-requisitos foram cumpridos:
- Uma ou mais funções foi criado e colocado na pasta 'RoleCapabilities' de um módulo do PowerShell válida.
- Foi criado e testado um ficheiro de configuração de sessão.
- O utilizador ao registar a configuração de JEA tem direitos de administrador sobre os sistemas.

Também terá de selecionar um nome para o ponto final JEA.
O nome do ponto final JEA serão necessário quando os utilizadores que pretende estabelecer ligação ao sistema através da JEA.
Pode utilizar o [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet para verificar os nomes dos pontos finais existentes no sistema.
Pontos finais que começam por 'microsoft', normalmente, são fornecidos com o Windows.
O ponto final 'Microsoft' é o ponto final predefinido utilizado ao ligar a um ponto final de PowerShell remoto.

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

Quando determinar um nome adequado para o ponto final JEA, execute o seguinte comando para registar o ponto final.

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> O comando acima irá reiniciar o serviço WinRM no sistema.
> Isto irá terminar todas as sessões de comunicação remota do PowerShell, bem como quaisquer configurações de DSC em curso.
> Recomenda-se que colocar as máquinas de produção offline antes de executar o comando para evitar perturbar operações de negócio.

Se o registo foi efetuado com êxito, está pronto para [utilizar JEA](using-jea.md).
Pode eliminar o ficheiro de configuração de sessão em qualquer altura; Não é utilizado após o registo.

## <a name="multi-machine-configuration-with-dsc"></a>Configuração de múltiplos computador com o DSC

Se estiver a implementar o JEA em várias máquinas, o modelo de implementação mais simples consiste em utilizar o JEA [configuração de estado pretendido](https://msdn.microsoft.com/en-us/powershell/dsc/overview) recursos para implementar rápida e consistentemente JEA em cada máquina.

Para implementar JEA com DSC, terá de Certifique-se de que são cumpridos os seguintes pré-requisitos:
- Um ou mais capacidades de função tenham sido criadas e adicionadas a um módulo do PowerShell válido.
- O módulo do PowerShell que contém as funções é armazenado numa partilha de ficheiros (só de leitura) acessível por cada máquina.
- Definições para a configuração de sessão foram identificadas. Não é necessário criar um ficheiro de configuração de sessão ao utilizar o recurso de JEA DSC.
- Tem de ter credenciais que permitem-lhe efetuar ações administrativas em cada máquina ou ter acesso a um servidor de solicitação do DSC utilizado para gerir as máquinas.
- Transferiu o [recursos de JEA DSC](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)

Num destino máquina (ou servidor de solicitação, se estiver a utilizar um), crie uma configuração de DSC para o ponto final JEA.
Nesta configuração, irá utilizar os recursos de JustEnoughAdministration DSC para configurar o ficheiro de configuração de sessão e o recurso de ficheiros a copiar sobre as capacidades de função da partilha de ficheiros.

As seguintes propriedades são configuráveis com os recursos de DSC:
- Definições de função
- Grupos de conta virtuais
- Nome de conta de serviço gerida de grupo
- Diretório de transcript
- Unidade de utilizador
- Regras de acesso condicional
- Scripts de arranque para a sessão JEA

A sintaxe para cada uma destas propriedades numa configuração de DSC é consistente com o ficheiro de configuração de sessão do PowerShell.

Segue-se uma configuração de DSC de exemplo para um módulo de manutenção gerais do servidor.

Parte do pressuposto de que um módulo do PowerShell válido que contém as capacidades de função numa subpasta 'RoleCapabilities' se encontra localizado no '\\\\myfileshare\\JEA' Partilha de ficheiros.


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

Esta configuração, em seguida, pode ser aplicada num sistema por [diretamente invocar o Gestor de configuração Local](https://msdn.microsoft.com/en-us/powershell/dsc/metaconfig) ou atualizar o [configuração do servidor de solicitação](https://msdn.microsoft.com/en-us/powershell/dsc/pullserver).

O recurso de DSC também permite-lhe substituir o ponto de final predefinido da gestão remota do Microsoft.
Se o fizer, o recurso será registado automaticamente um ponto final de cópia de segurança unconstrainted com o nome "Microsoft.PowerShell.Restricted" que tem a predefinição de ACL de WinRM (permitir que utilizadores de gestão remota e os administradores locais membros do grupo para aceder ao mesmo).

## <a name="unregistering-jea-configurations"></a>A anular registo configurações de JEA

Para remover um ponto final de JEA num sistema, utilize o [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet.
A anulação do registo um ponto final JEA irá impedir que os novos utilizadores da criação de novas sessões JEA no sistema.
Também permite-lhe atualizar uma configuração de JEA registando novamente um ficheiro de configuração de sessão atualizadas com o mesmo nome de ponto final.

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> A anulação do registo um JEA endpoint fará com que o serviço WinRM para reiniciar.
> Isto irá interromper a operações de gestão mais remotas em curso, incluindo outras sessões de PowerShell, invocações de WMI e algumas ferramentas de gestão.
> Anular o registo apenas pontos finais de PowerShell durante as janelas de manutenção planeada.

## <a name="next-steps"></a>Próximos passos

- [O ponto final JEA de teste](using-jea.md)