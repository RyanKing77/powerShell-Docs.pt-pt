---
ms.date: 08/24/2018
keywords: DSC, powershell, configuração, a configuração
title: Recursos de Script de DSC
ms.openlocfilehash: ef84239820a44aab2a028f7f0fe17653a851b72e
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048515"
---
# <a name="dsc-script-resource"></a><span data-ttu-id="e9bac-103">Recursos de Script de DSC</span><span class="sxs-lookup"><span data-stu-id="e9bac-103">DSC Script Resource</span></span>

> <span data-ttu-id="e9bac-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="e9bac-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="e9bac-105">O **Script** recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para executar blocos de script do Windows PowerShell em nós de destino.</span><span class="sxs-lookup"><span data-stu-id="e9bac-105">The **Script** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="e9bac-106">O **Script** utilizações de recursos `GetScript`, `SetScript`, e `TestScript` operações de estado de propriedades que contêm os blocos de script que define para realizar o DSC correspondente.</span><span class="sxs-lookup"><span data-stu-id="e9bac-106">The **Script** resource uses `GetScript`, `SetScript`, and `TestScript` properties that contain script blocks you define to perform the corresponding DSC state operations.</span></span>

## <a name="syntax"></a><span data-ttu-id="e9bac-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e9bac-107">Syntax</span></span>

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

> [!NOTE]
> <span data-ttu-id="e9bac-108">O `GetScript`, `TestScript`, e `SetScript` blocos são armazenados como cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e9bac-108">The `GetScript`, `TestScript`, and `SetScript` blocks are stored as strings.</span></span>

## <a name="properties"></a><span data-ttu-id="e9bac-109">Propriedades</span><span class="sxs-lookup"><span data-stu-id="e9bac-109">Properties</span></span>

|<span data-ttu-id="e9bac-110">Propriedade</span><span class="sxs-lookup"><span data-stu-id="e9bac-110">Property</span></span>|<span data-ttu-id="e9bac-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="e9bac-111">Description</span></span>|
|--------|-----------|
|<span data-ttu-id="e9bac-112">GetScript</span><span class="sxs-lookup"><span data-stu-id="e9bac-112">GetScript</span></span>|<span data-ttu-id="e9bac-113">Um bloco de script que retorna o estado atual do nó.</span><span class="sxs-lookup"><span data-stu-id="e9bac-113">A script block that returns the current state of the Node.</span></span>|
|<span data-ttu-id="e9bac-114">SetScript</span><span class="sxs-lookup"><span data-stu-id="e9bac-114">SetScript</span></span>|<span data-ttu-id="e9bac-115">Um bloco de script que utiliza o DSC para impor a conformidade quando o nó não está no estado pretendido.</span><span class="sxs-lookup"><span data-stu-id="e9bac-115">A script block that DSC uses to enforce compliance when the Node is not in the desired state.</span></span>|
|<span data-ttu-id="e9bac-116">TestScript</span><span class="sxs-lookup"><span data-stu-id="e9bac-116">TestScript</span></span>|<span data-ttu-id="e9bac-117">Um bloco de script que determina se o nó está no estado pretendido.</span><span class="sxs-lookup"><span data-stu-id="e9bac-117">A script block that determines if the Node is in the desired state.</span></span>|
|<span data-ttu-id="e9bac-118">Credencial</span><span class="sxs-lookup"><span data-stu-id="e9bac-118">Credential</span></span>| <span data-ttu-id="e9bac-119">Indica as credenciais a utilizar para executar este script, se as credenciais são necessárias.</span><span class="sxs-lookup"><span data-stu-id="e9bac-119">Indicates the credentials to use for running this script, if credentials are required.</span></span>|
|<span data-ttu-id="e9bac-120">DependsOn</span><span class="sxs-lookup"><span data-stu-id="e9bac-120">DependsOn</span></span>| <span data-ttu-id="e9bac-121">Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="e9bac-121">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="e9bac-122">Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será **ResourceName** e seu tipo é **ResourceType**, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="e9bac-122">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>

