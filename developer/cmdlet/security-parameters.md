---
title: Parâmetros de segurança | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e199bba3-90d3-41ca-9d78-cb502e58508d
caps.latest.revision: 6
ms.openlocfilehash: 9b4d83aeaf45eab1365dec5fbf48c3c796ed5bde
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057134"
---
# <a name="security-parameters"></a>Security Parameters (Parâmetros de Segurança)

A tabela seguinte lista os nomes recomendados e a funcionalidade para os parâmetros utilizados para fornecer informações de segurança de uma operação, como parâmetros que especifique informações do certificado de chave e privilégios.

|Parâmetro|Funcionalidade|
|---|---|
|**ACL**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para especificar o nível de controlo de acesso de proteção para um catálogo ou para um identificador URI (Uniform Resource).|
|**CertFile**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar o nome de um ficheiro que contém um dos seguintes:<br>-Um certificado de x.509 codificado em Base64 ou codificação regras der (DISTINGUISHED)<br>-Um ficheiro de público Key Cryptography Standards (PKCS) #12 que contém pelo menos um certificado e chave|
|**CertIssuerName**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar o nome do emissor de um certificado ou, de modo a que o utilizador pode especificar uma subcadeia.|
|**CertRequestFile**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para especificar o nome de um ficheiro que contém um pedido de certificado em Base64 ou PKCS #10 codificado em DER.|
|**CertSerialNumber**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para especificar o número de série que foi emitido pela autoridade de certificação.|
|**CertStoreLocation**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar a localização do arquivo de certificados. A localização é, normalmente, um caminho de ficheiro.|
|**CertSubjectName**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar o emissor de um certificado ou, de modo a que o utilizador pode especificar uma subcadeia.|
|**CertUsage**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para especificar a utilização da chave ou a utilização de chave avançada. A chave pode ser representada como um pouco mascarar, um pouco, um identificador de objeto (OID), ou uma cadeia de caracteres.|
|**Credencial**<br>Tipo de dados: [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential)|Implemente este parâmetro para que o cmdlet automaticamente pedirá ao utilizador para um nome de utilizador ou palavra-passe. Uma linha de comandos para ambos é apresentada se uma credencial completa não é fornecida diretamente.|
|**CSPName**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar o nome do fornecedor de serviços de certificado (CSP).|
|**CSPType**<br>Tipo de dados: Número inteiro|Implemente este parâmetro para que o utilizador pode especificar o tipo de CSP.|
|**Grupo**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar uma coleção de entidades de segurança para o acesso. Para obter mais informações, consulte a descrição dos **Principal** parâmetro.|
|**KeyAlgorithm**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar o algoritmo de geração de chaves a utilizar para a segurança.|
|**KeyContainerName**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar o nome do contentor de chaves.|
|**KeyLength**<br>Tipo de dados: Número inteiro|Implemente este parâmetro para que o utilizador pode especificar o comprimento da chave em bits.|
|**Operação**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar uma ação que pode ser executada num objeto protegido.|
|**Principal**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar uma entidade de identificação exclusiva para o acesso.|
|**Privilégio**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar o direito de que um cmdlet tem de realizar uma operação de uma entidade específica.|
|**Privilégios**<br>Tipo de dados: Matriz de privilégios|Implemente este parâmetro para que o utilizador pode especificar os direitos de que precisa de um cmdlet para efetuar a operação para uma entrada específica.|
|**Função**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar um conjunto de operações que podem ser executadas por uma entidade.|
|**SaveCred**<br>Tipo de dados: SwitchParameter|Implemente este parâmetro para que as credenciais guardadas anteriormente pelo utilizador serão utilizadas quando o parâmetro for especificado.|
|**Âmbito**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar o grupo de objetos protegidos para o cmdlet.|
|**SID**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar um identificador exclusivo que representa uma entidade de segurança.|
|**Fidedigno**<br>Tipo de dados: SwitchParameter|Implemente este parâmetro, de modo a que níveis de confiança são suportadas quando o parâmetro for especificado.|
|**TrustLevel**<br>Tipo de dados: Palavra-chave|Implemente este parâmetro para que o utilizador pode especificar o nível de confiança que é suportado. Por exemplo, os valores possíveis incluem fulltrust, intranet e internet.|

## <a name="see-also"></a>Veja Também

[Parâmetros do cmdlet](./cmdlet-parameters.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
