---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: Que s novas no PowerShell 50 ISE
ms.assetid: 38648d47-7c27-4b37-a40e-ad29948519c2
ms.openlocfilehash: 9fd25a4759602bebf2b5df2c17d0c816a15e5e2b
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/15/2018
---
# <a name="what39s-new-in-the-windows-powershell-ise"></a>O que&#39;s no ISE do Windows PowerShell
Este tópico explica as funcionalidades novas e atualizadas que foi introduzidas em versões do Windows PowerShell Integrated Scripting Environment (ISE).

## <a name="feature-description"></a>Descrição da funcionalidade
O ISE do Windows PowerShell é uma aplicação de anfitrião que permite-lhe escrever, executar e testar scripts e de módulos num ambiente gráfico e intuitivo. As principais funcionalidades, tais como cores da sintaxe separador conclusão, depuração visual, compatibilidade de Unicode e ajuda sensível ao contexto fornecer uma experiência avançada do script.

Para obter uma descrição geral do ISE do Windows PowerShell, consulte [descrição geral do Windows PowerShell Integrated Scripting ambiente](https://technet.microsoft.com/library/3c1892c2-bf84-4cb6-af26-1f453be9e671).

## <a name="new-and-changed-functionality-in-windows-powershell-ise"></a>Funcionalidades novas e alteradas no ISE do Windows PowerShell
A tabela seguinte lista as funcionalidades novas e alteradas para esta versão do ISE do Windows PowerShell no Windows PowerShell.

|Funcionalidade|Windows PowerShell ISE 4.0|ISE do Windows PowerShell 3.0|Windows PowerShell ISE 2.0|
|--------------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
|**[IntelliSense](#intellisense)**|X|X||
|**[Snippets](#snippets)**|X|X||
|**[Ferramentas de suplemento](#add-on-tools)**|X|X||
|**[Reinicie o gestor e guardar automática](#restart-manager-and-auto-save)**|X|X||
|**[Mais recentemente utilizados lista](#most-recently-used-list)**|X|X||
|**[Painel de consola](#console-pane)**|X|X||
|**[Parâmetros da linha de comandos](#command-line-switches)**|X|X||
|**[Novas funcionalidades de editor](#new-editor-features)**|X|X||
|**[Nova janela de Visualizador da ajuda](#new-help-viewer-window)**|X|X||
|**[Mostrar comando cmdlet](#show-command-cmdlet)**|X|X||

### <a name="intellisense"></a>IntelliSense
**Adicionado no ISE 3.0**

O IntelliSense é uma funcionalidade de assistência de conclusão automática que faz parte do ISE do Windows PowerShell. O IntelliSense mostra clicáveis menus de correspondência potencialmente cmdlets, parâmetros, os valores de parâmetros, os ficheiros ou pastas à medida que escreve.

**Que valor acrescenta esta alteração?**

Com a adição de IntelliSense, é mais fácil detetar os cmdlets e sintaxe quando utilizar o ISE do Windows PowerShell para criar scripts. Também pode utilizar o ISE do Windows PowerShell para saber o Windows PowerShell enquanto cria os scripts de novo.

**O que funciona de forma diferente?**

Quando escreve cmdlets no Windows PowerShell ISE 3.0 ou posterior, apresenta um menu deslocável e clicável, permitindo-lhe procurar e selecionar os comandos apropriados.

### <a name="snippets"></a>Fragmentos
**Adicionado no ISE 3.0**

*Fragmentos* são secções abreviadas do código do Windows PowerShell que pode inserir os scripts que criar no ISE do Windows PowerShell. ISE do Windows PowerShell inclui um conjunto predefinido de fragmentos. Pode adicionar fragmentos utilizando o **New-fragmento** cmdlet ao trabalhar no ISE do Windows PowerShell.

**Que valor acrescenta esta alteração?**

Ao utilizar fragmentos, pode rapidamente Monte e criar scripts para automatizar o seu ambiente.

**O que funciona de forma diferente?**

Para utilizar fragmentos do Windows PowerShell 3.0 ou posterior, no **editar** menu, clique em **iniciar fragmentos**, ou prima **Ctrl-J**.

### <a name="add-on-tools"></a>Ferramentas de suplemento
**Adicionado no PowerShell 3.0**

ISE do Windows PowerShell suporta agora ferramentas de suplemento, que são os controlos de Windows Presentation Foundation (WPF) que são adicionados ao utilizar o modelo de objeto. Ferramentas de suplemento podem ser apresentadas como um painel vertical ou horizontal na consola. Várias ferramentas de suplemento num painel são apresentadas como um controlo de separadores. Também pode adicionar ou remover as ferramentas de suplementares que são produzidas por entidades confiadoras de terceiros. Para obter mais informações sobre como importar ou remover as ferramentas de suplemento, consulte [operações do Windows PowerShell ISE](http://technet.microsoft.com/library/cc732148.aspx).

**Que valor acrescenta esta alteração?**

Suplementos permitem-lhe expandir e personalizar o ISE do Windows PowerShell com ferramentas que podem melhorar a sua experiência de script ou adicionar funcionalidades ao ISE do Windows PowerShell.

**O que funciona de forma diferente?**

Windows PowerShell ISE 3.0 e posterior vêm com o **comandos** suplemento. O **comandos** suplemento permite-lhe procurar os cmdlets e aceder à ajuda sobre o cmdlets do lado do lado a lado com o **Script** e **consola** painéis.

Suplementos adicionais podem ser encontrados utilizando o **Open suplemento ferramentas site** comando no **suplementos** menu.

### <a name="restart-manager-and-auto-save"></a>Reinicie o gestor e guardar automática
**Adicionado no PowerShell 3.0**

ISE do Windows PowerShell agora guarda automaticamente os scripts Abra cada dois minutos num local separado.  Se o ISE do Windows PowerShell deixa de funcionar, ou se o sistema operativo for reiniciado após o reinício do Windows PowerShell ISE, recupera scripts que foram abra na sessão do último, mesmo se os scripts não foram guardados.

Para alterar o intervalo de guardar automático, execute o seguinte comando no painel de consola: **$psise. Options.AutoSaveMinuteInterval**.

**Que valor acrescenta esta alteração?**

Agora, pode trabalhar no ISE do Windows PowerShell, sabendo que os scripts abra são guardados automaticamente em caso de um reinício inesperado.

**O que funciona de forma diferente?**

O Windows PowerShell ISE 2.0 não guarda os scripts automaticamente em caso de um reinício.

### <a name="most-recently-used-list"></a>Mais recentemente utilizados lista
**Adicionado no PowerShell 3.0**

ISE do Windows PowerShell tem agora uma lista de ficheiros utilizada mais recentemente. Quando abre um ficheiro no ISE do Windows PowerShell, o ficheiro é adicionado à lista de mais recentemente utilizada no **ficheiro** menu.

Para alterar o número predefinido de ficheiros na lista mais recentemente utilizado, execute o seguinte comando no painel de consola: **$psise. Options.MruCount**.

**Que valor acrescenta esta alteração?**

Agora, pode utilizar a lista mais recentemente utilizada para aceder facilmente aos seus ficheiros utilizados frequentemente.

**O que funciona de forma diferente?**

O Windows PowerShell ISE 2.0 não tem uma lista mais recentemente utilizada.

### <a name="console-pane"></a>Painel de consola
**Adicionado no PowerShell 3.0**

O comando e os painéis de saída que estavam disponíveis na primeira versão do ISE do Windows PowerShell separado foram combinadas para um painel único de consola. O painel de consola é semelhante na função e do aspeto a uma consola do Windows PowerShell típica, mas inclui as seguintes melhorias (o máximo é descritos neste tópico).

- Sintaxe coloração para texto de entrada (não texto de saída), incluindo sintaxe XML

- IntelliSense

- Chaveta correspondente

- Indicação de erro

- Suporte de Unicode completo

- **F1** ajuda sensível ao contexto

- **CTRL + F1** Mostrar-Command sensíveis ao contexto

- Script complexa e suporte para a esquerda

- Suporte de tipo de letra

- Zoom

- Selecione linha e selecione bloco modos

- Preservação de conteúdo escrito na linha de comandos quando prime o **segurança** seta para ver o histórico na consola do

**Que valor acrescenta esta alteração?**

A adição destas alterações de painel de consola fornece uma experiência de script que é mais consistente com a interface da consola.

**O que funciona de forma diferente?**

O Windows PowerShell ISE 2.0 tem separado comando e painéis de saída.

### <a name="command-line-switches"></a>Parâmetros da linha de comandos
**Adicionado no PowerShell 3.0**

Se iniciar o ISE do Windows PowerShell a partir da linha de comandos (escrevendo **powershell_ise.exe**), pode adicionar os seguintes parâmetros da linha de comandos de novo.

- *-NoProfile*: inicia o Windows PowerShell ISE sem execução **$profile**

- *-Ajudar*: apresenta uma janela de ajuda

- *-mta*: começa ISE do Windows PowerShell no modo apartment multithread. O modo de operação de predefinido para o ISE do Windows PowerShell é o modo de apartamento de thread único, ou *- sta*.

**Que valor acrescenta esta alteração?**

A adição destes parâmetros da linha de comandos permite-lhe controlar o ambiente em que executa o ISE do Windows PowerShell.

**O que funciona de forma diferente?**

O Windows PowerShell ISE 2.0 não reconhece estes parâmetros da linha de comandos.

### <a name="new-editor-features"></a>Novas funcionalidades de editor
**Adicionado no PowerShell 3.0**

Outras funcionalidades de edição do ISE do Windows PowerShell incluem:

- **XML de cores da sintaxe**ISE do Windows PowerShell cores agora sintaxe XML da mesma forma como este cores sintaxe do Windows PowerShell.

- **Correspondência Chaveta** ISE do Windows PowerShell inclui Chaveta correspondentes e de realce e pode ser utilizado das seguintes formas: (por exemplo, utilizando o **aceda a correspondência** comando ou **Ctrl +]** localiza o fechar a chaveta, se tiver uma chaveta de abertura selecionada).

- **Descrevem vista** o painel de Script suporta definido que estipule, que lhe permite collapsing ou expandir secções de código, clicando em mais ou menos inicia na margem esquerda. Pode utilizar chavetas ou **#region** e **#endregion** etiquetas para marcar o início ou fim de uma secção expansível. Para expandir ou fechar todas as regiões, prima **Ctrl + M**.

- **Arraste e largue a edição de texto**ISE do Windows PowerShell agora suporta arrastar e largar a edição de texto. Pode selecionar qualquer bloco de texto e arraste esse texto para outra localização no editor ou a consola para mover o texto. Se, mantenha premida a tecla Ctrl enquanto arraste o texto seleccionado, quando solta o botão do rato o texto é copiado para a nova localização. Nesta versão do ISE do Windows PowerShell, bem como a versão anterior do ISE do Windows PowerShell, ao arrastar e largar ficheiros no ISE do Windows PowerShell ISE do Windows PowerShell abre-se o ficheiro.

- **Analisar a apresentação de erro** erros de análise são indicados com indicação vermelha. Quando paira o rato sobre o erro indicado, o texto da descrição apresenta o problema que foi encontrado no código.

- **Zoom** a percentagem de zoom da consola '™ conteúdo s pode ser definido utilizando o controlo de deslize de zoom (no canto inferior direito da janela do Windows PowerShell ISE) ou introduzindo o comando **$psise.options.Zoom** no painel de consola.

- **Avançada texto copiar e colar** copiar para a área de transferência no ISE do Windows PowerShell preserva o tipo de letra, tamanho e informações de cor da seleção original.

- **Bloquear seleção** pode selecionar um bloco de texto ao premir a tecla ALT ao selecionar o texto no painel de Script com o rato ou premindo **Alt + Shift + seta para a**.

**Que valor acrescenta esta alteração?**

As funcionalidades adicionais de edição fornecem um ambiente de edição mais consistente e eficiente.

**O que funciona de forma diferente?**

Estas melhorias de edição não estavam presentes no Windows PowerShell ISE 2.0.

### <a name="new-help-viewer-window"></a>Nova janela de Visualizador da ajuda
**Adicionado no PowerShell 3.0**

Se premir **F1** quando o cursor é um cmdlet ou tiver parte de um cmdlet realçado, o novo Visualizador da ajuda abre ajuda sensível ao contexto sobre o cmdlet realçado. Para apresentar a ajuda do Windows PowerShell sobre, escreva **operadores** no painel de consola e, em seguida, prima **F1**.

Antes de utilizar esta funcionalidade, transfira a versão mais recente dos tópicos de ajuda do Windows PowerShell a partir do Web site da Microsoft. O método mais simples para transferir os tópicos de ajuda está a ser executado o **Update-Help** cmdlet no painel de consola ao utilizar o ISE do Windows PowerShell como administrador.

Pode alterar onde o **F1** chave de procura para obter ajuda. No **ferramentas**/**opções** menu, no **definições gerais** separador em **outras definições**, pode definir ou limpar o caixa de verificação **utilizar conteúdo de ajuda local em vez de conteúdo online**. Se a opção estiver marcada, o cliente procura para o cmdlet ajuda na ajuda do transferido encontradas na pasta de módulos.  Se a caixa de verificação está desmarcada, o cliente procura na Biblioteca TechNet para a ajuda do cmdlet.

**Que valor acrescenta esta alteração?**

Ajuda sensível ao contexto sem sair sua atual cmdlet ou script fornece uma experiência totalmente integrada de aprendizagem.

**O que funciona de forma diferente?**

Premir F1 em versões anteriores do Windows PowerShell ISE abrir o ficheiro de ajuda no computador local. No Windows PowerShell ISE 3.0 e mais tarde, será apresentada uma janela que contém a ajuda do cmdlet que é configurável e pesquisáveis. Esta experiência de ajuda é nova no Windows PowerShell ISE 3.0 e ajuda Atualizável é nova no Windows PowerShell 3.0.

### <a name="show-command-cmdlet"></a>Mostrar comando cmdlet
**Adicionado no PowerShell 3.0**

O **Mostrar comando** cmdlet permite-lhe compor ou executar um cmdlet ou uma função ao preencher um formulário gráfico. O formulário permite aos utilizadores trabalhar com o Windows PowerShell num ambiente gráfico. **Mostrar comando** também permite avançadas scripters para criar uma rápida GUI de acesso baseado no Windows PowerShell.

**Que valor acrescenta esta alteração?**

Ao utilizar **Mostrar comando** nos scripts do Windows PowerShell, pode fornecer os seus utilizadores com o ambiente gráfico com a qual está familiarizados. **Mostrar comando** também podem ajudar os utilizadores introdutórias saiba do Windows PowerShell.

**O que funciona de forma diferente?**

Mostrar comando é novo do Windows PowerShell ISE 3.0.

## <a name="see-also"></a>Consulte também
Para obter mais informações sobre como utilizar o ISE do Windows PowerShell no Windows PowerShell, consulte as hiperligações seguintes.

- [Explorar o ambiente de script integrada do Windows PowerShell](../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
- [ISE no TechNet Wiki](http://social.technet.microsoft.com/wiki/search/searchresults.aspx?q=ISE)
- [Centro de scripts](http://technet.microsoft.com/scriptcenter/default)

