---
title: Programador do Windows PowerShell&#39;guia de s | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows PowerShell Programmer's Guide
ms.assetid: f3aaf667-af84-4ea8-a5ad-d454d0d700b8
caps.latest.revision: 9
ms.openlocfilehash: 44a9c970d32dc6f98456227f8b02101280541dd9
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734883"
---
# <a name="windows-powershell-programmer39s-guide"></a>Programador do Windows PowerShell&#39;guia de s

Guia do programador, esta é direcionado para desenvolvedores que estejam interessados no fornecimento de um ambiente de linha de comandos de gestão para administradores de sistema. Windows PowerShell fornece uma forma simples para criar comandos de gestão que expõem os objetos .NET, enquanto permite que o Windows PowerShell fazer a maior parte do trabalho para.

No desenvolvimento de comando tradicionais, tem de escrever um analisador de parâmetro, um associador de parâmetro, filtros e todas as outras funcionalidades expostas por cada comando. Windows PowerShell fornece o seguinte para tornar mais fácil escrever comandos:

- Um poderoso Windows runtime do PowerShell (motor de execução) com seu próprio analisador e um mecanismo para ligar automaticamente os parâmetros de comando.

- Utilitários para formatar e exibir os resultados de comando usando um interpretador de linha de comandos (CLI).

- Suporte para altos níveis de funcionalidade (através de fornecedores de Windows PowerShell) que o tornam fácil aceder aos dados armazenados.

  A pequena custo, pode representar um objeto .NET por um comando avançado ou um conjunto de comandos que oferecem uma experiência completa de linha de comandos para o administrador.

  A próxima seção aborda os principais conceitos do Windows PowerShell e os termos. Familiarize-se com esses conceitos e termos antes de iniciar o desenvolvimento.

## <a name="about-windows-powershell"></a>Acerca do Windows PowerShell

Windows PowerShell define vários tipos de comandos que podem ser usados no desenvolvimento. Estes comandos incluem: as funções, filtros, scripts, aliases e executáveis (aplicações). O tipo de comando principal, discutido neste guia é um comando simple, pequeno, chamado "cmdlet". Windows PowerShell furnishes um conjunto de cmdlets e suporta totalmente a personalização de cmdlet de acordo com seu ambiente. O tempo de execução do Windows PowerShell processa todos os tipos de comando, tal como cmdlets, utilizando pipelines.

