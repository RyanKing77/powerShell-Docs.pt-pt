---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Como Depurar Scripts no ISE do Windows PowerShell
ms.openlocfilehash: b7af2de83a3f796a2057514e36ad8b74367e8ce2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="how-to-debug-scripts-in-windows-powershell-ise"></a>Como Depurar Scripts no ISE do Windows PowerShell

Este artigo descreve como depurar scripts num computador local, utilizando as funcionalidades de depuração visual do Windows PowerShell Integrated Scripting Environment (ISE).

## <a name="how-to-manage-breakpoints"></a>Como gerir pontos de interrupção

Um ponto de interrupção é um designado lugar para cima num script onde pretende colocar em pausa para que pode examinar o estado atual de variáveis e o ambiente no qual o script está em execução da operação. Assim que o script está em pausa por um ponto de interrupção, pode executar comandos no painel de consola para examinar o estado do seu script.  Pode variáveis de saída ou executar outros comandos. Ainda pode modificar o valor das eventuais variáveis que estão visíveis para o contexto do script em execução. Depois de ter examinadas pretende ver, pode retomar o funcionamento do script.

Pode definir os três tipos de pontos de interrupção no ambiente de depuração do Windows PowerShell:

1. **Ponto de interrupção de linha**. O script interrompe quando for atingida a linha designada durante a operação do script

2. **Ponto de interrupção de variável.** Interrompe o script sempre que o valor da variável de designado é alterado.

3. **Ponto de interrupção de comando.** Interrompe o script sempre que o comando designado está prestes a ser executado durante a operação do script. Pode incluir parâmetros para o ponto de interrupção para apenas a operação que pretende continuar a filtrar. O comando também pode ser uma função que criou.

