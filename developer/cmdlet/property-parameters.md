---
title: Parâmetros de propriedade | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d17e0d66-42ea-4e4c-a85b-3ca09b146492
caps.latest.revision: 6
ms.openlocfilehash: cc0742b86a7a36e5712707c077fd1952691f3f4b
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251426"
---
# <a name="property-parameters"></a>Property Parameters (Parâmetros de Propriedade)

A tabela seguinte lista os nomes recomendados e a funcionalidade para os parâmetros de propriedade.

|Parâmetro|Funcionalidade|
|---|---|
|**Contagem**<br>Tipo de dados: Int32|Implemente este parâmetro para que o utilizador pode especificar o número de objetos a serem processados.|
|**Descrição**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar uma descrição para um recurso.|
|**De**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar o objeto de referência para obter informações do.|
|**Id**<br>Tipo de dados: Recursos dependentes|Implemente este parâmetro para que o utilizador pode especificar o identificador de um recurso.|
|**Input (Entrada)**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar a especificação do ficheiro de entrada.|
|**Localização**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar a localização do recurso.|
|**LogName**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar o nome do ficheiro de registo para processar ou utilizar.|
|**Nome**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar o nome do recurso.|
|**Saída**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar o ficheiro de saída.|
|**Proprietário**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar o nome do proprietário do recurso.|
|**Propriedade**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar o nome ou os nomes das propriedades a utilizar.|
|**Reason**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar o motivo pelo qual este cmdlet está sendo solicitado.|
|**Regex**<br>Tipo de dados: SwitchParameter|Implemente este parâmetro para que as expressões regulares são utilizadas quando o parâmetro for especificado. Quando este parâmetro for especificado, os carateres universais não são resolvidos.|
|**velocidade**<br>Tipo de dados: Int32|Implemente este parâmetro para que o utilizador pode especificar a taxa de transmissão. O utilizador define este parâmetro para a velocidade do recurso.|
|**Estado**<br>Tipo de dados: Matriz de palavra-chave|Implemente este parâmetro para que o utilizador pode especificar os nomes dos Estados, como KEYDOWN.|
|**Valor**<br>Tipo de dados: Objeto|Implemente este parâmetro para que o utilizador pode especificar um valor para fornecer ao cmdlet.|
|**Versão**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar a versão da propriedade.|

## <a name="see-also"></a>Veja Também

[Parâmetros do cmdlet](./cmdlet-parameters.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
