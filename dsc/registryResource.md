---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Recursos de registo DSC
ms.openlocfilehash: 8819b3704fa1a61d2be5ce11c974542f48177e09
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-registry-resource"></a><span data-ttu-id="a6a11-103">Recursos de registo DSC</span><span class="sxs-lookup"><span data-stu-id="a6a11-103">DSC Registry Resource</span></span>

> <span data-ttu-id="a6a11-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a6a11-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="a6a11-105">O **registo** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para gerir as chaves de registo e valores num nó de destino.</span><span class="sxs-lookup"><span data-stu-id="a6a11-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="a6a11-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a6a11-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="a6a11-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="a6a11-107">Properties</span></span>
|  <span data-ttu-id="a6a11-108">Propriedade</span><span class="sxs-lookup"><span data-stu-id="a6a11-108">Property</span></span>  |  <span data-ttu-id="a6a11-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6a11-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="a6a11-110">Tecla</span><span class="sxs-lookup"><span data-stu-id="a6a11-110">Key</span></span>| <span data-ttu-id="a6a11-111">Indica o caminho da chave do registo para o qual pretende garantir um estado específico.</span><span class="sxs-lookup"><span data-stu-id="a6a11-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="a6a11-112">Este caminho tem de incluir o ramo de registo.</span><span class="sxs-lookup"><span data-stu-id="a6a11-112">This path must include the hive.</span></span>|
| <span data-ttu-id="a6a11-113">ValueName</span><span class="sxs-lookup"><span data-stu-id="a6a11-113">ValueName</span></span>| <span data-ttu-id="a6a11-114">Indica o nome do valor de registo.</span><span class="sxs-lookup"><span data-stu-id="a6a11-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="a6a11-115">Para adicionar ou remover uma chave de registo, especificar esta propriedade como uma cadeia vazia sem a especificação ValueType ou ValueData.</span><span class="sxs-lookup"><span data-stu-id="a6a11-115">To add or remove a registry key, specify this property as an empty string without specifying ValueType or ValueData.</span></span> <span data-ttu-id="a6a11-116">Para modificar ou remover o valor predefinido de uma chave de registo, ao especificar também um ValueType ou ValueData de especificar esta propriedade como uma cadeia vazia.</span><span class="sxs-lookup"><span data-stu-id="a6a11-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying ValueType or ValueData.</span></span>|
| <span data-ttu-id="a6a11-117">Certifique-se</span><span class="sxs-lookup"><span data-stu-id="a6a11-117">Ensure</span></span>| <span data-ttu-id="a6a11-118">Indica se a chave e valor existem.</span><span class="sxs-lookup"><span data-stu-id="a6a11-118">Indicates if the key and value exist.</span></span> <span data-ttu-id="a6a11-119">Para garantir que fazem, defina esta propriedade para "Presente".</span><span class="sxs-lookup"><span data-stu-id="a6a11-119">To ensure that they do, set this property to "Present".</span></span> <span data-ttu-id="a6a11-120">Para garantir que estes não existirem, defina a propriedade "Ausente".</span><span class="sxs-lookup"><span data-stu-id="a6a11-120">To ensure that they do not exist, set the property to "Absent".</span></span> <span data-ttu-id="a6a11-121">O valor predefinido é "Presente".</span><span class="sxs-lookup"><span data-stu-id="a6a11-121">The default value is "Present".</span></span>|
| <span data-ttu-id="a6a11-122">Force</span><span class="sxs-lookup"><span data-stu-id="a6a11-122">Force</span></span>| <span data-ttu-id="a6a11-123">Se a chave de registo especificado estiver presente, __Force__ substitui-lo com o novo valor.</span><span class="sxs-lookup"><span data-stu-id="a6a11-123">If the specified registry key is present, __Force__ overwrites it with the new value.</span></span> <span data-ttu-id="a6a11-124">Se eliminar uma chave de registo com subchaves, este tem de ser __$true__</span><span class="sxs-lookup"><span data-stu-id="a6a11-124">If deleting a registry key with subkeys, this needs to be __$true__</span></span>|
| <span data-ttu-id="a6a11-125">Hexadecimal</span><span class="sxs-lookup"><span data-stu-id="a6a11-125">Hex</span></span>| <span data-ttu-id="a6a11-126">Indica se os dados irão ser expressos numa formato hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="a6a11-126">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="a6a11-127">Se for especificado, os dados do valor DWORD/QWORD são apresentados no formato hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="a6a11-127">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="a6a11-128">Não é válido para outros tipos.</span><span class="sxs-lookup"><span data-stu-id="a6a11-128">Not valid for other types.</span></span> <span data-ttu-id="a6a11-129">O valor predefinido é __$false__.</span><span class="sxs-lookup"><span data-stu-id="a6a11-129">The default value is __$false__.</span></span>|
| <span data-ttu-id="a6a11-130">dependsOn</span><span class="sxs-lookup"><span data-stu-id="a6a11-130">DependsOn</span></span>| <span data-ttu-id="a6a11-131">Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado.</span><span class="sxs-lookup"><span data-stu-id="a6a11-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a6a11-132">Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="a6a11-132">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="a6a11-133">ValueData</span><span class="sxs-lookup"><span data-stu-id="a6a11-133">ValueData</span></span>| <span data-ttu-id="a6a11-134">Os dados para o valor de registo.</span><span class="sxs-lookup"><span data-stu-id="a6a11-134">The data for the registry value.</span></span>|
| <span data-ttu-id="a6a11-135">ValueType</span><span class="sxs-lookup"><span data-stu-id="a6a11-135">ValueType</span></span>| <span data-ttu-id="a6a11-136">Indica o tipo do valor.</span><span class="sxs-lookup"><span data-stu-id="a6a11-136">Indicates the type of the value.</span></span> <span data-ttu-id="a6a11-137">Os tipos suportados são:</span><span class="sxs-lookup"><span data-stu-id="a6a11-137">The supported types are:</span></span>
<ul><li><span data-ttu-id="a6a11-138">Cadeia (REG_SZ)</span><span class="sxs-lookup"><span data-stu-id="a6a11-138">String (REG_SZ)</span></span></li>


