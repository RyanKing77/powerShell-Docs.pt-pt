---
ms.date: 07/10/2019
keywords: jea, powershell, segurança
title: Considerações de segurança JEA
ms.openlocfilehash: befc24fec368c4f6d60477daf63bf17e9431133e
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726579"
---
# <a name="jea-security-considerations"></a>Considerações de segurança JEA

JEA ajuda-o a melhorar a sua postura de segurança, reduzindo o número de administradores permanentes nas suas máquinas. JEA utiliza uma configuração de sessão do PowerShell para criar um novo ponto de entrada para os utilizadores gerir o sistema. Os utilizadores que precisam de acesso elevado, mas não ilimitado, para a máquina para realizar tarefas administrativas, podem ser concedidos acesso ao ponto final JEA. Uma vez que o JEA permite que esses usuários executar comandos de administrador sem ter acesso de administrador completo, em seguida, pode remover esses utilizadores de grupos de segurança com privilégios elevados.

## <a name="run-as-account"></a>Conta Run As

Cada ponto final da JEA tem um designado **Run** conta. Esta é a conta sob a qual são executadas ações do usuário conectado. Esta conta pode ser configurada no [o ficheiro de configuração de sessão](session-configurations.md), e a conta que escolher tem um efeito significativo sobre a segurança do seu ponto final.

**Contas virtuais** são a forma recomendada de configurar o **Run** conta. Contas virtuais são a únicas de temporárias contas locais que são criadas para o usuário conectado a utilizar durante a duração da sua sessão JEA. Assim que a sessão foi terminada, a conta virtual é destruída e não pode ser utilizada. O usuário conectado, não sabe as credenciais da conta virtual. Não é possível utilizar a conta virtual para aceder ao sistema através de outros meios, como o ambiente de trabalho remoto ou um ponto de extremidade irrestrita do PowerShell.

Por predefinição, as contas virtuais pertencem local **administradores** grupo na máquina. Isto dá a eles todos os direitos para gerir qualquer coisa no sistema, mas nenhum direito para gerir os recursos na rede.
Durante a autenticação com outras máquinas, o contexto do usuário é que a conta de computador local, a conta virtual.

Controladores de domínio são um caso especial, uma vez que existem não é um local **administradores** grupo. Em vez disso, as contas virtuais pertencem à **Admins do domínio** e pode gerir os serviços de diretório no controlador de domínio. A identidade de domínio é ainda restringida para utilização no controlador de domínio em que a sessão JEA foi instanciada. É apresentada qualquer acesso de rede proveniente do objeto de computador do controlador de domínio em vez disso.

Em ambos os casos, pode definir explicitamente quais grupos de segurança da conta virtual pertence. Esta é uma boa prática, quando a tarefa pode ser feita sem privilégios de administrador local ou de domínio. Se já tiver um grupo de segurança definido para os seus administradores, conceda a associação de conta virtual a esse grupo. A associação de grupo conta virtual é limitada a grupos de segurança local nos servidores de estação de trabalho e o membro. Em controladores de domínio virtual contas tem de ser membros dos grupos de segurança do domínio.
Depois de adicionada a um ou mais grupos de segurança, a conta virtual já não pertence aos grupos padrão (administradores locais ou de domínio).

A tabela seguinte resume as opções de configuração possíveis e permissões resultantes para contas virtuais:

|        Tipo de computador         | Configuração do grupo de conta virtual |                   Contexto de utilizador local                    | Contexto de utilizador de rede |
| ---------------------------- | ----------------------------------- | ------------------------------------------------------- | -------------------- |
| Controlador de domínio            | Predefinição                             | Utilizador de domínio, o membro de '*domínio*administradores \Domain         | Conta de computador     |
| Controlador de domínio            | Grupos de domínio A e B               | Utilizador de domínio, o membro de '*domínio*\A ','*domínio*\B'       | Conta de computador     |
| Servidor membro ou estação de trabalho | Predefinição                             | Utilizador local, o membro de '*BUILTIN*dos \Administrators        | Conta de computador     |
| Servidor membro ou estação de trabalho | Grupos locais, C e D                | Utilizador local, o membro de '*computador*\C' e '*computador*\D' | Conta de computador     |

