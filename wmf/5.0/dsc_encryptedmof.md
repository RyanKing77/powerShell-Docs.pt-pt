---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9af931a1a2b545ba36826246c4155f42052a16bf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085711"
---
# <a name="mof-documents-are-encrypted-by-default"></a>Documentos MOF são criptografados por padrão

Documentos de configuração contêm informações confidenciais. Nas versões anteriores do DSC era necessário para distribuir e gerir certificados para proteger as credenciais dentro de uma configuração. Para muitos, isso foi um fardo da gestão significativas e mesmo com todo o trabalho necessário para fazê-lo que ainda ficaram com algumas informações de configuração que não era e não pudessem ser protegidas.

Que já não é o caso, pois **todas as configurações são protegidas por predefinição MOFs**. Não existem certificados ou as definições de configuração de meta são necessários. Sempre que uma configuração de MOF é guardado no disco, o Local Configuration Manager (LCM) num nó de destino, são encriptado. Os MOFs são encriptados com [DPAPI](https://msdn.microsoft.com/library/ms995355.aspx). **Nota:** MOFs gerados por um script de configuração não estão encriptados.

**Example:** Criptografia no modo push ![encriptação da MOF](../images/MOF_Encryption.jpg)

Se já estiver a utilizar o método de certificado para encriptar as palavras-passe ou se precisar de segurança adicional para as palavras-passe, o [método existente de encriptação baseada em certificado](https://msdn.microsoft.com/powershell/dsc/securemof) continuarão a funcionar. O resultado será um documento MOF que está totalmente encriptado utilizando os DPAPIs e além disso, ter palavras-passe encriptada dentro da mesma.

Esta encriptação só se aplica a documentos do MOF de configuração (pending.mof, current.mof, previous.mof e MOFs parciais). MOFs de meta-configuração ainda são guardadas em texto simples, já que menos provável que contêm segredos.
