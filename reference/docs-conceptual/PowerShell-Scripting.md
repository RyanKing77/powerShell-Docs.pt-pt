---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Script do PowerShell
ms.openlocfilehash: c6ba3abc2544834e2cbec16a524f79399a1d2599
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094056"
---
# <a name="powershell"></a>PowerShell

Baseado no .NET Framework, o PowerShell é um shell de linha de comandos baseada em tarefas e linguagem de script; foi concebido especificamente para os administradores de sistemas e usuários avançados, rapidamente a automatizar a administração de vários sistemas operacionais (Linux, macOS, Unix e Windows) e os processos relacionados com os aplicativos executados nesses sistemas operacionais.

## <a name="powershell-is-open-source"></a>O PowerShell é o código-fonte aberto

Código-fonte base do PowerShell está agora disponível no GitHub e aberta a contribuições da Comunidade.
Ver [PowerShell fonte no GitHub](https://github.com/powershell/powershell).

Pode começar com os bits que necessita em [PowerShell obter](https://github.com/PowerShell/PowerShell#get-powershell).
Ou, talvez, com um tour rápido, [introdução](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)

## <a name="powershell-design-goals"></a>Metas de design do PowerShell
PowerShell foi projetado para melhorar o ambiente de criação de scripts e linha de comandos, eliminando consideravelmente os problemas de longa data e a acrescentar novas funcionalidades.

### <a name="discoverability"></a>Capacidade de deteção
PowerShell torna mais fácil detetar os seus recursos. Por exemplo, para encontrar uma lista de cmdlets que ver e alterar os serviços do Windows, escreva:

```powershell
Get-Command *-Service
```

Depois de descobrir qual cmdlet realiza uma tarefa, pode saber mais sobre o cmdlet, utilizando o `Get-Help` cmdlet.
Por exemplo, para apresentar a ajuda sobre o `Get-Service` cmdlet, tipo:

```powershell
Get-Help Get-Service
```
A maioria dos cmdlets emitir objetos que podem ser manipulados e, em seguida, processados em texto para exibição.
Para compreender totalmente o resultado desse cmdlet, encaminhar o resultado para o `Get-Member` cmdlet.
Por exemplo, o comando seguinte apresenta informações sobre os membros da saída de objeto pelo `Get-Service` cmdlet.

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a>Consistência
Gerenciamento de sistemas pode ser um empreendimento complexo e ferramentas que têm uma interface consistente ajudam a controlar a complexidade inerente.
Infelizmente, nem ferramentas da linha de comandos como objetos de COM programável por scripts já são conhecidos sua consistência.

A consistência do PowerShell é um de seus ativos primários.
Por exemplo, se aprender a utilizar o `Sort-Object` cmdlet, pode usar esse conhecimento para ordenar a saída de qualquer cmdlet.
Não é necessário que saber as rotinas de classificação diferentes de cada cmdlet.

Além disso, os desenvolvedores de cmdlet não tem a criação de funcionalidades de classificação para os seus cmdlets.
PowerShell dá a eles uma estrutura que fornece as funcionalidades básicas e força-os para ser consistente sobre muitos aspectos da interface.
O framework elimina algumas das opções que são normalmente deixadas para o desenvolvedor, mas, em troca, torna o desenvolvimento dos cmdlets robustos e fácil de usar muito mais simples.

### <a name="interactive-and-scripting-environments"></a>Ambientes de criação de scripts e interativos
PowerShell é um ambiente de criação de scripts e interativo combinado que lhe dá acesso a ferramentas de linha de comandos e objetos COM e também permite-lhe utilizar o poder do .NET Framework Class Library (FCL).

Neste ambiente melhora após o Windows linha de comandos, que fornece um ambiente interativo com várias ferramentas de linha de comandos.
Ele também oferecer melhorias em scripts do Windows Script Host (WSH), que lhe permite utilizar várias ferramentas de linha de comandos e objetos de automação COM, mas não fornecem um ambiente interativo.

Ao combinar o acesso a todos esses recursos, o PowerShell amplia a capacidade do usuário interativo e do escritor de script e torna a administração de sistema mais gerenciáveis.

### <a name="object-orientation"></a>Orientação a objeto
Embora interage com o PowerShell, digitando comandos em texto, o PowerShell se baseia em objetos, e não texto.
A saída de um comando é um objeto.
Pode enviar o objeto de saída para outro comando como entrada.
Como resultado, o PowerShell fornece uma interface familiar para pessoas experimentadas em outros shells, ao mesmo tempo apresentando um paradigma de linha de comandos novo e poderoso.
Ele estende o conceito de envio de dados entre comandos, permitindo-lhe para enviar a objetos, em vez de texto.

### <a name="easy-transition-to-scripting"></a>Transição fácil para a criação de scripts
PowerShell facilita facilita a transição de digitar comandos interativamente a criação e execução de scripts.
Pode escrever os comandos na linha de comando do PowerShell para descobrir os comandos que executam uma tarefa.
Em seguida, pode salvar esses comandos numa transcrição ou um histórico antes de copiá-los para um ficheiro para utilização como um script.
