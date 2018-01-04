---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Recurso de Script de DSC
ms.openlocfilehash: d3e231d33a04fd8a018ffe2f3d51a15360e0d312
ms.sourcegitcommit: 60f06a06c2fce63024f3f4cbd7657b1dfe7fcb1a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/03/2018
---
# <a name="dsc-script-resource"></a><span data-ttu-id="03aed-103">Recurso de Script de DSC</span><span class="sxs-lookup"><span data-stu-id="03aed-103">DSC Script Resource</span></span>

 
> <span data-ttu-id="03aed-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="03aed-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="03aed-105">O **Script** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para executar os blocos de script do Windows PowerShell em nós de destino.</span><span class="sxs-lookup"><span data-stu-id="03aed-105">The **Script** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="03aed-106">O `Script` recurso tem `GetScript`, `SetScript`, e `TestScript` propriedades.</span><span class="sxs-lookup"><span data-stu-id="03aed-106">The `Script` resource has `GetScript`, `SetScript`, and `TestScript` properties.</span></span> <span data-ttu-id="03aed-107">Estas propriedades devem ser definidas para blocos de script que serão executada em cada nó de destino.</span><span class="sxs-lookup"><span data-stu-id="03aed-107">These properties should be set to script blocks that will run on each target node.</span></span> 

<span data-ttu-id="03aed-108">O `GetScript` bloco de script deve devolver uma tabela hash que representa o estado do nó atual.</span><span class="sxs-lookup"><span data-stu-id="03aed-108">The `GetScript` script block should return a hashtable representing the state of the current node.</span></span> <span data-ttu-id="03aed-109">A tabela hash só pode conter uma chave `Result` e o valor tem de ser do tipo `String`.</span><span class="sxs-lookup"><span data-stu-id="03aed-109">The hashtable must only contain one key `Result` and the value must be of type `String`.</span></span> <span data-ttu-id="03aed-110">Não é necessário para devolver nada.</span><span class="sxs-lookup"><span data-stu-id="03aed-110">It is not required to return anything.</span></span> <span data-ttu-id="03aed-111">DSC não faz nada com o resultado deste bloco de script.</span><span class="sxs-lookup"><span data-stu-id="03aed-111">DSC doesn't do anything with the output of this script block.</span></span>

<span data-ttu-id="03aed-112">O `TestScript` bloco de script deve determinar se o nó atual tem de ser modificado.</span><span class="sxs-lookup"><span data-stu-id="03aed-112">The `TestScript` script block should determine if the current node needs to be modified.</span></span> <span data-ttu-id="03aed-113">Deverá devolver `$true` se o nó é atualizado.</span><span class="sxs-lookup"><span data-stu-id="03aed-113">It should return `$true` if the node is up-to-date.</span></span> <span data-ttu-id="03aed-114">Deverá devolver `$false` se a configuração do nó está desatualizada e devem ser atualizada pelo `SetScript` bloco de script.</span><span class="sxs-lookup"><span data-stu-id="03aed-114">It should return `$false` if the node's configuration is out-of-date and should be updated by the `SetScript` script block.</span></span> <span data-ttu-id="03aed-115">O `TestScript` bloco de script é chamado pelo DSC.</span><span class="sxs-lookup"><span data-stu-id="03aed-115">The `TestScript` script block is called by DSC.</span></span>

<span data-ttu-id="03aed-116">O `SetScript` bloco de script deve modificar o nó.</span><span class="sxs-lookup"><span data-stu-id="03aed-116">The `SetScript` script block should modify the node.</span></span> <span data-ttu-id="03aed-117">É denominado pelo DSC se o `TestScript` bloquear retorno `$false`.</span><span class="sxs-lookup"><span data-stu-id="03aed-117">It is called by DSC if the `TestScript` block return `$false`.</span></span>

