---
ms.date: 06/27/2017
keywords: PowerShell, o cmdlet
title: Regras de Autorização e Funcionalidades de Segurança do Windows PowerShell Web Access
ms.openlocfilehash: 07b85a3c7bced58b9ee8db401f0339ba6011bc96
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268352"
---
# <a name="authorization-rules-and-security-features-of-windows-powershell-web-access"></a>Regras de Autorização e Funcionalidades de Segurança do Windows PowerShell Web Access

Atualização: 24 de Junho de 2013

Aplica-se a: Windows Server 2012 R2, Windows Server 2012

Windows PowerShell Web Access no Windows Server 2012 R2 e Windows Server 2012 tem um modelo de segurança restritivas. Explicitamente devem ser concedido acesso aos utilizadores antes de poderem iniciar sessão para o gateway do Windows PowerShell Web Access e utilizar a consola do Windows PowerShell baseada na web.

## <a name="configuring-authorization-rules-and-site-security"></a>Configurar as regras de autorização e de segurança do site

Após instalação do Windows PowerShell Web Access e o gateway está configurado, os utilizadores podem abrir a página de início de sessão num browser, mas não consigo iniciar sessão até que o administrador do Windows PowerShell Web Access conceda explicitamente acesso de utilizadores. Controlo de acesso de 'Windows PowerShell Web Access' gerido com o conjunto de cmdlets do Windows PowerShell descritos na tabela seguinte. Não existe nenhuma GUI comparável para adicionar ou gerir regras de autorização.
Ver [Cmdlets do Windows PowerShell Web Access](cmdlets/web-access-cmdlets.md).

Os administradores podem definir `{0-n}` regras de autenticação para o Windows PowerShell Web Access. A segurança predefinida é restritiva, em vez de permissiva; haver zero regras de autenticação significa que nenhum utilizador tem acesso a nada.

[Adicionar-PswaAuthorizationRule](cmdlets/add-pswaauthorizationrule.md) e [Test-PswaAuthorizationRule](cmdlets/test-pswaauthorizationrule.md) no Windows Server 2012 R2 incluem um parâmetro Credential que lhe permite adicionar e testar regras de autorização do Windows PowerShell Web Access do remoto computador, ou a partir de dentro de uma sessão ativa do Windows PowerShell Web Access. Como com outros cmdlets do Windows PowerShell que têm um parâmetro de credencial, pode especificar um objeto PSCredential como o valor do parâmetro. Para criar um objeto PSCredential que contém as credenciais que pretende passar para um computador remoto, execute o [Get-Credential](/powershell/module/microsoft.powershell.security/Get-Credential) cmdlet.

