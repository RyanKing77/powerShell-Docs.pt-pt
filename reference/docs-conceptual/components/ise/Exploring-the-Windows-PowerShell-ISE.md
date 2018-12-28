---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Explorar o ISE do Windows PowerShell
ms.assetid: e0d2c6e8-5126-40e7-a1e1-d1cff29fe94a
ms.openlocfilehash: 059651f159fb2636a93167709134788e90d062b8
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405370"
---
# <a name="exploring-the-windows-powershell-ise"></a>Explorar o ISE do Windows PowerShell

Pode utilizar o Windows PowerShell® Integrated Scripting Environment (ISE) para criar, executar e depurar os comandos e scripts. ISE do Windows PowerShell é composta por barra de menus, guias do Windows PowerShell, a barra de ferramentas, guias de script, um painel de Script, um painel de consola, uma barra de estado, um controlo de deslize do tamanho do texto e ajuda sensível ao contexto.

> [!NOTE]
> Iniciando com o Windows PowerShell ISE 3.0, o comando e painéis de saída foram combinados num único painel de consola.

## <a name="menu-bar"></a>Barra de menus

Barra de menus contém os **arquivo**, **editar**, **vista**, **ferramentas**, **depurar**,  **Complementos**, e **ajudar** menus. Os botões os menus permitem-lhe executar tarefas relacionadas com os scripts de escrever e em execução e execução de comandos no ISE do Windows PowerShell. Além disso, um [ferramenta do suplemento](../../core-powershell/ise/The-ISEAddOnTool-Object.md) pode ser colocado na barra de menus, ao executar scripts que utilizam o [a hierarquia do modelo de objeto ISE](../../core-powershell/ise/The-ISE-Object-Model-Hierarchy.md).

> [!NOTE]
> No Windows PowerShell ISE 2.0, o **ferramentas** e **suplementos** menus não estavam presentes.

## <a name="windows-powershell-tabs"></a>Guias do Windows PowerShell

Um separador do Windows PowerShell é o ambiente no qual um script do Windows PowerShell é executado. Pode abrir novas guias do Windows PowerShell no ISE do Windows PowerShell, para criar ambientes separados no seu computador local ou em computadores remotos. Pode ter um máximo de oito PowerShell separadores abrir em simultâneo.

## <a name="toolbar"></a>Barra de ferramentas

Os botões seguintes estão localizados na barra de ferramentas.

|Botão|Função|
|----------|------------|
|**Novo**|É aberto um novo script.|
|**Aberto**|Abre-se de um script existente ou um ficheiro.|
|**Guardar**|Guarda um script ou arquivo.|
|**Operações de corte**|Reduz o texto selecionado e copia-o para a área de transferência.|
|**Cópia**|Copia o texto selecionado para a área de transferência.|
|**Paste**|Cola o conteúdo da área de transferência ao local do cursor.|
|**Limpar o painel de resultados**|Limpa a todo o conteúdo no painel de saída.|
|**Anular**|Reverte a ação que acabou de executar.|
|**Refazer**|Executa a ação que foi anulada apenas.|
|**Executar Script**|Executa um script.|
|**Executar seleção**|Executa uma parte selecionada de um script.|
|**Parar a execução**|Interrompe um script que está em execução.|
|**Novo separador do PowerShell remoto**|Cria um novo separador do PowerShell que estabelece uma sessão num computador remoto. Uma caixa de diálogo é apresentada e pede-lhe para introduzir os detalhes necessários para estabelecer a ligação remota.|
|**Iniciar PowerShell.exe**|Abre a consola do PowerShell.|
|**Mostrar parte superior do painel de Script**|Move o painel de scripts na parte superior na exibição.|
|**Mostrar painel de Script correto**|Move o painel de scripts para a direita na exibição.|
|**Mostrar painel de Script maximizada**|Maximiza o painel de scripts.|

## <a name="script-tab"></a>Separador de script

Apresenta o nome do script que está a editar. Pode clicar numa guia de script para selecionar o script que pretende editar.

Quando apontar para o separador de script, o caminho totalmente qualificado para o ficheiro de script é apresentado numa descrição.

## <a name="script-pane"></a>Painel de script

Permite-lhe criar e executar scripts. Pode abrir, editar e executar scripts existentes no painel de Script.

## <a name="output-pane"></a>Painel de resultados

Apresenta os resultados dos comandos e scripts que executou. Também pode copiar e limpar o conteúdo no painel de saída.

## <a name="command-pane"></a>Painel de comando

Permite-lhe escrever os comandos. Pode executar um comando de uma linha ou um comando de várias linhas no painel de comando. Prima SHIFT + ENTER para inserir cada linha de um comando de várias linhas e prima ENTER depois da última linha a executar o comando com várias linhas. Linha de comandos apresentada na parte superior do painel de comando mostra o caminho para o diretório de trabalho atual.

## <a name="status-bar"></a>Barra de status

Permite-lhe ver se os comandos e scripts que executar são completas. É a barra de status na parte inferior da tela. Selecionado partes das mensagens de erro são apresentadas na barra de status.

## <a name="text-size-slider"></a>Controlo de deslize do tamanho do texto

Aumenta ou diminui o tamanho do texto na tela.

## <a name="help"></a>Ajuda

Ajuda para o Windows PowerShell ISE está disponível na Web na Biblioteca TechNet. Pode abrir a ajuda ao clicar **ajuda do Windows PowerShell ISE** no **ajudar** menu ou ao premir a tecla F1 em qualquer lugar, exceto quando o cursor está no nome de um cmdlet no painel de Script ou no painel da consola. Do **ajudar** menu também pode executar o cmdlet Update-Help e exibir a janela de comando que ajuda a construir comandos, que mostra todos os parâmetros para um cmdlet e permitindo que preencher os parâmetros num formulário de fácil de usar.

## <a name="see-also"></a>Consulte Também

- [Introdução ao ISE do Windows PowerShell](../../core-powershell/ise/Introducing-the-Windows-PowerShell-ISE.md)