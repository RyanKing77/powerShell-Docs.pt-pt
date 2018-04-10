---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: DSC de Linux nxScript recursos
ms.openlocfilehash: 7c8c3aa16af5b31c0a549972288c9466bb56609d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxscript-resource"></a><span data-ttu-id="b7686-103">DSC de Linux nxScript recursos</span><span class="sxs-lookup"><span data-stu-id="b7686-103">DSC for Linux nxScript Resource</span></span>

<span data-ttu-id="b7686-104">O **nxScript** recursos no PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para executar scripts de Linux num nó de Linux.</span><span class="sxs-lookup"><span data-stu-id="b7686-104">The **nxScript** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to run Linux scripts on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="b7686-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7686-105">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="b7686-106">Propriedades</span><span class="sxs-lookup"><span data-stu-id="b7686-106">Properties</span></span>

|  <span data-ttu-id="b7686-107">Propriedade</span><span class="sxs-lookup"><span data-stu-id="b7686-107">Property</span></span> |  <span data-ttu-id="b7686-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7686-108">Description</span></span> |
|---|---|
| <span data-ttu-id="b7686-109">GetScript</span><span class="sxs-lookup"><span data-stu-id="b7686-109">GetScript</span></span>| <span data-ttu-id="b7686-110">Fornece um script que é executado quando invocar o [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b7686-110">Provides a script that runs when you invoke the [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet.</span></span> <span data-ttu-id="b7686-111">O script tem de começar com uma shebang, tais como #! / bin/bash.</span><span class="sxs-lookup"><span data-stu-id="b7686-111">The script must begin with a shebang, such as #!/bin/bash.</span></span>|
| <span data-ttu-id="b7686-112">SetScript</span><span class="sxs-lookup"><span data-stu-id="b7686-112">SetScript</span></span>| <span data-ttu-id="b7686-113">Fornece um script.</span><span class="sxs-lookup"><span data-stu-id="b7686-113">Provides a script.</span></span> <span data-ttu-id="b7686-114">Quando invocar o [início DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, a **TestScript** executa primeiro.</span><span class="sxs-lookup"><span data-stu-id="b7686-114">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, the **TestScript** runs first.</span></span> <span data-ttu-id="b7686-115">Se o **TestScript** bloco devolve um código de saída diferente de 0, o **SetScript** bloco será executado.</span><span class="sxs-lookup"><span data-stu-id="b7686-115">If the **TestScript** block returns an exit code other than 0, the **SetScript** block will run.</span></span> <span data-ttu-id="b7686-116">Se o **TestScript** devolve um código de saída de 0, o **SetScript** não será executado.</span><span class="sxs-lookup"><span data-stu-id="b7686-116">If the **TestScript** returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="b7686-117">O script tem de começar com uma shebang, tais como `#!/bin/bash`.</span><span class="sxs-lookup"><span data-stu-id="b7686-117">The script must begin with a shebang, such as `#!/bin/bash`.</span></span>|
| <span data-ttu-id="b7686-118">TestScript</span><span class="sxs-lookup"><span data-stu-id="b7686-118">TestScript</span></span>| <span data-ttu-id="b7686-119">Fornece um script.</span><span class="sxs-lookup"><span data-stu-id="b7686-119">Provides a script.</span></span> <span data-ttu-id="b7686-120">Quando invocar o [início DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, este script é executado.</span><span class="sxs-lookup"><span data-stu-id="b7686-120">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, this script runs.</span></span> <span data-ttu-id="b7686-121">Se devolver um código de saída diferente de 0, o SetScript será executado.</span><span class="sxs-lookup"><span data-stu-id="b7686-121">If it returns an exit code other than 0, the SetScript will run.</span></span> <span data-ttu-id="b7686-122">Se devolver um código de saída 0, o **SetScript** não será executado.</span><span class="sxs-lookup"><span data-stu-id="b7686-122">If it returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="b7686-123">O **TestScript** também é executada quando invocar o [teste DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b7686-123">The **TestScript** also runs when you invoke the [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span></span> <span data-ttu-id="b7686-124">No entanto, neste caso, o **SetScript** não será executado, independentemente do é devolvido o código de saída do **TestScript**.</span><span class="sxs-lookup"><span data-stu-id="b7686-124">However, in this case, the **SetScript** will not run, no matter what exit code is returned from the **TestScript**.</span></span> <span data-ttu-id="b7686-125">O **TestScript** tem de devolver um código de saída 0 se a configuração real corresponde a configuração atual do estado pretendido e uma saída de código à 0 se não corresponde.</span><span class="sxs-lookup"><span data-stu-id="b7686-125">The **TestScript** must return an exit code of 0 if the actual configuration matches the current desired state configuration, and an exit code other than 0 if it does not match.</span></span> <span data-ttu-id="b7686-126">(É a última configuração enacted no nó que está a utilizar o DSC da configuração atual do estado pretendido).</span><span class="sxs-lookup"><span data-stu-id="b7686-126">(The current desired state configuration is the last configuration enacted on the node that is using DSC).</span></span> <span data-ttu-id="b7686-127">O script tem de começar com uma shebang, tais como 1#!/bin/bash.1</span><span class="sxs-lookup"><span data-stu-id="b7686-127">The script must begin with a shebang, such as 1#!/bin/bash.1</span></span>|
| <span data-ttu-id="b7686-128">Utilizador</span><span class="sxs-lookup"><span data-stu-id="b7686-128">User</span></span>| <span data-ttu-id="b7686-129">O utilizador para executar o script como.</span><span class="sxs-lookup"><span data-stu-id="b7686-129">The user to run the script as.</span></span>|
| <span data-ttu-id="b7686-130">Grupo</span><span class="sxs-lookup"><span data-stu-id="b7686-130">Group</span></span>| <span data-ttu-id="b7686-131">O grupo para executar o script como.</span><span class="sxs-lookup"><span data-stu-id="b7686-131">The group to run the script as.</span></span>|
| <span data-ttu-id="b7686-132">dependsOn</span><span class="sxs-lookup"><span data-stu-id="b7686-132">DependsOn</span></span> | <span data-ttu-id="b7686-133">Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado.</span><span class="sxs-lookup"><span data-stu-id="b7686-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b7686-134">Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e o respetivo tipo é **ResourceType**, a sintaxe para utilizar esta a propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="b7686-134">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="b7686-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b7686-135">Example</span></span>

<span data-ttu-id="b7686-136">O exemplo seguinte demonstra a utilização do **nxScript** recursos para fazer a gestão de configuração adicionais.</span><span class="sxs-lookup"><span data-stu-id="b7686-136">The following example demonstrates the use of the **nxScript** resource to perform additional configuration management.</span></span>

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