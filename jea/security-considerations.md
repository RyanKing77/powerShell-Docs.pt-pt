---
ms.date: 06/12/2017
keywords: jea, powershell, segurança
title: Considerações de segurança JEA
ms.openlocfilehash: ede727f0f30412d520712d6ba855ba2008375d9a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687245"
---
# <a name="jea-security-considerations"></a>Considerações de segurança JEA

> Aplica-se a: Windows PowerShell 5.0

JEA ajuda-o a melhorar a sua postura de segurança, reduzindo o número de administradores permanentes nas suas máquinas.
Ele faz isso ao criar um novo ponto de entrada para os utilizadores gerir o sistema (uma configuração de sessão do PowerShell), que é rigidamente bloqueado por predefinição, para evitar o uso indevido.
Os utilizadores que precisam de alguma, mas não ilimitados, o acesso ao computador para executar tarefas administrativas pode ser concedido acesso ao ponto final JEA.
Como JEA permite a execução de comandos de administrador sem diretamente a ter acesso de administrador, em seguida, pode remover esses utilizadores de grupos de segurança com privilégios elevados (torná-los usuários padrão).

Este tópico descreve o modelo de segurança JEA e práticas recomendadas mais detalhadamente.

## <a name="run-as-account"></a>Conta Run As

Cada ponto final da JEA tem uma conta designada "Executar como", que é a conta sob a qual são realizadas ações do usuário conectado.
Esta conta pode ser configurada no [o ficheiro de configuração de sessão](session-configurations.md), e a conta que escolher tem um efeito significativo sobre a segurança do seu ponto final.

**Contas virtuais** são a forma recomendada de configurar a execução como conta.
Contas virtuais são a únicas de temporárias contas locais que são criadas para o usuário conectado a utilizar durante a duração da sua sessão JEA.
Assim que a sessão foi terminada, a conta virtual será destruída e não pode ser utilizada.
O usuário conectado, não sabe as credenciais da conta virtual e não é possível utilizar a conta virtual para aceder ao sistema através de outros meios, como o ambiente de trabalho remoto ou um ponto de extremidade irrestrita do PowerShell.

Por predefinição, contas virtuais pertencem ao grupo de administradores locais no computador.
Isto dá a eles todos os direitos para gerir qualquer coisa no sistema, mas nenhum direito para gerir os recursos na rede.
Durante a autenticação com outras máquinas, o contexto de utilizador será que a conta de computador local, a conta virtual.

Controladores de domínio são um caso especial, pois não há conceito de um grupo de administradores locais.
Em vez disso, contas virtuais pertencem a administradores do domínio em vez disso e podem gerir os serviços de diretório no controlador de domínio.
A identidade de domínio é restrita a utilizar no controlador de domínio em que a sessão JEA foi instanciada, e qualquer acesso de rede serão apresentados provenientes em vez disso, o objeto de computador do controlador de domínio.

Em ambos os casos, pode definir explicitamente também que grupos de segurança da conta virtual deve pertencer à.
Esta é uma boa prática, quando a tarefa que está a efetuar pode ser feita sem privilégios de administrador de domínio/local.
Se já tiver um grupo de segurança definido para os seus administradores, pode simplesmente conceder a associação de conta virtual para esse grupo para atribuir-lhe as permissões necessárias.
Associação de grupo de conta virtual é limitada a grupos de segurança local nos servidores de estação de trabalho e o membro, mas num controlador de domínio só podem ser membros dos grupos de segurança do domínio.
Depois de especificar um ou mais grupos de segurança para a conta virtual pertence a, já não irá pertencer aos grupos padrão (administrador local ou administrador de domínio).

A tabela abaixo resume as opções de configuração possíveis e permissões resultantes para contas virtuais

Tipo de computador                | Configuração do grupo de conta virtual | Contexto de utilizador local                                      | Contexto de utilizador de rede
-----------------------------|-------------------------------------|---------------------------------------------------------|--------------------------------------------------
Controlador de domínio            | Predefinido                             | Utilizador de domínio, o membro de '*domínio*administradores \Domain         | Conta de computador
Controlador de domínio            | Grupos de domínio A e B               | Utilizador de domínio, o membro de '*domínio*\A ','*domínio*\B'       | Conta de computador
Servidor membro ou estação de trabalho | Predefinido                             | Utilizador local, o membro de '*BUILTIN*dos \Administrators        | Conta de computador
Servidor membro ou estação de trabalho | Grupos locais, C e D                | Utilizador local, o membro de '*computador*\C' e '*computador*\D' | Conta de computador

