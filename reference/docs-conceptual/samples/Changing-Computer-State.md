---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Alterar o Estado do Computador
ms.openlocfilehash: de3e31e358548943a015b7bba275c4461202b20f
ms.sourcegitcommit: d1ba596f9e0d4df9565601a70687a126d535c917
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/05/2019
ms.locfileid: "70386289"
---
# <a name="changing-computer-state"></a>Alterar o Estado do Computador

Para redefinir um computador no Windows PowerShell, use uma ferramenta de linha de comando padrão, a classe WMI ou CIM. Embora você esteja usando o Windows PowerShell somente para executar a ferramenta, aprender a alterar o estado de energia de um computador no Windows PowerShell ilustra alguns dos detalhes importantes sobre como trabalhar com ferramentas externas no Windows PowerShell.

## <a name="locking-a-computer"></a>Bloqueando um computador

A única maneira de bloquear um computador diretamente com as ferramentas padrão disponíveis é chamar a função **LockWorkstation ()** no **user32. dll**:

```
rundll32.exe user32.dll,LockWorkStation
```

Esse comando bloqueia imediatamente a estação de trabalho. Ele usa o *rundll32. exe*, que executa as DLLs do Windows (e salva suas bibliotecas para uso repetido) para executar user32. dll, uma biblioteca de funções de gerenciamento do Windows.

Quando você bloqueia uma estação de trabalho enquanto a troca rápida de usuário está habilitada, como no Windows XP, o computador exibe a tela de logon do usuário em vez de iniciar a proteção do usuário atual.

Para desligar sessões específicas em um Terminal Server, use a ferramenta de linha de comando **tsshutdn. exe** .

## <a name="logging-off-the-current-session"></a>Fazendo logoff da sessão atual

Você pode usar várias técnicas diferentes para fazer logoff de uma sessão no sistema local. A maneira mais simples é usar a ferramenta de linha de comando Área de Trabalho Remota/serviços de terminal, **logoff. exe** (para obter detalhes, no prompt do Windows PowerShell, digite **logoff/?** ). Para fazer logoff da sessão ativa atual, digite **logoff** sem argumentos.

Você também pode usar a ferramenta **Shutdown. exe** com sua opção de logoff:

```
shutdown.exe -l
```

Outra opção é usar o WMI. A classe Win32_OperatingSystem tem um método Win32Shutdown. Invocar o método com o sinalizador 0 inicia o logoff:

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

Para obter mais informações e para encontrar outros recursos do método Win32Shutdown, consulte "método Win32Shutdown da classe Win32_OperatingSystem" no MSDN.

Por fim, você pode usar o CIM com a mesma classe Win32_OperatingSystem, conforme descrito acima no método WMI.

```powershell
Get-CIMInstance -Classname Win32_OperatingSystem | Invoke-CimMethod -MethodName Shutdown
```

## <a name="shutting-down-or-restarting-a-computer"></a>Desligando ou reiniciando um computador

O desligamento e a reinicialização de computadores geralmente são os mesmos tipos de tarefa. As ferramentas que desligam um computador geralmente também o reiniciam, e vice-versa. Há duas opções simples para reiniciar um computador do Windows PowerShell. Use tsshutdn. exe ou Shutdown. exe com argumentos apropriados. Você pode obter informações de uso detalhadas de **tsshutdn. exe/?** ou **Shutdown. exe/?** .

Também é possível executar operações de desligamento e reinicialização diretamente do Windows PowerShell.

Para desligar o computador, use o comando Stop-Computer

```powershell
Stop-Computer
```

Para reiniciar o sistema operacional, use o comando Restart-Computer

```powershell
Restart-Computer
```

Para forçar uma reinicialização imediata do computador, use o parâmetro-Force.

```powershell
Restart-Computer -Force
```