<span data-ttu-id="03aed-118">Se tiver de utilizar variáveis do seu script de configuração no `GetScript`, `TestScript`, ou `SetScript` blocos de script, utilize o `$using:` âmbito (consulte abaixo para obter um exemplo).</span><span class="sxs-lookup"><span data-stu-id="03aed-118">If you need to use variables from your configuration script in the `GetScript`, `TestScript`, or `SetScript` script blocks, use the `$using:` scope (see below for an example).</span></span>


## <a name="syntax"></a><span data-ttu-id="03aed-119">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="03aed-119">Syntax</span></span>

```
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="03aed-120">Propriedades</span><span class="sxs-lookup"><span data-stu-id="03aed-120">Properties</span></span>

|  <span data-ttu-id="03aed-121">Propriedade</span><span class="sxs-lookup"><span data-stu-id="03aed-121">Property</span></span>  |  <span data-ttu-id="03aed-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="03aed-122">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="03aed-123">GetScript</span><span class="sxs-lookup"><span data-stu-id="03aed-123">GetScript</span></span>| <span data-ttu-id="03aed-124">Fornece um bloco de script do Windows PowerShell que é executado quando invocar o [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="03aed-124">Provides a block of Windows PowerShell script that runs when you invoke the [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx) cmdlet.</span></span> <span data-ttu-id="03aed-125">Este bloco tem de devolver uma tabela hash.</span><span class="sxs-lookup"><span data-stu-id="03aed-125">This block must return a hashtable.</span></span> <span data-ttu-id="03aed-126">A tabela hash só pode conter uma chave **resultado** e o valor tem de ser do tipo **cadeia**.</span><span class="sxs-lookup"><span data-stu-id="03aed-126">The hashtable must only contain one key **Result** and the value must be of type **String**.</span></span>| 
| <span data-ttu-id="03aed-127">SetScript</span><span class="sxs-lookup"><span data-stu-id="03aed-127">SetScript</span></span>| <span data-ttu-id="03aed-128">Fornece um bloco de script do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="03aed-128">Provides a block of Windows PowerShell script.</span></span> <span data-ttu-id="03aed-129">Quando invocar o [início DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, a **TestScript** bloco executa primeiro.</span><span class="sxs-lookup"><span data-stu-id="03aed-129">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, the **TestScript** block runs first.</span></span> <span data-ttu-id="03aed-130">Se o **TestScript** bloquear devolve **$false**, a **SetScript** bloco será executado.</span><span class="sxs-lookup"><span data-stu-id="03aed-130">If the **TestScript** block returns **$false**, the **SetScript** block will run.</span></span> <span data-ttu-id="03aed-131">Se o **TestScript** bloquear devolve **$true**, a **SetScript** blocos não serão executado.</span><span class="sxs-lookup"><span data-stu-id="03aed-131">If the **TestScript** block returns **$true**, the **SetScript** block will not run.</span></span>| 
| <span data-ttu-id="03aed-132">TestScript</span><span class="sxs-lookup"><span data-stu-id="03aed-132">TestScript</span></span>| <span data-ttu-id="03aed-133">Fornece um bloco de script do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="03aed-133">Provides a block of Windows PowerShell script.</span></span> <span data-ttu-id="03aed-134">Quando invocar o [início DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) executa o cmdlet, este bloco.</span><span class="sxs-lookup"><span data-stu-id="03aed-134">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, this block runs.</span></span> <span data-ttu-id="03aed-135">Se devolver **$false**, o bloco de SetScript será executado.</span><span class="sxs-lookup"><span data-stu-id="03aed-135">If it returns **$false**, the SetScript block will run.</span></span> <span data-ttu-id="03aed-136">Se devolver **$true**, SetScript bloco serão não executado.</span><span class="sxs-lookup"><span data-stu-id="03aed-136">If it returns **$true**, the SetScript block will not run.</span></span> <span data-ttu-id="03aed-137">O **TestScript** bloco também é executada quando invocar o [teste DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="03aed-137">The **TestScript** block also runs when you invoke the [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span></span> <span data-ttu-id="03aed-138">No entanto, neste caso, o **SetScript** blocos não serão executados, independentemente do valor que o TestScript bloquear devolve.</span><span class="sxs-lookup"><span data-stu-id="03aed-138">However, in this case, the **SetScript** block will not run, no matter what value the TestScript block returns.</span></span> <span data-ttu-id="03aed-139">O **TestScript** bloco tem de devolver VERDADEIRO se a configuração real corresponder a configuração atual do estado pretendido e False se não corresponde.</span><span class="sxs-lookup"><span data-stu-id="03aed-139">The **TestScript** block must return True if the actual configuration matches the current desired state configuration, and False if it does not match.</span></span> <span data-ttu-id="03aed-140">(É a última configuração enacted no nó que está a utilizar o DSC da configuração atual do estado pretendido.)</span><span class="sxs-lookup"><span data-stu-id="03aed-140">(The current desired state configuration is the last configuration enacted on the node that is using DSC.)</span></span>| 
| <span data-ttu-id="03aed-141">credencial</span><span class="sxs-lookup"><span data-stu-id="03aed-141">Credential</span></span>| <span data-ttu-id="03aed-142">Indica as credenciais a utilizar para executar este script, se são necessárias credenciais.</span><span class="sxs-lookup"><span data-stu-id="03aed-142">Indicates the credentials to use for running this script, if credentials are required.</span></span>| 
| <span data-ttu-id="03aed-143">dependsOn</span><span class="sxs-lookup"><span data-stu-id="03aed-143">DependsOn</span></span>| <span data-ttu-id="03aed-144">Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado.</span><span class="sxs-lookup"><span data-stu-id="03aed-144">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="03aed-145">Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é **ResourceName** e o respetivo tipo é **ResourceType**, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="03aed-145">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>

## <a name="example-1"></a><span data-ttu-id="03aed-146">Exemplo 1</span><span class="sxs-lookup"><span data-stu-id="03aed-146">Example 1</span></span>
```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script ScriptExample
    {
        SetScript = 
        { 
            $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
            $sw.WriteLine("Some sample string")
            $sw.Close()
        }
        TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
        GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }          
    }
}
```

## <a name="example-2"></a><span data-ttu-id="03aed-147">Exemplo 2</span><span class="sxs-lookup"><span data-stu-id="03aed-147">Example 2</span></span>
```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script UpdateConfigurationVersion
    {
        GetScript = { 
            $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            return @{ 'Result' = "$currentVersion" }
        }          
        TestScript = { 
            $state = $GetScript
            if( $state['Result'] -eq $using:version )
            {
                Write-Verbose -Message ('{0} -eq {1}' -f $state['Result'],$using:version)
                return $true
            }
            Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
            return $false
        }
        SetScript = { 
            $using:version | Set-Content -Path (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
        }
    }
}
```

<span data-ttu-id="03aed-148">Este recurso é ao escrever a versão da configuração para um ficheiro de texto.</span><span class="sxs-lookup"><span data-stu-id="03aed-148">This resource is writing the configuration's version to a text file.</span></span> <span data-ttu-id="03aed-149">Esta versão está disponível no computador cliente, mas não se encontra em nenhum de nós, pelo que tem de ser transferidos para cada um do `Script` blocos de script do recurso com o do PowerShell `using` âmbito.</span><span class="sxs-lookup"><span data-stu-id="03aed-149">This version is available on the client computer, but isn't on any of the nodes, so it has to be passed to each of the `Script` resource's script blocks with PowerShell's `using` scope.</span></span> <span data-ttu-id="03aed-150">Quando MOF o nó a gerar ficheiro, o valor da `$version` variável é ler a partir de um ficheiro de texto no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="03aed-150">When generating the node's MOF file, the value of the `$version` variable is read from a text file on the client computer.</span></span> <span data-ttu-id="03aed-151">Substitui o DSC de `$using:version` bloquear variáveis em cada script com o valor da `$version` variável.</span><span class="sxs-lookup"><span data-stu-id="03aed-151">DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span>

