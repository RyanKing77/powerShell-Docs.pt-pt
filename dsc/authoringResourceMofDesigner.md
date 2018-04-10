---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Utilizar a ferramenta do Designer de recursos
ms.openlocfilehash: e0282671861755a5f147de4d07783a4680024ec5
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="using-the-resource-designer-tool"></a><span data-ttu-id="e4067-103">Utilizar a ferramenta do Designer de recursos</span><span class="sxs-lookup"><span data-stu-id="e4067-103">Using the Resource Designer tool</span></span>

> <span data-ttu-id="e4067-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e4067-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="e4067-105">A ferramenta do Designer de recursos é um conjunto de cmdlets expostos pelo **xDscResourceDesigner** módulo que o facilitar a configuração de estado pretendido do Windows PowerShell (DSC) criação dos recursos.</span><span class="sxs-lookup"><span data-stu-id="e4067-105">The Resource Designer tool is a set of cmdlets exposed by the **xDscResourceDesigner** module that make creating Windows PowerShell Desired State Configuration (DSC) resources easier.</span></span> <span data-ttu-id="e4067-106">Os cmdlets deste recurso ajudar a criar o esquema MOF, o módulo de script e a estrutura de diretórios para o novo recurso.</span><span class="sxs-lookup"><span data-stu-id="e4067-106">The cmdlets in this resource help create the MOF schema, the script module, and the directory structure for your new resource.</span></span> <span data-ttu-id="e4067-107">Para obter mais informações sobre os recursos de DSC, consulte [criar Windows PowerShell pretendido estado configuração recursos personalizados](authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="e4067-107">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md).</span></span>
<span data-ttu-id="e4067-108">Este tópico, vamos criar um recurso de DSC que gere os utilizadores do Active Directory.</span><span class="sxs-lookup"><span data-stu-id="e4067-108">In this topic, we will create a DSC resource that manages Active Directory users.</span></span>
<span data-ttu-id="e4067-109">Utilize o [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) cmdlet para instalar o **xDscResourceDesigner** módulo.</span><span class="sxs-lookup"><span data-stu-id="e4067-109">Use the [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) cmdlet to install the **xDscResourceDesigner** module.</span></span>

