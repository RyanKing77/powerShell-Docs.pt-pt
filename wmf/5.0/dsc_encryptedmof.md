---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: d19f3c47af858eb18a39847050f80ffa013c59bb
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="mof-documents-are-encrypted-by-default"></a>MOF documentos são encriptados por predefinição

Documentos de configuração contêm informações confidenciais. Nas versões anteriores do DSC era necessário para distribuir e gerir certificados para proteger as credenciais dentro de uma configuração. Para muitos, isto era uma carga de gestão significativos e mesmo com todo o trabalho demorou a fazê-lo que foram deixou ainda com algumas informações de configuração que não estava e não podem ser protegidas. 

Que já não for o caso, porque **toda a configuração MOFs são protegidas por predefinição**. Não existem certificados ou as definições de configuração de metadados necessários. Sempre que uma configuração MOF é guardado no disco pelo Local Configuration Manager (MMC) num nó de destino, é encriptado. Os MOFs estão encriptadas com [DPAPI](https://msdn.microsoft.com/en-us/library/ms995355.aspx). **Nota:** MOFs gerados por um script de configuração não estão encriptados.

**Exemplo:** encriptação no modo de push ![encriptação MOF](../images/MOF_Encryption.jpg)

Se já estiver a utilizar o método de certificado para encriptar as palavras-passe ou se precisar de segurança adicional para as palavras-passe, o [existente método de encriptação baseada em certificado](https://msdn.microsoft.com/en-us/powershell/dsc/securemof) continuarão a funcionar. O resultado será um documento MOF totalmente é encriptado utilizando os DPAPIs e além disso, ter palavras-passe encriptado dentro da mesma.

Esta encriptação só se aplica a documentos MOF de configuração (pending.mof, current.mof, previous.mof e MOFs parciais). Configuração meta MOFs ainda são guardados em texto simples, uma vez que menos provável que contêm segredos.
