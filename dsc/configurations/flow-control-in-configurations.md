---
ms.date: 12/12/2018
keywords: DSC, powershell, configuração, a configuração
title: Instruções condicionais e loops em configurações
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404770"
---
# <a name="conditional-statements-and-loops-in-configurations"></a><span data-ttu-id="91576-103">Instruções condicionais e loops em configurações</span><span class="sxs-lookup"><span data-stu-id="91576-103">Conditional statements and loops in Configurations</span></span>

<span data-ttu-id="91576-104">Pode fazer sua [configurações](configurations.md) mais dinâmicos com palavras-chave de controle de fluxo de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="91576-104">You can make your [Configurations](configurations.md) more dynamic using PowerShell flow-control keywords.</span></span> <span data-ttu-id="91576-105">Este artigo irá mostrar como pode usar instruções condicionais e loops para tornar suas configurações mais dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="91576-105">This article will show you how you can use conditional statements, and loops to make your Configurations more dynamic.</span></span> <span data-ttu-id="91576-106">Combinar condicional e loops com [parâmetros](add-parameters-to-a-configuration.md) e [dados de configuração](configData.md) permite-lhe mais flexibilidade e controle ao compilar suas configurações.</span><span class="sxs-lookup"><span data-stu-id="91576-106">Combining conditional and loops with [parameters](add-parameters-to-a-configuration.md) and [Configuration Data](configData.md) allows you more flexibility and control when compiling your Configurations.</span></span>

<span data-ttu-id="91576-107">Tal como uma função ou um bloco de scripts, pode usar qualquer linguagem de PowerShell dentro de uma configuração.</span><span class="sxs-lookup"><span data-stu-id="91576-107">Just like a Function or a Script Block, you can use any PowerShell language within a Configuration.</span></span> <span data-ttu-id="91576-108">As instruções que utilizar apenas serão avaliadas quando chama a sua configuração para compilar um arquivo de ". MOF".</span><span class="sxs-lookup"><span data-stu-id="91576-108">The statements you use will only be evaluated when you call your Configuration to compile a ".mof" file.</span></span> <span data-ttu-id="91576-109">Os exemplos abaixo mostram cenários simples para demonstrar conceitos.</span><span class="sxs-lookup"><span data-stu-id="91576-109">The examples below show simple scenarios to demonstrate concepts.</span></span> <span data-ttu-id="91576-110">Condicionais são loops com mais frequência são utilizados com parâmetros e dados de configuração.</span><span class="sxs-lookup"><span data-stu-id="91576-110">Conditionals are loops are more often used with parameters and Configuration Data.</span></span>

<span data-ttu-id="91576-111">Neste exemplo simples, o **serviço** bloco de recurso obtém o estado atual de um serviço em tempo de compilação para gerar um arquivo de ". MOF" que mantém o estado atual.</span><span class="sxs-lookup"><span data-stu-id="91576-111">In this simple example, the **Service** resource block retrieves the current state of a service at compile time to generate a ".mof" file that maintains its current state.</span></span>

> [!NOTE]
> <span data-ttu-id="91576-112">Utilizar blocos de recursos dinâmicos antecipará a eficácia do Intellisense.</span><span class="sxs-lookup"><span data-stu-id="91576-112">Using dynamic Resource blocks will preempt the effectiveness of Intellisense.</span></span> <span data-ttu-id="91576-113">O analisador do PowerShell não é possível determinar se os valores especificados são aceitáveis até que a configuração é compilada.</span><span class="sxs-lookup"><span data-stu-id="91576-113">The PowerShell parser cannot determine if the values specified are acceptable until the Configuration is compiled.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Service Spooler
        {
            Name = "Spooler"
            State = $(Get-Service -Name 'spooler').Status
            StartType = $(Get-Service -Name 'spooler').StartType
        }
    }
}
```

<span data-ttu-id="91576-114">Além disso, poderia criar uma **serviço** bloquear recursos para cada serviço no computador atual, usando um `foreach` loop.</span><span class="sxs-lookup"><span data-stu-id="91576-114">Additionally, you could create a **Service** block resource for every service on the current machine, using a `foreach` loop.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Foreach ($service in $(Get-Service))
        {
            Service $service.Name
            {
                Name = $service.Name
                State = $service.Status
                StartType = $service.StartType
            }
        }
    }
}
```

