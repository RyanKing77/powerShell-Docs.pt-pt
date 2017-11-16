---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: d40e5475c4132d6377c9a4559262a41b4842180a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="class-based-dsc-resources"></a>Recursos de DSC com base na classe

## <a name="defining-dsc-resources-with-classes"></a>Definir os recursos de DSC com classes

Com base nos comentários, que fizemos criação de recursos de DSC com base na classe mais simples e mais fácil de compreender. As principais diferenças entre um recurso de DSC com base na classe e um fornecedor de recursos de DSC de cmdlet são:

* Não é necessário um ficheiro MOF para o esquema.
* A **DSCResource** subpasta da pasta do módulo não é necessária.
* Um ficheiro de módulo do PowerShell pode conter várias classes de recursos de DSC.

Para obter mais informações, consulte [escrever um recurso personalizado de DSC com classes de PowerShell](https://msdn.microsoft.com/powershell/dsc/authoringresource).

