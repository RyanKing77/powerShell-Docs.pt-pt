---
ms.date: 10/31/2017
keywords: DSC, powershell, configuração, a configuração
title: Proteger o ficheiro MOF
ms.openlocfilehash: f17c95c951151c0c11057ac0bce172c4ec73c91d
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893268"
---
# <a name="securing-the-mof-file"></a><span data-ttu-id="5b606-103">Proteger o ficheiro MOF</span><span class="sxs-lookup"><span data-stu-id="5b606-103">Securing the MOF File</span></span>

> <span data-ttu-id="5b606-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5b606-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="5b606-105">DSC gerencia a configuração de nós do servidor ao aplicar as informações armazenadas num ficheiro MOF, em que o Gestor de configuração Local (LCM) implementa o estado final desejada.</span><span class="sxs-lookup"><span data-stu-id="5b606-105">DSC manages the configuration of server nodes by applying information stored in a MOF file, where the Local Configuration Manager (LCM) implements the desired end state.</span></span>
<span data-ttu-id="5b606-106">Uma vez que este ficheiro contém os detalhes da configuração, é importante para mantê-lo seguro.</span><span class="sxs-lookup"><span data-stu-id="5b606-106">Because this file contains the details of the configuration, it’s important to keep it secure.</span></span>
<span data-ttu-id="5b606-107">Este tópico descreve como garantir que o nó de destino tiver encriptados o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="5b606-107">This topic describes how to ensure the target node has encrypted the file.</span></span>

