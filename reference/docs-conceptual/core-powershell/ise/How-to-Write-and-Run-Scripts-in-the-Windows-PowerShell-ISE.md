---
ms.date: 08/14/2018
keywords: PowerShell, o cmdlet
title: Como Escrever e Executar Scripts no ISE do Windows PowerShell
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
ms.openlocfilehash: 943752df2ecd3fce715dda0ca7ade97186620560
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133834"
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a>Como Escrever e Executar Scripts no ISE do Windows PowerShell

Este artigo descreve como criar, editar, executar e guardar a scripts no painel de Script.

## <a name="how-to-create-and-run-scripts"></a>Como criar e executar scripts

Pode abrir e editar ficheiros do Windows PowerShell no painel de Script. Tipos de ficheiro específicas de interesse no Windows PowerShell são arquivos de script (. ps1), arquivos de dados de script (. psd1) e arquivos de módulo de script (. psm1). Estes tipos de ficheiro são sintaxe colorido no editor do painel de Script. Outros tipos de ficheiros comuns, que pode abrir o no painel de Script são arquivos de configuração (.ps1xml), arquivos XML e arquivos de texto.

> [!NOTE]
> A política de execução do Windows PowerShell determina se pode executar scripts e carregar ficheiros de configuração e de perfis do Windows PowerShell. A diretiva de execução padrão Restricted, impede que todos os scripts em execução e impede que os perfis de carregamento. Para alterar a diretiva de execução para permitir que os perfis de carga e ser utilizado, consulte [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) e [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).

### <a name="to-create-a-new-script-file"></a>Para criar um novo ficheiro de script

Na barra de ferramentas, clique em **New**, ou no **ficheiro** menu, clique em **New**. O ficheiro criado é apresentado num novo separador do arquivo sob a guia atual do PowerShell. Lembre-se de que as guias do PowerShell só estão visíveis quando há mais do que um. Por predefinição é criado um ficheiro de script de tipo (. ps1), mas pode ser salvo com um novo nome e a extensão. Podem ser criados vários ficheiros de script no mesmo separador do PowerShell.

### <a name="to-open-an-existing-script"></a>Para abrir um script existente

Na barra de ferramentas, clique em **aberto**, ou no **ficheiro** menu, clique em **aberto**. Na **abra** diálogo caixa, selecione o ficheiro que pretende abrir. É apresentado o arquivo aberto num novo separador.

### <a name="to-close-a-script-tab"></a>Para fechar um separador de script

Clique nas **feche** ícone (X) do separador de ficheiro que pretende fechar ou selecione o **ficheiro** menu e clique em **fechar**.

Se o ficheiro foi alterado desde que foi guardado pela última vez, lhe for pedido para guardar ou rejeitá-lo.

### <a name="to-display-the-file-path"></a>Para exibir o caminho de ficheiro

No separador ficheiro, aponte para o nome de ficheiro. O caminho totalmente qualificado para o ficheiro de script é apresentado numa descrição.

### <a name="to-run-a-script"></a>Para executar um script

Na barra de ferramentas, clique em **executar Script**, ou no **ficheiro** menu, clique em **executar**.

### <a name="to-run-a-portion-of-a-script"></a>Para executar uma parte de um script

1. No painel de Script, selecione uma parte de um script.
2. Sobre o **arquivo** menu, clique em **Run Selection**, ou na barra de ferramentas, clique em **Run Selection**.

### <a name="to-stop-a-running-script"></a>Para parar um script em execução

Existem várias formas de parar um script em execução.

- Clique em **operação parar** na barra de ferramentas
- Prima CTRL + BREAK
- Selecione o **arquivo** menu e clique em **parar a operação**.

Premir **CTRL + C** também funciona, a menos que algum texto atualmente selecionado, caso em que **CTRL + C** mapeia para a função de cópia para o texto selecionado.

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a>Como escrever e editar texto no painel de Script

Pode copiar, cortar, colar, localizar e substituir texto no painel de Script. Também pode desfazer e Refazer a última ação que acabou de executar. Os atalhos de teclado para estas ações são os mesmo atalhos utilizados para todos os aplicativos do Windows.

### <a name="to-enter-text-in-the-script-pane"></a>Introduza o texto no painel de Script

1. Mover o cursor para o painel de scripts ao clicar em qualquer lugar no painel de Script, ou ao clicar **vá para Painel de Script** no **vista** menu.
2. Crie um script. Sintaxe colorida e conclusão de tabulação fornecem uma experiência mais rica de edição no ISE do Windows PowerShell.
3. Ver [como uso de conclusão de tabulação no painel de Script e o painel de consola](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) para obter detalhes sobre como utilizar a funcionalidade de conclusão de separador para ajudar a escrever.

