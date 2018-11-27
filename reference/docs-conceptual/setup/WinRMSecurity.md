---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: WinRMSecurity
ms.openlocfilehash: 59717e4806857e6760de523335bbee6028da8e84
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/27/2018
ms.locfileid: "52320555"
---
# <a name="powershell-remoting-security-considerations"></a>Considerações de segurança de comunicação remota do PowerShell

Comunicação remota do PowerShell é a forma recomendada para gerenciar sistemas Windows. Comunicação remota do PowerShell está ativada por predefinição no Windows Server 2012 R2. Este documento aborda as questões de segurança, recomendações e melhores práticas quando utilizar a comunicação remota do PowerShell.

## <a name="what-is-powershell-remoting"></a>O que é a comunicação remota do PowerShell?

Utiliza a comunicação remota do PowerShell [gestão remota do Windows (WinRM)](https://msdn.microsoft.com/library/windows/desktop/aa384426.aspx), que é a implementação da Microsoft a [serviços Web para gestão (WS-Management)](https://www.dmtf.org/sites/default/files/standards/documents/DSP0226_1.2.0.pdf) protocolo, para permitir que os utilizadores executar o PowerShell comandos em computadores remotos. Pode encontrar mais informações sobre como utilizar a comunicação remota do PowerShell no [executar comandos remotos](https://technet.microsoft.com/library/dd819505.aspx).

Comunicação remota do PowerShell não é igual a utilizar o **ComputerName** parâmetro de um cmdlet para executá-lo num computador remoto, que utiliza a chamada de procedimento remoto (RPC) como seu protocolo subjacente.

## <a name="powershell-remoting-default-settings"></a>Definições predefinidas da comunicação remota do PowerShell

Comunicação remota do PowerShell (e WinRM) escutam as portas seguintes:

- HTTP: 5985
- HTTPS: 5986

Por predefinição, comunicação remota do PowerShell só permite ligações de membros do grupo Administradores. Sessões são iniciadas no contexto do usuário, para que todos os controlos de acesso do sistema operativo aplicada a utilizadores individuais e grupos de continuam a aplicar enquanto esteve ligado ao longo de comunicação remota do PowerShell.

Em redes privadas, a regra de Firewall do Windows predefinida para a gestão remota do PowerShell aceita todas as ligações. Em redes públicas, a regra de Firewall do Windows padrão permite ligações de comunicação remota do PowerShell apenas a partir de dentro da mesma sub-rede. Precisa alterar explicitamente essa regra para abrir a comunicação remota do PowerShell para todas as ligações numa rede pública.

>**Aviso:** destina-se a regra de firewall para redes públicas para proteger o computador de tentativas de ligação externa potencialmente maliciosos. Tenha cuidado ao remover esta regra.

## <a name="process-isolation"></a>Isolamento do processo

Utiliza a comunicação remota do PowerShell [gestão remota do Windows (WinRM)](https://msdn.microsoft.com/library/windows/desktop/aa384426) para a comunicação entre computadores.
WinRM é executado como um serviço sob a conta de serviço de rede e gera isolados processos em execução como contas de utilizador para instâncias de PowerShell do anfitrião. Uma instância do PowerShell em execução como um utilizador não tem acesso a um processo em execução numa instância do PowerShell como outro utilizador.

## <a name="event-logs-generated-by-powershell-remoting"></a>Registos de eventos gerados pelo comunicação remota do PowerShell

FireEye tiver fornecido um resumo boa os registos de eventos e outras evidências de segurança gerados pelo sessões de comunicação remota do PowerShell, disponíveis em [investigar ataques de PowerShell](https://www.fireeye.com/content/dam/fireeye-www/global/en/solutions/pdfs/wp-lazanciyan-investigating-powershell-attacks.pdf).

## <a name="encryption-and-transport-protocols"></a>Protocolos de transporte e de encriptação

É útil considerar a segurança de uma ligação de comunicação remota do PowerShell de duas perspetivas: autenticação inicial e a comunicação em curso.

Independentemente do protocolo de transporte usado (HTTP ou HTTPS), comunicação remota do PowerShell encripta sempre todas as comunicações após a autenticação inicial com uma chave simétrica de AES-256 por sessão.

### <a name="initial-authentication"></a>Autenticação inicial

Autenticação confirma a identidade do cliente para o servidor - e Idealmente - o servidor ao cliente.

Quando um cliente se liga a um servidor de domínio que usa seu nome de computador (ou seja: servidor01, ou server01.contoso.com), o protocolo de autenticação predefinido é [Kerberos](https://msdn.microsoft.com/library/windows/desktop/aa378747.aspx).
Kerberos garante a identidade de utilizador e a identidade do servidor sem enviar qualquer tipo de credencial reutilizável.

Quando um cliente se liga a um servidor de domínio utilizando o respetivo endereço IP, ou se liga a um servidor de grupo de trabalho, a autenticação Kerberos não é possível. Nesse caso, a comunicação remota do PowerShell baseia-se na [protocolo de autenticação NTLM](https://msdn.microsoft.com/library/windows/desktop/aa378749.aspx). O protocolo de autenticação NTLM garante a identidade do utilizador sem enviar qualquer tipo de credencial delegável. Para provar a identidade do utilizador, o protocolo NTLM exige que o cliente e o servidor computação uma chave de sessão de palavra-passe do utilizador sem nunca trocar a palavra-passe em si. O servidor normalmente não sabe a senha do usuário, para que ele se comunica com o controlador de domínio, o que saber a senha do usuário e calcula a chave de sessão para o servidor.

O protocolo NTLM, no entanto, garante a identidade do servidor. Tal como acontece com todos os protocolos que utilizam o NTLM para autenticação, um invasor com acesso à conta de máquina de um computador associado a um domínio conseguiu invocar o controlador de domínio para calcular uma chave de sessão NTLM e, deste modo, representar o servidor.

Autenticação baseada em NTLM está desativada por predefinição, mas pode ter permissão por qualquer configuração SSL no servidor de destino, ou ao configurar a definição de WinRM TrustedHosts no cliente.

#### <a name="using-ssl-certificates-to-validate-server-identity-during-ntlm-based-connections"></a>Utilizar certificados SSL para validar a identidade do servidor durante a conexões baseadas em NTLM

Uma vez que o protocolo de autenticação NTLM não é possível garantir que a identidade do servidor de destino (apenas que ele já sabe a palavra-passe), pode configurar os servidores de destino utilizem SSL para comunicação remota do PowerShell. Atribuir um certificado SSL para o servidor de destino (se emitido por uma autoridade de certificação que o cliente também confia) permite a autenticação baseada em NTLM que garante a identidade de utilizador e a identidade do servidor.

#### <a name="ignoring-ntlm-based-server-identity-errors"></a>Ignorar erros de identidade do servidor baseado em NTLM

Se a implantação de um certificado SSL para um servidor para ligações de NTLM é inviável, pode suprimir os erros de identidade resultante ao adicionar o servidor para o WinRM **TrustedHosts** lista. Tenha em atenção que a adição de um nome de servidor à lista TrustedHosts não deve ser considerado como qualquer outra forma de declaração de estado da confiabilidade dos anfitriões propriamente ditos – como o protocolo de autenticação NTLM não pode garantir que está a ligar na verdade para o anfitrião está destinar a ligar a.
Em vez disso, deve considerar a definição de TrustedHosts para ser a lista de anfitriões para o qual desejar suprimir o erro gerado pelo facto de ser não é possível verificar a identidade do servidor.


### <a name="ongoing-communication"></a>Comunicação em curso

Assim que a autenticação inicial estiver concluída, o [protocolo de comunicação remota do PowerShell](https://msdn.microsoft.com/library/dd357801.aspx) encripta todas as comunicações em curso com uma chave simétrica de AES-256 por sessão.


## <a name="making-the-second-hop"></a>Efetuar segundo salto

Por predefinição, comunicação remota do PowerShell utiliza Kerberos (se disponível) ou o NTLM para autenticação. Ambos os protocolos autenticar para o computador remoto sem enviar credenciais ao mesmo.
Esta é a forma mais segura de autenticar, mas porque o computador remoto não tem as credenciais do usuário, não pode aceder a outros computadores e serviços em nome do utilizador.
Isso é conhecido como o "segundo salto problema".

Existem várias formas de evitar este problema. Para descrições desses métodos e os profissionais e os contras de cada um, consulte [efetuar segundo salto na comunicação remota do PowerShell](PS-remoting-second-hop.md).