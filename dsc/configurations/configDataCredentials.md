---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Opções de credenciais nos dados de configuração
ms.openlocfilehash: 2a326e45bbbad7bd2362b66b88bf61b98df7b02e
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/18/2019
ms.locfileid: "55686377"
---
# <a name="credentials-options-in-configuration-data"></a>Opções de credenciais nos dados de configuração

>Aplica-se a: Windows PowerShell 5.0

## <a name="plain-text-passwords-and-domain-users"></a>As palavras-passe de texto simples e os utilizadores de domínio

Configurações de DSC que contém uma credencial sem encriptação irão gerar uma mensagem de erro sobre palavras-passe de texto simples.
Além disso, DSC irá gerar um aviso ao utilizar as credenciais do domínio.
Para suprimir estas mensagens de aviso de erro e utilizam as palavras-chave do DSC configuração dados:

- **PsDscAllowPlainTextPassword**
- **PsDscAllowDomainUser**

> [!NOTE]
> Armazenar/transmitir palavras-passe de texto simples não encriptadas é geralmente não segura. É recomendado proteger credenciais através de técnicas tratadas mais à frente neste tópico.
> O serviço do Automation DSC do Azure permite-lhe gerir centralmente as credenciais para ser compilado em configurações e armazenadas em segurança.
> Para informações, consulte: [Compilar configurações de DSC / ativos de credenciais](/azure/automation/automation-dsc-compile#credential-assets)

## <a name="handling-credentials-in-dsc"></a>Processamento de credenciais no DSC

Recursos de configuração de DSC run `Local System` por predefinição.
No entanto, alguns recursos tem uma credencial, por exemplo quando o `Package` recursos tem de instalar o software com uma conta de utilizador específico.

Recursos anteriores utilizados um hard-coded `Credential` nome da propriedade para lidar com isto.
WMF 5.0 adicionado um automático `PsDscRunAsCredential` propriedade para todos os recursos.
Para obter informações sobre como utilizar `PsDscRunAsCredential`, consulte [DSC em execução com as credenciais de utilizador](runAsUser.md).
Recursos mais recentes e recursos personalizados podem utilizar esta propriedade automática em vez de criar as seus próprios propriedade credenciais.

> [!NOTE]
> A estrutura de alguns recursos estão a utilizar várias credenciais para um motivo específico e terá as seus próprios propriedades de credencial.

Para localizar a credencial disponível propriedades num recurso utilizam `Get-DscResource -Name ResourceName -Syntax` ou o Intellisense no ISE do (`CTRL+SPACE`).

```powershell
PS C:\> Get-DscResource -Name Group -Syntax
Group [String] #ResourceName
{
    GroupName = [string]
    [Credential = [PSCredential]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Members = [string[]]]
    [MembersToExclude = [string[]]]
    [MembersToInclude = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

Este exemplo utiliza um [grupo](../resources/resources.md) recurso do `PSDesiredStateConfiguration` módulo incorporado de recursos de DSC.
Pode criar grupos locais e adicionar ou remover membros.
Aceita ambos o `Credential` propriedade e o automático `PsDscRunAsCredential` propriedade.
No entanto, o recurso utiliza apenas a `Credential` propriedade.

Para obter mais informações sobre o `PsDscRunAsCredential` propriedade, consulte [DSC em execução com as credenciais de utilizador](runAsUser.md).

## <a name="example-the-group-resource-credential-property"></a>Exemplo: O recurso do grupo de propriedade de credencial

É executado DSC `Local System`, pelo que já tem as permissões para alterar os utilizadores e grupos locais.
Se o membro adicionado é uma conta local, não é necessária nenhuma credencial.
Se o `Group` recursos adiciona uma conta de domínio ao grupo local, em seguida, é necessária uma credencial.

Não são permitidas consultas anónimas ao Active Directory.
O `Credential` propriedade o `Group` recurso é a conta de domínio utilizada para a consulta do Active Directory.
Para fins de maioria dos tal poderá dever uma conta de utilizador genérico, por predefinição, os utilizadores podem *ler* maioria dos objetos no Active Directory.

## <a name="example-configuration"></a>Configuração de exemplo

O código de exemplo seguinte utiliza DSC para preencher um grupo local com um utilizador de domínio:

```powershell
Configuration DomainCredentialExample
{
    param
    (
        [PSCredential] $DomainCredential
    )
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $DomainCredential
        }
    }
}

$cred = Get-Credential -UserName contoso\genericuser -Message "Password please"
DomainCredentialExample -DomainCredential $cred
```

Este código gera um erro e a mensagem de aviso:

```
ConvertTo-MOFInstance : System.InvalidOperationException error processing property 'Credential' OF
TYPE 'Group': Converting and storing encrypted passwords as plain text is not recommended.
For more information on securing credentials in MOF file, please refer to MSDN blog:
https://go.microsoft.com/fwlink/?LinkId=393729

At line:11 char:9
+   Group
At line:341 char:16
+     $aliasId = ConvertTo-MOFInstance $keywordName $canonicalizedValue
+                ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessProperty,ConvertTo-MOFInstance
WARNING: It is not recommended to use domain credential for node 'localhost'. In order to suppress
the warning, you can add a property named 'PSDscAllowDomainUser' with a value of $true to your DSC
configuration data for node 'localhost'.