Quando examinar os eventos de auditoria de segurança e logs de eventos do aplicativo, verá que cada sessão de utilizador JEA tem uma conta virtual exclusiva.
Isto ajuda a controlar as ações do usuário num ponto final JEA novamente para o utilizador original que executou o comando.
Conta virtual nomes seguem o formato "utilizadores de Virtual de WinRM\\WinRM\_VA\_*ACCOUNTNUMBER*\_*domínio* \_ *sAMAccountName*", por exemplo, se o utilizador"Alice"no domínio"Contoso"reinicia um serviço num ponto final JEA, o nome de utilizador associado a quaisquer eventos de Gestor de controlo de serviço seria" utilizadores do WinRM Virtual\\WinRM\_ Avaliação de vulnerabilidades\_1\_contoso\_alice ".


**Grupo de contas de serviço geridas (gMSAs)** são úteis quando um servidor membro tem de ter acesso a recursos de rede na sessão JEA.
Um caso de utilização de exemplo para que isso é um ponto final da JEA que é utilizado para controlar o acesso a uma API de REST alojada num computador diferente.
É fácil escrever funções para tornar as invocações pretendidas na REST API, mas para autenticar com a API necessita de uma identidade de rede.
Utilizar uma conta de serviço geridas de grupo torna "segundo salto" possível enquanto ainda tem controlo sobre o qual os computadores podem utilizar a conta.
As permissões efetivas da gMSA são definidas por grupos de segurança (locais ou de domínio) para que a conta gMSA pertence.

Quando um ponto final JEA é configurado para utilizar uma conta gMSA, as ações de todos os utilizadores JEA aparecerá provenientes do mesmo grupo de conta de serviço gerida.
A única maneira que pode rastrear ações para um utilizador específico é identificar o conjunto de comandos são executados numa transcrição de sessão do PowerShell.

