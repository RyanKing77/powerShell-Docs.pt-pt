---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: Explorar o ISE do Windows PowerShell
ms.assetid: e0d2c6e8-5126-40e7-a1e1-d1cff29fe94a
ms.openlocfilehash: 979209d4b200728b7e78e341bb9595741d2b8e68
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2017
---
# <a name="exploring-the-windows-powershell-ise"></a>Explorar o ISE do Windows PowerShell
Pode utilizar o Windows PowerShell® Integrated Scripting Environment (ISE) para criar, executar e comandos e scripts de depuração. O ISE do Windows PowerShell é constituído por barra de menus, separadores do Windows PowerShell, a barra de ferramentas, separadores de script, um painel de Script, um painel de consola, uma barra de estado, um controlo de deslize do tamanho do texto e ajuda sensível ao contexto.

> [!NOTE]
> Começando com o Windows PowerShell ISE 3.0, o comando e os painéis de saída foram combinados um painel único de consola.

## <a name="menu-bar"></a>Barra de menus
Barra de menus contém o **ficheiro**, **editar**, **vista**, **ferramentas**, **depurar**,  **Suplementos**, e **ajudar** menus. Os botões nos menus permitem-lhe efetuar tarefas relacionadas com a escrever e executar scripts e comandos em execução no ISE do Windows PowerShell. Além disso, um [ferramenta suplemento](../../core-powershell/ise/The-ISEAddOnTool-Object.md) pode ser colocado na barra de menus, executando a aplicação de scripts que utilizam o [modelo de objeto de Scripting Windows PowerShell ISE](../../core-powershell/ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md).

> [!NOTE]
> No Windows PowerShell ISE 2.0, o **ferramentas** e **suplementos** menus não estavam presentes.

## <a name="windows-powershell-tabs"></a>Separadores do Windows PowerShell
Um separador de Windows PowerShell é o ambiente em que executa um script do Windows PowerShell. Pode abrir novos separadores do Windows PowerShell no ISE do Windows PowerShell para criar ambientes separados no seu computador local ou em computadores remotos. Pode ter um máximo de oito PowerShell separadores abrir em simultâneo.

## <a name="toolbar"></a>Barra de ferramentas
Os botões seguintes estão localizados na barra de ferramentas.

|Botão|Função|
|----------|------------|
|**Novo**|Abre-se um script novo.|
|**Abrir**|Abre-se de um script existente ou o ficheiro.|
|**Guardar**|Guarda um ficheiro ou do script.|
|**Cortar**|Cuts o texto seleccionado e copia-o para a área de transferência.|
|**Copiar**|Copia o texto selecionado para a área de transferência.|
|**Colar**|Cola sobre o conteúdo da área de transferência na localização de cursor.|
|**Limpar o painel de resultados**|Limpa todo o conteúdo no painel de resultados.|
|**Anular**|Inverte a ação que apenas foi efetuada.|
|**Ação de Refazer**|Executa a ação que foi anulada apenas.|
|**Executar Script**|Executa um script.|
|**Executar Selction**|Executa uma parte de um script selecionada.|
|**Parar a execução**|Deixa de um script que está em execução.|
|**Novo separador do PowerShell remoto**|Cria um novo separador do PowerShell que estabelece uma sessão num computador remoto. Uma caixa de diálogo é apresentada e pede-lhe que introduza os detalhes necessários para estabelecer a ligação remota.|
|**Iniciar o PowerShell.exe**|Abre uma consola do PowerShell.|
|**Mostrar parte superior do painel de Script**|Move o painel de Script na parte superior no ecrã.|
|**Mostrar o painel de Script direita**|Move o painel de Script para a direita na apresentação do.|
|**Mostrar o painel de Script maximizado**|Maximiza o painel de Script.|

## <a name="script-tab"></a>Separador de script
Apresenta o nome do script que está a editar. Pode clicar num separador de script para selecionar o script que pretende editar.

Quando aponta para o separador de script, o caminho completamente qualificado para o ficheiro de script é apresentada numa descrição.

## <a name="script-pane"></a>Painel de script
Permite-lhe criar e executar scripts. Pode abrir, editar e executar scripts existentes no painel de Script.

## <a name="output-pane"></a>Painel de resultados
Apresenta os resultados de comandos e scripts, que foram executados. Também pode copiar e limpar o conteúdo no painel de resultados.

## <a name="command-pane"></a>Painel de comandos
Permite-lhe escrever comandos. Pode executar um comando de uma linha ou um comando de múltiplas linhas no painel de comandos. Prima SHIFT + ENTER para introduzir cada linha de um comando de múltiplas linhas e prima ENTER depois da última linha ao executar o comando de múltiplas linhas. A linha de comandos apresentada na parte superior do painel de comando mostra o caminho para o diretório de trabalho atual.

## <a name="status-bar"></a>Na barra de estado
Permite-lhe ver se os comandos e scripts que executar são concluídas. A barra de estado é na parte inferior muito a apresentação. Selecionado partes de mensagens de erro são apresentadas na barra de estado.

## <a name="text-size-slider"></a>O controlo de deslize do tamanho do texto
Aumenta ou diminui o tamanho do texto no ecrã.

## <a name="help"></a>Ajuda
Ajuda para o Windows PowerShell ISE está disponível na Web na Biblioteca TechNet. Pode abrir a ajuda clicando **ajuda do Windows PowerShell ISE** no **ajudar** menu ou premindo a tecla F1 em qualquer lugar, exceto quando o cursor está num nome de cmdlet no painel de Script ou no painel de consola. Do **ajudar** menu também pode executar o cmdlet Update-Help e apresentar a janela de comandos que ajuda a construção de comandos, que mostra todos os parâmetros de um cmdlet e Ativando que preencha os parâmetros um formato de fácil utilização.

## <a name="see-also"></a>Consulte Também
- [Utilizar o ISE do Windows PowerShell](../../core-powershell/ise/Using-the-Windows-PowerShell-ISE.md)