### <a name="to-find-text-in-the-script-pane"></a>Para localizar texto no painel de Script

1. Para localizar o texto em qualquer lugar, prima **CTRL + F** ou, no **editar** menu, clique em **encontrar no Script**.
2. Para localizar o texto após o cursor, prima **F3** ou, no **editar** menu, clique em **Localizar seguinte no Script**.
3. Para localizar texto antes do cursor, prima **SHIFT+F3** ou, no **editar** menu, clique em **encontrar anteriores no Script**.

### <a name="to-find-and-replace-text-in-the-script-pane"></a>Para localizar e substituir textos no painel de Script

Prima **CTRL + H** ou, no **editar** menu, clique em **substituir no Script**. Introduza o texto que pretende para localizar e o texto de substituição, em seguida, prima **ENTER**.

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a>Para ir para uma determinada linha de texto no painel de Script

1. No painel de Script, prima **CTRL + G** ou, no **editar** menu, clique em **vá para a linha**.

2. Introduza um número de linha.

### <a name="to-copy-text-in-the-script-pane"></a>Para copiar o texto no painel de Script

1. No painel de Script, selecione o texto que pretende copiar.

2. Prima **CTRL + C** ou, na barra de ferramentas, clique nas **cópia** ícone, ou no **editar** menu, clique em **cópia**.

### <a name="to-cut-text-in-the-script-pane"></a>Cortar o texto no painel de Script

1. No painel de Script, selecione o texto que pretende cortar.
2. Prima **CTRL + X** ou, na barra de ferramentas, clique nas **Cortar** ícone, ou no **editar** menu, clique em **Cortar**.

### <a name="to-paste-text-into-the-script-pane"></a>Colar o texto no painel de Script

Prima **CTRL + V** ou, na barra de ferramentas, clique nas **colar** ícone, ou no **editar** menu, clique em **colar**.

### <a name="to-undo-an-action-in-the-script-pane"></a>Para anular uma ação no painel de Script

Prima **CTRL + Z** ou, na barra de ferramentas, clique nas **anular** ícone, ou no **editar** menu, clique em **anular**.

### <a name="to-redo-an-action-in-the-script-pane"></a>Refazer uma ação no painel de Script

Prima **CTRL + Y** ou, na barra de ferramentas, clique nas **Refazer** ícone, ou no **editar** menu, clique em **Refazer**.

## <a name="how-to-save-a-script"></a>Como guardar um script

Um asterisco é apresentado junto ao nome do script para marcar um arquivo que ainda não foram guardado, desde que foi alterada. O asterisco desaparece quando o ficheiro é guardado.

### <a name="to-save-a-script"></a>Para guardar um script

Prima **CTRL + S** ou, na barra de ferramentas, clique nas **guardar** ícone, ou no **ficheiro** menu, clique em **guardar**.

### <a name="to-save-and-name-a-script"></a>Para guardar e nome de um script

1. Sobre o **arquivo** menu, clique em **guardar como**. O **guardar como** será apresentada a caixa de diálogo.
2. Na **nome de ficheiro** , introduza um nome para o ficheiro.
3. Na **guardar como tipo** caixa, selecione um tipo de ficheiro. Por exemplo, no **guardar como tipo** caixa, selecione "Scripts do PowerShell (\*. ps1)".
4. Clique em **Guardar**.

### <a name="to-save-a-script-in-ascii-encoding"></a>Para guardar um script na codificação ASCII

Por predefinição, o ISE do Windows PowerShell salva novos arquivos de script (. ps1), arquivos de dados de script (. psd1) e arquivos de módulo de script (. psm1) como Unicode (BigEndianUnicode) por predefinição. Â para guardar um script em outra codificação, como o ASCII (ANSI), utilize o **salvar** ou **SaveAs** métodos no [$psISE.CurrentFile](the-ise-object-model-hierarchy.md) objeto.

O comando seguinte guarda um novo script como MyScript.ps1 com codificação ASCII.

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

O comando seguinte substitui o ficheiro de script atual com um ficheiro com o mesmo nome, mas com codificação ASCII.

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

O comando seguinte obtém a codificação do ficheiro atual.

```powershell
$psISE.CurrentFile.encoding
```

ISE do Windows PowerShell suporta as seguintes opções de codificação: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 e padrão. O valor da opção predefinida varia de acordo com o sistema.

ISE do Windows PowerShell não altera a codificação de ficheiros de script, quando utiliza o guardar ou guardar como comandos.

## <a name="see-also"></a>Consulte Também

- [Explorar o ISE do Windows PowerShell](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
