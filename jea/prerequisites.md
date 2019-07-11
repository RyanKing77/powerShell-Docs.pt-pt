---
ms.date: 07/10/2019
keywords: jea, powershell, segurança
title: Pré-requisitos JEA
ms.openlocfilehash: 8fca5c068412e86acfdb8bed400699f721b76191
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734287"
---
# <a name="prerequisites"></a>Pré-requisitos

Administração just Enough é uma funcionalidade incluída no PowerShell 5.0 e superior. Este artigo descreve os pré-requisitos que devem ser satisfeitos para começar a utilizar a JEA.


## <a name="check-which-version-of-powershell-is-installed"></a>Verifique qual é a versão do PowerShell está instalada

Para verificar a versão do PowerShell está instalada no seu sistema, verifique o `$PSVersionTable` variável numa linha de comandos do Windows PowerShell.

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

JEA está disponível com o PowerShell 5.0 e superior. Para todas as funcionalidades, recomenda-se que instale a versão mais recente do PowerShell disponível para o seu sistema. A tabela seguinte descreve a disponibilidade da JEA no Windows Server:

| Sistema operativo do servidor |                Disponibilidade JEA                |
| ----------------------- | ---------------------------------------------- |
| Windows Server 2016+    | Pré-instalados                                   |
| Windows Server 2012 R2  | Todas as funcionalidades com o WMF 5.1                |
| Windows Server 2012     | Todas as funcionalidades com o WMF 5.1                |
| Windows Server 2008 R2  | Funcionalidades reduzidas<sup>1</sup> com o WMF 5.1 |

Também pode utilizar a JEA no seu computador doméstica ou de trabalho:

| Sistema operativo do cliente |                   Disponibilidade JEA                   |
| ----------------------- | ---------------------------------------------------- |
| Windows 10 1607+        | Pré-instalados                                         |
| Windows 10 1603, 1511   | Pré-instalado, com funcionalidades reduzidas<sup>2</sup> |
| Windows 10 1507         | Não disponível                                        |
| Windows 8, 8.1          | Todas as funcionalidades com o WMF 5.1                      |
| Windows 7               | Funcionalidades reduzidas<sup>1</sup> com o WMF 5.1       |

- <sup>1</sup> JEA não pode ser configurado para utilizar contas de serviço gerida de grupo no Windows Server 2008 R2 ou Windows 7. Contas virtuais e outros recursos JEA *são* suportado.

- <sup>2</sup> as seguintes funcionalidades JEA não são suportadas em versões do Windows 10 1511 e 1603:

  - Em execução como uma conta de serviço gerida de grupo
  - Regras de acesso condicional em configurações de sessão
  - A unidade de utilizador
  - Conceder acesso a contas de utilizador local

  Para obter suporte para estas funcionalidades, atualizar o Windows para a versão 1607 (atualização de aniversário) ou superior.

### <a name="install-windows-management-framework"></a>Instalar o Windows Management Framework

Se estiver a executar uma versão mais antiga do PowerShell, terá de atualizar o sistema com a atualização mais recente do Windows Management Framework (WMF). Para obter mais informações, consulte a [documentação de WMF](/powershell/wmf/overview).

Recomenda-se que teste a compatibilidade de sua carga de trabalho com o WMF antes de atualizar todos os seus servidores.

Utilizadores do Windows 10 devem instalar as atualizações de funcionalidades mais recentes para obter a versão atual do Windows PowerShell.

## <a name="enable-powershell-remoting"></a>Ativar a comunicação remota do PowerShell

Comunicação remota do PowerShell fornece a base no qual o JEA é criado. É necessário garantir a comunicação remota do PowerShell está ativada e estão protegida corretamente antes de poder utilizar JEA. Para obter mais informações, consulte [segurança de WinRM](/powershell/scripting/learn/remoting/winrmsecurity).

Comunicação remota do PowerShell está ativada por predefinição no Windows Server 2012, 2012 R2 e 2016. Pode ativar a comunicação remota do PowerShell ao executar o seguinte comando numa janela elevada do PowerShell.

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a>Ativar o registo de bloco de script (opcional) e do módulo do PowerShell

Os seguintes passos ativam o registo para todas as ações do PowerShell no seu sistema. O registo de módulo do PowerShell não é necessário para JEA, no entanto recomenda-se ativar o registo para garantir que os utilizadores de comandos executarem são registados numa localização central.

Pode configurar a política de registo de módulo do PowerShell através da política de grupo.

1. Abra o Editor de diretiva de Grupo Local numa estação de trabalho ou um objeto de política de grupo na consola de gestão de política de grupo num controlador de domínio do Active Directory
2. Navegue para **configuração do computador\\modelos administrativos\\componentes do Windows\\Windows PowerShell**
3. Faça duplo clique no **ativar o registo de módulo**
4. Clique em **ativada**
5. Na secção de opções, clique em **mostrar** junto aos nomes de módulos
6. Tipo de `*` na janela de pop-up para iniciar comandos a partir de todos os módulos.
7. Clique em **OK** para definir a política
8. Faça duplo clique no **ativar o registo de bloco de Script do PowerShell**
9. Clique em **ativada**
10. Clique em **OK** para definir a política
11. (No máquinas associadas a domínios apenas) Executar `gpupdate` ou aguarde pela diretiva de grupo para processar a política atualizada e aplicar as definições

Também pode ativar a transcrição do PowerShell de todo o sistema por meio da diretiva de grupo.

## <a name="next-steps"></a>Passos Seguintes

[Crie um ficheiro de recurso de função](role-capabilities.md)

[Criar um ficheiro de configuração de sessão](session-configurations.md)

## <a name="see-also"></a>Consulte também

[Segurança de WinRM](/powershell/scripting/learn/remoting/winrmsecurity)

[PowerShell ♥ a equipa de azul](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