Quando examinar os eventos de auditoria de segurança e logs de eventos do aplicativo, verá que cada sessão de utilizador JEA tem uma conta virtual exclusiva. Esta conta exclusiva ajuda-o a controlar as ações do usuário num ponto final JEA novamente para o utilizador original que executou o comando. Conta virtual nomes seguem o formato `WinRM Virtual Users\WinRM_VA_<ACCOUNTNUMBER>_<DOMAIN>_<sAMAccountName>` por exemplo, se usuário **Alice** no domínio **Contoso** reinicia um serviço num ponto de final JEA, o nome de utilizador associada a qualquer Gerenciador de controle de serviço eventos seria `WinRM Virtual Users\WinRM_VA_1_contoso_alice`.

**Contas de serviço gerida de grupo (gMSAs)** são úteis quando um servidor membro tem de ter acesso a recursos de rede na sessão JEA. Por exemplo, quando um ponto final JEA é utilizado para controlar o acesso a um serviço de REST API alojado num computador diferente. É fácil escrever funções para chamar as APIs REST, mas terá uma identidade de rede para se autenticar com a API. Utilizar uma conta de serviço gerida de grupo torna o segundo salto possível e manter o controlo sobre o qual os computadores podem utilizar a conta. As permissões efetivas da gMSA são definidas por grupos de segurança (locais ou de domínio) para que a conta gMSA pertence.

Quando um ponto final JEA é configurado para utilizar um gMSA, as ações de todos os utilizadores JEA aparecem provenientes do mesmo gMSA. A única forma de ações de rastreio para um utilizador específico é identificar o conjunto de comandos são executados numa transcrição de sessão do PowerShell.

