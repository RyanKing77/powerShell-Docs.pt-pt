---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 4def20aa95f66ab23c9eee575150bc3db02541d8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="class-based-dsc-resources"></a>Recursos de DSC baseados em classes

## <a name="defining-dsc-resources-with-classes"></a>Definir os recursos de DSC com classes

Com base nos comentários, que fizemos criação de recursos de DSC com base na classe mais simples e mais fácil de compreender.
As principais diferenças entre um recurso de DSC com base na classe e um fornecedor de recursos de DSC de cmdlet são:

* Não é necessário um ficheiro MOF para o esquema.
* A **DSCResource** subpasta da pasta do módulo não é necessária.
* Um ficheiro de módulo do PowerShell pode conter várias classes de recursos de DSC.

Para obter mais informações, consulte [escrever um recurso personalizado de DSC com classes de PowerShell](https://msdn.microsoft.com/powershell/dsc/authoringresource).