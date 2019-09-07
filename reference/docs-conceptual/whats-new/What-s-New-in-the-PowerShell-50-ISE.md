---
ms.date: 09/06/2019
keywords: PowerShell, cmdlet
title: O que há de novo no PowerShell 5,0 ISE
ms.openlocfilehash: a719baef0da1600f0a5377e1b72c81b67e37eef2
ms.sourcegitcommit: a74ae7ed089301992fed201fbe55d827a622afa0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70746230"
---
# <a name="whats-new-in-the-windows-powershell-50-ise"></a>O que há de novo no ISE do Windows PowerShell 5,0

Este tópico explica os recursos novos e atualizados que foram introduzidos em versões do Ambiente de Script Integrado do Windows PowerShell (ISE).

## <a name="feature-description"></a>Descrição da funcionalidade

O ISE do Windows PowerShell é um aplicativo host que permite gravar, executar e testar scripts e módulos em um ambiente gráfico e intuitivo. Os principais recursos, como cores de sintaxe, preenchimento com Tab, depuração Visual, conformidade com Unicode e ajuda contextual fornecem uma experiência de script avançada.

Para obter mais informações, consulte [apresentando o ISE do Windows PowerShell](../components/ise/Introducing-the-Windows-PowerShell-ISE.md).

A tabela a seguir lista os recursos novos e alterados para esta versão do ISE do Windows PowerShell no Windows PowerShell.

## <a name="intellisense"></a>IntelliSense

> Adicionado no ISE 3,0

O IntelliSense é um recurso de assistência de conclusão automática que faz parte do ISE do Windows PowerShell.
O IntelliSense exibe menus clicáveis de cmdlets, parâmetros, valores de parâmetro, arquivos ou pastas potencialmente correspondentes conforme você digita.

**Que valor essa alteração adiciona?**

Com a adição do IntelliSense, é mais fácil descobrir cmdlets e sintaxe quando você usa ISE do Windows PowerShell para criar scripts. Você também pode usar ISE do Windows PowerShell para aprender o Windows PowerShell enquanto cria novos scripts.

**O que funciona de maneira diferente?**

Quando você digita cmdlets no ISE do Windows PowerShell, um menu rolável e clicável é exibido, permitindo que você procure e selecione os comandos apropriados.

## <a name="snippets"></a>Trechos

> Adicionado no ISE 3,0

Os *trechos* são seções curtas do código do Windows PowerShell que você pode inserir nos scripts criados no ISE do Windows PowerShell. ISE do Windows PowerShell vem com um conjunto padrão de trechos de código. Você pode adicionar trechos de código usando `New-Snippet` o cmdlet enquanto trabalha no ISE do Windows PowerShell.

**Que valor essa alteração adiciona?**

Usando trechos de código, você pode montar e criar scripts rapidamente para automatizar seu ambiente.

**O que funciona de maneira diferente?**

Para usar trechos de código no Windows PowerShell 3,0 ou posterior, no menu **Editar** , clique em **Iniciar trechos de código**ou pressione <kbd>Ctrl</kbd>+<kbd>J</kbd>.

## <a name="add-on-tools"></a>Ferramentas complementares

> Adicionado no PowerShell 3,0

O ISE do Windows PowerShell agora dá suporte a ferramentas de complemento usando o modelo de objeto. Esses Complementos são controles Windows Presentation Foundation (WPF) que são exibidos como um painel vertical ou horizontal no console do. Várias ferramentas complementares em um painel são exibidas como um controle com guias. Você também pode adicionar ou remover ferramentas complementares que são produzidas por partes que não são da Microsoft. Para obter mais informações, consulte [a finalidade do modelo de objeto de script de ISE do Windows PowerShell](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md).

**Que valor essa alteração adiciona?**

Os complementos permitem que você estenda e personalize ISE do Windows PowerShell com ferramentas que adicionam funcionalidade e aprimoram sua experiência de script.

**O que funciona de maneira diferente?**

ISE do Windows PowerShell 3,0 e posteriores vêm com o complemento de **comandos** . O complemento **comandos** permite que você procure cmdlets e acesse a ajuda dos cmdlets lado a lado com os painéis de **script** e de **console** .

Complementos adicionais podem ser encontrados usando o comando **abrir site de ferramentas complementares** no menu **Complementos** .

## <a name="restart-manager-and-auto-save"></a>Gerenciador de reinicialização e salvamento automático

> Adicionado no PowerShell 3,0

ISE do Windows PowerShell agora salva automaticamente os scripts abertos a cada dois minutos, em um local separado. Quando ISE do Windows PowerShell reinicia após uma falha inesperada ou uma reinicialização, ela recupera os scripts que estavam abertos na última sessão, mesmo que os scripts não tenham sido salvos.

