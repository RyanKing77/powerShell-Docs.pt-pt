---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: "jea, powershell, segurança"
title: "Considerações de segurança JEA"
ms.openlocfilehash: 69bbe50fb1a7580c32d657a0f084cc80c28825c7
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/15/2018
---
# <a name="jea-security-considerations"></a>Considerações de segurança JEA

> Aplica-se a: Windows PowerShell 5.0

JEA ajuda a melhorar a sua postura de segurança, reduzindo o número de administradores permanentes nas suas máquinas.
Isto é feito através da criação de um novo ponto de entrada para os utilizadores gerir o sistema (uma configuração de sessão do PowerShell), que é totalmente bloqueado por predefinição, para impedir a utilização indevida.
Os utilizadores que necessitam de algumas, mas não ilimitado, o acesso ao computador para executar tarefas administrativas pode ser concedido acesso ao ponto final do JEA.
Porque JEA permite-lhes para executarem comandos admin sem diretamente ter acesso de administrador, em seguida, pode remover os utilizadores de grupos de segurança altamente privilegiadas (faz com que os utilizadores padrão).

Este tópico descreve o modelo de segurança JEA e melhores práticas em mais detalhe.

## <a name="run-as-account"></a>Conta Run As

Cada ponto final JEA tem uma conta designada "Executar como" qual é a conta sob a qual as ações o utilizador ao ligar é efetuado.
Esta conta é configurável no [ficheiro de configuração de sessão](session-configurations.md), e a conta que escolher tem um efeito significativo da segurança do seu ponto final.

**As contas virtual** são a forma recomendada de configuração o ser executado como conta.
As contas de virtual são monouso, temporárias contas locais que são criadas para o utilizador ao ligar a utilizar durante a duração da sessão JEA.
Assim que a sessão foi terminada, a conta virtual irá ser destruída e não pode ser utilizada já.
O utilizador de ligação não souber as credenciais da conta virtual e não é possível utilizar a conta virtual para aceder ao sistema através de outros meios, como o ambiente de trabalho remoto ou um ponto de final do PowerShell.

Por predefinição, as contas virtual pertencem ao grupo de administradores local no computador.
Isto proporciona-lhes direitos totais para gerir nada no sistema, mas não existem direitos para gerir os recursos na rede.
Quando a autenticação com outras máquinas, o contexto de utilizador será da conta de computador local, não a conta virtual.

Os controladores de domínio são um caso especial porque não existe nenhum conceito de um grupo de administradores locais.
Em vez disso, as contas virtual pertencem a Admins do domínio em vez disso e podem gerir os serviços de diretório no controlador de domínio.
A identidade do domínio é ainda restringida para utilizar no controlador de domínio em que a sessão JEA instanciada e será apresentado qualquer acesso à rede ser proveniente do objeto de computador do controlador de domínio em vez disso.

Em ambos os casos, pode definir explicitamente também que a conta virtual deve pertencer de grupos de segurança.
Esta é uma boa prática quando a tarefa que está a efetuar pode ser realizada sem privilégios de administrador local/domínio.
Se já tiver um grupo de segurança definido para os seus administradores, pode conceder a associação de conta virtual simplesmente a esse grupo para atribuir-lhe as permissões que necessita.
Associação ao grupo de conta virtual está limitada a grupos de segurança local nos servidores de estação de trabalho e o membro, mas num controlador de domínio só podem ser membros dos grupos de segurança do domínio.
Depois de especificar um ou mais grupos de segurança para a conta virtual pertence a, já não irá pertencer aos grupos predefinidos (administrador local ou o administrador de domínio).

A tabela abaixo resume as opções de configuração possíveis e permissões resultantes para contas virtuais

Tipo de computador                | Configuração do grupo de conta virtual | Contexto de utilizador local                                      | Contexto de utilizador de rede
-----------------------------|-------------------------------------|---------------------------------------------------------|--------------------------------------------------
Controlador de domínio            | Predefinido                             | Utilizador de domínio, membro de '*domínio*\Domain Admins         | Conta de computador
Controlador de domínio            | Grupos de domínio A e B               | Utilizador de domínio, membro de '*domínio*\A ','*domínio*\B'       | Conta de computador
Servidor membro ou estação de trabalho | Predefinido                             | Utilizador local, membro de '*BUILTIN*dos \Administrators        | Conta de computador
Servidor membro ou estação de trabalho | Grupos locais C e D                | Utilizador local, membro de '*computador*\C' e '*computador*\D' | Conta de computador

