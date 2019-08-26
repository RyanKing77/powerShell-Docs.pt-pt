---
ms.date: 07/10/2019
keywords: Jea, PowerShell, segurança
title: Pré-requisitos do JEA
ms.openlocfilehash: 8fca5c068412e86acfdb8bed400699f721b76191
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017938"
---
# <a name="prerequisites"></a>Pré-requisitos

Apenas administração suficiente é um recurso incluído no PowerShell 5,0 e superior. Este artigo descreve os pré-requisitos que devem ser satisfeitos para começar a usar o JEA.


## <a name="check-which-version-of-powershell-is-installed"></a>Verifique qual versão do PowerShell está instalada

Para verificar qual versão do PowerShell está instalada em seu sistema, verifique a `$PSVersionTable` variável em um prompt do Windows PowerShell.

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

O JEA está disponível com o PowerShell 5,0 e superior. Para obter funcionalidade completa, é recomendável que você instale a versão mais recente do PowerShell disponível para seu sistema. A tabela a seguir descreve a disponibilidade do JEA no Windows Server:

| Sistema operacional do servidor |                Disponibilidade do JEA                |
| ----------------------- | ---------------------------------------------- |
| Windows Server 2016 +    | Pré-instalado                                   |
| Windows Server 2012 R2  | Funcionalidade completa com o WMF 5,1                |
| Windows Server 2012     | Funcionalidade completa com o WMF 5,1                |
| Windows Server 2008 R2  | Funcionalidade reduzida<sup>1</sup> com o WMF 5,1 |

Você também pode usar o JEA em seu computador doméstico ou de trabalho:

| Sistema operacional do cliente |                   Disponibilidade do JEA                   |
| ----------------------- | ---------------------------------------------------- |
| Windows 10 1607+        | Pré-instalado                                         |
| Windows 10 1603, 1511   | Pré-instalado, com funcionalidade reduzida<sup>2</sup> |
| Windows 10 1507         | Não disponível                                        |
| Windows 8, 8,1          | Funcionalidade completa com o WMF 5,1                      |
| Windows 7               | Funcionalidade reduzida<sup>1</sup> com o WMF 5,1       |

- <sup>1</sup> Jea não pode ser configurada para usar contas de serviço gerenciadas por grupo no windows Server 2008 R2 ou no Windows 7. Há suporte para contas virtuais e outros recursos do Jea.

- <sup>2</sup> os seguintes recursos de Jea não têm suporte no Windows 10 versões 1511 e 1603:

  - Executando como uma conta de serviço gerenciado por grupo
  - Regras de acesso condicional em configurações de sessão
  - A unidade do usuário
  - Concedendo acesso a contas de usuário local

  Para obter suporte para esses recursos, atualize o Windows para a versão 1607 (atualização de aniversário) ou superior.

### <a name="install-windows-management-framework"></a>Instalar o Windows Management Framework

Se você estiver executando uma versão mais antiga do PowerShell, talvez seja necessário atualizar seu sistema com a atualização mais recente do WMF (Windows Management Framework). Para obter mais informações, consulte a [documentação do WMF](/powershell/wmf/overview).

É recomendável que você teste a compatibilidade da sua carga de trabalho com o WMF antes de atualizar todos os servidores.

Os usuários do Windows 10 devem instalar as atualizações de recursos mais recentes para obter a versão atual do Windows PowerShell.

## <a name="enable-powershell-remoting"></a>Habilitar a comunicação remota do PowerShell

A comunicação remota do PowerShell fornece a base na qual o JEA é criado. É necessário garantir que a comunicação remota do PowerShell esteja habilitada e protegida corretamente antes de poder usar o JEA. Para obter mais informações, consulte [segurança do WinRM](/powershell/scripting/learn/remoting/winrmsecurity).

A comunicação remota do PowerShell é habilitada por padrão no Windows Server 2012, 2012 R2 e 2016. Você pode habilitar a comunicação remota do PowerShell executando o seguinte comando em uma janela do PowerShell com privilégios elevados.

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a>Habilitar o módulo do PowerShell e o log de bloco de script (opcional)

As etapas a seguir habilitam o registro em log para todas as ações do PowerShell em seu sistema. O log de módulo do PowerShell não é necessário para JEA, no entanto, é recomendável ativar o registro em log para garantir que os comandos executados pelos usuários sejam registrados em um local central.

Você pode configurar a política de log do módulo do PowerShell usando Política de Grupo.

1. Abrir o Editor de Política de Grupo Local em uma estação de trabalho ou um objeto de Política de Grupo no Console de Gerenciamento de Política de Grupo em um controlador de Domínio do Active Directory
2. Navegue até **configuração\\do computador\\modelos administrativos componentes\\do Windows Windows PowerShell**
3. Clique duas vezes em **Ativar registro em log de módulo**
4. Clique em **habilitado**
5. Na seção Opções, clique em **Mostrar** ao lado de nomes de módulo
6. Digite `*` a janela pop-up para registrar comandos de todos os módulos.
7. Clique em **OK** para definir a política
8. Clique duas vezes em **ativar o log de bloco de script do PowerShell**
9. Clique em **habilitado**
10. Clique em **OK** para definir a política
11. (Somente em computadores ingressados no domínio) Executar `gpupdate` ou aguardar política de grupo processar a política atualizada e aplicar as configurações

Você também pode habilitar a transcrição do PowerShell em todo o sistema por meio de Política de Grupo.

## <a name="next-steps"></a>Próximos passos

[Criar um arquivo de capacidade de função](role-capabilities.md)

[Criar um arquivo de configuração de sessão](session-configurations.md)

## <a name="see-also"></a>Consulte também

[Segurança do WinRM](/powershell/scripting/learn/remoting/winrmsecurity)

[PowerShell ♥ equipe azul](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
