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
ms.openlocfilehash: bdf88de0258af75c01739f30a71fb4914cac3a9a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849029"
---
# <a name="security-parameters"></a>Security Parameters (Parâmetros de Segurança)

A tabela seguinte lista os nomes recomendados e a funcionalidade para os parâmetros utilizados para fornecer informações de segurança de uma operação, como parâmetros que especifique informações do certificado de chave e privilégios.

Tipo de dados de ACL: Cadeia (de carateres)

Implemente este parâmetro para especificar o nível de controlo de acesso de proteção para um catálogo ou para um identificador URI (Uniform Resource).

Tipo de dados de CertFile: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar o nome de um ficheiro que contém um dos seguintes:

- Um certificado de x.509 codificado em Base64 ou codificação regras der (DISTINGUISHED)

- Um ficheiro de público Key Cryptography Standards (PKCS) #12 que contém pelo menos um certificado e chave

Tipo de dados de CertIssuerName: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar o nome do emissor de um certificado ou, de modo a que o utilizador pode especificar uma subcadeia.

Tipo de dados de CertRequestFile: Cadeia (de carateres)

Implemente este parâmetro para especificar o nome de um ficheiro que contém um pedido de certificado em Base64 ou PKCS #10 codificado em DER.

Tipo de dados de CertSerialNumber: Cadeia (de carateres)

Implemente este parâmetro para especificar o número de série que foi emitido pela autoridade de certificação.

Tipo de dados de CertStoreLocation: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar a localização do arquivo de certificados. A localização é, normalmente, um caminho de ficheiro.

Tipo de dados de CertSubjectName: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar o emissor de um certificado ou, de modo a que o utilizador pode especificar uma subcadeia.

Tipo de dados de CertUsage: Cadeia (de carateres)

Implemente este parâmetro para especificar a utilização da chave ou a utilização de chave avançada. A chave pode ser representada como um pouco mascarar, um pouco, um identificador de objeto (OID), ou uma cadeia de caracteres.

Tipo de dados de credencial: [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)

Implemente este parâmetro para que o cmdlet automaticamente pedirá ao utilizador para um nome de utilizador ou palavra-passe. Uma linha de comandos para ambos é apresentada se uma credencial completa não é fornecida diretamente.

Tipo de dados de CSPName: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar o nome do fornecedor de serviços de certificado (CSP).

Tipo de dados de CSPType: Número inteiro

Implemente este parâmetro para que o utilizador pode especificar o tipo de CSP.

Tipo de dados do grupo: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar uma coleção de entidades de segurança para o acesso. Para obter mais informações, consulte a descrição do `Principal` parâmetro.

Tipo de dados de KeyAlgorithm: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar o algoritmo de geração de chaves a utilizar para a segurança.

Tipo de dados de KeyContainerName: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar o nome do contentor de chaves.

Tipo de dados de KeyLength: Número inteiro

Implemente este parâmetro para que o utilizador pode especificar o comprimento da chave em bits.

Tipo de dados de operação: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar uma ação que pode ser executada num objeto protegido.

Tipo de dados principal: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar uma entidade de identificação exclusiva para o acesso.

Tipo de dados de privilégio: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar o direito de que um cmdlet tem de realizar uma operação de uma entidade específica.

Tipo de dados de privilégios: Matriz de privilégios

Implemente este parâmetro para que o utilizador pode especificar os direitos de que precisa de um cmdlet para efetuar a operação para uma entrada específica.

Tipo de dados de função: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar um conjunto de operações que podem ser executadas por uma entidade.

Tipo de dados de SaveCred: SwitchParameter

Implemente este parâmetro para que as credenciais guardadas anteriormente pelo utilizador serão utilizadas quando o parâmetro for especificado.

Tipo de dados de âmbito: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar o grupo de objetos protegidos para o cmdlet.

Tipo de dados do SID: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar um identificador exclusivo que representa uma entidade de segurança.

Tipo de dados de confiável: SwitchParameter

Implemente este parâmetro, de modo a que níveis de confiança são suportadas quando o parâmetro for especificado.

Tipo de dados de TrustLevel: Palavra-chave

Implemente este parâmetro para que o utilizador pode especificar o nível de confiança que é suportado. Por exemplo, os valores possíveis incluem fulltrust, intranet e internet.

## <a name="see-also"></a>Consulte Também

[Parâmetros do cmdlet](./cmdlet-parameters.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
