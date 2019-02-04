---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: a1e90a0b96f74decb55343292b97befaf1a85f8a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685754"
---
# <a name="class-based-dsc-resources"></a>Recursos de DSC baseados em classes

## <a name="defining-dsc-resources-with-classes"></a>Definir os recursos de DSC com classes

Com base nos comentários, fizemos-se a criação de recursos de DSC baseados na classe mais simples e mais fácil de entender.
As principais diferenças entre um recurso de DSC baseados na classe e um fornecedor de recursos de DSC de cmdlet são:

* Não é necessário um ficheiro MOF para o esquema.
* R **DSCResource** subpasta da pasta do módulo não é necessária.
* Um arquivo de módulo do PowerShell pode conter várias classes de recursos de DSC.

Para obter mais informações, consulte [escrever um recurso personalizado do DSC com classes do PowerShell](https://msdn.microsoft.com/powershell/dsc/authoringresource).
