---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Utilizar dados de configuração
ms.openlocfilehash: d42c43fddb54050adcbac949e7f67f3b41b540f1
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="using-configuration-data-in-dsc"></a><span data-ttu-id="fbfc5-103">A utilização de dados de configuração DSC</span><span class="sxs-lookup"><span data-stu-id="fbfc5-103">Using configuration data in DSC</span></span>

><span data-ttu-id="fbfc5-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="fbfc5-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="fbfc5-105">Ao utilizar o DSC incorporada **ConfigurationData** parâmetro, pode definir os dados que podem ser utilizados dentro de uma configuração.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-105">By using the built-in DSC **ConfigurationData** parameter, you can define data that can be used within a configuration.</span></span>
<span data-ttu-id="fbfc5-106">Isto permite-lhe criar uma configuração única que pode ser utilizada para vários nós ou para os diferentes ambientes.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-106">This allows you to create a single configuration that can be used for multiple nodes or for different environments.</span></span>
<span data-ttu-id="fbfc5-107">Por exemplo, se estiver a desenvolver uma aplicação, pode utilizar uma configuração para ambientes de desenvolvimento e de produção e utilizar dados de configuração para especificar os dados para cada ambiente.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-107">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

<span data-ttu-id="fbfc5-108">Este tópico descreve a estrutura do **ConfigurationData** tabela hash.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-108">This topic describes the structure of the **ConfigurationData** hashtable.</span></span>
<span data-ttu-id="fbfc5-109">Para obter exemplos de como utilizar os dados de configuração, consulte [separação de dados de configuração e ambiente](separatingEnvData.md).</span><span class="sxs-lookup"><span data-stu-id="fbfc5-109">For examples of how to use configuration data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="the-configurationdata-common-parameter"></a><span data-ttu-id="fbfc5-110">O parâmetro comum de ConfigurationData</span><span class="sxs-lookup"><span data-stu-id="fbfc5-110">The ConfigurationData common parameter</span></span>

<span data-ttu-id="fbfc5-111">Uma configuração de DSC assume um parâmetro comum, **ConfigurationData**, que especifica quando compilar a configuração.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-111">A DSC configuration takes a common parameter, **ConfigurationData**, that you specify when you compile the configuration.</span></span>
<span data-ttu-id="fbfc5-112">Para obter informações sobre configurações de compilação, consulte [configurações de DSC](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="fbfc5-112">For information about compiling configurations, see [DSC configurations](configurations.md).</span></span>

<span data-ttu-id="fbfc5-113">O **ConfigurationData** parâmetro é uma hasthtable que têm de ter, pelo menos, uma chave denominada **AllNodes**.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-113">The **ConfigurationData** parameter is a hasthtable that must have at least one key named **AllNodes**.</span></span>
<span data-ttu-id="fbfc5-114">Também pode ter uma ou mais chaves.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-114">It can also have one or more other keys.</span></span>

><span data-ttu-id="fbfc5-115">**Nota:** os exemplos neste tópico utilizam uma única chave adicional (que não seja o nomeado **AllNodes** chave) com o nome `NonNodeData`, mas pode incluir qualquer número de chaves adicionais e nome que pretende.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-115">**Note:** The examples in this topic use a single additional key (other than the named **AllNodes** key) named `NonNodeData`, but you can include any number of additional keys, and name them whatever you want.</span></span>

```powershell
$MyData =
@{
    AllNodes = @()
    NonNodeData = ""
}
```

<span data-ttu-id="fbfc5-116">O valor da **AllNodes** chave é uma matriz.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-116">The value of the **AllNodes** key is an array.</span></span> <span data-ttu-id="fbfc5-117">Cada elemento da matriz deste também é uma tabela hash que têm de ter, pelo menos, uma chave denominada **NodeName**:</span><span class="sxs-lookup"><span data-stu-id="fbfc5-117">Each element of this array is also a hash table that must have at least one key named **NodeName**:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
        },


        @{
            NodeName = "VM-2"
        },


        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""
}
```

<span data-ttu-id="fbfc5-118">Pode adicionar outras chaves para cada tabela hash, bem como:</span><span class="sxs-lookup"><span data-stu-id="fbfc5-118">You can add other keys to each hash table as well:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
        },


        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },


        @{
            NodeName = "VM-3"
            Role     = "WebServer"
        }
    );

    NonNodeData = ""
}
```

