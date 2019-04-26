---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Como Depurar Scripts no ISE do Windows PowerShell
ms.openlocfilehash: b7af2de83a3f796a2057514e36ad8b74367e8ce2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086872"
---
# <a name="how-to-debug-scripts-in-windows-powershell-ise"></a>Como Depurar Scripts no ISE do Windows PowerShell

Este artigo descreve como depurar scripts num computador local, utilizando os recursos de depuração visual do Windows PowerShell Integrated Scripting Environment (ISE).

## <a name="how-to-manage-breakpoints"></a>Como gerir pontos de interrupção

Um ponto de interrupção é um lugar num script designado onde pretende colocar em pausa, para que pode examinar o estado atual de variáveis e o ambiente no qual o script está em execução da operação. Depois do script está em pausa por um ponto de interrupção, pode executar comandos no painel da consola para examinar o estado do seu script.  Pode variáveis de saída ou executar outros comandos. Pode até mesmo modificar o valor de todas as variáveis que estão visíveis para o contexto do script em execução. Após ter examinado o que pretende ver, é possível retomar o funcionamento do script.

Pode definir três tipos de pontos de interrupção no ambiente de depuração do Windows PowerShell:

1. **Ponto de interrupção de linha**. O script faz uma pausa quando a linha designada é atingida durante a operação do script

2. **Ponto de interrupção de variável.** O script faz uma pausa sempre que altera o valor da variável designado.

3. **Ponto de interrupção de comando.** O script faz uma pausa sempre que o comando designado está prestes a ser executado durante a operação do script. Ele pode incluir parâmetros para filtrar ainda mais o ponto de interrupção para apenas a operação que deseja. O comando também pode ser uma função que criou.

