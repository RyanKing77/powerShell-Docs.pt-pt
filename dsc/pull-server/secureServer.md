---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Melhores práticas do servidor de solicitação
ms.openlocfilehash: fe483a487f85f2e4edb0928fccfe98746ae11231
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079205"
---
# <a name="pull-server-best-practices"></a>Melhores práticas do servidor de solicitação

Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> O servidor de solicitação (recurso do Windows *DSC-serviço*) é um componente suportado do Windows Server no entanto, não existem planos para oferecer novas funcionalidades ou capacidades. É recomendado para começar a fazer a transição geridos os clientes [DSC de automatização do Azure](/azure/automation/automation-dsc-getting-started) (inclui funcionalidades além do servidor de solicitação de mensagens em fila no Windows Server) ou uma das soluções da Comunidade listados [aqui](pullserver.md#community-solutions-for-pull-service).

Resumo: Este documento destina-se para incluir o processo e extensibilidade para ajudar os engenheiros que estiver a preparar para a solução. Detalhes devem fornecer melhores práticas, conforme identificado por parte dos clientes e, em seguida, validada pela equipe do produto para garantir que as recomendações são voltado para o futuro e considerado estáveis.

| |Informações do documento|
|:---|:---|
Autor | Michael Greene
Revisores | Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic
Publicado | Abril de 2015

## <a name="abstract"></a>Abstrato

Este documento destina-se para fornecer orientações oficial para qualquer pessoa a planear uma implementação de servidor de solicitação do Windows PowerShell Desired State Configuration. Um servidor de solicitação é um serviço simple que deve demorar apenas alguns minutos a implementar. Embora este documento oferece orientações técnicas de procedimentos que podem ser utilizada numa implementação, o valor deste documento é como uma referência para as práticas recomendadas e o que pensar antes de implementar.
Os leitores devem ter familiaridade básica com DSC e os termos utilizados para descrever os componentes que estão incluídas numa implantação de DSC. Para obter mais informações, consulte a [Windows PowerShell Desired State Configuration descrição geral](/powershell/dsc/overview) tópico.
Como o DSC é esperada a evoluir em cadência de cloud, a tecnologia subjacente, incluindo o servidor de solicitação também se espera que a evoluir e introduzir novas capacidades. Este documento inclui uma tabela de versão no apêndice que fornece referências para versões anteriores e referências a soluções de aparência futuras para incentivar a designs futuro.

As duas secções principais deste documento:

- Planejamento da configuração
- Guia de instalação

### <a name="versions-of-the-windows-management-framework"></a>Versões do Windows Management Framework

As informações neste documento destina-se aplicar ao Windows Management Framework 5.0. Embora o WMF 5.0 não seja necessário para implantar e operar um servidor de solicitação, a versão 5.0 é o foco deste documento.

### <a name="windows-powershell-desired-state-configuration"></a>Windows PowerShell Desired State Configuration

Desired State Configuration (DSC) é uma plataforma de gestão que permite implementar e gerir dados de configuração utilizando uma sintaxe de setor com o nome de formato MOF (Managed Object Format) para descrever o modelo CIM (Common Information). Existe um projeto de código-fonte aberto, o Open Management Infrastructure (OMI), sistemas de operativos de hardware de rede e ainda mais o desenvolvimento desses padrões entre plataformas, incluindo o Linux. Para obter mais informações, consulte a [página DMTF vinculando a especificações de MOF](https://www.dmtf.org/standards/cim), e [OMI documentos e origem](https://collaboration.opengroup.org/omi/documents.php).

Windows PowerShell fornece um conjunto de extensões de linguagem para Desired State Configuration, que pode utilizar para criar e gerir configurações declarativas.

### <a name="pull-server-role"></a>Função de servidor de solicitação

Um servidor de solicitação fornece um serviço centralizado para armazenar as configurações que estarão acessíveis a nós de destino.

A função de servidor de solicitação pode ser implementada como uma instância de servidor Web ou uma partilha de ficheiros SMB. A capacidade de servidor web inclui uma interface de OData e, opcionalmente, pode incluir capacidades para nós de destino relatar confirmação de êxito ou falha conforme as configurações são aplicadas. Essa funcionalidade é útil em ambientes em que há um grande número de nós de destino.
Depois de configurar um nó de destino (também referido como um cliente) para apontar para o servidor de solicitação, a configuração mais recente os dados e quaisquer scripts necessários são transferidos e aplicados. Isto pode acontecer como uma implementação de uso individual ou como uma tarefa que novamente que também faz com que o servidor de solicitação um ativo importante para o gerenciamento de alterações em escala. Para obter mais informações, consulte [Windows PowerShell Desired State Configuration extrair servidores](/powershell/dsc/pullServer) e

[Enviar e extrair os modos de configuração](/powershell/dsc/pullServer).

## <a name="configuration-planning"></a>Planejamento da configuração

Para qualquer implementação de software empresarial há informações que podem ser coletadas com antecedência para ajudar a planear para a arquitetura correta e estar preparado para os passos necessários para concluir a implementação. As secções seguintes fornecem informações sobre como preparar e as ligações organizacionais que provavelmente terá de acontecer com antecedência.

### <a name="software-requirements"></a>Requisitos de software

Implementação de um servidor de solicitação requer a funcionalidade de serviço de DSC do Windows Server. Esta funcionalidade foi introduzida no Windows Server 2012 e tiver sido atualizada por meio de versões em curso do Windows Management Framework (WMF).

### <a name="software-downloads"></a>Downloads de software

Para além de instalar o conteúdo mais recente do Windows Update, existem dois downloads consideradas uma prática recomendada para implementar um servidor de solicitação de DSC: A versão mais recente do Windows Management Framework e como um módulo de DSC para automatizar o provisionamento do servidor de solicitação.

### <a name="wmf"></a>WMF

Windows Server 2012 R2 inclui um recurso com o nome do serviço de DSC. O recurso de DSC serviço fornece a funcionalidade de servidor de solicitação, incluindo os binários que suportam o ponto final de OData.
WMF está incluído no Windows Server e é atualizado a uma cadência agile entre as versões do Windows Server. [Novas versões do WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=54616) podem incluir atualizações para a funcionalidade serviço de DSC. Por esse motivo, é uma prática recomendada para transferir a versão mais recente do WMF e para rever as notas de versão para determinar se a versão inclui uma atualização para o recurso de serviço do DSC. Também deve consultar a secção das notas de versão que indica se o estado de design para uma atualização ou cenário está listado como estável ou experimentais.
Para permitir um ciclo de lançamento ágil, funcionalidades individuais podem ser declaradas estáveis, que indica que o recurso está pronta para ser utilizada num ambiente de produção, mesmo quando o WMF é lançado em pré-visualização.
Outros recursos que tenham sido atualizados historicamente por versões do WMF (consulte as notas de versão do WMF para obter mais detalhes):

- Windows PowerShell de Windows PowerShell de script integrado
- Serviços da Web de PowerShell Windows Environment (ISE) (gestão de OData
- Extensão do IIS) Windows PowerShell Desired State Configuration (DSC)
- Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)

### <a name="dsc-resource"></a>Recursos de DSC

A implementação de um servidor de solicitação pode ser simplificada ao aprovisionar o serviço usando um script de configuração de DSC. Este documento inclui scripts de configuração que podem ser utilizados para implementar um nó de servidor pronto de produção. Para utilizar os scripts de configuração, um módulo de DSC é necessário ou seja não incluídos no Windows Server. É o nome do módulo de necessários **xPSDesiredStateConfiguration**, que inclui o recurso de DSC **xDscWebService**. O módulo de xPSDesiredStateConfiguration pode ser transferido [aqui](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).

Utilize o `Install-Module` cmdlet a partir de **PowerShellGet** módulo.

```powershell
Install-Module xPSDesiredStateConfiguration
```

O **PowerShellGet** módulo irá transferir o módulo para:

`C:\Program Files\Windows PowerShell\Modules`

Tarefas de planeamento|
---|
Tem acesso para os ficheiros de instalação para Windows Server 2012 R2?|
O ambiente de implantação terão acesso à Internet para transferir WMF e o módulo a partir da Galeria online?|
Como instalar as atualizações de segurança mais recentes depois de instalar o sistema operativo?|
O ambiente terão acesso à Internet para obter atualizações ou terão um servidor local do Windows Server Update Services (WSUS)?|
Tem acesso aos ficheiros de instalação do Windows Server que já incluem atualizações por meio de injeção offline?|

### <a name="hardware-requirements"></a>Requisitos de hardware

Implementações de servidor de solicitação são suportadas em servidores físicos e virtuais. Os requisitos de dimensionamento do servidor de solicitação se alinham com os requisitos para o Windows Server 2012 R2.

CPU: 1,4 processador de bits a GHz 64 memória: Espaço em disco de 512 MB: Rede de 32 GB: Adaptador Ethernet Gigabit

Tarefas de planeamento|
---|
Irá implementar em hardware físico ou numa plataforma de Virtualização?|
O que é o processo para pedir um novo servidor para o seu ambiente de destino?|
O que é o tempo de resposta médio para um servidor para se tornar disponível?|
O que servidor de tamanho irá pedir?|

### <a name="accounts"></a>Contas

Não existem não requisitos de conta de serviço para implementar uma instância de servidor de solicitação.
No entanto, existem cenários onde o Web site pode ser executado em contexto de uma conta de utilizador local.
Por exemplo, se houver a necessidade de acesso à partilha de um armazenamento para o conteúdo do Web site e o Windows Server ou o dispositivo que aloja a partilha de armazenamento não estão associados a um domínio.

### <a name="dns-records"></a>Registos DNS

Terá um nome de servidor a utilizar quando configurar clientes para trabalhar com um ambiente de servidor de solicitação.
Em ambientes de teste, normalmente, é utilizado o nome de anfitrião do servidor ou o endereço IP para o servidor pode ser utilizado se a resolução de nomes DNS não está disponível.
Em ambientes de produção ou num ambiente de laboratório que se destina-se para representar uma implementação de produção, a prática recomendada é criar um registo CNAME no DNS.

Um CNAME DNS permite-lhe criar um alias para fazer referência ao seu host (A) registo.
A intenção de registo de nome adicionais é aumentar a flexibilidade devem uma ser necessárias alterações no futuro.
Um CNAME pode ajudar a isolar a configuração do cliente para que as alterações ao ambiente do servidor, como substituir um servidor de solicitação ou adicionar servidores de solicitação adicionais, não precisará de uma alteração correspondente para a configuração do cliente.

Ao escolher um nome para o registo DNS, manter a arquitetura da solução em mente.
Se utilizar o balanceamento de carga, o certificado utilizado para proteger o tráfego através de HTTPS precisam de partilhar o mesmo nome que o registo DNS.

Cenário |Melhor prática
:---|:---
Ambiente de teste |Reproduza o ambiente de produção planeada, se possível. Um nome de anfitrião do servidor é adequada para configurações simples. Se o DNS não estiver disponível, um endereço IP pode ser utilizado em lugar de um nome de anfitrião.|
Implementação de nó único |Crie um registo CNAME no DNS que aponta para o nome de anfitrião do servidor.|

Para obter mais informações, consulte [configurar o DNS Round Robin no Windows Server](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)).

