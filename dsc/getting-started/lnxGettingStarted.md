---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Começar com o Desired State Configuration (DSC) para Linux
ms.openlocfilehash: a18b226d4b2d8b8e1ba8b4168ec6ad8f73c73c42
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079698"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a>Começar com o Desired State Configuration (DSC) para Linux

Este tópico explica como começar a utilizar o PowerShell Desired State Configuration (DSC) para Linux. Para obter informações gerais sobre o DSC, veja [introdução ao Windows PowerShell Desired State Configuration](../overview/overview.md).

## <a name="supported-linux-operation-system-versions"></a>Versões suportadas do sistema de operação do Linux

As seguintes versões do sistema operativo Linux são suportadas para DSC para Linux.

- CentOS 5, 6 e 7 (x86/x64)
- Debian GNU/Linux 6, 7 e 8 (x86/x64)
- Oracle Linux 5, 6 e 7 (x86/x64)
- Red Hat Enterprise Linux Server 5, 6 e 7 (x86/x64)
- SUSE Linux Enterprise Server 10, 11 e 12 (x86/x64)
- Servidor de Ubuntu 12.04 LTS, 14.04 LTS e 16.04 LTS (x86/x64)

A tabela seguinte descreve as dependências de pacote necessária para DSC para Linux.

|  Pacote necessário |  Descrição |  Versão mínima |
|---|---|---|
| glibc| Biblioteca do GNU| 2…4 – 31.30|
| python| Python| 2.4 – 3.4|
| omiserver| Abrir infraestrutura de gestão| 1.0.8.1|
| openssl| Bibliotecas de OpenSSL| 0.9.8 ou 1.0|
| ctypes| Biblioteca de Python CTypes| Tem de corresponder à versão do Python|
| libcurl| biblioteca de clientes de http de cURL| 7.15.1|

## <a name="installing-dsc-for-linux"></a>Instalar o DSC para Linux

Tem de instalar o [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) antes de instalar o DSC para Linux.

### <a name="installing-omi"></a>Instalar o OMI

Desired State Configuration for Linux requer que o servidor CIM Open Management Infrastructure (OMI), versão 1.0.8.1 ou posterior. O OMI pode ser transferido da Open Group: [Abra o Management Infrastructure (OMI)](https://github.com/Microsoft/omi).

Para instalar o OMI, instale o pacote que é adequado para o seu sistema Linux (.rpm ou .deb) e a versão de OpenSSL (ssl_098 ou ssl_100) e a arquitetura (x64/x86). Pacotes de RPM são adequadas para CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server e Oracle Linux. Pacotes de DEB são adequadas para Debian GNU/Linux e Ubuntu Server. Os pacotes de ssl_098 são adequados para computadores com OpenSSL 0.9.8 instalado enquanto os pacotes de ssl_100 são adequados para computadores com o 1.0 OpenSSL instalado.

> [!NOTE]
> Para determinar a versão de OpenSSL instalada, execute o comando `openssl version`.

Execute o seguinte comando para instalar o OMI num sistema de CentOS 7 x64.

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a>Instalar o DSC

DSC para Linux está disponível para download [aqui](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294).

Para instalar o DSC, instale o pacote que é adequado para o seu sistema Linux (.rpm ou .deb) e a versão de OpenSSL (ssl_098 ou ssl_100) e a arquitetura (x64/x86). Pacotes de RPM são adequadas para CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server e Oracle Linux. Pacotes de DEB são adequadas para Debian GNU/Linux e Ubuntu Server. Os pacotes de ssl_098 são adequados para computadores com OpenSSL 0.9.8 instalado enquanto os pacotes de ssl_100 são adequados para computadores com o 1.0 OpenSSL instalado.

> [!NOTE]
> Para determinar a versão de OpenSSL instalada, execute a versão de openssl de comando.

Execute o seguinte comando para instalar o DSC num sistema de CentOS 7 x64.

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`

## <a name="using-dsc-for-linux"></a>Utilizar o DSC para Linux

As secções seguintes explicam como criar e executar configurações de DSC em computadores com Linux.

### <a name="creating-a-configuration-mof-document"></a>Criar um documento de MOF de configuração

A palavra-chave de configuração do Windows PowerShell é utilizada para criar uma configuração para computadores Linux, assim como para computadores Windows. Os passos seguintes descrevem a criação de um documento de configuração para um computador Linux com o Windows PowerShell.

1. Importe o módulo de nx. O módulo do Windows PowerShell nx contém o esquema para recursos incorporados para DSC para Linux e tem de ser instalado no computador local e importado para a configuração.

   - Para instalar o módulo de nx, copie o diretório de módulo nx para qualquer um `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` ou `$PSHOME\Modules`. O módulo de nx está incluído no DSC para o pacote de instalação de Linux. Para importar o módulo de nx na sua configuração, utilize o `Import-DSCResource` comando:

   ```powershell
   Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

   }
   ```

2. Definir uma configuração e gerar o documento de configuração:

   ```powershell
   Configuration ExampleConfiguration
   {
        Import-DscResource -Module nx

        Node  "linuxhost.contoso.com"
        {
            nxFile ExampleFile 
            {
                DestinationPath = "/tmp/example"
                Contents = "hello world `n"
                Ensure = "Present"
                Type = "File"
            }
        }
   }

   ExampleConfiguration -OutputPath:"C:\temp"
   ```

### <a name="push-the-configuration-to-the-linux-computer"></a>Enviar a configuração para o computador com Linux

Documentos de configuração (ficheiros MOF) podem ser enviados para o computador Linux, com o [Start-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet. Para utilizar este cmdlet, juntamente com o [Get-dscconfiguration para](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration), ou [Test-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) cmdlets, remotamente para um computador Linux, tem de utilizar um CIMSession. O [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet é utilizado para criar um CIMSession para o computador Linux.

O código seguinte mostra como criar um CIMSession para DSC para Linux.

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName "root" -Message "Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl $true -SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl $true
$Sess=New-CimSession -Credential $credential -ComputerName $Node -Port 5986 -Authentication basic -SessionOption $opt -OperationTimeoutSec 90
```

