---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: f929ce4684bb53c3039238ecd465f1c0e432f741
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225679"
---
# <a name="deliver-a-configuration-document-without-applying"></a>Fornecer um documento de configuração sem aplicar

O [publicar DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) cmdlet copia um ficheiro MOF de configuração para um nó de destino, mas não se aplica a configuração.
Esta configuração é aplicada durante a próxima passagem de consistência ou ao executar o [atualização DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) cmdlet.