Tarefas de planeamento|
---|
Sabe quem entrar em contato para que os registos DNS criados e alterados?|
O que é a resposta média para um pedido para um registo DNS?|
Precisa pedir os registros de nome de anfitrião (A) estáticos para os servidores?|
O que irá pedir como um CNAME?|
Se for necessário, o tipo de solução de balanceamento de carga que utilizará? (consulte a secção intitulada o balanceamento de carga para obter detalhes)|

### <a name="public-key-infrastructure"></a>Infraestrutura de chaves públicas

A maioria das organizações de hoje exigem que o tráfego de rede, especialmente o tráfego que inclua esses dados confidenciais, como a forma como servidores estiverem configurados, deve ser validado e/ou encriptado durante o trânsito.
Embora seja possível implementar um servidor de solicitação através de HTTP que facilita a solicitações do cliente de limpar o texto, é melhor prática para proteger o tráfego através de HTTPS. O serviço pode ser configurado para utilizar HTTPS com um conjunto de parâmetros no recurso de DSC **xPSDesiredStateConfiguration**.

Os requisitos de certificado para proteger o tráfego HTTPS para o servidor de solicitação não são diferentes de proteção de qualquer outro site da web HTTPS. O **servidor Web** modelo num servidor Windows Certificate Services coincida com as capacidades necessárias.

