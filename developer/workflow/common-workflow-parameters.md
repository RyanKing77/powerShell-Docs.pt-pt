---
title: Parâmetros comuns do fluxo de trabalho | Documentos da Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5891467-8e13-484d-b7af-32e6bffab35d
caps.latest.revision: 4
ms.openlocfilehash: 2aca4483e500432ef9f52804e85678d2268aa4cd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846908"
---
# <a name="common-workflow-parameters"></a>Common Workflow Parameters (Parâmetros de Fluxo de Trabalho Comuns)

Uma atividade de fluxo de trabalho gerada a partir de um cmdlet do Windows PowerShell define vários parâmetros comuns a todas as atividades. Pode ser especificado um subconjunto desses parâmetros no momento da criação, para que os autores de fluxo de trabalho podem personalizar a atividades. Outro subconjunto desses parâmetros pode ser especificado pelo utilizador ao chamar a atividade.

Os parâmetros comuns de fluxo de trabalho são agrupados em várias categorias, da seguinte forma.

## <a name="connectivity-parameters"></a>Parâmetros de conectividade

|Nome|Tipo|Descrição|Pode ser especificado pelo utilizador final no tempo de execução?|Pode ser especificado pelo autor do fluxo de trabalho no momento da criação?|Pode ser especificado pelo autor do fluxo de trabalho na Instanciação?|
|----------|----------|-----------------|-----------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------|
|PSComputerName|String[]|Uma lista de nomes de computador para o qual pretende iniciar trabalhos.|Sim|Sim|Sim|
|PSCredential|[System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)|A credencial de autenticação a utilizar para início de sessão para os computadores especificados pelo parâmetro PSComputerName. Este parâmetro é válido apenas se PSComputerName for especificado.|Sim|Sim|Sim|
|PSPort|UInt32|A porta a ser utilizada para executar o fluxo de trabalho.|Sim|Sim|Sim|
|PSUseSSL|Booleano|Utilize o protocolo Secure Sockets Layer (SSL) para estabelecer uma ligação segura para o computador remoto a executar o fluxo de trabalho.|Sim|Sim|Sim|
|PSConfigurationName|Cadeia (de carateres)|A configuração de sessão utilizada para executar o fluxo de trabalho.|Sim|Sim|Sim|
|PSApplicationName|Cadeia (de carateres)|A parte do nome de aplicação da ligação de URI para a execução de fluxo de trabalho. Utilize este parâmetro, apenas quando não estiver a utilizar o parâmetro ConnectionURI.|Sim|Sim|Sim|
|PSThrottleLimit|UInt32|O número máximo de ligações simultâneas que podem ser estabelecidas para executar o fluxo de trabalho.|Sim|TBD|Sim|
|PSConnectionURI|String[]|Uma matriz de URIs completamente qualificado que especifique os pontos de extremidade para as sessões interativas utilizadas para executar o fluxo de trabalho.|Sim|Sim|Sim|
|PSAllowRedirection|Booleano|Especifica se pretende permitir o redireccionamento desta ligação para um URI alternativo a executar o fluxo de trabalho.|Sim|Sim|Sim|
|PSSessionOption|[System.Management.Automation.Remoting.Pssessionoption](/dotnet/api/System.Management.Automation.Remoting.PSSessionOption)|Opções avançadas para a sessão utilizada para executar o fluxo de trabalho.|Sim|Sim|Sim|
|PSAuthentication|[System.Management.Automation.Runspaces.Authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism)|Um valor do [System.Management.Automation.Runspaces.Authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism) enumeração que especifica o mecanismo de autenticação utilizado para autenticar as credenciais do utilizador.|Sim|Sim|Sim|
|PSCertificateThumbprint|Cadeia (de carateres)|O digital certificado de chave pública (X509) de uma conta de utilizador que tenha permissão para executar o fluxo de trabalho.|Sim|Sim|Sim|

### <a name="behavior-parameters"></a>Parâmetros de comportamento