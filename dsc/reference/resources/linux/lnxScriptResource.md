---
ms.date: 06/12/2017
keywords: DSC, PowerShell, configuração, instalação
title: Recurso de nxScript do DSC para Linux
ms.openlocfilehash: 0ad0530f1de7b86ff48c4eb1f79870f6682894a1
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372158"
---
# <a name="dsc-for-linux-nxscript-resource"></a><span data-ttu-id="3ba62-103">Recurso de nxScript do DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="3ba62-103">DSC for Linux nxScript Resource</span></span>

<span data-ttu-id="3ba62-104">O recurso **nxScript** na configuração de estado desejado (DSC) do PowerShell fornece um mecanismo para executar scripts do Linux em um nó do Linux.</span><span class="sxs-lookup"><span data-stu-id="3ba62-104">The **nxScript** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to run Linux scripts on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="3ba62-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3ba62-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="3ba62-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="3ba62-106">Properties</span></span>

|  <span data-ttu-id="3ba62-107">Propriedade</span><span class="sxs-lookup"><span data-stu-id="3ba62-107">Property</span></span> |  <span data-ttu-id="3ba62-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="3ba62-108">Description</span></span> |
|---|---|
| <span data-ttu-id="3ba62-109">GetScript</span><span class="sxs-lookup"><span data-stu-id="3ba62-109">GetScript</span></span>| <span data-ttu-id="3ba62-110">Fornece um script para retornar o status atual do computador.</span><span class="sxs-lookup"><span data-stu-id="3ba62-110">Provides a script to return current status of the machine.</span></span>  <span data-ttu-id="3ba62-111">Esse script é executado quando você invoca o script [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) .</span><span class="sxs-lookup"><span data-stu-id="3ba62-111">This script runs when you invoke the [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script.</span></span> <span data-ttu-id="3ba62-112">O script deve começar com um shebang, como #!/bin/bash.</span><span class="sxs-lookup"><span data-stu-id="3ba62-112">The script must begin with a shebang, such as #!/bin/bash.</span></span>|
| <span data-ttu-id="3ba62-113">SetScript</span><span class="sxs-lookup"><span data-stu-id="3ba62-113">SetScript</span></span>| <span data-ttu-id="3ba62-114">Fornece um script que coloca o computador no estado correto.</span><span class="sxs-lookup"><span data-stu-id="3ba62-114">Provides a script that puts the machine in the correct state.</span></span> <span data-ttu-id="3ba62-115">Quando você invoca o script [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) , o **TestScript** é executado primeiro.</span><span class="sxs-lookup"><span data-stu-id="3ba62-115">When you invoke the [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script, the **TestScript** runs first.</span></span> <span data-ttu-id="3ba62-116">Se o bloco **TestScript** retornar um código de saída diferente de 0, o bloco setscript será executado.</span><span class="sxs-lookup"><span data-stu-id="3ba62-116">If the **TestScript** block returns an exit code other than 0, the **SetScript** block will run.</span></span> <span data-ttu-id="3ba62-117">Se o **TestScript** retornar um código de saída de 0,  o setscript não será executado.</span><span class="sxs-lookup"><span data-stu-id="3ba62-117">If the **TestScript** returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="3ba62-118">O script deve começar com um shebang, `#!/bin/bash`como.</span><span class="sxs-lookup"><span data-stu-id="3ba62-118">The script must begin with a shebang, such as `#!/bin/bash`.</span></span>|
| <span data-ttu-id="3ba62-119">TestScript</span><span class="sxs-lookup"><span data-stu-id="3ba62-119">TestScript</span></span>| <span data-ttu-id="3ba62-120">Fornece um script que avalia se o nó está atualmente no estado correto.</span><span class="sxs-lookup"><span data-stu-id="3ba62-120">Provides a script that evaluates whether the node is currently in the correct state.</span></span> <span data-ttu-id="3ba62-121">Quando você invoca o script [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) , esse script é executado.</span><span class="sxs-lookup"><span data-stu-id="3ba62-121">When you invoke the [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script, this script runs.</span></span> <span data-ttu-id="3ba62-122">Se ele retornar um código de saída diferente de 0, o setscript será executado.</span><span class="sxs-lookup"><span data-stu-id="3ba62-122">If it returns an exit code other than 0, the SetScript will run.</span></span> <span data-ttu-id="3ba62-123">Se ele retornar um código de saída de 0,  o setscript não será executado.</span><span class="sxs-lookup"><span data-stu-id="3ba62-123">If it returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="3ba62-124">O **TestScript** também é executado quando você invoca o script [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) .</span><span class="sxs-lookup"><span data-stu-id="3ba62-124">The **TestScript** also runs when you invoke the [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script.</span></span> <span data-ttu-id="3ba62-125">No entanto, nesse caso,  o setscript não será executado, independentemente do código de saída retornado do **TestScript**.</span><span class="sxs-lookup"><span data-stu-id="3ba62-125">However, in this case, the **SetScript** will not run, no matter what exit code is returned from the **TestScript**.</span></span> <span data-ttu-id="3ba62-126">O **TestScript** deve conter conteúdo e deve retornar um código de saída de 0 se a configuração real corresponder à configuração de estado atual desejado e um código de saída diferente de 0 se não corresponder.</span><span class="sxs-lookup"><span data-stu-id="3ba62-126">The **TestScript** must contain content and must return an exit code of 0 if the actual configuration matches the current desired state configuration, and an exit code other than 0 if it does not match.</span></span> <span data-ttu-id="3ba62-127">(A configuração de estado atual desejada é a última configuração aplicada no nó que está usando a DSC).</span><span class="sxs-lookup"><span data-stu-id="3ba62-127">(The current desired state configuration is the last configuration enacted on the node that is using DSC).</span></span> <span data-ttu-id="3ba62-128">O script deve começar com um shebang, como 1 #!/bin/bash.1</span><span class="sxs-lookup"><span data-stu-id="3ba62-128">The script must begin with a shebang, such as 1#!/bin/bash.1</span></span>|
| <span data-ttu-id="3ba62-129">Utilizador</span><span class="sxs-lookup"><span data-stu-id="3ba62-129">User</span></span>| <span data-ttu-id="3ba62-130">O usuário para executar o script como.</span><span class="sxs-lookup"><span data-stu-id="3ba62-130">The user to run the script as.</span></span>|
| <span data-ttu-id="3ba62-131">Grupo</span><span class="sxs-lookup"><span data-stu-id="3ba62-131">Group</span></span>| <span data-ttu-id="3ba62-132">O grupo para o qual executar o script.</span><span class="sxs-lookup"><span data-stu-id="3ba62-132">The group to run the script as.</span></span>|
| <span data-ttu-id="3ba62-133">DependsOn</span><span class="sxs-lookup"><span data-stu-id="3ba62-133">DependsOn</span></span> | <span data-ttu-id="3ba62-134">Indica que a configuração de outro recurso deve ser executada antes que este recurso seja configurado.</span><span class="sxs-lookup"><span data-stu-id="3ba62-134">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="3ba62-135">Por exemplo, se a **ID** do bloco de script de configuração de recurso que você deseja executar primeiro  for resourceName e seu tipo for **ResourceType**, a sintaxe para usar `DependsOn = "[ResourceType]ResourceName"`essa propriedade será.</span><span class="sxs-lookup"><span data-stu-id="3ba62-135">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="3ba62-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3ba62-136">Example</span></span>

<span data-ttu-id="3ba62-137">O exemplo a seguir demonstra o uso do recurso **nxScript** para executar o gerenciamento de configuração adicional.</span><span class="sxs-lookup"><span data-stu-id="3ba62-137">The following example demonstrates the use of the **nxScript** resource to perform additional configuration management.</span></span>

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
