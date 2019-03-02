---
title: Parâmetros de recursos | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 460c43aa-f5c5-4a1a-a6f2-5e07db143de1
caps.latest.revision: 5
ms.openlocfilehash: 9752570e5c997ef4da56a08df14f39b77ba37a4a
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251205"
---
# <a name="resource-parameters"></a>Resource Parameters (Parâmetros de Recurso)

A tabela seguinte lista os nomes recomendados e a funcionalidade para os parâmetros de recurso. Para estes parâmetros, os recursos podem ser o assembly que contém a classe cmdlet ou o aplicativo de host que está a executar o cmdlet.

|Parâmetro|Funcionalidade|
|---|---|
|**Aplicação**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar uma aplicação.|
|**Assemblagem**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar um assembly.|
|**Atributo**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar um atributo.|
|**Classe**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar uma classe do Microsoft .NET Framework.|
|**Cluster**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar um cluster.|
|**cultura**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar a cultura para executar o cmdlet.|
|**Domínio**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar o nome de domínio.|
|**Drive**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar um nome de unidade.|
|**Event**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar um nome de evento.|
|**Interface**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar um nome de interface de rede.|
|**IpAddress**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar um endereço IP.|
|**Tarefa**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar uma tarefa.|
|**LiteralPath**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar o caminho para um recurso quando não são suportados carateres universais. (Utilize o **caminho** parâmetro quando são suportados carateres universais.)|
|**Mac**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar um endereço de controlador (MAC) de acesso de suporte de dados.|
|**ParentId**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar o identificador principal.|
|**Path**<br>Tipo de dados: String, String[]|Implemente este parâmetro para que o utilizador pode indicar os caminhos a um recurso quando são suportados carateres universais. (Utilize o **LiteralPath** parâmetro quando não são suportados carateres universais.) Recomendamos que desenvolva este parâmetro para que ele oferece suporte a toda a `provider:path` sintaxe usada pelos fornecedores. Também recomendamos que desenvolva-lo para que ele funciona com fornecedores de tantas quanto possível.|
|**Porta**<br>Tipo de dados: Número inteiro, cadeia de caracteres|Implemente este parâmetro para que o utilizador pode especificar um valor inteiro para funcionamento em rede ou um valor de cadeia de caracteres como "biztalk" para outros tipos de porta.|
|**Impressora**<br>Tipo de dados: Número inteiro, cadeia de caracteres|Implemente este parâmetro para que o utilizador pode especificar a impressora para o cmdlet para utilizar.|
|**Size**<br>Tipo de dados: Int32|Implemente este parâmetro para que o utilizador pode especificar um tamanho.|
|**TID**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar um identificador de transação (NIF) para o cmdlet.|
|**Tipo**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar o tipo de recurso para operar.|
|**URL**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar um localizador de recurso uniforme (URL).|
|**Utilizador**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar o respetivo nome ou o nome de outro utilizador.|

## <a name="see-also"></a>Veja Também

[Parâmetros do cmdlet](./cmdlet-parameters.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
