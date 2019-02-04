---
ms.date: 06/12/2017
keywords: jea, powershell, segurança
title: Pré-requisitos JEA
ms.openlocfilehash: acc16c0c7eec357b621c0706a66b8752ae5578cd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688358"
---
# <a name="prerequisites"></a>Pré-requisitos

> Aplica-se a: Windows PowerShell 5.0

Administração just Enough é uma funcionalidade incluída com o Windows PowerShell 5.0 e superior.
Este tópico descreve os pré-requisitos que devem ser satisfeitos para começar a utilizar a JEA.

## <a name="install-jea"></a>Instalar a JEA

JEA está disponível com o Windows PowerShell 5.0 e superior, mas para todas as funcionalidades é recomendado que instale a versão mais recente do PowerShell disponível para o seu sistema.
A tabela seguinte descreve a disponibilidade da JEA no Windows Server:

Sistema operativo do servidor   | Disponibilidade JEA
--------------------------|--------------------------------
Windows Server 2016       | Pré-instalados
Windows Server 2012 R2    | Todas as funcionalidades com o WMF 5.1
Windows Server 2012       | Todas as funcionalidades com o WMF 5.1
Windows Server 2008 R2    | Funcionalidades reduzidas<sup>1</sup> com o WMF 5.1

Também pode utilizar a JEA no seu computador doméstica ou de trabalho:

Sistema operativo do cliente   | Disponibilidade JEA
--------------------------|-----------------------------------------------------
Windows 10 1607+          | Pré-instalados
Windows 10 1603, 1511     | Pré-instalado, com funcionalidades reduzidas<sup>2</sup>
Windows 10 1507           | Não disponível
Windows 8, 8.1            | Todas as funcionalidades com o WMF 5.1
Windows 7                 | Funcionalidades reduzidas<sup>1</sup> com o WMF 5.1

<sup>1</sup> JEA não pode ser configurado para utilizar contas de serviço geridas de grupo no Windows Server 2008 R2 ou Windows 7.
Contas virtuais e outros recursos JEA *são* suportado.

<sup>2</sup> versões do Windows 10 1511 e 1603 não suportam as seguintes funcionalidades JEA: em execução como um grupo gerido conta de serviço, as regras de acesso condicional em configurações de sessão, a unidade de utilizador e concederem acesso a contas de utilizador local.
Para obter suporte para estas funcionalidades, atualizar o Windows para a versão 1607 (atualização de aniversário) ou superior.

### <a name="check-which-version-of-powershell-is-installed"></a>Verifique qual é a versão do PowerShell está instalada

Para verificar a versão do PowerShell está instalada no seu sistema, verifique o `$PSVersionTable` variável numa linha de comandos do Windows PowerShell.

```powershell
$PSVersionTable.PSVersion
```

```output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

Está pronto para utilizar a JEA se o *principais* versão é maior que ou igual a **5**.
Para obter a melhor experiência e ter acesso a todas as funcionalidades mais recentes, recomenda-se que Atualize para a versão do PowerShell **5.1** sempre que possível.

### <a name="install-windows-management-framework"></a>Instalar o Windows Management Framework

Se estiver a executar uma versão mais antiga do PowerShell, terá de atualizar o sistema com a atualização mais recente do Windows Management Framework (WMF).
Pacotes de atualização e uma ligação para as notas de versão mais recente do WMF estão disponíveis no [Centro de transferências](https://blogs.msdn.microsoft.com/powershell/2016/02/24/windows-management-framework-wmf-5-0-rtm-packages-has-been-republished/).

Recomenda-se vivamente que testar a compatibilidade de sua carga de trabalho com o WMF antes de atualizar todos os seus servidores.

Utilizadores do Windows 10 devem instalar as atualizações de funcionalidades mais recentes para obter a versão atual do Windows PowerShell.

## <a name="enable-powershell-remoting"></a>Ativar a comunicação remota do PowerShell

Comunicação remota do PowerShell fornece a base no qual o JEA é criado.
Portanto, é necessário para garantir a comunicação remota do PowerShell está ativada e [bem protegida](/powershell/scripting/setup/winrmsecurity) no seu sistema antes de poder utilizar JEA.

Comunicação remota do PowerShell está ativada por predefinição no Windows Server 2012, 2012 R2 e 2016.
Pode ativar a comunicação remota do PowerShell ao executar o seguinte comando numa janela elevada do PowerShell.

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a>Ativar o registo de bloco de script (opcional) e do módulo do PowerShell

Os seguintes passos ativam o registo para todas as ações do PowerShell no seu sistema.
O registo de módulo do PowerShell não é necessário para JEA, no entanto é altamente recomendável que a ativá-lo para garantir que os utilizadores de comandos executarem são registados numa localização central.

Pode configurar a política de registo de módulo do PowerShell através da política de grupo.

1. Abra o Editor de diretiva de Grupo Local numa estação de trabalho ou um objeto de política de grupo na consola de gestão de política de grupo num controlador de domínio do Active Directory
2. Navegue para **configuração do computador\\modelos administrativos\\componentes do Windows\\Windows PowerShell**
3. Faça duplo clique no **ativar o registo de módulo**
4. Clique em **ativada**
5. Na secção de opções, clique em **mostrar** junto aos nomes de módulos
6. Tipo de `\*` de pop-up de janela. Isso instrui o PowerShell para iniciar comandos a partir de todos os módulos.
7. Clique em **OK** para definir a política
8. Faça duplo clique no **ativar o registo de bloco de Script do PowerShell**
9. Clique em **ativada**
10. Clique em **OK** para definir a política
11. (No máquinas associadas a domínios apenas) Executar `gpupdate` ou aguarde pela diretiva de grupo para processar a política atualizada e aplicar as definições

Também pode ativar a transcrição do PowerShell de todo o sistema por meio da diretiva de grupo.

## <a name="next-steps"></a>Próximos passos

[Crie um ficheiro de recurso de função](role-capabilities.md)

[Criar um ficheiro de configuração de sessão](session-configurations.md)

## <a name="see-also"></a>Consulte também

[Informações adicionais sobre a segurança da comunicação remota do PowerShell e WinRM](/powershell/scripting/setup/winrmsecurity)

[*PowerShell ♥ a equipa de azul* mensagem de blogue sobre segurança](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)