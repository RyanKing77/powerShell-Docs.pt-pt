---
title: Exemplo de código AccessDbProviderSample04 | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9374c4a-e499-4516-9eb6-107c59df98d9
caps.latest.revision: 7
ms.openlocfilehash: 43f01b9cd6af3ab6c26f88ee0c1e9269499b2bc3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081959"
---
# <a name="accessdbprovidersample04-code-sample"></a>AccessDbProviderSample04 Code Sample (Código de Exemplo AccessDbProviderSample04)

O código a seguir mostra a implementação do fornecedor de Windows PowerShell descrito em [criar um fornecedor de contentor do Windows PowerShell](./creating-a-windows-powershell-container-provider.md). Este fornecedor funciona em arquivos de dados de multi camada. Para este tipo de arquivo de dados, o nível superior do arquivo contém os itens de raiz e cada nível subseqüente é referido como um nó de itens subordinados. Ao permitir que o utilizador trabalhar em de nós subordinados, um usuário pode interagir hierarquicamente por meio do arquivo de dados.

## <a name="code-sample"></a>Exemplo de código

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>Veja Também

[SDK do Windows PowerShell](../windows-powershell-reference.md)