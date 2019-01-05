---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recurso de registro de DSC
ms.openlocfilehash: e0ae1a4a27edc08c4e6ccd47786426917eb1ccb4
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048491"
---
# <a name="dsc-registry-resource"></a><span data-ttu-id="5fa24-103">Recurso de registro de DSC</span><span class="sxs-lookup"><span data-stu-id="5fa24-103">DSC Registry Resource</span></span>

<span data-ttu-id="5fa24-104">_Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="5fa24-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="5fa24-105">O **Registro** recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para gerir as chaves de registro e os valores num nó de destino.</span><span class="sxs-lookup"><span data-stu-id="5fa24-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="5fa24-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5fa24-106">Syntax</span></span>

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Present | Absent }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a><span data-ttu-id="5fa24-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="5fa24-107">Properties</span></span>

| <span data-ttu-id="5fa24-108">Propriedade</span><span class="sxs-lookup"><span data-stu-id="5fa24-108">Property</span></span> | <span data-ttu-id="5fa24-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="5fa24-109">Description</span></span> |
| --- | --- |
| <span data-ttu-id="5fa24-110">Tecla</span><span class="sxs-lookup"><span data-stu-id="5fa24-110">Key</span></span>| <span data-ttu-id="5fa24-111">Indica o caminho da chave do registo para o qual pretende garantir um estado específico.</span><span class="sxs-lookup"><span data-stu-id="5fa24-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="5fa24-112">Este caminho tem de incluir o hive.</span><span class="sxs-lookup"><span data-stu-id="5fa24-112">This path must include the hive.</span></span>|
| <span data-ttu-id="5fa24-113">valueName</span><span class="sxs-lookup"><span data-stu-id="5fa24-113">ValueName</span></span>| <span data-ttu-id="5fa24-114">Indica o nome do valor do Registro.</span><span class="sxs-lookup"><span data-stu-id="5fa24-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="5fa24-115">Para adicionar ou remover uma chave de registo, especifique esta propriedade como uma cadeia vazia sem especificar ValueType ou ValueData.</span><span class="sxs-lookup"><span data-stu-id="5fa24-115">To add or remove a registry key, specify this property as an empty string without specifying ValueType or ValueData.</span></span> <span data-ttu-id="5fa24-116">Para modificar ou remover o valor predefinido de uma chave de registo, especifique esta propriedade como uma cadeia vazia ao especificar também o ValueType ou ValueData.</span><span class="sxs-lookup"><span data-stu-id="5fa24-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying ValueType or ValueData.</span></span>|
| <span data-ttu-id="5fa24-117">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="5fa24-117">Ensure</span></span>| <span data-ttu-id="5fa24-118">Indica se a chave e valor existirem.</span><span class="sxs-lookup"><span data-stu-id="5fa24-118">Indicates if the key and value exist.</span></span> <span data-ttu-id="5fa24-119">Para garantir que eles fazem, defina esta propriedade para "Presente".</span><span class="sxs-lookup"><span data-stu-id="5fa24-119">To ensure that they do, set this property to "Present".</span></span> <span data-ttu-id="5fa24-120">Para garantir que não existam, defina a propriedade como "Ausente".</span><span class="sxs-lookup"><span data-stu-id="5fa24-120">To ensure that they do not exist, set the property to "Absent".</span></span> <span data-ttu-id="5fa24-121">O valor predefinido é "Presente".</span><span class="sxs-lookup"><span data-stu-id="5fa24-121">The default value is "Present".</span></span>|
| <span data-ttu-id="5fa24-122">Force</span><span class="sxs-lookup"><span data-stu-id="5fa24-122">Force</span></span>| <span data-ttu-id="5fa24-123">Se a chave de registo especificado estiver presente, **força** é substituído pelo novo valor.</span><span class="sxs-lookup"><span data-stu-id="5fa24-123">If the specified registry key is present, **Force** overwrites it with the new value.</span></span> <span data-ttu-id="5fa24-124">Se eliminar uma chave de registo com subchaves, esse processo precisa ser **$true**</span><span class="sxs-lookup"><span data-stu-id="5fa24-124">If deleting a registry key with subkeys, this needs to be **$true**</span></span> |
| <span data-ttu-id="5fa24-125">Hexadecimal</span><span class="sxs-lookup"><span data-stu-id="5fa24-125">Hex</span></span>| <span data-ttu-id="5fa24-126">Indica se os dados irão ser expressos em formato hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="5fa24-126">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="5fa24-127">Se for especificado, os dados do valor DWORD/QWORD são apresentados em formato hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="5fa24-127">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="5fa24-128">Não é válido para outros tipos.</span><span class="sxs-lookup"><span data-stu-id="5fa24-128">Not valid for other types.</span></span> <span data-ttu-id="5fa24-129">O valor predefinido é **$false**.</span><span class="sxs-lookup"><span data-stu-id="5fa24-129">The default value is **$false**.</span></span>|
| <span data-ttu-id="5fa24-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="5fa24-130">DependsOn</span></span>| <span data-ttu-id="5fa24-131">Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado.</span><span class="sxs-lookup"><span data-stu-id="5fa24-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="5fa24-132">Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será **ResourceName** e seu tipo é **ResourceType**, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="5fa24-132">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="5fa24-133">ValueData</span><span class="sxs-lookup"><span data-stu-id="5fa24-133">ValueData</span></span>| <span data-ttu-id="5fa24-134">Os dados para o valor de registo.</span><span class="sxs-lookup"><span data-stu-id="5fa24-134">The data for the registry value.</span></span>|
| <span data-ttu-id="5fa24-135">ValueType</span><span class="sxs-lookup"><span data-stu-id="5fa24-135">ValueType</span></span>| <span data-ttu-id="5fa24-136">Indica o tipo do valor.</span><span class="sxs-lookup"><span data-stu-id="5fa24-136">Indicates the type of the value.</span></span> <span data-ttu-id="5fa24-137">Os tipos suportados são: Cadeia (REG_SZ), o binário (REG binário), Dword de 32 bits (REG_DWORD), Qword 64-bit (REG_QWORD), cadeia de caracteres múltipla (REG_MULTI_SZ), (REG_EXPAND_SZ) de cadeia expansível</span><span class="sxs-lookup"><span data-stu-id="5fa24-137">The supported types are: String (REG_SZ), Binary (REG-BINARY), Dword 32-bit (REG_DWORD), Qword 64-bit (REG_QWORD), Multi-string (REG_MULTI_SZ), Expandable string (REG_EXPAND_SZ)</span></span> |

## <a name="example"></a><span data-ttu-id="5fa24-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5fa24-138">Example</span></span>

<span data-ttu-id="5fa24-139">Neste exemplo, garante que uma chave denominada "ExampleKey" está presente no **HKEY\_locais\_máquina** hive.</span><span class="sxs-lookup"><span data-stu-id="5fa24-139">This example ensures that a key named "ExampleKey" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

> [!NOTE]
> <span data-ttu-id="5fa24-140">Alterar uma definição de registo no `HKEY\CURRENT\USER` hive requer que a configuração seja executado com credenciais do usuário, em vez de como o sistema.</span><span class="sxs-lookup"><span data-stu-id="5fa24-140">Changing a registry setting in the `HKEY\CURRENT\USER` hive requires that the configuration runs with user credentials, rather than as the system.</span></span> <span data-ttu-id="5fa24-141">Pode utilizar o **PsDscRunAsCredential** propriedade para especificar as credenciais de utilizador para a configuração.</span><span class="sxs-lookup"><span data-stu-id="5fa24-141">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="5fa24-142">Por exemplo, veja [a executar o DSC com as credenciais de utilizador](../../../configurations/runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="5fa24-142">For an example, see [Running DSC with user credentials](../../../configurations/runAsUser.md).</span></span>
