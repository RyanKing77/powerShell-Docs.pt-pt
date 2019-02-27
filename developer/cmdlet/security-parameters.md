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
# <a name="security-parameters"></a><span data-ttu-id="345a4-102">Security Parameters (Parâmetros de Segurança)</span><span class="sxs-lookup"><span data-stu-id="345a4-102">Security Parameters</span></span>

<span data-ttu-id="345a4-103">A tabela seguinte lista os nomes recomendados e a funcionalidade para os parâmetros utilizados para fornecer informações de segurança de uma operação, como parâmetros que especifique informações do certificado de chave e privilégios.</span><span class="sxs-lookup"><span data-stu-id="345a4-103">The following table lists the recommended names and functionality for parameters used to provide security information for an operation, such as parameters that specify certificate key and privilege information.</span></span>

<span data-ttu-id="345a4-104">Tipo de dados de ACL: Cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="345a4-104">ACL Data type: String</span></span>

<span data-ttu-id="345a4-105">Implemente este parâmetro para especificar o nível de controlo de acesso de proteção para um catálogo ou para um identificador URI (Uniform Resource).</span><span class="sxs-lookup"><span data-stu-id="345a4-105">Implement this parameter to specify the access control level of protection for a catalog or for a Uniform Resource Identifier (URI).</span></span>

<span data-ttu-id="345a4-106">Tipo de dados de CertFile: Cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="345a4-106">CertFile Data type: String</span></span>

<span data-ttu-id="345a4-107">Implemente este parâmetro para que o utilizador pode especificar o nome de um ficheiro que contém um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="345a4-107">Implement this parameter so that the user can specify the name of a file that contains one of the following:</span></span>

- <span data-ttu-id="345a4-108">Um certificado de x.509 codificado em Base64 ou codificação regras der (DISTINGUISHED)</span><span class="sxs-lookup"><span data-stu-id="345a4-108">A Base64 or Distinguished Encoding Rules (DER) encoded x.509 certificate</span></span>

- <span data-ttu-id="345a4-109">Um ficheiro de público Key Cryptography Standards (PKCS) #12 que contém pelo menos um certificado e chave</span><span class="sxs-lookup"><span data-stu-id="345a4-109">A Public Key Cryptography Standards (PKCS) #12 file that contains at least one certificate and key</span></span>

<span data-ttu-id="345a4-110">Tipo de dados de CertIssuerName: Cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="345a4-110">CertIssuerName Data type: String</span></span>

<span data-ttu-id="345a4-111">Implemente este parâmetro para que o utilizador pode especificar o nome do emissor de um certificado ou, de modo a que o utilizador pode especificar uma subcadeia.</span><span class="sxs-lookup"><span data-stu-id="345a4-111">Implement this parameter so that the user can specify the name of the issuer of a certificate or so that the user can specify a substring.</span></span>

<span data-ttu-id="345a4-112">Tipo de dados de CertRequestFile: Cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="345a4-112">CertRequestFile Data type: String</span></span>

<span data-ttu-id="345a4-113">Implemente este parâmetro para especificar o nome de um ficheiro que contém um pedido de certificado em Base64 ou PKCS #10 codificado em DER.</span><span class="sxs-lookup"><span data-stu-id="345a4-113">Implement this parameter to specify the name of a file that contains a Base64 or DER-encoded PKCS #10 certificate request.</span></span>

<span data-ttu-id="345a4-114">Tipo de dados de CertSerialNumber: Cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="345a4-114">CertSerialNumber Data type: String</span></span>

<span data-ttu-id="345a4-115">Implemente este parâmetro para especificar o número de série que foi emitido pela autoridade de certificação.</span><span class="sxs-lookup"><span data-stu-id="345a4-115">Implement this parameter to specify the serial number that was issued by the certification authority.</span></span>

<span data-ttu-id="345a4-116">Tipo de dados de CertStoreLocation: Cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="345a4-116">CertStoreLocation Data type: String</span></span>

<span data-ttu-id="345a4-117">Implemente este parâmetro para que o utilizador pode especificar a localização do arquivo de certificados.</span><span class="sxs-lookup"><span data-stu-id="345a4-117">Implement this parameter so that the user can specify the location of the certificate store.</span></span> <span data-ttu-id="345a4-118">A localização é, normalmente, um caminho de ficheiro.</span><span class="sxs-lookup"><span data-stu-id="345a4-118">The location is typically a file path.</span></span>

<span data-ttu-id="345a4-119">Tipo de dados de CertSubjectName: Cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="345a4-119">CertSubjectName Data type: String</span></span>

<span data-ttu-id="345a4-120">Implemente este parâmetro para que o utilizador pode especificar o emissor de um certificado ou, de modo a que o utilizador pode especificar uma subcadeia.</span><span class="sxs-lookup"><span data-stu-id="345a4-120">Implement this parameter so that the user can specify the issuer of a certificate or so that the user can specify a substring.</span></span>

