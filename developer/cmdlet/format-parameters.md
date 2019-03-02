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
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251188"
---
# <a name="format-parameters"></a><span data-ttu-id="d2759-102">Format Parameters (Parâmetros de Formatação)</span><span class="sxs-lookup"><span data-stu-id="d2759-102">Format Parameters</span></span>

<span data-ttu-id="d2759-103">A tabela seguinte apresenta uma lista de nomes recomendados e funcionalidades para os parâmetros que são usadas para formatar ou para gerar dados.</span><span class="sxs-lookup"><span data-stu-id="d2759-103">The following table lists recommended names and functionality for parameters that are used to format or to generate data.</span></span>

|<span data-ttu-id="d2759-104">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="d2759-104">Parameter</span></span>|<span data-ttu-id="d2759-105">Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="d2759-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="d2759-106">**Como**</span><span class="sxs-lookup"><span data-stu-id="d2759-106">**As**</span></span><br><span data-ttu-id="d2759-107">Tipo de dados: Palavra-chave</span><span class="sxs-lookup"><span data-stu-id="d2759-107">Data type: Keyword</span></span>|<span data-ttu-id="d2759-108">Implemente este parâmetro para especificar o formato de saída do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d2759-108">Implement this parameter to specify the cmdlet output format.</span></span> <span data-ttu-id="d2759-109">Por exemplo, os valores possíveis podem ser texto ou de Script.</span><span class="sxs-lookup"><span data-stu-id="d2759-109">For example, possible values could be Text or Script.</span></span>|
|<span data-ttu-id="d2759-110">**binário**</span><span class="sxs-lookup"><span data-stu-id="d2759-110">**Binary**</span></span><br><span data-ttu-id="d2759-111">Tipo de dados: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="d2759-111">Data type: SwitchParameter</span></span>|<span data-ttu-id="d2759-112">Implemente este parâmetro para indicar que o cmdlet processa valores binários.</span><span class="sxs-lookup"><span data-stu-id="d2759-112">Implement this parameter to indicate that the cmdlet handles binary values.</span></span>|
|<span data-ttu-id="d2759-113">**Codificação**</span><span class="sxs-lookup"><span data-stu-id="d2759-113">**Encoding**</span></span><br><span data-ttu-id="d2759-114">Tipo de dados: Palavra-chave</span><span class="sxs-lookup"><span data-stu-id="d2759-114">Data type: Keyword</span></span>|<span data-ttu-id="d2759-115">Implemente este parâmetro para especificar o tipo de codificação que é suportado.</span><span class="sxs-lookup"><span data-stu-id="d2759-115">Implement this parameter to specify the type of encoding that is supported.</span></span> <span data-ttu-id="d2759-116">Por exemplo, os valores possíveis poderiam ser ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte e cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d2759-116">For example, possible values could be ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte, and String.</span></span>|
|<span data-ttu-id="d2759-117">**NewLine**</span><span class="sxs-lookup"><span data-stu-id="d2759-117">**NewLine**</span></span><br><span data-ttu-id="d2759-118">Tipo de dados: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="d2759-118">Data type: SwitchParameter</span></span>|<span data-ttu-id="d2759-119">Implemente este parâmetro para que os carateres de nova linha são suportados quando o parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="d2759-119">Implement this parameter so that the newline characters are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="d2759-120">**ShortName**</span><span class="sxs-lookup"><span data-stu-id="d2759-120">**ShortName**</span></span><br><span data-ttu-id="d2759-121">Tipo de dados: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="d2759-121">Data type: SwitchParameter</span></span>|<span data-ttu-id="d2759-122">Implemente este parâmetro, de modo a que os nomes abreviados são suportados quando o parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="d2759-122">Implement this parameter so that short names are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="d2759-123">**Width**</span><span class="sxs-lookup"><span data-stu-id="d2759-123">**Width**</span></span><br><span data-ttu-id="d2759-124">Tipo de dados: Int32</span><span class="sxs-lookup"><span data-stu-id="d2759-124">Data type: Int32</span></span>|<span data-ttu-id="d2759-125">Implemente este parâmetro para que o utilizador pode especificar a largura do dispositivo de saída.</span><span class="sxs-lookup"><span data-stu-id="d2759-125">Implement this parameter so that the user can specify the width of the output device.</span></span>|
|<span data-ttu-id="d2759-126">**Encapsular**</span><span class="sxs-lookup"><span data-stu-id="d2759-126">**Wrap**</span></span><br><span data-ttu-id="d2759-127">Tipo de dados: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="d2759-127">Data type: SwitchParameter</span></span>|<span data-ttu-id="d2759-128">Implemente este parâmetro para que a quebra automática é suportada quando o parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="d2759-128">Implement this parameter so that text wrapping is supported when the parameter is specified.</span></span>|
## <a name="see-also"></a><span data-ttu-id="d2759-129">Veja Também</span><span class="sxs-lookup"><span data-stu-id="d2759-129">See Also</span></span>

[<span data-ttu-id="d2759-130">Parâmetros do cmdlet</span><span class="sxs-lookup"><span data-stu-id="d2759-130">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="d2759-131">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d2759-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="d2759-132">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d2759-132">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
