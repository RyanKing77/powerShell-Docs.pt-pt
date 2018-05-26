---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: WinRMSecurity
ms.openlocfilehash: 43e77067e301cdf1b792cb0d24b72ee0abb3349a
ms.sourcegitcommit: 735ccab3fb3834ccd8559fab6700b798e8e5ffbf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/25/2018
---
# <a name="powershell-remoting-security-considerations"></a>Considerações de segurança de comunicação remota do PowerShell

Comunicação remota do PowerShell é a forma recomendada para gerir sistemas Windows. Comunicação remota do PowerShell está ativada por predefinição no Windows Server 2012 R2. Este documento abrange as questões de segurança, recomendações e melhores práticas quando utilizar a comunicação remota do PowerShell.

## <a name="what-is-powershell-remoting"></a>O que é a comunicação remota do PowerShell?

Utiliza a comunicação remota do PowerShell [gestão remota do Windows (WinRM)](https://msdn.microsoft.com/library/windows/desktop/aa384426.aspx), que é a implementação Microsoft do [serviços Web para gestão (WS-Management)](http://www.dmtf.org/sites/default/files/standards/documents/DSP0226_1.2.0.pdf) protocolo, para permitir aos utilizadores executar o PowerShell comandos em computadores remotos. Pode encontrar mais informações sobre como utilizar a comunicação remota do PowerShell em [executar comandos remotos](https://technet.microsoft.com/library/dd819505.aspx).

Comunicação remota do PowerShell não é igual a utilizar o **ComputerName** parâmetro de um cmdlet executá-la num computador remoto, que utiliza a chamada de procedimento remoto (RPC) do respetivo protocolo subjacente.

## <a name="powershell-remoting-default-settings"></a>Definições predefinidas da gestão remota de PowerShell

Comunicação remota do PowerShell (e WinRM) escutarem nas portas seguintes:

- HTTP: 5985
- HTTPS: 5986

Por predefinição, comunicação remota do PowerShell só permite que as ligações dos membros do grupo Administradores. As sessões são iniciadas no contexto do utilizador, para que todos os controlos de acesso do sistema operativo aplicada a utilizadores individuais e grupos continuam a aplicar aos mesmos enquanto estiver ligado através de comunicação remota do PowerShell.

Em redes privadas, a regra de Firewall do Windows predefinida para a gestão remota de PowerShell aceita todas as ligações. Em redes públicas, a regra de Firewall do Windows predefinida permite ligações de comunicação remota do PowerShell apenas a partir de dentro da mesma sub-rede. Tem de alterar explicitamente dessa regra para abrir a comunicação remota do PowerShell para todas as ligações de uma rede pública.

>**Aviso:** destina-se a regra de firewall para redes públicas para proteger o computador de tentativas de ligação externa potencialmente maliciosas. Tenha cuidado ao remover esta regra.

## <a name="process-isolation"></a>Isolamento de processo

Utiliza a comunicação remota do PowerShell [gestão remota do Windows (WinRM)](https://msdn.microsoft.com/library/windows/desktop/aa384426) para comunicação entre computadores.
WinRM é executado como um serviço sob a conta de serviço de rede e cria isolados processos em execução como contas de utilizador para instâncias do PowerShell de anfitrião. Uma instância do PowerShell em execução como um utilizador não tem acesso a um processo em execução uma instância do PowerShell como outro utilizador.

## <a name="event-logs-generated-by-powershell-remoting"></a>Registos de eventos gerados pela comunicação remota do PowerShell

FireEye tiver fornecido um resumo dos registos de eventos e outras provas de segurança gerados pelo sessões de comunicação remota do PowerShell, disponíveis em boa [investigar PowerShell ataques](https://www.fireeye.com/content/dam/fireeye-www/global/en/solutions/pdfs/wp-lazanciyan-investigating-powershell-attacks.pdf).

## <a name="encryption-and-transport-protocols"></a>Protocolos de encriptação e de transporte

É útil considerar a segurança de uma ligação de comunicação remota do PowerShell de duas perspetivas: autenticação inicial e a comunicação em curso.

O protocolo de transporte utilizado (HTTP ou HTTPS), independentemente de comunicação remota do PowerShell encripta sempre todas as comunicações após a autenticação inicial com uma chave simétrica por sessão AES 256.

### <a name="initial-authentication"></a>Autenticação inicial

Autenticação confirma a identidade do cliente para o servidor - e Idealmente - o servidor para o cliente.

Quando um cliente liga a um servidor de domínio utilizando o respetivo nome de computador (ou seja,: servidor01, ou server01.contoso.com), o protocolo de autenticação predefinido é [Kerberos](https://msdn.microsoft.com/library/windows/desktop/aa378747.aspx).
Kerberos garante a identidade de utilizador e a identidade do servidor sem enviar algum tipo de credencial reutilizável.

Quando um cliente liga a um servidor de domínio utilizando o respetivo endereço IP ou liga a um servidor de grupo de trabalho, a autenticação Kerberos não é possível. Nesse caso, a comunicação remota do PowerShell baseia-se no [protocolo de autenticação de NTLM](https://msdn.microsoft.com/library/windows/desktop/aa378749.aspx). O protocolo de autenticação de NTLM garante a identidade do utilizador sem enviar algum tipo de credencial delegable. Para comprovar a identidade do utilizador, o protocolo NTLM requer que o cliente e o servidor computação uma chave de sessão de palavra-passe do utilizador sem nunca trocar a palavra-passe em si. O servidor, normalmente, não sabe palavra-passe do utilizador para comunicar com o controlador de domínio, o que saber a palavra-passe do utilizador e calcula a chave de sessão para o servidor.

O protocolo NTLM, no entanto, garante a identidade do servidor. Tal como acontece com todos os protocolos que utilizam o NTLM para autenticação, um atacante com acesso à conta de computador de um computador associado ao domínio conseguiu invocar o controlador de domínio para calcular uma chave de sessão NTLM e, deste modo, representar o servidor.

Autenticação baseada em NTLM está desativada por predefinição, mas pode ser autorizada por qualquer um dos configurar SSL no servidor de destino ou configurar a definição de WinRM TrustedHosts no cliente.

#### <a name="using-ssl-certificates-to-validate-server-identity-during-ntlm-based-connections"></a>Utilizar certificados SSL para validar a identidade do servidor durante a ligações de NTLM

Uma vez que o protocolo de autenticação de NTLM não é possível garantir a identidade do servidor de destino (apenas que já sabe a palavra-passe), pode configurar os servidores de destino utilizem SSL para comunicação remota do PowerShell. Atribuir um certificado SSL para o servidor de destino (se emitido por uma autoridade de certificação que o cliente também confianças) permite a autenticação baseada em NTLM que garante a identidade de utilizador e a identidade do servidor.

#### <a name="ignoring-ntlm-based-server-identity-errors"></a>A ignorar erros de identidade do servidor com base em NTLM

Se implementar um certificado SSL para um servidor para ligações de NTLM é infeasible, pode suprimir os resultante erros de identidade ao adicionar o servidor para o WinRM **TrustedHosts** lista. Tenha em atenção que adicionar um nome de servidor à lista de TrustedHosts não deve ser considerado como qualquer outra forma de declaração de estado de fidedignidade dos anfitriões próprios – como o protocolo de autenticação de NTLM não pode garantir que está a ligar na realidade para o anfitrião estiver pretender ligar ao.
Em vez disso, deve considerar a definição de TrustedHosts para ser a lista de anfitriões para os quais pretende suprimir erros gerados pelo facto de ser não é possível verificar a identidade do servidor.


### <a name="ongoing-communication"></a>Comunicação em curso

Assim que a autenticação inicial estiver concluída, o [protocolo de comunicação remota de PowerShell](https://msdn.microsoft.com/library/dd357801.aspx) encripta todas as comunicações em curso com uma chave simétrica por sessão AES 256.


## <a name="making-the-second-hop"></a>Tornar o segundo hop

Por predefinição, o sistema de interação remota do PowerShell utiliza NTLM ou Kerberos (se disponível) para autenticação. Ambos estes protocolos autentiquem para o computador remoto sem enviar credenciais ao mesmo.
Esta é a forma mais segura de autenticar, mas porque o computador remoto não tem as credenciais do utilizador, não pode aceder a outros computadores e serviços em nome do utilizador.
Isto é conhecido como "segundo problema-salto".

Existem várias formas para evitar este problema. Para obter descrições destes métodos e os profissionais de TI e contras de cada, consulte [tornando-o segundo hop comunicação remota do PowerShell](PS-remoting-second-hop.md).