><span data-ttu-id="e4067-110">**Tenha em atenção**: **Install-Module** está incluído no **PowerShellGet** módulo, que está incluído no PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="e4067-110">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="e4067-111">Pode transferir o **PowerShellGet** módulo para o PowerShell 3.0 e 4.0 em [pré-visualização de módulos do PowerShell PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="e4067-111">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>

## <a name="creating-resource-properties"></a><span data-ttu-id="e4067-112">Criar propriedades de recurso</span><span class="sxs-lookup"><span data-stu-id="e4067-112">Creating resource properties</span></span>
<span data-ttu-id="e4067-113">A primeira coisa que temos de fazer é decidir propriedades que irá expor o recurso.</span><span class="sxs-lookup"><span data-stu-id="e4067-113">The first thing we need to do is decide on properties that the resource will expose.</span></span> <span data-ttu-id="e4067-114">Neste exemplo, iremos definir um utilizador do Active Directory com as seguintes propriedades.</span><span class="sxs-lookup"><span data-stu-id="e4067-114">For this example, we will define an Active Directory user with the following properties.</span></span>

<span data-ttu-id="e4067-115">Nome do parâmetro descrição</span><span class="sxs-lookup"><span data-stu-id="e4067-115">Parameter name  Description</span></span>
* <span data-ttu-id="e4067-116">**Nome de utilizador**: a chave de propriedade que identifica exclusivamente um utilizador.</span><span class="sxs-lookup"><span data-stu-id="e4067-116">**UserName**: Key property that uniquely identifies a user.</span></span>
* <span data-ttu-id="e4067-117">**Certifique-se**: Especifica se a conta de utilizador deve estar presente ou estiver ausente.</span><span class="sxs-lookup"><span data-stu-id="e4067-117">**Ensure**: Specifies whether the user account should be Present or Absent.</span></span> <span data-ttu-id="e4067-118">Este parâmetro tem apenas dois valores possíveis.</span><span class="sxs-lookup"><span data-stu-id="e4067-118">This parameter will have only two possible values.</span></span>
* <span data-ttu-id="e4067-119">**DomainCredential**: A palavra-passe de domínio para o utilizador.</span><span class="sxs-lookup"><span data-stu-id="e4067-119">**DomainCredential**: The domain password for the user.</span></span>
* <span data-ttu-id="e4067-120">**Palavra-passe**: A palavra-passe pretendida para o utilizador permitir uma configuração alterar a palavra-passe do utilizador, se necessário.</span><span class="sxs-lookup"><span data-stu-id="e4067-120">**Password**: The desired password for the user to allow a configuration to change the user password if necessary.</span></span>

<span data-ttu-id="e4067-121">Para criar as propriedades, utilizamos o **New-xDscResourceProperty** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e4067-121">To create the properties, we use the **New-xDscResourceProperty** cmdlet.</span></span> <span data-ttu-id="e4067-122">Os comandos PowerShell seguintes criam as propriedades descritas acima.</span><span class="sxs-lookup"><span data-stu-id="e4067-122">The following PowerShell commands create the properties described above.</span></span>

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet “Present”, “Absent”
$DomainCredential = New-xDscResourceProperty –Name DomainCredential -Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a><span data-ttu-id="e4067-123">Criar o recurso</span><span class="sxs-lookup"><span data-stu-id="e4067-123">Create the resource</span></span>

<span data-ttu-id="e4067-124">Agora que as propriedades de recurso foram criadas, podemos chamar a **New-xDscResource** cmdlet para criar o recurso.</span><span class="sxs-lookup"><span data-stu-id="e4067-124">Now that the resource properties have been created, we can call the **New-xDscResource** cmdlet to create the resource.</span></span> <span data-ttu-id="e4067-125">O **New-xDscResource** cmdlet demora a lista de propriedades como parâmetros.</span><span class="sxs-lookup"><span data-stu-id="e4067-125">The **New-xDscResource** cmdlet takes the list of properties as parameters.</span></span> <span data-ttu-id="e4067-126">Demora também o caminho onde o módulo deve ser criado, o nome do novo recurso e o nome do módulo que está contido.</span><span class="sxs-lookup"><span data-stu-id="e4067-126">It also takes the path where the module should be created, the name of the new resource, and the name of the module in which it is contained.</span></span> <span data-ttu-id="e4067-127">O seguinte comando do PowerShell cria o recurso.</span><span class="sxs-lookup"><span data-stu-id="e4067-127">The following PowerShell command creates the resource.</span></span>

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path ‘C:\Program Files\WindowsPowerShell\Modules’ –ModuleName Demo_DSCModule
```

<span data-ttu-id="e4067-128">O **New-xDscResource** cmdlet cria o esquema MOF, um script de estrutura de recursos, a estrutura de diretórios necessários para o novo recurso e um manifesto para o módulo que expõe o novo recurso.</span><span class="sxs-lookup"><span data-stu-id="e4067-128">The **New-xDscResource** cmdlet creates the MOF schema, a skeleton resource script, the required directory structure for your new resource, and a manifest for the module that exposes the new resource.</span></span>

<span data-ttu-id="e4067-129">O ficheiro de esquema MOF é **c:\Programas\Microsoft Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, e o respetivo conteúdo é os seguintes.</span><span class="sxs-lookup"><span data-stu-id="e4067-129">The MOF schema file is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, and its contents are as follows.</span></span>

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

<span data-ttu-id="e4067-130">O script de recurso é **c:\Programas\Microsoft Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**.</span><span class="sxs-lookup"><span data-stu-id="e4067-130">The resource script is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**.</span></span> <span data-ttu-id="e4067-131">Não inclui a lógica real para implementar o recurso, o que tem de adicionar manualmente.</span><span class="sxs-lookup"><span data-stu-id="e4067-131">It does not include the actual logic to implement the resource, which you must add yourself.</span></span> <span data-ttu-id="e4067-132">O conteúdo do script esqueleto é os seguintes.</span><span class="sxs-lookup"><span data-stu-id="e4067-132">The contents of the skeleton script are as follows.</span></span>

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

## <a name="updating-the-resource"></a><span data-ttu-id="e4067-133">Atualizar o recurso</span><span class="sxs-lookup"><span data-stu-id="e4067-133">Updating the resource</span></span>

<span data-ttu-id="e4067-134">Se precisar de adicionar ou modificar a lista de parâmetros do recurso, pode chamar o **atualização xDscResource** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e4067-134">If you need to add or modify the parameter list of the resource, you can call the **Update-xDscResource** cmdlet.</span></span> <span data-ttu-id="e4067-135">O cmdlet atualiza o recurso com uma nova lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="e4067-135">The cmdlet updates the resource with a new parameter list.</span></span> <span data-ttu-id="e4067-136">Se já tiver adicionado lógica no seu script de recurso,-intacto.</span><span class="sxs-lookup"><span data-stu-id="e4067-136">If you have already added logic in your resource script, it is left intact.</span></span>

<span data-ttu-id="e4067-137">Por exemplo, suponha que pretende incluir o último registo em tempo para o utilizador no nosso recurso.</span><span class="sxs-lookup"><span data-stu-id="e4067-137">For example, suppose you want to include the last log in time for the user in our resource.</span></span> <span data-ttu-id="e4067-138">Em vez de escrever novamente completamente o recurso, pode chamar o **New-xDscResourceProperty** para criar a nova propriedade e, em seguida, chame **atualização xDscResource** e adicionar a nova propriedade para o lista de propriedades.</span><span class="sxs-lookup"><span data-stu-id="e4067-138">Rather than writing the resource again completely, you can call the **New-xDscResourceProperty** to create the new property, and then call **Update-xDscResource** and add your new property to the properties list.</span></span>

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description “For mapping users to their last log on time”
Update-xDscResource –Name ‘Demo_ADUser’ –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a><span data-ttu-id="e4067-139">Um esquema de recurso de teste</span><span class="sxs-lookup"><span data-stu-id="e4067-139">Testing a resource schema</span></span>

<span data-ttu-id="e4067-140">A ferramenta de recurso Designer expõe um cmdlet mais que pode ser utilizada para testar a validade de um esquema MOF ter escrito manualmente.</span><span class="sxs-lookup"><span data-stu-id="e4067-140">The Resource Designer tool exposes one more cmdlet that can be used to test the validity of a MOF schema that you have written manually.</span></span> <span data-ttu-id="e4067-141">Chamar o **teste xDscSchema** cmdlet, transmitir o caminho de um esquema de recurso MOF como parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e4067-141">Call the **Test-xDscSchema** cmdlet, passing the path of a MOF resource schema as a parameter.</span></span> <span data-ttu-id="e4067-142">O cmdlet irá emitir quaisquer erros no esquema.</span><span class="sxs-lookup"><span data-stu-id="e4067-142">The cmdlet will output any errors in the schema.</span></span>

### <a name="see-also"></a><span data-ttu-id="e4067-143">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="e4067-143">See Also</span></span>

#### <a name="concepts"></a><span data-ttu-id="e4067-144">Conceitos</span><span class="sxs-lookup"><span data-stu-id="e4067-144">Concepts</span></span>
[<span data-ttu-id="e4067-145">Criar recursos de configuração do estado pretendido do PowerShell de personalizada do Windows</span><span class="sxs-lookup"><span data-stu-id="e4067-145">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)

#### <a name="other-resources"></a><span data-ttu-id="e4067-146">Outros Recursos</span><span class="sxs-lookup"><span data-stu-id="e4067-146">Other Resources</span></span>
[<span data-ttu-id="e4067-147">xDscResourceDesigner Module</span><span class="sxs-lookup"><span data-stu-id="e4067-147">xDscResourceDesigner Module</span></span>](https://powershellgallery.com/packages/xDscResourceDesigner)