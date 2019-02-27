---
title: Interpretar os objetos de ErrorRecord | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a65b964-5bc6-4ade-a66b-b6afa7351ce7
caps.latest.revision: 9
ms.openlocfilehash: d77e4daf25bfcd5e76c184f6dbdb619368627bfa
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847671"
---
# <a name="interpreting-errorrecord-objects"></a>Interpreting ErrorRecord Objects (Interpretar Objetos ErrorRecord)

Na maioria dos casos, um [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto representa um erro de não terminação gerado por um comando ou script. Erros de terminação também pode especificar as informações adicionais de um ErrorRecord através da [System.Management.Automation.Icontainserrorrecord](/dotnet/api/System.Management.Automation.IContainsErrorRecord) interface.

Se quiser escrever um manipulador de erros em seu script ou um anfitrião para lidar com erros específicos que ocorrem durante a execução de comando ou script, deve interpretar os [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) objecto para determinar se ele representa a classe de erro que deseja manipular.

Quando um cmdlet encontra acabar ou erro de não terminação, é necessário criar um registo de erro que descreve a condição de erro. O aplicativo host deve investigar estes registos de erro e efetuar a ação que irá reduzir o erro. O aplicativo host também deve investigar registos de erro para erros de não terminação que processou um registo, mas foram continuar e deve investigar registos de erro para erros de finalização que causou o pipeline parar.

> [!NOTE]
> Para erros de terminação, chama o cmdlet do [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) método. Para erros de não terminação, o cmdlet chama o [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método.

## <a name="error-record-design"></a>Design de registo de erro

Registos de erro foram concebidos para fornecer informações de erro adicionais que não estão disponíveis em exceções, garantindo que as informações combinadas em cada registo de erro são exclusivas. Este exclusividade permite que o aplicativo de host inspecionar as diferentes partes do registo de erro, para que ele pode identificar a condição de erro e a ação que o anfitrião tem de efetuar.

## <a name="interpreting-error-records"></a>Interpretar os registos de erro

Poderá rever as várias partes do registo de erros para identificar o erro. Essas partes incluem o seguinte:

- A categoria de erro

- A exceção de erro

- O identificador do erro completamente qualificado (FQID)

- Outras informações

### <a name="the-error-category"></a>A categoria de erro

A categoria de erro do registo de erro é um das constantes predefinidas fornecidas pelos [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumeração. Essas informações estão disponíveis através do [System.Management.Automation.Errorrecord.Categoryinfo*](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) propriedade da [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto.

O cmdlet pode especificar as categorias de CloseError, OpenError, InvalidType, ReadError e WriteError e outras categorias de erro. O aplicativo host pode utilizar a categoria de erro para capturar os grupos de erros.

### <a name="the-exception"></a>A exceção

A exceção incluída no registo de erro é fornecida pelo cmdlet e podem ser acessada através da [System.Management.Automation.Errorrecord.Exception*](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) propriedade do [ System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto.

Anfitrião de aplicações pode utilizar o `is` palavra-chave para identificar que a exceção é de uma classe específica ou de uma classe derivada. É melhor para o ramo no tipo de exceção, conforme mostrado no exemplo a seguir.

`if (MyNonTerminatingError.Exception is AccessDeniedException)`

Dessa forma, capturar as classes derivadas. No entanto, há problemas se a exceção é desserializada.

### <a name="the-fqid"></a>O FQID

O FQID é as informações mais específicas, que pode utilizar para identificar o erro. É uma cadeia que inclui um identificador definido pelo cmdlet, o nome da classe cmdlet e a origem que comunicou o erro. Em geral, um registo de erro é semelhante a um registo de eventos de um registo de eventos do Windows. O FQID é análogo à seguinte cadeia de identificação, o que identifica a classe do registo de eventos: (*nome do registo*, *origem*, *ID de evento*).

O FQID foi concebido para ser possível inspecioná-lo como uma única cadeia de caracteres. No entanto, os casos existem em que o identificador de erro foi concebido para ser analisado pelo aplicativo host. O exemplo seguinte é um identificador de erro completamente qualificado bem formado.

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand.`

No exemplo anterior, o token primeiro é o identificador de erro, o que é seguido do nome da classe cmdlet. O identificador de erro pode ser um único token, ou pode ser um identificador separado por ponto que permite a ramificação na inspeção do identificador. Não utilize espaços em branco ou pontuação no identificador de erro. É especialmente importante para não utilizar uma vírgula; uma vírgula é usada pelo Windows PowerShell para separar o identificador e o nome da classe cmdlet.

### <a name="other-information"></a>Outras informações

O [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto também pode fornecer informações que descrevem o ambiente em que ocorreu o erro. Estas informações incluem itens como detalhes do erro, informações de invocação e o objeto de destino que estava a ser processado quando ocorreu o erro. Embora estas informações poderão ser úteis para o aplicativo host, ele não é normalmente utilizado para identificar o erro. Essas informações estão disponíveis através das seguintes propriedades:

[System.Management.Automation.Errorrecord.Errordetails*](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails)

[System.Management.Automation.Errorrecord.Invocationinfo*](/dotnet/api/System.Management.Automation.ErrorRecord.InvocationInfo)

[System.Management.Automation.Errorrecord.Targetobject*](/dotnet/api/System.Management.Automation.ErrorRecord.TargetObject)

## <a name="see-also"></a>Consulte Também

[System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)

[System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[Adicionar relatórios de erros e seu Cmdlet de não terminação](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Relatório de erros do Windows PowerShell](./error-reporting-concepts.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
