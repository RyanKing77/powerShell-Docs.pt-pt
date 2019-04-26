---
title: Formatar parâmetros | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068118"
---
# <a name="format-parameters"></a>Format Parameters (Parâmetros de Formatação)

A tabela seguinte apresenta uma lista de nomes recomendados e funcionalidades para os parâmetros que são usadas para formatar ou para gerar dados.

|Parâmetro|Funcionalidade|
|---|---|
|**Como**<br>Tipo de dados: Palavra-chave|Implemente este parâmetro para especificar o formato de saída do cmdlet. Por exemplo, os valores possíveis podem ser texto ou de Script.|
|**binário**<br>Tipo de dados: SwitchParameter|Implemente este parâmetro para indicar que o cmdlet processa valores binários.|
|**Codificação**<br>Tipo de dados: Palavra-chave|Implemente este parâmetro para especificar o tipo de codificação que é suportado. Por exemplo, os valores possíveis poderiam ser ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte e cadeia de caracteres.|
|**NewLine**<br>Tipo de dados: SwitchParameter|Implemente este parâmetro para que os carateres de nova linha são suportados quando o parâmetro for especificado.|
|**ShortName**<br>Tipo de dados: SwitchParameter|Implemente este parâmetro, de modo a que os nomes abreviados são suportados quando o parâmetro for especificado.|
|**Width**<br>Tipo de dados: Int32|Implemente este parâmetro para que o utilizador pode especificar a largura do dispositivo de saída.|
|**Encapsular**<br>Tipo de dados: SwitchParameter|Implemente este parâmetro para que a quebra automática é suportada quando o parâmetro for especificado.|
## <a name="see-also"></a>Veja Também

[Parâmetros do cmdlet](./cmdlet-parameters.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