Compilation errors occurred while processing configuration
'DomainCredentialExample'. Please review the errors reported in error stream and modify your
configuration code appropriately.
At C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:3917 char:5
+     throw $ErrorRecord
+     ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (DomainCredentialExample:String) [], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessConfiguration
```

Neste exemplo tem dois problemas:

1. Um erro explica de que as palavras-passe de texto simples não são recomendadas
2. Indica um aviso contra a utilização de uma credencial de domínio

Os sinalizadores **PSDSCAllowPlainTextPassword** e **PSDSCAllowDomainUser** suprimir o erro e aviso a informar o utilizador de risco envolvido.

## <a name="psdscallowplaintextpassword"></a>PSDSCAllowPlainTextPassword

A primeira mensagem de erro tem um URL com a documentação.
Esta ligação explica como encriptar as palavras-passe a utilizar um [ConfigurationData](./configData.md) estrutura e um certificado.
Para obter mais informações sobre certificados e DSC [ler esta mensagem](http://aka.ms/certs4dsc).

Para forçar uma palavra-passe de texto simples, o recurso requer o `PsDscAllowPlainTextPassword` secção de palavra-chave dos dados de configuração da seguinte forma:

```powershell
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "contoso\Administrator"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

Configuration DomainCredentialExample
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $credential
        }
    }
}

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowPlainTextPassword = $true
        }
    )
}

DomainCredentialExample -ConfigurationData $cd
```

### <a name="localhostmof"></a>localhost.mof

O **PSDSCAllowPlainTextPassword** sinalizador requer que o utilizador aceitar o risco de armazenar palavras-passe de texto simples num ficheiro MOF. No ficheiro MOF gerado, apesar de um **PSCredential** objeto que contém um **SecureString** foi utilizado, as palavras-passe de ainda aparecem como texto simples. Este é o único momento em que as credenciais são expostas. Obtenha acesso a este oferece de ficheiro MOF que qualquer pessoa aceder à conta de administrador.

```
/*
@TargetNode='localhost'
@GeneratedBy=Administrator
@GenerationDate=01/31/2019 06:43:13
@GenerationHost=Server01
*/

instance of MSFT_Credential as $MSFT_Credential1ref
{
Password = "ThisIsAPlaintextPassword";
 UserName = "Administrator";

};

instance of MSFT_GroupResource as $MSFT_GroupResource1ref
{
ResourceID = "[Group]DomainUserToLocalGroup";
 MembersToInclude = {
    "contoso\\alice"
};
 Credential = $MSFT_Credential1ref;
 SourceInfo = "::11::9::Group";
 GroupName = "ApplicationAdmins";
 ModuleName = "PSDesiredStateConfiguration";

ModuleVersion = "1.0";

 ConfigurationName = "DomainCredentialExample";

};
```

### <a name="credentials-in-transit-and-at-rest"></a>Credenciais em trânsito e inativos

- O **PSDscAllowPlainTextPassword** sinalizador permite compilar ficheiros MOF que contém as palavras-passe em texto não encriptado.
  Tome precauções ao armazenar ficheiros MOF que contém as palavras-passe de texto não encriptado.
- Quando o ficheiro MOF é entregue para um nó no **Push** modo, WinRM encripta a comunicação para proteger a palavra-passe de texto não encriptado, exceto se substituir a predefinição com o **AllowUnencrypted** parâmetro.
  - O MOF com um certificado de encriptação protege o ficheiro MOF Inativos antes de ter sido aplicado a um nó.
- No **solicitação** modo, pode configurar o servidor de solicitação do Windows para utilizar HTTPS para encriptar o tráfego utilizando o protocolo especificado na Internet Information Server. Para obter mais informações, consulte os artigos [configurar um cliente de solicitação do DSC](../pull-server/pullclient.md) e [MOF proteger os ficheiros com certificados](../pull-server/secureMOF.md).
  - No [configuração de estado de automatização do Azure](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) service, extração de tráfego é sempre encriptado.
- No nó, ficheiros MOF são encriptados em descanso à partir do PowerShell 5.0.
  - No PowerShell 4.0 MOF ficheiros estão não encriptados inativos, a menos que sejam encriptados com um certificado quando é feito o Push ou solicitados para o nó.

**Microsoft aconselha para evitar palavras-passe de texto simples devido ao risco de segurança significativo.**

## <a name="domain-credentials"></a>Credenciais do domínio

Ainda executar novamente o script de configuração de exemplo (com ou sem encriptação), gera o aviso de que a conta para uma credencial não é recomendada utilizar um domínio.
Utilizar uma conta local elimina potencial exposição de credenciais de domínio que possam ser utilizados noutros servidores.

**Ao utilizar as credenciais com recursos de DSC, preferir uma conta local através de uma conta de domínio sempre que possível.**

Se existir um '\\'ou'\@' no `Username` propriedade de credencial, DSC irá processá-lo como uma conta de domínio.
Há uma exceção para "localhost", "127.0.0.1" e ":: 1" na parte do domínio do nome de utilizador.

## <a name="psdscallowdomainuser"></a>PSDscAllowDomainUser

No DSC `Group` exemplo de recurso acima, consultar um domínio do Active Directory *requer* uma conta de domínio.
Neste caso, adicione o `PSDscAllowDomainUser` propriedade para o `ConfigurationData` bloquear da seguinte forma:

```powershell
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "contoso\Administrator"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

Configuration DomainCredentialExample
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $credential
        }
    }
}

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowDomainUser = $true
            PSDscAllowPlainTextPassword = $true
        }
    )
}

DomainCredentialExample -ConfigurationData $cd
```

Agora, o script de configuração irá gerar o ficheiro MOF com sem erros ou avisos.
