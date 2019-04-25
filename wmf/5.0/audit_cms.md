---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: b8940ded189d822a5a2cd40773ef5146353611cc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62059003"
---
# <a name="cryptographic-message-syntax-cms-cmdlets"></a>Cmdlets de sintaxe de mensagem (CMS) criptográfico

Os cmdlets de sintaxe de mensagem criptográfica suportam a encriptação e desencriptação de conteúdo utilizando o formato de padrão IETF para proteger criptograficamente mensagens conforme documentado [RFC5652](https://tools.ietf.org/html/rfc5652).

```powershell
Get-CmsMessage [-Content] <string>
Get-CmsMessage [-Path] <string>
Get-CmsMessage [-LiteralPath] <string>
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Content] <string> [[-OutFile] <string>]
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Path] <string> [[-OutFile] <string>]
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-LiteralPath] <string> [[-OutFile] <string>]
Unprotect-CmsMessage [-EventLogRecord] <EventLogRecord> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-Content] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-Path] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-LiteralPath] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
```

A encriptação de CMS padrão implementa a criptografia de chave pública, onde as chaves utilizadas para encriptar o conteúdo (a *chave pública*) e as chaves utilizadas para desencriptar o conteúdo (a *chave privada*) estão separados.

A chave pública pode ser partilhada amplamente e não dados confidenciais. Se qualquer conteúdo é encriptado com esta chave pública, apenas a chave privada pode descriptografá-la. Para obter mais informações, consulte [criptografia de chave pública](https://en.wikipedia.org/wiki/Public-key_cryptography).

A ser reconhecida no PowerShell, os certificados de encriptação exigem um identificador exclusivo de utilização de chave (EKU) para identificá-los como certificados de encriptação de dados (como os identificadores para "assinatura de código', 'Mail encriptados').

Eis um exemplo de criação de um certificado que é bom para a encriptação de documentos:

```powershell
(Change the text in **Subject** to your name, email, or other identifier), and put in a file (i.e.: DocumentEncryption.inf):
[Version]
Signature = "$Windows NT$"
[Strings]
szOID\_ENHANCED\_KEY\_USAGE = "2.5.29.37"
szOID\_DOCUMENT\_ENCRYPTION = "1.3.6.1.4.1.311.80.1"
[NewRequest]
Subject = "<cn=me@somewhere.com>"
MachineKeySet = false
KeyLength = 2048
KeySpec = AT\_KEYEXCHANGE
HashAlgorithm = Sha1
Exportable = true
RequestType = Cert
KeyUsage = "CERT\_KEY\_ENCIPHERMENT\_KEY\_USAGE | CERT\_DATA\_ENCIPHERMENT\_KEY\_USAGE"
ValidityPeriod = "Years"
ValidityPeriodUnits = "1000"
[Extensions]
%szOID\_ENHANCED\_KEY\_USAGE% = "{text}%szOID\_DOCUMENT\_ENCRYPTION%"
```

Em seguida, execute:
```powershell
certreq -new DocumentEncryption.inf DocumentEncryption.cer
```

E agora pode encriptar e desencriptar o conteúdo:

```powershell
$protected = "Hello World" | Protect-CmsMessage -To "\*me@somewhere.com\*[](mailto:*leeholm@microsoft.com*)"
$protected
-----BEGIN CMS-----
MIIBqAYJKoZIhvcNAQcDoIIBmTCCAZUCAQAxggFQMIIBTAIBADA0MCAxHjAcBgNVBAMMFWxlZWhv
bG1AbWljcm9zb2Z0LmNvbQIQQYHsbcXnjIJCtH+OhGmc1DANBgkqhkiG9w0BAQcwAASCAQAnkFHM
proJnFy4geFGfyNmxH3yeoPvwEYzdnsoVqqDPAd8D3wao77z7OhJEXwz9GeFLnxD6djKV/tF4PxR
E27aduKSLbnxfpf/sepZ4fUkuGibnwWFrxGE3B1G26MCenHWjYQiqv+Nq32Gc97qEAERrhLv6S4R
G+2dJEnesW8A+z9QPo+DwYU5FzD0Td0ExrkswVckpLNR6j17Yaags3ltNVmbdEXekhi6Psf2MLMP
TSO79lv2L0KeXFGuPOrdzPAwCkV0vNEqTEBeDnZGrjv/5766bM3GW34FXApod9u+VSFpBnqVOCBA
DVDraA6k+xwBt66cV84OHLkh0kT02SIHMDwGCSqGSIb3DQEHATAdBglghkgBZQMEASoEEJbJaiRl
KMnBoD1dkb/FzSWAEBaL8xkFwCu0e1ZtDj7nSJc=
-----END CMS-----

$protected | Unprotect-CmsMessage
Hello World
```

Qualquer parâmetro do tipo **CMSMessageRecipient** suporta identificadores nos seguintes formatos:
- Um certificado real (como obtidos a partir do fornecedor de certificado)
- Caminho para a um ficheiro que contém o certificado
- Caminho para um diretório que contém o certificado
- Thumbprint do certificado (usado para examinar o arquivo de certificados)
- Nome do requerente do certificado (usado para examinar o arquivo de certificados)

Para ver os certificados de encriptação de documentos no fornecedor de certificado, pode utilizar o **- DocumentEncryptionCert** parâmetro dinâmico:

```powershell
dir -DocumentEncryptionCert
```
