---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Utilizar a ferramenta do Designer de recursos
ms.openlocfilehash: c39b48f67d3874ee3cd2f2704aeb7390fa186fe4
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/15/2018
---
# <a name="using-the-resource-designer-tool"></a>Utilizar a ferramenta do Designer de recursos

> Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

A ferramenta do Designer de recursos é um conjunto de cmdlets expostos pelo **xDscResourceDesigner** módulo que o facilitar a configuração de estado pretendido do Windows PowerShell (DSC) criação dos recursos. Os cmdlets deste recurso ajudar a criar o esquema MOF, o módulo de script e a estrutura de diretórios para o novo recurso. Para obter mais informações sobre os recursos de DSC, consulte [criar Windows PowerShell pretendido estado configuração recursos personalizados](authoringResource.md).
Este tópico, vamos criar um recurso de DSC que gere os utilizadores do Active Directory.
Utilize o [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) cmdlet para instalar o **xDscResourceDesigner** módulo.

>**Tenha em atenção**: **Install-Module** está incluído no **PowerShellGet** módulo, que está incluído no PowerShell 5.0. Pode transferir o **PowerShellGet** módulo para o PowerShell 3.0 e 4.0 em [pré-visualização de módulos do PowerShell PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186).

## <a name="creating-resource-properties"></a>Criar propriedades de recurso
A primeira coisa que temos de fazer é decidir propriedades que irá expor o recurso. Neste exemplo, iremos definir um utilizador do Active Directory com as seguintes propriedades.
 
Nome do parâmetro descrição
* **Nome de utilizador**: a chave de propriedade que identifica exclusivamente um utilizador.
* **Certifique-se**: Especifica se a conta de utilizador deve estar presente ou estiver ausente. Este parâmetro tem apenas dois valores possíveis.
* **DomainCredential**: A palavra-passe de domínio para o utilizador.
* **Palavra-passe**: A palavra-passe pretendida para o utilizador permitir uma configuração alterar a palavra-passe do utilizador, se necessário.

Para criar as propriedades, utilizamos o **New-xDscResourceProperty** cmdlet. Os comandos PowerShell seguintes criam as propriedades descritas acima.

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet “Present”, “Absent”
$DomainCredential = New-xDscResourceProperty –Name DomainCredential-Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a>Criar o recurso

Agora que as propriedades de recurso foram criadas, podemos chamar a **New-xDscResource** cmdlet para criar o recurso. O **New-xDscResource** cmdlet demora a lista de propriedades como parâmetros. Demora também o caminho onde o módulo deve ser criado, o nome do novo recurso e o nome do módulo que está contido. O seguinte comando do PowerShell cria o recurso.

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path ‘C:\Program Files\WindowsPowerShell\Modules’ –ModuleName Demo_DSCModule
```

O **New-xDscResource** cmdlet cria o esquema MOF, um script de estrutura de recursos, a estrutura de diretórios necessários para o novo recurso e um manifesto para o módulo que expõe o novo recurso.

O ficheiro de esquema MOF é **c:\Programas\Microsoft Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, e o respetivo conteúdo é os seguintes.

```
[ClassVersion("1.0.0.0"), FriendlyName("Demo_ADUser")]
class Demo_ADUser : OMI_BaseResource
{
  [Key] string UserName;
  [Write, ValueMap{"Present","Absent"}, Values{"Present","Absent"}] string Ensure;
  [Write, EmbeddedInstance("MSFT_Credential")] String DomainCredential;
  [Write, EmbeddedInstance("MSFT_Credential")] String Password;
};
```

O script de recurso é **c:\Programas\Microsoft Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**. Não inclui a lógica real para implementar o recurso, o que tem de adicionar manualmente. O conteúdo do script esqueleto é os seguintes.

```powershell
function Get-TargetResource
{
  [CmdletBinding()]
  [OutputType([System.Collections.Hashtable])]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."


  <#
  $returnValue = @{
  UserName = [System.String]
  Ensure = [System.String]
  DomainAdminCredential = [System.Management.Automation.PSCredential]
  Password = [System.Management.Automation.PSCredential]
  }

  $returnValue
  #>
}


function Set-TargetResource
{
  [CmdletBinding()]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName,

    [ValidateSet("Present","Absent")]
    [System.String]
    $Ensure,

    [System.Management.Automation.PSCredential]
    $DomainAdminCredential,

    [System.Management.Automation.PSCredential]
    $Password
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."

  #Include this line if the resource requires a system reboot.
  #$global:DSCMachineStatus = 1


}


function Test-TargetResource
{
  [CmdletBinding()]
  [OutputType([System.Boolean])]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName,

    [ValidateSet("Present","Absent")]
    [System.String]
    $Ensure,

    [System.Management.Automation.PSCredential]
    $DomainAdminCredential,

    [System.Management.Automation.PSCredential]
    $Password
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."


  <#
  $result = [System.Boolean]

  $result
  #>
}


Export-ModuleMember -Function *-TargetResource
```

## <a name="updating-the-resource"></a>Atualizar o recurso

Se precisar de adicionar ou modificar a lista de parâmetros do recurso, pode chamar o **atualização xDscResource** cmdlet. O cmdlet atualiza o recurso com uma nova lista de parâmetros. Se já tiver adicionado lógica no seu script de recurso,-intacto.

Por exemplo, suponha que pretende incluir o último registo em tempo para o utilizador no nosso recurso. Em vez de escrever novamente completamente o recurso, pode chamar o **New-xDscResourceProperty** para criar a nova propriedade e, em seguida, chame **atualização xDscResource** e adicionar a nova propriedade para o lista de propriedades.

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description “For mapping users to their last log on time”
Update-xDscResource –Name ‘Demo_ADUser’ –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a>Um esquema de recurso de teste

A ferramenta de recurso Designer expõe um cmdlet mais que pode ser utilizada para testar a validade de um esquema MOF ter escrito manualmente. Chamar o **teste xDscSchema** cmdlet, transmitir o caminho de um esquema de recurso MOF como parâmetro. O cmdlet irá emitir quaisquer erros no esquema.

### <a name="see-also"></a>Consulte Também

#### <a name="concepts"></a>Conceitos
[Criar recursos de configuração do estado pretendido do PowerShell de personalizada do Windows](authoringResource.md)

#### <a name="other-resources"></a>Outros Recursos
[xDscResourceDesigner Module](https://powershellgallery.com/packages/xDscResourceDesigner)