> [!NOTE]
> Para o modo "Push", a credencial do usuário tem de ser o utilizador raiz no computador Linux.
> Ligações de SSL/TLS apenas são suportadas para DSC para Linux, o `New-CimSession` deve ser utilizado com o parâmetro – UseSSL definido como $true.
> O certificado SSL utilizado pelo OMI (para DSC) é especificado no ficheiro: `/opt/omi/etc/omiserver.conf` com as propriedades: pemfile e ficheiro de chave.
> Se este certificado não é considerado fidedigno pelo computador do Windows que está a executar o [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet no, pode optar por ignorar a validação do certificado com as opções de CIMSession: `-SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true`

Execute o seguinte comando para enviar a configuração de DSC para o nó de Linux.

`Start-DscConfiguration -Path:"C:\temp" -CimSession $Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a>Distribuir a configuração com um servidor de solicitação

Configurações podem ser distribuídas para um computador com Linux com um servidor de solicitação, assim como para computadores Windows. Para obter orientações sobre como utilizar um servidor de solicitação, veja [Windows PowerShell Desired State Configuration Pull servidores](../pull-server/pullServer.md). Para obter informações adicionais e limitações relacionadas ao uso de computadores com Linux com um servidor de solicitação, consulte as notas de versão para de Desired State Configuration para Linux.

### <a name="working-with-configurations-locally"></a>Trabalhar com configurações localmente

DSC para Linux inclui scripts para trabalhar com a configuração do computador local do Linux. Estes scripts estão localizar no `/opt/microsoft/dsc/Scripts` e inclua o seguinte:

- GetDscConfiguration.py

Devolve a configuração atual aplicada ao computador. Semelhante para o cmdlet do Windows PowerShell `Get-DscConfiguration` cmdlet.

`# sudo ./GetDscConfiguration.py`

- GetDscLocalConfigurationManager.py

Devolve o meta-configuração atual aplicada ao computador. Semelhante ao cmdlet [Get-dsclocalconfigurationmanager para](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet.

`# sudo ./GetDscLocalConfigurationManager.py`

- InstallModule.py

Instala um módulo de recurso personalizado do DSC. Requer o caminho para um ficheiro. zip que contém a biblioteca de objetos partilhados do módulo e ficheiros MOF de esquema.

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

- RemoveModule.py

Remove um módulo de recurso personalizado do DSC. Requer o nome do módulo para remover.

`# sudo ./RemoveModule.py cnx_Resource`

- StartDscLocalConfigurationManager.py

Aplica-se um ficheiro MOF de configuração para o computador. Semelhante a [Start-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet. Requer o caminho para a configuração do MOF para aplicar.

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

- SetDscLocalConfigurationManager.py

Aplica-se um ficheiro MOF de configuração de Meta no computador. Semelhante a [Set-dsclocalconfigurationmanager para](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet. Requer o caminho para o MOF de configuração de Meta para aplicar.

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a>PowerShell Desired State Configuration para ficheiros de registo do Linux

Os seguintes ficheiros de registo são gerados para DSC para Linux de mensagens.

|Ficheiro de registo|Diretório|Descrição|
|---|---|---|
|**omiserver.log**|`/var/opt/omi/log`|Mensagens relacionadas com a operação do servidor OMI CIM.|
|**dsc.log**|`/var/opt/omi/log`|Mensagens relacionadas com a operação das operações de recursos do Gestor de configuração Local (LCM) e de DSC.|
