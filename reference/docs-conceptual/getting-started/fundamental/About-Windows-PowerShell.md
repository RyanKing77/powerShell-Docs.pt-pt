---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: Sobre o Windows PowerShell
ms.assetid: 979654ae-7994-47f8-be43-d79e7a140143
ms.openlocfilehash: 5e6d1bb4d8915ba3c83ba0020b959e444b5211cd
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2017
---
# <a name="about-windows-powershell"></a>Sobre o Windows PowerShell
Windows PowerShell foi concebido para melhorar o ambiente de linha de comandos e script, eliminando os problemas long-standing e adicionando novas funcionalidades.

## <a name="discoverability"></a>Capacidade de deteção
Windows PowerShell torna mais fácil detetar as respetivas funcionalidades. Por exemplo, para encontrar uma lista de cmdlets que ver e alterar os serviços do Windows, escreva:

```
Get-Command *-Service
```

Depois de descobrir qual cmdlet concretiza uma tarefa, pode saber mais sobre o cmdlet utilizando o cmdlet Get-Help. Por exemplo, para apresentar a ajuda sobre o cmdlet Get-Service, escreva:

```
Get-Help Get-Service
```
A maioria dos cmdlets emitir objetos que podem ser manipulados e, em seguida, apresentados em texto para apresentação. Para compreender o resultado que cmdlet, encaminhe o resultado para o cmdlet Get-membro. Por exemplo, o comando seguinte apresenta informações sobre os membros da saída de objeto pelo cmdlet Get-Service.

```
Get-Service | Get-Member
```

## <a name="consistency"></a>Consistência
Gestão de sistemas pode ser um endeavor complexa e ferramentas que tenha uma interface consistente ajudam a controlar a complexidade inerente. Infelizmente, não as ferramentas de linha de comandos nem pode ser passível de ter scripts objectos COM foi conhecidos para as suas consistência.

A consistência do Windows PowerShell é um dos respetivos recursos primários. Por exemplo, se irá aprender a utilizar o cmdlet Sort-Object, pode utilizar esse conhecimento para ordenar a saída de qualquer cmdlet. Não é necessário saber as rotinas de ordenação diferentes de cada cmdlet.

Além disso, os programadores de cmdlet não dispõe de funcionalidades de ordenação para os seus cmdlets de design. Windows PowerShell, fornece-lhes uma estrutura que fornece as funcionalidades básicas e força-os para estar consistente sobre muitos aspetos da interface. A estrutura elimina algumas das opções que normalmente são mantidas ao programador, mas, além return, torna o desenvolvimento dos cmdlets robustos e fácil de utilizar muito mais simples.

## <a name="interactive-and-scripting-environments"></a>Ambientes interativas e scripts
O Windows PowerShell é um ambiente combinado interativo e script que lhe dá acesso a objetos COM e ferramentas de linha de comandos e também permite-lhe utilizar a capacidade da biblioteca de classe do .NET Framework (FCL).

Este ambiente melhora após Windows linha de comandos, que fornece um ambiente com várias ferramentas da linha de comandos interativo. Melhora também após scripts de Script anfitrião para WSH (Windows), que lhe permitem utilizar várias ferramentas da linha de comandos e objetos de automatização COM, mas não fornece um ambiente interativo.

Ao combinar o acesso a todas estas funcionalidades, o Windows PowerShell expande a capacidade de utilizador interativo e o escritor de script e torna mais fácil gerir a administração de sistema.

## <a name="object-orientation"></a>Orientação do objeto
Apesar de interagir com o Windows PowerShell, escrevendo comandos em texto, do Windows PowerShell baseia-se em objetos, não texto. O resultado de um comando é um objeto. Pode enviar o objeto de resultado para outro comando como entrada. Como resultado, o Windows PowerShell fornece uma interface familiar para pessoas teve com outros shells ao introduzir uma paradigma novo e poderosa da linha de comandos. Se expande o conceito de enviar dados entre comandos, permitindo enviar objetos, em vez de texto.

## <a name="easy-transition-to-scripting"></a>Transição fácil para processamento de scripts
Windows PowerShell faz com que facilitam a transição de escrever os comandos interativamente para criar e executar scripts. Pode escrever comandos na linha de comandos do Windows PowerShell para detetar os comandos que executar uma tarefa. Em seguida, pode guardar os comandos num transcript ou um histórico antes copiá-las para um ficheiro para utilização como um script.

