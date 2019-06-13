---
ms.date: 08/23/2018
keywords: PowerShell, o cmdlet
title: Noções sobre conceitos importantes do PowerShell
ms.openlocfilehash: 8f9af370db46ea47dbccbabb7cc90fc27b8f2765
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030977"
---
# <a name="understanding-important-powershell-concepts"></a>Noções sobre conceitos importantes do PowerShell

O design de PowerShell integra-se os conceitos de muitos ambientes diferentes. Vários dos conceitos será familiares para pessoas com experiência em shells ou ambientes de programação. No entanto, algumas pessoas saberá sobre todos eles. Ver algumas desses conceitos fornece uma visão geral útil do shell.

## <a name="output-is-object-based"></a>O resultado é baseado no objeto

Ao contrário das interfaces de linha de comandos tradicionais, os cmdlets do PowerShell foram concebidos para lidar com objetos.
Um objeto é informações estruturadas, que é mais do que apenas a cadeia de caracteres que aparece na tela. Sempre a saída do comando transporta informações adicionais que podem ser utilizados se for necessário.

Se já usou as ferramentas de processamento de texto para processar dados no passado, verá que eles ter um comportamento diferente quando utilizado no PowerShell. Na maioria dos casos, não precisa de ferramentas de processamento de texto para extrair informações específicas. Aceder diretamente a partes de dados usando a sintaxe de objeto do PowerShell padrão.

## <a name="the-command-family-is-extensible"></a>A família de comando é extensível

Como interfaces **cmd.exe** não fornecem uma forma de estender diretamente o conjunto de comandos incorporada. Pode criar ferramentas de linha de comando externas que são executados em **cmd.exe**. Mas essas ferramentas externas não têm a serviços, como integração de ajuda. **cmd.exe** automaticamente não sabe que estas ferramentas externas são comandos válidos.

Os comandos nativos do PowerShell são conhecidos como *cmdlets* (pronuncia-se permite que o comando). Pode criar seus próprios módulos de cmdlets e funções com compilado código ou em scripts. Módulos podem adicionar os cmdlets e provedores para o shell. PowerShell também oferece suporte a scripts que são análogos aos scripts de shell de UNIX e **cmd.exe** arquivos em lote.

## <a name="powershell-handles-console-input-and-display"></a>PowerShell cuida de entrada do console e a exibição

Quando escreve um comando, PowerShell sempre processa a entrada de linha de comando diretamente. PowerShell também formata o resultado que vê no ecrã. Esta diferença será significativa, dado que reduz o trabalho necessário de cada cmdlet. Ele garante que pode sempre fazer coisas da mesma forma com qualquer cmdlet. Os desenvolvedores de cmdlet não precisam escrever código para analisar os argumentos da linha de comandos ou formatar a saída.

Ferramentas tradicionais de linha de comandos têm seus próprios esquemas para pedir e exibição de ajuda. Utilizam algumas ferramentas de linha de comando **/?** para disparar a exibição de ajuda; outras usam **-?** , **/H**, ou até mesmo **//** . Alguns irão apresentar a ajuda numa janela de GUI, em vez de na apresentação da consola. Se utilizar o parâmetro errado, a ferramenta poderá ignorar o que escreveu e começar a executar uma tarefa automaticamente.
Uma vez que o PowerShell automaticamente analisa e processa a linha de comandos, o **-?** parâmetro sempre significa "mostre-me ajuda para este comando".

> [!NOTE]
> Se executar uma aplicação de gráfica no PowerShell, é aberta a janela para a aplicação.
> PowerShell intervém apenas quando a linha de comandos de processamento de entrada fornecimento ou a saída do aplicativo retornado para a janela da consola. Não afeta como ele funciona internamente.

## <a name="powershell-uses-some-c-syntax"></a>PowerShell usa alguns C# sintaxe

PowerShell baseia-se no .NET Framework. Ele compartilha alguns recursos de sintaxe e palavras-chave com o C# linguagem de programação. Aprendizagem do PowerShell torna mais fácil aprender C#. Se já estiver familiarizado com o C#, essas semelhanças podem tornar a aprendizagem do PowerShell mais fácil.