<span data-ttu-id="fbfc5-119">Para aplicar uma propriedade a todos os nós, pode criar um membro do **AllNodes** matriz que tenha um **NodeName** de `*`.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-119">To apply a property to all nodes, you can create a member of the **AllNodes** array that has a **NodeName** of `*`.</span></span>
<span data-ttu-id="fbfc5-120">Por exemplo, para cada nó de dar um `LogPath` propriedade, pode efetuar este procedimento:</span><span class="sxs-lookup"><span data-stu-id="fbfc5-120">For example, to give every node a `LogPath` property, you could do this:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName     = "*"
            LogPath      = "C:\Logs"
        },


        @{
            NodeName     = "VM-1"
            Role         = "WebServer"
            SiteContents = "C:\Site1"
            SiteName     = "Website1"
        },


        @{
            NodeName     = "VM-2"
            Role         = "SQLServer"
        },


        @{
            NodeName     = "VM-3"
            Role         = "WebServer"
            SiteContents = "C:\Site2"
            SiteName     = "Website3"
        }
    );
}
```

<span data-ttu-id="fbfc5-121">Este é o equivalente da adição de uma propriedade com um nome de `LogPath` com um valor de `"C:\Logs"` para cada um dos outros blocos de (`VM-1`, `VM-2`, e `VM-3`).</span><span class="sxs-lookup"><span data-stu-id="fbfc5-121">This is the equivalent of adding a property with a name of `LogPath` with a value of `"C:\Logs"` to each of the other blocks (`VM-1`, `VM-2`, and `VM-3`).</span></span>

## <a name="defining-the-configurationdata-hashtable"></a><span data-ttu-id="fbfc5-122">Definir a tabela hash ConfigurationData</span><span class="sxs-lookup"><span data-stu-id="fbfc5-122">Defining the ConfigurationData hashtable</span></span>

<span data-ttu-id="fbfc5-123">Pode definir **ConfigurationData** como uma variável no mesmo ficheiro de script como um configuration (tal como nos nossos exemplos anteriores) ou um separado `.psd1` ficheiro.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-123">You can define **ConfigurationData** either as a variable within the same script file as a configuration (as in our previous examples) or in a separate `.psd1` file.</span></span>
<span data-ttu-id="fbfc5-124">Para definir **ConfigurationData** num `.psd1` de ficheiros, criar um ficheiro que contém apenas a tabela hash que representa os dados de configuração.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-124">To define **ConfigurationData** in a `.psd1` file, create a file that contains only the hashtable that represents the configuration data.</span></span>

<span data-ttu-id="fbfc5-125">Por exemplo, pode criar um ficheiro denominado `MyData.psd1` com o seguinte conteúdo:</span><span class="sxs-lookup"><span data-stu-id="fbfc5-125">For example, you could create a file named `MyData.psd1` with the following contents:</span></span>

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        },

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

## <a name="compiling-a-configuration-with-configuration-data"></a><span data-ttu-id="fbfc5-126">Compilar uma configuração com dados de configuração</span><span class="sxs-lookup"><span data-stu-id="fbfc5-126">Compiling a configuration with configuration data</span></span>

<span data-ttu-id="fbfc5-127">Para compilar uma configuração para o qual definiu os dados de configuração, transmitir os dados de configuração como o valor de **ConfigurationData** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-127">To compile a configuration for which you have defined configuration data, you pass the configuration data as the value of the **ConfigurationData** parameter.</span></span>

<span data-ttu-id="fbfc5-128">Esta ação irá criar um ficheiro MOF para cada entrada no **AllNodes** matriz.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-128">This will create a MOF file for each entry in the **AllNodes** array.</span></span>
<span data-ttu-id="fbfc5-129">Cada ficheiro MOF será nomeado com o `NodeName` propriedade da entrada de matriz correspondentes.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-129">Each MOF file will be named with the `NodeName` property of the corresponding array entry.</span></span>

<span data-ttu-id="fbfc5-130">Por exemplo, se definir dados de configuração como no `MyData.psd1` ficheiro acima, compilar uma configuração criaria ambos `VM-1.mof` e `VM-2.mof` ficheiros.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-130">For example, if you define configuration data as in the `MyData.psd1` file above, compiling a configuration would create both `VM-1.mof` and `VM-2.mof` files.</span></span>

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a><span data-ttu-id="fbfc5-131">Compilar uma configuração com os dados de configuração utilizando uma variável</span><span class="sxs-lookup"><span data-stu-id="fbfc5-131">Compiling a configuration with configuration data using a variable</span></span>

<span data-ttu-id="fbfc5-132">Para utilizar dados de configuração que estão definidos como uma variável na mesma `.ps1` ficheiros como a configuração, transmitir o nome da variável como o valor a **ConfigurationData** parâmetro ao compilar a configuração:</span><span class="sxs-lookup"><span data-stu-id="fbfc5-132">To use configuration data that is defined as a variable in the same `.ps1` file as the configuration, you pass the variable name as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a><span data-ttu-id="fbfc5-133">Compilar uma configuração com os dados de configuração através de um ficheiro de dados</span><span class="sxs-lookup"><span data-stu-id="fbfc5-133">Compiling a configuration with configuration data using a data file</span></span>

<span data-ttu-id="fbfc5-134">Para utilizar dados de configuração que estão definidos num ficheiro. psd1, passar o caminho e nome desse ficheiro como o valor de **ConfigurationData** parâmetro ao compilar a configuração:</span><span class="sxs-lookup"><span data-stu-id="fbfc5-134">To use configuration data that is defined in a .psd1 file, you pass the path and name of that file as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a><span data-ttu-id="fbfc5-135">Utilizar variáveis de ConfigurationData numa configuração</span><span class="sxs-lookup"><span data-stu-id="fbfc5-135">Using ConfigurationData variables in a configuration</span></span>

<span data-ttu-id="fbfc5-136">O DSC fornece três variáveis especiais que podem ser utilizadas um script de configuração: **$AllNodes**, **$Node**, e **$ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-136">DSC provides three special variables that can be used in a configuration script: **$AllNodes**, **$Node**, and **$ConfigurationData**.</span></span>

- <span data-ttu-id="fbfc5-137">**$AllNodes** refere-se para o conjunto completo de nós definido no **ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-137">**$AllNodes** refers to the entire collection of nodes defined in **ConfigurationData**.</span></span> <span data-ttu-id="fbfc5-138">Pode filtrar o **AllNodes** coleção utilizando **. WHERE()** e **. ForEach()**.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-138">You can filter the **AllNodes** collection by using **.Where()** and **.ForEach()**.</span></span>
- <span data-ttu-id="fbfc5-139">**Nó** refere-se a uma entrada específico no **AllNodes** coleção depois-é filtrado utilizando **. WHERE()** ou **. ForEach()**.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-139">**Node** refers to a particular entry in the **AllNodes** collection after it is filtered by using **.Where()** or **.ForEach()**.</span></span>
- <span data-ttu-id="fbfc5-140">**ConfigurationData** refere-se a tabela hash completo que é transmitida como o parâmetro ao compilar uma configuração.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-140">**ConfigurationData** refers to the entire hash table that is passed as the parameter when compiling a configuration.</span></span>

## <a name="using-non-node-data"></a><span data-ttu-id="fbfc5-141">Utilização de dados do nó não</span><span class="sxs-lookup"><span data-stu-id="fbfc5-141">Using non-node data</span></span>

<span data-ttu-id="fbfc5-142">Como podemos viu nos exemplos anteriores, o **ConfigurationData** tabela hash pode ter uma ou mais chaves para além de necessários **AllNodes** chave.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-142">As we've seen in previous examples, the **ConfigurationData** hashtable can have one or more keys in addition to the required **AllNodes** key.</span></span>
<span data-ttu-id="fbfc5-143">Nos exemplos neste tópico, podemos ter utilizado apenas um único nó adicional e com o mesmo nome `NonNodeData`.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-143">In the examples in this topic, we have used only a single additional node, and named it `NonNodeData`.</span></span>
<span data-ttu-id="fbfc5-144">No entanto, pode definir qualquer número de chaves adicionais e nome tudo o que pretende.</span><span class="sxs-lookup"><span data-stu-id="fbfc5-144">However, you can define any number of additional keys, and name them anything you want.</span></span>

<span data-ttu-id="fbfc5-145">Para obter um exemplo de utilização de dados do nó não, consulte [separação de dados de configuração e ambiente](separatingEnvData.md).</span><span class="sxs-lookup"><span data-stu-id="fbfc5-145">For an example of using non-node data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fbfc5-146">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="fbfc5-146">See Also</span></span>
- [<span data-ttu-id="fbfc5-147">Opções de credenciais nos dados de configuração</span><span class="sxs-lookup"><span data-stu-id="fbfc5-147">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="fbfc5-148">Configurações de DSC</span><span class="sxs-lookup"><span data-stu-id="fbfc5-148">DSC Configurations</span></span>](configurations.md)