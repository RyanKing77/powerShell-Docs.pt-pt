---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Começar com configuração de estado pretendido (DSC) para Linux"
ms.openlocfilehash: fd4820d27de5958a325032ca3fc202a521c131b4
ms.sourcegitcommit: 28e71b0ae868014523631fec3f5417de751944f3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/25/2017
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a>Começar com configuração de estado pretendido (DSC) para Linux

Este tópico explica como começar a utilizar o PowerShell pretendido Estado Configuration (DSC) para o Linux. Para obter informações gerais sobre o DSC, consulte [começar com a configuração de estado pretendido do Windows PowerShell](overview.md).

## <a name="supported-linux-operation-system-versions"></a>Versões suportadas do sistema de operação do Linux

As seguintes versões de sistema operativo Linux são suportadas para DSC para Linux.
- CentOS 5, 6 e 7 (x86/x64)
- Debian GNU/Linux 6, 7 e 8 (x86/x64)
- Oracle Linux 5, 6 e 7 (x86/x64)
- Red Hat Enterprise Linux Server 5, 6 e 7 (x86/x64)
- SUSE Linux Enterprise Server 10, 11 e 12 (x86/x64)
- Ubuntu Server 12.04 LTS, 14.04 LTS e 16.04 LTS (x86/x64)

A tabela seguinte descreve as dependências de pacote necessário para DSC para Linux.

|  Pacote necessário |  Descrição |  Versão mínima | 
|---|---|---|
| Glibc| Biblioteca de GNU| 2…4 – 31.30| 
| Python| Python| 2.4 – 3.4| 
| omiserver| Abrir Infraestrutura de Gestão| 1.0.8.1| 
| OpenSSL| Bibliotecas de OpenSSL| 0.9.8 ou 1.0| 
| ctypes| Biblioteca Python CTypes| Tem de corresponder à versão do Python| 
| libcurl| biblioteca de clientes http cURL| 7.15.1| 

## <a name="installing-dsc-for-linux"></a>Instalar o DSC para Linux

Tem de instalar o [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) antes de instalar o DSC de Linux.

### <a name="installing-omi"></a>Instalar o OMI

Configuração do estado pretendido de para Linux requer o servidor CIM Open Management Infrastructure (OMI), versão 1.0.8.1 ou posterior. Pode ser transferido OMI da Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).

Para instalar o OMI, instale o pacote que é adequado para o seu sistema Linux (.rpm ou .deb) e a versão de OpenSSL (ssl_098 ou ssl_100) e a arquitetura (x64/x86). Pacotes RPM são adequados para CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server e Oracle Linux. Pacotes de DEB são adequados para Debian GNU/Linux e Ubuntu Server. Os pacotes de ssl_098 são adequados para computadores com OpenSSL 0.9.8 instalado enquanto os pacotes de ssl_100 são adequados para computadores com OpenSSL 1.0 instalado.

> **Tenha em atenção**: para determinar a versão de OpenSSL instalada, execute o comando `openssl version`.

Execute o seguinte comando para instalar o OMI num sistema CentOS 7 x64.

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a>Instalar o DSC

O DSC de Linux está disponível para transferência [aqui](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/latest). 

Para instalar o DSC, instale o pacote que é adequado para o seu sistema Linux (.rpm ou .deb) e a versão de OpenSSL (ssl_098 ou ssl_100) e a arquitetura (x64/x86). Pacotes RPM são adequados para CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server e Oracle Linux. Pacotes de DEB são adequados para Debian GNU/Linux e Ubuntu Server. Os pacotes de ssl_098 são adequados para computadores com OpenSSL 0.9.8 instalado enquanto os pacotes de ssl_100 são adequados para computadores com OpenSSL 1.0 instalado.

> **Tenha em atenção**: para determinar a versão de OpenSSL instalada, execute a versão de openssl de comando.
 
