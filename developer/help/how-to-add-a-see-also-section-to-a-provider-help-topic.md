---
title: Como adicionar uma Veja também seção um tópico de ajuda do Provedor | Documentos da Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: f5c48fd04c620828a6e99c5c5424d11b31fd10e5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848455"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a>How to Add a See Also Section to a Provider Help Topic (Como Adicionar uma Secção Consulte Também ao Tópico de Ajuda de um Fornecedor)

Esta secção explica como preencher os **ver também** seção um tópico de ajuda do fornecedor.

O **ver também** secção consiste numa lista de tópicos que estão relacionadas com o fornecedor ou poderá ajudar o utilizador a compreender melhor e a utilizar o fornecedor. A lista de tópico pode incluir a ajuda do cmdlet, ajuda do provedor e conceitual ("sobre") tópicos de ajuda do Windows PowerShell. Ele também pode incluir referências a livros, papel e tópicos online, incluindo uma versão online do tópico de ajuda do fornecedor atual.

Quando consulte online tópicos, forneça o URI ou um termo de pesquisa em texto simples. O `Get-Help` cmdlet não ligar ou redirecionar para qualquer um dos tópicos na lista. Além disso, o `Online` parâmetro do `Get-Help` cmdlet não funciona com a ajuda do provedor.

A secção Consulte também é criada a partir do `RelatedLinks` elemento e as etiquetas que ele contém. O XML a seguir mostra como adicionar as etiquetas.

### <a name="to-add-see-also-topics"></a>Para adicionar "Consulte também" Tópicos

1. Na *AssemblyName*help.xml. dll do ficheiro, dentro da `providerHelp` elemento, adicionar um `RelatedLinks` elemento. O `RelatedLinks` elemento deve ser o último elemento no `providerHelp` elemento. Apenas um `RelatedLinks` elemento é permitido em cada tópico de ajuda do fornecedor.

   Por exemplo:

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. Para cada tópico na **Consulte também** secção, dentro do `RelatedLinks` elemento, adicionar um `navigationLink` elemento. Em seguida, dentro de cada `navigationLink` elemento, adicione uma `linkText` e um elemento `uri` elemento. Se não estiver a utilizar o `uri` elemento, pode adicioná-lo como um elemento vazio (\<uri / >).

   Por exemplo:

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> </linkText>
                <uri> </uri>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```

3. Escreva o nome de tópico entre o `linkText` etiquetas. Se está a fornecer um URI, escreva-entre o `uri` etiquetas. Para indicar a versão online do tópico de ajuda do fornecedor atual, entre o `linkText` etiquetas, tipo "versão Online:" em vez do nome de tópico. Normalmente, a "versão Online:" link é o primeiro tópico na lista de tópico Consulte também.

   O exemplo seguinte inclui três tópicos Consulte também. A primeira referem-se para a versão online do tópico atual. O segundo refere-se para um tópico de ajuda do cmdlet Windows PowerShell. A terceira refere-se para outro tópico online.

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> Online version: </linkText>
                <uri>http://www.fabrikam.com/help/myFunction.htm</uri>
            </navigationLink>
            <navigationLink>
                <linkText> about_functions </linkText>
                <uri/>
            </navigationLink>
            <navigationLink>
                <linkText> Windows PowerShell Getting Started Guide </linkText>
                <uri>http://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```