<span data-ttu-id="5b606-108">A partir do PowerShell versão 5.0, todo o arquivo MOF é encriptado por predefinição quando é aplicada para o nó com o `Start-DSCConfiguration` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5b606-108">Beginning with PowerShell version 5.0, the entire MOF file is encrypted by default when it is applied to the node using the `Start-DSCConfiguration` cmdlet.</span></span>
<span data-ttu-id="5b606-109">O processo descrito neste artigo, é necessário apenas quando implementar uma solução utilizando o protocolo de serviço de solicitação, se os certificados não são geridos, para garantir que configurações transferidas pelo nó de destino podem ser desencriptadas e leia pelo sistema antes de estas são aplicadas (por exemplo, o serviço de solicitação disponível no Windows Server).</span><span class="sxs-lookup"><span data-stu-id="5b606-109">The process described in this article is required only when implementing a solution using the pull service protocol if certificates are not managed, to ensure configurations downloaded by the target node can be decrypted and read by the system before they are applied (for example, the pull service available in Windows Server).</span></span>
<span data-ttu-id="5b606-110">Nós registados [DSC de automatização do Azure](https://docs.microsoft.com/azure/automation/automation-dsc-overview) terão automaticamente certificados instalado e gerido pelo serviço sem sobrecarga administrativa necessária.</span><span class="sxs-lookup"><span data-stu-id="5b606-110">Nodes registered to [Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview) will automatically have certificates installed and managed by the service with no administrative overhead required.</span></span>

> [!NOTE]
> <span data-ttu-id="5b606-111">Este tópico aborda os certificados utilizados para encriptação.</span><span class="sxs-lookup"><span data-stu-id="5b606-111">This topic discusses certificates used for encryption.</span></span>
> <span data-ttu-id="5b606-112">Para a encriptação, um certificado auto-assinado é suficiente, porque a chave privada é sempre mantida segredo e de encriptação não implica a confiança do documento.</span><span class="sxs-lookup"><span data-stu-id="5b606-112">For encryption, a self-signed certificate is sufficient, because the private key is always kept secret and encryption does not imply trust of the document.</span></span>
> <span data-ttu-id="5b606-113">Certificados autoassinados devem *não* ser utilizados para fins de autenticação.</span><span class="sxs-lookup"><span data-stu-id="5b606-113">Self-signed certificates should *not* be used for authentication purposes.</span></span>
> <span data-ttu-id="5b606-114">Deve utilizar um certificado de uma confiança autoridade de certificação (AC) para efeitos de autenticação.</span><span class="sxs-lookup"><span data-stu-id="5b606-114">You should use a certificate from a trusted Certification Authority (CA) for any authentication purposes.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5b606-115">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="5b606-115">Prerequisites</span></span>

<span data-ttu-id="5b606-116">Para encriptar com êxito as credenciais utilizadas para proteger uma configuração de DSC, certifique-se de que tem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5b606-116">To successfully encrypt the credentials used to secure a DSC configuration, make sure you have the following:</span></span>

- <span data-ttu-id="5b606-117">**Alguns meios de emissão e distribuição de certificados**.</span><span class="sxs-lookup"><span data-stu-id="5b606-117">**Some means of issuing and distributing certificates**.</span></span> <span data-ttu-id="5b606-118">Este tópico e seus exemplos partem do princípio de que está a utilizar autoridade de certificação do Active Directory.</span><span class="sxs-lookup"><span data-stu-id="5b606-118">This topic and its examples assume you are using Active Directory Certification Authority.</span></span> <span data-ttu-id="5b606-119">Para obter mais informações sobre os serviços de certificados do Active Directory, consulte [Active Directory certificado serviços descrição geral](https://technet.microsoft.com/library/hh831740.aspx) e [serviços de certificados do Active Directory no Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).</span><span class="sxs-lookup"><span data-stu-id="5b606-119">For more background information on Active Directory Certificate Services, see [Active Directory Certificate Services Overview](https://technet.microsoft.com/library/hh831740.aspx) and [Active Directory Certificate Services in Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).</span></span>
- <span data-ttu-id="5b606-120">**Acesso administrativo para o nó de destino ou nós**.</span><span class="sxs-lookup"><span data-stu-id="5b606-120">**Administrative access to the target node or nodes**.</span></span>
- <span data-ttu-id="5b606-121">**Cada nó de destino tem um certificado com capacidade de encriptação, guardar Store seu pessoal**.</span><span class="sxs-lookup"><span data-stu-id="5b606-121">**Each target node has an encryption-capable certificate saved its Personal Store**.</span></span> <span data-ttu-id="5b606-122">No Windows PowerShell, o caminho para o arquivo é Cert: \LocalMachine\My.</span><span class="sxs-lookup"><span data-stu-id="5b606-122">In Windows PowerShell, the path to the store is Cert:\LocalMachine\My.</span></span> <span data-ttu-id="5b606-123">Os exemplos neste tópico utilizam o modelo de "autenticação de estação de trabalho", que pode ser encontrado (juntamente com outros modelos de certificado) em [modelos de certificado predefinido](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="5b606-123">The examples in this topic use the “workstation authentication” template, which you can find (along with other certificate templates) at [Default Certificate Templates](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span></span>
- <span data-ttu-id="5b606-124">Se executar esta configuração num computador que não seja o nó de destino **exportar a chave pública do certificado**e, em seguida, importe-o para o computador irá executar a configuração a partir de.</span><span class="sxs-lookup"><span data-stu-id="5b606-124">If you will be running this configuration on a computer other than the target node, **export the public key of the certificate**, and then import it to the computer you will run the configuration from.</span></span> <span data-ttu-id="5b606-125">Certifique-se de que exporta apenas o **público** chave; proteger a chave privada.</span><span class="sxs-lookup"><span data-stu-id="5b606-125">Make sure that you export only the **public** key; keep the private key secure.</span></span>

## <a name="overall-process"></a><span data-ttu-id="5b606-126">Processo geral</span><span class="sxs-lookup"><span data-stu-id="5b606-126">Overall process</span></span>

 1. <span data-ttu-id="5b606-127">Configure os certificados, chaves e thumbprints, certificar-se de que cada nó de destino tem cópias do certificado e a configuração de computador tem a chave pública e o thumbprint.</span><span class="sxs-lookup"><span data-stu-id="5b606-127">Set up the certificates, keys, and thumbprints, making sure that each target node has copies of the certificate and the configuration computer has the public key and thumbprint.</span></span>
 2. <span data-ttu-id="5b606-128">Crie um bloco de dados de configuração que contém o caminho e o thumbprint da chave pública.</span><span class="sxs-lookup"><span data-stu-id="5b606-128">Create a configuration data block that contains the path and thumbprint of the public key.</span></span>
 3. <span data-ttu-id="5b606-129">Crie um script de configuração que define a configuração pretendida para o nó de destino e configura a desencriptação em nós de destino por comandos de configuração Local manager para descriptografar os dados de configuração a utilizar o certificado e sua impressão digital.</span><span class="sxs-lookup"><span data-stu-id="5b606-129">Create a configuration script that defines your desired configuration for the target node and sets up decryption on the target nodes by commanding the Local Configuration manager to decrypt the configuration data using the certificate and its thumbprint.</span></span>
 4. <span data-ttu-id="5b606-130">Execute a configuração, que irá configurar as definições do Gestor de configuração Local e iniciar a configuração de DSC.</span><span class="sxs-lookup"><span data-stu-id="5b606-130">Run the configuration, which will set the Local Configuration Manager settings and start the DSC configuration.</span></span>

![Diagram1](images/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a><span data-ttu-id="5b606-132">Requisitos de certificado</span><span class="sxs-lookup"><span data-stu-id="5b606-132">Certificate Requirements</span></span>

<span data-ttu-id="5b606-133">Adotar a encriptação de credenciais, um certificado de chave pública tem de estar disponível na _nó de destino_ ou seja **fidedigna** pelo computador que está a ser usado para criar a configuração de DSC.</span><span class="sxs-lookup"><span data-stu-id="5b606-133">To enact credential encryption, a public key certificate must be available on the _Target Node_ that is **trusted** by the computer being used to author the DSC configuration.</span></span>
<span data-ttu-id="5b606-134">Este certificado de chave pública tem requisitos específicos para poder ser utilizado para encriptação de credenciais de DSC:</span><span class="sxs-lookup"><span data-stu-id="5b606-134">This public key certificate has specific requirements for it to be used for DSC credential encryption:</span></span>

1. <span data-ttu-id="5b606-135">**Utilização de chave**:</span><span class="sxs-lookup"><span data-stu-id="5b606-135">**Key Usage**:</span></span>
   - <span data-ttu-id="5b606-136">Tem de conter: 'KeyEncipherment' e 'DataEncipherment'.</span><span class="sxs-lookup"><span data-stu-id="5b606-136">Must contain: 'KeyEncipherment' and 'DataEncipherment'.</span></span>
   - <span data-ttu-id="5b606-137">Deve _não_ contêm: "Assinatura Digital".</span><span class="sxs-lookup"><span data-stu-id="5b606-137">Should _not_ contain: 'Digital Signature'.</span></span>
2. <span data-ttu-id="5b606-138">**Utilização de chave avançada**:</span><span class="sxs-lookup"><span data-stu-id="5b606-138">**Enhanced Key Usage**:</span></span>
   - <span data-ttu-id="5b606-139">Tem de conter: encriptação de documentos (1.3.6.1.4.1.311.80.1).</span><span class="sxs-lookup"><span data-stu-id="5b606-139">Must contain: Document Encryption (1.3.6.1.4.1.311.80.1).</span></span>
   - <span data-ttu-id="5b606-140">Deve _não_ contêm: autenticação de cliente (1.3.6.1.5.5.7.3.2) e a autenticação de servidor (1.3.6.1.5.5.7.3.1).</span><span class="sxs-lookup"><span data-stu-id="5b606-140">Should _not_ contain: Client Authentication (1.3.6.1.5.5.7.3.2) and Server Authentication (1.3.6.1.5.5.7.3.1).</span></span>
3. <span data-ttu-id="5b606-141">A chave privada do certificado está disponível na \* Node_ de destino.</span><span class="sxs-lookup"><span data-stu-id="5b606-141">The Private Key for the certificate is available on the \*Target Node_.</span></span>
4. <span data-ttu-id="5b606-142">O **fornecedor** para o certificado tem de ser "Microsoft RSA SChannel fornecedor de criptografia".</span><span class="sxs-lookup"><span data-stu-id="5b606-142">The **Provider** for the certificate must be "Microsoft RSA SChannel Cryptographic Provider".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5b606-143">Apesar de poder utilizar um certificado com que contém uma utilização de chave de "Assinatura Digital" ou uma da EKU de autenticação, isso permitirá que a chave de encriptação mais facilmente ser desfeitos e vulnerável a ataques.</span><span class="sxs-lookup"><span data-stu-id="5b606-143">Although you can use a certificate with containing a Key Usage of 'Digital Signature' or one of the Authentication EKU's, this will enable the encryption key to be more easily misused and vulnerable to attack.</span></span> <span data-ttu-id="5b606-144">Portanto, é melhor prática para utilizar um certificado criado especificamente para a finalidade de proteger as credenciais de DSC que omite estes utilização de chave e EKUs.</span><span class="sxs-lookup"><span data-stu-id="5b606-144">So it is best practice to use a certificate created specifically for the purpose of securing DSC credentials that omits these Key Usage and EKUs.</span></span>

<span data-ttu-id="5b606-145">Qualquer certificado existente no _nó de destino_ que satisfazem esses critérios podem ser utilizadas para proteger credenciais de DSC.</span><span class="sxs-lookup"><span data-stu-id="5b606-145">Any existing certificate on the _Target Node_ that meets these criteria can be used to secure DSC credentials.</span></span>

## <a name="certificate-creation"></a><span data-ttu-id="5b606-146">Criação do certificado</span><span class="sxs-lookup"><span data-stu-id="5b606-146">Certificate creation</span></span>

<span data-ttu-id="5b606-147">Existem duas abordagens que pode seguir para criar e utilizar o certificado de encriptação necessário (par de chaves públicas-privadas).</span><span class="sxs-lookup"><span data-stu-id="5b606-147">There are two approaches you can take to create and use the required Encryption Certificate (public-private key pair).</span></span>

1. <span data-ttu-id="5b606-148">Criá-la no **nó de destino** e exportar a chave pública para o **nó de criação**</span><span class="sxs-lookup"><span data-stu-id="5b606-148">Create it on the **Target Node** and export just the public key to the **Authoring Node**</span></span>
2. <span data-ttu-id="5b606-149">Criá-la no **nó criação** e exportar o par de chaves completo para o **nó de destino**</span><span class="sxs-lookup"><span data-stu-id="5b606-149">Create it on the **Authoring Node** and export the entire key pair to the **Target Node**</span></span>

<span data-ttu-id="5b606-150">Método 1 é recomendado porque a chave privada utilizada para desencriptar credenciais no MOF permanece no nó de destino em todos os momentos.</span><span class="sxs-lookup"><span data-stu-id="5b606-150">Method 1 is recommended because the private key used to decrypt credentials in the MOF stays on the Target Node at all times.</span></span>

### <a name="creating-the-certificate-on-the-target-node"></a><span data-ttu-id="5b606-151">Criar o certificado no nó de destino</span><span class="sxs-lookup"><span data-stu-id="5b606-151">Creating the Certificate on the Target Node</span></span>

<span data-ttu-id="5b606-152">A chave privada deve ser mantida em sigilo, porque é utilizado para desencriptar o MOF no **nó de destino** a forma mais fácil de fazer isso é criar o certificado de chave privado no **nó de destino**e copie o  **certificado de chave pública** para o computador que está a ser utilizado para criar a configuração de DSC para um ficheiro MOF.</span><span class="sxs-lookup"><span data-stu-id="5b606-152">The private key must be kept secret, because is used to decrypt the MOF on the **Target Node** The easiest way to do that is to create the private key certificate on the **Target Node**, and copy the **public key certificate** to the computer being used to author the DSC configuration into a MOF file.</span></span>
<span data-ttu-id="5b606-153">O exemplo seguinte:</span><span class="sxs-lookup"><span data-stu-id="5b606-153">The following example:</span></span>

1. <span data-ttu-id="5b606-154">cria um certificado no **nó de destino**</span><span class="sxs-lookup"><span data-stu-id="5b606-154">creates a certificate on the **Target node**</span></span>
2. <span data-ttu-id="5b606-155">Exporta o certificado de chave público no **nó de destino**.</span><span class="sxs-lookup"><span data-stu-id="5b606-155">exports the public key certificate on the **Target node**.</span></span>
3. <span data-ttu-id="5b606-156">importa o certificado de chave público para o **minha** arquivo de certificados a **criação nó**.</span><span class="sxs-lookup"><span data-stu-id="5b606-156">imports the public key certificate into the **my** certificate store on the **Authoring node**.</span></span>

#### <a name="on-the-target-node-create-and-export-the-certificate"></a><span data-ttu-id="5b606-157">No nó de destino: criar e exportar o certificado</span><span class="sxs-lookup"><span data-stu-id="5b606-157">On the Target Node: create and export the certificate</span></span>

> <span data-ttu-id="5b606-158">Nó de destino: Windows Server 2016 e Windows 10</span><span class="sxs-lookup"><span data-stu-id="5b606-158">Target Node: Windows Server 2016 and Windows 10</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

<span data-ttu-id="5b606-159">Exportar uma vez, o `DscPublicKey.cer` precisaria ser copiados para o **criação nó**.</span><span class="sxs-lookup"><span data-stu-id="5b606-159">Once exported, the `DscPublicKey.cer` would need to be copied to the **Authoring Node**.</span></span>

> <span data-ttu-id="5b606-160">Nó de destino: Windows Server 2012 R2/Windows 8.1 e versões anteriores</span><span class="sxs-lookup"><span data-stu-id="5b606-160">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>
> [!WARNING]
> <span data-ttu-id="5b606-161">Uma vez que o `New-SelfSignedCertificate` cmdlet no Windows sistemas operativos anteriores ao Windows 10 e Windows Server 2016 não suportam a **tipo** parâmetro, um método alternativo de criar este certificado é necessário nesses sistemas operacionais.</span><span class="sxs-lookup"><span data-stu-id="5b606-161">Because the `New-SelfSignedCertificate` cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span>
>
> <span data-ttu-id="5b606-162">Neste caso, pode utilizar `makecert.exe` ou `certutil.exe` para criar o certificado.</span><span class="sxs-lookup"><span data-stu-id="5b606-162">In this case you can use `makecert.exe` or `certutil.exe` to create the certificate.</span></span>
>
><span data-ttu-id="5b606-163">É um método alternativo [transferir o script New-SelfSignedCertificateEx.ps1 a partir do Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) e utilizá-lo para criar o certificado em vez disso:</span><span class="sxs-lookup"><span data-stu-id="5b606-163">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
# and in the folder that contains New-SelfSignedCertificateEx.ps1
. .\New-SelfSignedCertificateEx.ps1
New-SelfsignedCertificateEx `
    -Subject "CN=${ENV:ComputerName}" `
    -EKU 'Document Encryption' `
    -KeyUsage 'KeyEncipherment, DataEncipherment' `
    -SAN ${ENV:ComputerName} `
    -FriendlyName 'DSC Credential Encryption certificate' `
    -Exportable `
    -StoreLocation 'LocalMachine' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

<span data-ttu-id="5b606-164">Exportar uma vez, o ```DscPublicKey.cer``` precisaria ser copiados para o **criação nó**.</span><span class="sxs-lookup"><span data-stu-id="5b606-164">Once exported, the ```DscPublicKey.cer``` would need to be copied to the **Authoring Node**.</span></span>

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a><span data-ttu-id="5b606-165">No nó de criação: importar a chave pública do certificado</span><span class="sxs-lookup"><span data-stu-id="5b606-165">On the Authoring Node: import the cert’s public key</span></span>

```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a><span data-ttu-id="5b606-166">Criar o certificado no nó de criação</span><span class="sxs-lookup"><span data-stu-id="5b606-166">Creating the Certificate on the Authoring Node</span></span>

<span data-ttu-id="5b606-167">Em alternativa, o certificado de encriptação pode ser criado no **nó criação**, exportado com o **chave privada** como um PFX do ficheiro e, em seguida, importado no **nó de destino**.</span><span class="sxs-lookup"><span data-stu-id="5b606-167">Alternately, the encryption certificate can be created on the **Authoring Node**, exported with the **private key** as a PFX file and then imported on the **Target Node**.</span></span>
<span data-ttu-id="5b606-168">Este é o método atual para a implementação de encriptação de credenciais do DSC na _servidor Nano_.</span><span class="sxs-lookup"><span data-stu-id="5b606-168">This is the current method for implementing DSC credential encryption on _Nano Server_.</span></span>
<span data-ttu-id="5b606-169">Embora o PFX é protegido com uma palavra-passe deve ser mantida seguro durante o trânsito.</span><span class="sxs-lookup"><span data-stu-id="5b606-169">Although the PFX is secured with a password it should be kept secure during transit.</span></span>
<span data-ttu-id="5b606-170">O exemplo seguinte:</span><span class="sxs-lookup"><span data-stu-id="5b606-170">The following example:</span></span>

1. <span data-ttu-id="5b606-171">cria um certificado no **Authoring nó**.</span><span class="sxs-lookup"><span data-stu-id="5b606-171">creates a certificate on the **Authoring node**.</span></span>
2. <span data-ttu-id="5b606-172">Exporta o certificado, incluindo a chave privada sobre o **Authoring nó**.</span><span class="sxs-lookup"><span data-stu-id="5b606-172">exports the certificate including the private key on the **Authoring node**.</span></span>
3. <span data-ttu-id="5b606-173">Remove a chave privada do **nó de criação de conteúdos**, mas mantém o certificado de chave público na **meu** armazenar.</span><span class="sxs-lookup"><span data-stu-id="5b606-173">removes the private key from the **Authoring node**, but keeps the public key certificate in the **my** store.</span></span>
4. <span data-ttu-id="5b606-174">importa o certificado de chave privado para o arquivo de certificados My(Personal) sobre o **nó de destino**.</span><span class="sxs-lookup"><span data-stu-id="5b606-174">imports the private key certificate into the My(Personal) certificate store on the **Target node**.</span></span>
   - <span data-ttu-id="5b606-175">tem de ser adicionado ao arquivo de raiz, para que possam confiar nele o **nó de destino**.</span><span class="sxs-lookup"><span data-stu-id="5b606-175">it must be added to the root store so that it will be trusted by the **Target node**.</span></span>

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a><span data-ttu-id="5b606-176">No nó de criação: criar e exportar o certificado</span><span class="sxs-lookup"><span data-stu-id="5b606-176">On the Authoring Node: create and export the certificate</span></span>

> <span data-ttu-id="5b606-177">Nó de destino: Windows Server 2016 e Windows 10</span><span class="sxs-lookup"><span data-stu-id="5b606-177">Target Node: Windows Server 2016 and Windows 10</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the private key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

<span data-ttu-id="5b606-178">Exportar uma vez, o `DscPrivateKey.pfx` precisaria ser copiados para o **nó de destino**.</span><span class="sxs-lookup"><span data-stu-id="5b606-178">Once exported, the `DscPrivateKey.pfx` would need to be copied to the **Target Node**.</span></span>

> <span data-ttu-id="5b606-179">Nó de destino: Windows Server 2012 R2/Windows 8.1 e versões anteriores</span><span class="sxs-lookup"><span data-stu-id="5b606-179">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>
> [!WARNING]
> <span data-ttu-id="5b606-180">Uma vez que o `New-SelfSignedCertificate` cmdlet no Windows sistemas operativos anteriores ao Windows 10 e Windows Server 2016 não suportam a **tipo** parâmetro, um método alternativo de criar este certificado é necessário nesses sistemas operacionais.</span><span class="sxs-lookup"><span data-stu-id="5b606-180">Because the `New-SelfSignedCertificate` cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span>
>
> <span data-ttu-id="5b606-181">Neste caso, pode utilizar `makecert.exe` ou `certutil.exe` para criar o certificado.</span><span class="sxs-lookup"><span data-stu-id="5b606-181">In this case you can use `makecert.exe` or `certutil.exe` to create the certificate.</span></span>
>
> <span data-ttu-id="5b606-182">É um método alternativo [transferir o script New-SelfSignedCertificateEx.ps1 a partir do Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) e utilizá-lo para criar o certificado em vez disso:</span><span class="sxs-lookup"><span data-stu-id="5b606-182">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
# and in the folder that contains New-SelfSignedCertificateEx.ps1
. .\New-SelfSignedCertificateEx.ps1
New-SelfsignedCertificateEx `
    -Subject "CN=${ENV:ComputerName}" `
    -EKU 'Document Encryption' `
    -KeyUsage 'KeyEncipherment, DataEncipherment' `
    -SAN ${ENV:ComputerName} `
    -FriendlyName 'DSC Credential Encryption certificate' `
    -Exportable `
    -StoreLocation 'LocalMachine' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

#### <a name="on-the-target-node-import-the-certs-private-key-as-a-trusted-root"></a><span data-ttu-id="5b606-183">No nó de destino: importar a chave privada do certificado como uma raiz confiável</span><span class="sxs-lookup"><span data-stu-id="5b606-183">On the Target Node: import the cert’s private key as a trusted root</span></span>

```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\My -Password $mypwd > $null
```

## <a name="configuration-data"></a><span data-ttu-id="5b606-184">Dados de configuração</span><span class="sxs-lookup"><span data-stu-id="5b606-184">Configuration data</span></span>

<span data-ttu-id="5b606-185">O bloco de dados de configuração define que nós de destino para operar em se deve ou não para encriptar as credenciais, o meio de encriptação e outras informações.</span><span class="sxs-lookup"><span data-stu-id="5b606-185">The configuration data block defines which target nodes to operate on, whether or not to encrypt the credentials, the means of encryption, and other information.</span></span> <span data-ttu-id="5b606-186">Para obter mais informações sobre o bloco de dados de configuração, consulte [separar a configuração e dados de ambiente](configData.md).</span><span class="sxs-lookup"><span data-stu-id="5b606-186">For more information on the configuration data block, see [Separating Configuration and Environment Data](configData.md).</span></span>

<span data-ttu-id="5b606-187">Os elementos que podem ser configurados para cada nó que estão relacionados com a encriptação de credenciais são:</span><span class="sxs-lookup"><span data-stu-id="5b606-187">The elements that can be configured for each node that are related to credential encryption are:</span></span>

- <span data-ttu-id="5b606-188">**NodeName** -o nome do nó de destino que está a ser configurado para a encriptação de credenciais.</span><span class="sxs-lookup"><span data-stu-id="5b606-188">**NodeName** - the name of the target node that the credential encryption is being configured for.</span></span>
- <span data-ttu-id="5b606-189">**PsDscAllowPlainTextPassword** - se as credenciais não encriptadas terá permissão para ser passado para este nó.</span><span class="sxs-lookup"><span data-stu-id="5b606-189">**PsDscAllowPlainTextPassword** - whether unencrypted credentials will be allowed to be passed to this node.</span></span> <span data-ttu-id="5b606-190">Isto é **não recomendada**.</span><span class="sxs-lookup"><span data-stu-id="5b606-190">This is **not recommended**.</span></span>
- <span data-ttu-id="5b606-191">**Thumbprint** -o thumbprint do certificado que será utilizado para desencriptar as credenciais na configuração do DSC na _nó de destino_.</span><span class="sxs-lookup"><span data-stu-id="5b606-191">**Thumbprint** - the thumbprint of the certificate that will be used to decrypt the credentials in the DSC Configuration on the _Target Node_.</span></span> <span data-ttu-id="5b606-192">**Este certificado tem de existir no arquivo de certificados do computador Local no nó de destino.**</span><span class="sxs-lookup"><span data-stu-id="5b606-192">**This certificate must exist in the Local Machine certificate store on the Target Node.**</span></span>
- <span data-ttu-id="5b606-193">**CertificateFile** – o ficheiro de certificado (contendo apenas a chave pública) que deve ser utilizada para encriptar as credenciais para o _nó de destino_.</span><span class="sxs-lookup"><span data-stu-id="5b606-193">**CertificateFile** - the certificate file (containing the public key only) that should be used to encrypt the credentials for the _Target Node_.</span></span> <span data-ttu-id="5b606-194">Isso tem de ser binário codificado um DER X.509 ou ficheiro de certificado de formato X.509 com codificação Base 64.</span><span class="sxs-lookup"><span data-stu-id="5b606-194">This must be either a DER encoded binary X.509 or Base-64 encoded X.509 format certificate file.</span></span>

<span data-ttu-id="5b606-195">Este exemplo mostra um bloco de dados de configuração que especifica um nó de destino para atuar em targetNode com nome, o caminho para o ficheiro de certificado de chave pública (denominado targetNode.cer) e o thumbprint para a chave pública.</span><span class="sxs-lookup"><span data-stu-id="5b606-195">This example shows a configuration data block that specifies a target node to act on named targetNode, the path to the public key certificate file (named targetNode.cer), and the thumbprint for the public key.</span></span>

```powershell
$ConfigData= @{
    AllNodes = @(
            @{
                # The name of the node we are describing
                NodeName = "targetNode"

                # The path to the .cer file containing the
                # public key of the Encryption Certificate
                # used to encrypt credentials for this node
                CertificateFile = "C:\publicKeys\targetNode.cer"


                # The thumbprint of the Encryption Certificate
                # used to decrypt the credentials on target node
                Thumbprint = "AC23EA3A9E291A75757A556D0B71CBBF8C4F6FD8"
            };
        );
    }
```

## <a name="configuration-script"></a><span data-ttu-id="5b606-196">Script de configuração</span><span class="sxs-lookup"><span data-stu-id="5b606-196">Configuration script</span></span>

<span data-ttu-id="5b606-197">O script de configuração em si, utilize o `PsCredential` parâmetro para garantir que as credenciais são armazenadas para o menor tempo possível.</span><span class="sxs-lookup"><span data-stu-id="5b606-197">In the configuration script itself, use the `PsCredential` parameter to ensure that credentials are stored for the shortest possible time.</span></span> <span data-ttu-id="5b606-198">Ao executar o exemplo fornecido, DSC irá solicitar-lhe as credenciais e, em seguida, encriptar o ficheiro MOF utilizando o CertificateFile que estão associado com o nó de destino no bloco de dados de configuração.</span><span class="sxs-lookup"><span data-stu-id="5b606-198">When you run the supplied example, DSC will prompt you for credentials and then encrypt the MOF file using the CertificateFile that is associated with the target node in the configuration data block.</span></span> <span data-ttu-id="5b606-199">Este exemplo de código copia um ficheiro a partir de um compartilhamento que está protegido para um utilizador.</span><span class="sxs-lookup"><span data-stu-id="5b606-199">This code example copies a file from a share that is secured to a user.</span></span>

```powershell
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\Server\share\path\file.ext"
            DestinationPath = "C:\destinationPath"
            Credential = $credential
        }
    }
}
```

## <a name="setting-up-decryption"></a><span data-ttu-id="5b606-200">Configuração de desencriptação</span><span class="sxs-lookup"><span data-stu-id="5b606-200">Setting up decryption</span></span>

<span data-ttu-id="5b606-201">Antes de [ `Start-DscConfiguration` ](https://technet.microsoft.com/library/dn521623.aspx) pode funcionar, é necessário informar ao Gestor de configuração Local em cada nó de destino de certificado a utilizar para desencriptar as credenciais, usando o recurso de CertificateID para verificar o thumbprint do certificado.</span><span class="sxs-lookup"><span data-stu-id="5b606-201">Before [`Start-DscConfiguration`](https://technet.microsoft.com/library/dn521623.aspx) can work, you have to tell the Local Configuration Manager on each target node which certificate to use to decrypt the credentials, using the CertificateID resource to verify the certificate’s thumbprint.</span></span> <span data-ttu-id="5b606-202">Esta função de exemplo irá encontrar o certificado local apropriado (poderá ter de personalizá-lo para que ele irá encontrar o certificado exato de que pretende utilizar):</span><span class="sxs-lookup"><span data-stu-id="5b606-202">This example function will find the appropriate local certificate (you might have to customize it so it will find the exact certificate you want to use):</span></span>

```powershell
# Get the certificate that works for encryption
function Get-LocalEncryptionCertificateThumbprint
{
    (dir Cert:\LocalMachine\my) | %{
        # Verify the certificate is for Encryption and valid
        if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
        {
            return $_.Thumbprint
        }
    }
}
```

<span data-ttu-id="5b606-203">Com o certificado identificado por sua impressão digital, o script de configuração pode ser atualizado para utilizar o valor:</span><span class="sxs-lookup"><span data-stu-id="5b606-203">With the certificate identified by its thumbprint, the configuration script can be updated to use the value:</span></span>

```powershell
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\Server\share\path\file.ext"
            DestinationPath = "C:\destinationPath"
            Credential = $credential
        }

        LocalConfigurationManager
        {
             CertificateId = $node.Thumbprint
        }
    }
}
```

## <a name="running-the-configuration"></a><span data-ttu-id="5b606-204">Executar a configuração</span><span class="sxs-lookup"><span data-stu-id="5b606-204">Running the configuration</span></span>

<span data-ttu-id="5b606-205">Neste momento, pode executar a configuração, que vai exportar os dois arquivos:</span><span class="sxs-lookup"><span data-stu-id="5b606-205">At this point, you can run the configuration, which will output two files:</span></span>

- <span data-ttu-id="5b606-206">A \*. ficheiro meta.mof que configura o Gestor de configuração de Local para desencriptar as credenciais a utilizar o certificado que é armazenado no arquivo local e identificado por sua impressão digital.</span><span class="sxs-lookup"><span data-stu-id="5b606-206">A \*.meta.mof file that configures the Local Configuration Manager to decrypt the credentials using the certificate that is stored on the local machine store and identified by its thumbprint.</span></span> <span data-ttu-id="5b606-207">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx) aplica-se a \*. meta.mof ficheiro.</span><span class="sxs-lookup"><span data-stu-id="5b606-207">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx) applies the \*.meta.mof file.</span></span>
- <span data-ttu-id="5b606-208">Um ficheiro MOF que, na verdade, se aplica a configuração.</span><span class="sxs-lookup"><span data-stu-id="5b606-208">A MOF file that actually applies the configuration.</span></span> <span data-ttu-id="5b606-209">Start-dscconfiguration para aplica-se a configuração.</span><span class="sxs-lookup"><span data-stu-id="5b606-209">Start-DscConfiguration applies the configuration.</span></span>

<span data-ttu-id="5b606-210">Estes comandos irão realizar essas etapas:</span><span class="sxs-lookup"><span data-stu-id="5b606-210">These commands will accomplish those steps:</span></span>

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

<span data-ttu-id="5b606-211">Neste exemplo emitiria a configuração de DSC para o nó de destino.</span><span class="sxs-lookup"><span data-stu-id="5b606-211">This example would push the DSC configuration to the target node.</span></span>
<span data-ttu-id="5b606-212">Também pode ser aplicada a configuração de DSC com um servidor de solicitação de DSC, se disponível.</span><span class="sxs-lookup"><span data-stu-id="5b606-212">The DSC configuration can also be applied using a DSC Pull Server if one is available.</span></span>

<span data-ttu-id="5b606-213">Ver [como configurar um cliente de solicitação de DSC](pullClient.md) para obter mais informações sobre a aplicação de configurações de DSC com um servidor de solicitação de DSC.</span><span class="sxs-lookup"><span data-stu-id="5b606-213">See [Setting up a DSC pull client](pullClient.md) for more information on applying DSC configurations using a DSC Pull Server.</span></span>

## <a name="credential-encryption-module-example"></a><span data-ttu-id="5b606-214">Exemplo de módulo de encriptação de credenciais</span><span class="sxs-lookup"><span data-stu-id="5b606-214">Credential Encryption Module Example</span></span>

<span data-ttu-id="5b606-215">Eis um exemplo completo que incorpora todas essas etapas, além de um cmdlet de programa auxiliar que exporta e copia as chaves públicas:</span><span class="sxs-lookup"><span data-stu-id="5b606-215">Here is a full example that incorporates all of these steps, plus a helper cmdlet that exports and copies the public keys:</span></span>

```powershell
# A simple example of using credentials
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\server\share\file.txt"
            DestinationPath = "C:\Users\user"
            Credential = $credential
        }

        LocalConfigurationManager
        {
            CertificateId = $node.Thumbprint
        }
    }
}

