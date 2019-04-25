---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: db4543b788ad0a5c7aa32706246446533b901d09
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085818"
---
# <a name="deliver-a-configuration-document-without-applying"></a>Fornecer um documento de configuração sem aplicar

O [Publish-dscconfiguration para](https://technet.microsoft.com/library/mt517875.aspx) cmdlet copia um ficheiro MOF de configuração para um nó de destino, mas não se aplica a configuração.
Esta configuração é aplicada durante o próximo passo de consistência, ou ao executar o [Update-dscconfiguration para](https://technet.microsoft.com/library/mt143541.aspx) cmdlet.