Para alterar o intervalo de salvamento automático, execute o seguinte comando no painel de console `$psise.Options.AutoSaveMinuteInterval`:.

**Que valor essa alteração adiciona?**

Agora você pode trabalhar em ISE do Windows PowerShell sabendo que os scripts abertos são salvos automaticamente.

**O que funciona de maneira diferente?**

ISE do Windows PowerShell 2,0 não salva os scripts automaticamente.

## <a name="most-recently-used-list"></a>Lista de usados mais recentemente

> Adicionado no PowerShell 3,0

ISE do Windows PowerShell agora tem uma lista de arquivos usada mais recentemente. Quando você abre um arquivo em ISE do Windows PowerShell, o arquivo é adicionado à lista de usados mais recentemente no menu **arquivo** .

Para alterar o número padrão de arquivos na lista de usados mais recentemente, execute o seguinte comando no painel de console: `$psise.Options.MruCount`.

**Que valor essa alteração adiciona?**

Agora você pode usar a lista de usados mais recentemente para acessar facilmente os arquivos usados com frequência.

**O que funciona de maneira diferente?**

ISE do Windows PowerShell 2,0 não tem uma lista de usados mais recentemente.

## <a name="console-pane"></a>Painel de console

> Adicionado no PowerShell 3,0

Os painéis de comando e saída separados que estavam disponíveis na primeira versão do ISE do Windows PowerShell foram combinados em um único painel de console. O painel de console é semelhante em função e aparência a um console típico do Windows PowerShell, mas inclui os seguintes aprimoramentos:

- Cores de sintaxe para texto de entrada (não texto de saída), incluindo sintaxe XML
- IntelliSense
- Correspondência de chaves
- Indicação de erro
- Suporte completo a Unicode
- Ajuda sensível ao contexto <kbd>F1</kbd>
- <kbd></kbd>Ctrl+<kbd>F1</kbd> show-Command sensível ao contexto
- Script complexo e suporte da direita para a esquerda
- Suporte a fontes
- Zoom
- Modos de seleção de linha e seleção de bloco
- Preservação do conteúdo digitado na linha de comando quando você pressiona a <kbd>seta</kbd> para exibir o histórico no console

**Que valor essa alteração adiciona?**

A adição dessas alterações do painel de console fornece uma experiência de script que é mais consistente com a interface do console.

**O que funciona de maneira diferente?**

ISE do Windows PowerShell 2,0 tem painéis de comando e de saída separados.

## <a name="command-line-switches"></a>Opções de linha de comando

> Adicionado no PowerShell 3,0

Se você iniciar ISE do Windows PowerShell na linha de comando (digitando **Powershell_ise. exe**), poderá adicionar as novas opções de linha de comando a seguir.

- `-NoProfile`: Inicia ISE do Windows PowerShell sem execução`$profile`
- `-Help`: Exibe uma janela de ajuda
- `-mta`: Inicia ISE do Windows PowerShell no modo Apartment multithread. O modo de operação padrão para ISE do Windows PowerShell é o modo Apartment de thread único ou `-sta`.

**Que valor essa alteração adiciona?**

A adição dessas opções de linha de comando permite controlar o ambiente no qual o ISE do Windows PowerShell é executado.

**O que funciona de maneira diferente?**

ISE do Windows PowerShell 2,0 não reconhece essas opções de linha de comando.

## <a name="new-editor-features"></a>Novos recursos do editor

> Adicionado no PowerShell 3,0

Outros recursos de edição de ISE do Windows PowerShell incluem:

