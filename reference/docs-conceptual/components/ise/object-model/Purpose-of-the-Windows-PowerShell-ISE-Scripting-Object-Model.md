---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Objetivo do Modelo de Objeto de Processamento de Scripts do ISE do Windows PowerShell
ms.openlocfilehash: e59593ef06911c709e92fa7a1eabd96d2636ca30
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030909"
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a>Objetivo do Modelo de Objeto de Processamento de Scripts do ISE do Windows PowerShell

Objetos estão associados com o formulário e a função do Windows PowerShell Integrated Scripting Environment (ISE). A referência de modelo de objeto fornece detalhes sobre o membro, propriedades e métodos que expõem esses objetos. São fornecidos exemplos para mostrar como pode usar scripts para aceder diretamente a esses métodos e propriedades. O modelo de objeto de script torna mais fácil do seguinte intervalo de tarefas.

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a>Personalizando a aparência do ISE do Windows PowerShell

Pode utilizar o modelo de objeto para modificar as opções e definições da aplicação. Por exemplo, pode modificá-los da seguinte forma:

- Pode alterar a cor de erros, avisos, saídas verbosas, depuração e dá como.
- Pode obter ou definir as cores de fundo para o painel de comando, o painel de resultados e o painel de scripts.
- Pode definir a cor de primeiro plano para o painel de resultados.
- Pode definir o nome da fonte e tamanho da fonte para o Windows PowerShell ISE.
- Pode configurar avisos. Esta definição inclui avisos que são emitidos quando um ficheiro é aberto em várias guias do PowerShell, ou quando um script no ficheiro é executado antes do ficheiro foi guardado.
- Pode alternar entre uma vista onde o painel de Script e o painel de saída são lado a lado e uma vista onde o painel de scripts está na parte superior do painel de resultados. Podem encaixar o painel de comando na parte inferior ou da parte superior do painel de saída.

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a>Melhorar a funcionalidade do Windows PowerShell ISE

Pode utilizar o modelo de objeto para aprimorar a funcionalidade do ISE do Windows PowerShell. Por exemplo, pode:

- Adicionar e modificar a instância do ISE do Windows PowerShell em si. Por exemplo, para alterar os menus, pode adicionar novos itens de menu e mapear os novos itens de menu para scripts.
- Crie scripts que executem algumas das tarefas que pode efetuar ao utilizar os comandos de menu e botões no ISE do Windows PowerShell. Por exemplo, pode adicionar, remover ou selecione um separador do PowerShell.
- Tarefas de complemento que podem ser executadas usando comandos de menu e botões. Por exemplo, pode mudar o nome de um separador do PowerShell.
- Manipular os buffers de texto para o painel de comando, o painel de resultados e o painel de scripts que estão associados um ficheiro. Por exemplo, pode:
  - Obter ou definir todo o texto.
  - Obter ou definir uma seleção de texto.
  - Executar um script ou execute uma parte selecionada de um script.
  - Desloque-se de uma linha numa vista.
  - Inserir texto numa posição do sinal de interpolação.
  - Selecione um bloco de texto.
  - Obtenha o último número de linha.
- Realizar operações de ficheiros. Por exemplo, pode:
  - Abrir um arquivo, salvar um arquivo ou guardar um ficheiro com um nome diferente.
  - Determine se um ficheiro foi alterado depois de guardado pela última vez.
  - Obtenha o nome de ficheiro.
  - Selecione um ficheiro.

## <a name="automating-tasks"></a>Automatização de tarefas

Pode utilizar o modelo de objeto de script para criar atalhos de teclado para operações frequentes.

## <a name="see-also"></a>Consulte também

- [Hierarquia do Modelo de Objeto ISE](The-ISE-Object-Model-Hierarchy.md)