<li><span data-ttu-id="a6a11-139">Binário (REG binário)</span><span class="sxs-lookup"><span data-stu-id="a6a11-139">Binary (REG-BINARY)</span></span></li>


<li><span data-ttu-id="a6a11-140">DWORD 32 bits (REG_DWORD)</span><span class="sxs-lookup"><span data-stu-id="a6a11-140">Dword 32-bit (REG_DWORD)</span></span></li>


<li><span data-ttu-id="a6a11-141">QWORD 64-bit (REG_QWORD)</span><span class="sxs-lookup"><span data-stu-id="a6a11-141">Qword 64-bit (REG_QWORD)</span></span></li>


<li><span data-ttu-id="a6a11-142">Cadeia múltipla (REG_MULTI_SZ)</span><span class="sxs-lookup"><span data-stu-id="a6a11-142">Multi-string (REG_MULTI_SZ)</span></span></li>


<li><span data-ttu-id="a6a11-143">Cadeia expansível (REG_EXPAND_SZ)</span><span class="sxs-lookup"><span data-stu-id="a6a11-143">Expandable string (REG_EXPAND_SZ)</span></span></li></ul>

## <a name="example"></a><span data-ttu-id="a6a11-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a6a11-144">Example</span></span>
<span data-ttu-id="a6a11-145">Neste exemplo garante que uma chave denominada "ExampleKey" está presente no **HKEY\_LOCAL\_máquina** ramo de registo.</span><span class="sxs-lookup"><span data-stu-id="a6a11-145">This example ensures that a key named "ExampleKey" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>
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

><span data-ttu-id="a6a11-146">**Nota:** alterar uma definição de registo no **HKEY\_atual\_utilizador** hive requer que a configuração é executada com as credenciais de utilizador, em vez do sistema.</span><span class="sxs-lookup"><span data-stu-id="a6a11-146">**Note:** Changing a registry setting in the **HKEY\_CURRENT\_USER** hive requires that the configuration runs with user credentials, rather than as the system.</span></span>
><span data-ttu-id="a6a11-147">Pode utilizar o **PsDscRunAsCredential** propriedade para especificar as credenciais de utilizador para a configuração.</span><span class="sxs-lookup"><span data-stu-id="a6a11-147">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="a6a11-148">Por exemplo, consulte [DSC em execução com as credenciais do utilizador](runAsUser.md)</span><span class="sxs-lookup"><span data-stu-id="a6a11-148">For an example, see [Running DSC with user credentials](runAsUser.md)</span></span>