- **Cor de sintaxe XML** -ISE do Windows PowerShell agora tem a sintaxe XML colorida da mesma maneira que a sintaxe de cores de ti do Windows PowerShell.
- **Correspondência de chaves** -ISE do Windows PowerShell inclui correspondência de chaves e realce e pode ser usada das seguintes maneiras: (por exemplo, usar o comando **ir para correspondência** ou <kbd>Ctrl</kbd>+<kbd>]</kbd> localiza a chave de fechamento, se você ter uma chave de abertura selecionada).
- **Modo de exibição da estrutura do código** O painel de script oferece suporte a estrutura de tópicos, que permite recolher ou expandir seções de código clicando em mais ou menos sinais na margem esquerda. Você pode usar chaves ou as marcas `#region` e `#endregion` para marcar o início ou o fim de uma seção recolhível. Para expandir ou recolher todas as regiões, pressione <kbd>Ctrl</kbd>+<kbd>M</kbd>.
- **Edição de texto arrastar e soltar** -ISE do Windows PowerShell agora dá suporte à edição de texto de arrastar e soltar. Você pode selecionar qualquer bloco de texto e arrastar esse texto para outro local no editor ou no console do para mover o texto. Se você mantiver pressionada a tecla <kbd>Ctrl</kbd> enquanto arrasta o texto selecionado, ao liberar o botão do mouse, o texto será copiado para o novo local. Nesta versão do ISE do Windows PowerShell, quando você arrasta e solta arquivos em ISE do Windows PowerShell, ISE do Windows PowerShell abre o arquivo.
- **Exibição de erro de análise** -os erros de análise são indicados com sublinhados vermelhos. Quando você passa o mouse sobre um erro indicado, o texto da dica de ferramenta exibe o problema encontrado no código.
- **Zoom** -o percentual de zoom do conteúdo do console pode ser definido usando o controle deslizante de zoom (no canto inferior direito da janela ISE do Windows PowerShell) ou inserindo o comando `$psise.options.Zoom` no painel de console.
- **Cópias de Rich Text e** cópia de colagem na área de transferência em ISE do Windows PowerShell preserva a fonte, o tamanho e as informações de cor da seleção original.
- **Seleção de bloco** – você pode selecionar um bloco de texto mantendo a tecla <kbd>ALT</kbd> pressionada enquanto seleciona o texto no painel de script com o mouse ou pressionando <kbd>ALT</kbd>+<kbd>Shift</kbd>+<kbd>seta</kbd>.

**Que valor essa alteração adiciona?**

Os recursos de edição adicionais fornecem um ambiente de edição mais consistente e eficiente.

**O que funciona de maneira diferente?**

Esses aprimoramentos de edição não estavam presentes no ISE do Windows PowerShell 2,0.

## <a name="new-help-viewer-window"></a>Janela do novo Visualizador da ajuda

> Adicionado no PowerShell 3,0

Se você pressionar <kbd>F1</kbd> quando o cursor estiver em um cmdlet ou se parte de um cmdlet estiver realçada, o novo Visualizador da ajuda abrirá a ajuda contextual sobre o cmdlet realçado. Para exibir **a ajuda do** Windows PowerShell, `operators` digite no painel de console e pressione <kbd>F1</kbd>.

Antes de usar esse recurso, baixe a versão mais atual dos tópicos da ajuda do Windows PowerShell no site da Microsoft. O método mais simples para baixar os tópicos da ajuda é executar o `Update-Help` cmdlet no painel de console ao executar ISE do Windows PowerShell como administrador.

Você pode alterar o local em que a tecla <kbd>F1</kbd> procura ajuda. No menu**Opções** de **ferramentas**/, na guia **configurações gerais** , em **outras configurações**, você pode definir ou desmarcar a caixa de seleção **usar conteúdo de ajuda local em vez de conteúdo online**. Quando marcada, o cliente procura a ajuda do cmdlet na ajuda baixada encontrada na pasta modules. Se a caixa de seleção for desmarcada, o cliente procurará ajuda online.

**Que valor essa alteração adiciona?**

A ajuda contextual sem deixar seu cmdlet ou script atual fornece uma experiência de aprendizado integrada.

**O que funciona de maneira diferente?**

Pressionar <kbd>F1</kbd> em versões anteriores do ISE do Windows PowerShell abriu o arquivo de ajuda no computador local. No ISE do Windows PowerShell 3,0 e posterior, é aberta uma janela que contém a ajuda para o cmdlet que pode ser pesquisado e configurável. Esta experiência de ajuda é nova para o ISE do Windows PowerShell 3,0, e a ajuda atualizável é nova para o Windows PowerShell 3,0.

## <a name="show-command-cmdlet"></a>Cmdlet show-Command

> Adicionado no PowerShell 3,0

O `Show-Command` cmdlet permite compor ou executar um cmdlet ou uma função preenchendo um formulário gráfico. O formulário permite que os usuários trabalhem com o Windows PowerShell em um ambiente gráfico.
`Show-Command`também permite que os scripts avançados criem uma GUI rápida baseada no Windows PowerShell.

**Que valor essa alteração adiciona?**

Usando `Show-Command` o em seus scripts do Windows PowerShell, você pode fornecer aos usuários o ambiente gráfico com o qual eles estão familiarizados. `Show-Command`também pode ajudar os usuários introdutórios a aprender o Windows PowerShell.

**O que funciona de maneira diferente?**

`Show-Command`é novo ISE do Windows PowerShell 3,0.

## <a name="see-also"></a>Consulte também

Para obter mais informações sobre como usar ISE do Windows PowerShell, consulte [explorando o ambiente de script integrado do Windows PowerShell](../getting-started/fundamental/exploring-the-windows-powershell-ise.md).
