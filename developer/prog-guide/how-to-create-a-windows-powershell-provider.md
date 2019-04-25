---
title: Como criar um provedor de PowerShell do Windows | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide]
- providers [PowerShellProgrammer's Guide], creating
- Windows PowerShell Programmer's Guide, providers
ms.assetid: 863e48e9-7206-4c6a-a59a-2ab2d30396bc
caps.latest.revision: 5
ms.openlocfilehash: 06910f32752668f13400f9be0767a2179133df04
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081755"
---
# <a name="how-to-create-a-windows-powershell-provider"></a>How to Create a Windows PowerShell Provider (Como Criar um Fornecedor do Windows PowerShell)

Esta secção descreve como criar um fornecedor de Windows PowerShell. Um fornecedor de Windows PowerShell pode ser considerado de duas formas. Para o usuário, o fornecedor representa um conjunto de dados armazenados. Por exemplo, os dados armazenados podem ser a Metabase dos serviços de informação Internet (IIS), o Registro do Microsoft Windows, o sistema de ficheiros do Windows, Active Directory e os dados de variável e alias armazenados pelo Windows PowerShell.

Para o desenvolvedor, o fornecedor de Windows PowerShell é a interface entre o utilizador e os dados que o utilizador precisa de acesso. Sob essa perspectiva, cada tipo de fornecedor descrita nesta secção suporta um conjunto de classes de bases específicas e interfaces que permitem que o tempo de execução do Windows PowerShell para expor determinados cmdlets para o utilizador de uma maneira comum.

## <a name="providers-provided-by-windows-powershell"></a>Provedores fornecidos pelo Windows PowerShell

Windows PowerShell fornece vários fornecedores (por exemplo, o fornecedor do sistema de ficheiros, o fornecedor de registo e o fornecedor de Alias) que são utilizados para aceder aos arquivos de dados conhecidos. Para obter mais informações sobre os fornecedores fornecidos pelo Windows PowerShell, utilize o seguinte comando para aceder à ajuda online:

**PS > get-help about_providers**

## <a name="accessing-the-stored-data-using-windows-powershell-paths"></a>Acessar os dados armazenados através de caminhos do Windows PowerShell

Fornecedores de Windows PowerShell estão acessíveis para o tempo de execução do Windows PowerShell e a comandos por meio de programação com o uso de caminhos do Windows PowerShell. A maioria das vezes, estes caminhos são usados para acessar diretamente os dados por meio do provedor. No entanto, alguns caminhos podem ser resolvidos em caminhos de fornecedor interno que permitem que um cmdlet para utilizar interfaces de programação de aplicações (APIs) não - Windows PowerShell para acessar os dados. Para obter mais informações sobre como os fornecedores de Windows PowerShell funcionam no Windows PowerShell, consulte [como o Windows PowerShell funciona](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

## <a name="exposing-provider-cmdlets-using-windows-powershell-drives"></a>Unidades de expor Cmdlets de fornecedor com o Windows PowerShell

Um fornecedor de Windows PowerShell expõe seus cmdlets suportados com unidades virtuais do Windows PowerShell. Windows PowerShell aplica-se as seguintes regras para uma unidade do Windows PowerShell:

- O nome de uma unidade pode ser qualquer sequência de alfanumérica.

- Uma unidade pode ser especificada em qualquer ponto válido num caminho, chamado "raiz".

- Uma unidade pode ser implementada para todos os dados armazenados, não apenas o sistema de ficheiros.

- Cada unidade mantém sua própria localização atual do trabalho, permitindo que o usuário manter o contexto quando mudar entre unidades.

## <a name="in-this-section"></a>Nesta Secção

A tabela seguinte apresenta uma lista de tópicos que incluem exemplos de código que completam. A partir do segundo tópico, o fornecedor básico do Windows PowerShell pode ser inicializado e não inicializado pelo tempo de execução do Windows PowerShell, o próximo tópico adiciona funcionalidade para acessar os dados, o próximo tópico adiciona funcionalidade para manipular o (de dados os itens de dados armazenados), e assim por diante.

|Tópico|Definição|
|-----------|----------------|
|[Estruturar o seu fornecedor do Windows PowerShell](./designing-your-windows-powershell-provider.md)|Este tópico aborda as coisas que deve considerar antes de implementar um fornecedor de Windows PowerShell. Resume as classes de bases de fornecedor de Windows PowerShell e interfaces que são utilizados.|
|[Criar um fornecedor de PowerShell do Windows básica](./creating-a-basic-windows-powershell-provider.md)|Este tópico mostra como criar um fornecedor de Windows PowerShell que permite que o tempo de execução do Windows PowerShell inicializar e uninitialize o fornecedor.|
|[Criar um fornecedor de unidade do PowerShell do Windows](./creating-a-windows-powershell-drive-provider.md)|Este tópico mostra como criar um fornecedor de Windows PowerShell que permite ao usuário acessar um arquivo de dados por meio de uma unidade do Windows PowerShell.|
|[Criar um fornecedor de Item de PowerShell do Windows](./creating-a-windows-powershell-item-provider.md)|Este tópico mostra como criar um fornecedor de Windows PowerShell que permite ao usuário manipular os itens num arquivo de dados.|
|[Criar um fornecedor de contentor do Windows PowerShell](./creating-a-windows-powershell-container-provider.md)|Este tópico mostra como criar um fornecedor de Windows PowerShell que permite ao usuário trabalhar em arquivos de dados multicamada.|
|[Criar um fornecedor de navegação do Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md)|Este tópico mostra como criar um fornecedor de Windows PowerShell que permite que o usuário navegue os itens de um arquivo de dados de uma forma hierárquica.|
|[Criar um fornecedor de conteúdo do PowerShell do Windows](./creating-a-windows-powershell-content-provider.md)|Este tópico mostra como criar um fornecedor de Windows PowerShell que permite ao usuário manipular o conteúdo dos itens num arquivo de dados.|
|[Criar um fornecedor de propriedade do PowerShell do Windows](./creating-a-windows-powershell-property-provider.md)|Este tópico mostra como criar um fornecedor de Windows PowerShell que permite ao usuário manipular as propriedades de itens num arquivo de dados.|

## <a name="see-also"></a>Veja Também

[Como funciona o Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[SDK do Windows PowerShell](../windows-powershell-reference.md)

[Guia do programador do Windows PowerShell](./windows-powershell-programmer-s-guide.md)
