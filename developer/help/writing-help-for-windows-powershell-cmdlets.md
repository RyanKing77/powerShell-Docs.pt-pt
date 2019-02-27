---
title: Escrever ajuda para Cmdlets do PowerShell | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848112"
---
# <a name="writing-help-for-powershell-cmdlets"></a>Escrever ajuda para Cmdlets do PowerShell

Cmdlets do PowerShell pode ser útil, mas, a menos que os tópicos de ajuda explicar claramente o que o cmdlet faz e como usá-lo, o cmdlet não pode ser usado ou, ainda pior, ele pode frustrar utilizadores.
O formato de arquivo de ajuda do cmdlet baseado em XML melhora a consistência, mas necessita de grande ajuda muito mais.

Se nunca escreveu a ajuda do cmdlet, reveja as seguintes diretrizes.
O esquema XML necessário para criar o tópico de ajuda do cmdlet é descrito na secção seguinte.
Começar com [criando o arquivo de ajuda do Cmdlet](./how-to-create-the-cmdlet-help-file.md).
Esse tópico inclui uma descrição de nós XML de nível superior.

## <a name="writing-guidelines-for-cmdlet-help"></a>Diretrizes de escrita para a ajuda do Cmdlet

### <a name="write-well"></a>Escrever bem
Nada substitui um tópico bem escrito.
Se não for um escritor profissional, localize um escritor ou o editor para ajudá-lo.
Outra alternativa é copiar o texto de ajuda no Microsoft Word e utilizar a gramática e ortografia verifica para melhorar o seu trabalho.

### <a name="write-simply"></a>Escrever simplesmente
Utilize palavras simples e expressões.
Evite jargão.
Considere que muitos leitores são equipados apenas com um dicionário em idiomas estrangeiros e seu tópico de ajuda.

### <a name="write-consistently"></a>Escrita de forma consistente
Ajuda de cmdlets relacionados deve ser semelhantes (por exemplo, get-x e set-x).
Utiliza as descrições de standard para os parâmetros padrão, como **força** e **InputObject**.
(Copiá-los de ajuda para os cmdlets de núcleo.) Utilize termos padrão.
Por exemplo, utilize "parâmetro", não ". o argumento" e utilização "cmdlet" não "comando" ou "command-let."

### <a name="start-the-synopsis-with-a-verb"></a>Inicie o sinopse com um verbo
O campo de sinopse informa o utilizador que o cmdlet não, o que é ou como ele funciona.
Verbos criar uma instrução baseado em tarefas que informa os utilizadores se este cmdlet cumpre os seus requisitos.
Utilize verbos de simples como "get", "Criar" e "alterar".
Evitar "set", que pode ser vaga e palavras bonitas como "Modificar".

### <a name="focus-on-objects"></a>Concentre-se em objetos
A maioria "get" cmdlets apresentar algo, mas sua função principal é obter um objeto.
Na sua ajuda, concentre-se no objeto, para que os utilizadores compreendam que a exibição padrão é uma das muitas e que pode utilizar os métodos e propriedades do objeto que obteve da-los de formas diferentes.

### <a name="write-detailed-descriptions"></a>Escrever descrições detalhadas
Liste resumidamente tudo o que o cmdlet pode fazer na descrição detalhada.
Se a função principal é alterar uma propriedade, mas o cmdlet pode alterar todas as propriedades, liste isso na descrição detalhada.

### <a name="use-conventional-syntax"></a>Utilize sintaxe convencional
Utilize o formato de Backus-Naur padrão que é comum para obter ajuda de linha de comando de UNIX e Windows.

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a>Utilizar tipos de Microsoft .NET Framework para valores de parâmetro
Os marcadores de posição para valores de parâmetro (nas descrições de sintaxe e parâmetros) mostram os tipos do .NET Framework os objetos que o parâmetro aceitará.
A equipe de PowerShell desenvolveu essa convenção para o ajudar a ensinar aos utilizadores como o .NET Framework.

### <a name="write-complete-parameter-descriptions"></a>Escrever descrições de parâmetros concluída
Descrições de parâmetros devem informar os utilizadores de duas coisas: o que o parâmetro não (seu efeito) e o que eles tem de escrever para os valores de parâmetro.

### <a name="write-practical-examples"></a>Exemplos práticos de escrita
Os exemplos devem mostram como utilizar todos os parâmetros, mas o mais importante é mostrar como utilizar o cmdlet no mundo real de tarefas.
Começar com um exemplo simples e escrever os exemplos de cada vez mais complexos.
O exemplo final, mostre como utilizar o cmdlet num pipeline.

### <a name="use-the-notes-field"></a>Utilize o campo de notas
Utilize o campo de notas para explicar conceitos que os utilizadores precisam compreender o cmdlet.
Também pode utilizar notas para ajudar os utilizadores a evitar erros comuns.
Evite URLs, à medida que eles mudam.
Em vez disso, forneça os termos de utilizadores a procurar.

### <a name="test-your-help"></a>Testar a sua ajuda
Teste a ajuda, tal como testar o seu código.
Tenho amigos e colegas ler o conteúdo de ajuda e fornecem comentários.
Também pode solicitar comentários dos grupos de notícias.

## <a name="see-also"></a>Veja Também

 [Como criar o ficheiro de ajuda do Cmdlet](./how-to-create-the-cmdlet-help-file.md)

 [Como adicionar o nome do Cmdlet e o resumo para um tópico de ajuda do Cmdlet](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [Como adicionar a descrição detalhada para um tópico de ajuda do Cmdlet](./how-to-add-a-cmdlet-description.md)

 [Como adicionar a sintaxe para um tópico de ajuda do Cmdlet](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Como adicionar parâmetros a um tópico de ajuda do Cmdlet](./how-to-add-parameter-information.md)

 [Como adicionar tipos de entrada para um tópico de ajuda do Cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Como adicionar valores de retorno para um tópico de ajuda do Cmdlet](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Como adicionar notas a um tópico de ajuda do Cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Como adicionar exemplos para um tópico de ajuda do Cmdlet](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Como adicionar Links relacionados a um tópico de ajuda do Cmdlet](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [SDK do Windows PowerShell](../windows-powershell-reference.md)