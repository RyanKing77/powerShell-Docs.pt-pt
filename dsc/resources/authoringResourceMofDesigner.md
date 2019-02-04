---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Usando a ferramenta de Designer de recursos
ms.openlocfilehash: 3fd2f06cf46602ee30dd34f8e7bd77d3c92b808f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686657"
---
# <a name="using-the-resource-designer-tool"></a><span data-ttu-id="d167f-103">Usando a ferramenta de Designer de recursos</span><span class="sxs-lookup"><span data-stu-id="d167f-103">Using the Resource Designer tool</span></span>

> <span data-ttu-id="d167f-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d167f-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="d167f-105">A ferramenta de Designer de recursos é um conjunto de cmdlets expostos pelos **xDscResourceDesigner** módulo que facilitam a criar recursos do Windows PowerShell Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="d167f-105">The Resource Designer tool is a set of cmdlets exposed by the **xDscResourceDesigner** module that make creating Windows PowerShell Desired State Configuration (DSC) resources easier.</span></span> <span data-ttu-id="d167f-106">Os cmdlets neste recurso ajudam a criar o esquema do MOF, o módulo de script e a estrutura de diretórios para o seu novo recurso.</span><span class="sxs-lookup"><span data-stu-id="d167f-106">The cmdlets in this resource help create the MOF schema, the script module, and the directory structure for your new resource.</span></span> <span data-ttu-id="d167f-107">Para obter mais informações sobre os recursos de DSC, veja [criar Windows PowerShell Desired State Configuration recursos personalizados](authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="d167f-107">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md).</span></span>
<span data-ttu-id="d167f-108">Neste tópico, iremos criar um recurso de DSC que gere os utilizadores do Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d167f-108">In this topic, we will create a DSC resource that manages Active Directory users.</span></span>
<span data-ttu-id="d167f-109">Utilize o [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet para instalar o **xDscResourceDesigner** módulo.</span><span class="sxs-lookup"><span data-stu-id="d167f-109">Use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xDscResourceDesigner** module.</span></span>

><span data-ttu-id="d167f-110">**Tenha em atenção**: **Install-Module** está incluído nos **PowerShellGet** módulo, que está incluído no PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="d167f-110">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="d167f-111">Pode baixar o **PowerShellGet** módulo para o PowerShell 3.0 e 4.0 na [pré-visualização de módulos do PowerShell PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="d167f-111">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>

## <a name="creating-resource-properties"></a><span data-ttu-id="d167f-112">Criar propriedades de recurso</span><span class="sxs-lookup"><span data-stu-id="d167f-112">Creating resource properties</span></span>
<span data-ttu-id="d167f-113">A primeira coisa que precisamos fazer é decidir qual a propriedades que o recurso irá expor.</span><span class="sxs-lookup"><span data-stu-id="d167f-113">The first thing we need to do is decide on properties that the resource will expose.</span></span> <span data-ttu-id="d167f-114">Neste exemplo, iremos definir um utilizador do Active Directory com as seguintes propriedades.</span><span class="sxs-lookup"><span data-stu-id="d167f-114">For this example, we will define an Active Directory user with the following properties.</span></span>

<span data-ttu-id="d167f-115">Nome do parâmetro de descrição</span><span class="sxs-lookup"><span data-stu-id="d167f-115">Parameter name  Description</span></span>
* <span data-ttu-id="d167f-116">**UserName**: Propriedade de chave que identifica exclusivamente um utilizador.</span><span class="sxs-lookup"><span data-stu-id="d167f-116">**UserName**: Key property that uniquely identifies a user.</span></span>
* <span data-ttu-id="d167f-117">**Certifique-se de**: Especifica se a conta de utilizador deve estar presente ou ausência.</span><span class="sxs-lookup"><span data-stu-id="d167f-117">**Ensure**: Specifies whether the user account should be Present or Absent.</span></span> <span data-ttu-id="d167f-118">Este parâmetro tem apenas dois valores possíveis.</span><span class="sxs-lookup"><span data-stu-id="d167f-118">This parameter will have only two possible values.</span></span>
* <span data-ttu-id="d167f-119">**DomainCredential**: A palavra-passe do domínio para o utilizador.</span><span class="sxs-lookup"><span data-stu-id="d167f-119">**DomainCredential**: The domain password for the user.</span></span>
* <span data-ttu-id="d167f-120">**Palavra-passe**: A palavra-passe pretendida para o utilizador permitir que uma configuração alterar a palavra-passe do utilizador, se necessário.</span><span class="sxs-lookup"><span data-stu-id="d167f-120">**Password**: The desired password for the user to allow a configuration to change the user password if necessary.</span></span>

<span data-ttu-id="d167f-121">Para criar as propriedades, usamos o **New-xDscResourceProperty** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d167f-121">To create the properties, we use the **New-xDscResourceProperty** cmdlet.</span></span> <span data-ttu-id="d167f-122">Os comandos PowerShell seguintes criam as propriedades descritas acima.</span><span class="sxs-lookup"><span data-stu-id="d167f-122">The following PowerShell commands create the properties described above.</span></span>

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet “Present”, “Absent”
$DomainCredential = New-xDscResourceProperty –Name DomainCredential -Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a><span data-ttu-id="d167f-123">Criar o recurso</span><span class="sxs-lookup"><span data-stu-id="d167f-123">Create the resource</span></span>

<span data-ttu-id="d167f-124">Agora que as propriedades de recurso foram criadas, podemos chamar o **New-xDscResource** cmdlet para criar o recurso.</span><span class="sxs-lookup"><span data-stu-id="d167f-124">Now that the resource properties have been created, we can call the **New-xDscResource** cmdlet to create the resource.</span></span> <span data-ttu-id="d167f-125">O **New-xDscResource** cmdlet utiliza a lista de propriedades como parâmetros.</span><span class="sxs-lookup"><span data-stu-id="d167f-125">The **New-xDscResource** cmdlet takes the list of properties as parameters.</span></span> <span data-ttu-id="d167f-126">Ela também leva o caminho onde o módulo deve ser criado, o nome do novo recurso e o nome do módulo no qual está contido.</span><span class="sxs-lookup"><span data-stu-id="d167f-126">It also takes the path where the module should be created, the name of the new resource, and the name of the module in which it is contained.</span></span> <span data-ttu-id="d167f-127">O seguinte comando do PowerShell cria o recurso.</span><span class="sxs-lookup"><span data-stu-id="d167f-127">The following PowerShell command creates the resource.</span></span>

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path ‘C:\Program Files\WindowsPowerShell\Modules’ –ModuleName Demo_DSCModule
```

<span data-ttu-id="d167f-128">O **New-xDscResource** cmdlet cria o esquema do MOF, um script de estrutura de recursos, a estrutura de diretório necessárias para o seu novo recurso e um manifesto para o módulo que expõe o novo recurso.</span><span class="sxs-lookup"><span data-stu-id="d167f-128">The **New-xDscResource** cmdlet creates the MOF schema, a skeleton resource script, the required directory structure for your new resource, and a manifest for the module that exposes the new resource.</span></span>

<span data-ttu-id="d167f-129">O ficheiro de esquema do MOF tenha **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, e seu conteúdo é os seguintes.</span><span class="sxs-lookup"><span data-stu-id="d167f-129">The MOF schema file is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, and its contents are as follows.</span></span>

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

<span data-ttu-id="d167f-130">O script de recurso tenha **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**.</span><span class="sxs-lookup"><span data-stu-id="d167f-130">The resource script is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**.</span></span> <span data-ttu-id="d167f-131">Não inclui a lógica real para implementar o recurso, que tem de adicionar por conta própria.</span><span class="sxs-lookup"><span data-stu-id="d167f-131">It does not include the actual logic to implement the resource, which you must add yourself.</span></span> <span data-ttu-id="d167f-132">Seguem-se o conteúdo do script estrutural.</span><span class="sxs-lookup"><span data-stu-id="d167f-132">The contents of the skeleton script are as follows.</span></span>

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

## <a name="updating-the-resource"></a><span data-ttu-id="d167f-133">Atualizar o recurso</span><span class="sxs-lookup"><span data-stu-id="d167f-133">Updating the resource</span></span>

<span data-ttu-id="d167f-134">Se precisar de adicionar ou modificar a lista de parâmetros do recurso, pode chamar o **xDscResource atualização** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d167f-134">If you need to add or modify the parameter list of the resource, you can call the **Update-xDscResource** cmdlet.</span></span> <span data-ttu-id="d167f-135">O cmdlet atualiza o recurso com uma nova lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="d167f-135">The cmdlet updates the resource with a new parameter list.</span></span> <span data-ttu-id="d167f-136">Se já tiver adicionado lógica no seu script de recurso, ele intacto.</span><span class="sxs-lookup"><span data-stu-id="d167f-136">If you have already added logic in your resource script, it is left intact.</span></span>

<span data-ttu-id="d167f-137">Por exemplo, suponha que deseja incluir o último registo para o utilizador no nosso recurso no tempo.</span><span class="sxs-lookup"><span data-stu-id="d167f-137">For example, suppose you want to include the last log in time for the user in our resource.</span></span> <span data-ttu-id="d167f-138">Em vez de escrever novamente completamente o recurso, pode chamar o **New-xDscResourceProperty** para criar a nova propriedade e, em seguida, chamar **atualização xDscResource** e adicionar a nova propriedade para o lista de propriedades.</span><span class="sxs-lookup"><span data-stu-id="d167f-138">Rather than writing the resource again completely, you can call the **New-xDscResourceProperty** to create the new property, and then call **Update-xDscResource** and add your new property to the properties list.</span></span>

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description “For mapping users to their last log on time”
Update-xDscResource –Name ‘Demo_ADUser’ –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a><span data-ttu-id="d167f-139">Um esquema de recursos de teste</span><span class="sxs-lookup"><span data-stu-id="d167f-139">Testing a resource schema</span></span>

<span data-ttu-id="d167f-140">A ferramenta de Designer de recursos expõe um cmdlet mais que pode ser utilizado para testar a validade de um esquema MOF que escreveu manualmente.</span><span class="sxs-lookup"><span data-stu-id="d167f-140">The Resource Designer tool exposes one more cmdlet that can be used to test the validity of a MOF schema that you have written manually.</span></span> <span data-ttu-id="d167f-141">Chamar o **teste xDscSchema** cmdlet, passando o caminho de um esquema de recursos do MOF como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d167f-141">Call the **Test-xDscSchema** cmdlet, passing the path of a MOF resource schema as a parameter.</span></span> <span data-ttu-id="d167f-142">O cmdlet irá saída quaisquer erros no esquema.</span><span class="sxs-lookup"><span data-stu-id="d167f-142">The cmdlet will output any errors in the schema.</span></span>

### <a name="see-also"></a><span data-ttu-id="d167f-143">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="d167f-143">See Also</span></span>

#### <a name="concepts"></a><span data-ttu-id="d167f-144">Conceitos</span><span class="sxs-lookup"><span data-stu-id="d167f-144">Concepts</span></span>
[<span data-ttu-id="d167f-145">Criar recursos do Windows personalizados do PowerShell Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="d167f-145">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)

#### <a name="other-resources"></a><span data-ttu-id="d167f-146">Outros Recursos</span><span class="sxs-lookup"><span data-stu-id="d167f-146">Other Resources</span></span>
[<span data-ttu-id="d167f-147">xDscResourceDesigner módulo</span><span class="sxs-lookup"><span data-stu-id="d167f-147">xDscResourceDesigner Module</span></span>](https://www.powershellgallery.com/packages/xDscResourceDesigner/1.12.0.0)
