---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Utilizar dados de configuração
ms.openlocfilehash: f2d25b9ced805fb4c91378ebfe840104eb6ce52a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404857"
---
# <a name="using-configuration-data-in-dsc"></a><span data-ttu-id="7830a-103">Utilizar os dados de configuração no DSC</span><span class="sxs-lookup"><span data-stu-id="7830a-103">Using configuration data in DSC</span></span>

> <span data-ttu-id="7830a-104">Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7830a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="7830a-105">Ao utilizar o DSC incorporada **ConfigurationData** parâmetro, pode definir os dados que podem ser utilizados dentro de uma configuração.</span><span class="sxs-lookup"><span data-stu-id="7830a-105">By using the built-in DSC **ConfigurationData** parameter, you can define data that can be used within a configuration.</span></span>
<span data-ttu-id="7830a-106">Isto permite-lhe criar uma configuração única que pode ser utilizada para vários nós ou para ambientes diferentes.</span><span class="sxs-lookup"><span data-stu-id="7830a-106">This allows you to create a single configuration that can be used for multiple nodes or for different environments.</span></span>
<span data-ttu-id="7830a-107">Por exemplo, se estiver a desenvolver uma aplicação, pode utilizar uma configuração para ambientes de desenvolvimento e produção e utilizar dados de configuração para especificar os dados para cada ambiente.</span><span class="sxs-lookup"><span data-stu-id="7830a-107">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

<span data-ttu-id="7830a-108">Este tópico descreve a estrutura do **ConfigurationData** hashtable.</span><span class="sxs-lookup"><span data-stu-id="7830a-108">This topic describes the structure of the **ConfigurationData** hashtable.</span></span>
<span data-ttu-id="7830a-109">Para obter exemplos de como utilizar os dados de configuração, consulte [separação de dados de configuração e ambiente](separatingEnvData.md).</span><span class="sxs-lookup"><span data-stu-id="7830a-109">For examples of how to use configuration data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="the-configurationdata-common-parameter"></a><span data-ttu-id="7830a-110">O parâmetro comum de ConfigurationData</span><span class="sxs-lookup"><span data-stu-id="7830a-110">The ConfigurationData common parameter</span></span>