Além de comandos, o Windows PowerShell suporta vários fornecedores de Windows PowerShell personalizáveis que tornam disponíveis conjuntos específicos de cmdlets. O shell deve operar dentro do aplicativo de host fornecido com o Windows PowerShell (Windows PowerShell.exe), mas é igualmente acessível a partir de um aplicativo de host personalizados que podem ser desenvolvidos para atender aos requisitos específicos. Para obter mais informações, consulte [como o Windows PowerShell funciona](/previous-versions//ms714658(v=vs.85)).

### <a name="windows-powershell-cmdlets"></a>Cmdlets do Windows PowerShell

Um cmdlet é um comando simples que é utilizado no ambiente do Windows PowerShell. O tempo de execução do Windows PowerShell invoca estes cmdlets no contexto de scripts de automatização que são fornecidos na linha de comandos e o tempo de execução do Windows PowerShell também chama programaticamente pelas APIs do Windows PowerShell.

Para obter mais informações sobre os cmdlets, consulte [escrever um Cmdlet do Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md).

### <a name="windows-powershell-providers"></a>Provedores do Windows PowerShell

Na execução de tarefas administrativas, o utilizador poderá ter examinar os dados armazenados num arquivo de dados (por exemplo, o sistema de ficheiros, o Registro do Windows ou um arquivo de certificados). Para facilitar essas operações, o Windows PowerShell define um módulo chamado um fornecedor de Windows PowerShell que pode ser utilizado para aceder a um arquivo de dados específicos, como o Registro do Windows. Cada fornecedor suporta um conjunto de cmdlets relacionados dar ao usuário uma exibição simétrico dos dados no arquivo.

Windows PowerShell fornece o padrão de vários fornecedores de Windows PowerShell. Por exemplo, o fornecedor de registo oferece suporte a navegação e a manipulação do Registro do Windows. Chaves de registo são representadas como itens e valores de registo são tratados como propriedades.

Se expor um arquivo de dados que o utilizador terá de aceder, poderá ter de escrever seu próprio fornecedor de Windows PowerShell, conforme descrito em [criar provedores do Windows PowerShell](./how-to-create-a-windows-powershell-provider.md). Para obter mais informações aboutWindows provedores PowerShell, consulte [como o Windows PowerShell funciona](/previous-versions//ms714658(v=vs.85)).

### <a name="host-application"></a>Aplicativo de Host

Windows PowerShell inclui o padrão anfitrião aplicação powershell.exe, que é um aplicativo de console que interage com o usuário e hospeda o tempo de execução do Windows PowerShell com uma janela de console.

Raramente precisará escrever seu próprio aplicativo de host para o Windows PowerShell, embora a personalização é suportada. Um caso em que poderá ter sua própria aplicação é quando tem um requisito para uma interface GUI que é mais avançada do que a interface fornecida pelo aplicativo de host padrão. Também pode desejar um aplicativo personalizado quando são basear sua GUI na linha de comandos. Para obter mais informações, consulte [como criar um aplicativo de Host do Windows PowerShell](/powershell/developer/hosting/writing-a-windows-powershell-host-application).

### <a name="windows-powershell-runtime"></a>O tempo de execução do Windows PowerShell

O tempo de execução do Windows PowerShell é o motor de execução que implementa o processamento do comando. Ele inclui as classes que fornecem a interface entre o aplicativo host e comandos do Windows PowerShell e fornecedores. O tempo de execução do Windows PowerShell é implementado como um objeto de espaço de execução para a sessão atual do Windows PowerShell, que é o ambiente operacional em que o shell e os comandos executam. Para obter detalhes operacionais, consulte [como o Windows PowerShell funciona](/previous-versions//ms714658(v=vs.85)).

### <a name="windows-powershell-language"></a>Idioma do Windows PowerShell

O idioma do Windows PowerShell fornece funções de script e mecanismos para invocar comandos. Para informações completas de criação de scripts, consulte que a referência de idioma do Windows PowerShell fornecido com o Windows PowerShell.

### <a name="extended-type-system-ets"></a>Sistema de tipo de extensão (ETS)

Windows PowerShell fornece acesso a uma variedade de objetos diferentes, como o .NET e XML. Como conseqüência, o shell para apresentar uma abstração comum para todos os tipos de objeto usa seu sistema de tipo de extensão (ETS). A maioria das funcionalidades ETS são transparente para o usuário, mas o script ou um desenvolvedor .NET utiliza-o para os seguintes fins:

- Visualizar um subconjunto de membros de objetos específicos. Windows PowerShell fornece uma vista de "adaptada" dos vários tipos de objeto específico.

- Adicionar membros a objetos existentes.

- Acesso ao serializar objetos.

- Escrever personalizadas de objetos.

  Usando ETS, pode criar novos flexíveis "tipos" que são compatíveis com o idioma do Windows PowerShell. Se for um desenvolvedor de .NET, é possível trabalhar com objetos com a mesma semântica, como o idioma do Windows PowerShell se aplica aos scripts, por exemplo, para determinar se um objeto é avaliada como `true`.

  Para obter mais informações sobre ETS e como o Windows PowerShell usa os objetos, consulte [conceitos de objeto do Windows PowerShell](/powershell/scripting/learn/understanding-important-powershell-concepts?view=powershell-6).

## <a name="programming-for-windows-powershell"></a>Programação para o Windows PowerShell

Windows PowerShell define seu código para comandos, fornecedores e outros módulos de programa usando o .NET Framework. Não é se limita ao uso do Microsoft Visual Studio na criação de módulos personalizados para o Windows PowerShell, embora os exemplos fornecidos neste guia são conhecidos por executar nesta ferramenta. Pode usar qualquer linguagem .NET que oferece suporte a herança de classe e o uso de atributos. Em alguns casos, as APIs do Windows PowerShell exigir que a linguagem de programação para poder aceder a tipos genéricos.

## <a name="programmers-reference"></a>Referência do Programador

Para referência ao desenvolver para o Windows PowerShell, consulte a [SDK do Windows PowerShell](../windows-powershell-reference.md).

## <a name="getting-started-using-windows-powershell"></a>Começar a usar o Windows PowerShell

Para obter mais informações sobre como começar a utilizar a shell do Windows PowerShell, consulte a [introdução ao Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell) fornecido com o Windows PowerShell. Um documento de três fases de referência rápida também é fornecido como um manual para utilização do cmdlet.

## <a name="contents-of-this-guide"></a>Conteúdo deste guia

|Tópico|Definição|
|-----------|----------------|
|[Como criar um fornecedor do Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)|Esta secção descreve como criar um fornecedor de Windows PowerShell para o Windows PowerShell.|
|[Como criar um aplicativo de Host de PowerShell do Windows](/powershell/developer/hosting/writing-a-windows-powershell-host-application)|Esta secção descreve como escrever um aplicativo de host que manipula um espaço de execução e como escrever um aplicativo de host que implementa o seu próprio host personalizado.|
|[Como criar um Snap-in do PowerShell do Windows](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)|Esta secção descreve como criar um snap-in que é utilizado para registar todos os cmdlets e provedores num assembly e como criar um snap-in personalizado.|
|[Como criar um Shell do Console](./how-to-create-a-console-shell.md)|Esta secção descreve como criar um shell de consola que não é extensível.|
|[Conceitos do Windows PowerShell](./windows-powershell-concepts.md)|Esta secção contém informações conceituais que irão ajudar a compreender o Windows PowerShell do ponto de vista de um desenvolvedor.|

## <a name="see-also"></a>Veja Também

[SDK do Windows PowerShell](../windows-powershell-reference.md)
