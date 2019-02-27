---
title: Como importar os Cmdlets que utilizam módulos | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: c007bb11324e10ffd100797dccd9e6ab0d09a73e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849015"
---
# <a name="how-to-import-cmdlets-using-modules"></a>How to Import Cmdlets Using Modules (Como Importar Cmdlets Através de Módulos)

Este tópico descreve como importar os cmdlets para uma sessão do Windows PowerShell através de um módulo de binário.

> [!NOTE]
> Os membros dos módulos podem incluir cmdlets, provedores, funções, variáveis, aliases e muito mais. Snap-ins pode conter apenas os cmdlets e provedores.

## <a name="how-to-load-cmdlets-using-a-module"></a>Como carregar cmdlets a utilizar um módulo

1. Crie uma pasta de módulo que tem o mesmo nome que o ficheiro de assemblagem em que os cmdlets são implementados. Neste procedimento, a pasta de módulo é criada no `system32` pasta.

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

2. Certifique-se de que o `PSModulePath` variável de ambiente inclui o caminho para a nova pasta de módulo. Por predefinição, a pasta de sistema já foi adicionada ao `PSModulePath` variável de ambiente.

3. Copie o assembly de cmdlet para a pasta de módulo.

4. Execute o seguinte comando para adicionar os cmdlets para a sessão:

   `import-module [Module_Name]`

   Este procedimento pode ser utilizado para testar seus cmdlets. Ele adiciona todos os cmdlets no assembly para a sessão. Para obter mais informações sobre os módulos, os diferentes tipos de módulos, as diferentes formas de carregar módulos e como restringir os elementos de um módulo que são exportados, consulte [escrever um módulo do Windows PowerShell](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Consulte Também

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Instalar módulos](../module/installing-a-powershell-module.md)