---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: e7198999c17b5c0d77724a82b322e6485065225e
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/07/2018
ms.locfileid: "34482850"
---
# <a name="software-inventory-logging-sil"></a>Registo de Inventário de Software (SIL)

**Importante:** *ao instalar o WMF 5.0 num Windows Server 2012 R2 servidor que já está a executar o SIL, é necessário executar o cmdlet Start-SilLogging uma vez após a instalação do WMF, como o processo de instalação erradamente irá parar a Funcionalidade de registo de inventário de software.*

O registo de inventário de software ajuda a reduzir os custos operacionais resultantes da obtenção de informações exatas relacionadas sobre o software da Microsoft instalado localmente num servidor, mas sobretudo em vários servidores num ambiente de TI (pressupondo que o software é instalado e em execução no ambiente de TI). Fornecido um estiver configurado, pode reencaminhar estes dados para um servidor de agregação e recolher os dados de registo num local através da utilização de um processo automático e uniforme.

Apesar de também pode iniciar sessão dados de inventário de software através de consultas diretas cada computador, registo de inventário de Software, ao empregar uma arquitetura de reencaminhamento (através da rede) iniciada por cada servidor, consegue superar os desafios de deteção de servidor que são normais de muitas software de inventário e asset cenários de gestão. O registo de inventário de software utiliza SSL para proteger os dados reencaminhados por HTTPS para um servidor de agregação. Armazenar os dados num único local facilita os dados para análise, a manipulação e a partilha quando for necessário.

Nenhuma destes dados é enviada à Microsoft como parte da funcionalidade de funcionalidade. A funcionalidade e os dados do Registo de Inventário de Software destinam-se apenas a serem utilizados pelos administradores e pelo proprietário licenciado do software de servidor.

Para obter mais informações e documentação sobre cmdlets de registo de inventário de Software, consulte recursos online do Windows Server 2012 R2 em <http://technet.microsoft.com/library/dn383584.aspx>.
