---
ms.date: 06/12/2017
keywords: jea, powershell, segurança
title: Pré-requisitos JEA
ms.openlocfilehash: a5cf5519b30b24d44c12bdeedcf4cd763e2edbde
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189776"
---
# <a name="prerequisites"></a>Pré-requisitos

> Aplica-se a: Windows PowerShell 5.0

Apenas suficiente administração é uma funcionalidade incluída com o Windows PowerShell 5.0 e posterior.
Este tópico descreve os pré-requisitos que devem ser satisfeitos para poder começar a utilizar o JEA.

## <a name="install-jea"></a>Instalar JEA

O JEA é disponível com o Windows PowerShell 5.0 e posterior, mas para uma funcionalidade completa é recomendado que instale a versão mais recente do PowerShell disponível para o seu sistema.
A tabela seguinte descreve a disponibilidade do JEA no Windows Server:

Sistema operativo do servidor   | Disponibilidade JEA
--------------------------|--------------------------------
Windows Server 2016       | Pré-instalado
Windows Server 2012 R2    | Funcionalidade completa com WMF 5.1
Windows Server 2012       | Funcionalidade completa com WMF 5.1
Windows Server 2008 R2    | Reduzido funcionalidade<sup>1</sup> com WMF 5.1

Também pode utilizar o JEA no seu computador de casa ou de trabalho:

Sistema operativo do cliente   | Disponibilidade JEA
--------------------------|-----------------------------------------------------
Windows 10 1607+          | Pré-instalado
Windows 10 1603, 1511     | Pré-instalado, com um reduzido funcionalidade<sup>2</sup>
Windows 10 1507           | Não disponível
Windows 8, 8.1            | Funcionalidade completa com WMF 5.1
Windows 7                 | Reduzido funcionalidade<sup>1</sup> com WMF 5.1

<sup>1</sup> JEA não pode ser configurado para utilizar contas de serviço geridas de grupo no Windows Server 2008 R2 ou Windows 7.
As contas virtual e outras funcionalidades JEA *são* suportado.

<sup>2</sup> versões do Windows 10 1511 e 1603 não suportam as seguintes funcionalidades JEA: em execução como um grupo gerido a conta de serviço, as regras de acesso condicional em configurações de sessão, a unidade de utilizador e conceder acesso a contas de utilizador local.
Para obter suporte para estas funcionalidades, atualização do Windows para a versão 1607 (aniversário da atualização) ou superior.

### <a name="check-which-version-of-powershell-is-installed"></a>Verifique a versão do PowerShell está instalado

Para verificar qual é a versão do PowerShell está instalada no seu sistema, verifique o `$PSVersionTable` variável numa linha de comandos do Windows PowerShell.

```powershell
PS C:\> $PSVersionTable.PSVersion

Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

Está pronto a utilizar o JEA se o *principais* versão for igual ou maior do que **5**.
Para uma experiência otimizada e ter acesso a todas as funcionalidades mais recentes, recomenda-se que Atualize a versão do PowerShell **5.1** sempre que possível.

### <a name="install-windows-management-framework"></a>Instalar o Windows Management Framework

Se estiver a executar uma versão mais antiga do PowerShell, terá de atualizar o sistema com a atualização mais recente do Windows Management Framework (WMF).
Estão disponíveis em pacotes de atualização e uma ligação para as notas de versão mais recentes do WMF o [Centro de transferências](https://aka.ms/WMF5).

Recomenda-se vivamente que teste a compatibilidade da carga de trabalho com WMF antes da atualização de todos os servidores.

Os utilizadores do Windows 10, devem instalar as atualizações de funcionalidade mais recentes para obter a versão atual do Windows PowerShell.

## <a name="enable-powershell-remoting"></a>Ativar a comunicação remota do PowerShell

Comunicação remota do PowerShell fornece a base no qual o JEA é criada.
Consequentemente, é necessário para garantir a comunicação remota do PowerShell está ativada e [corretamente protegida](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity) no seu sistema antes de poder utilizar JEA.

Comunicação remota do PowerShell está ativada por predefinição no Windows Server 2012, 2012 R2 e 2016.
Pode ativar a comunicação remota do PowerShell, executando o seguinte comando numa janela elevada do PowerShell.

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a>Ativar o módulo do PowerShell e o registo de bloco de script (opcional)

Os seguintes passos ativam o registo de todas as ações de PowerShell no seu sistema.
O registo de módulo do PowerShell não é necessário para JEA, no entanto recomenda-se vivamente que ative-lo para garantir que os utilizadores de comandos executaram são registados numa localização central.

Pode configurar a política de registo de módulo do PowerShell através da política de grupo.

1. Abra o Editor de política de Grupo Local numa estação de trabalho ou um objeto de política de grupo na consola de gestão de política de grupo num controlador de domínio do Active Directory
2. Navegue para **configuração do computador\\modelos administrativos\\componentes do Windows\\do Windows PowerShell**
3. Faça duplo clique em **ative o registo de módulo**
4. Clique em **ativada**
5. Na secção Opções, clique em **mostrar** junto aos nomes de módulo
6. Tipo de "**\***" no pop de janela. Isto dá instruções ao PowerShell para registar os comandos de todos os módulos.
7. Clique em **OK** para definir a política
8. Faça duplo clique em **ativar o registo de bloco de Script do PowerShell**
9. Clique em **ativada**
10. Clique em **OK** para definir a política
11. (No associados a um domínio máquinas apenas) Executar **gpupdate** ou aguarde pela política de grupo para processar a política e aplique as definições

Também pode ativar transcription do PowerShell de todo sistema através da política de grupo.

## <a name="next-steps"></a>Próximos passos

- [Criar um ficheiro de capacidade de função](role-capabilities.md)
- [Criar um ficheiro de configuração de sessão](session-configurations.md)

## <a name="see-also"></a>Consulte também

- [Informações adicionais sobre a segurança de comunicação remota do PowerShell e WinRM](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity)
- [*PowerShell ♥ a equipa azul* blogue de segurança](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)