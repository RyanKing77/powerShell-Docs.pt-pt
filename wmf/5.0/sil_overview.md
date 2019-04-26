---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 7e87ed4bc9a86be52d4d06d3e87386a1111227c5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085019"
---
# <a name="software-inventory-logging-sil"></a>Registo de Inventário de Software (SIL)

**IMPORTANTE:** *Ao instalar o WMF 5.0 num servidor Windows Server 2012 R2 que já está a executar o SIL, é necessário executar o cmdlet Start-SilLogging uma vez depois de instalar o WMF, como o processo de instalação incorretamente irá parar a funcionalidade registo de inventário de Software.*

Registo de inventário de software ajuda a reduzir os custos operacionais de obter informações precisas sobre o software da Microsoft instalado localmente num servidor, mas sobretudo em vários servidores num ambiente de TI (partindo do princípio de que o software é instalado e em execução no ambiente de TI). Desde que uma configuração, pode reencaminhar estes dados para um servidor de agregação e recolher os dados de registo num único local, utilizando um processo automático e uniforme.

Embora também pode iniciar os dados de inventário de software através de consultas diretas cada computador, registo de inventário de Software, ao empregar uma arquitetura de reencaminhamento (através da rede) iniciada por cada servidor, consegue superar os desafios de deteção de servidor característicos para muitos software de inventário e asset cenários de gestão. Registo de inventário de software utiliza o SSL para proteger os dados que são reencaminhados através de HTTPS para um servidor de agregação. Armazenamento de dados num único local torna os dados mais fácil de analisar, manipular e partilhar quando necessário.

Nenhuma destes dados é enviada à Microsoft como parte da funcionalidade de funcionalidade. A funcionalidade e os dados do Registo de Inventário de Software destinam-se apenas a serem utilizados pelos administradores e pelo proprietário licenciado do software de servidor.

Para obter mais informações e documentação sobre os cmdlets de registo de inventário de Software, consulte recursos online do Windows Server 2012 R2 em <http://technet.microsoft.com/library/dn383584.aspx>.
