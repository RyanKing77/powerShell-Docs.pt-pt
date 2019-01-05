---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: DSC para Linux nxScript recursos
ms.openlocfilehash: 339968512ab1c16c4c3785a3a19b00c3fbbf9ea1
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048400"
---
# <a name="dsc-for-linux-nxscript-resource"></a><span data-ttu-id="b2a40-103">DSC para Linux nxScript recursos</span><span class="sxs-lookup"><span data-stu-id="b2a40-103">DSC for Linux nxScript Resource</span></span>

<span data-ttu-id="b2a40-104">O **nxScript** recursos no PowerShell Desired State Configuration (DSC) fornece um mecanismo para executar scripts do Linux num nó de Linux.</span><span class="sxs-lookup"><span data-stu-id="b2a40-104">The **nxScript** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to run Linux scripts on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="b2a40-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b2a40-105">Syntax</span></span>

```
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    [ Group = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="b2a40-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="b2a40-106">Properties</span></span>

|  <span data-ttu-id="b2a40-107">Propriedade</span><span class="sxs-lookup"><span data-stu-id="b2a40-107">Property</span></span> |  <span data-ttu-id="b2a40-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="b2a40-108">Description</span></span> |
|---|---|
| <span data-ttu-id="b2a40-109">GetScript</span><span class="sxs-lookup"><span data-stu-id="b2a40-109">GetScript</span></span>| <span data-ttu-id="b2a40-110">Fornece um script que é executado quando invoca o [Get-dscconfiguration para](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b2a40-110">Provides a script that runs when you invoke the [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet.</span></span> <span data-ttu-id="b2a40-111">O script tem de começar com um shebang, tais como #! / bin/bash.</span><span class="sxs-lookup"><span data-stu-id="b2a40-111">The script must begin with a shebang, such as #!/bin/bash.</span></span>|
| <span data-ttu-id="b2a40-112">SetScript</span><span class="sxs-lookup"><span data-stu-id="b2a40-112">SetScript</span></span>| <span data-ttu-id="b2a40-113">Fornece um script.</span><span class="sxs-lookup"><span data-stu-id="b2a40-113">Provides a script.</span></span> <span data-ttu-id="b2a40-114">Quando invoca o [Start-dscconfiguration para](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, o **TestScript** é executado primeiro.</span><span class="sxs-lookup"><span data-stu-id="b2a40-114">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, the **TestScript** runs first.</span></span> <span data-ttu-id="b2a40-115">Se o **TestScript** bloco devolve um código de saída diferente de 0, o **SetScript** bloco será executado.</span><span class="sxs-lookup"><span data-stu-id="b2a40-115">If the **TestScript** block returns an exit code other than 0, the **SetScript** block will run.</span></span> <span data-ttu-id="b2a40-116">Se o **TestScript** devolve um código de saída 0, o **SetScript** não será executado.</span><span class="sxs-lookup"><span data-stu-id="b2a40-116">If the **TestScript** returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="b2a40-117">O script tem de começar com um shebang, tais como `#!/bin/bash`.</span><span class="sxs-lookup"><span data-stu-id="b2a40-117">The script must begin with a shebang, such as `#!/bin/bash`.</span></span>|
| <span data-ttu-id="b2a40-118">TestScript</span><span class="sxs-lookup"><span data-stu-id="b2a40-118">TestScript</span></span>| <span data-ttu-id="b2a40-119">Fornece um script.</span><span class="sxs-lookup"><span data-stu-id="b2a40-119">Provides a script.</span></span> <span data-ttu-id="b2a40-120">Quando invoca o [Start-dscconfiguration para](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, este script é executado.</span><span class="sxs-lookup"><span data-stu-id="b2a40-120">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, this script runs.</span></span> <span data-ttu-id="b2a40-121">Se ela retornar um código de saída diferente de 0, o SetScript será executado.</span><span class="sxs-lookup"><span data-stu-id="b2a40-121">If it returns an exit code other than 0, the SetScript will run.</span></span> <span data-ttu-id="b2a40-122">Se ele retorna um código de saída 0, o **SetScript** não será executado.</span><span class="sxs-lookup"><span data-stu-id="b2a40-122">If it returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="b2a40-123">O **TestScript** também é executada quando invoca o [Test-dscconfiguration para](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b2a40-123">The **TestScript** also runs when you invoke the [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span></span> <span data-ttu-id="b2a40-124">No entanto, no caso, o **SetScript** não será executado, não importa qual código de saída é retornado do **TestScript**.</span><span class="sxs-lookup"><span data-stu-id="b2a40-124">However, in this case, the **SetScript** will not run, no matter what exit code is returned from the **TestScript**.</span></span> <span data-ttu-id="b2a40-125">O **TestScript** tem de devolver um código de saída 0 se a configuração real corresponde a configuração atual do estado pretendido e uma saída de código que 0 se não corresponde.</span><span class="sxs-lookup"><span data-stu-id="b2a40-125">The **TestScript** must return an exit code of 0 if the actual configuration matches the current desired state configuration, and an exit code other than 0 if it does not match.</span></span> <span data-ttu-id="b2a40-126">(A configuração atual do estado pretendido é a última configuração elaborada no nó que está a utilizar o DSC).</span><span class="sxs-lookup"><span data-stu-id="b2a40-126">(The current desired state configuration is the last configuration enacted on the node that is using DSC).</span></span> <span data-ttu-id="b2a40-127">O script tem de começar com um shebang, tais como 1#!/bin/bash.1</span><span class="sxs-lookup"><span data-stu-id="b2a40-127">The script must begin with a shebang, such as 1#!/bin/bash.1</span></span>|
| <span data-ttu-id="b2a40-128">Utilizador</span><span class="sxs-lookup"><span data-stu-id="b2a40-128">User</span></span>| <span data-ttu-id="b2a40-129">O utilizador para executar o script como.</span><span class="sxs-lookup"><span data-stu-id="b2a40-129">The user to run the script as.</span></span>|
| <span data-ttu-id="b2a40-130">Grupo</span><span class="sxs-lookup"><span data-stu-id="b2a40-130">Group</span></span>| <span data-ttu-id="b2a40-131">O grupo para executar o script como.</span><span class="sxs-lookup"><span data-stu-id="b2a40-131">The group to run the script as.</span></span>|
| <span data-ttu-id="b2a40-132">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b2a40-132">DependsOn</span></span> | <span data-ttu-id="b2a40-133">Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="b2a40-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b2a40-134">Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e seu tipo é **ResourceType**, a sintaxe para usar isso a propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="b2a40-134">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="b2a40-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b2a40-135">Example</span></span>

<span data-ttu-id="b2a40-136">O exemplo seguinte demonstra o uso do **nxScript** recursos para executar o gerenciamento de configuração adicionais.</span><span class="sxs-lookup"><span data-stu-id="b2a40-136">The following example demonstrates the use of the **nxScript** resource to perform additional configuration management.</span></span>

```
Import-DSCResource -Module nx

Node $node {
nxScript KeepDirEmpty{

    GetScript = @"
#!/bin/bash
ls /tmp/mydir/ | wc -l
"@

    SetScript = @"
#!/bin/bash
rm -rf /tmp/mydir/*
"@

    TestScript = @'
#!/bin/bash
filecount=`ls /tmp/mydir | wc -l`
if [ $filecount -gt 0 ]
then
    exit 1
else
    exit 0
fi
'@
}
}
```