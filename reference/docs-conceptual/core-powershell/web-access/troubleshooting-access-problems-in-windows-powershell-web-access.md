---
ms.date: 08/23/2017
keywords: PowerShell, o cmdlet
title: resolução de problemas de acesso no acesso web windows powershell
ms.openlocfilehash: c9b98c7a1685679eb88b718de0351154cb84e92e
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/27/2018
ms.locfileid: "52320997"
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a>Resolução de Problemas de Acesso no Windows PowerShell Web Access

Atualizado: 24 de Junho de 2013 (revisto 23 de Agosto de 2017)

Aplica-se a: Windows Server 2012 R2, Windows Server 2012

As secções seguintes identificar alguns problemas comuns durante a tentativa de ligar a um computador remoto com o Windows PowerShell Web Access e inclui sugestões para resolver os problemas.

## <a name="sign-in-failure"></a>Falha de início de sessão

Falha pode ocorrer devido a qualquer um dos seguintes procedimentos.

- Uma regra de autorização que permita o acesso do utilizador ao computador, ou uma configuração específica de sessão no computador remoto não existe.

  Segurança do Windows PowerShell Web Access é restrita; os utilizadores devem ser concedidos acesso explícito a computadores remotos utilizando regras de autorização.

  Para obter mais informações sobre a criação de regras de autorização, consulte [regras de autorização e segurança recursos do Windows PowerShell Web Access](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

- O utilizador não tem acesso autorizado ao computador de destino. É determinado por listas de controlo de acesso (ACL).

  Para obter mais informações, consulte [iniciar sessão no Windows PowerShell Web Access](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access), ou o Blog da Equipe do Windows PowerShell.

- Gestão remota do Windows PowerShell não pode ser ativada no computador de destino.

  Certifique-se a gestão remota está ativada no computador ao qual o usuário está tentando se conectar.

  Para obter mais informações, consulte [como configurar o seu computador para a gestão remota](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting).

## <a name="internal-server-error"></a>Erro de servidor interno

Quando os utilizadores tentam iniciar sessão no Windows PowerShell Web Access numa janela do Internet Explorer, são apresentados um **erro de servidor interno** página, ou *Internet Explorer* deixa de responder.

Este problema é específico ao Internet Explorer.

### <a name="possible-cause"></a>Causa possível

Esta situação pode ocorrer a utilizadores que tenham sessão iniciada com um nome de domínio que contém carateres chineses, ou se um ou mais carateres chineses fizerem parte do nome de servidor do gateway.

#### <a name="workaround"></a>Solução

1. [Instalar e executar o Internet Explorer 10](https://ie.microsoft.com/testdrive/info/downloads/Default.html)
1. Alterar o Internet Explorer **modo de documento** definição *IE10* padrões.
   1. Prima **F12** para abrir a consola de ferramentas de programador
   1. No Internet Explorer 10, clique em **modo de Browser**e, em seguida, selecione *Internet Explorer 10*.
   1. Clique em **modo de documento**e, em seguida, clique em *IE10* padrões.
   1. Prima **F12** novamente para fechar a consola de ferramentas de programação.
1. Desative a configuração automática do proxy no Internet Explorer 10.
   1. Clique em **ferramentas**e, em seguida, clique em **opções da Internet**.
   1. Na **opções da Internet** caixa de diálogo a **ligações** separador, clique em **definições de LAN**.
   1. Limpar o **detetar automaticamente as definições** caixa de verificação. Clique em **OK**e, em seguida, clique em **OK** novamente para fechar o *opções da Internet* caixa de diálogo.

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a>Não é possível ligar a um computador de grupo de trabalho remoto

Se o computador de destino for um membro de um grupo de trabalho, utilize a seguinte sintaxe para fornecer o nome de utilizador e inicie sessão computador: `<workgroup_name>\<user_name>`

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a>Não é possível localizar ferramentas de gestão do Servidor Web (IIS), apesar da função ter sido instalada

Se tiver instalado o Windows PowerShell Web Access utilizando o `Install-WindowsFeature` cmdlet, gestão de ferramentas não estão instaladas, a menos que o `-IncludeManagementTools` parâmetro é adicionado ao cmdlet.

Por exemplo, veja [para instalar o Windows PowerShell Web Access, utilizando cmdlets do Windows PowerShell](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).

Pode adicionar a consola do Gestor de IIS e que precisa, ao selecionar as ferramentas de ferramentas de gestão outros IIS uma **Assistente Adicionar funções e funcionalidades** sessão direcionada para o servidor de gateway.
A adicionar assistente funções e funcionalidades aberto a partir do Gestor de servidores.

## <a name="windows-powershell-web-access-website-is-not-accessible"></a>Web site do Windows PowerShell Web Access não está acessível

Se a configuração de segurança avançada está ativada no Internet Explorer (IE ESC), pode adicionar o site do Windows PowerShell Web Access para a lista de sites fidedignos.

Uma abordagem menos recomendada, devido a riscos de segurança, é desativar IE ESC.
Pode desativar IE ESC no mosaico propriedades na página servidor Local no Gestor de servidores.

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a>Ocorreu uma falha de autorização. Certifique-se de que está autorizado para se ligar ao computador de destino.

Ao tentar ligar ao servidor de gateway é o computador de destino e também está num grupo de trabalho, é apresentada a mensagem de erro acima.

Quando o servidor de gateway também é o servidor de destino e, é um grupo de trabalho, especifique o nome de utilizador, o nome do computador e o nome de grupo do utilizador.
Não utilize um ponto (.) por si só, para representar o nome do computador.

### <a name="scenarios-and-proper-values"></a>Cenários e os valores adequados

#### <a name="all-cases"></a>Todos os casos

Parâmetro | Valor
-- | --
UserName | Servidor\_name\\utilizador\_nome<br/>Localhost\\utilizador\_nome<br/>. \\utilizador\_nome
Grupo de utilizadores | Servidor\_name\\utilizador\_grupo<br/>Localhost\\user\_group<br/>. \\utilizador\_grupo
Grupo de computador | Servidor\_name\\computador\_grupo<br/>Localhost\\computer\_group<br/>. \\computador\_grupo

#### <a name="gateway-server-is-in-a-domain"></a>Servidor de gateway está num domínio

Parâmetro | Valor
-- | --
ComputerName | Nome completamente qualificado do servidor de gateway ou Localhost

#### <a name="gateway-server-is-in-a-workgroup"></a>O servidor de gateway está num grupo de trabalho

Parâmetro | Valor
-- | --
ComputerName | Nome do servidor

### <a name="gateway-credentials"></a>Credenciais de gateway

Inicie sessão num servidor de gateway como computador de destino utilizando as credenciais formatadas através de um dos seguintes procedimentos.

- Servidor\_name\\utilizador\_nome
- Localhost\\utilizador\_nome
- . \\utilizador\_nome

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a>Um identificador de segurança (SID) é apresentado numa regra de autorização

Um identificador de segurança (SID) é apresentado numa regra de autorização em vez do utilizador de sintaxe\_nome/computador\_nome.

A regra já não é válida ou a consulta dos Serviços de Domínio do Active Directory falhou.
Uma regra de autorização, normalmente, não é válida em cenários em que o servidor de gateway foi em simultâneo a um grupo de trabalho, mas foi posteriormente associado a um domínio

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a>Não é possível iniciar a sessão com a regra como um endereço IPv6 com um domínio

Não é possível iniciar sessão num computador de destino que foi especificado nas regras de autorização como um endereço IPv6 com um domínio.

As regras de autorização não suportam um endereço IPv6 no formato de um nome de domínio.

Para especificar um computador de destino utilizando um endereço IPv6, utilize o endereço IPv6 original (que contém dois pontos) na regra de autorização.
Domínio e os endereços IPv6 numéricos (com dois pontos) são suportados como o nome do computador de destino na página de início de sessão do Windows PowerShell Web Access, mas não em regras de autorização.

Para obter mais informações sobre os endereços IPv6, consulte [como IPv6 funciona](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx).

## <a name="see-also"></a>Consulte Também

- [Regras de autorização e funcionalidades de segurança do Windows PowerShell Web Access](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
- [Utilizar a consola do PowerShell de Windows baseado na Web](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
- [about_Remote_Requirements](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_remote_requirements)