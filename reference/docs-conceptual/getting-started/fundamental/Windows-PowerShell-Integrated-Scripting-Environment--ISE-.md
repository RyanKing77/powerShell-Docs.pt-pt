---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: Integrada de Windows PowerShell ISE de ambiente de script
ms.assetid: f156b92d-0203-46d2-89c7-b4989d32e3d2
ms.openlocfilehash: 6a2d2bada2d8d6a1d5bedffc7b1b28fe9472544a
ms.sourcegitcommit: 755d7bc0740573d73613cedcf79981ca3dc81c5e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/09/2018
---
# <a name="windows-powershell-integrated-scripting-environment-ise"></a>Windows PowerShell Integrated Scripting Environment (ISE)

O Windows PowerShell Integrated Scripting Environment (ISE) é um dos dois anfitriões para o motor do Windows PowerShell e o idioma. Com a mesma que pode escrever, executar e testar scripts de formas que não estão disponíveis na consola do Windows PowerShell. ISE do adiciona cores da sintaxe, conclusão de separador, o IntelliSense, depuração visual e ajuda context confidenciais.

O ISE permite-lhe executar comandos no painel de consola, mas também suporta painéis que pode utilizar para ver em simultâneo o código fonte da sua script e outras ferramentas que podem ligue o ISE. Pode abrir, mesmo se várias janelas de script ao mesmo tempo, que é especialmente útil quando está a depurar um script que utiliza as funções definidas em outros scripts ou os módulos.

## <a name="whats-new"></a>What’s New (O que há de novo)

Seguem-se algumas das funcionalidades que foram adicionadas ao ISE nas versões mais recentes do PowerShell.

### <a name="added-in-powershell-30-windows-server-2012-windows-8"></a>Adicionado no PowerShell 3.0 (Windows Server 2012, Windows 8)

**O IntelliSense** conclui automaticamente os comandos, apresentando menus correspondente cmdlets, parâmetros, os valores de parâmetros, os ficheiros ou pastas à medida que escreve.

**Fragmentos** são secções abreviadas do código que lhe pode facilmente inserir os scripts a escrita. Uma coleção de fragmentos útil está incluída na caixa e pode mais utilizando o **New-fragmento** cmdlet.

**Ferramentas de suplemento** que adiciona funcionalidades ao ISE do podem ser criadas por código de escrita de mensagens em fila que interage com o [o Windows PowerShell ISE Scripting modelo de objeto](../../core-powershell/ise/The-ISE-Object-Model-Hierarchy.md).

Estas ferramentas podem apresentar os controlos no painel de separadores ou invisibly de trabalho em segundo plano. O **comandos** suplemento é um bom exemplo e está incluído com a versão 3.0 e mais tarde que mostra uma lista dos comandos disponíveis e as respetivas ajuda.

**Reinicie o gestor e guardar automática** guarda automaticamente os scripts cada dois minutos para o ajudar a evitar a perda do seu trabalho em caso de uma falha ou um reinício inesperado.

**A maioria das lista utilizados recentemente** faz agora parte do menu ficheiro aberto para tornar mais fácil obter os ficheiros que utiliza mais frequentemente.

**Painel de consola intercalado**. Em versões anteriores do ISE do ocorreram painéis de comando e de saída separados. Estes são agora combinados um painel único que mais diretamente mimics veem na consola do Windows Powershell.

**Parâmetros da linha de comandos**. Vários comutadores da linha de comandos novo dão-lhe mais controlo sobre a forma como funciona o ISE. -NoProfile inicia o ISE sem executar um script de perfil. -Help abre-se uma janela de ajuda com o ISE. -mta inicia o ISE no "modo apartment multi-thread". A predefinição é o único thread.

**Novas funcionalidades de editor** tornam mais fácil criar e ler o código:

- **XML de cores da sintaxe**. O editor de ISE cores agora sintaxe XML da mesma forma como esta sintaxe de código do Windows PowerShell de cores.

- **Correspondência da Chaveta**. ISE do PowerShell ISEWindows realça chavetas correspondentes para o ajudar a garantir que tem o número correto de chavetas para corresponder a abertura de fecho aqueles. Utilize CTRL -\[ para localizar a chaveta de fecho que corresponda a chaveta de abertura que se encontra o cursor.

- **Descrevem vista**. Pode fechar ou expandir as secções do seu código clicando o sinal de adição e menos sinais na margem esquerda. Isto torna mais fácil localizar o código que procura num script longo.

- **Arraste e largue a edição de texto**. Pode selecionar um bloco de texto e arraste-o para outra localização movê-lo. Se, mantenha premida a tecla Ctrl enquanto arraste o texto seleccionado que copiá-los em vez de mover.

- **Analisar a apresentação de erro**. Windows PowerShell examina o script à medida que escreve. Se detetar um erro, mostra um squiggle vermelho sob o código inválido. Quando paira o rato sobre o erro indicado, descrição mostra-lhe o problema encontrado.

- **Zoom**. Pode ampliar no seu texto para facilitar a leitura ou reduzir para ver a imagem maior, utilizando o controlo de deslize no canto inferior direito da janela ISE.

- **Avançada texto copiar e colar**. Quando copiar do ISE para a área de transferência, o tipo de letra, tamanho e informações de cor do texto seleccionado está incluído.

- **Bloquear seleção**. Pode selecionar um segmento em forma de bloco de texto ao premir a tecla ALT ao selecionar o texto no painel de script com o rato ou premindo **Alt + Shift + seta para a**.

### <a name="added-in-powershell-20-windows-server-2008-r2-windows-7"></a>Adicionado no PowerShell 2.0 (Windows Server 2008 R2, Windows 7)

Foi introduzido o ISE com v 2.0 do PowerShell.

## <a name="requirements-for-running-the-windows-powershell-ise"></a>Requisitos para executar o ISE do Windows PowerShell

ISE do está disponível em qualquer computador com o Windows que pode ser executados v do Windows PowerShell 2.0 ou posterior. Cada versão do Windows e Windows Server inclui uma versão do Windows PowerShell e o ISE, mas pode atualizar para o mais recente disponível ao instalar o Windows Management Framework (WMF). Consulte o [WMF](/powershell/wmf/readme) documentação para obter mais informações.

> [!NOTE]
> Uma vez ISE do Windows PowerShell requer uma interface gráfica, não é possível executá-lo a opção Server Core do Windows Server.

## <a name="see-also"></a>Consulte também

[Objetivo do ise do windows power shell modelo de objeto de scripting](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