<span data-ttu-id="345a4-121">Tipo de dados de CertUsage: Cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="345a4-121">CertUsage Data type: String</span></span>

<span data-ttu-id="345a4-122">Implemente este parâmetro para especificar a utilização da chave ou a utilização de chave avançada.</span><span class="sxs-lookup"><span data-stu-id="345a4-122">Implement this parameter to specify the key usage or the enhanced key usage.</span></span> <span data-ttu-id="345a4-123">A chave pode ser representada como um pouco mascarar, um pouco, um identificador de objeto (OID), ou uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="345a4-123">The key can be represented as a bit mask, a bit, an object identifier (OID), or a string.</span></span>

<span data-ttu-id="345a4-124">Tipo de dados de credencial: [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)</span><span class="sxs-lookup"><span data-stu-id="345a4-124">Credential Data type: [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)</span></span>

<span data-ttu-id="345a4-125">Implemente este parâmetro para que o cmdlet automaticamente pedirá ao utilizador para um nome de utilizador ou palavra-passe.</span><span class="sxs-lookup"><span data-stu-id="345a4-125">Implement this parameter so that the cmdlet will automatically prompt the user for a user name or password.</span></span> <span data-ttu-id="345a4-126">Uma linha de comandos para ambos é apresentada se uma credencial completa não é fornecida diretamente.</span><span class="sxs-lookup"><span data-stu-id="345a4-126">A prompt for both is displayed if a full credential is not supplied directly.</span></span>

<span data-ttu-id="345a4-127">Tipo de dados de CSPName: Cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="345a4-127">CSPName Data type: String</span></span>

<span data-ttu-id="345a4-128">Implemente este parâmetro para que o utilizador pode especificar o nome do fornecedor de serviços de certificado (CSP).</span><span class="sxs-lookup"><span data-stu-id="345a4-128">Implement this parameter so that the user can specify the name of the certificate service provider (CSP).</span></span>

<span data-ttu-id="345a4-129">Tipo de dados de CSPType: Número inteiro</span><span class="sxs-lookup"><span data-stu-id="345a4-129">CSPType Data type: Integer</span></span>

<span data-ttu-id="345a4-130">Implemente este parâmetro para que o utilizador pode especificar o tipo de CSP.</span><span class="sxs-lookup"><span data-stu-id="345a4-130">Implement this parameter so that the user can specify the type of CSP.</span></span>

<span data-ttu-id="345a4-131">Tipo de dados do grupo: Cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="345a4-131">Group Data type: String</span></span>

<span data-ttu-id="345a4-132">Implemente este parâmetro para que o utilizador pode especificar uma coleção de entidades de segurança para o acesso.</span><span class="sxs-lookup"><span data-stu-id="345a4-132">Implement this parameter so that the user can specify a collection of principals for access.</span></span> <span data-ttu-id="345a4-133">Para obter mais informações, consulte a descrição do `Principal` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="345a4-133">For more information, see the description of the `Principal` parameter.</span></span>

<span data-ttu-id="345a4-134">Tipo de dados de KeyAlgorithm: Cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="345a4-134">KeyAlgorithm Data type: String</span></span>

<span data-ttu-id="345a4-135">Implemente este parâmetro para que o utilizador pode especificar o algoritmo de geração de chaves a utilizar para a segurança.</span><span class="sxs-lookup"><span data-stu-id="345a4-135">Implement this parameter so that the user can specify the key generation algorithm to use for security.</span></span>

<span data-ttu-id="345a4-136">Tipo de dados de KeyContainerName: Cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="345a4-136">KeyContainerName Data type: String</span></span>

<span data-ttu-id="345a4-137">Implemente este parâmetro para que o utilizador pode especificar o nome do contentor de chaves.</span><span class="sxs-lookup"><span data-stu-id="345a4-137">Implement this parameter so that the user can specify the name of the key container.</span></span>

<span data-ttu-id="345a4-138">Tipo de dados de KeyLength: Número inteiro</span><span class="sxs-lookup"><span data-stu-id="345a4-138">KeyLength Data type: Integer</span></span>

<span data-ttu-id="345a4-139">Implemente este parâmetro para que o utilizador pode especificar o comprimento da chave em bits.</span><span class="sxs-lookup"><span data-stu-id="345a4-139">Implement this parameter so that the user can specify the length of the key in bits.</span></span>

<span data-ttu-id="345a4-140">Tipo de dados de operação: Cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="345a4-140">Operation Data type: String</span></span>