### <a name="getscript"></a><span data-ttu-id="e9bac-123">GetScript</span><span class="sxs-lookup"><span data-stu-id="e9bac-123">GetScript</span></span>

<span data-ttu-id="e9bac-124">DSC não utiliza a saída do `GetScript`.</span><span class="sxs-lookup"><span data-stu-id="e9bac-124">DSC does not use the output from `GetScript`.</span></span> <span data-ttu-id="e9bac-125">O [Get-dscconfiguration para](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet é executado o `GetScript` para obter o estado atual de um nó.</span><span class="sxs-lookup"><span data-stu-id="e9bac-125">The [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet executes the `GetScript` to retrieve a node's current state.</span></span> <span data-ttu-id="e9bac-126">Não é necessário de um valor de retorno `GetScript`.</span><span class="sxs-lookup"><span data-stu-id="e9bac-126">A return value is not required from `GetScript`.</span></span> <span data-ttu-id="e9bac-127">Se especificar um valor de retorno, tem de ser um `hashtable` que contém um **resultado** chave cujo valor é um `String`.</span><span class="sxs-lookup"><span data-stu-id="e9bac-127">If you specify a return value, it must be a `hashtable` containing a **Result** key whose value is a `String`.</span></span>

### <a name="testscript"></a><span data-ttu-id="e9bac-128">TestScript</span><span class="sxs-lookup"><span data-stu-id="e9bac-128">TestScript</span></span>

<span data-ttu-id="e9bac-129">O `TestScript` executado pela DSC para determinar se o `SetScript` deve ser executado.</span><span class="sxs-lookup"><span data-stu-id="e9bac-129">The `TestScript` is executed by DSC to determine if the `SetScript` should be run.</span></span> <span data-ttu-id="e9bac-130">Se o `TestScript` devolve `$false`, DSC executa o `SetScript` para colocar o nó para o estado pretendido.</span><span class="sxs-lookup"><span data-stu-id="e9bac-130">If the `TestScript` returns `$false`, DSC executes the `SetScript` to bring the node back to the desired state.</span></span> <span data-ttu-id="e9bac-131">Tem de devolver um `boolean` valor.</span><span class="sxs-lookup"><span data-stu-id="e9bac-131">It must return a `boolean` value.</span></span> <span data-ttu-id="e9bac-132">O resultado de `$true` indica que o nó está em conformidade e `SetScript` não deve ser executado.</span><span class="sxs-lookup"><span data-stu-id="e9bac-132">A result of `$true` indicates that the node is compliant and `SetScript` should not executed.</span></span>

<span data-ttu-id="e9bac-133">O [Test-dscconfiguration para](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet, executa o `TestScript` para obter a conformidade de nós com o **Script** recursos.</span><span class="sxs-lookup"><span data-stu-id="e9bac-133">The [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet, executes the `TestScript` to retrieve the nodes compliance with the  **Script** resources.</span></span> <span data-ttu-id="e9bac-134">No entanto, no caso, o `SetScript` não é executado, não importa o que o `TestScript` bloquear devolve.</span><span class="sxs-lookup"><span data-stu-id="e9bac-134">However, in this case, the `SetScript` does not run, no matter what the `TestScript` block returns.</span></span>

> [!NOTE]
> <span data-ttu-id="e9bac-135">Todos os resultados da sua `TestScript` faz parte do valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="e9bac-135">All output from your `TestScript` is part of its return value.</span></span> <span data-ttu-id="e9bac-136">PowerShell interpreta unsuppressed saída diferente de zero, que significa que seu `TestScript` retornará `$true` independentemente do Estado de seu nó.</span><span class="sxs-lookup"><span data-stu-id="e9bac-136">PowerShell interprets unsuppressed output as non-zero, which means that your `TestScript` will return `$true` regardless of your node's state.</span></span>
> <span data-ttu-id="e9bac-137">Isso resulta em resultados imprevisíveis, falsos positivos e faz com que dificuldade durante a resolução de problemas.</span><span class="sxs-lookup"><span data-stu-id="e9bac-137">This results in unpredictable results, false positives, and causes difficulty during troubleshooting.</span></span>

### <a name="setscript"></a><span data-ttu-id="e9bac-138">SetScript</span><span class="sxs-lookup"><span data-stu-id="e9bac-138">SetScript</span></span>

<span data-ttu-id="e9bac-139">O `SetScript` modifica o nó para enfore o estado pretendido.</span><span class="sxs-lookup"><span data-stu-id="e9bac-139">The `SetScript` modifies the node to enfore the desired state.</span></span> <span data-ttu-id="e9bac-140">Ela é chamada pelo DSC se o `TestScript` devolve de bloco de script `$false`.</span><span class="sxs-lookup"><span data-stu-id="e9bac-140">It is called by DSC if the `TestScript` script block returns `$false`.</span></span> <span data-ttu-id="e9bac-141">O `SetScript` não deve ter nenhum valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="e9bac-141">The `SetScript` should have no return value.</span></span>

## <a name="examples"></a><span data-ttu-id="e9bac-142">Exemplos</span><span class="sxs-lookup"><span data-stu-id="e9bac-142">Examples</span></span>

### <a name="example-1-write-sample-text-using-a-script-resource"></a><span data-ttu-id="e9bac-143">Exemplo 1: Escrever o texto de exemplo através de um recurso de Script</span><span class="sxs-lookup"><span data-stu-id="e9bac-143">Example 1: Write sample text using a Script resource</span></span>

<span data-ttu-id="e9bac-144">Neste exemplo, testa a existência de `C:\TempFolder\TestFile.txt` em cada nó.</span><span class="sxs-lookup"><span data-stu-id="e9bac-144">This example tests for the existence of `C:\TempFolder\TestFile.txt` on each node.</span></span> <span data-ttu-id="e9bac-145">Se não existir, cria-o com o `SetScript`.</span><span class="sxs-lookup"><span data-stu-id="e9bac-145">If it does not exist, it creates it using the `SetScript`.</span></span> <span data-ttu-id="e9bac-146">O `GetScript` devolve o conteúdo do ficheiro e o valor de retorno não é utilizado.</span><span class="sxs-lookup"><span data-stu-id="e9bac-146">The `GetScript` returns the contents of the file, and its return value is not used.</span></span>

```powershell
Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script ScriptExample
        {
            SetScript = {
                $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
                $sw.WriteLine("Some sample string")
                $sw.Close()
            }
            TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
            GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }
        }
    }
}
```

### <a name="example-2-compare-version-information-using-a-script-resource"></a><span data-ttu-id="e9bac-147">Exemplo 2: Comparar as informações de versão usando um recurso de Script</span><span class="sxs-lookup"><span data-stu-id="e9bac-147">Example 2: Compare version information using a Script resource</span></span>

<span data-ttu-id="e9bac-148">Este exemplo obtém o *em conformidade* informações sobre a versão de um ficheiro de texto no computador de criação e armazena-na `$version` variável.</span><span class="sxs-lookup"><span data-stu-id="e9bac-148">This example retrieves the *compliant* version information from a text file on the authoring computer and stores it in the `$version` variable.</span></span> <span data-ttu-id="e9bac-149">Ao gerar o ficheiro MOF do nó, DSC substitui o `$using:version` variáveis em cada script bloquear com o valor do `$version` variável.</span><span class="sxs-lookup"><span data-stu-id="e9bac-149">When generating the node's MOF file, DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span> <span data-ttu-id="e9bac-150">Durante a execução, o *em conformidade* versão é armazenada num arquivo de texto em cada nó e em comparação com e atualizada sobre as execuções subsequentes.</span><span class="sxs-lookup"><span data-stu-id="e9bac-150">During execution, the *compliant* version is stored in a text file on each Node and compared and updated on subsequent executions.</span></span>

```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

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
}
```