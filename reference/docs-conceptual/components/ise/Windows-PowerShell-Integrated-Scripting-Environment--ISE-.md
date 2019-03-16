---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Windows PowerShell Integrated Scripting Environment ISE
ms.assetid: f156b92d-0203-46d2-89c7-b4989d32e3d2
ms.openlocfilehash: 3002c2cb7213b1c2d7201dddf5ff3c0651fad767
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054718"
---
# <a name="windows-powershell-integrated-scripting-environment-ise"></a>Windows PowerShell Integrated Scripting Environment (ISE)

O Windows PowerShell Integrated Scripting Environment (ISE) é um dos dois anfitriões para o motor do Windows PowerShell e o idioma. Com o mesmo que pode escrever, executar e testar scripts de forma a que não está disponível na consola do Windows PowerShell. O ISE adiciona sintaxe colorida, conclusão de tabulação, IntelliSense, depuração visual e ajuda contextual.

O ISE permite-lhe executar comandos num painel de consola, mas também dá suporte a painéis que pode utilizar para a visualização simultânea de código-fonte do seu script e outras ferramentas que podem se conectar o ISE. Pode até mesmo abrir várias janelas de script ao mesmo tempo, o que é especialmente útil quando estiver depurando um script que utiliza funções definidas em outros scripts ou módulos.

## <a name="whats-new"></a>What’s New (O que há de novo)

Aqui estão alguns dos recursos que foram adicionados ao ISE nas versões mais recentes do PowerShell.

### <a name="added-in-powershell-30-windows-server-2012-windows-8"></a>Adicionado no PowerShell 3.0 (Windows Server 2012, Windows 8)

**IntelliSense** preenche automaticamente os seus comandos exibindo os menus de correspondente cmdlets, parâmetros, valores de parâmetros, ficheiros ou pastas à medida que escreve.

**Trechos de código** são curtas seções do código que pode inserir facilmente para os scripts sua escrita. Uma coleção de trechos de código útil está incluída na caixa e, mais pode utilizando o **New-fragmento** cmdlet.

**Ferramentas de suplemento** que adiciona funcionalidades ao ISE do podem ser criadas ao escrever código que interage com [o Windows PowerShell ISE scripts modelo de objeto](../../core-powershell/ise/The-ISE-Object-Model-Hierarchy.md).

Essas ferramentas podem exibir controles num painel com guias ou invisivelmente de trabalho em segundo plano. O **comandos** suplemento é um bom exemplo e está incluído na versão 3.0 e posterior que apresenta uma lista de comandos disponíveis e sua ajuda.

**Gerenciador de reinicialização e salvamento automático** automaticamente salvar seus scripts a cada dois minutos para ajudar a evitar a perda do seu trabalho em caso de uma pane ou um reinício inesperado.

**A maioria dos lista utilizados recentemente** faz agora parte do arquivo abrir menu para tornar mais fácil para os ficheiros que utiliza mais frequentemente.

**Painel de consola intercalado**. Nas versões anteriores do ISE, havia painéis de comando e de saída separados. Eles são agora combinados num único painel que mais diretamente imita o que vê na consola do Windows PowerShell.

**Opções da linha de comandos**. Vários comutadores da linha de comandos nova dão-lhe mais controlo sobre a forma como funciona o ISE. -NoProfile inicia o ISE sem executar um script de perfil. -Help abre uma janela de ajuda com o ISE. -mta inicia o ISE no "modo de multi-threaded apartment". A predefinição é o único thread.

**Novos recursos do editor** que seja mais fácil criar e ler o seu código:

- **Cores de sintaxe XML**. O editor do ISE cores agora sintaxe XML da mesma forma como ele cores sintaxe de código do Windows PowerShell.

- **Correspondência de chaves**. O ISE do PowerShell ISEWindows destaca as chavetas correspondentes para o ajudar a garantir que tem o número certo de fechar as chavetas de acordo com sua abertura aqueles. Use CTRL -\[ para localizar a chave de fechamento que corresponda a chave de abertura que se encontra o cursor.

- **Descrever vista**. Pode fechar ou expandir as secções do seu código, ao clicar no sinal de adição e subtração sinais na margem esquerda. Isto torna mais fácil encontrar o código que está procurando num script longo.

- **Arraste e largue a edição de texto**. Pode selecionar um bloco de texto e arrastá-lo para outra localização para movê-la. Se mantenha premida a tecla Ctrl enquanto arrasta o texto selecionado, que copiar, em vez de mover.

- **Analisar a exibição de erro**. Windows PowerShell examina o script, à medida que escreve. Se detetar um erro, mostra um squiggle vermelho sob o código incorreto. Quando focaliza o erro indicado, uma dica de ferramenta mostra-lhe o problema que foi encontrado.

- **Zoom**. Pode ampliar seu texto para torná-lo mais fácil de ler ou aplicar o zoom para ver o quadro, utilizando o controlo de deslize no canto inferior direito da janela de ISE.

- **Rich text copiar e colar**. Quando copia do ISE para a área de transferência, o tipo de letra, tamanho e as informações de cor do texto selecionado está incluído.

- **Bloquear a seleção**. Pode selecionar um segmento em forma de bloco de texto ao premir a tecla ALT ao selecionar o texto no painel de script com o rato ou ao premir **Alt + Shift + seta**.

### <a name="added-in-powershell-20-windows-server-2008-r2-windows-7"></a>Adicionado no PowerShell 2.0 (Windows Server 2008 R2, Windows 7)

O ISE foi introduzido com o PowerShell v2.0.

## <a name="requirements-for-running-the-windows-powershell-ise"></a>Requisitos para executar o ISE do Windows PowerShell

O ISE encontra-se disponíveis em qualquer computador Windows que pode executar a versão do Windows PowerShell 2.0 ou posterior. Cada versão do Windows e Windows Server inclui uma versão do Windows PowerShell e o ISE, mas pode atualizar para o mais recente disponível ao instalar o Windows Management Framework (WMF). Consulte a [WMF](/powershell/wmf) documentação para obter mais informações.

> [!NOTE]
> Como o ISE do Windows PowerShell exige uma interface gráfica do usuário, não é possível executá-lo a opção Server Core do Windows Server.

## <a name="see-also"></a>Consulte também

[Objetivo do windows power shell do ise do modelo de objeto de script](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)