**As credenciais de pass-até** são utilizadas quando não especificar uma execução como conta e quiser PowerShell para utilizar credenciais de ligação do utilizador para executar comandos no servidor remoto.
Esta configuração é *não* recomendado para JEA, pois exigiria a conceder o acesso direto de utilizador ao ligar a grupos de gestão com privilégios.
Se o usuário conectado já tiver privilégios de administrador, pode evitar totalmente o JEA e gerir o sistema por meio de outro, irrestrita.
Consulte a secção abaixo sobre como [JEA não protege contra administradores](#jea-does-not-protect-against-admins) para obter mais informações.

**Padrão contas executar como** permitem-lhe especificar uma conta de utilizador na qual a sessão de PowerShell completa será executado.
Esta é uma distinção importante, porque uma configuração de sessão definido para utilizar uma execução fixa como conta (com o `-RunAsCredential` parâmetro) não está ciente de JEA.
Isso significa que as definições de função deixarão de funcionar conforme esperado, e cada usuário tem autorizado para aceder ao ponto final será atribuído a mesma função.

Não deve usar um RunAsCredential num ponto final JEA devido a dificuldade em ações para utilizadores específicos e a falta de suporte para o mapeamento de utilizadores a funções de rastreio.

## <a name="winrm-endpoint-acl"></a>ACL de ponto final WinRM

Como com regulares PowerShell remoting pontos finais, cada ponto final da JEA tem uma lista de controlo de acesso separado (ACL) definida na configuração do WinRM que controla quem pode autenticar com o ponto final da JEA.
Se configurado incorretamente, utilizadores fidedignos podem não conseguir aceder ao ponto de final JEA e/ou os utilizadores não fidedignos podem obter acesso.
No entanto, a ACL de WinRM não, afeta o mapeamento de utilizadores às funções JEA.
Que é controlado pelos *RoleDefinitions* campo no ficheiro de configuração de sessão que foi registado no sistema.

Por predefinição, quando se registra um ponto final JEA utilizando um ficheiro de configuração de sessão e um ou mais funcionalidades de função, a ACL de WinRM será configurada para permitir que todos os utilizadores a mapear para um ou mais acesso de funções para o ponto final.
Por exemplo, uma sessão JEA configurada com os comandos seguintes irá garantir o acesso total às *CONTOSO\JEA\_Lev1* e *CONTOSO\JEA\_Lev2*.

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

É possível auditar as permissões de utilizador com o [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.

```powershell
PS C:\> Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission

Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

Para alterar os utilizadores que têm acesso, execute `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` para uma linha de comandos interativa ou `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` para atualizar as permissões.
Os utilizadores necessitam de pelo menos *Invoke* direitos para aceder ao ponto de final JEA.

Se os utilizadores adicionais são concedidos acesso ao ponto final JEA, mas não se enquadram em qualquer uma das funções definidas no ficheiro de configuração da sessão, poderão iniciar uma sessão JEA, mas só tem acesso aos cmdlets do padrão.
É possível auditar as permissões de utilizador num ponto final JEA executando `Get-PSSessionCapability`.
Veja a [auditoria e relatórios na JEA](audit-and-report.md) artigo para obter mais informações sobre a auditoria de que os comandos de um utilizador tem acesso a um ponto de final JEA.

## <a name="least-privilege-roles"></a>Funções de privilégio mínimo

Ao desenvolver funções JEA, é importante lembrar-se de que o virtual ou grupo serviço gerido conta em execução em segundo plano, muitas vezes, tem acesso ilimitado para gerir a máquina local.
Funcionalidades de função JEA ajudar a restringir o que essa conta pode ser utilizada, limitando os comandos e as aplicações que podem ser executadas com esse contexto privilegiado.
Funções desenvolvidas podem permitir perigosos comandos a executar que podem permitir que um utilizador sair os limites JEA ou obter acesso a informações confidenciais.

Por exemplo, considere a seguinte entrada de recurso de função:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

Esta capacidade de função permite aos utilizadores executar qualquer cmdlet do PowerShell com o substantivo "Processo" do módulo Management.
Os usuários podem precisar acessar os cmdlets, como `Get-Process` para compreender quais aplicativos estão sendo executados no sistema e `Stop-Process` interromper qualquer suspenso aplicativos.
No entanto, esta entrada também permite `Start-Process`, que pode ser utilizado para iniciar um programa arbitrário com permissões de administrador completo.
O programa não precisa ser instalado localmente no sistema, para que um adversário simplesmente foi possível iniciar um programa numa partilha de ficheiros que dá os ligação privilégios de administrador local do utilizador, o malware de execuções e muito mais. "

Uma versão mais segura desse mesmo recurso de função teria o seguinte aspeto:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

Evitar usar curingas nos recursos de função e certifique-se de que a [auditar as permissões de utilizador Efetivo](audit-and-report.md#check-effective-rights-for-a-specific-user) regularmente entender os comandos que um utilizador tem acesso.

## <a name="jea-does-not-protect-against-admins"></a>JEA não protege contra administradores

Um dos princípios fundamentais da JEA é que ela permite que não-administradores efetuar *alguns* as tarefas administrativas.
JEA não protege contra aqueles que já tem privilégios de administrador.
Os utilizadores que pertencem a "admins do domínio," "local admins", ou outros grupos com privilégios elevados no seu ambiente ainda conseguirá contornar as proteções da JEA ao iniciar sessão na máquina através de outros meios.
Por exemplo, que poderiam, inicie sessão com RDP, utilizar as consolas remotas do MMC ou ligar a pontos de extremidade de PowerShell irrestrita.
Administradores locais no sistema também podem modificar as configurações de JEA para permitir que os utilizadores adicionais gerir o sistema ou alterar um recurso de função para estender o escopo do que um utilizador pode fazer na sua sessão JEA.
Portanto, é importante avaliar as permissões de expandida dos seus utilizadores JEA para verificar se há outras maneiras que poderiam ganhar acesso privilegiado ao sistema.

Uma prática comum é usar JEA para manutenção diária regular e tem um "apenas no tempo" privilegiado de solução de gestão de acesso permitem aos utilizadores temporariamente tornam-se a administradores locais em situações de emergência.
Isto ajuda a garantir que os utilizadores não são administradores permanentes no sistema, mas podem obter esses direitos se e somente quando, concluírem o fluxo de trabalho que documenta o uso dessas permissões.