---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 4db2237678649c23729bd1f41bf88f1b9f8f0eef
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="software-inventory-logging-sil"></a>Registo de Inventário de Software (SIL)

* * Importante: * * *ao instalar o WMF 5.0 num Windows Server 2012 R2 servidor que já está a executar o SIL, é necessário para executar o cmdlet Start-SilLogging uma vez após a instalação do WMF, uma vez que o processo de instalação erradamente irá parar o Software Funcionalidade de registo de inventário.*

O registo de inventário de software ajuda a reduzir os custos operacionais resultantes da obtenção de informações exatas relacionadas sobre o software da Microsoft instalado localmente num servidor, mas sobretudo em vários servidores num ambiente de TI (pressupondo que o software é instalado e em execução no ambiente de TI). Fornecido um estiver configurado, pode reencaminhar estes dados para um servidor de agregação e recolher os dados de registo num local através da utilização de um processo automático e uniforme.

Apesar de também pode iniciar sessão dados de inventário de software através de consultas diretas cada computador, registo de inventário de Software, ao empregar uma arquitetura de reencaminhamento (através da rede) iniciada por cada servidor, consegue superar os desafios de deteção de servidor que são normais de muitas software de inventário e asset cenários de gestão. O registo de inventário de software utiliza SSL para proteger os dados reencaminhados por HTTPS para um servidor de agregação. Armazenar os dados num único local facilita os dados para análise, a manipulação e a partilha quando for necessário.

Nenhuma destes dados é enviada à Microsoft como parte da funcionalidade de funcionalidade. A funcionalidade e os dados do Registo de Inventário de Software destinam-se apenas a serem utilizados pelos administradores e pelo proprietário licenciado do software de servidor.

Para obter mais informações e documentação sobre cmdlets de registo de inventário de Software, consulte recursos online do Windows Server 2012 R2 em <http://technet.microsoft.com/library/dn383584.aspx>.