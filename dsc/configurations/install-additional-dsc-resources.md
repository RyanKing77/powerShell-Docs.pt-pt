---
ms.date: 12/12/2018
keywords: DSC, powershell, recurso, galeria, a configuração
title: Instalar os recursos de DSC adicionais
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405214"
---
# <a name="install-additional-dsc-resources"></a>Instalar os recursos de DSC adicionais

PowerShell inclui vários recursos de Out-of-the-box para Desired State Configuration (DSC). O **PSDesiredStateConfiguration** módulo contém todos os recursos de DSC de OOB disponíveis na sua instância específica do PowerShell.

Esta é uma lista dos recursos OOB incluídos no PowerShell 4.0 e uma descrição das capacidades do recurso.

> [!NOTE]
> Esta é uma lista incompleta, como o número de recursos OOB cresceu com cada versão do PowerShell.

|Recurso  |Descrição  |
|---------|---------|
|**Ficheiro**|Controla o estado de arquivos e diretórios. Copia os ficheiros a partir de um **origem** para um **destino** e atualiza-las quando o **origem** alterações comparando as datas, as somas de verificação e hashes.|
|**Arquivo**|Descompacta arquivos mortos e uma localização especificada. Valida os arquivos com uma determinada **soma de verificação**.|
|**Ambiente**|Gere as variáveis de ambiente.|
|**Grupo**|Gere os grupos locais e controla a associação de grupo.|
|**Registo**|Escreve mensagens para o `Microsoft-Windows-Desired State Configuration/Analytic` registo de eventos.|
|**Pacote**|Instala ou desinstala os pacotes usando **argumentos**, **LogPath**, **ReturnCode**, outras definições.|
|**registo**|Gere chaves de registo e valores.|
|**Script**|Permite-lhe criar sua própria [get-teste-set](../resources/get-test-set.md) blocos de script.|
|**Serviço**|Configura os serviços do Windows.|
|**Utilizador** |Gere utilizadores locais e atributos.|
|**WindowsFeature**|Gere funções e funcionalidades.|
|**WindowsProcess**|Configura os processos do Windows.|

Os recursos OOB permitem que um ponto de partida para operações comuns. Se os recursos OOB não atenderem às suas necessidades, pode escrever a sua própria [recurso personalizado](../resources/authoringResource.md). Antes de escrever um recurso personalizado para resolver seu problema, deve procurar por meio do grande número de recursos de DSC que já foram criados pela Microsoft e a Comunidade do PowerShell.

