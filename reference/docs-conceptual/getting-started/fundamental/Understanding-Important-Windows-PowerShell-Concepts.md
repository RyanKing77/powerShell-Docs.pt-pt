---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Noções sobre Conceitos Importantes do Windows PowerShell
ms.assetid: 3e601e38-4520-4578-a48d-b6779f1d35ee
ms.openlocfilehash: 07ceaa2f3e6a192c6281cb4c99aed4c3f66afc7e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="understanding-important-windows-powershell-concepts"></a>Noções sobre Conceitos Importantes do Windows PowerShell
A estrutura do Windows PowerShell integra conceitos de vários ambientes diferentes. Vários deles estão familiarizados para pessoas com experiência na shells específicos ou ambientes de programação, mas muito poucas pessoas irão conhecer todos eles. Alguns destes conceitos observar fornece uma descrição útil de shell.

### <a name="commands-are-not-text-based"></a>Os comandos não são baseados em texto
Ao contrário dos comandos de interface de linha de comandos tradicionais, do Windows PowerShell cmdlets foram concebidos para lidar com objetos - estruturados informações que são mais do que apenas uma cadeia de carateres, volte a aparecer no ecrã. Acarreta sempre a saída do comando ao longo de informações adicionais que pode utilizar se o ficheiro necessário. Este tópico em profundidade neste documento, vamos abordar.

Se utilizou as ferramentas de processamento de texto para processar os dados da linha de comandos no passado, irá encontrar-se de que estes se comportam de forma diferente se tentar utilizá-los no Windows PowerShell. Na maioria dos casos, não precisa de ferramentas de processamento de texto para extrair informações específicas. Pode aceder a partes dos dados diretamente utilizando comandos de manipulação de objeto do padrão do Windows PowerShell.

### <a name="the-command-family-is-extensible"></a>A família de comando é extensível
Interfaces como Cmd.exe não fornecem uma forma de diretamente alargar o conjunto de comandos incorporada. Pode criar as ferramentas da linha de comandos externas que são executados em Cmd.exe, mas estas ferramentas externas não dispõe de serviços, como a integração de ajuda, e Cmd.exe não automaticamente saibam que conseguem comandos válidos.

O binário nativo comandos no Windows PowerShell, conhecido como *cmdlets* (pronuncia-se comando-lets), podem ser aumentados pelos cmdlets que criar e que adiciona ao Windows PowerShell utilizando o snap-ins. Windows PowerShell *snap-ins* são compilados, tal como binárias ferramentas em qualquer outra interface. Pode utilizá-los para adicionar fornecedores do Windows PowerShell para o shell, bem como os novos cmdlets.

Devido à natureza especial dos comandos internas do Windows PowerShell, iremos dá-los como *cmdlets*.

> [!NOTE]
> Windows PowerShell, pode executar comandos que não sejam cmdlets. Iremos será não ser debatê-los em detalhe no Guia do utilizador do Windows PowerShell, mas são úteis para conhecer as categorias dos tipos de comando. O Windows PowerShell suporta scripts que são análogos a scripts de shell de UNIX e os ficheiros de batch Cmd.exe, mas tem uma extensão de nome de ficheiro. ps1. Também o Windows PowerShell permite-lhe criar funções internas, que podem ser utilizadas diretamente na interface ou em scripts.

### <a name="windows-powershell-handles-console-input-and-display"></a>Entrada da consola do Windows PowerShell identificadores e apresentar
Quando escreve um comando, do Windows PowerShell sempre processa a entrada da linha de comandos diretamente. Windows PowerShell também formata o resultado que vê no ecrã. O que é significativo porque esta reduz o trabalho necessário de cada cmdlet e assegura que pode sempre fazer coisas da mesma forma, independentemente da que cmdlet estiver a utilizar. Um exemplo de como Isto simplifica vida para os programadores de ferramenta e os utilizadores é ajuda da linha de comandos.

Ferramentas tradicionais de linha de comandos tem os seus próprios esquemas para pedir e apresentar a ajuda. Algumas ferramentas de linha de comandos utilizam **/?** para acionar a apresentação de ajuda; outras pessoas utilizam **-?**, **/H**, ou mesmo **//**. Algumas irão apresentar a ajuda numa janela de GUI, em vez de na apresentação de consola. Algumas ferramentas complexas, tais como updaters de aplicação, descompacte internos ficheiros antes de apresentar os respetivos ajuda. Se utilizar o parâmetro incorreto, a ferramenta poderá ignorar que escreveu e começar a executar automaticamente uma tarefa.

Ao introduzir um comando no Windows PowerShell, tudo o que introduz é analisado e automaticamente pré-processado pelo Windows PowerShell. Se utilizar o **-?** parâmetro com um cmdlet do Windows PowerShell, sempre significa "Mostrar ajuda para este comando". Os programadores de cmdlet não dispõe de analisar o comando; apenas necessário fornecer o texto de ajuda.

É importante compreender que estão disponíveis as funcionalidades de ajuda do Windows PowerShell, mesmo quando executar ferramentas tradicionais de linha de comandos do Windows PowerShell. Windows PowerShell processa os parâmetros e transmite os resultados para as ferramentas externas.

> [!NOTE]
> Se executar uma aplicação de gráfico no Windows PowerShell, abre-se a janela para a aplicação. Windows PowerShell intervenes apenas quando a processar a linha de comandos de entrada tem alimentação ou o resultado de aplicação devolvido para a janela de consola; -não afeta a forma como a aplicação funciona internamente.

### <a name="windows-powershell-uses-some-c-syntax"></a>O Windows PowerShell utiliza algumas sintaxe c#
Windows PowerShell tem funcionalidades de sintaxe e palavras-chave que são muito semelhantes às utilizadas no c# programação idioma, porque o Windows PowerShell é baseado no .NET Framework. Aprendizagem do Windows PowerShell tornarão mais fácil e saber c#, se estiver interessado no idioma.

Se não tiver um programador de c#, este semelhança não é importante. No entanto, se já estiver familiarizado com c#, as semelhanças podem tornar a aprendizagem muito mais fácil do Windows PowerShell.