Tarefas de planeamento|
---|
Se os pedidos de certificado não são automatizados, que será necessário entrar em contacto para pedidos de um certificado?|
O que é a resposta média para o pedido?|
Como será o ficheiro de certificado ser transferido para si?|
Como será a chave privada do certificado ser transferida para si?|
Quanto tempo dura a hora de expiração padrão?|
Definir um nome DNS para o ambiente de servidor de solicitação, o que pode utilizar para o nome do certificado?|

### <a name="choosing-an-architecture"></a>Escolher uma arquitetura

Um servidor de solicitação pode ser implementado com um serviço de web hospedado no IIS ou uma partilha de ficheiros SMB. Na maioria das situações, a opção de serviço da web irá fornecer maior flexibilidade. Não é incomum para tráfego HTTPS de percorrer os limites de rede, ao passo que o tráfego SMB é, muitas vezes, filtrado ou bloqueado entre redes. O serviço web também oferece a opção de incluir um servidor de conformidade ou Web Reporting Manager (ambos os tópicos abordados numa futura versão deste documento) que fornecem um mecanismo para que os clientes comunicar o estado para um servidor para visibilidade centralizada.
SMB fornece uma opção para ambientes em que a política de estabelece que não deve ser utilizado um servidor web e outros requisitos ambientais que fazem com que uma função de servidor web indesejáveis.
Em ambos os casos, lembre-se avaliar os requisitos para assinar e criptografar o tráfego. Políticas IPSEC, assinatura SMB e HTTPS são todas as opções que vale a pena considerar.

