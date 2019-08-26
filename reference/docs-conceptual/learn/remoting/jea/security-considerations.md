---
ms.date: 07/10/2019
keywords: Jea, PowerShell, segurança
title: Considerações de segurança do JEA
ms.openlocfilehash: befc24fec368c4f6d60477daf63bf17e9431133e
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017910"
---
# <a name="jea-security-considerations"></a>Considerações de segurança do JEA

O JEA ajuda a melhorar sua postura de segurança, reduzindo o número de administradores permanentes em seus computadores. O JEA usa uma configuração de sessão do PowerShell para criar um novo ponto de entrada para os usuários gerenciarem o sistema. Os usuários que precisam de acesso elevado, mas não ilimitado, ao computador para realizar tarefas administrativas podem receber acesso ao ponto de extremidade JEA. Como o JEA permite que esses usuários executem comandos de administrador sem ter acesso de administrador completo, você pode remover esses usuários de grupos de segurança altamente privilegiados.

## <a name="run-as-account"></a>Conta Executar como

Cada ponto de extremidade JEA tem uma conta **Executar como** designada. Essa é a conta sob a qual as ações do usuário que está se conectando são executadas. Essa conta é configurável no [arquivo de configuração de sessão](session-configurations.md)e a conta escolhida tem uma influência significativa sobre a segurança de seu ponto de extremidade.

As **contas virtuais** são a maneira recomendada de configurar a conta **Executar como** . As contas virtuais são contas locais temporárias única que são criadas para o usuário que está se conectando para uso durante a sua sessão JEA. Assim que sua sessão é encerrada, a conta virtual é destruída e não pode mais ser usada. O usuário que está se conectando não conhece as credenciais da conta virtual. A conta virtual não pode ser usada para acessar o sistema por meio de outros meios como Área de Trabalho Remota ou um ponto de extremidade do PowerShell irrestrito.

Por padrão, as contas virtuais pertencem ao grupo local de **Administradores** no computador. Isso concede a eles direitos totais para gerenciar qualquer coisa no sistema, mas não há direitos para gerenciar recursos na rede.
Ao autenticar com outros computadores, o contexto do usuário é o da conta do computador local, não a conta virtual.

Os controladores de domínio são um caso especial, pois não há um grupo local de **Administradores** . Em vez disso, as contas virtuais pertencem a **Administradores de domínio** e podem gerenciar os serviços de diretório no controlador de domínio. A identidade do domínio ainda é restrita para uso no controlador de domínio em que a sessão JEA foi instanciada. Qualquer acesso à rede parece vir do objeto de computador do controlador de domínio.

Em ambos os casos, você pode definir explicitamente a quais grupos de segurança a conta virtual pertence. Essa é uma boa prática quando a tarefa pode ser feita sem privilégios locais ou de administrador de domínio. Se você já tiver um grupo de segurança definido para seus administradores, conceda a associação de conta virtual a esse grupo. A associação ao grupo de contas virtuais é limitada a grupos de segurança locais em servidores de estação de trabalho e membros. Em controladores de domínio, as contas virtuais devem ser membros de grupos de segurança de domínio.
Depois que a conta virtual tiver sido adicionada a um ou mais grupos de segurança, ela não pertencerá mais aos grupos padrão (administradores locais ou de domínio).

A tabela a seguir resume as possíveis opções de configuração e as permissões resultantes para contas virtuais:

|        Tipo de computador         | Configuração do grupo de contas virtuais |                   Contexto de usuário local                    | Contexto de usuário de rede |
| ---------------------------- | ----------------------------------- | ------------------------------------------------------- | -------------------- |
| Controlador de domínio            | Predefinido                             | Usuário de domínio, membro de '*domínio*\Domain admins '         | Conta de computador     |
| Controlador de domínio            | Grupos de domínio A e B               | Usuário de domínio, membro de '*domínio*\a ', '*domínio*\b '       | Conta de computador     |
| Servidor membro ou estação de trabalho | Predefinido                             | Usuário local, membro de '*BuiltIn*\Administrators '        | Conta de computador     |
| Servidor membro ou estação de trabalho | Grupos locais C e D                | Usuário local, membro de '*computador*\c ' e '*computador*\d ' | Conta de computador     |

