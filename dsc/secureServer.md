---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Melhores práticas do servidor de solicitação
ms.openlocfilehash: d8d8667e2fc608e0c5948a0b5046bf92801b49db
ms.sourcegitcommit: ece1794c94be4880a2af5a2605ed4721593643b6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="pull-server-best-practices"></a>Melhores práticas do servidor de solicitação

>Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> O servidor de solicitação (funcionalidade do Windows *DSC serviço*) é um componente suportado do Windows Server no entanto, são não planos para oferecer novas funcionalidades ou capacidades. É recomendado para começar a transição geridos os clientes [Automation DSC do Azure](/azure/automation/automation-dsc-getting-started) (inclui funcionalidades além do servidor de solicitação no Windows Server) ou uma das soluções de Comunidade listados [aqui](pullserver.md#community-solutions-for-pull-service).

Resumo: Este documento destina-se para incluir o processo e extensibilidade para ajudá-lo engenheiros estiver a preparar para a solução. Detalhes devem fornecer melhores práticas, conforme identificado por clientes e, em seguida, validar pela equipa do produto para garantir que as recomendações são direcionadas para o futura e considerados estáveis.

| |Informações do documento|
|:---|:---|
autor | Miguel Greene
Revisores | Bernardo Gelens, Ravikanth Chaganti, Aleksandar Nikolic
Publicado | Abril de 2015

## <a name="abstract"></a>Abstrato

Este documento foi concebido para fornecer orientações oficial para qualquer pessoa planear uma implementação de servidor de solicitação de configuração de estado pretendido do Windows PowerShell. Um servidor de solicitação é um serviço simple que deve demorar apenas minutos a implementar. Embora este documento irá oferecer técnica orientações procedimentos que podem ser utilizada numa implementação, o valor deste documento é como uma referência para as melhores práticas e que tenha em consideração antes de implementar.
Os leitores devem ter básica familiaridade com DSC e termos utilizados para descrever os componentes que estão incluídas na implementação de DSC. Para obter mais informações, consulte o [Windows PowerShell Desired Configuration descrição geral do estado](https://technet.microsoft.com/library/dn249912.aspx) tópico.
Como é esperado DSC evoluir em cadência de nuvem, a tecnologia subjacente, incluindo o servidor de solicitação também é esperada para evoluem e introduzem novas capacidades. Este documento inclui uma tabela de versão no anexo que fornece as referências para futuras soluções procura a encorajar forward-looking estruturas e referências a versões anteriores.

As duas secções principais deste documento:

 - Planear a configuração
 - Guia de instalação

### <a name="versions-of-the-windows-management-framework"></a>Versões do Windows Management Framework
As informações neste documento destina-se a aplicar ao Windows Management Framework 5.0. Enquanto o WMF 5.0 não é necessário para implementar e operar um servidor de solicitação, versão 5.0 é o objetivo deste documento.

### <a name="windows-powershell-desired-state-configuration"></a>Configuração do estado pretendido do Windows PowerShell
Pretendido a configuração de estado (DSC) é uma plataforma de gestão que permite que os dados de configuração de implementação e gestão utilizando uma sintaxe de setor com o nome de formato (Managed Object) para descrever o modelo CIM (Common Information). Um projeto de código aberto, abra o Management Infrastructure (OMI), existe ainda mais o desenvolvimento dessas normas entre plataformas, incluindo o Linux e os sistemas operativos de hardware de rede. Para obter mais informações, consulte o [página DMTF a associar ao especificações MOF](http://dmtf.org/standards/cim), e [OMI documentos e origem](https://collaboration.opengroup.org/omi/documents.php).

Windows PowerShell fornece um conjunto de extensões de idioma para configuração de estado pretendido que pode utilizar para criar e gerir configurações declarativas.

### <a name="pull-server-role"></a>Função de servidor de solicitação
Um servidor de solicitação fornece um serviço centralizado para armazenar as configurações que estarão acessíveis a nós de destino.

A função de servidor de solicitação pode ser implementada como uma instância de servidor Web ou uma partilha de ficheiros SMB. A capacidade de servidor web inclui uma interface de OData e, opcionalmente, pode incluir capacidades para nós de destino informar confirmação de êxito ou falha como configurações são aplicadas. Esta funcionalidade é útil em ambientes onde existe um grande número de nós de destino.
Depois de configurar um nó de destino (também referido como um cliente) para apontar para o servidor de solicitação a configuração mais recente os dados e quaisquer scripts necessários são transferidos e aplicadas. Isto pode acontecer como uma única implementação ou como uma tarefa novamente occurring que também faz com que o servidor de solicitação um recurso importante para a gestão de alterações à escala. Para obter mais informações, consulte [Windows PowerShell pretendido Estado solicitar a servidores de configuração](https://technet.microsoft.com/library/dn249913.aspx) e [Push e Pull modos de configuração](https://technet.microsoft.com/library/dn249913.aspx).

## <a name="configuration-planning"></a>Planear a configuração

Para qualquer implementação de software empresarial não há informações que podem ser recolhidas seguinte com antecedência para ajudar a planear para a arquitetura correta e para estar preparado para os passos necessários para concluir a implementação. As secções seguintes fornecem informações sobre como preparar e as ligações organizacionais que, provavelmente, serão necessário acontecer antecipadamente.

### <a name="software-requirements"></a>Requisitos de software

Implementação de um servidor de solicitação necessita da funcionalidade de DSC serviço do Windows Server. Esta funcionalidade foi introduzida no Windows Server 2012 e tiver sido atualizada através da Windows Management Framework (WMF) de versões em curso.

### <a name="software-downloads"></a>Transferências de software

Para além de instalar o conteúdo mais recente do Windows Update, existem dois transferências consideradas a melhor prática para implementar um servidor de solicitação do DSC: A versão mais recente do Windows Management Framework e um módulo de DSC para automatizar o aprovisionamento do servidor de solicitação.

### <a name="wmf"></a>WMF

Windows Server 2012 R2 inclui uma funcionalidade com o nome do serviço de DSC. A funcionalidade do serviço de DSC fornece a funcionalidade de servidor de solicitação, incluindo os binários que suportam o ponto final de OData.
WMF está incluído no Windows Server e é atualizado uma cadência seja ágil entre versões do Windows Server. [Novas versões do WMF 5.0](http://aka.ms/wmf5latest) podem incluir atualizações para a funcionalidade serviço de DSC. Por este motivo, é melhor prática para transferir a versão mais recente do WMF e para rever as notas de versão para determinar se a versão inclui uma atualização para a funcionalidade de serviço do DSC. Também deve consultar a secção das notas de versão que indica se o estado da estrutura de um cenário de atualização ou está listado como estável ou experimental.
Para permitir um ciclo de lançamento seja ágil funcionalidades individuais podem ser declaradas estáveis, que indica que a funcionalidade, está pronto para ser utilizada num ambiente de produção, mesmo enquanto WMF é lançado em pré-visualização.
Outras funcionalidades que tenham sido atualizadas historicamente por versões WMF (consulte as notas de versão do WMF para obter mais detalhes):

 - Windows PowerShell Windows PowerShell, integrado Scripting
 - Serviços de ambiente (ISE) Web do Windows PowerShell (gestão OData
 - Extensão IIS) Windows PowerShell estada configuração pretendido (DSC)
 - Windows (WinRM) de gestão remota Windows Management Instrumentation (WMI)

### <a name="dsc-resource"></a>Recursos de DSC

Uma implementação de servidor de solicitação pode ser simplificada pelo aprovisionamento do serviço através de um script de configuração de DSC. Este documento inclui scripts de configuração que podem ser utilizados para implementar um nó de servidor preparada de produção. Para utilizar os scripts de configuração, um módulo de DSC esteja necessário que não incluídos no Windows Server. O nome do módulo necessário é **xPSDesiredStateConfiguration**, que inclui os recursos de DSC **xDscWebService**. O módulo de xPSDesiredStateConfiguration pode ser transferido [aqui](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).

Utilize o **Install-Module** cmdlet a partir de **PowerShellGet** módulo.

```powershell
Install-Module xPSDesiredStateConfiguration
```

O **PowerShellGet** módulo irá transferir o módulo para:

`C:\Program Files\Windows PowerShell\Modules`

Tarefas de planeamento|
---|
Tem acesso para os ficheiros de instalação para o Windows Server 2012 R2?|
O ambiente de implementação terá acesso à Internet para transferir o WMF e o módulo da galeria do online?|
Como irá instalar as atualizações de segurança mais recentes depois de instalar o sistema operativo?|
O ambiente terá acesso à Internet para obter as atualizações ou terão um servidor local do Windows Server Update Services (WSUS)?|
Tem acesso aos ficheiros de instalação do Windows Server que já incluem atualizações através de injeção offline?|

### <a name="hardware-requirements"></a>Requisitos de hardware

Implementações de servidor de solicitação são suportadas em servidores físicos e virtuais. Os requisitos de dimensionamento para o servidor de solicitação alinharem com os requisitos do Windows Server 2012 R2.

Da CPU: processador de 64 bits GHz 1,4 memória: 512 MB de espaço em disco: 32 GB de rede: adaptador Ethernet Gigabit

Tarefas de planeamento|
---|
Irá implementar em hardware físico ou numa plataforma de Virtualização?|
O que é o processo para pedir um novo servidor para o seu ambiente de destino?|
O que é o tempo de resposta médio mais rápida para um servidor fique disponível?|
O servidor de tamanho irá solicitar?|

### <a name="accounts"></a>Contas

Não existem não requisitos de conta de serviço para implementar uma instância de servidor de solicitação.
No entanto, existem cenários onde o Web site foi executada no contexto de uma conta de utilizador local.
Por exemplo, se for necessário para acesso de armazenamento de partilha de conteúdo do Web site e o Windows Server ou o dispositivo que aloja a partilha de armazenamento não estão associados a um domínio.

### <a name="dns-records"></a>Registos DNS

É necessário um nome de servidor para utilizar quando configurar clientes para trabalhar com um ambiente de servidor de solicitação.
Em ambientes de teste, normalmente é utilizado o nome de anfitrião do servidor ou o endereço IP para o servidor pode ser utilizado se a resolução do nome DNS não está disponível.
Em ambientes de produção ou num ambiente de laboratório que se destina a representar uma implementação de produção, a melhor prática é criar um registo CNAME no DNS.

Um CNAME DNS permite-lhe criar um alias referir-se para o anfitrião (A) registo.
A intenção de registo de nome adicionais é aumentar flexibilidade deve uma alteração necessário no futuro.
Um CNAME pode ajudar a isolar a configuração do cliente para que as alterações para o ambiente de servidor, tais como substituir um servidor de solicitação ou adicionar servidores de solicitação adicionais, não irão exigir uma alteração à configuração de cliente correspondente.

Ao escolher um nome para o registo DNS, mantenha a arquitetura de solução em mente.
Se utilizar o balanceamento de carga, o certificado utilizado para proteger o tráfego através de HTTPS terá de partilhar o mesmo nome que o registo DNS.

Cenário |Melhores práticas
:---|:---
Ambiente de testes |Reproduza o ambiente de produção planeada, se possível. Um nome de anfitrião do servidor é adequado para configurações simples. Se o DNS não estiver disponível, um endereço IP pode ser utilizado in lieu of um nome de anfitrião.|
Implementação de nó único |Crie um registo CNAME no DNS que aponta para o nome de anfitrião do servidor.|

Para obter mais informações, consulte [configurar o DNS Round Robin no Windows Server](https://technet.microsoft.com/en-us/library/cc787484(v=ws.10).aspx).

Tarefas de planeamento|
---|
Saber quem entrar em contacto com registos DNS criados e alterados?|
O que é a resposta mais rápida média de um pedido para um registo DNS?|
Precisa de pedir estático registos de nome de anfitrião (A) para servidores?|
O que irá solicitar como um CNAME?|
Se for necessário, tipo de solução de balanceamento de carga que irá utilizar? (consulte a secção intitulada balanceamento de carga para obter detalhes)|

### <a name="public-key-infrastructure"></a>Infraestrutura de chaves públicas

A maioria das organizações hoje necessitam que o tráfego de rede, especialmente tráfego que inclua esses dados confidenciais, como servidores estiverem configurados, deve ser validado e/ou encriptado durante a trânsito.
Embora seja possível implementar um servidor de solicitação utilizando HTTP que facilita a pedidos de cliente no apague o texto, é uma melhor prática para o tráfego seguro através de HTTPS. O serviço pode ser configurado para utilizar HTTPS utilizando um conjunto de parâmetros no recurso DSC **xPSDesiredStateConfiguration**.

Os requisitos de certificados para proteger o tráfego HTTPS para o servidor de solicitação não são diferentes proteger outro HTTPS web site. O **servidor Web** modelo nos serviços de certificados de servidor Windows satisfaça as capacidades necessárias.

Tarefas de planeamento|
---|
Se os pedidos de certificado não são automatizados, que vai precisar de contactar a pedidos de um certificado?|
O que é a resposta mais rápida média do pedido?|
Como será o ficheiro de certificado transferido para si?|
Como será a chave privada de certificado transferida para si?|
Qual é a hora de expiração predefinido?|
Ter settled num nome de DNS para o ambiente de servidor de solicitação, o que pode utilizar para o nome do certificado?|

### <a name="choosing-an-architecture"></a>Escolher uma arquitetura

Um servidor de solicitação pode ser implementado utilizando um serviço de web alojado no IIS ou uma partilha de ficheiros SMB. Na maioria das situações, a opção de serviço web irá fornecer maior flexibilidade. Não é invulgar para tráfego HTTPS para percorrer os limites de rede, enquanto que o tráfego SMB é, muitas vezes, filtrado ou bloqueado entre redes. O serviço web também oferece a opção para incluir um servidor de conformidade ou Web Gestor Reporting Services (ambos os tópicos para ser resolvido numa versão futura deste documento) que fornecem um mecanismo para os clientes para comunicar o estado para um servidor de visibilidade centralizada.
O SMB fornece uma opção para ambientes onde a política dita que não deve ser utilizado de um servidor web e outros requisitos ambientais que tornam uma função de servidor web indesejável.
Em ambos os casos, lembre-se avaliar os requisitos para assinatura e encriptação de tráfego. HTTPS, a assinatura SMB e políticas IPSEC são todas as opções de vale a considerar.

#### <a name="load-balancing"></a>Balanceamento de carga
Os clientes a interagir com o serviço web efetuar um pedido com indicação de que é devolvido numa única resposta. Não existem pedidos sequenciais são necessários, pelo que não é necessário para a plataforma para garantir sessões são mantidas num único servidor em qualquer ponto no tempo de balanceamento de carga.

Tarefas de planeamento|
---|
Que solução será utilizada para balanceamento de carga tráfego entre servidores?|
Se utilizar um balanceador de carga de hardware, que irá demorar um pedido para adicionar uma nova configuração para o dispositivo?|
O que é a resposta mais rápida para um pedido para configurar uma nova carga média com balanceamento de serviço web?|
As informações que será necessárias para o pedido?|
Vai precisar de pedir um IP adicional ou a equipa responsável pelo balanceamento de carga processará que?|
Pretende que os registos DNS necessários, e este terão pela equipa responsável pela configuração de solução de balanceamento de carga?|
A solução de balanceamento de carga requer que a PKI ser processados pelo dispositivo ou pode-o balanceamento de carga tráfego HTTPS, desde que existem não requisitos de sessão?|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a>Configurações e os módulos no servidor de solicitação de teste

Como parte do planeamento de configuração, terá de pensar sobre o DSC módulos e configurações serão alojadas pelo servidor de solicitação. Para efeitos de planeamento da configuração é importante ter uma compreensão básica sobre como preparar e implementar conteúdo num servidor de solicitação.

No futuro, esta secção será expandida e incluída no guia de operações do servidor de solicitação do DSC.  O guia de abordar o processo de diário para a gestão de módulos e configurações ao longo do tempo com a automatização.

#### <a name="dsc-modules"></a>Módulos de DSC
Clientes que solicitam uma configuração terá dos módulos necessários do DSC. É uma funcionalidade do servidor de solicitação automatizar a distribuição a pedido dos módulos de DSC nos clientes. Se estiver a implementar um servidor de solicitação pela primeira vez, talvez como um laboratório ou de prova de conceito, provavelmente pretender dependem de módulos de DSC que estão disponíveis de repositórios públicos, como a galeria do PowerShell ou repositórios do PowerShell.org GitHub para módulos de DSC .

É essencial Lembre-se de que, mesmo para origens de online fidedignas, tais como a galeria do PowerShell, qualquer módulo que é transferido a partir de um repositório público deve ser revisto por alguém com experiência com o PowerShell e o conhecimento do ambiente onde os módulos será utilizar antes a ser utilizado em produção. Ao concluir esta tarefa é uma boa altura para verificar a existência de quaisquer payload adicional no módulo que possa ser removido como scripts de exemplo e a documentação. Isto irá reduzir a largura de banda de rede por cliente aquando do primeiro pedido, quando os módulos serão transferidos através da rede do servidor ao cliente.

Cada módulo tem de ser compactado num formato específico, um ficheiro ZIP com o nome ModuleName_Version.zip que contém o payload de módulo. Depois do ficheiro é copiado para o servidor tem de ser criado um ficheiro de soma de verificação. Quando os clientes ligam ao servidor, a soma de verificação é utilizada para verificar que o conteúdo do módulo do DSC não mudou desde que foi publicada.

```powershell
New-DscCheckSum -ConfigurationPath .\ -OutPath .\
```

Tarefas de planeamento|
---|
Se estiver a planear um ambiente de laboratório ou de teste que cenários são fundamentais para validar?|
Existem módulos publicamente disponíveis que contêm os recursos para cobrir tudo o que necessita ou terá de criar os seus próprios recursos?|
O ambiente terão acesso à Internet para obter os módulos públicos?|
Quem será o responsável pela revisão módulos de DSC?|
Se estiver a planear um ambiente de produção que irá utilizar como um repositório local para armazenar os módulos de DSC?|
Um agrupamento central aceitará módulos de DSC das equipas de aplicação? O que será o processo?|
Será automatizar empacotamento, copiar e criar uma soma de verificação para módulos de DSC prontos para produção ao servidor, do seu repositório de origem?|
A equipa será responsável por gerir a plataforma de automatização?|

#### <a name="dsc-configurations"></a>Configurações de DSC

O objetivo de um servidor de solicitação consiste em fornecer um mecanismo centralizado para distribuir as configurações de DSC em nós de cliente. As configurações são armazenadas no servidor como documentos MOF.
Cada documento será nomeado com um GUID exclusivo. Quando os clientes são configurados para estabelecer ligação com um servidor de solicitação, também são fornecidos o GUID para a configuração deve pedir. Este sistema de referência configurações pelo GUID garantias de exclusividade global e é flexível do que uma configuração pode ser aplicada com granularidade por nó, ou como uma configuração de função que abranja vários servidores que devem ter configurações idênticas.

#### <a name="guids"></a>GUIDs

Planear a configuração GUIDs é, atenção adicional quando pensar através de uma implementação de servidor de solicitação. Não é necessário para saber como processar GUIDs específico e o processo é provável que seja exclusivo para cada ambiente. O processo pode variar desde simples para complexa: um ficheiro CSV centralmente armazenado, uma tabela SQL simple, uma CMDB ou uma solução complexa que requerem integração com outra solução de software ou a ferramenta. Existem duas abordagens gerais:

 - **Atribuir GUIDs por servidor** — fornece uma medida de garantia que cada configuração do servidor é controlada individualmente. Isto fornece um nível de precisão à volta de atualizações e pode funcionar bem em ambientes com alguns servidores.
 - **Atribuir GUIDs por função de servidor** — todos os servidores que executam a mesma função, tais como servidores web, utilizam o mesmo GUID para fazer referência os dados de configuração necessárias.  Lembre-se de que se o número de servidores de partilhar o mesmo GUID, todos eles seriam atualizados em simultâneo quando a configuração for alterada.

O GUID é algo que devem ser consideradas dados confidenciais porque pode ser aproveitado por alguém com intenções maliciosas para obterem intelligence sobre como os servidores são implementados e configurados no seu ambiente. Para obter mais informações, consulte [em segurança alocar GUIDs no PowerShell pretendido estado configuração solicitar modo](http://blogs.msdn.com/b/powershell/archive/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode.aspx).

Tarefas de planeamento|
---|
Quem será o responsável pela cópia configurações para a pasta de servidor de solicitação quando estas estão prontas?|
Se as configurações são criadas por uma equipa de aplicação, o que o processo será entregam-las?|
Tirar partido um repositório para armazenar as configurações que estes são criados, entre equipas?|
Será automatizar o processo de copiar as configurações para o servidor e criar uma soma de verificação quando estas estão prontas?|
Como irá mapear GUIDs para servidores ou funções e isto armazenar?|
O que irá utilizar como um processo para configurar computadores cliente e como serão-lo a integrar com o processo para criar e armazenar os GUIDs de configuração?|

## <a name="installation-guide"></a>Guia de instalação

*Scripts indicados neste documento são exemplos estáveis. Reveja sempre scripts cuidadosamente antes de executá-los num ambiente de produção.*

### <a name="prerequisites"></a>Pré-requisitos

Para verificar a versão do PowerShell no seu servidor, utilize o seguinte comando.

```powershell
$PSVersionTable.PSVersion
```

Se for possível, atualize para a versão mais recente do Windows Management Framework.
Em seguida, transferir o `xPsDesiredStateConfiguration` módulo com o seguinte comando.


```powershell
Install-Module xPSDesiredStateConfiguration
```

O comando irá perguntar-sua aprovação antes de transferir o módulo.

### <a name="installation-and-configuration-scripts"></a>Scripts de instalação e configuração
-

O melhor método para implementar um servidor de solicitação do DSC consiste em utilizar um script de configuração de DSC. Este documento apresenta scripts, incluindo as definições básicas que teria de configurar apenas o serviço web do DSC e as definições que teria de configurar um serviço de web de DSC incluindo do Windows Server ponto-a-ponto avançadas.

Nota: Atualmente o `xPSDesiredStateConfiguation` módulo DSC requer que o servidor para ser a região EN-US.

### <a name="basic-configuration-for-windows-server-2012"></a>Configuração básica para o Windows Server 2012
-------------------------------------------
```powershell
# This is a very basic Configuration to deploy a pull server instance in a lab environment on Windows Server 2012.

Configuration PullServer {
Import-DscResource -ModuleName xPSDesiredStateConfiguration

        # Load the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
          Ensure = 'Present'
          Name = 'DSC-Service'
        }

        # Use the DSC Resource to simplify deployment of the web service
        xDSCWebService PSDSCPullServer
        {
          Ensure = 'Present'
          EndpointName = 'PSDSCPullServer'
          Port = 8080
          PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
          CertificateThumbPrint = 'AllowUnencryptedTraffic'
          ModulePath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
          ConfigurationPath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
          State = 'Started'
          DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
}
PullServer -OutputPath 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'
```

### <a name="advanced-configuration-for-windows-server-2012-r2"></a>Configuração avançada para o Windows Server 2012 R2

```powershell
# This is an advanced Configuration example for Pull Server production deployments on Windows Server 2012 R2.
# Many of the features demonstrated are optional and provided to demonstrate how to adapt the Configuration for multiple scenarios
# Select the needed resources based on the requirements for each environment.
# Optional scenarios include:
#      * Reduce footprint to Server Core
#      * Rename server and join domain
#      * Switch from SSL to TLS for HTTPS
#      * Automatically load certificate from Certificate Authority
#      * Locate Modules and Configuration data on remote SMB share
#      * Manage state of default websites in IIS

param (
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [System.String] $ServerName,
        [System.String] $DomainName,
        [System.String] $CARootName,
        [System.String] $CAServerFQDN,
        [System.String] $CertSubject,
        [System.String] $SMBShare,
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $Credential
    )

Configuration PullServer {
    Import-DscResource -ModuleName xPSDesiredStateConfiguration, xWebAdministration, xCertificate, xComputerManagement
    Node localhost
    {

        # Configure the server to automatically corret configuration drift including reboots if needed.
        LocalConfigurationManager
        {
            ConfigurationMode = 'ApplyAndAutoCorrect'
            RebootNodeifNeeded = $node.RebootNodeifNeeded
            CertificateId = $node.Thumbprint
        }

        # Remove all GUI interfaces so the server has minimum running footprint.
        WindowsFeature ServerCore
        {
            Ensure = 'Absent'
            Name = 'User-Interfaces-Infra'
        }

        # Set the server name and if needed, join a domain. If not joining a domain, remove the DomainName parameter.
        xComputer DomainJoin
        {
            Name = $Node.ServerName
            DomainName = $Node.DomainName
            Credential = $Node.Credential
        }

        # The next series of settings disable SSL and enable TLS, for environments where that is required by policy.
        Registry TLS1_2ServerEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }
        Registry TLS1_2ServerDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }
        Registry TLS1_2ClientEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }
        Registry TLS1_2ClientDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }
        Registry SSL2ServerDisabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\SSL 2.0\Server'
            ValueName = 'Enabled'
            ValueData = 0
            ValueType = 'Dword'
        }

        # Install the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
            Ensure = 'Present'
            Name = 'DSC-Service'
        }

        # If using a certificate from a local Active Directory Enterprise Root Certificate Authority, complete a request and install the certificate
        xCertReq SSLCert
        {
            CARootName = $Node.CARootName
            CAServerFQDN = $Node.CAServerFQDN
            Subject = $Node.CertSubject
            AutoRenew = $Node.AutoRenew
            Credential = $Node.Credential
        }

        # Use the DSC resource to simplify deployment of the web service.  You might also consider modifying the default port, possibly leveraging port 443 in environments where that is enforced as a standard.
        xDSCWebService PSDSCPullServer
        {
            Ensure = 'Present'
            EndpointName = 'PSDSCPullServer'
            Port = 8080
            PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
            CertificateThumbPrint = 'CertificateSubject'
            CertificateSubject = $Node.CertSubject
            ModulePath = "$($Node.SMBShare)\DscService\Modules"
            ConfigurationPath = "$($Node.SMBShare)\DscService\Configuration"
            State = 'Started'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }

        # Validate web config file contains current DB settings
        xWebConfigKeyValue CorrectDBProvider
        {
            ConfigSection = 'AppSettings'
            Key = 'dbprovider'
            Value = 'System.Data.OleDb'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }
        xWebConfigKeyValue CorrectDBConnectionStr
        {
            ConfigSection = 'AppSettings'
            Key = 'dbconnectionstr'
            Value = 'Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Program Files\WindowsPowerShell\DscService\Devices.mdb;'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }

        # Stop the default website
        xWebsite StopDefaultSite
        {
            Ensure = 'Present'
            Name = 'Default Web Site'
            State = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
    }
}
$configData = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            ServerName = $ServerName
            DomainName = $DomainName
            CARootName = $CARootName
            CAServerFQDN = $CAServerFQDN
            CertSubject = $CertSubject
            AutoRenew = $true
            SMBShare = $SMBShare
            Credential = $Credential
            RebootNodeifNeeded = $true
            CertificateFile = 'c:\PullServerConfig\Cert.cer'
            Thumbprint = 'B9A39921918B466EB1ADF2509E00F5DECB2EFDA9'
            }
        )
    }
PullServer -ConfigurationData $configData -OutputPath 'C:\PullServerConfig\'
Set-DscLocalConfigurationManager -ComputerName localhost -Path 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'

# .\Script.ps1 -ServerName web1 -domainname 'test.pha' -carootname 'test-dc01-ca' -caserverfqdn 'dc01.test.pha' -certsubject 'CN=service.test.pha' -smbshare '\\sofs1.test.pha\share'
```


### <a name="verify-pull-server-functionality"></a>Verificar a funcionalidade de servidor de solicitação

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](invoke-webrequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}
Verify-DSCPullServer 'INSERT SERVER FQDN'

Expected Result:
Action
Module
StatusReport
Node
```

### <a name="configure-clients"></a>Configurar os clientes

```powershell
Configuration PullClient {
    param(
    $ID,
    $Server
    )
        LocalConfigurationManager
                {
                    ConfigurationID = $ID;
                    RefreshMode = 'PULL';
                    DownloadManagerName = 'WebDownloadManager';
                    RebootNodeIfNeeded = $true;
                    RefreshFrequencyMins = 30;
                    ConfigurationModeFrequencyMins = 15;
                    ConfigurationMode = 'ApplyAndAutoCorrect';
                    DownloadManagerCustomData = @{ServerUrl = "http://"+$Server+":8080/PSDSCPullServer.svc"; AllowUnsecureConnection = $true}
                }
}
PullClient -ID 'INSERTGUID' -Server 'INSERTSERVER' -Output 'C:\DSCConfig\'
Set-DscLocalConfigurationManager -ComputerName 'Localhost' -Path 'C:\DSCConfig\' -Verbose
```


## <a name="additional-references-snippets-and-examples"></a>Referências adicionais, fragmentos e exemplos

Este exemplo mostra como iniciar manualmente uma ligação de cliente (requer WMF5) para fins de teste.

```powershell
Update-DSCConfiguration –Wait -Verbose
```

O [adicionar DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet é utilizado para adicionar um tipo de registo CNAME para uma zona DNS.

A função de PowerShell para [criar uma soma de verificação e publicar o DSC MOF para o servidor de solicitação do SMB](http://bit.ly/1E46BhI) gera automaticamente a soma de verificação necessária e, em seguida, copia a configuração de MOF e de ficheiros de soma de verificação para o servidor de solicitação SMB.

## <a name="appendix---understanding-odata-service-data-file-types"></a>Apêndice - compreender ODATA tipos de ficheiros de dados do serviço

Um ficheiro de dados é armazenado para criar informações durante a implementação de um servidor de solicitação, que inclui o serviço web de OData. O tipo do ficheiro depende do sistema operativo, conforme descrito abaixo.

 - **Windows Server 2012** o tipo de ficheiro será sempre. mdb
 - **Windows Server 2012 R2** o tipo de ficheiro será predefinido para. edb, a menos que um. mdb é especificado na configuração

No [avançadas de script de exemplo](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) para instalar um servidor de solicitação, também irá encontrar um exemplo de como controlar automaticamente as definições do ficheiro Web. config para evitar qualquer probabilidade de erro foi causado por tipo de ficheiro.