Pode encontrar recursos de DSC em ambos os [galeria do PowerShell](https://www.powershellgallery.com/) e [GitHub](https://github.com/). Também pode instalar os recursos de DSC diretamente a partir da consola do PowerShell através de [PowerShellGet](/powershell/module/powershellget/).

## <a name="installing-powershellget"></a>Installing PowerShellGet (Instalar o PowerShellGet)

Para determinar se já tiver **PowerShell** obter ou para obter ajuda instalá-lo, consulte o guia seguinte: [Instalar o PowerShellGet](/powershell/gallery/installing-psget).

## <a name="finding-dsc-resources-using-powershellget"></a>Localizar recursos de DSC a utilização do PowerShellGet

Uma vez **PowerShellGet** está instalado no seu sistema, pode encontrar e instalar os recursos de DSC alojados no [galeria do PowerShell](https://www.powershellgallery.com/).

Em primeiro lugar, utilize o [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet para localizar os recursos de DSC. Quando executa `Find-DSCResource` pela primeira vez, verá o seguinte pedido para instalar o fornecedor"NuGet".

```
PS> Find-DSCResource

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The
NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\xAdministrator\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider
 by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to
install and import the NuGet provider now?
[Y] Yes  [N] No  [?] Help (default is "Y"):
```

Depois prima 'y', está instalado o fornecedor de "NuGet", é apresentada uma lista de recursos de DSC que pode instalar a partir da galeria do PowerShell.

> [!NOTE]
> Não é apresentada a lista porque é muito grande.

Também pode especificar a `-Name` parâmetro utilizando carateres universais, ou `-Filter` parâmetro sem carateres universais para limitar a pesquisa. Neste exemplo tenta encontrar um recurso de "Fuso horário" DSC com os carateres universais.

> [!IMPORTANT]
> Atualmente, existe um bug no `Find-DSCResource` cmdlet que impede a utilização de carateres universais em ambos os `-Name` e `-Filter` parâmetros. O segundo exemplo abaixo mostra uma solução usando `Where-Object`.

```
PS> Find-DSCResource -Name *Time*

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Carbon_EnvironmentVariable          2.6.0      Carbon                              PSGallery
Carbon_FirewallRule                 2.6.0      Carbon                              PSGallery
Carbon_Group                        2.6.0      Carbon                              PSGallery
Carbon_IniFile                      2.6.0      Carbon                              PSGallery
Carbon_Permission                   2.6.0      Carbon                              PSGallery
Carbon_Privilege                    2.6.0      Carbon                              PSGallery
Carbon_ScheduledTask                2.6.0      Carbon                              PSGallery
Carbon_Service                      2.6.0      Carbon                              PSGallery
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
xTimeZone                           1.8.0.0    xTimeZone                           PSGallery
xSqlServerDefaultDir                1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerMoveDatabaseFiles         1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerSQLDataRoot               1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerStartupParam              1.0.0      mlSqlServerDSC                      PSGallery
```

Também pode utilizar `Where-Object` para localizar os recursos de DSC com a filtragem mais granular. Essa abordagem será mais lenta do que usando incorporado em parâmetros de filtragem.

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

Para obter mais informações sobre a filtragem, consulte [Where-Object](/powershell/module/microsoft.powershell.core/where-object).

## <a name="installing-dsc-resources-using-powershellget"></a>Instalar os recursos de DSC com o PowerShellGet

Para instalar um recurso de DSC, utilize o [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, especificando o nome do módulo mostrado na **módulo** nome nos resultados da pesquisa.

O recurso de "Fuso horário" existe no módulo "ComputerManagementDSC", é assim que este exemplo instala o módulo.

> [!NOTE]
> Se não tiver considerado fidedigno da galeria do PowerShell, verá o aviso abaixo solicitar a confirmação e, com instruções como evitar pedidos subsequentes no instala.

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

Prima 'y' para continuar a instalar o módulo. Após a instalação, pode verificar se o seu novo recurso está instalado usando [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).

```
PS> Get-DSCResource -Name TimeZone -Syntax

TimeZone [String] #ResourceName
{
    IsSingleInstance = [string]{ Yes }
    TimeZone = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

Também pode exibir outros recursos no seu módulo recentemente instalado, especificando o `-ModuleName` parâmetro.

```
PS> Get-DSCResource -Module ComputerManagementDSC

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      Computer                  ComputerManagementDsc          6.0.0.0    {Name, Credential, DependsOn, ...
PowerShell      OfflineDomainJoin         ComputerManagementDsc          6.0.0.0    {IsSingleInstance, RequestFile...
PowerShell      PowerPlan                 ComputerManagementDsc          6.0.0.0    {IsSingleInstance, Name, Depen...
PowerShell      PowerShellExecutionPolicy ComputerManagementDsc          6.0.0.0    {ExecutionPolicy, ExecutionPol...
PowerShell      ScheduledTask             ComputerManagementDsc          6.0.0.0    {TaskName, ActionArguments, Ac...
PowerShell      TimeZone                  ComputerManagementDsc          6.0.0.0    {IsSingleInstance, TimeZone, D...
PowerShell      VirtualMemory             ComputerManagementDsc          6.0.0.0    {Drive, Type, DependsOn, Initi...
```

## <a name="see-also"></a>Consulte também

- [Quais são os recursos?](../resources/resources.md)
