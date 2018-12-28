---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Utilizar o DSC no Servidor Nano
ms.openlocfilehash: fd81fe56d16100f45d9ee2dfd8fdc303c2a6c17a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404956"
---
# <a name="using-dsc-on-nano-server"></a>Utilizar o DSC no Servidor Nano

> Aplica-se a: Windows PowerShell 5.0

**DSC no servidor Nano** é um pacote opcional no `NanoServer\Packages` pasta do suporte de dados do Windows Server 2016. O pacote pode ser instalado quando criar um VHD para um servidor Nano, especificando **Microsoft-NanoServer-DSC-Package** como o valor da **pacotes** parâmetro do **New-NanoServerImage**  função. Por exemplo, se estiver a criar um VHD para uma máquina virtual, o comando teria o aspeto semelhante ao seguinte:

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

Para obter informações sobre como instalar e utilizar o servidor Nano, bem como gerir o servidor Nano com a comunicação remota do PowerShell, consulte [introdução ao Nano Server](/windows-server/get-started/getting-started-with-nano-server).

## <a name="dsc-features-available-on-nano-server"></a>Recursos de DSC disponíveis no servidor Nano

Como o servidor Nano suporta apenas um conjunto limitado de APIs em comparação com uma versão completa do Windows Server, o DSC no servidor Nano não tem paridade completa funcional com DSC em execução em SKUs completos por enquanto. DSC no servidor Nano está em fase de desenvolvimento e ainda não está recursos completos.

Os seguintes recursos de DSC estão atualmente disponíveis no servidor Nano:

Modos push e pull

- Todos os cmdlets de DSC que existe uma versão completa do Windows Server, incluindo o seguinte:
- [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [Stop-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [Publish-DscConfiguraiton](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [Restore-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [Remove-DscConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [Find-DscResource](https://technet.microsoft.com/en-us/library/mt517874.aspx)
- [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- Compilar configurações (veja [configurações de DSC](../configurations/configurations.md))

  **Problema:** Encriptação de palavra-passe (consulte [proteger o ficheiro MOF](../pull-server/secureMOF.md)) durante a configuração de compilação não funciona.

- Compilar metaconfigurations (consulte [configurar o Gestor de configuração Local](../managing-nodes/metaConfig.md))

- Executar um recurso no contexto de usuário (consulte [a executar o DSC com as credenciais de utilizador (RunAs)](../configurations/runAsUser.md))

- Recursos baseados na classe (consulte [escrever um recurso personalizado do DSC com classes do PowerShell](../resources/authoringResourceClass.md))

- Depuração de recursos de DSC (consulte [recursos de DSC de depuração](../troubleshooting/debugResource.md))

  **Problema:** Não funciona se um recurso está a utilizar PsDscRunAsCredential (consulte [a executar o DSC com as credenciais de utilizador](../configurations/runAsUser.md))

- [Especificar dependências entre nós](../configurations/crossNodeDependencies.md)

- [Controle de versão do recurso](../configurations/sxsResource.md)

- Cliente de solicitação (configurações e recursos) (consulte [como configurar um cliente de solicitação através de nomes de configuração](../pull-server/pullClientConfigNames.md))

- [Configurações parciais (pull & push)](../pull-server/partialConfigs.md)

- [Relatórios para o servidor de solicitação](../pull-server/reportServer.md)

- Encriptação do MOF

- Registo de eventos

- Relatórios de DSC de automatização do Azure

- Recursos que são totalmente funcionais

- **Arquivo**
- **Ambiente**
- **Ficheiro**
- **Registo**
- **ProcessSet**
- **registo**
- **Script**
- **WindowsPackageCab**
- **WindowsProcess**
- **WaitForAll** (consulte [especificar dependências entre nós](../configurations/crossNodeDependencies.md))
- **WaitForAny** (consulte [especificar dependências entre nós](../configurations/crossNodeDependencies.md))
- **WaitForSome** (consulte [especificar dependências entre nós](../configurations/crossNodeDependencies.md))

- Recursos que são parcialmente funcionais
- **Grupo**
- **GroupSet**

  **Problema:** Acima recursos falhar se a instância específica é chamada duas vezes (a ser executada duas vezes a mesma configuração)

- **Serviço**
- **ServiceSet**

  **Problema:** Só funciona para iniciar/parar serviço (estado). Falhar, se um tentar altere os outros atributos de serviço como statuptype, credenciais, descrição etc... O erro gerado é semelhante a:

  *Não é possível localizar o tipo [management.managementobject]: Certifique-se de que o assembly que contém este tipo é carregado.*

- Recursos que não estão funcionais
- **Utilizador**

## <a name="dsc-features-not-available-on-nano-server"></a>Recursos de DSC não está disponíveis no servidor Nano

Os seguintes recursos de DSC não estão atualmente disponíveis no servidor Nano:

- A desencriptação de documento MOF com incorrectas encriptados
- Servidor de solicitação, não pode atualmente configurar um servidor de solicitação no servidor Nano
- Tudo o que não está na lista de recurso funciona

## <a name="using-custom-dsc-resources-on-nano-server"></a>Utilizar recursos de DSC personalizados no servidor Nano

Devido a um limitado conjuntos de APIs do Windows e bibliotecas CLR disponíveis no servidor Nano, os recursos de DSC que funcionam na versão CLR completa do Windows não necessariamente funcionar no servidor Nano.
Conclua o teste de ponto-a-ponto antes de implementar quaisquer recursos personalizados de DSC para um ambiente de produção.

## <a name="see-also"></a>Consulte Também

- [Introdução ao servidor Nano](/windows-server/get-started/getting-started-with-nano-server)
