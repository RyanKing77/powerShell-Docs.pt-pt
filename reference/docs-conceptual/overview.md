---
ms.date: 08/27/2018
keywords: PowerShell, o cmdlet
title: Script do PowerShell
ms.openlocfilehash: 281f2e798b3d3fa1c150b079d633cb7e8490dcec
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058493"
---
# <a name="powershell"></a>PowerShell

O PowerShell é um shell de linha de comandos baseada em tarefas e linguagem de script parte do .NET.
Os administradores de sistema de ajuda do PowerShell e usuários avançados rapidamente a automatizar tarefas que gerem os sistemas operativos (Linux, macOS e Windows) e os processos.

Comandos do PowerShell permitem-lhe gerir computadores a partir da linha de comando. Fornecedores de PowerShell permitem-lhe aceder aos arquivos de dados, como o registro e tão facilmente quanto acessar o sistema de ficheiros de arquivo, de certificados. PowerShell inclui um analisador de expressão avançada e uma linguagem de script inteiramente desenvolvida.

## <a name="powershell-is-open-source"></a>O PowerShell é o código-fonte aberto

Código-fonte base do PowerShell está agora disponível no GitHub e aberta a contribuições da Comunidade.
Ver [PowerShell fonte no GitHub](https://github.com/powershell/powershell).

Pode começar com os bits que necessita em [PowerShell obter](https://github.com/PowerShell/PowerShell#get-powershell).
Ou, talvez, com uma visita guiada às [introdução ao](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).

## <a name="powershell-design-goals"></a>Metas de design do PowerShell

PowerShell foi projetado para melhorar o ambiente de criação de scripts e linha de comandos, eliminando consideravelmente os problemas de longa data e a acrescentar novas funcionalidades.

### <a name="discoverability"></a>Capacidade de deteção

PowerShell torna mais fácil detetar os seus recursos. Por exemplo, para encontrar uma lista de cmdlets que ver e alterar os serviços do Windows, escreva:

```powershell
Get-Command *-Service
```

Depois de descobrir qual cmdlet realiza uma tarefa, pode saber mais sobre o cmdlet, utilizando o `Get-Help` cmdlet. Por exemplo, para apresentar a ajuda sobre o `Get-Service` cmdlet, tipo:

```powershell
Get-Help Get-Service
```

A maioria dos cmdlets retorno objetos que podem ser manipulados e, em seguida, composto como texto para exibição. Para compreender totalmente a saída de um cmdlet, encaminhar a saída para o `Get-Member` cmdlet. Por exemplo, o comando seguinte apresenta informações sobre os membros da saída de objeto pelo `Get-Service` cmdlet.

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a>Consistência

Gerenciamento de sistemas pode ser uma tarefa complexa. Ferramentas que têm uma interface consistente que ajudam a controlar a complexidade inerente. Infelizmente, as ferramentas da linha de comandos e objetos de modelo COM (Component Object) programável por scripts não são conhecidos por sua consistência.

A consistência do PowerShell é um de seus ativos primários. Por exemplo, se aprender a utilizar o `Sort-Object` cmdlet, pode usar esse conhecimento para ordenar a saída de qualquer cmdlet. Não precisa de saber as rotinas de classificação diferentes de cada cmdlet.

Além disso, os desenvolvedores de cmdlet não precisam de recursos de classificação para os seus cmdlets de design. PowerShell fornece uma estrutura com as funcionalidades básicas que força a consistência. O framework elimina algumas opções que restam para o desenvolvedor. Mas, em troca, torna o desenvolvimento dos cmdlets muito mais simples.

### <a name="interactive-and-scripting-environments"></a>Ambientes de criação de scripts e interativos

Linha de comandos do Windows fornece um shell interativo com o acesso a ferramentas de linha de comandos e scripts básica. Windows Script Host (WSH) tem ferramentas de linha de comando programável por scripts e objetos de automação COM, mas não fornece um shell interativo.

PowerShell combina um shell interativo e um ambiente de script. PowerShell pode acessar as ferramentas da linha de comandos, objetos COM e bibliotecas de classes do .NET. Esta combinação de funcionalidades estende os recursos do usuário interativo, o escritor de script e o administrador de sistema.

### <a name="object-orientation"></a>Orientação a objeto

PowerShell baseia-se no objeto não texto. A saída de um comando é um objeto. Pode enviar o objeto de saída, através do pipeline para outro comando como entrada.

Este pipeline fornece uma interface familiar para as pessoas experientes com outros shells. PowerShell expande este conceito ao enviar objetos em vez de texto.

### <a name="easy-transition-to-scripting"></a>Transição fácil para a criação de scripts

Facilita de capacidade de deteção de comando do PowerShell facilita a transição de digitar comandos interativamente a criação e execução de scripts. Transcrições de PowerShell e o histórico facilitam a copiar os comandos para um ficheiro para utilização como um script.