Regras de autenticação do Windows PowerShell Web Access são regras de lista de permissões. Cada regra é uma definição de uma ligação permitida entre utilizadores, computadores de destino e determinado Windows PowerShellÂ [configurações de sessão](/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) (também conhecido como pontos finais ou _espaços de execução_) em computadores de destino especificado.
Para obter uma explicação sobre **espaços de execução** consulte [início utilização do PowerShell espaços de execução](https://blogs.technet.microsoft.com/heyscriptingguy/2015/11/26/beginning-use-of-powershell-runspaces-part-1/)

> [!IMPORTANT]
> Um utilizador precisa apenas que uma regra seja verdadeira para obter acesso. Se um utilizador é dado acesso a um computador com acesso completo de linguagem ou acesso apenas aos cmdlets de gestão remota do Windows PowerShell, a partir da consola baseada na web, o utilizador pode iniciar sessão (ou hop) noutros computadores ligados ao primeiro computador de destino. É a forma mais segura para configurar o Windows PowerShell Web Access permitir aos utilizadores acesso apenas a configurações de sessão restritas que lhes permitem realizar tarefas específicas que normalmente precisam para executarem remotamente.

Os cmdlets referenciados no [Cmdlets do Windows PowerShell Web Access](cmdlets/web-access-cmdlets.md) permitem criar um conjunto de regras de acesso que são utilizados para autorizar um utilizador no gateway do Windows PowerShell Web Access. As regras são diferentes das listas de controlo de acesso (ACL) no computador de destino e fornecem uma camada adicional de segurança para o acesso à Web. Encontram-se mais detalhes sobre a segurança são descritas na secção seguinte.

Se os utilizadores não é possível passar em alguma das anteriores camadas de segurança, que recebem uma mensagem genérica "acesso negado" nas respetivas janelas do browser. Apesar dos detalhes de segurança serem registados no servidor de gateway, não são mostradas aos utilizadores finais as informações sobre quantas camadas de segurança passaram, ou em que camada ocorreu a falha de início de sessão ou autenticação.

Para obter mais informações sobre como configurar regras de autorização, consulte [configurar regras de autorização](#configuring-authorization-rules-and-site-security) neste tópico.

### <a name="security"></a>Segurança

O modelo de segurança do Windows PowerShell Web Access tem quatro camadas entre um utilizador final da consola baseada na web e um computador de destino. Os administradores do Windows PowerShell Web Access podem adicionar camadas de segurança através de configurações adicionais na consola do Gestor de IIS. Para obter mais informações sobre como proteger Web sites na consola do Gestor de IIS, consulte [configurar a segurança de servidor Web (IIS7)](https://technet.microsoft.com/library/cc731278).

Para obter mais informações sobre o IIS melhores práticas e a impedir ataques denial-of-service, consulte [melhores práticas para impedir DoS/negação de ataques do serviço](https://technet.microsoft.com/library/cc750213).
Um administrador também pode comprar e instalar software de autenticação adicional de revenda.

A tabela seguinte descreve as quatro camadas de segurança entre os utilizadores finais e os computadores de destino.

|Nível|Camada|
|-|-|
|1|[funcionalidades de segurança do servidor de web do IIS](#iis-web-server-security-features)|
|2|[autenticação de gateway baseada em formulários do Windows powershell web access](#windows-powershell-web-access-forms-based-gateway-authentication)|
|3|[regras de autorização do Windows powershell web access](#windows-powershell-web-access-authorization-rules)|
|4|[regras de autenticação e autorização de destino](#target-authentication-and-authorization-rules)|

Podem encontrar informações detalhadas sobre cada camada sob os cabeçalhos seguintes:

#### <a name="iis-web-server-security-features"></a>Recursos de segurança do servidor Web do IIS

Os utilizadores do Windows PowerShell Web Access sempre tem de fornecer um nome de utilizador e palavra-passe para autenticar as respetivas contas no gateway. No entanto, os administradores do Windows PowerShell Web Access podem também ativar autenticação de certificado opcional do cliente ativada ou desativada, consulte [instalar e utilizar o acesso web windows powershell](install-and-use-windows-powershell-web-access.md) para permitir que um certificado de teste e, posteriormente, como configurar um certificado original).

A funcionalidade de certificado opcional de cliente necessita que os utilizadores finais tenham um certificado de cliente válido, para além dos nomes de utilizador e palavras-passe e faz parte da configuração do Servidor Web (IIS). Quando a camada de certificado de cliente está ativada, a página de início de sessão do Windows PowerShell Web Access solicita aos utilizadores que forneçam certificados válidos antes das credenciais de início de sessão são avaliadas. A autenticação do certificado de cliente faz a sua verificação automaticamente. Se não for encontrado um certificado válido, o Windows PowerShell Web Access informa os utilizadores, para que possam fornecer o certificado. Se for encontrado um certificado de cliente válido, o Windows PowerShell Web Access é aberta a página de início de sessão para que os utilizadores forneçam os nomes de utilizador e palavras-passe.

Este é um exemplo de definições de segurança adicionais que são oferecidos pelo servidor Web do IIS. Para obter mais informações sobre outras funcionalidades de segurança do IIS, consulte [configurar a segurança de servidor Web (IIS 7)](https://technet.microsoft.com/library/cc731278).

#### <a name="windows-powershell-web-access-forms-based-gateway-authentication"></a>Autenticação de gateway baseada em formulários do Windows PowerShell Web Access

A página de início de sessão do Windows PowerShell Web Access requer um conjunto de credenciais (nome de utilizador e palavra-passe) e oferece aos utilizadores a opção de fornecer credenciais diferentes para o computador de destino.
Se o utilizador não fornecer credenciais alternativas, o nome de utilizador principal e a palavra-passe utilizadas para ligar ao gateway também são utilizados para ligar ao computador de destino.

As credenciais necessárias são autenticadas no gateway do Windows PowerShell Web Access. Estas credenciais têm de ser contas de utilizador válido no Windows PowerShell Web Access gateway servidor local ou no Active Directory.

#### <a name="windows-powershell-web-access-authorization-rules"></a>Regras de autorização do Windows PowerShell Web Access

Depois de um utilizador é autenticado no gateway, o Windows PowerShell Web Access verifica as regras de autorização para verificar se o utilizador tem acesso ao computador de destino solicitadas. Depois da autorização efetuada com êxito, as credenciais do utilizador são transferidas para o computador de destino.

Estas regras são avaliadas apenas depois de um utilizador ter sido autenticado pelo gateway e antes de poder ser autenticado num computador de destino.

#### <a name="target-authentication-and-authorization-rules"></a>Autenticação de destino e regras de autorização

A camada final de segurança para o Windows PowerShell Web Access é a configuração de segurança do computador de destino. Os utilizadores tem de ter os direitos de acesso adequados configurados no computador de destino e também nas regras de autorização do Windows PowerShell Web Access, para executar a uma consola baseada na web do Windows PowerShell que afeta um computador de destino por meio do Windows PowerShell Web Access.

Esta camada oferece os mesmos mecanismos de segurança que iriam avaliar as tentativas de ligação caso os utilizadores tentem criar uma sessão remota do Windows PowerShell para um computador de destino a partir do Windows PowerShell ao executar o [Enter-PSSession](/powershell/module/microsoft.powershell.core/Enter-PSSession) ou [New-PSSession](/powershell/module/microsoft.powershell.core/new-pssession) cmdlets.

Por predefinição, o Windows PowerShell Web Access utiliza o nome de utilizador principal e a palavra-passe para autenticação no computador de destino e o gateway. Baseado na web início de sessão na página, numa secção intitulada **definições de ligação opcionais**, oferece aos usuários a opção de fornecer credenciais diferentes para o computador de destino, se forem necessários. Se o utilizador não fornecer credenciais alternativas, o nome de utilizador principal e a palavra-passe utilizadas para ligar ao gateway também são utilizados para ligar ao computador de destino.

As regras de autorização podem ser utilizadas para permitir que os utilizadores acedam a uma configuração de sessão específica. Pode criar _espaços de execução restritos_ ou configurações de sessão para o Windows PowerShell Web Access, e permitir que utilizadores específicos se liguem a configurações de sessão específicas apenas para quando iniciam sessão no Windows PowerShell Web Access. Pode utilizar as listas de controlo de acesso (ACL) para determinar quais os utilizadores que têm acesso a pontos finais específicos, bem como restringir mais o acesso de um conjunto específico de utilizadores ao ponto final com regras de autorização descritas nesta secção. Para obter mais informações sobre espaços de execução restritos, consulte [criar um espaço de execução restrito](https://msdn.microsoft.com/library/dn614668).

### <a name="configuring-authorization-rules"></a>Configurar regras de autorização

Os administradores provavelmente querem a mesma regra de autorização para usuários do Windows PowerShell Web Access que já esteja definida no respetivo ambiente para a gestão remota do Windows PowerShell. O primeiro procedimento desta secção descreve como adicionar uma regra de autorização segura capaz de conceder acesso a um utilizador, de modo a iniciar sessão para gerir um computador, dentro de uma única configuração de sessão. O segundo procedimento descreve como remover uma regra de autorização que já não é necessária.

Se planeja usar configurações de sessão personalizadas para permitir que utilizadores específicos funcionar apenas dentro de espaços de execução restritos no Windows PowerShell Web Access, crie as configurações de sessão personalizadas antes de adicionar regras de autorização que se referem aos mesmos. Não é possível utilizar os cmdlets do Windows PowerShell Web Access para criar configurações de sessão personalizadas. Para obter mais informações sobre a criação de configurações de sessão personalizadas, consulte [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configuration_files).

Cmdlets do Windows PowerShell Web Access suportam um caráter universal, um asterisco ( \* ). Os carateres universais não são suportados dentro de cadeias de carateres. Utilize um único asterisco por propriedade (utilizadores, computadores ou configurações de sessão).

> [!NOTE]
> Para mais formas que pode utilizar regras de autorização para conceder acesso a utilizadores e ajudar a proteger o ambiente do Windows PowerShell Web Access, consulte [outros exemplos de cenário de regra de autorização](#other-authorization-rule-scenario-examples) neste tópico.

#### <a name="to-add-a-restrictive-authorization-rule"></a>Para adicionar uma regra de autorização restrita

1. Efetue um dos seguintes procedimentos para abrir uma sessão do Windows PowerShell com direitos de utilizador elevados.

   - No ambiente de trabalho do Windows, com o botão direito **do Windows PowerShell** na barra de tarefas e, em seguida, clique em **Executar como administrador**.

   - Sobre o Windows **começar** ecrã, clique com botão direito **Windows PowerShell**e, em seguida, clique em **executar como administrador**.

2. **Passo opcional** para restringir o acesso de utilizador utilizando configurações de sessão:

   Certifique-se de que as configurações de sessão que pretende utilizar, já existem nas suas regras.

   Se ainda não tiver sido criados, utilize as instruções para a criação de configurações de sessão no [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configuration_files).

3. Esta regra de autorização permite um acesso de utilizador específico a um computador na rede para os quais normalmente tenham acesso, com acesso a uma configuração específica de sessão que tem um âmbito para o utilizador '™ necessidades de criação de scripts e o cmdlet típicas no s. Escreva o seguinte e, em seguida, prima **Enter**.

   ```
   Add-PswaAuthorizationRule -UserName <domain\user | computer\user> `
      -ComputerName <computer_name> -ConfigurationName <session_configuration_name>
   ```

   - No exemplo a seguir, um utilizador com o nome _JSmith_ no _Contoso_ domínio é concedido acesso para gerir o computador _Contoso_214_e utilizar uma configuração de sessão com o nome _NewAdminsOnly_.

   ```powershell
   Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' `
      -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly
   ```

4. Certifique-se de que a regra foi criada através da execução de **Get-PswaAuthorizationRule** cmdlet, ou `Test-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName** <computer_name>`.
   Por exemplo, `Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214`.

#### <a name="to-remove-an-authorization-rule"></a>Para remover uma regra de autorização

1. Se uma sessão do Windows PowerShell ainda não estiver aberta, consulte o passo 1 de [para adicionar uma regra de autorização restrita](#to-add-a-restrictive-authorization-rule) nesta secção.

2. Escreva o seguinte e, em seguida, prima **Enter**, onde *ID da regra* representa o número de ID exclusivo da regra que pretende remover.

   ```
   Remove-PswaAuthorizationRule -ID <rule ID>
   ```

   Em alternativa, se não souber o número da ID, mas souber o nome amigável da regra que pretende remover, pode obter o nome da regra e encaminhá-la para o cmdlet `Remove-PswaAuthorizationRule` para remover a regra, conforme exemplificado no exemplo seguinte:

   ```
   Get-PswaAuthorizationRule `
      -RuleName <rule-name> | Remove-PswaAuthorizationRule
  ```

> [!NOTE]
> Não for pedido para confirmar que pretende eliminar a regra de autorização especificada; a regra é eliminada ao premir **Enter**. Certifique-se de que pretende remover a regra de autorização antes de executar o cmdlet `Remove-PswaAuthorizationRule`.

#### <a name="other-authorization-rule-scenario-examples"></a>Outros exemplos de cenário de regra de autorização

Cada sessão do Windows PowerShell utiliza uma configuração de sessão; Se não for especificada para uma sessão, o Windows PowerShell utiliza a predefinição, a configuração de sessão do Windows PowerShell incorporados, chamado Microsoft. A configuração de sessão predefinida inclui todos os cmdlets disponíveis num computador. Os administradores podem restringir o acesso a todos os computadores ao definir uma configuração de sessão com um espaço de execução restrito (um intervalo limitado de cmdlets e tarefas que os utilizadores finais podem executar). Um utilizador que é concedido acesso a um computador com acesso completo de linguagem ou apenas os cmdlets de gestão remota do Windows PowerShell pode ligar a outros computadores que estejam ligados ao primeiro computador. Definir um espaço de execução restrito pode impedir que os utilizadores acedam a outros computadores do seu espaço de execução do Windows PowerShell permitido e melhora a segurança do seu ambiente do Windows PowerShell Web Access. A configuração de sessão pode ser distribuída (utilizando a política de grupo) para todos os computadores que os administradores pretendam tornar acessíveis através do Windows PowerShell Web Access. Para obter mais informações sobre configurações de sessão, consulte [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx). Seguem-se alguns exemplos deste cenário.

- Um administrador cria um ponto de extremidade, chamado **PswaEndpoint**, com um espaço de execução restrito. Em seguida, o administrador cria uma regra, `*,*,PswaEndpoint`e distribui o ponto final para outros computadores. A regra permite que todos os utilizadores acedam a todos os computadores com o ponto final **PswaEndpoint**.
  Se esta for a única regra de autorização definida no conjunto de regras, os computadores desse ponto final não se encontrarão acessíveis.

- O administrador criado um ponto final com um espaço de execução restrito denominado **PswaEndpoint**e pretende restringir o acesso a utilizadores específicos. O administrador cria um grupo de utilizadores denominado **Level1Support**e define a seguinte regra: **level1support,*,pswaendpoint\*, PswaEndpoint**. A regra concede todos os utilizadores no grupo **Level1Support** acesso a todos os computadores com o **PswaEndpoint** configuração. Da mesma forma, o acesso pode ser restringido a um conjunto específico de computadores.

- Alguns administradores fornecem mais acesso a determinados utilizadores que outros. Por exemplo, um administrador cria dois grupos de utilizadores **Admins** e **BasicSupport**. O administrador também cria um ponto final com um espaço de execução restrito denominado **PswaEndpoint**e define as duas regras seguintes: **Admins,\*,\***  e  **BasicSupport,\*, PswaEndpoint**. A primeira regra fornece todos os utilizadores a **administrador** acesso de grupo para todos os computadores e a segunda regra fornece todos os utilizadores na **BasicSupport** agrupam o acesso apenas a esses computadores com  **PswaEndpoint**.

- Um administrador configurou um ambiente de teste privado e pretende permitir que todos os utilizadores autorizados tenham acesso de rede a todos os computadores na rede a que normalmente tenham acesso, tendo acesso a todas as configurações de sessão às que têm normalmente acesso. Por ser um ambiente de teste privado, o administrador cria uma regra de autorização que não é segura. -O administrador executa o cmdlet `Add-PswaAuthorizationRule * * *`, que utiliza o caráter universal **\*** para representar todos os utilizadores, todos os computadores e todas as configurações. -Esta regra é o equivalente dos seguintes procedimentos: `Add-PswaAuthorizationRule -UserName * -ComputerName * -ConfigurationName *`.

  > [!NOTE]
  > Esta regra não é recomendada num ambiente seguro e ignora a camada de regra de autorização de segurança fornecida pelo Windows PowerShell Web Access.

- Um administrador tem de permitir que os utilizadores se liguem a computadores de destino de um ambiente que inclua os grupos de trabalho e domínios, onde os computadores do grupo de trabalho são ocasionalmente utilizados para ligar a computadores de destino em domínios, da mesma forma que os computadores em domínios são ocasionalmente utilizados para ligar a computadores de destino em grupos de trabalho. O administrador tem um servidor de gateway, *PswaServer*, no grupo de trabalho e o computador de destino *srv1.contoso.com* está num domínio. Usuário *Chris* é um utilizador local autorizado no servidor de gateway do grupo de trabalho e o computador de destino. Nome de utilizador no servidor do grupo de trabalho é *chrisLocal*; e o seu nome de utilizador no computador de destino é *contoso\\chris*. Para autorizar o acesso de Chris ao srv1.contoso.com, o administrador adiciona a seguinte regra.

```powershell
Add-PswaAuthorizationRule -userName PswaServer\chrisLocal `
   -computerName srv1.contoso.com -configurationName Microsoft.PowerShell
```

O exemplo anterior da regra autentica o Chris no servidor de gateway e, em seguida, autoriza o seu acesso ao *srv1*. Na página de início de sessão, Chris tem de fornecer um segundo conjunto de credenciais no **definições de ligação opcionais** área (*contoso\\chris*). O servidor de gateway utiliza o conjunto de credenciais adicional para autenticá-lo no computador de destino, *srv1.contoso.com*.

No cenário anterior, o Windows PowerShell Web Access estabelece uma ligação com êxito ao computador de destino apenas depois da seguinte ter sido concluída com êxito bem como permitida por, pelo menos, uma regra de autorização.

1. Autenticação no servidor de gateway do grupo de trabalho ao adicionar um nome de utilizador no formato *server_name*\\*user_name* para a regra de autorização

2. Autenticação no computador de destino utilizando credenciais alternativas fornecidas na página de início de sessão, o **definições de ligação opcionais** área

   > [!NOTE]
   > Se os computadores de gateway e de destino se encontrarem em diferentes grupos de trabalho ou domínios, é necessário estabelecer uma relação de fidedignidade entre os dois computadores de grupo de trabalho, os dois domínios, ou entre o grupo de trabalho e o domínio. Esta relação não pode ser configurada utilizando os cmdlets de regra de autorização do Windows PowerShell Web Access. As regras de autorização não definem uma relação de fidedignidade entre computadores; apenas podem autorizar os utilizadores a ligar para computadores de destino específicos e configurações de sessão. Para obter mais informações sobre como configurar uma relação de confiança entre domínios diferentes, consulte [domínio criação e confianças de floresta](https://technet.microsoft.com/library/cc794775.aspx).
   > Para obter mais informações sobre como adicionar computadores do grupo de trabalho a uma lista de anfitriões fidedignos, consulte [com o Gestor de servidor de gestão remota](https://technet.microsoft.com/library/dd759202.aspx).

### <a name="using-a-single-set-of-authorization-rules-for-multiple-sites"></a>Utilizar um único conjunto de regras de autorização para vários sites

As regras de autorização são armazenadas num ficheiro XML. Por predefinição, o nome do caminho do ficheiro XML é `%windir%\Web\PowershellWebAccess\data\AuthorizationRules.xml`.

O caminho para o ficheiro XML de regras de autorização é armazenado no **powwa** arquivo, que se encontra no `%windir%\Web\PowershellWebAccess\data`. O administrador tem a flexibilidade para alterar a referência para o caminho predefinido no **powwa** de acordo com as preferências ou requisitos. Permitindo que o administrador alterar a localização do ficheiro permite que vários gateways do Windows PowerShell Web Access usam as mesmas regras de autorização, se essa configuração for o pretendido.

## <a name="session-management"></a>Gestão de sessão

Por predefinição, o Windows PowerShell Web Access limita um utilizador a três sessões em simultâneo. Pode editar a aplicação web **Web. config** ficheiros no Gestor do IIS para suportar um número diferente de sessões por utilizador. O caminho para o **Web. config** ficheiro é `$Env:Windir\Web\PowerShellWebAccess\wwwroot\Web.config`.

Por predefinição, o servidor Web do IIS está configurado para reiniciar o conjunto aplicacional se quaisquer definições forem editadas. Por exemplo, o conjunto aplicacional é reiniciado se forem feitas alterações para o **Web. config** ficheiro. > porque **Windows PowerShell Web Access** utiliza os Estados de sessão na memória, > utilizadores tem sessão iniciada no **do Windows PowerShell Web Access** sessões perdem as respetivas sessões quando o conjunto aplicacional é reiniciado.

### <a name="setting-default-parameters-on-the-sign-in-page"></a>Definição parâmetros de predefinição na página de início de sessão

Se o gateway do Windows PowerShell Web Access está em execução no Windows Server 2012 R2, pode configurar valores predefinidos para as definições que são apresentadas na página de início de sessão do Windows PowerShell Web Access. Pode configurar os valores na **Web. config** ficheiro que é descrito no parágrafo anterior. Valores predefinidos para as definições da página de início de sessão encontram-se no **appSettings** secção do ficheiro Web. config; o seguinte é um exemplo da **appSettings** secção. Valores válidos para muitas destas definições são idênticos aos para os parâmetros correspondentes dos [New-PSSession](https://technet.microsoft.com/library/hh849717.aspx) cmdlet no Windows PowerShell.

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

Limite de tempo de sessões do Windows PowerShell Web Access. No Windows PowerShell Web Access em execução no Windows Server 2012, é apresentada uma mensagem de limite de tempo para utilizadores com sessão iniciada após 15 minutos de inatividade de sessão. Se o utilizador não responder dentro de cinco minutos após a mensagem de tempo limite ser apresentada, a sessão é encerrada e a sessão do utilizador é terminada. Pode alterar os períodos de tempo de limite das sessões nas definições de Web site no Gestor do IIS.

No Windows PowerShell Web Access em execução no Windows Server 2012 R2, o tempo limite de sessões, por predefinição, passados 20 minutos de inatividade. Se os utilizadores forem desligados das sessões na consola baseada na web devido a erros de rede ou outros encerramentos não planeados ou falhas, e não porque eles tem sido fechada próprios as sessões, as sessões do Windows PowerShell Web Access continuam em execução, ligado a computadores de destino, até que o período de tempo limite para o mercado de lado do cliente. A sessão é desligada após os 20 minutos predefinidos ou após o período de tempo limite especificado pelo administrador do gateway, conforme o que for mais curto.

Se o servidor de gateway estiver a executar o Windows Server 2012 R2, permite acesso Web do Windows PowerShell, os utilizadores voltem a ligar aos guardadas sessões num momento posterior, mas quando os erros de rede, encerramentos não planeados ou outras falhas desligam as sessões, os utilizadores não podem ver ou voltar a ligar a guardado sessões até após o período de tempo limite especificado pelo gateway ter passado o administrador.

## <a name="see-also"></a>Consulte Também

[Instalar e utilizar o Windows PowerShell Web Access](https://technet.microsoft.com/library/hh831611(v=ws.11).aspx)

[about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)

[Cmdlets do Windows PowerShell Web Access](cmdlets/web-access-cmdlets.md)