<span data-ttu-id="345a4-141">Implemente este parâmetro para que o utilizador pode especificar uma ação que pode ser executada num objeto protegido.</span><span class="sxs-lookup"><span data-stu-id="345a4-141">Implement this parameter so that the user can specify an action that can be performed on a protected object.</span></span>

<span data-ttu-id="345a4-142">Tipo de dados principal: Cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="345a4-142">Principal Data type: String</span></span>

<span data-ttu-id="345a4-143">Implemente este parâmetro para que o utilizador pode especificar uma entidade de identificação exclusiva para o acesso.</span><span class="sxs-lookup"><span data-stu-id="345a4-143">Implement this parameter so that the user can specify a unique identifiable entity for access.</span></span>

<span data-ttu-id="345a4-144">Tipo de dados de privilégio: Cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="345a4-144">Privilege Data type: String</span></span>

<span data-ttu-id="345a4-145">Implemente este parâmetro para que o utilizador pode especificar o direito de que um cmdlet tem de realizar uma operação de uma entidade específica.</span><span class="sxs-lookup"><span data-stu-id="345a4-145">Implement this parameter so that the user can specify the right a cmdlet needs to perform an operation for a particular entity.</span></span>

<span data-ttu-id="345a4-146">Tipo de dados de privilégios: Matriz de privilégios</span><span class="sxs-lookup"><span data-stu-id="345a4-146">Privileges Data type: Array of privileges</span></span>

<span data-ttu-id="345a4-147">Implemente este parâmetro para que o utilizador pode especificar os direitos de que precisa de um cmdlet para efetuar a operação para uma entrada específica.</span><span class="sxs-lookup"><span data-stu-id="345a4-147">Implement this parameter so that the user can specify the rights that a cmdlet needs to perform its operation for a particular entry.</span></span>

<span data-ttu-id="345a4-148">Tipo de dados de função: Cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="345a4-148">Role Data type: String</span></span>

<span data-ttu-id="345a4-149">Implemente este parâmetro para que o utilizador pode especificar um conjunto de operações que podem ser executadas por uma entidade.</span><span class="sxs-lookup"><span data-stu-id="345a4-149">Implement this parameter so that the user can specify a set of operations that can be performed by an entity.</span></span>

<span data-ttu-id="345a4-150">Tipo de dados de SaveCred: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="345a4-150">SaveCred Data type: SwitchParameter</span></span>

<span data-ttu-id="345a4-151">Implemente este parâmetro para que as credenciais guardadas anteriormente pelo utilizador serão utilizadas quando o parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="345a4-151">Implement this parameter so that credentials that were previously saved by the user will be used when the parameter is specified.</span></span>

<span data-ttu-id="345a4-152">Tipo de dados de âmbito: Cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="345a4-152">Scope Data type: String</span></span>

<span data-ttu-id="345a4-153">Implemente este parâmetro para que o utilizador pode especificar o grupo de objetos protegidos para o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="345a4-153">Implement this parameter so that the user can specify the group of protected objects for the cmdlet.</span></span>

<span data-ttu-id="345a4-154">Tipo de dados do SID: Cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="345a4-154">SID Data type: String</span></span>

<span data-ttu-id="345a4-155">Implemente este parâmetro para que o utilizador pode especificar um identificador exclusivo que representa uma entidade de segurança.</span><span class="sxs-lookup"><span data-stu-id="345a4-155">Implement this parameter so that the user can specify a unique identifier that represents a principal.</span></span>

<span data-ttu-id="345a4-156">Tipo de dados de confiável: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="345a4-156">Trusted Data type: SwitchParameter</span></span>

<span data-ttu-id="345a4-157">Implemente este parâmetro, de modo a que níveis de confiança são suportadas quando o parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="345a4-157">Implement this parameter so that trust levels are supported when the parameter is specified.</span></span>

<span data-ttu-id="345a4-158">Tipo de dados de TrustLevel: Palavra-chave</span><span class="sxs-lookup"><span data-stu-id="345a4-158">TrustLevel Data type: Keyword</span></span>

<span data-ttu-id="345a4-159">Implemente este parâmetro para que o utilizador pode especificar o nível de confiança que é suportado.</span><span class="sxs-lookup"><span data-stu-id="345a4-159">Implement this parameter so that the user can specify the trust level that is supported.</span></span> <span data-ttu-id="345a4-160">Por exemplo, os valores possíveis incluem fulltrust, intranet e internet.</span><span class="sxs-lookup"><span data-stu-id="345a4-160">For example, possible values include internet, intranet, and fulltrust.</span></span>

## <a name="see-also"></a><span data-ttu-id="345a4-161">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="345a4-161">See Also</span></span>

[<span data-ttu-id="345a4-162">Parâmetros do cmdlet</span><span class="sxs-lookup"><span data-stu-id="345a4-162">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="345a4-163">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="345a4-163">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="345a4-164">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="345a4-164">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
