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
ms.openlocfilehash: f58e8ecb67238939e90d4c5650bddd03da3c9409
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851752"
---
# <a name="resource-parameters"></a>Resource Parameters (Parâmetros de Recurso)

A tabela seguinte lista os nomes recomendados e a funcionalidade para os parâmetros de recurso. Para estes parâmetros, os recursos podem ser o assembly que contém a classe cmdlet ou o aplicativo de host que está a executar o cmdlet.

Tipo de dados de aplicação: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar uma aplicação.

Tipo de dados do Assembly: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar um assembly.

Tipo de dados de atributo: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar um atributo.

Tipo de dados de classe: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar uma classe do Microsoft .NET Framework.

Tipo de dados de cluster: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar um cluster.

Tipo de dados de cultura: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar a cultura para executar o cmdlet.

Tipo de dados do domínio: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar o nome de domínio.

Tipo de dados de unidade: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar um nome de unidade.

Tipo de dados do evento: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar um nome de evento.

Tipo de dados de interface: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar um nome de interface de rede.

Tipo de dados de IpAddress: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar um endereço IP.

Tipo de dados de tarefa: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar uma tarefa.

Tipo de dados de LiteralPath: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar o caminho para um recurso quando não são suportados carateres universais. (Utilize o `Path` parâmetro quando são suportados carateres universais.)

Tipo de dados de MAC: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar um endereço de controlador (MAC) de acesso de suporte de dados.

Tipo de dados de ParentId: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar o identificador principal.

Tipo de dados de caminho: String, String[]

Implemente este parâmetro para que o utilizador pode indicar os caminhos a um recurso quando são suportados carateres universais. (Utilize o `LiteralPath` parâmetro quando não são suportados carateres universais.)

Recomendamos que desenvolva este parâmetro para que ele oferece suporte a sintaxe completa ": caminho do fornecedor" utilizada pelos fornecedores. Também recomendamos que desenvolva-lo para que ele funciona com fornecedores de tantas quanto possível.

Tipo de dados de porta: Número inteiro, cadeia de caracteres

Implemente este parâmetro para que o utilizador pode especificar um valor inteiro para funcionamento em rede ou um valor de cadeia de caracteres como "biztalk" para outros tipos de porta.

Tipo de dados de impressora: Número inteiro, cadeia de caracteres

Implemente este parâmetro para que o utilizador pode especificar a impressora para o cmdlet para utilizar.

Tipo de dados de tamanho: Int32

Implemente este parâmetro para que o utilizador pode especificar um tamanho.

Tipo de dados do NIF: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar um identificador de transação (NIF) para o cmdlet.

Tipo de dados de tipo: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar o tipo de recurso para operar.

Tipo de dados de URL: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar um localizador de recurso uniforme (URL).

Tipo de dados de utilizador: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar o respetivo nome ou o nome de outro utilizador.

## <a name="see-also"></a>Veja Também

[Parâmetros do cmdlet](./cmdlet-parameters.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
