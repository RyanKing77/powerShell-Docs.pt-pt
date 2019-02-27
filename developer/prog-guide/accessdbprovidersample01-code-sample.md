---
title: Exemplo de código AccessDbProviderSample01 | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35540d2a-c18f-4179-b869-1a3dc5a8c1bd
caps.latest.revision: 6
ms.openlocfilehash: 01b95e18794501c2aff13d1e51b7400ae6fb8730
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849379"
---
# <a name="accessdbprovidersample01-code-sample"></a>AccessDbProviderSample01 Code Sample (Código de Exemplo AccessDbProviderSample01)

O código a seguir mostra a implementação do fornecedor de Windows PowerShell descrito em [criar um fornecedor de PowerShell básica do Windows](./creating-a-basic-windows-powershell-provider.md). Esta implementação fornece métodos para iniciar e parar o fornecedor e, embora ele não fornece um meio para aceder a um arquivo de dados ou para obter ou definir os dados no arquivo de dados, ela fornece a funcionalidade básica que sejam necessários para todos os fornecedores.

> [!NOTE]
> Pode transferir o C# ficheiro de origem (AccessDBSampleProvider01.cs) para este fornecedor com o Windows Software Development Kit para Windows Vista e o Microsoft .NET Framework 3.0 Runtime Components. Para obter instruções de transferência, consulte [como instalar o Windows PowerShell e transferir o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Os arquivos de fonte transferido estão disponíveis no  **\<exemplos do PowerShell >** diretório.
>
> Para obter mais informações sobre outras implementações de provedores do Windows PowerShell, consulte [conceber Windows PowerShell Fornecedor_de_e](./designing-your-windows-powershell-provider.md).

## <a name="code-sample"></a>Exemplo de código

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L11-L30 "AccessDBProviderSample01.cs")]

## <a name="see-also"></a>Veja Também

[Guia do programador do Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)