Um deles, no ambiente de depuração do Windows PowerShell ISE, apenas pontos de interrupção da linha podem ser definidos utilizando o menu ou os atalhos de teclado. Os outros dois tipos de pontos de interrupção podem ser definidos, mas eles são definidos do painel de consola utilizando o [Set-PSBreakpoint](https://technet.microsoft.com/library/88d2d9ad-17dc-44ae-99aa-f841125b9dc8) cmdlet. Esta secção descreve como efetuar tarefas de depuração no ISE do Windows PowerShell com os menus que estiverem disponíveis e executar uma variedade maior de comandos a partir do painel de consola usando o script.

### <a name="to-set-a-breakpoint"></a>Para definir um ponto de interrupção

Um ponto de interrupção pode ser definido num script apenas depois foi guardado. Com o botão direito a linha em que pretende definir um ponto de interrupção de linha e, em seguida, clique em **Ativar/desativar ponto de interrupção**. Em alternativa, clique na linha em que queira definir um ponto de interrupção de linha, e prima **F9** ou, no **depurar** menu, clique em **Ativar/desativar ponto de interrupção**.

O script seguinte é um exemplo de como pode definir um ponto de interrupção de variável do painel de consola utilizando o [Set-PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420) cmdlet.

```powershell
# This command sets a breakpoint on the Server variable in the Sample.ps1 script.
Set-PSBreakpoint -Script sample.ps1 -Variable Server
```

### <a name="list-all-breakpoints"></a>Lista de todos os pontos de interrupção

Mostra todos os pontos de interrupção na sessão atual do Windows PowerShell.

Sobre o **depurar** menu, clique em **lista de pontos de interrupção**. O script seguinte é um exemplo de como pode listar todos os pontos de interrupção do painel de consola utilizando o [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) cmdlet.

```powershell
# This command lists all breakpoints in the current session.
Get-PSBreakpoint
```

### <a name="remove-a-breakpoint"></a>Remover um ponto de interrupção

Remover um ponto de interrupção elimina-a.

Se acha que poderá querer utilizá-lo novamente mais tarde, considere [desativar um ponto de interrupção](#disable-a-breakpoint) -lo em vez disso.
Com o botão direito a linha em que pretende remover um ponto de interrupção e, em seguida, clique em **Ativar/desativar ponto de interrupção**.
Em alternativa, clique na linha em que pretende remover um ponto de interrupção, e, no **depurar** menu, clique em **Ativar/desativar ponto de interrupção**.
O script seguinte é um exemplo de como remover um ponto de interrupção com um ID especificado a partir do painel de consola utilizando o [Remove-PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) cmdlet.

```powershell
# This command deletes the breakpoint with breakpoint ID 2.
Remove-PSBreakpoint -Id 2
```

### <a name="remove-all-breakpoints"></a>Remover todos os pontos de interrupção

Para remover todos os pontos de interrupção definidos na sessão atual, sobre o **depurar** menu, clique em **remover todos os pontos de interrupção**.

O script seguinte é um exemplo de como remover todos os pontos de interrupção do painel de consola com o [Remove-PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) cmdlet.

```powershell
# This command deletes all of the breakpoints in the current session.
Get-PSBreakpoint | Remove-PSBreakpoint
```

### <a name="disable-a-breakpoint"></a>Desativar um ponto de interrupção

Desativar um ponto de interrupção não remove-lo. ele a desativa até que seja ativado.  Para desativar um ponto de interrupção de linha específica, com o botão direito a linha em que pretende desativar um ponto de interrupção e, em seguida, clique em **desativar ponto de interrupção**. Em alternativa, clique na linha em que pretende desativar um ponto de interrupção, e prima **F9** ou, no **depurar** menu, clique em **desativar ponto de interrupção**. O script seguinte é um exemplo de como pode remover um ponto de interrupção com uma ID especificada do painel de consola utilizando o [Disable-PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) cmdlet.

```powershell
# This command disables the breakpoint with breakpoint ID 0.
Disable-PSBreakpoint -Id 0
```

### <a name="disable-all-breakpoints"></a>Desativar todos os pontos de interrupção

Desativar um ponto de interrupção não remove-lo. ele a desativa até que seja ativado.  Para desativar todos os pontos de interrupção na sessão atual, sobre o **depurar** menu, clique em **desativar todos os pontos de interrupção**. O script seguinte é um exemplo de como pode desativar todos os pontos de interrupção do painel de consola, utilizando o [Disable-PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) cmdlet.

```powershell
# This command disables all breakpoints in the current session.
# You can abbreviate this command as: "gbp | dbp".
Get-PSBreakpoint | Disable-PSBreakpoint
```

### <a name="enable-a-breakpoint"></a>Ativar um ponto de interrupção

Para ativar um ponto de interrupção específico, clique com botão direito a linha em que pretende ativar um ponto de interrupção e, em seguida, clique em **ativar o ponto de interrupção**. Em alternativa, clique na linha em que pretende ativar um ponto de interrupção e, em seguida, prima **F9** ou, no **depurar** menu, clique em **ativar o ponto de interrupção**. O script seguinte é um exemplo de como pode ativar pontos de interrupção específicos do painel de consola utilizando o [Enable-PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) cmdlet.

```powershell
# This command enables breakpoints with breakpoint IDs 0, 1, and 5.
Enable-PSBreakpoint -Id 0, 1, 5
```

### <a name="enable-all-breakpoints"></a>Ativar todos os pontos de interrupção

Para permitir que todos os pontos de interrupção definidos na sessão atual, sobre o **depurar** menu, clique em **ativar todos os pontos de interrupção**. O script seguinte é um exemplo de como pode permitir todos os pontos de interrupção do painel de consola utilizando o [Enable-PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) cmdlet.

```powershell
# This command enables all breakpoints in the current session.
# You can abbreviate the command by using their aliases: "gbp | ebp".
Get-PSBreakpoint | Enable-PSBreakpoint
```

## <a name="how-to-manage-a-debugging-session"></a>Como gerir uma sessão de depuração

Antes de iniciar a depuração, tem de definir uma ou mais pontos de interrupção. Não é possível definir um ponto de interrupção, a menos que o script que deseja depurar é guardado. Para instruções sobre como definir um ponto de interrupção, consulte [como gerir pontos de interrupção](#how-to-manage-breakpoints) ou [conjunto PSBreakpoint](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-psbreakpoint). Depois de iniciar a depuração, não é possível editar um script até que interrompa a depuração. Um script que tenha um ou mais pontos de interrupção definido é guardado automaticamente antes que seja executado.

### <a name="to-start-debugging"></a>Para iniciar a depuração

Prima **F5** ou, na barra de ferramentas, clique nas **executar Script** ícone, ou no **depurar** menu clique **execução/continuar**. O script é executado até que ele encontra o primeiro ponto de interrupção. Ele interrompe a operação aí e realça a linha em que em pausa.

### <a name="to-continue-debugging"></a>Para continuar a depuração

Prima **F5** ou, na barra de ferramentas, clique nas **executar Script** ícone, ou no **depurar** menu, clique em **execução/continuar** ou, no painel da consola, escreva **C** e, em seguida, prima **ENTER**. Isso faz com que o script para continuar a ser executada para o ponto de interrupção seguinte ou para o final do script, se não existem mais pontos de interrupção são encontrados.

### <a name="to-view-the-call-stack"></a>Para ver a pilha de chamadas

A pilha de chamadas apresenta a localização de execução do script atual. Se o script é executado numa função que foi chamada por outra função, em seguida, que é representado na exibição por linhas adicionais na saída. A linha na extremidade inferior mostra o script original e a linha na mesma na qual era chamada de uma função. A próxima fila mostra essa função e a linha na mesma na qual outra função poderá ter chamada.  A linha mais mostra o contexto atual da linha atual no qual o ponto de interrupção está definido.

Embora em pausa, para ver a atual pilha de chamada, prima **CTRL + SHIFT + D** ou, no **depurar** menu, clique em **pilha de chamadas de exibição** ou, no painel da consola, escreva **K**  e, em seguida, prima **ENTER**.

### <a name="to-stop-debugging"></a>Para parar a depuração

Prima **SHIFT-F5** ou, no **depurar** menu, clique em **parar o depurador**, ou, no painel da consola, escreva **p** e, em seguida, prima  **INTRODUZA**.

## <a name="how-to-step-over-step-into-and-step-out-while-debugging"></a>Como passo ao longo, entrar e sair durante a depuração

Etapa é o processo de execução de uma instrução por vez. Pode parar numa linha de código e examinar os valores de variáveis e o estado do sistema. A tabela seguinte descreve as tarefas comuns de depuração como passar ao longo, examinarmos e passar a.

| Depuração de tarefas | Descrição | Como realizá-lo no ISE do PowerShell |
| --- | --- | --- |
| **Avance para** | Executa a instrução atual e, em seguida, termina com a próxima instrução. Se a instrução atual é uma função ou chamada de script, em seguida, os passos de depurador para essa função ou script, caso contrário, ele será interrompido na próxima instrução. | Prima **F11** ou, no **depurar** menu, clique em **entrar**, ou no painel da consola, escreva **S** e prima **ENTER**. |
| **Step Over** | Executa a instrução atual e, em seguida, termina com a próxima instrução. Se a instrução atual é uma função ou chamada de script, em seguida, o depurador executa a função de toda ou o script e parar na próxima instrução após a chamada de função. | Prima **F10** ou, no **depurar** menu, clique em **Pular**, ou no painel da consola, escreva **V** e prima **ENTER**. |
| **Krokovat s Vystoupením** | Passos da função atual e um nível se a função está aninhada acima. Se, no corpo principal, o script é executado no final, ou para o ponto de interrupção seguinte. As instruções ignoradas são executadas, mas não apresentou. | Prima **SHIFT+F11**, ou no **depurar** menu, clique em **Step Out**, ou no painel da consola, escreva **s** e prima **ENTER**. |
| **Continuar** | Continua a execução no final, ou para o ponto de interrupção seguinte. As funções ignoradas e as invocações são executadas, mas não apresentou. | Prima **F5** ou, no **depurar** menu, clique em **execução/continuar**, ou no painel da consola, escreva **C** e prima **ENTER**. |

## <a name="how-to-display-the-values-of-variables-while-debugging"></a>Como exibir os valores de variáveis durante a depuração

Pode exibir os valores atuais das variáveis no script, à medida que avança o código.

### <a name="to-display-the-values-of-standard-variables"></a>Para apresentar os valores das variáveis padrão

Utilize um dos seguintes métodos:

- No painel de Script, coloque o cursor sobre a variável para apresentar o respetivo valor como uma dica de ferramenta.

- No painel da consola, escreva o nome da variável e prima **ENTER**.

Todos os painéis no ISE são sempre no mesmo âmbito. Por isso, enquanto faz a depuração um script, executam os comandos que digitar no painel de consola no âmbito de script. Isto permite-lhe utilizar o painel de consola para localizar os valores das variáveis e chamar funções que são definidas apenas no script.

### <a name="to-display-the-values-of-automatic-variables"></a>Para exibir os valores das variáveis automáticas

Pode usar o método anterior para exibir o valor de quase todas as variáveis, enquanto faz a depuração um script. No entanto, esses métodos não trabalharem para as seguintes variáveis automáticas.

- $_

- $Input

- $MyInvocation

- $PSBoundParameters

- $Args

Se tentar exibir o valor de qualquer uma destas variáveis, obter o valor dessa variável para num pipeline interno o depurador utiliza, não o valor da variável no script. Pode contornar isso para algumas variáveis ($_, $Input, $MyInvocation, $PSBoundParameters e $Args) utilizando o seguinte método:

1. O script, atribua o valor da variável automática para uma nova variável.

2. Apresenta o valor da variável nova, ao pairar o rato sobre a variável nova no painel de Script ou ao escrever a nova variável no painel da consola.

Por exemplo, para exibir o valor da variável $MyInvocation, no script, Atribuímos o valor para uma nova variável, tais como $scriptname e, em seguida, coloque o cursor sobre ou escreva a variável de $scriptname para apresentar o respetivo valor.

```powershell
# In C:\ps-test\MyScript.ps1
$scriptname = $MyInvocation.MyCommand.Path
```

```output
# In the Console Pane:
PS> .\MyScript.ps1
PS> $scriptname
C:\ps-test\MyScript.ps1
```

## <a name="see-also"></a>Veja Também

- [Explorar o ISE do Windows PowerShell](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)