---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Usando a ferramenta de Designer de recursos
ms.openlocfilehash: 3fd2f06cf46602ee30dd34f8e7bd77d3c92b808f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404941"
---
# <a name="using-the-resource-designer-tool"></a>Usando a ferramenta de Designer de recursos

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

A ferramenta de Designer de recursos é um conjunto de cmdlets expostos pelos **xDscResourceDesigner** módulo que facilitam a criar recursos do Windows PowerShell Desired State Configuration (DSC). Os cmdlets neste recurso ajudam a criar o esquema do MOF, o módulo de script e a estrutura de diretórios para o seu novo recurso. Para obter mais informações sobre os recursos de DSC, veja [criar Windows PowerShell Desired State Configuration recursos personalizados](authoringResource.md).
Neste tópico, iremos criar um recurso de DSC que gere os utilizadores do Active Directory.
Utilize o [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet para instalar o **xDscResourceDesigner** módulo.

>**Tenha em atenção**: **Install-Module** está incluído nos **PowerShellGet** módulo, que está incluído no PowerShell 5.0. Pode baixar o **PowerShellGet** módulo para o PowerShell 3.0 e 4.0 na [pré-visualização de módulos do PowerShell PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186).

## <a name="creating-resource-properties"></a>Criar propriedades de recurso
A primeira coisa que precisamos fazer é decidir qual a propriedades que o recurso irá expor. Neste exemplo, iremos definir um utilizador do Active Directory com as seguintes propriedades.

Nome do parâmetro de descrição
* **Nome de utilizador**: Propriedade de chave que identifica exclusivamente um utilizador.
* **Certifique-se de**: Especifica se a conta de utilizador deve estar presente ou ausência. Este parâmetro tem apenas dois valores possíveis.
* **DomainCredential**: A palavra-passe do domínio para o utilizador.
* **Palavra-passe**: A palavra-passe pretendida para o utilizador permitir que uma configuração alterar a palavra-passe do utilizador, se necessário.

Para criar as propriedades, usamos o **New-xDscResourceProperty** cmdlet. Os comandos PowerShell seguintes criam as propriedades descritas acima.

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet “Present”, “Absent”
$DomainCredential = New-xDscResourceProperty –Name DomainCredential -Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a>Criar o recurso

Agora que as propriedades de recurso foram criadas, podemos chamar o **New-xDscResource** cmdlet para criar o recurso. O **New-xDscResource** cmdlet utiliza a lista de propriedades como parâmetros. Ela também leva o caminho onde o módulo deve ser criado, o nome do novo recurso e o nome do módulo no qual está contido. O seguinte comando do PowerShell cria o recurso.

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path ‘C:\Program Files\WindowsPowerShell\Modules’ –ModuleName Demo_DSCModule
```

O **New-xDscResource** cmdlet cria o esquema do MOF, um script de estrutura de recursos, a estrutura de diretório necessárias para o seu novo recurso e um manifesto para o módulo que expõe o novo recurso.

O ficheiro de esquema do MOF tenha **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, e seu conteúdo é os seguintes.

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

O script de recurso tenha **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**. Não inclui a lógica real para implementar o recurso, que tem de adicionar por conta própria. Seguem-se o conteúdo do script estrutural.

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

Se precisar de adicionar ou modificar a lista de parâmetros do recurso, pode chamar o **xDscResource atualização** cmdlet. O cmdlet atualiza o recurso com uma nova lista de parâmetros. Se já tiver adicionado lógica no seu script de recurso, ele intacto.

Por exemplo, suponha que deseja incluir o último registo para o utilizador no nosso recurso no tempo. Em vez de escrever novamente completamente o recurso, pode chamar o **New-xDscResourceProperty** para criar a nova propriedade e, em seguida, chamar **atualização xDscResource** e adicionar a nova propriedade para o lista de propriedades.

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description “For mapping users to their last log on time”
Update-xDscResource –Name ‘Demo_ADUser’ –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a>Um esquema de recursos de teste

A ferramenta de Designer de recursos expõe um cmdlet mais que pode ser utilizado para testar a validade de um esquema MOF que escreveu manualmente. Chamar o **teste xDscSchema** cmdlet, passando o caminho de um esquema de recursos do MOF como um parâmetro. O cmdlet irá saída quaisquer erros no esquema.

### <a name="see-also"></a>Consulte Também

#### <a name="concepts"></a>Conceitos
[Criar recursos do Windows personalizados do PowerShell Desired State Configuration](authoringResource.md)

#### <a name="other-resources"></a>Outros Recursos
[xDscResourceDesigner módulo](https://www.powershellgallery.com/packages/xDscResourceDesigner/1.12.0.0)