No ambiente de depuração do ISE do Windows PowerShell, apenas pontos de interrupção da linha podem ser definidos utilizando o menu ou os atalhos de teclado. Os outros dois tipos de pontos de interrupção podem ser definidos, mas estão definidas no painel de consola utilizando o [conjunto PSBreakpoint](https://technet.microsoft.com/library/88d2d9ad-17dc-44ae-99aa-f841125b9dc8) cmdlet. Esta secção descreve como efetuar tarefas de depuração no ISE do Windows PowerShell, utilizando os menus, quando disponíveis e executar uma vasta gama de comandos a partir do painel de consola através do scripting.

### <a name="to-set-a-breakpoint"></a>Para definir um ponto de interrupção

Um ponto de interrupção pode ser definido num script apenas depois de foi guardado. A linha onde pretende definir um ponto de interrupção de linha e, em seguida, clique com o botão direito **Ativar/desativar ponto de interrupção**. Em alternativa, clique na linha onde pretende definir um ponto de interrupção de linha, e prima **F9** ou, no **depurar** menu, clique em **Ativar/desativar ponto de interrupção**.

O script seguinte é um exemplo de como pode definir um ponto de interrupção de variável de painel de consola utilizando o [conjunto PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420) cmdlet.

```powershell
# This command sets a breakpoint on the Server variable in the Sample.ps1 script.
Set-PSBreakpoint -Script sample.ps1 -Variable Server
```

### <a name="list-all-breakpoints"></a>Listar todos os pontos de interrupção

Mostra todos os pontos de interrupção na sessão atual do Windows PowerShell.

No **depurar** menu, clique em **lista de pontos de interrupção**. O script seguinte é um exemplo de como pode listar todos os pontos de interrupção no painel de consola utilizando o [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) cmdlet.

```powershell
# This command lists all breakpoints in the current session.
Get-PSBreakpoint
```

### <a name="remove-a-breakpoint"></a>Remover um ponto de interrupção

Remover um ponto de interrupção elimina.

Se considerar que poderá pretender utilizá-lo novamente mais tarde, considere [desativar um ponto de interrupção](#disable-a-breakpoint) -lo em vez disso.
Clique com o botão direito a linha em que pretende remover um ponto de interrupção e, em seguida, clique em **Ativar/desativar ponto de interrupção**.
Ou, clique na linha em que pretende remover um ponto de interrupção, e o **depurar** menu, clique em **Ativar/desativar ponto de interrupção**.
O script seguinte é um exemplo de como remover um ponto de interrupção com um ID especificado a partir do painel de consola utilizando o [remover PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) cmdlet.

```powershell
# This command deletes the breakpoint with breakpoint ID 2.
Remove-PSBreakpoint -Id 2
```

### <a name="remove-all-breakpoints"></a>Remover todos os pontos de interrupção

Para remover todos os pontos de interrupção definidos na sessão atual, o **depurar** menu, clique em **remover todos os pontos de interrupção**.

O script seguinte é um exemplo de como remover todos os pontos de interrupção do painel de consola utilizando o [remover PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) cmdlet.

```powershell
# This command deletes all of the breakpoints in the current session.
Get-PSBreakpoint | Remove-PSBreakpoint
```

### <a name="disable-a-breakpoint"></a>Desativar um ponto de interrupção

Desativar um ponto de interrupção não removê-lo; -Desativa-lo até que seja ativado.  Para desativar um ponto de interrupção de linha específico, clique com botão direito a linha em que pretende desativar um ponto de interrupção e, em seguida, clique em **desativar ponto de interrupção**. Em alternativa, clique na linha onde pretende desativar um ponto de interrupção, e prima **F9** ou, no **depurar** menu, clique em **desativar ponto de interrupção**. O script seguinte é um exemplo de como pode remover um ponto de interrupção com um ID especificado no painel de consola utilizando o [desativar PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) cmdlet.

```powershell
# This command disables the breakpoint with breakpoint ID 0.
Disable-PSBreakpoint -Id 0
```

### <a name="disable-all-breakpoints"></a>Desative todos os pontos de interrupção

Desativar um ponto de interrupção não removê-lo; -Desativa-lo até que seja ativado.  Desativar a todos os pontos de interrupção na sessão atual, no **depurar** menu, clique em **desative todos os pontos de interrupção**. O script seguinte é um exemplo de como pode desativar todos os pontos de interrupção no painel de consola, utilizando o [desativar PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) cmdlet.

```powershell
# This command disables all breakpoints in the current session.
# You can abbreviate this command as: "gbp | dbp".
Get-PSBreakpoint | Disable-PSBreakpoint
```

### <a name="enable-a-breakpoint"></a>Ativar um ponto de interrupção

Para ativar um ponto de interrupção específico, clique com botão direito a linha onde pretende ativar um ponto de interrupção e, em seguida, clique em **ativar o ponto de interrupção**. Em alternativa, clique na linha onde pretende ativar um ponto de interrupção e, em seguida, prima **F9** ou, no **depurar** menu, clique em **ativar o ponto de interrupção**. O script seguinte é um exemplo de como pode ativar a pontos de interrupção específicos no painel de consola utilizando o [ativar PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) cmdlet.

```powershell
# This command enables breakpoints with breakpoint IDs 0, 1, and 5.
Enable-PSBreakpoint -Id 0, 1, 5
```

### <a name="enable-all-breakpoints"></a>Ativar todos os pontos de interrupção

Para ativar todos os pontos de interrupção definidos na sessão atual, o **depurar** menu, clique em **ativar todos os pontos de interrupção**. O script seguinte é um exemplo de como pode permitir todos os pontos de interrupção no painel de consola utilizando o [ativar PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) cmdlet.

```powershell
# This command enables all breakpoints in the current session.
# You can abbreviate the command by using their aliases: "gbp | ebp".
Get-PSBreakpoint | Enable-PSBreakpoint
```

## <a name="how-to-manage-a-debugging-session"></a>Como gerir uma sessão de depuração

Antes de iniciar a depuração, tem de definir uma ou mais pontos de interrupção. Não é possível definir um ponto de interrupção, a menos que o script que pretende depurar é guardado. Para instruções sobre como definir um ponto de interrupção, consulte [como gerir pontos de interrupção](#how-to-manage-breakpoints) ou [conjunto PSBreakpoint](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-psbreakpoint). Depois de iniciar a depuração, não é possível editar um script até que interrompa a depuração. Um script que tem um ou mais pontos de interrupção definido é guardado automaticamente antes de ser executada.

### <a name="to-start-debugging"></a>Para iniciar a depuração

Prima **F5** ou, na barra de ferramentas, clique em de **executar Script** ícone, ou no **depurar** menu clique **executar/continuar**. O script é executado até encontrar o primeiro ponto de interrupção. Interrompe a operação aí e realça a linha em que em pausa.

### <a name="to-continue-debugging"></a>Para continuar a depuração

Prima **F5** ou, na barra de ferramentas, clique em de **executar Script** ícone, ou no **depurar** menu, clique em **executar/continuar** ou, no painel de consola, escreva **C** e, em seguida, prima **ENTER**. Isto faz com que o script continuar a executar para o próximo ponto de interrupção ou ao fim do script se forem encontrados não existem mais pontos de interrupção.

### <a name="to-view-the-call-stack"></a>Para ver a pilha de chamadas

A pilha de chamadas apresenta atual executar localização no script. Se o script está em execução numa função que foi chamada por uma função diferente, em seguida, que é representado na apresentação por linhas adicionais na saída. A linha na parte inferior mais apresenta o script original e a linha no mesmo em que uma função foi chamada. O seguinte linha segurança mostra que funcionam e a linha na mesma na qual outra função poderá ter sido chamada.  A linha mais alto mostra o contexto atual da linha atual no qual o ponto de interrupção está definido.

Enquanto está em pausa, para ver a pilha de chamadas atual, prima **CTRL + SHIFT + D** ou, no **depurar** menu, clique em **pilha de chamadas de apresentação** ou, no painel de consola, escreva **K**  e, em seguida, prima **ENTER**.

### <a name="to-stop-debugging"></a>Para parar a depuração

Prima **SHIFT F5** ou, no **depurar** menu, clique em **parar o depurador**, ou, no painel de consola, escreva **Q** e, em seguida, prima  **INTRODUZA**.

## <a name="how-to-step-over-step-into-and-step-out-while-debugging"></a>Como passo ao longo, avance para e passo durante a depuração

Avance é o processo de execução de uma instrução de cada vez. Pode parar numa linha de código e examinar os valores das variáveis e o estado do sistema. A tabela seguinte descreve as tarefas comuns de depuração como avance através de, avance para e avance.

| Tarefa de depuração | Descrição | Como fazê-lo no ISE do PowerShell |
| --- | --- | --- |
| **Avance para** | Executa a instrução atual e, em seguida, interrompe a seguinte instrução. Se a instrução atual é uma função ou chamada de script, em seguida, os passos de depurador para essa função ou script, caso contrário, interrompe a seguinte instrução. | Prima **F11** ou, no **depurar** menu, clique em **para o passo**, ou no painel de consola, escreva **S** e prima **ENTER**. |
| **Passo ao longo do** | Executa a instrução atual e, em seguida, interrompe a seguinte instrução. Se a instrução atual é uma função ou chamada de script, em seguida, o depurador executa a função de toda ou script e interrompe a seguinte instrução após a chamada de função. | Prima **F10** ou, no **depurar** menu, clique em **passo ao longo do**, ou no painel de consola, escreva **V** e prima **ENTER**. |
| **Passo** | Passos sem a função atual e agregar um nível se a função está aninhada. Se, no corpo do principal, o script é executado para o fim ou para o próximo ponto de interrupção. As instruções ignoradas são executadas, mas não stepped através de. | Prima **SHIFT + F11**, ou no **depurar** menu, clique em **passo saída**, ou no painel de consola, escreva **Nã** e prima **ENTER**. |
| **Continuar** | Continua a execução para o fim ou para o ponto de interrupção seguinte. As funções ignoradas e invocações são executadas, mas não stepped através de. | Prima **F5** ou, no **depurar** menu, clique em **executar/continuar**, ou no painel de consola, escreva **C** e prima **ENTER**. |

## <a name="how-to-display-the-values-of-variables-while-debugging"></a>Como apresentar os valores das variáveis durante a depuração

Pode apresentar os valores atuais de variáveis no script como seguir o código.

### <a name="to-display-the-values-of-standard-variables"></a>Para apresentar os valores das variáveis padrão

Utilize um dos seguintes métodos:

- No painel de Script, coloque o cursor sobre a variável para apresentar o respetivo valor como uma descrição.

- No painel de consola, escreva o nome da variável e prima **ENTER**.

Todos os painéis no ISE são sempre no mesmo âmbito. Por conseguinte, enquanto está a depurar um script, executam os comandos que digitar no painel de consola no âmbito de script. Isto permite-lhe utilizar o painel de consola para localizar os valores das variáveis e chamar funções que são definidas apenas no script.

### <a name="to-display-the-values-of-automatic-variables"></a>Para apresentar os valores das variáveis automáticas

Pode utilizar o método anterior para apresentar o valor de quase todas as variáveis enquanto está a depurar o script. No entanto, estes métodos não funcionam para as seguintes variáveis automáticas.

- $_

- $Input

- $MyInvocation

- $PSBoundParameters

- $Args

Se tentar apresentar o valor de qualquer um destas variáveis, obter o valor dessa variável para um pipeline interno do depurador utiliza, não o valor da variável no script. Pode contornar esta para algumas variáveis ($_, $Input, $MyInvocation, $PSBoundParameters e $Args) utilizando o método seguinte:

1. O script, atribua o valor da variável automática para uma nova variável.

2. Apresenta o valor da variável nova, por cima a variável nova no painel de Script ou escrevendo a variável nova no painel de consola.

Por exemplo, para apresentar o valor da variável $MyInvocation, o script, atribua o valor para uma nova variável, tal como $scriptname e, em seguida, coloque o cursor sobre ou escreva a variável de $scriptname para apresentar o respectivo valor.

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

## <a name="see-also"></a>Consulte Também

- [Explorar o ISE do Windows PowerShell](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)