#### <a name="load-balancing"></a>Balanceamento de carga

Clientes interagindo com o serviço web fazem um pedido para obter informações que são retornados numa única resposta. Não existem pedidos sequenciais são necessários, pelo que não é necessário para a plataforma para garantir sessões são mantidos num único servidor em qualquer ponto no tempo de balanceamento de carga.

Tarefas de planeamento|
---|
O que é solução será utilizada para tráfego entre servidores de balanceamento de carga?|
Se utilizar um balanceador de carga de hardware, o que levará um pedido para adicionar uma nova configuração para o dispositivo?|
O que é a resposta média para um pedido configurar uma nova carga balanceada o serviço web?|
As informações que serão necessárias para o pedido?|
Precisará solicitar um IP adicional ou será a equipe responsável por balanceamento de carga tratar disso?|
Tem os registros DNS necessários, e isso necessárias para a equipe responsável por configurar a solução de balanceamento de carga?|
A solução de balanceamento de carga requer que a PKI ser processadas pelo dispositivo ou pode-balanceamento de carga de tráfego HTTPS, desde que existem não requisitos de sessão?|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a>Configurações de teste e os módulos no servidor de solicitação

Como parte do planeamento de configuração, terá de pensar sobre o DSC módulos e configurações serão alojadas pelo servidor de solicitação. Para fins de planejamento da configuração é importante ter um entendimento básico de como preparar e implementar conteúdo para um servidor de solicitação.

No futuro, esta seção será expandida e incluída no guia de operações para o servidor de solicitação do DSC.  O guia discutirá o processo de dia a dia para a gestão de módulos e configurações ao longo do tempo com a automatização.

#### <a name="dsc-modules"></a>Módulos de DSC