# A Helper to invoke the configuration, with the correct public key
# To encrypt the configuration credentials
function Start-CredentialEncryptionExample
{
    [CmdletBinding()]
    param ($computerName)


    [string] $thumbprint = Get-EncryptionCertificate -computerName $computerName -Verbose
    Write-Verbose "using cert: $thumbprint"

    $certificatePath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"

    $ConfigData=    @{
        AllNodes = @(
                        @{
                            # The name of the node we are describing
                            NodeName = "$computerName"

                            # The path to the .cer file containing the
                            # public key of the Encryption Certificate
                            CertificateFile = "$certificatePath"

                            # The thumbprint of the Encryption Certificate
                            # used to decrypt the credentials
                            Thumbprint = $thumbprint
                        };
                    );
    }

    Write-Verbose "Generate DSC Configuration..."
    CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample `
        -credential (Get-Credential -UserName "$env:USERDOMAIN\$env:USERNAME" -Message "Enter credentials for configuration")

    Write-Verbose "Setting up LCM to decrypt credentials..."
    Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

    Write-Verbose "Starting Configuration..."
    Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose

}


#region HelperFunctions

# The folder name for the exported public keys
$script:publicKeyFolder = "publicKeys"

# Get the certificate that works for encryptions
function Get-EncryptionCertificate
{
    [CmdletBinding()]
    param ($computerName)
    $returnValue= Invoke-Command -ComputerName $computerName -ScriptBlock {
            $certificates = dir Cert:\LocalMachine\my

            $certificates | %{
                    # Verify the certificate is for Encryption and valid
                    if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
                    {
                        # Create the folder to hold the exported public key
                        $folder= Join-Path -Path $env:SystemDrive\ -ChildPath $using:publicKeyFolder
                        if (! (Test-Path $folder))
                        {
                            md $folder | Out-Null
                        }

                        # Export the public key to a well known location
                        $certPath = Export-Certificate -Cert $_ -FilePath (Join-Path -path $folder -childPath "EncryptionCertificate.cer")

                        # Return the thumbprint, and exported certificate path
                        return @($_.Thumbprint,$certPath);
                    }
                  }
        }
    Write-Verbose "Identified and exported cert..."
    # Copy the exported certificate locally
    $destinationPath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"
    Copy-Item -Path (join-path -path \\$computername -childPath $returnValue[1].FullName.Replace(":","$"))  $destinationPath | Out-Null

    # Return the thumbprint
    return $returnValue[0]
}

Start-CredentialEncryptionExample
```