Ao examinar os eventos de auditoria de segurança e os logs de eventos do aplicativo, você verá que cada sessão de usuário do JEA tem uma conta virtual exclusiva. Essa conta exclusiva ajuda a rastrear ações do usuário em um ponto de extremidade JEA de volta para o usuário original que executou o comando. Nomes de conta virtual seguem o `WinRM Virtual Users\WinRM_VA_<ACCOUNTNUMBER>_<DOMAIN>_<sAMAccountName>` formato por exemplo, se o usuário **Alice** no domínio **contoso** reinicia um serviço em um ponto de extremidade Jea, o nome de usuário associado a qualquer evento `WinRM Virtual Users\WinRM_VA_1_contoso_alice`do Gerenciador de controle de serviço seria.

**As contas de serviço gerenciado por grupo (gMSAs)** são úteis quando um servidor membro precisa ter acesso aos recursos de rede na sessão Jea. Por exemplo, quando um ponto de extremidade JEA é usado para controlar o acesso a um serviço de API REST hospedado em um computador diferente. É fácil escrever funções para invocar as APIs REST, mas você precisa de uma identidade de rede para autenticar com a API. O uso de uma conta de serviço gerenciado por grupo torna o segundo salto possível, mantendo o controle sobre quais computadores podem usar a conta. As permissões efetivas do gMSA são definidas pelos grupos de segurança (local ou domínio) aos quais a conta gMSA pertence.

Quando um ponto de extremidade JEA é configurado para usar um gMSA, as ações de todos os usuários do JEA parecem vir do mesmo gMSA. A única maneira de rastrear ações de volta para um usuário específico é identificar o conjunto de comandos executados em uma transcrição de sessão do PowerShell.