Os clientes que pedem uma configuração terão os módulos necessários do DSC. É uma funcionalidade do servidor de solicitação automatizar a distribuição a pedido dos módulos de DSC para clientes. Se estiver a implementar um servidor de solicitação pela primeira vez, talvez como um laboratório ou de uma prova de conceito, provavelmente vai depender de módulos de DSC que estão disponíveis a partir de repositórios públicos, como a galeria do PowerShell ou de repositórios do GitHub de PowerShell.org para módulos de DSC .

É essencial lembrar-se de que mesmo para origens online confiáveis, como a galeria do PowerShell, qualquer módulo que é transferido a partir de um repositório público deve ser revisado por alguém com experiência com o PowerShell e o conhecimento do ambiente em que os módulos será utilizado antes de a ser utilizados na produção. Ao concluir esta tarefa é um bom momento para verificar a existência de qualquer carga adicional no módulo que pode ser removido, como scripts de exemplo e documentação. Isto irá reduzir a largura de banda de rede por cliente na sua primeira solicitação, quando módulos serão transferidos através da rede do servidor ao cliente.

Cada módulo tem de ser empacotado num formato específico, um ficheiro ZIP com o nome ModuleName_Version.zip que contém a carga de módulo. Depois do ficheiro é copiado para o servidor tem de ser criado um ficheiro de soma de verificação. Quando os clientes ligam ao servidor, a soma de verificação é usada para verificar que o conteúdo do módulo de DSC não foi alterado, uma vez que foi publicada.

```powershell
New-DscChecksum -ConfigurationPath .\ -OutPath .\
```

Tarefas de planeamento|
---|
Se estiver a planear um ambiente de laboratório ou teste que cenários são fundamentais para validar?|
Existem módulos publicamente disponíveis que contêm recursos para cobrir tudo o que precisa, ou precisará de criar seus próprios recursos?|
Seu ambiente terão acesso à Internet para obter os módulos públicos?|
Quem será responsável pela revisão módulos de DSC?|
Se estiver a planear um ambiente de produção que irá utilizar como um repositório local para armazenar os módulos de DSC?|
Uma equipa central aceitará módulos de DSC das equipas de aplicações? Qual será o processo?|
Irá automatizar empacotamento, copiar e criar uma soma de verificação para os módulos de DSC prontos para produção para o servidor, a partir do seu repositório de origem?|
Sua equipe será responsável por gerenciar também a plataforma de automatização?|

#### <a name="dsc-configurations"></a>Configurações de DSC

A finalidade de um servidor de solicitação é fornecer um mecanismo centralizado para distribuição de configurações de DSC por nós de cliente. As configurações são armazenadas no servidor, como documentos do MOF.
Cada documento será nomeado com um exclusivo **Guid**. Quando os clientes estão configurados para ligar com um servidor de solicitação, eles também têm o **Guid** para a configuração deve pedir. Este sistema de referência de configurações por **Guid** garante que é exclusivo global e é flexível, de modo a que pode ser aplicada uma configuração com granularidade por nó, ou como uma configuração de função que abranja vários servidores que devem ter configurações idênticas.

#### <a name="guids"></a>GUIDs

Planear a configuração **Guids** vale a pena de atenção adicional ao pensar numa implementação de servidor de solicitação. Não existe nenhum requisito específico para saber como lidar com **Guids** e o processo é provável que seja exclusivo para cada ambiente. O processo pode variar de simples a complexos: um ficheiro CSV armazenado de forma centralizada, uma tabela SQL simples, um CMDB ou uma solução complexa que requerem integração com outra solução de software ou a ferramenta. Existem duas abordagens gerais:

- **Atribuir Guids por servidor** — fornece uma medida de garantia de que cada configuração de servidor é controlada individualmente. Isso fornece um nível de precisão em torno de atualizações e pode funcionar bem em ambientes com alguns servidores.
- **Atribuir Guids por função de servidor** — todos os servidores que executam a mesma função, tais como servidores web, utilizem o mesmo GUID para referenciar os dados de configuração necessárias.  Lembre-se de que se muitos servidores partilharem o mesmo GUID, todos eles seriam atualizados simultaneamente quando a configuração for alterada.

  O GUID é algo que devem ser considerados confidenciais dados uma vez que pode ser aproveitado por alguém com más intenções para obter informações sobre como os servidores são implementados e configurados no seu ambiente. Para obter mais informações, consulte [alocar em segurança Guids no PowerShell Desired State Configuration extrair modo](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/).

