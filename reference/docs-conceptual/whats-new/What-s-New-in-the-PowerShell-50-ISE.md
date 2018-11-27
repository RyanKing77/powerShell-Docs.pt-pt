---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Novidades no PowerShell 50 ISE
ms.assetid: 38648d47-7c27-4b37-a40e-ad29948519c2
ms.openlocfilehash: f05e3f3f95c8ceec6e843b8a1c79e6f092e1b87b
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/27/2018
ms.locfileid: "52320589"
---
# <a name="what39s-new-in-the-windows-powershell-ise"></a>O que&#39;novidade do ISE do Windows PowerShell
Este tópico explica os recursos novos e atualizados que foram introduzidos em versões do Windows PowerShell Integrated Scripting Environment (ISE).

## <a name="feature-description"></a>Descrição da funcionalidade
ISE do Windows PowerShell é um aplicativo de host que permite-lhe escrever, executar e testar scripts e módulos num ambiente de gráfico e intuitivo. Funcionalidades vitais, como a sintaxe de codificação por cores, separador de conclusão, depuração visual, conformidade de Unicode e ajuda sensível ao contexto fornecem uma Rica experiência de criação de scripts.

Para uma descrição geral do ISE do Windows PowerShell, consulte [descrição geral do Windows PowerShell Integrated Scripting ambiente](https://technet.microsoft.com/library/3c1892c2-bf84-4cb6-af26-1f453be9e671).

## <a name="new-and-changed-functionality-in-windows-powershell-ise"></a>Funcionalidades novas e alteradas no ISE do Windows PowerShell
A tabela seguinte lista as funcionalidades novas e alteradas para esta versão do Windows PowerShell ISE do Windows PowerShell.

|Funcionalidade|ISE do Windows PowerShell 4.0|ISE do Windows PowerShell 3.0|ISE do Windows PowerShell 2.0|
|--------------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
|**[IntelliSense](#intellisense)**|X|X||
|**[Trechos de código](#snippets)**|X|X||
|**[Ferramentas de suplemento](#add-on-tools)**|X|X||
|**[Gerenciador de reinicialização e salvamento automático](#restart-manager-and-auto-save)**|X|X||
|**[Mais recentemente utilizado lista](#most-recently-used-list)**|X|X||
|**[Painel de consola](#console-pane)**|X|X||
|**[Opções da linha de comandos](#command-line-switches)**|X|X||
|**[Novos recursos do editor](#new-editor-features)**|X|X||
|**[Nova janela de Visualizador da ajuda](#new-help-viewer-window)**|X|X||
|**[Cmdlet de comando show](#show-command-cmdlet)**|X|X||

### <a name="intellisense"></a>IntelliSense
**Adicionado no ISE 3.0**

IntelliSense é uma funcionalidade de assistência de preenchimento automático que faz parte do ISE do Windows PowerShell. O IntelliSense apresenta clicáveis menus de potencialmente correspondentes cmdlets, parâmetros, valores de parâmetros, ficheiros ou pastas à medida que escreve.

**Que valor acrescenta esta alteração?**

Com a adição do IntelliSense, é mais fácil detetar os cmdlets e sintaxe ao utilizar o ISE do Windows PowerShell para criar scripts. Também pode utilizar o ISE do Windows PowerShell para obter o Windows PowerShell enquanto cria novos scripts.

**O que funciona de forma diferente?**

Quando escreve cmdlets no Windows PowerShell ISE 3.0 ou posterior, apresenta um menu rolável e clicável, permitindo que navegue e selecione os comandos apropriados.

### <a name="snippets"></a>Trechos de código
**Adicionado no ISE 3.0**

*Trechos de código* são curtas seções de código do Windows PowerShell que pode inserir em scripts que criar no ISE do Windows PowerShell. ISE do Windows PowerShell vem com um conjunto predefinido de trechos de código. Pode adicionar trechos de código utilizando o **New-fragmento** cmdlet enquanto trabalha no ISE do Windows PowerShell.

**Que valor acrescenta esta alteração?**

Ao usar trechos de código, pode rapidamente montar e criar scripts para automatizar o seu ambiente.

**O que funciona de forma diferente?**

Para utilizar em trechos de código no Windows PowerShell 3.0 ou posterior, o **editar** menu, clique em **iniciar trechos de código**, ou prima **Ctrl-J**.

### <a name="add-on-tools"></a>Ferramentas de suplemento
**Adicionado no PowerShell 3.0**

ISE do Windows PowerShell agora oferece suporte a ferramentas de suplemento, que são controles do Windows Presentation Foundation (WPF) que são adicionados ao utilizar o modelo de objeto. Ferramentas de suplemento podem ser apresentadas como um painel vertical ou horizontal na consola do. Várias ferramentas de suplemento num painel são apresentadas como um controle com guias. Também pode adicionar ou remover as ferramentas de suplemento que são produzidas por partes não são da Microsoft. Para obter mais informações sobre como importar ou remover as ferramentas de suplemento, consulte [operações de ISE do Windows PowerShell](https://technet.microsoft.com/library/cc732148.aspx).

**Que valor acrescenta esta alteração?**

Suplementos permitem-lhe expandir e personalizar o ISE do Windows PowerShell com ferramentas que podem aprimorar sua experiência de criação de scripts ou adicionar funcionalidade ao ISE do Windows PowerShell.

**O que funciona de forma diferente?**

Windows PowerShell ISE 3.0 e versões posterior são fornecidos com o **comandos** suplemento. O **comandos** suplemento permite-lhe procurar os cmdlets e aceder à ajuda sobre a cmdlets lado a lado com o **Script** e **consola** painéis.

Suplementos adicionais podem ser encontrados ao utilizar o **Web site de ferramentas de suplemento aberto** comando o **suplementos** menu.

### <a name="restart-manager-and-auto-save"></a>Gerenciador de reinicialização e salvamento automático
**Adicionado no PowerShell 3.0**

ISE do Windows PowerShell agora guarda automaticamente seus scripts abertos a cada dois minutos, num local separado.  Se o ISE do Windows PowerShell deixa de funcionar ou se o sistema operativo for reiniciado, após o reinício do Windows PowerShell ISE, ele recupera scripts que foram abrir na última sessão, mesmo que os scripts não foram guardados.

Para alterar o intervalo de salvamento automático, execute o seguinte comando no painel da consola: **$psise. Options.AutoSaveMinuteInterval**.

**Que valor acrescenta esta alteração?**

Agora, pode trabalhar no ISE do Windows PowerShell, sabendo que os seus scripts abertos são guardadas automaticamente em caso de uma reinicialização inesperada.

**O que funciona de forma diferente?**

Windows PowerShell ISE 2.0 não guardar os scripts automaticamente em caso de um reinício.

### <a name="most-recently-used-list"></a>Mais recentemente utilizado lista
**Adicionado no PowerShell 3.0**

ISE do Windows PowerShell tem agora uma lista mais recentemente utilizada para ficheiros. Quando abre um ficheiro no ISE do Windows PowerShell, o arquivo for adicionado à lista mais recentemente utilizada no **ficheiro** menu.

Para alterar o número predefinido de arquivos na lista de mais recentemente utilizado, execute o seguinte comando no painel da consola: **$psise. Options.MruCount**.

**Que valor acrescenta esta alteração?**

Agora, pode utilizar a lista mais recentemente utilizada para aceder facilmente aos seus arquivos usados com frequência.

**O que funciona de forma diferente?**

Windows PowerShell ISE 2.0 não tem uma lista mais recentemente utilizada.

### <a name="console-pane"></a>Painel de consola
**Adicionado no PowerShell 3.0**

O comando separado e os painéis de saída que estavam disponíveis na primeira versão do Windows PowerShell ISE foram combinados num único painel de consola. O painel de consola é semelhante em função e a aparência de uma consola típica do Windows PowerShell, mas inclui os seguintes aprimoramentos (a maioria é descrita neste tópico).

- Cores da sintaxe para texto de entrada (não texto de saída), incluindo sintaxe XML

- IntelliSense

- Correspondência de chave

- Indicação do erro

- Suporte completo a Unicode

- **F1** ajuda sensível ao contexto

- **CTRL + F1** sensível ao contexto de comando de Show

- Script complexo e suporte da direita para a esquerda

- Suporte de tipo de letra

- Zoom

- Modos de seleção de linha e selecione de bloco

- Preservação de conteúdo digitado na linha de comandos quando pressiona o **cópia** seta para ver o histórico na consola do

**Que valor acrescenta esta alteração?**

A adição dessas alterações de painel de consola fornece uma experiência de criação de scripts mais consistente com a interface de console.

**O que funciona de forma diferente?**

Windows PowerShell ISE 2.0 tem separado de comando e painéis de saída.

### <a name="command-line-switches"></a>Opções da linha de comandos
**Adicionado no PowerShell 3.0**

Se iniciar o ISE do Windows PowerShell a partir da linha de comandos (digitando **powershell_ise.exe**), pode adicionar os seguintes parâmetros de linha de comando novo.

- *-NoProfile*: inicia o Windows PowerShell ISE sem executar **$profile**

- *-Ajudar*: exibe uma janela de ajuda

- *-mta*: inicia o ISE do PowerShell do Windows no modo multithreaded apartment. O modo de operação do padrão do Windows PowerShell ISE é o modo de apartamento de thread único, ou *- sta*.

**Que valor acrescenta esta alteração?**

A adição desses interruptores de linha de comando permite-lhe controlar o ambiente no qual o ISE do Windows PowerShell é executado.

**O que funciona de forma diferente?**

Windows PowerShell ISE 2.0 não reconhece esses comutadores da linha de comandos.

### <a name="new-editor-features"></a>Novos recursos do editor
**Adicionado no PowerShell 3.0**

Outras funcionalidades de edição do Windows PowerShell ISE incluem:

- **Cores de sintaxe XML**ISE do Windows PowerShell agora as cores sintaxe XML da mesma forma como ele cores a sintaxe do Windows PowerShell.

- **Correspondência de chaves** ISE do Windows PowerShell inclui a correspondência de chaves e realce e pode ser usado das seguintes formas: (por exemplo, utilizando o **Ir para correspondência** comando ou **Ctrl +]** localiza o a fechar a chave, se tiver uma chave de abertura selecionado).

- **Descrever vista** o painel de Script suporta descrevendo, que permite que o recolhimento ou expandir seções do código ao clicar em mais ou menos, que inicia sessão na margem esquerda. Pode utilizar chaves ou o **#region** e **#endregion** etiquetas para marcar o início ou fim de uma seção recolhível. Para expandir ou fechar todas as regiões, prima **Ctrl + M**.

- **Arraste e largue a edição de texto**ISE do Windows PowerShell agora suporta arrasta e largar a edição de texto. Pode selecionar qualquer bloco de texto e arrastar esse texto para outra localização num editor ou a consola para mover o texto. Se mantenha premida a tecla Ctrl enquanto arrasta o texto selecionado, quando soltar o botão do mouse o texto é copiado para a nova localização. Esta versão do Windows PowerShell ISE, bem como a versão anterior do Windows PowerShell ISE, quando arrastar e soltar arquivos no ISE do Windows PowerShell, o Windows PowerShell ISE abre o arquivo.

- **Analisar a exibição de erro** erros de análise são indicados com sublinhados vermelhos. Quando coloque o cursor sobre um erro indicado, o texto de descrição apresenta o problema que foi encontrado no código.

- **Zoom** a percentagem de zoom da consola "™ conteúdo s pode ser definido utilizando o controlo de deslize de zoom (no canto inferior direito da janela do Windows PowerShell ISE), ou introduza o comando **$psise.options.Zoom** no painel da consola.

- **Rich text copiar e colar** copiar para a área de transferência no ISE do Windows PowerShell preserva o tipo de letra, tamanho e as informações de cor da seleção original.

- **Bloquear a seleção** pode selecionar um bloco de texto ao premir a tecla ALT ao selecionar o texto no painel de Script com o rato ou ao premir **Alt + Shift + seta**.

**Que valor acrescenta esta alteração?**

Os recursos de edição adicionais fornecem um ambiente de edição mais consistente e eficiente.

**O que funciona de forma diferente?**

Estas melhorias de edição não estavam presentes no Windows PowerShell ISE 2.0.

### <a name="new-help-viewer-window"></a>Nova janela de Visualizador da ajuda
**Adicionado no PowerShell 3.0**

Se pressionar **F1** quando o cursor está num cmdlet ou, se tiver parte de um cmdlet realçado, o novo Visualizador da ajuda abre ajuda sensível ao contexto sobre o cmdlet realçado. Para apresentar a ajuda do Windows PowerShell sobre, escreva **operadores** no painel de consola e, em seguida, prima **F1**.

Antes de utilizar esta funcionalidade, baixe a versão mais atual dos tópicos de ajuda do Windows PowerShell a partir do site da Microsoft. O método mais simples para baixar os tópicos de ajuda é executar o **Update-Help** cmdlet no painel da consola ao executar o ISE do Windows PowerShell como administrador.

É possível alterar a onde o **F1** chave procura de ajuda. Na **ferramentas**/**opções** menu, no **definições gerais** separador, em **outras definições**, pode definir ou limpar o caixa de verificação **utilizar o conteúdo da ajuda local em vez de conteúdo online**. Se a opção estiver marcada, o cliente procura o ajuda na ajuda do transferido encontradas na pasta de módulos do cmdlet.  Se a caixa de verificação está desmarcada, em seguida, o cliente procura na Biblioteca TechNet para a ajuda do cmdlet.

**Que valor acrescenta esta alteração?**

Ajuda sensível ao contexto sem sair do seus atual cmdlet ou script fornece uma experiência de aprendizagem contínua.

**O que funciona de forma diferente?**

Pressionar F1 nas versões anteriores do Windows PowerShell ISE abrir o arquivo de ajuda no computador local. No Windows PowerShell ISE 3.0 e versões posteriores, é aberta uma janela que contém a ajuda do cmdlet que é pesquisável e configuráveis. Esta experiência de ajuda é nova para o Windows PowerShell ISE 3.0 e ajuda Atualizável é novo para o Windows PowerShell 3.0.

### <a name="show-command-cmdlet"></a>Cmdlet de comando show
**Adicionado no PowerShell 3.0**

O **comando Show** cmdlet permite-lhe compor ou executar um cmdlet ou uma função ao preencher um formulário de gráfico. O formulário permite aos utilizadores trabalhar com o Windows PowerShell num ambiente gráfico. **Comando show** também possibilita a autores de script para criar uma rápida GUI de acesso baseado em Windows PowerShell.

**Que valor acrescenta esta alteração?**

Usando **comando Show** nos seus scripts do Windows PowerShell, pode fornecer aos usuários com o ambiente gráfico com as quais está familiarizados. **Comando show** também pode ajudar os utilizadores introdutórios aprender o Windows PowerShell.

**O que funciona de forma diferente?**

Comando show é o novo Windows PowerShell ISE 3.0.

## <a name="see-also"></a>Consulte também
Para obter mais informações sobre como utilizar o ISE do Windows PowerShell no Windows PowerShell, consulte os links a seguir.

- [Explorar o ambiente de script integrado do Windows PowerShell](../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
- [ISE no TechNet Wiki](https://social.technet.microsoft.com/wiki/search/searchresults.aspx?q=ISE)
- [Centro de scripts](https://technet.microsoft.com/scriptcenter/default)