Quando observar os eventos de auditoria de segurança e registos de eventos de aplicações, verá que cada sessão de utilizador JEA tem uma conta virtual exclusiva.
Isto ajuda a controlar as ações do utilizador num ponto final JEA novamente para o utilizador original que executou o comando.
Conta virtual nomes seguem o formato "utilizadores do WinRM Virtual\\WinRM\_VA\_*ACCOUNTNUMBER*\_*domínio* \_ *sAMAccountName*"por exemplo, se o utilizador"Alice"no domínio"Contoso"reinicia um serviço num ponto final JEA, o nome de utilizador associado a quaisquer eventos de Gestor de controlo do serviço será" utilizadores do WinRM Virtual\\WinRM\_ VA\_1\_contoso\_alice ".


**Grupo de contas de serviço geridas (gMSAs)** são úteis quando um servidor membro tem de ter acesso a recursos de rede na sessão JEA.
Um caso de utilização de exemplo para este é um ponto final de JEA é utilizado para controlar o acesso a uma API REST alojada num computador diferente.
É mais fácil escrever funções para tornar as invocações pretendidas na REST API, mas para autenticar com a API precisam de uma identidade de rede.
Utilizar uma conta de serviço geridas de grupo possibilita o "segundo hop" enquanto ainda tem controlo sobre o qual os computadores podem utilizar a conta.
As permissões efetivas de capacidade de gMSA são definidas por grupos de segurança (locais ou domínio) para que a conta gMSA pertence.

Quando um ponto final JEA é configurado para utilizar uma conta gMSA, as ações de todos os utilizadores JEA aparecerá fique do mesmo grupo de conta de serviço gerida.
É a única forma de pode analisar as ações para um utilizador específico para identificar o conjunto de comandos a executar um transcript de sessão do PowerShell.

