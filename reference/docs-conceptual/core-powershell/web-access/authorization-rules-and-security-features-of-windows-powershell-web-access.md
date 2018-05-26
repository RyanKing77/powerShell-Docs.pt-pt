---
ms.date: 06/27/2017
keywords: PowerShell, o cmdlet
title: Regras de Autorização e Funcionalidades de Segurança do Windows PowerShell Web Access
ms.openlocfilehash: 1b4d4339efda78a5cb719921a9cb06881d119930
ms.sourcegitcommit: 735ccab3fb3834ccd8559fab6700b798e8e5ffbf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/25/2018
---
# <a name="authorization-rules-and-security-features-of-windows-powershell-web-access"></a>Regras de Autorização e Funcionalidades de Segurança do Windows PowerShell Web Access

Atualizada: 24 de Junho de 2013

Aplica-se a: Windows Server 2012 R2, Windows Server 2012

Acesso de Web do Windows PowerShell no Windows Server 2012 R2 e Windows Server 2012 tem um modelo de segurança restritivo.
Explicitamente tem de ser concedido acesso aos utilizadores para que poderem iniciar sessão para o gateway de acesso Web Windows PowerShell e utilizar a consola do Windows PowerShell baseada na web.

## <a name="configuring-authorization-rules-and-site-security"></a>Configurar as regras de autorização e de segurança do site

Depois de acesso Web Windows PowerShell está instalado e o gateway está configurado, os utilizadores podem abrir a página de início de sessão num browser, mas não conseguirão iniciar sessão até que o administrador do acesso Web Windows PowerShell conceda explicitamente acesso de utilizadores.
Controlo de acesso de 'Acesso Web Windows PowerShell' gerido com o conjunto de cmdlets do Windows PowerShell descritos na seguinte tabela.
Não existe nenhuma GUI comparável para adicionar ou gerir regras de autorização.
Consulte [Cmdlets do Windows PowerShell Web Access](cmdlets/web-access-cmdlets.md).

Os administradores podem definir 0 -*n* regras de autenticação para acesso Web Windows PowerShell.
A segurança predefinida é restritiva, em vez de permissiva; haver zero regras de autenticação significa que nenhum utilizador tem acesso a nada.

