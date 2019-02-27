---
title: Registos de erro do Windows PowerShell | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error category [PowerShell SDK]
- error identifier [PowerShell SDK]
- error records [PowerShell SDK]
- error category string [PowerShell SDK]
ms.assetid: bdd66fea-eb63-4bb6-9cbe-9a799e5e0db5
caps.latest.revision: 9
ms.openlocfilehash: bbe04a8fb556f0f6807bc0eae6634e3cf505759e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850996"
---
# <a name="windows-powershell-error-records"></a>Windows PowerShell Error Records (Registos de Erros do Windows PowerShell)

Cmdlets tem de passar um [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto que identifica a condição de erro para erros de terminação e de não terminação.

O [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto contém as seguintes informações:

- A exceção que descreve o erro. Muitas vezes, esta é uma exceção de que o cmdlet detetada e convertidas em horas de um registo de erro. Todos os registos de erro tem de conter uma exceção.

Se o cmdlet não capturar uma exceção, tem de criar uma nova exceção e escolher a classe de exceção que melhor descreve a condição de erro. No entanto, não é necessário gerar a exceção porque podem ser acedido através da [System.Management.Automation.Errorrecord.Exception*](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) propriedade do [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto.

- Um identificador de erro que fornece um designador de destino que pode ser utilizado para fins de diagnóstico e, por scripts do Windows PowerShell para lidar com condições de erro específico com os manipuladores de erro específico. Todos os registos de erro tem de conter um identificador de erro (consulte o identificador de erro).

- Categoria de erro que fornece um designador de geral que pode ser utilizado para fins de diagnóstico. Todos os registos de erro tem de especificar uma categoria de erro (consulte a categoria de erro).

- Uma mensagem de erro de substituição opcional e uma ação recomendada (consulte a mensagem de erro de substituição).

- Informações de invocação opcional sobre o cmdlet que gerou o erro. Esta informação é especificada pelo Windows PowerShell (consulte a mensagem de invocação).

- O objeto de destino que estava a ser processado quando ocorreu o erro. Isso pode ser o objeto de entrada ou pode ser outro objeto que estava processar seu cmdlet. Por exemplo, para o comando `remove-item -recurse c:\somedirectory`, o erro pode ser uma instância de um objeto FileInfo para "c:\somedirectory\lockedfile". As informações do objeto de destino são opcionais.

## <a name="error-identifier"></a>Identificador de erro

Quando cria um registo de erro, especifique um identificador que designa a condição de erro no seu cmdlet. Windows PowerShell combina o identificador de destino com o nome do seu cmdlet para criar um identificador de erro completamente qualificado. O identificador do erro completamente qualificado pode ser acedido através da [System.Management.Automation.Errorrecord.Fullyqualifiederrorid*](/dotnet/api/System.Management.Automation.ErrorRecord.FullyQualifiedErrorId) propriedade do [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord)objeto. O identificador de erro não está disponível por si só. Está disponível apenas como parte do identificador completamente qualificado do erro.

Utilize as diretrizes seguintes para gerar os identificadores de erro ao criar registos de erro:

- Tornar os identificadores de erro específico para uma condição de erro. Os identificadores de erro de destino para fins de diagnóstico e para os scripts que lidar com condições de erro específico com os manipuladores de erro específico. Um utilizador deve ser capaz de usar o identificador de erro para identificar o erro e a respetiva origem. Identificadores de erro também ativar a geração de relatórios para condições de erro específico de exceções existentes para que não são necessárias novas subclasses de exceção.

- Em geral, atribua os identificadores de erro diferente a diferentes caminhos de código. O utilizador final se beneficia do identificadores específicos. Muitas vezes, cada caminho de código que chama [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) ou [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) tem seu próprio identificador. Como regra, define um novo identificador ao definir uma nova cadeia de modelo para a mensagem de erro e vice-versa. Não utilize a mensagem de erro como um identificador.

- Quando publica o código que usa um identificador de erro específico, o utilizador estabelece que a semântica de erros com esse identificador para o produto completo de ciclo de vida de suporte. Não reutilize-lo num contexto que é semanticamente diferente do contexto original. Se alterar a semântica deste erro, crie e, em seguida, utilize um novo identificador.

- Geralmente, deve utilizar um identificador de erro específico apenas para exceções de um determinado tipo CLR. Se alterar o tipo de exceção ou o tipo de objeto de destino, crie e, em seguida, utilize um novo identificador.

- Escolha o texto para o identificador de erro que concisa corresponde ao erro que estiver está a comunicar. Utilize as convenções padrão de nomenclatura e capitalização de .NET Framework. Não utilize espaços em branco ou pontuação. Não localize identificadores de erro.

- Não gere dinamicamente os identificadores de erro de forma não reproduzíveis. Por exemplo, não o incorporarem informações de erro como um ID de processo. Identificadores de erro são úteis apenas se eles correspondem aos identificadores de erro vistos por outros utilizadores que estão com a mesma condição de erro.

## <a name="error-category"></a>Categoria de erro

Quando cria um registo de erro, especificar a categoria de erro através de uma das constantes definidas pelos [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumeração. Windows PowerShell usa a categoria de erro para exibir informações de erro, aos usuários a `$ErrorView` variável à `"CategoryView"`.

Evite utilizar o [System.Management.Automation.Errorcategory.Notspecified](/dotnet/api/System.Management.Automation.ErrorCategory.NotSpecified) constante. Se tiver quaisquer informações sobre o erro ou a operação que causou o erro, escolha a categoria que melhor descreve o erro ou a operação, mesmo que a categoria não é uma combinação perfeita.

As informações apresentadas pelo Windows PowerShell são referidas como a cadeia de caracteres de vista de categorias e são criadas a partir das propriedades do [System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo) classe. (Essa classe é acessada através do erro [System.Management.Automation.Errorrecord.Categoryinfo*](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) propriedade.)

```
{Category}: ({TargetName}:{TargetType}):[{Activity}], {Reason}
```

A lista seguinte descreve as informações apresentadas:

- Categoria: Definido de Windows PowerShell [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) constante.

- TargetName: Por predefinição, o nome do objeto o cmdlet foi processamento quando ocorreu o erro. Ou outra cadeia definido pelo cmdlet.

- TargetType: Por predefinição, o tipo de objeto de destino. Ou outra cadeia definido pelo cmdlet.

- Atividade: Por predefinição, o nome do cmdlet que criou o registo de erro. Em alternativa, algumas outra cadeia definido pelo cmdlet.

- Motivo: Por predefinição, o tipo de exceção. Ou outra cadeia definido pelo cmdlet.

## <a name="replacement-error-message"></a>Mensagem de erro de substituição

Ao desenvolver um registo de erro para um cmdlet, a mensagem de erro padrão para o erro provém o texto da mensagem predefinido no [System.Exception.Message](/dotnet/api/System.Exception.Message) propriedade. Esta é uma propriedade só de leitura, cujo texto da mensagem destina-se apenas para fins de depuração (de acordo com as diretrizes do .NET Framework). Recomendamos que crie uma mensagem de erro que substitui ou aumenta o texto da mensagem predefinido. Torne a mensagem mais amigável e mais específicas para o cmdlet.

A mensagem de substituição é fornecida por um [System.Management.Automation.Errordetails](/dotnet/api/System.Management.Automation.ErrorDetails) objeto. Utilize um dos seguintes construtores deste objeto porque fornecem informações de localização adicionais que podem ser utilizadas pelo Windows PowerShell.

- [ErrorDetails.ErrorDetails (objeto de Cmdlet, a cadeia de caracteres, a cadeia de caracteres,\[System.Management.Automation.Errordetails.%23Ctor%28System.Management.Automation.Cmdlet%2Csystem.String%2Csystem.String%2Csystem.Object%5B%5D%29? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.ErrorDetails.%23ctor%28System.Management.Automation.Cmdlet%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29): Usar esse construtor, se a sua cadeia de caracteres do modelo é uma cadeia de caracteres de recurso no mesmo assembly em que o cmdlet é implementado ou se pretender carregar a cadeia de caracteres de modelo por meio de uma substituição do [System.Management.Automation.Cmdlet.Getresourcestring* ](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString) método.

- [ErrorDetails.ErrorDetails (objeto de assemblagem, cadeia, cadeia de caracteres,\[System.Management.Automation.Errordetails.%23Ctor%28System.Reflection.Assembly%2Csystem.String%2Csystem.String%2Csystem.Object%5B%5D%29? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.ErrorDetails.%23ctor%28System.Reflection.Assembly%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29): Usar esse construtor, se a cadeia de modelo é em outro assembly e carregá-los não por meio de uma substituição do [System.Management.Automation.Cmdlet.Getresourcestring*](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString).

A mensagem de substituição deve estar em conformidade com as diretrizes de design do .NET Framework para escrever mensagens de exceção com uma pequena diferença. O estado de diretrizes que mensagens de exceção devem ser escritas para desenvolvedores. Estas mensagens de substituição devem ser escritas para o utilizador de cmdlet.

A mensagem de erro de substituição tem de ser adicionada antes do [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) ou [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) são chamados de métodos . Para adicionar uma mensagem de substituição, defina o [System.Management.Automation.Errorrecord.Errordetails*](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails) propriedade do registo de erro. Quando essa propriedade é definida, o Windows PowerShell apresenta os [System.Management.Automation.Errordetails.Message*](/dotnet/api/System.Management.Automation.ErrorDetails.Message) propriedade em vez do texto da mensagem predefinido.

## <a name="recommended-action-information"></a>Recomendado de informações de ações

O [System.Management.Automation.Errordetails](/dotnet/api/System.Management.Automation.ErrorDetails) objeto também pode fornecer informações sobre quais ações são recomendadas quando ocorrer o erro.

## <a name="invocation-information"></a>Informações de invocação

Quando utiliza um cmdlet [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) ou [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) para reportar um registo de erro, o Windows PowerShell Adiciona automaticamente as informações que descrevem o comando que foi invocado quando ocorreu o erro. Estas informações são fornecidas por um [System.Management.Automation.Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo) objeto que contém o nome do cmdlet que foi invocado pelo comando, o comando em si e informações sobre o pipeline ou script. Esta propriedade é só de leitura.

## <a name="see-also"></a>Veja Também

[System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)

[System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System.Management.Automation.Errordetails](/dotnet/api/System.Management.Automation.ErrorDetails)

[System.Management.Automation.Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo)

[Relatório de erros do Windows PowerShell](./error-reporting-concepts.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