**Pass-até credenciais** são utilizados quando não especificar um **Run** conta. PowerShell utiliza credenciais de ligação do utilizador para executar comandos no servidor remoto. Isto requer a conceder o acesso direto de utilizador ao ligar a grupos de gestão com privilégios. Esta configuração é **não** recomendado para JEA. Se o usuário conectado já tiver privilégios de administrador, pode evitar JEA e gerir o sistema por meio de outro, irrestrita. Para obter mais informações, consulte a secção abaixo sobre como [JEA não protege contra administradores](#jea-doesnt-protect-against-admins).

**Contas executar como padrão** permitem-lhe especificar uma conta de utilizador na qual a sessão do PowerShell toda é executado. Fixo de configurações de sessão usando **Run** contas (com o `-RunAsCredential` parâmetro) não têm consciência de JEA. Definições de funções deixarão de funcionar conforme esperado. Cada usuário tem autorizado para aceder ao ponto final é atribuído a mesma função.

Não deve utilizar um **RunAsCredential** num ponto final JEA porque é difícil para ações de rastreio para específico utilizadores e não dispõe o suporte para o mapeamento de utilizadores a funções.

## <a name="winrm-endpoint-acl"></a>ACL de ponto final WinRM

Como com regulares PowerShell remoting pontos finais, cada ponto final da JEA tem uma lista de controlo de acesso separado (ACL) que controla quem pode autenticar com o ponto final da JEA. Se configurado incorretamente, utilizadores fidedignos podem não conseguir aceder ao ponto de final JEA e os utilizadores não fidedignos podem ter acesso. A ACL de WinRM não afeta o mapeamento de utilizadores às funções JEA. Mapeamento é controlado pelos **RoleDefinitions** campo no ficheiro de configuração de sessão utilizado para registar o ponto final.

Por predefinição, quando um ponto final JEA tem várias funcionalidades de função, a ACL de WinRM está configurada para permitir o acesso a todos os utilizadores mapeados. Por exemplo, uma sessão JEA configurada com os comandos seguintes concede acesso total à `CONTOSO\JEA_Lev1` e `CONTOSO\JEA_Lev2`.

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

É possível auditar as permissões de utilizador com o [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.

```powershell
Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission
```

```Output
Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

Para alterar os utilizadores que têm acesso, execute `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` para uma linha de comandos interativa ou `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` para atualizar as permissões. Os utilizadores necessitam de pelo menos *Invoke* direitos para aceder ao ponto de final JEA.

É possível criar um ponto final JEA que não mapeiam uma função definida para cada utilizador que tenha acesso. Estes utilizadores podem iniciar uma sessão JEA, mas só tem acesso aos cmdlets do padrão. É possível auditar as permissões de utilizador num ponto final JEA executando `Get-PSSessionCapability`. Para obter mais informações, consulte [auditoria e relatórios na JEA](audit-and-report.md).

## <a name="least-privilege-roles"></a>Funções de privilégio mínimo

Ao desenvolver funções JEA, é importante lembrar-se de que as contas de serviço gerida de grupo e virtual em execução em segundo plano podem ter acesso ilimitado ao computador local. Funcionalidades de função JEA ajudam a limitar os comandos e as aplicações que podem ser executadas em que o contexto privilegiado.
Funções desenvolvidas podem permitir que os comandos perigosos que podem permitir a um utilizador de invasão os limites JEA ou de obter acesso a informações confidenciais.

Por exemplo, considere a seguinte entrada de recurso de função:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

Esta capacidade de função permite aos utilizadores executar qualquer cmdlet do PowerShell com o substantivo **processo** partir do **Management** módulo. Os usuários podem precisar acessar os cmdlets, como `Get-Process` para ver quais aplicativos estão sendo executados no sistema e `Stop-Process` para eliminar aplicativos que não estão a responder. No entanto, esta entrada também permite `Start-Process`, que pode ser utilizado para iniciar um programa arbitrário com permissões de administrador completo. O programa não precisa ser instalado localmente no sistema. Um usuário conectado foi possível iniciar um programa a partir de uma partilha de ficheiros que disponibiliza ao utilizador privilégios de administrador local, é executado software maligno e muito mais.

Uma versão mais segura desse mesmo recurso de função teria o seguinte aspeto:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

Evite a utilização de carateres universais no funcionalidades de função. Não se esqueça de regularmente [auditar as permissões de utilizador Efetivo](audit-and-report.md#check-effective-rights-for-a-specific-user) para compreender quais comandos estão disponíveis ao usuário.

## <a name="jea-doesnt-protect-against-admins"></a>JEA não protege contra administradores

Um dos princípios fundamentais da JEA é que ele permite fazer algumas tarefas de administração não administradores. JEA não protege contra utilizadores que já têm privilégios de administrador. Os utilizadores que pertencem **Admins do domínio**local **administradores**, ou outros grupos com privilégios elevados, podem contornar proteções de JEA por meio de outros meios. Por exemplo, pode iniciar sessão com o RDP, utilizar as consolas remotas do MMC ou ligar a pontos de extremidade de PowerShell irrestrita. Além disso, os administradores locais num sistema podem modificar configurações de JEA para permitir que os utilizadores adicionais ou alterar um recurso de função para estender o escopo do que um utilizador pode fazer na sua sessão JEA. É importante avaliar as permissões de expandida dos seus utilizadores JEA para ver se existem outras formas de obter acesso privilegiado ao sistema.

Uma prática comum é utilizar JEA para manutenção diária regular e fazer um just-in-time, solução de gestão de acesso privilegiado que permite que os usuários fiquem temporariamente administradores locais em situações de emergência. Isto ajuda a garantir que os utilizadores não são administradores permanentes no sistema, mas podem obter esses direitos se e somente quando, concluírem o fluxo de trabalho que documenta o uso dessas permissões.