[Adicionar-PswaAuthorizationRule](cmdlets/add-pswaauthorizationrule.md) e [Test-PswaAuthorizationRule](cmdlets/test-pswaauthorizationrule.md) no Windows Server 2012 R2 incluir um parâmetro Credential que lhe permite adicionar e testar regras de autorização de acesso Web Windows PowerShell de remota computador, ou a partir de dentro de uma sessão ativa de acesso Web Windows PowerShell.
Como com outros cmdlets do Windows PowerShell que têm um parâmetro Credential, pode especificar um objeto PSCredential como o valor do parâmetro.
Para criar um objeto PSCredential que contém as credenciais que pretende passar para um computador remoto, execute o [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.

As regras de autenticação de acesso Web Windows PowerShell são regras da lista branca.
Cada regra é uma definição de uma ligação permitida entre os utilizadores, computadores de destino e determinado Windows PowerShellÂ [configurações de sessão](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) (também referido como pontos finais ou _espaços de execução_) no computadores de destino especificado.
Para obter uma explicação sobre **espaços de execução** consulte [início utilização do PowerShell espaços de execução](https://blogs.technet.microsoft.com/heyscriptingguy/2015/11/26/beginning-use-of-powershell-runspaces-part-1/)

> **Nota de segurança**
>
> Um utilizador precisa apenas que uma regra seja verdadeira para obter acesso.
Se um utilizador é dado acesso a um computador com acesso completo de linguagem ou acesso apenas aos cmdlets de gestão remota do Windows PowerShell, a partir da consola baseada na web, o utilizador pode iniciar sessão (ou salto) para outros computadores que estejam ligados ao primeiro computador de destino.
É a forma mais segura de configurar o acesso Web Windows PowerShell para permitir aos utilizadores acesso apenas a configurações de sessão restritas que lhes permitem realizar tarefas específicas que normalmente precisam para executarem remotamente.

Os cmdlets referenciados no [Cmdlets do Windows PowerShell Web Access](cmdlets/web-access-cmdlets.md) permitir para criar um conjunto de regras de acesso que são utilizadas para autorizar um utilizador no gateway de acesso Web Windows PowerShell.
As regras são diferentes das listas de controlo de acesso (ACL) no computador de destino e fornecem uma camada adicional de segurança para o acesso à Web.
Encontram-se mais detalhes sobre a segurança são descritas na secção seguinte.

Se os utilizadores não é possível passar em alguma das anteriores camadas de segurança, recebem uma mensagem genérica "acesso negado" nas respetivas janelas do browser.
Apesar dos detalhes de segurança serem registados no servidor de gateway, não são mostradas aos utilizadores finais as informações sobre quantas camadas de segurança passaram, ou em que camada ocorreu a falha de início de sessão ou autenticação.

Para obter mais informações sobre como configurar regras de autorização, consulte [configurar regras de autorização](#configuring-authorization-rules-and-site-security) neste tópico.

### <a name="security"></a>Segurança

O modelo de segurança de acesso Web Windows PowerShell tem quatro camadas entre um utilizador final da consola baseada na web e um computador de destino.
Os administradores do acesso Web Windows PowerShell podem adicionar camadas de segurança através de configurações adicionais na consola do Gestor de IIS.
Para obter mais informações sobre como proteger Web sites na consola do Gestor de IIS, consulte [configurar a segurança de servidor Web (IIS 7)](https://technet.microsoft.com/library/cc731278).
Para obter mais informações sobre o IIS melhores práticas e a impedir ataques denial-of-service, consulte [melhores práticas para impedir DoS/ataques Denial of Service](https://technet.microsoft.com/library/cc750213).
Um administrador também pode comprar e instalar software de autenticação adicional de revenda.

A tabela seguinte descreve as quatro camadas de segurança entre os utilizadores finais e os computadores de destino.

|Nível|Camada|
|-|-|
|1|[funcionalidades de segurança do servidor de web do IIS](#iis-web-server-security-features)|
|2|[autenticação de gateway baseada em formulários do Windows powershell web acesso](#windows-powershell-web-access-forms-based-gateway-authentication)|
|3|[regras de autorização de acesso do Windows powershell web](#windows-powershell-web-access-authorization-rules)|
|4|[regras de autorização e autenticação de destino](#target-authentication-and-authorization-rules)|

Informações detalhadas sobre cada camada podem ser encontradas nos cabeçalhos seguintes:

#### <a name="iis-web-server-security-features"></a>Funcionalidades de segurança do servidor Web do IIS

Utilizadores de acesso Web Windows PowerShell têm sempre de fornecer um nome de utilizador e palavra-passe para autenticar as respetivas contas no gateway.
No entanto, os administradores do acesso Web Windows PowerShell também podem ativar autenticação de certificados de cliente opcional ligado ou desligado, consulte [instalar e utilizar o acesso web windows powershell](install-and-use-windows-powershell-web-access.md) para ativar um certificado de teste e, posteriormente, como configurar um certificado genuíno).

A funcionalidade de certificado opcional de cliente necessita que os utilizadores finais tenham um certificado de cliente válido, para além dos nomes de utilizador e palavras-passe e faz parte da configuração do Servidor Web (IIS).
Quando a camada de certificado de cliente estiver ativada, a página de início de sessão do acesso Web Windows PowerShell irá solicitar que os utilizadores forneçam certificados válidos antes das respetivas credenciais de início de sessão são avaliadas.
A autenticação do certificado de cliente faz a sua verificação automaticamente.
Se não for encontrado um certificado válido, o acesso Web Windows PowerShell informa os utilizadores para que possam fornecer o certificado.
Se for encontrado um certificado de cliente válido, o acesso Web Windows PowerShell abre a página de início de sessão para os utilizadores forneçam os respetivos nomes de utilizador e palavras-passe.

Este é um exemplo de definições de segurança adicionais que são oferecidos pelo servidor Web do IIS.
Para obter mais informações sobre outras funcionalidades de segurança do IIS, consulte [configurar a segurança de servidor Web (IIS 7)](https://technet.microsoft.com/library/cc731278)

#### <a name="windows-powershell-web-access-forms-based-gateway-authentication"></a>Autenticação de gateway baseada em formulários de acesso Web Windows PowerShell

A página de início de sessão do acesso Web Windows PowerShell necessita de um conjunto de credenciais (nome de utilizador e palavra-passe) e oferece aos utilizadores a opção de fornecer credenciais diferentes para o computador de destino.
Se o utilizador não fornecer credenciais alternativas, o nome de utilizador principal e a palavra-passe utilizadas para ligar ao gateway também são utilizados para ligar ao computador de destino.

As credenciais necessárias são autenticadas no gateway de acesso Web Windows PowerShell.
Estas credenciais têm de ser contas de utilizador válido no acesso Web Windows PowerShell gateway servidor local ou no Active Directory.

#### <a name="windows-powershell-web-access-authorization-rules"></a>Regras de autorização de acesso Web Windows PowerShell

Depois de um utilizador é autenticado no gateway, o acesso Web Windows PowerShell verifica as regras de autorização para verificar se o utilizador tem acesso ao computador de destino solicitadas.
Depois da autorização com êxito, as credenciais do utilizador são transferidas para o computador de destino.

Estas regras são avaliadas apenas depois de um utilizador ter sido autenticado pelo gateway e antes de poder ser autenticado num computador de destino.

#### <a name="target-authentication-and-authorization-rules"></a>Autenticação de destino e regras de autorização

A camada final de segurança de acesso Web Windows PowerShell é a configuração de segurança do computador de destino.
Os utilizadores tem de ter os direitos de acesso adequados configurados no computador de destino e também nas regras de autorização de acesso Web Windows PowerShell, executar uma consola baseada na web de Windows PowerShell que afeta um computador de destino através do acesso Web Windows PowerShell.

Esta camada oferece os mesmos mecanismos de segurança que iriam avaliar as tentativas de ligação caso os utilizadores tentem criar uma sessão remota do Windows PowerShell para um computador de destino a partir do Windows PowerShell, executando o [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Enter-PSSession) ou [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/new-pssession) cmdlets.

Por predefinição, o acesso Web Windows PowerShell utiliza o nome de utilizador principal e a palavra-passe para autenticação no computador de destino e o gateway.
A baseada na web-página sessão, numa secção intitulada **definições de ligação opcionais**, oferece aos utilizadores a opção de fornecer credenciais diferentes para o computador de destino, se forem necessárias.
Se o utilizador não fornecer credenciais alternativas, o nome de utilizador principal e a palavra-passe que são utilizadas para ligar ao gateway também são utilizadas para ligar ao computador de destino.

As regras de autorização podem ser utilizadas para permitir que os utilizadores acedam a uma configuração de sessão específica.
Pode criar _restritos_ ou configurações de sessão para o Windows PowerShell Web Access e permitir que os utilizadores específicos se liguem configurações de sessão apenas a específicas quando iniciam sessão no Windows PowerShell Web Access.
Pode utilizar listas de controlo de acesso (ACL) para determinar quais os utilizadores têm acesso a pontos finais específicos e restringir mais o acesso ao ponto final de um conjunto específico de utilizadores utilizando regras de autorização descritas nesta secção.
Para obter mais informações sobre restritos, consulte [criar um espaço de execução restrita](https://msdn.microsoft.com/library/dn614668).

### <a name="configuring-authorization-rules"></a>Configurar regras de autorização

Os administradores provavelmente querem a mesma regra de autorização para os utilizadores de acesso Web Windows PowerShell que já está definido no respetivo ambiente para a gestão remota do Windows PowerShell.
O primeiro procedimento desta secção descreve como adicionar uma regra de autorização segura que concede acesso a um utilizador, iniciar sessão gerir um computador e dentro de uma configuração de sessão único.
O segundo procedimento descreve como remover uma regra de autorização que já não é necessária.

Se planeia utilizar configurações de sessão personalizadas para permitir que os utilizadores específicos trabalhem apenas dentro do restritos, no Windows PowerShell Web Access, crie as configurações de sessão personalizadas antes de adicionar regras de autorização que se referem às mesmas.
Não é possível utilizar os cmdlets de acesso Web Windows PowerShell para criar configurações de sessão personalizadas.
Para obter mais informações sobre como criar configurações de sessão personalizadas, consulte [about_Session_Configuration_Files](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configuration_files).

Cmdlets de acesso Web Windows PowerShell suportam um caráter universal, um asterisco ( \* ).
Os carateres universais não são suportados dentro de cadeias de carateres. Utilize um único asterisco por propriedade (utilizadores, computadores ou configurações de sessão).

> **Tenha em atenção**
>
> Para ver mais formas que pode utilizar regras de autorização para conceder acesso a utilizadores e ajudar a proteger o ambiente de acesso Web Windows PowerShell, [outros exemplos de cenário de regra de autorização](#other-authorization-rule-scenario-examples) neste tópico.

#### <a name="to-add-a-restrictive-authorization-rule"></a>Para adicionar uma regra de autorização restrita

1. Efetue um dos seguintes procedimentos para abrir uma sessão do Windows PowerShell com direitos de utilizador elevados.

    - No ambiente de trabalho do Windows, clique com botão direito **do Windows PowerShell** na barra de tarefas e, em seguida, clique em **executar como administrador**.

    - O Windows **iniciar** ecrã, faça duplo clique **do Windows PowerShell** e, em seguida, clique em **executar como administrador**.

2. **Passo opcional** para restringir o acesso de utilizador utilizando configurações de sessão:

    Certifique-se de que as configurações de sessão que pretende utilizar, já existem nas suas regras.
Se ainda não tiver sido criados, utilize as instruções para a criação de configurações de sessão no [about_Session_Configuration_Files](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configuration_files).

3. Esta regra de autorização permite um acesso de utilizador específico a um computador na rede a que normalmente tenham acesso, com o acesso a uma configuração específica de sessão que está confinada para o utilizador '™ necessidades de cmdlet e de scripting típicas no s. Escreva o seguinte e, em seguida, prima **Enter**.

```powershell
Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>
```

  - No exemplo seguinte, um utilizador com o nome _JSmith_ no _Contoso_ domínio é concedido acesso para gerir o computador _Contoso_214_e utilizar uma configuração de sessão com o nome _NewAdminsOnly_.

```powershell
Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly
```

4. Certifique-se de que a regra foi criada através da execução de **Get-PswaAuthorizationRule** cmdlet, ou **Test-PswaAuthorizationRule - nome de utilizador &lt;domínio\\utilizador | computador\\ utilizador&gt; - ComputerName** &lt;nome_do_computador&gt;. Por exemplo, **Test-PswaAuthorizationRule - nome de utilizador Contoso\\JSmith - ComputerName Contoso_214**.

#### <a name="to-remove-an-authorization-rule"></a>Para remover uma regra de autorização

1. Se uma sessão do Windows PowerShell ainda não estiver aberta, consulte o passo 1 de [para adicionar uma regra de autorização restrita](#to-add-a-restrictive-authorization-rule) nesta secção.

2. Escreva o seguinte e, em seguida, prima **Enter**, onde *ID da regra* representa o número de ID exclusivo da regra que pretende remover.

```powershell
Remove-PswaAuthorizationRule -ID <rule ID>
```

Em alternativa, se não souber o número de ID, mas souber o nome amigável da regra que pretende remover, pode obter o nome da regra e encaminhá-la para o `Remove-PswaAuthorizationRule` cmdlet para remover a regra, conforme mostrado no exemplo seguinte: `Get-PswaAuthorizationRule -RuleName <rule-name> | Remove-PswaAuthorizationRule`.

>**Tenha em atenção**:
>
>Não lhe para confirmar que pretende eliminar a regra de autorização especificada; a regra é eliminada ao premir **Enter**. Certifique-se de que pretende remover a regra de autorização antes de executar o cmdlet `Remove-PswaAuthorizationRule`.

#### <a name="other-authorization-rule-scenario-examples"></a>Outros exemplos de cenário de regra de autorização

Cada sessão do Windows PowerShell utiliza uma configuração de sessão; Se não for especificado para uma sessão, o Windows PowerShell utiliza a predefinição, a configuração de sessão do Windows PowerShell incorporada, denominada Microsoft. A configuração de sessão predefinida inclui todos os cmdlets disponíveis num computador. Os administradores podem restringir o acesso a todos os computadores ao definir uma configuração de sessão com um espaço de execução restrito (um intervalo limitado de cmdlets e tarefas que os utilizadores finais podem executar). Um utilizador que é concedido acesso a um computador com acesso completo de linguagem ou apenas os cmdlets de gestão remota do Windows PowerShell pode ligar a outros computadores que estejam ligados ao primeiro computador. Definir um espaço de execução restrito pode impedir que os utilizadores acedam a outros computadores do seu espaço de execução do Windows PowerShell permitido e melhora a segurança do seu ambiente de acesso Web Windows PowerShell. A configuração de sessão pode ser distribuída (utilizando a política de grupo) para todos os computadores que os administradores pretendam tornar acessíveis através do acesso Web Windows PowerShell. Para obter mais informações sobre configurações de sessão, consulte [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx).
Seguem-se alguns exemplos deste cenário.

- Um administrador cria um ponto final, denominado **PswaEndpoint**, com um espaço de execução restrito. Em seguida, o administrador cria uma regra,  **\*,\*, PswaEndpoint**e distribui o ponto final para outros computadores. A regra permite que todos os utilizadores acedam a todos os computadores com o ponto final **PswaEndpoint**. Se esta for a única regra de autorização definida no conjunto de regras, os computadores desse ponto final não se encontrarão acessíveis.

- O administrador criado um ponto final com um espaço de execução restrito denominado **PswaEndpoint**e pretende restringir o acesso a utilizadores específicos. O administrador cria um grupo de utilizadores denominado **Level1Support**e define a seguinte regra: **Level1Support,\*, PswaEndpoint**. A regra concede todos os utilizadores no grupo de **Level1Support** acesso a todos os computadores com o **PswaEndpoint** configuração. Da mesma forma, o acesso pode ser restringido a um conjunto específico de computadores.

- Alguns administradores fornecem mais acesso a determinados utilizadores que outros. Por exemplo, um administrador cria dois grupos de utilizadores, **Admins** e **BasicSupport**. O administrador também cria um ponto final com um espaço de execução restrito denominado **PswaEndpoint**e define as duas regras seguintes: **Admins,\*,\***  e  **BasicSupport,\*, PswaEndpoint**. A primeira regra fornece todos os utilizadores no **Admin** acesso de grupo para todos os computadores e a segunda regra fornece todos os utilizadores a **BasicSupport** grupo acesso apenas aos computadores com  **PswaEndpoint**.

- Um administrador configurou um ambiente de teste privado e pretende permitir que todos os utilizadores autorizados tenham acesso de rede a todos os computadores na rede a que normalmente tenham acesso, tendo acesso a todas as configurações de sessão às que têm normalmente acesso. Por ser um ambiente de teste privado, o administrador cria uma regra de autorização que não é segura.
  - O administrador executa o cmdlet `Add-PswaAuthorizationRule * * *`, que utiliza o caráter universal **\*** para representar todos os utilizadores, todos os computadores e todas as configurações.
  - Esta regra é o equivalente ao seguinte: `Add-PswaAuthorizationRule -UserName * -ComputerName * -ConfigurationName *`.

  >**Tenha em atenção**:
  >
  >Esta regra não é recomendada num ambiente seguro e ignora a camada de regra de autorização de segurança fornecida pelo acesso Web Windows PowerShell.

- Um administrador tem de permitir que os utilizadores se liguem a computadores de destino de um ambiente que inclua os grupos de trabalho e domínios, onde os computadores do grupo de trabalho são ocasionalmente utilizados para ligar a computadores de destino em domínios, da mesma forma que os computadores em domínios são ocasionalmente utilizados para ligar a computadores de destino em grupos de trabalho. O administrador tem um servidor de gateway, *PswaServer*, no grupo de trabalho e o computador de destino *srv1.contoso.com* estiver num domínio. Utilizador *Chris* é um utilizador local autorizado o servidor de gateway do grupo de trabalho e o computador de destino. O nome de utilizador no servidor do grupo de trabalho é *chrisLocal*; e o nome de utilizador no computador de destino é *contoso\\chris*. Para autorizar o acesso de Chris ao srv1.contoso.com, o administrador adiciona a seguinte regra.

```powershell
Add-PswaAuthorizationRule -userName PswaServer\chrisLocal -computerName srv1.contoso.com -configurationName Microsoft.PowerShell
```

O exemplo anterior da regra autentica o Chris no servidor de gateway e, em seguida, autoriza o seu acesso para *srv1*. Na página de início de sessão, Chris tem de fornecer um segundo conjunto de credenciais no **definições de ligação opcionais** área (*contoso\\chris*). O servidor de gateway utiliza o conjunto de credenciais adicional para autenticá-lo no computador de destino, *srv1.contoso.com*.

No cenário anterior, o acesso Web Windows PowerShell estabelece uma ligação com êxito ao computador de destino apenas depois do seguinte ter sido efetuada com êxito e permitido pela regra de autorização de pelo menos um.

1. Autenticação no servidor de gateway do grupo de trabalho ao adicionar um nome de utilizador no formato *server_name*\\*user_name* para a regra de autorização

2. Autenticação no computador de destino utilizando credenciais alternativas fornecidas na página de início de sessão, o **definições de ligação opcionais** área

  >**Tenha em atenção**:
  >
  >Se os computadores de gateway e de destino se encontrarem em diferentes grupos de trabalho ou domínios, é necessário estabelecer uma relação de fidedignidade entre os dois computadores de grupo de trabalho, os dois domínios, ou entre o grupo de trabalho e o domínio. Esta relação não pode ser configurada utilizando os cmdlets de regra de autorização de acesso Web Windows PowerShell. As regras de autorização não definem uma relação de fidedignidade entre computadores; apenas podem autorizar os utilizadores a ligar para computadores de destino específicos e configurações de sessão. Para obter mais informações sobre como configurar uma relação de confiança entre domínios diferentes, consulte [criação de domínios e confianças de floresta](https://technet.microsoft.com/library/cc794775.aspx"). Para obter mais informações sobre como adicionar computadores do grupo de trabalho para uma lista de anfitriões fidedignos, consulte [com o Gestor de servidor de gestão remota](https://technet.microsoft.com/library/dd759202.aspx)

### <a name="using-a-single-set-of-authorization-rules-for-multiple-sites"></a>Utilizar um único conjunto de regras de autorização para vários sites

As regras de autorização são armazenadas num ficheiro XML. Por predefinição, o nome do caminho do ficheiro XML é _% windir %\\Web\\PowershellWebAccess\\dados\\AuthorizationRules.xml_.

O caminho para o ficheiro XML de regras de autorização é armazenado no **powwa** ficheiro, que se encontra no _% windir %\\Web\\PowershellWebAccess\\dados_. O administrador tem a flexibilidade para alterar a referência para o caminho predefinido no **powwa** de acordo com as preferências ou requisitos. Permitir que o administrador alterar a localização do ficheiro permite que vários gateways de acesso Web Windows PowerShell, utilize as mesmas regras de autorização, se pretender a tipo de configuração.

## <a name="session-management"></a>Gestão de sessão

Por predefinição, o acesso Web Windows PowerShell limita um utilizador a três sessões em simultâneo. Pode editar a aplicação web **Web. config** ficheiros no Gestor do IIS para suportar um número diferente de sessões por utilizador.
O caminho para o **Web. config** ficheiro é _$Env: Windir\\Web\\PowerShellWebAccess\\wwwroot\\Web. config_.

Por predefinição, o servidor Web do IIS está configurado para reiniciar o conjunto aplicacional se quaisquer definições forem editadas. Por exemplo, o conjunto aplicacional é reiniciado, se as alterações sejam feitas a **Web. config** ficheiro.
>Porque **acesso Web Windows PowerShell** Estados de sessão de memória utiliza, os utilizadores com sessão iniciados para **acesso Web Windows PowerShell** sessões perdem as respetivas sessões quando o conjunto aplicacional é reiniciado.

### <a name="setting-default-parameters-on-the-sign-in-page"></a>Definição parâmetros de predefinição na página de início de sessão

Se o gateway do Windows PowerShell Web Access está em execução no Windows Server 2012 R2, pode configurar os valores predefinidos para as definições que são apresentados na página de início de sessão de acesso Web Windows PowerShell. Pode configurar os valores no **Web. config** ficheiro que está descrito no parágrafo anterior. Os valores predefinidos para as definições de página de início de sessão encontram-se no **appSettings** secção do ficheiro Web. config; o seguinte é um exemplo do **appSettings** secção. Os valores válidos para muitas destas definições são idênticos para os parâmetros correspondentes do [New-PSSession](https://technet.microsoft.com/library/hh849717.aspx) cmdlet no Windows PowerShell.
Por exemplo, o `defaultApplicationName` chave, conforme mostrado no bloco de código seguinte, é o valor da **$PSSessionApplicationName** variável de preferência no computador de destino.

```xml
    <appSettings>
            <add key="maxSessionsAllowedPerUser" value="3"/>
            <add key="defaultPortNumber" value="5985"/>
            <add key="defaultSSLPortNumber" value="5986"/>
            <add key="defaultApplicationName" value="WSMAN"/>
            <add key="defaultUseSslSelection" value="0"/>
            <add key="defaultAuthenticationType" value="0"/>
            <add key="defaultAllowRedirection" value="0"/>
            <add key="defaultConfigurationName" value="Microsoft.PowerShell"/>
    </appSettings>
```

### <a name="time-outs-and-unplanned-disconnections"></a>Tempos limite e interrupções não planeadas

Tempo limite de acesso Web Windows PowerShell sessões. No Windows PowerShell Web Access em execução no Windows Server 2012, é apresentada uma mensagem de limite de tempo para utilizadores com sessão iniciada após 15 minutos de inatividade de sessão. Se o utilizador não responder dentro de cinco minutos após a mensagem de tempo limite ser apresentada, a sessão é encerrada e a sessão do utilizador é terminada. Pode alterar os períodos de tempo de limite das sessões nas definições de Web site no Gestor do IIS.

No Windows PowerShell Web Access em execução no Windows Server 2012 R2, o tempo limite de sessões, por predefinição, passados 20 minutos de inatividade. Se os utilizadores forem desligados das sessões na consola baseada na web devido a erros de rede ou outros encerramentos não planeados ou falhas, e não porque possam tem sido fechada próprios as sessões, as sessões do Windows PowerShell Web Access continuarem a executar, ligada ao computadores de destino, até que o período de tempo limite do lado do cliente passe. A sessão é desligada após os 20 minutos predefinidos ou após o período de tempo limite especificado pelo administrador do gateway, conforme o que for mais curto.

Se o servidor de gateway estiver a executar o Windows Server 2012 R2, permite acesso Web Windows PowerShell, os utilizadores voltem a ligar aos guardadas sessões num momento posterior, mas quando erros de rede, encerramentos não planeados ou outras falhas desligam as sessões, os utilizadores não podem ver ou voltar a ligar a guardar sessões até após o período de tempo limite especificado pelo gateway ter passado o administrador.

## <a name="see-also"></a>Consulte Também

- [Instalar e utilizar o acesso Web Windows PowerShell](https://technet.microsoft.com/library/hh831611(v=ws.11).aspx)
- [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)
- [Cmdlets do Windows PowerShell Web Access](cmdlets/web-access-cmdlets.md)