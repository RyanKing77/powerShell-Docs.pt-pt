---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Utilizar o DSC no servidor de Nano
ms.openlocfilehash: 7427d6bb7644f513b9b523f284109f5ae0f8ef27
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="using-dsc-on-nano-server"></a>Utilizar o DSC no servidor de Nano

> Aplica-se a: O Windows PowerShell 5.0

**DSC no servidor de Nano** é um pacote opcional no `NanoServer\Packages` pasta do suporte de dados do Windows Server 2016. O pacote pode ser instalado quando criar um VHD para um servidor de nano for apresentado, especificando **Microsoft NanoServer-DSC pacote** como o valor a **pacotes** parâmetro do **NanoServerImage novo**  função. Por exemplo, se estiver a criar um VHD para uma máquina virtual, o comando seria o seguinte aspeto:

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

Para obter informações sobre como instalar e utilizar o servidor de nano for apresentado, bem como gerir o servidor de Nano com comunicação remota do PowerShell, consulte [introdução ao servidor Nano](https://technet.microsoft.com/en-us/library/mt126167.aspx).


## <a name="dsc-features-available-on-nano-server"></a>Funcionalidades de DSC disponíveis no servidor de Nano

 Porque o servidor de Nano suporta apenas um conjunto limitado de APIs comparado comparadas uma versão completa do Windows Server, DSC no servidor de Nano tem paridade funcional completa com DSC em execução no SKUs completos para o tempo a ser. DSC no servidor de Nano está em desenvolvimento Active Directory e não ainda funcionalidade completa.
 
 As seguintes funcionalidades de DSC estão atualmente disponíveis no servidor de Nano: 


* Modos push e pull

* Todos os cmdlets de DSC que existe uma versão completa do Windows Server, incluindo o seguinte: 
  * [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx)
  * [Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx)   
  * [Enable-DscDebug](https://technet.microsoft.com/en-us/library/mt517870.aspx)
  * [Disable-DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx)       
  * [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx)
  * [Stop-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143542.aspx)
  * [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx)
  * [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx)      
  * [Publish-DscConfiguraiton](https://technet.microsoft.com/en-us/library/mt517875.aspx) 
  * [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx)
  * [Restore-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407383.aspx)
  * [Remove-DscConfigurationDocument](https://technet.microsoft.com/en-us/library/mt143544.aspx)
  * [Get-DscConfigurationStatus](https://technet.microsoft.com/en-us/library/mt517868.aspx)
  * [Invoke-DscResource](https://technet.microsoft.com/en-us/library/mt517869.aspx)
  * [Find-DscResource](https://technet.microsoft.com/en-us/library/mt517874.aspx)
  * [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)
  * [New-DscChecksum](https://technet.microsoft.com/en-us/library/dn521622.aspx)    

* Compilar configurações (consulte [configurações de DSC](configurations.md))

  **Problema:** encriptação da palavra-passe (consulte [proteger o ficheiro MOF](securemof.md)) durante a configuração de compilação não funciona.

* Compilar metaconfigurations (consulte [configurar o Gestor de configuração Local](metaConfig.md))

* Executar um recurso no contexto de utilizador (consulte [DSC em execução com as credenciais de utilizador (RunAs)](runAsUser.md))

* Recursos baseados em classe (consulte [escrever um recurso personalizado de DSC com classes de PowerShell](authoringResourceClass.md))

* A depuração de recursos de DSC (consulte [recursos de DSC depuração](debugresource.md))
  
  **Problema:** não funciona se um recurso está a utilizar PsDscRunAsCredential (consulte [DSC em execução com as credenciais de utilizador](runAsUser.md))

* [Especificar dependências entre nós](crossNodeDependencies.md) 

* [Controlo de versões do recurso](sxsResource.md)

* Cliente de extração (configurações e recursos) (consulte [configurar um cliente de solicitação utilizando nomes de configuração](pullClientConfigNames.md))

* [Configurações parciais (extração & push)](partialConfigs.md)

* [Reportam ao servidor de solicitação](reportServer.md) 

* Encriptação de MOF

* Registo de eventos

* Relatório de DSC da automatização do Azure

* Recursos que são totalmente funcionais
  * [Arquivo](archiveResource.md)
  * [Environment](environmentResource.md)
  * [Ficheiro](fileResource.md)
  * [Registo](logResource.md)
  * ProcessSet
  * [Registry](registryResource.md)
  * [Script](scriptResource.md)
  * WindowsPackageCab
  * [WindowsProcess](windowsProcessResource.md)
  * WaitForAll (consulte [especificar dependências entre nós](crossNodeDependencies.md))
  * WaitForAny (consulte [especificar dependências entre nós](crossNodeDependencies.md))
  * WaitForSome (consulte [especificar dependências entre nós](crossNodeDependencies.md))

* Recursos que estão parcialmente funcionais
  * [Grupo](groupResource.md)
  * GroupSet
  
  **Problema:** acima recursos falhar se a instância específica é chamada duas vezes (com duas vezes a mesma configuração)
  
  * [Serviço](serviceResource.md)
  * ServiceSet
  
  **Problema:** só funciona para iniciar/parar serviço (estado). Falhar, se um tentar alterar outros atributos de serviço startuptype, as credenciais, descrição, etc.. O erro emitido é semelhante a:
  
  *Não é possível localizar o tipo [management.managementobject]: Certifique-se de que a assemblagem que contém este tipo está carregada.*
  
* Recursos que não estão funcionais
  * [Utilizador](userResource.md)
  

## <a name="dsc-features-not-available-on-nano-server"></a>Funcionalidades de DSC não está disponíveis no servidor de Nano

As seguintes funcionalidades de DSC não estão atualmente disponíveis no servidor de Nano:

* Desencriptar MOF documento com incorrectas encriptados 
* Servidor de solicitação – não pode atualmente configurar um servidor de solicitação no servidor de Nano
* Tudo o que não se encontra na lista de funcionalidade funciona

## <a name="using-custom-dsc-resources-on-nano-server"></a>Utilizar recursos de DSC personalizados no servidor de Nano
 
Devido a um conjuntos limitado das APIs do Windows e estão disponíveis no Nano servidor de bibliotecas CLR, recursos de DSC funcionam na versão CLR completa do Windows não necessariamente funcionam no servidor de nano for apresentado. Conclua o teste de ponto-a-ponto antes de implementar quaisquer recursos personalizados do DSC no ambiente de produção.

## <a name="see-also"></a>Consulte Também
- [Introdução ao servidor Nano](https://technet.microsoft.com/en-us/library/mt126167.aspx)