Tarefas de planeamento|
---|
Quem será responsável para copiar as configurações para a pasta de servidor de solicitação quando eles estão prontos?|
Se as configurações são criadas por uma equipe de aplicativos, o que o processo será passá-los?|
Tirar partido um repositório para armazenar configurações, como eles são criados, entre as equipes?|
Irá automatizar o processo de copiar as configurações para o servidor e a criação de uma soma de verificação quando eles estão prontos?|
Como mapeará Guids para servidores ou funções, e onde serão isso armazenados?|
O que irá utilizar como um processo para configurar computadores cliente e como ele integrar com o seu processo para criar e armazenar os Guids de configuração?|

## <a name="installation-guide"></a>Guia de instalação

*Scripts fornecidos neste documento são exemplos estáveis. Reveja sempre scripts cuidadosamente antes da execução num ambiente de produção.*

### <a name="prerequisites"></a>Pré-requisitos

Para verificar a versão do PowerShell no seu servidor, utilize o seguinte comando.

```powershell
$PSVersionTable.PSVersion
```

Se possível, atualize para a versão mais recente do Windows Management Framework.
Em seguida, transferir o `xPsDesiredStateConfiguration` módulo com o seguinte comando.

```powershell
Install-Module xPSDesiredStateConfiguration
```

O comando solicitará sua aprovação antes de transferir o módulo.

### <a name="installation-and-configuration-scripts"></a>Scripts de instalação e configuração

O melhor método para implementar um servidor de solicitação de DSC é usar um script de configuração de DSC. Este documento vai apresentar scripts incluindo ambas as definições básicas que poderia configurar apenas o serviço da web de DSC e definições que poderia configurar um serviço de web de DSC incluindo do Windows Server-a-ponto avançadas.

Nota:  Atualmente o `xPSDesiredStateConfiguration` módulo de DSC requer que o servidor para ser localidade EN-US.

### <a name="basic-configuration-for-windows-server-2012"></a>Configuração básica para o Windows Server 2012

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

### <a name="advanced-configuration-for-windows-server-2012-r2"></a>Configuração avançada do Windows Server 2012 R2

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
    ([xml](Invoke-WebRequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}

Verify-DSCPullServer 'INSERT SERVER FQDN'
```

```output
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

## <a name="additional-references-snippets-and-examples"></a>Referências adicionais, trechos e exemplos

Este exemplo mostra como iniciar manualmente uma ligação de cliente (requer WMF5) para fins de teste.

```powershell
Update-DscConfiguration –Wait -Verbose
```

O [Add-DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet é utilizado para adicionar um tipo de registo CNAME a uma zona DNS.

A função de PowerShell para [criar uma soma de verificação e publicar o MOF de DSC para o servidor de solicitação SMB](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) gera automaticamente a soma de verificação necessária e, em seguida, copia a configuração do MOF e ficheiros de soma de verificação para o servidor de solicitação SMB.

## <a name="appendix---understanding-odata-service-data-file-types"></a>Apêndice - Noções básicas sobre ODATA tipos de ficheiro de dados do serviço

Um ficheiro de dados é armazenado para criar informações durante a implementação de um servidor de solicitação que inclui o serviço da web de OData. O tipo de ficheiro depende do sistema operativo, conforme descrito abaixo.

- **Windows Server 2012** o tipo de ficheiro será sempre. mdb
- **Windows Server 2012 R2** o tipo de ficheiro usará como padrão. edb, a menos que um. mdb é especificado na configuração do

Na [avançada de script de exemplo](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) para instalar um servidor de solicitação, também encontrará um exemplo de como automaticamente controlar as definições do ficheiro Web. config para impedir que alguma chance de erros causados por tipo de ficheiro.