<span data-ttu-id="91576-115">Também só pode criar as configurações para as máquinas que estiverem online, através de um simples `if` instrução.</span><span class="sxs-lookup"><span data-stu-id="91576-115">You could also only create configurations for machines that are online, by using a simple `if` statement.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    Foreach ($computer in @('Server01', 'Server02', 'Server03'))
    {
        if (Test-Connection -ComputerName $computer)
        {
            Node $computer
            {
                Service "Spooler"
                {
                    Name = "Spooler"
                    State = "Started"
                }
            }
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="91576-116">O recurso dinâmico bloqueia, a referência de exemplos acima, a máquina atual.</span><span class="sxs-lookup"><span data-stu-id="91576-116">The dynamic resource blocks in the above examples reference the current machine.</span></span> <span data-ttu-id="91576-117">Neste caso, o que seria a máquina estiver a criar a configuração no, não o nó de destino.</span><span class="sxs-lookup"><span data-stu-id="91576-117">In this instance, that would be the machine you are authoring the Configuration on, not the target Node.</span></span>

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a><span data-ttu-id="91576-118">Resumo</span><span class="sxs-lookup"><span data-stu-id="91576-118">Summary</span></span>

<span data-ttu-id="91576-119">Em resumo, pode usar qualquer linguagem de PowerShell dentro de uma configuração.</span><span class="sxs-lookup"><span data-stu-id="91576-119">In summary, you can use any PowerShell language within a Configuration.</span></span>

<span data-ttu-id="91576-120">Isto inclui coisas como:</span><span class="sxs-lookup"><span data-stu-id="91576-120">This includes things like:</span></span>

- <span data-ttu-id="91576-121">Objetos personalizados</span><span class="sxs-lookup"><span data-stu-id="91576-121">Custom Objects</span></span>
- <span data-ttu-id="91576-122">Tabelas hash</span><span class="sxs-lookup"><span data-stu-id="91576-122">Hashtables</span></span>
- <span data-ttu-id="91576-123">Manipulação de cadeias</span><span class="sxs-lookup"><span data-stu-id="91576-123">String manipulation</span></span>
- <span data-ttu-id="91576-124">Comunicação remota</span><span class="sxs-lookup"><span data-stu-id="91576-124">Remoting</span></span>
- <span data-ttu-id="91576-125">WMI e CIM</span><span class="sxs-lookup"><span data-stu-id="91576-125">WMI and CIM</span></span>
- <span data-ttu-id="91576-126">Objetos do Active Directory</span><span class="sxs-lookup"><span data-stu-id="91576-126">ActiveDirectory objects</span></span>
- <span data-ttu-id="91576-127">e muito mais...</span><span class="sxs-lookup"><span data-stu-id="91576-127">and more...</span></span>

<span data-ttu-id="91576-128">Qualquer código de PowerShell definido numa configuração será avaliado um tempo de compilação, mas também é possível colocar código no script que contém a sua configuração.</span><span class="sxs-lookup"><span data-stu-id="91576-128">Any PowerShell code defined in a Configuration will be evaluated a compile time, but you can also place code in the script containing your Configuration.</span></span> <span data-ttu-id="91576-129">Nenhum código além do bloco de configuração será executado quando importar a configuração.</span><span class="sxs-lookup"><span data-stu-id="91576-129">Any code outside of the Configuration block will be executed when you import your Configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="91576-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91576-130">See also</span></span>

- [<span data-ttu-id="91576-131">Adicionar parâmetros a uma configuração</span><span class="sxs-lookup"><span data-stu-id="91576-131">Add parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
- [<span data-ttu-id="91576-132">Separar dados de configuração de configurações</span><span class="sxs-lookup"><span data-stu-id="91576-132">Separate Configuration data from Configurations</span></span>](configData.md)