Execute o seguinte comando para instalar o DSC num sistema CentOS 7 x64.

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`


## <a name="using-dsc-for-linux"></a>Utilizar o DSC para Linux

As secções seguintes explicam como criar e executar as configurações de DSC nos computadores com Linux.

### <a name="creating-a-configuration-mof-document"></a>Criar um documento MOF de configuração

A palavra-chave de configuração do Windows PowerShell é utilizada para criar uma configuração para computadores Linux, tal como em computadores Windows. Os passos seguintes descrevem a criação de um documento de configuração para um computador com Linux através do Windows PowerShell.

1. Importe o módulo de nx. O módulo do Windows PowerShell nx contém o esquema de recursos incorporados para DSC para Linux e tem de ser instalado no computador local e importado para a configuração.

    -Para instalar o módulo de nx, copie o diretório de módulo nx quer `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` ou `$PSHOME\Modules`. O módulo de nx está incluído no DSC Linux pacote de instalação (MSI). Para importar o módulo de nx na configuração, utilize o __importação DSCResource__ comando:
    
```powershell
Configuration ExampleConfiguration{
   
    Import-DSCResource -Module nx

}
```
2. Definir uma configuração e gerar o documento de configuração:

```powershell
Configuration ExampleConfiguration{
   
    Import-DscResource -Module nx
 
    Node  "linuxhost.contoso.com"{
    nxFile ExampleFile {

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

Documentos de configuração (ficheiros MOF) podem ser enviados para o computador Linux com o [início DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet. Para poder utilizar este cmdlet, juntamente com o [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx), ou [teste DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlets, remotamente para um computador com Linux, tem de utilizar um CIMSession. O [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet é utilizado para criar um CIMSession pelo computador Linux.

O código seguinte mostra como criar um CIMSession para DSC para Linux.

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName:"root" -Message:"Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl:$true -SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl:$true 
$Sess=New-CimSession -Credential:$credential -ComputerName:$Node -Port:5986 -Authentication:basic -SessionOption:$opt -OperationTimeoutSec:90 
```

> **Tenha em atenção**:
* Para o modo "Push", as credenciais de utilizador tem de ser o utilizador raiz no computador Linux.
* Ligações de SSL/TLS só são suportadas DSC para Linux, New-CimSession tem de ser utilizado com o parâmetro – UseSSL definido como $true.
* O certificado SSL utilizado pelo OMI (para DSC) está especificado no ficheiro: `/opt/omi/etc/omiserver.conf` com as propriedades: pemfile e ficheiro de chave.
Se este certificado não é considerado fidedigno pelo computador Windows que está a executar o [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet no, pode optar por ignorar a validação de certificado com as opções de CIMSession:`-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`

Execute o seguinte comando para enviar a configuração de DSC ao nó de Linux.

`Start-DscConfiguration -Path:"C:\temp" -CimSession:$Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a>Distribuir a configuração com um servidor de solicitação

Configurações podem ser distribuídas para um computador com Linux com um servidor de solicitação, tal como em computadores Windows. Para obter orientações sobre a utilização de um servidor de solicitação, consulte [Windows PowerShell pretendido Estado solicitação servidores de configuração](pullServer.md). Para obter informações adicionais e limitações relacionadas com a utilização de computadores com Linux com um servidor de solicitação, consulte as notas de versão para configuração de estado pretendido para Linux.

### <a name="working-with-configurations-locally"></a>Trabalhar com configurações localmente

DSC para Linux inclui scripts para trabalhar com a configuração do computador local do Linux. Estes scripts estão localizar no `/opt/microsoft/dsc/Scripts` e incluem o seguinte:
* GetDscConfiguration.py

 Devolve a configuração atual, aplicada ao computador. Semelhante para o cmdlet Get-DscConfiguration do cmdlet do Windows PowerShell.

`# sudo ./GetDscConfiguration.py`

* GetDscLocalConfigurationManager.py

 Devolve a configuração atual do meta-aplicada ao computador. Semelhante ao cmdlet [Get-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) cmdlet.

`# sudo ./GetDscLocalConfigurationManager.py`

* InstallModule.py

 Instala um módulo de recursos de DSC personalizado. Requer que o caminho para um ficheiro. zip que contém a biblioteca de partilhado do objeto de módulo e ficheiros MOF de esquema.

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

* RemoveModule.py

 Remove um módulo de recursos de DSC personalizado. Requer o nome do módulo a remover.

`# sudo ./RemoveModule.py cnx_Resource`

* StartDscLocalConfigurationManager.py 

 Aplica-se um ficheiro MOF de configuração para o computador. Semelhante para o [início DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet. Requer que o caminho para a configuração MOF a aplicar.

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

* SetDscLocalConfigurationManager.py

 Aplica-se um ficheiro MOF da configuração de metadados para o computador. Semelhante para o [conjunto DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx) cmdlet. Requer que o caminho para o MOF de configuração Meta para aplicar.

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a>Configuração de estado para ficheiros de registo do Linux de pretendido do PowerShell

Os seguintes ficheiros de registo são gerados para DSC para mensagens de Linux.

|Ficheiro de registo|Diretório|Descrição|
|---|---|---|
|omiserver.log|/var/OPT/OMI/log|Mensagens relacionadas com a operação do servidor OMI CIM.|
|DSC.log|/var/OPT/OMI/log|Mensagens relacionadas com a operação das operações de recursos do Gestor de configuração Local (MMC) e DSC.|