**As credenciais pass-thru** são usadas quando você não especifica uma conta **Executar como** . O PowerShell usa a credencial do usuário que está se conectando para executar comandos no servidor remoto. Isso exige que você conceda ao usuário que está se conectando acesso direto a grupos de gerenciamento privilegiado. Essa configuração **não** é recomendada para Jea. Se o usuário que está se conectando já tiver privilégios de administrador, ele poderá evitar JEA e gerenciar o sistema por meio de outros meios não restringidos. Para obter mais informações, consulte a seção abaixo sobre como o [Jea não protege contra administradores](#jea-doesnt-protect-against-admins).

As **contas Executar como padrão** permitem que você especifique qualquer conta de usuário na qual a sessão inteira do PowerShell seja executada. As configurações de sessão **que usam contas Executar como** fixas `-RunAsCredential` (com o parâmetro) não reconhecem o Jea. As definições de função não funcionam mais conforme o esperado. Cada usuário autorizado a acessar o ponto de extremidade recebe a mesma função.

Você não deve usar um **RunAsCredential** em um ponto de extremidade Jea porque é difícil rastrear ações de volta para usuários específicos e não tem suporte para mapear usuários para funções.

## <a name="winrm-endpoint-acl"></a>ACL de ponto de extremidade WinRM

Assim como acontece com os pontos de extremidade de comunicação remota do PowerShell, cada JEA Endpoint tem uma lista de controle de acesso (ACL) separada que controla quem pode autenticar com o ponto de extremidade JEA. Se estiverem configurados incorretamente, os usuários confiáveis não poderão acessar o ponto de extremidade JEA e os usuários não confiáveis poderão ter acesso. A ACL do WinRM não afeta o mapeamento de usuários para as funções JEA. O mapeamento é controlado pelo campo **RoleDefinitions** no arquivo de configuração de sessão usado para registrar o ponto de extremidade.

Por padrão, quando um ponto de extremidade JEA tem vários recursos de função, a ACL do WinRM é configurada para permitir o acesso a todos os usuários mapeados. Por exemplo, uma sessão Jea configurada usando os comandos a seguir concede `CONTOSO\JEA_Lev1` acesso `CONTOSO\JEA_Lev2`completo ao e ao.

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

Você pode auditar permissões de usuário com o cmdlet [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) .

```powershell
Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission
```

```Output
Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

Para alterar quais usuários têm acesso, execute `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` um prompt interativo ou `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` para atualizar as permissões. Os usuários precisam de pelo menos direitos de invocação para acessar o ponto de extremidade Jea.

É possível criar um ponto de extremidade JEA que não mapeie uma função definida para cada usuário que tenha acesso. Esses usuários podem iniciar uma sessão JEA, mas só têm acesso aos cmdlets padrão. Você pode auditar permissões de usuário em um ponto de `Get-PSSessionCapability`extremidade Jea executando. Para obter mais informações, consulte [auditoria e relatórios em Jea](audit-and-report.md).

## <a name="least-privilege-roles"></a>Funções de privilégios mínimos

Ao criar funções JEA, é importante lembrar que as contas de serviço gerenciadas por grupos e virtuais em execução nos bastidores podem ter acesso irrestrito ao computador local. Os recursos de função JEA ajudam a limitar os comandos e os aplicativos que podem ser executados nesse contexto privilegiado.
Funções criadas incorretamente podem permitir comandos perigosos que podem permitir que um usuário interrompa os limites do JEA ou obtenha acesso a informações confidenciais.

Por exemplo, considere a seguinte entrada de capacidade de função:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

Essa capacidade de função permite que os usuários executem qualquer cmdlet do PowerShell com o **processo** substantivo do módulo **Microsoft. PowerShell. Management** . Os usuários podem precisar acessar cmdlets como `Get-Process` para ver quais aplicativos estão sendo executados no sistema e `Stop-Process` para eliminar aplicativos que não estão respondendo. No entanto, essa entrada `Start-Process`também permite, que pode ser usada para iniciar um programa arbitrário com permissões totais de administrador. O programa não precisa ser instalado localmente no sistema. Um usuário conectado pode iniciar um programa de um compartilhamento de arquivos que dá aos privilégios de administrador local do usuário, executa malware e muito mais.

Uma versão mais segura desse mesmo recurso de função teria a seguinte aparência:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

Evite usar curingas em recursos de função. Certifique-se de [auditar regularmente as permissões de usuário efetivas](audit-and-report.md#check-effective-rights-for-a-specific-user) para entender quais comandos são acessíveis ao usuário.

## <a name="jea-doesnt-protect-against-admins"></a>O JEA não protege contra administradores

Um dos principais princípios do JEA é que ele permite que não-administradores realizem algumas tarefas de administração. O JEA não protege contra usuários que já têm privilégios de administrador. Os usuários que pertencem a **Administradores de domínio**, **Administradores**locais ou outros grupos altamente privilegiados podem burlar as proteções do Jea por meio de outros meios. Por exemplo, eles podiam entrar com o RDP, usar consoles do MMC remotos ou conectar-se a pontos de extremidade do PowerShell não restringidos. Além disso, os administradores locais em um sistema podem modificar as configurações de JEA para permitir usuários adicionais ou alterar uma capacidade de função para estender o escopo do que um usuário pode fazer em sua sessão JEA. É importante avaliar as permissões estendidas de seus usuários do JEA para ver se há outras maneiras de obter acesso privilegiado ao sistema.

Uma prática comum é usar o JEA para manutenção regular do dia a dia e ter uma solução de gerenciamento de acesso privilegiado just-in-time que permite que os usuários se tornem temporariamente administradores locais em situações de emergência. Isso ajuda a garantir que os usuários não sejam administradores permanentes no sistema, mas podem obter esses direitos se, e somente quando, eles concluírem um fluxo de trabalho que documenta o uso dessas permissões.