<span data-ttu-id="7830a-111">Uma configuração de DSC assume um parâmetro comum, **ConfigurationData**, que especifica quando compilar a configuração.</span><span class="sxs-lookup"><span data-stu-id="7830a-111">A DSC configuration takes a common parameter, **ConfigurationData**, that you specify when you compile the configuration.</span></span>
<span data-ttu-id="7830a-112">Para obter informações sobre como compilar configurações, consulte [configurações de DSC](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="7830a-112">For information about compiling configurations, see [DSC configurations](configurations.md).</span></span>

<span data-ttu-id="7830a-113">O **ConfigurationData** parâmetro é uma tabela de hash tem de ter pelo menos uma chave denominada **AllNodes**.</span><span class="sxs-lookup"><span data-stu-id="7830a-113">The **ConfigurationData** parameter is a hashtable that must have at least one key named **AllNodes**.</span></span>
<span data-ttu-id="7830a-114">Ele também pode ter uma ou mais chaves.</span><span class="sxs-lookup"><span data-stu-id="7830a-114">It can also have one or more other keys.</span></span>

> [!NOTE]
> <span data-ttu-id="7830a-115">Os exemplos neste tópico utilizam uma única chave adicional (que não seja o nomeado **AllNodes** chave) com o nome `NonNodeData`, mas pode incluir qualquer número de chaves adicionais e nomeá-los que quiser.</span><span class="sxs-lookup"><span data-stu-id="7830a-115">The examples in this topic use a single additional key (other than the named **AllNodes** key) named `NonNodeData`, but you can include any number of additional keys, and name them whatever you want.</span></span>

```powershell
$MyData =
@{
    AllNodes = @()
    NonNodeData = ""
}
```

<span data-ttu-id="7830a-116">O valor do **AllNodes** chave é uma matriz.</span><span class="sxs-lookup"><span data-stu-id="7830a-116">The value of the **AllNodes** key is an array.</span></span> <span data-ttu-id="7830a-117">Cada elemento dessa matriz também é uma tabela de hash que tem de ter pelo menos uma chave com o nome **NodeName**:</span><span class="sxs-lookup"><span data-stu-id="7830a-117">Each element of this array is also a hash table that must have at least one key named **NodeName**:</span></span>

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

<span data-ttu-id="7830a-118">Pode adicionar outras chaves para cada tabela de hash também:</span><span class="sxs-lookup"><span data-stu-id="7830a-118">You can add other keys to each hash table as well:</span></span>

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

<span data-ttu-id="7830a-119">Para aplicar uma propriedade a todos os nós, pode criar um membro do **AllNodes** matriz que tenha um **NodeName** de `*`.</span><span class="sxs-lookup"><span data-stu-id="7830a-119">To apply a property to all nodes, you can create a member of the **AllNodes** array that has a **NodeName** of `*`.</span></span>
<span data-ttu-id="7830a-120">Por exemplo, para dar a cada nó um `LogPath` propriedade, pode fazer isso:</span><span class="sxs-lookup"><span data-stu-id="7830a-120">For example, to give every node a `LogPath` property, you could do this:</span></span>

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

<span data-ttu-id="7830a-121">Isso é o equivalente da adição de uma propriedade com o nome `LogPath` com um valor de `"C:\Logs"` a cada um dos outros blocos de (`VM-1`, `VM-2`, e `VM-3`).</span><span class="sxs-lookup"><span data-stu-id="7830a-121">This is the equivalent of adding a property with a name of `LogPath` with a value of `"C:\Logs"` to each of the other blocks (`VM-1`, `VM-2`, and `VM-3`).</span></span>

## <a name="defining-the-configurationdata-hashtable"></a><span data-ttu-id="7830a-122">Definir a tabela de hash de ConfigurationData</span><span class="sxs-lookup"><span data-stu-id="7830a-122">Defining the ConfigurationData hashtable</span></span>

<span data-ttu-id="7830a-123">Pode definir **ConfigurationData** como uma variável dentro do mesmo arquivo de script como uma configuração (tal como nos nossos exemplos anteriores) ou num separado `.psd1` ficheiro.</span><span class="sxs-lookup"><span data-stu-id="7830a-123">You can define **ConfigurationData** either as a variable within the same script file as a configuration (as in our previous examples) or in a separate `.psd1` file.</span></span>
<span data-ttu-id="7830a-124">Para definir **ConfigurationData** num `.psd1` de ficheiros, crie um ficheiro que contém apenas a tabela de hash que representa os dados de configuração.</span><span class="sxs-lookup"><span data-stu-id="7830a-124">To define **ConfigurationData** in a `.psd1` file, create a file that contains only the hashtable that represents the configuration data.</span></span>

<span data-ttu-id="7830a-125">Por exemplo, pode criar um arquivo chamado `MyData.psd1` com o seguinte conteúdo:</span><span class="sxs-lookup"><span data-stu-id="7830a-125">For example, you could create a file named `MyData.psd1` with the following contents:</span></span>

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

## <a name="compiling-a-configuration-with-configuration-data"></a><span data-ttu-id="7830a-126">Compilar uma configuração com dados de configuração</span><span class="sxs-lookup"><span data-stu-id="7830a-126">Compiling a configuration with configuration data</span></span>

<span data-ttu-id="7830a-127">Para compilar uma configuração para o qual definiu dados de configuração, tem de transmitir os dados de configuração como o valor do **ConfigurationData** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7830a-127">To compile a configuration for which you have defined configuration data, you pass the configuration data as the value of the **ConfigurationData** parameter.</span></span>

<span data-ttu-id="7830a-128">Esta ação irá criar um ficheiro MOF para cada entrada o **AllNodes** matriz.</span><span class="sxs-lookup"><span data-stu-id="7830a-128">This will create a MOF file for each entry in the **AllNodes** array.</span></span>
<span data-ttu-id="7830a-129">Cada ficheiro MOF será nomeado com o `NodeName` propriedade de entrada de matriz correspondentes.</span><span class="sxs-lookup"><span data-stu-id="7830a-129">Each MOF file will be named with the `NodeName` property of the corresponding array entry.</span></span>

<span data-ttu-id="7830a-130">Por exemplo, se definir dados de configuração, como mostra a `MyData.psd1` ficheiro acima, compilar uma configuração criaria ambos `VM-1.mof` e `VM-2.mof` ficheiros.</span><span class="sxs-lookup"><span data-stu-id="7830a-130">For example, if you define configuration data as in the `MyData.psd1` file above, compiling a configuration would create both `VM-1.mof` and `VM-2.mof` files.</span></span>

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a><span data-ttu-id="7830a-131">Compilar uma configuração com os dados de configuração usando uma variável</span><span class="sxs-lookup"><span data-stu-id="7830a-131">Compiling a configuration with configuration data using a variable</span></span>

<span data-ttu-id="7830a-132">Utilizar dados de configuração que estão definidos como uma variável no mesmo `.ps1` ficheiro como a configuração, passa o nome da variável como o valor do **ConfigurationData** parâmetro ao compilar a configuração:</span><span class="sxs-lookup"><span data-stu-id="7830a-132">To use configuration data that is defined as a variable in the same `.ps1` file as the configuration, you pass the variable name as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a><span data-ttu-id="7830a-133">Compilar uma configuração com os dados de configuração através de um ficheiro de dados</span><span class="sxs-lookup"><span data-stu-id="7830a-133">Compiling a configuration with configuration data using a data file</span></span>

<span data-ttu-id="7830a-134">Para utilizar dados de configuração que são definidos num ficheiro. psd1, passe o caminho e nome de arquivo como o valor do **ConfigurationData** parâmetro ao compilar a configuração:</span><span class="sxs-lookup"><span data-stu-id="7830a-134">To use configuration data that is defined in a .psd1 file, you pass the path and name of that file as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a><span data-ttu-id="7830a-135">Usando variáveis de ConfigurationData numa configuração</span><span class="sxs-lookup"><span data-stu-id="7830a-135">Using ConfigurationData variables in a configuration</span></span>

<span data-ttu-id="7830a-136">DSC fornece as seguintes variáveis especiais que podem ser usadas num script de configuração:</span><span class="sxs-lookup"><span data-stu-id="7830a-136">DSC provides the following special variables that can be used in a configuration script:</span></span>

- <span data-ttu-id="7830a-137">**$AllNodes** refere-se a toda a coleção de nós definida no **ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="7830a-137">**$AllNodes** refers to the entire collection of nodes defined in **ConfigurationData**.</span></span> <span data-ttu-id="7830a-138">Pode filtrar os **AllNodes** coleção utilizando **. WHERE()** e **. Foreach ()**.</span><span class="sxs-lookup"><span data-stu-id="7830a-138">You can filter the **AllNodes** collection by using **.Where()** and **.ForEach()**.</span></span>
- <span data-ttu-id="7830a-139">**ConfigurationData** refere-se a tabela de hash de inteiro que é passada como parâmetro ao compilar uma configuração.</span><span class="sxs-lookup"><span data-stu-id="7830a-139">**ConfigurationData** refers to the entire hash table that is passed as the parameter when compiling a configuration.</span></span>
- <span data-ttu-id="7830a-140">**MyTypeName** contém o [configuração](configurations.md) nome de variável é utilizado.</span><span class="sxs-lookup"><span data-stu-id="7830a-140">**MyTypeName** contains the [configuration](configurations.md) name the variable is used in.</span></span> <span data-ttu-id="7830a-141">Por exemplo, na configuração do `MyDscConfiguration`, o `$MyTypeName` terá um valor de `MyDscConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="7830a-141">For example, in the configuration `MyDscConfiguration`, the `$MyTypeName` will have a value of `MyDscConfiguration`.</span></span>
- <span data-ttu-id="7830a-142">**Nó** refere-se para uma entrada no **AllNodes** coleção depois que ele é filtrado através da utilização **. WHERE()** ou **. Foreach ()**.</span><span class="sxs-lookup"><span data-stu-id="7830a-142">**Node** refers to a particular entry in the **AllNodes** collection after it is filtered by using **.Where()** or **.ForEach()**.</span></span>
  - <span data-ttu-id="7830a-143">Pode ler mais sobre estes métodos em [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)</span><span class="sxs-lookup"><span data-stu-id="7830a-143">You can read more about these methods in [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)</span></span>

## <a name="using-non-node-data"></a><span data-ttu-id="7830a-144">Utilizar os dados de nós não</span><span class="sxs-lookup"><span data-stu-id="7830a-144">Using non-node data</span></span>

<span data-ttu-id="7830a-145">Como vimos nos exemplos anteriores, o **ConfigurationData** hashtable pode ter uma ou mais chaves para além do necessário **AllNodes** chave.</span><span class="sxs-lookup"><span data-stu-id="7830a-145">As we've seen in previous examples, the **ConfigurationData** hashtable can have one or more keys in addition to the required **AllNodes** key.</span></span>
<span data-ttu-id="7830a-146">Nos exemplos neste tópico, temos usado apenas um único nó adicional e o nome de `NonNodeData`.</span><span class="sxs-lookup"><span data-stu-id="7830a-146">In the examples in this topic, we have used only a single additional node, and named it `NonNodeData`.</span></span>
<span data-ttu-id="7830a-147">No entanto, pode definir qualquer número de chaves adicionais e nomeá-los que quiser.</span><span class="sxs-lookup"><span data-stu-id="7830a-147">However, you can define any number of additional keys, and name them anything you want.</span></span>

<span data-ttu-id="7830a-148">Para obter um exemplo da utilização de dados não-nó, veja [separação de dados de configuração e ambiente](separatingEnvData.md).</span><span class="sxs-lookup"><span data-stu-id="7830a-148">For an example of using non-node data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7830a-149">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="7830a-149">See Also</span></span>

- [<span data-ttu-id="7830a-150">Opções de credenciais nos dados de configuração</span><span class="sxs-lookup"><span data-stu-id="7830a-150">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="7830a-151">Configurações de DSC</span><span class="sxs-lookup"><span data-stu-id="7830a-151">DSC Configurations</span></span>](configurations.md)