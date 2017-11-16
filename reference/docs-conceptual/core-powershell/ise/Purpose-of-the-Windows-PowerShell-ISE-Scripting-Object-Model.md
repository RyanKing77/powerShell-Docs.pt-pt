---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: Objetivo do Windows PowerShell ISE modelo de objeto de Scripting do
ms.assetid: d176a131-ab0c-43ee-80c1-f824ab8e4a05
ms.openlocfilehash: 3256d8bff3885d266f0db6f52932e40c4beaf8b1
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/08/2017
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a>Objetivo do Windows PowerShell ISE modelo de objeto de Scripting do
  Objetos associados a formulário e a função do Windows PowerShell Integrated Scripting Environment (ISE). A referência de modelo de objeto fornece detalhes sobre o membro, propriedades e métodos que estes objetos expõem. Os exemplos são fornecidos para mostrar a forma como pode utilizar scripts aceda diretamente a estes métodos e propriedades. O modelo de objeto de scripting facilita seguinte intervalo de tarefas.

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a>Personalizar o aspeto do ISE do Windows PowerShell
 Pode utilizar o modelo de objeto para modificar as definições da aplicação e as opções. Por exemplo, pode modificá-los da seguinte forma:

- Pode alterar a cor de erros, avisos, verbosas saídas e produz de depuração.

- Pode obter ou definir as cores de fundo para o painel de comando, o painel de resultados e o painel de Script.

- Pode definir a cor de primeiro plano para o painel de resultados.

- Pode definir o nome de tipo de letra e o tamanho de tipo de letra para o ISE do Windows PowerShell.

- Pode configurar avisos. Esta definição inclui avisos que são emitidos quando um ficheiro está aberto em vários separadores do PowerShell ou ao executar um script no ficheiro antes do ficheiro foi guardado.

- Pode alternar entre uma vista onde o painel de Script e o painel de resultados estão lado a lado e uma vista onde o painel de Script é na parte superior do painel de resultados. Pode ancoragem do painel de comando na parte inferior ou na parte superior do painel de resultados do.

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a>Otimização da funcionalidade do ISE do Windows PowerShell
 Pode utilizar o modelo de objeto para melhorar a funcionalidade do ISE do Windows PowerShell. Por exemplo, pode:

- Adicionar e modificar a instância do ISE do Windows PowerShell em si. Por exemplo, para alterar os menus, pode adicionar novos itens de menu e mapear os itens de menu novo scripts.

- Crie scripts que executar algumas das tarefas que pode realizar utilizando os comandos de menu e botões no ISE do Windows PowerShell. Por exemplo, pode adicionar, remover ou selecione um separador de PowerShell.

- Tarefas de complemento que podem ser efetuadas utilizando os botões e comandos de menu. Por exemplo, pode mudar o nome de um separador de PowerShell.

- Manipular memórias intermédias texto para o painel de comando, o painel de resultados e o painel de Script que estão associadas um ficheiro. Por exemplo, pode:

    -   Obter ou definir todo o texto.

    -   Obter ou definir uma selecção de texto.

    -   Executar um script ou executar uma parte de um script selecionada.

    -   Desloque-se de uma linha na vista.

    -   Inserir texto na posição acento circunflexo.

    -   Selecione um bloco de texto.

    -   Obter o último número de linha.

- Realizar operações de ficheiros. Por exemplo, pode:

    -   Abrir um ficheiro, guarde um ficheiro ou guardar um ficheiro ao utilizar um nome diferente.

    -   Determine se um ficheiro foi alterado após a última foi guardada.

    -   Obter o nome de ficheiro.

    -   Selecione um ficheiro.

## <a name="automating-tasks"></a>Automatizar tarefas
 Pode utilizar o modelo de objeto de scripting para criar atalhos de teclado para operações frequentes.

## <a name="see-also"></a>Consulte Também
- [A hierarquia de modelo de objeto ISE](The-ISE-Object-Model-Hierarchy.md) 
- [Referência de modelo de objeto do Windows PowerShell ISE](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [O ISE do Windows PowerShell modelo de objeto de Scripting](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