**Transmita-através da credenciais** são utilizadas quando não especificar um executado como conta e pretender do PowerShell para utilizar a ligação credencial do utilizador para executar comandos no servidor remoto.
Esta configuração é *não* recomendada para JEA, este seria tem de conceder o acesso direto ligação do utilizador aos grupos de gestão com privilégios.
Se o utilizador ligação já tiver privilégios de administrador, pode evitar completamente o JEA e gerir o sistema através de outros, significa.
Consulte a secção abaixo sobre como [JEA não protege contra a admins](#jea-does-not-protect-against-admins) para obter mais informações.

**Executar padrão como contas** permitem-lhe especificar uma conta de utilizador na qual a sessão de PowerShell completa será executado.
Esta é uma distinção importante, porque uma configuração de sessão definido para utilizar uma execução fixa como conta (com o `-RunAsCredential` parâmetro) não está ciente de JEA.
Isto significa que as definições de função deixarão de funcionar conforme esperado e todos os utilizadores autorizados a aceder ao ponto final serão atribuído a mesma função.

Não deve utilizar um RunAsCredential um ponto final JEA devido a dificuldade em ações para utilizadores específicos e a falta de suporte para o mapeamento de utilizadores a funções de rastreio.

## <a name="winrm-endpoint-acl"></a>WinRM Endpoint ACL

Como com regulares PowerShell remota pontos finais, cada ponto final JEA tem uma lista de controlo de acesso separado (ACL) definida na configuração do WinRM que controla quem pode autenticar com o ponto final JEA.
Se configurado incorretamente, utilizadores fidedignos poderão não conseguir aceder ao ponto final JEA e/ou os utilizadores não fidedignos, podem obter acesso.
A ACL de WinRM não, no entanto, afeta o mapeamento de utilizadores a funções JEA.
Que é controlada pelo *RoleDefinitions* campo no ficheiro de configuração de sessão que foi registado no sistema.

Por predefinição, ao registar um ponto final de JEA utilizando um ficheiro de configuração de sessão e um ou mais capacidades de função, a ACL de WinRM será configurada para permitir que todos os utilizadores de mapeamento para um ou mais o acesso de funções para o ponto final.
Por exemplo, uma sessão JEA configurada utilizando os seguintes comandos irá conceder acesso total ao *CONTOSO\JEA\_Lev1* e *CONTOSO\JEA\_Lev2*.

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

Pode auditar as permissões de utilizador com o [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.

```powershell
PS C:\> Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission

Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

Para alterar os utilizadores que têm acesso, execute um `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` para uma linha de comandos interativa ou `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` para atualizar as permissões.
Os utilizadores necessitam de pelo menos *Invoke* direitos para aceder ao ponto final JEA.

Se os utilizadores adicionais são concedidos o acesso ao ponto final do JEA, mas não se enquadram qualquer uma das funções definidas no ficheiro de configuração de sessão, poderão iniciar uma sessão JEA, mas só tem acesso para os cmdlets de predefinição.
Pode auditar as permissões de utilizador num ponto final JEA executando `Get-PSSessionCapability`.
Veja o [auditoria e de relatórios no JEA](audit-and-report.md) artigo para obter mais informações sobre a auditoria de que os comandos de um utilizador tem acesso num ponto final JEA.

## <a name="least-privilege-roles"></a>Funções do menor privilégio

Ao conceber funções JEA, é importante lembrar-se de que o virtual ou grupo serviço gerido conta em execução nos bastidores, muitas vezes, tem acesso sem restrições para gerir o computador local.
Capacidades de função JEA ajudam a restringir a que essa conta pode ser utilizada ao limitar os comandos e as aplicações que podem ser executadas utilizando nesse contexto com privilégios.
Funções concebidas incorretamente podem permitir perigosos comandos a executar que podem permitir que um utilizador break fora dos limites JEA ou obter acesso a informações confidenciais.

Por exemplo, considere a seguinte entrada de capacidade de função:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

Esta capacidade de função permite aos utilizadores executar qualquer cmdlet do PowerShell com o nome "Processo" do módulo de Management.
Os utilizadores podem precisar aceder aos cmdlets como `Get-Process` para compreender que aplicações estão em execução no sistema e `Stop-Process` eliminar qualquer suspensos aplicações.
No entanto, esta entrada também permite `Start-Process`, que podem ser utilizadas para iniciar um programa arbitrário com permissões de administrador total.
O programa não tem de estar instalado localmente no sistema, pelo que um adversário simplesmente foi possível iniciar um programa numa partilha de ficheiros que permite ao utilizador ligados de privilégios de administrador local, executa malware e muito mais.'

Uma versão mais segura desta mesma capacidade de função deverá ter o seguinte aspeto:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

Evitar a utilização de carateres universais no capacidades de função e não se esqueça de [auditoria permissões de utilizador Efetivo](audit-and-report.md#check-effective-rights-for-a-specific-user) regularmente a compreender de que os comandos de um utilizador tem acesso.

## <a name="jea-does-not-protect-against-admins"></a>JEA não protege contra a admins

Um dos princípios de núcleos de JEA é permitir que não administradores efetuar *algumas* tarefas de administração.
JEA não protege contra a quem já ter privilégios de administrador.
Os utilizadores que pertencem "admins do domínio," "local admins", ou outros grupos altamente privilegiados no seu ambiente ainda será capazes de contornar proteções do JEA inscrevendo-os no computador através de outro meio.
Por exemplo, estes foi, inicie sessão com RDP, utilize consolas remotas do MMC ou ligar a pontos finais de PowerShell.
Administradores local no sistema, também podem modificar as configurações de JEA para permitir que os utilizadores adicionais gerir o sistema ou alterar uma capacidade de função para expandir o âmbito do que um utilizador pode fazer na sua sessão JEA.
Consequentemente, é importante avaliar as permissões de expandida dos seus utilizadores JEA para ver se existem outras formas foi ganham acesso privilegiado ao sistema.

É uma prática comum utilizar JEA para manutenção de rotina regular e ter um "apenas no tempo" privilegiado solução de gestão de acesso permitir que os utilizadores ficam temporariamente administradores local em situações de emergência.
Isto ajuda a certifique-se de que os utilizadores não são administradores permanentes no sistema, mas podem obter esses direitos se, e apenas quando, concluírem o fluxo de trabalho que documentos a utilização dessas permissões.

