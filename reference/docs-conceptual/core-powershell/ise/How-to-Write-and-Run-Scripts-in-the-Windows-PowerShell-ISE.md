---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Como Escrever e Executar Scripts no ISE do Windows PowerShell
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
ms.openlocfilehash: 4d7c5352ef1dac6f63a50433676068f83a920db5
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/07/2018
ms.locfileid: "34483122"
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a>Como Escrever e Executar Scripts no ISE do Windows PowerShell

Este tópico descreve como criar, editar, executar e guardar scripts no painel de Script.

## <a name="how-to-create-and-run-scripts"></a>Como criar e executar scripts

Pode abrir e editar ficheiros do Windows PowerShell no painel de Script. Tipos de ficheiro específicos de interesse no Windows PowerShell são ficheiros de script (. ps1), ficheiros de dados do script (. psd1) e os ficheiros do módulo de script (. psm1). Estes tipos de ficheiro são sintaxe colorido no editor do painel de Script. Outros tipos de ficheiro comuns que poderá abrir no painel de Script são ficheiros de configuração (.ps1xml), ficheiros XML e ficheiros de texto.

> [!NOTE]
> A política de execução do Windows PowerShell determina se pode executar scripts e carga do Windows PowerShell perfis e ficheiros de configuração. A política de execução predefinidas, restrito, impede que todos os scripts em execução e impede que os perfis de carregamento. Para alterar a política de execução para permitir que os perfis a carregar e ser utilizado, consulte [Set-ExecutionPolicy [PSITPro5_Security]](https://technet.microsoft.com/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) e [about_Signing [v4]](https://technet.microsoft.com/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).

### <a name="to-create-a-new-script-file"></a>Para criar um novo ficheiro de script

Na barra de ferramentas, clique em **novo** , ou no **ficheiro** menu, clique em **novo**. O ficheiro criado é apresentado num separador novo do ficheiro no separador atual do PowerShell. Lembre-se de que os separadores de PowerShell apenas são visíveis quando existirem mais do que um. Por predefinição é criado um ficheiro de script de tipo (. ps1), mas podem ser guardado com um novo nome e extensão. Podem ser criados vários ficheiros de script no mesmo separador do PowerShell.

### <a name="to-open-an-existing-script"></a>Para abrir um script existente

Na barra de ferramentas, clique em **abra**, ou no **ficheiro** menu, clique em **abra**. No **abrir** diálogo caixa, selecione o ficheiro que pretende abrir. É apresentado o ficheiro aberto num novo separador.

### <a name="to-close-a-script-tab"></a>Para fechar um separador de script

Clique no separador de script do script que pretende fechar e, em seguida, efetue um dos seguintes procedimentos:

1. Clique em de **fechar** ícone (X) no separador de script.

2. No **ficheiro** menu, clique em **fechar**.

Se o ficheiro tiver sido alterado desde que foi guardada pela última vez, lhe for pedido que guarde ou elimine-lo.

### <a name="to-display-the-file-path"></a>Para apresentar o caminho do ficheiro

No separador ficheiros, aponte para o nome de ficheiro. O caminho completamente qualificado para o ficheiro de script é apresentada numa descrição.

### <a name="to-run-a-script"></a>Para executar um script

Na barra de ferramentas, clique em **executar Script**, ou no **ficheiro** menu, clique em **executar**.

### <a name="to-run-a-portion-of-a-script"></a>Para executar uma parte de um script

1. No painel de Script, selecione uma parte de um script.

2. No **ficheiro** menu, clique em **executar seleção**, ou na barra de ferramentas, clique em **executar seleção**.

### <a name="to-stop-a-running-script"></a>Para parar um script em execução

Na barra de ferramentas, clique em **operação parar**, prima CTRL + BREAK, ou no **ficheiro** menu, clique em **operação parar**. Premir **CTRL + C** também funciona, exceto se algum texto atualmente selecionado, caso em que **CTRL + C** mapeia para a função de cópia para o texto seleccionado.

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a>Como escrever e editar o texto no painel de Script

Utilize os seguintes passos para editar o texto no painel de Script. Pode copiar, cortar, colar, localizar e substituir texto. Também pode anular e Refazer a última ação que apenas efetuada. Os atalhos de teclado para efetuar estas ações são os mesmos que são utilizados para todas as aplicações do Windows.

### <a name="to-enter-text-in-the-script-pane"></a>Introduza o texto no painel de Script

1. Mova o cursor para o painel de Script ao clicar em qualquer lugar no painel de Script, ou clicando **aceda ao painel de Script** no **vista** menu.

2. Crie um script. Sintaxe coloração e conclusão de separador tornar esta uma experiência mais rica no ISE do Windows PowerShell.

3. Consulte [como conclusão de separador de utilização no painel de Script e painel de consola](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) para obter detalhes sobre como utilizar a funcionalidade de conclusão de separador para ajudar a escrever.

### <a name="to-find-text-in-the-script-pane"></a>Para localizar texto no painel de Script

1. Para localizar texto em qualquer lugar, prima **CTRL + F** ou, no **editar** menu, clique em **localizar no Script**.

2. Para localizar texto após o cursor, prima **F3** ou, no **editar** menu, clique em **Localizar seguinte script**.

3. Para localizar texto antes do cursor, prima **SHIFT + F3** ou, no **editar** menu, clique em **Localizar anterior no Script**.

### <a name="to-find-and-replace-text-in-the-script-pane"></a>Para localizar e substituir texto no painel de Script

Prima **CTRL + H** ou, no **editar** menu, clique em **substituir no Script**. Introduza o texto que pretende localizar e o texto com o qual pretende substituí-lo e, em seguida, prima **ENTER**.

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a>Ir para uma determinada linha de texto no painel de Script

1. No painel de Script, prima **CTRL + G** ou, no **editar** menu, clique em **aceda a linha**.

2. Introduza um número de linha.

### <a name="to-copy-text-in-the-script-pane"></a>Para copiar o texto no painel de Script

1. No painel de Script, selecione o texto que pretende copiar.

2. Prima **CTRL + C** ou, na barra de ferramentas, clique em de **cópia** ícone, ou no **editar** menu, clique em **cópia**.

### <a name="to-cut-text-in-the-script-pane"></a>Ao cortar texto no painel de Script

1. No painel de Script, selecione o texto que pretende cortar.

2. Prima **CTRL + X** ou, na barra de ferramentas, clique em de **Cortar** ícone, ou no **editar** menu, clique em **Cortar**.

### <a name="to-paste-text-into-the-script-pane"></a>Colar o texto no painel de Script

Prima **CTRL + V** ou, na barra de ferramentas, clique em de **colar** ícone, ou no **editar** menu, clique em **colar**.

### <a name="to-undo-an-action-in-the-script-pane"></a>Para anular uma ação no painel de Script

Prima **CTRL + Z** ou, na barra de ferramentas, clique em de **anular** ícone, ou no **editar** menu, clique em **anular**.

### <a name="to-redo-an-action-in-the-script-pane"></a>Refazer uma ação no painel de Script

Prima **CTRL + Y** ou, na barra de ferramentas, clique em de **Refazer** ícone, ou no **editar** menu, clique em **Refazer**.

## <a name="how-to-save-a-script"></a>Como guardar um script

Utilize os seguintes passos para guardar e nome de um script. Um asterisco é apresentado junto ao nome do script para marcar um ficheiro que não foi guardado, desde que foi alterado. O asterisco desaparece quando o ficheiro é guardado.

### <a name="to-save-a-script"></a>Para guardar um script

Prima **CTRL + G** ou, na barra de ferramentas, clique em de **guardar** ícone, ou no **ficheiro** menu, clique em **guardar**.

### <a name="to-save-and-name-a-script"></a>Para guardar e nome de um script

1. No **ficheiro** menu, clique em **guardar como**. O **guardar como** será apresentada a caixa de diálogo.

2. No **nome de ficheiro** box, introduza um nome para o ficheiro.

3. No **guardar como tipo** caixa, selecione um tipo de ficheiro. Por exemplo, no **guardar como tipo** caixa, selecione ' œPowerShell Scripts (\* . ps1)'.

4. Clique em **Guardar**.

### <a name="to-save-a-script-in-ascii-encoding"></a>Para guardar um script num codificação ASCII

Por predefinição, ISE do Windows PowerShell guarda novos ficheiros de script (. ps1), ficheiros de dados do script (. psd1) e os ficheiros do módulo de script (. psm1) como Unicode (BigEndianUnicode) por predefinição. Â para guardar um script na codificação outro, tais como ASCII (ANSI), utilize o **guardar** ou **SaveAs** os métodos no [$psISE.CurrentFile](https://technet.microsoft.com/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile) objeto.

O comando seguinte guarda um script novo como MyScript.ps1 com codificação ASCII.

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

O seguinte comando substitui o ficheiro de script atual com um ficheiro com o mesmo nome mas com codificação ASCII.

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

O seguinte comando obtém a codificação do ficheiro atual.

```powershell
$psISE.CurrentFile.encoding
```

ISE do Windows PowerShell suporta as seguintes opções de codificação: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 e predefinido. O valor da opção predefinida varia de acordo com o sistema.

ISE do Windows PowerShell não altera a codificação de scripts que foram criadas por em outros editores, mesmo quando utiliza o guardar ou guardar como comandos no ISE do Windows PowerShell.

## <a name="see-also"></a>Consulte Também

- [Explorar o ISE do Windows PowerShell](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)