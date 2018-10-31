---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Escrever a ajuda das configurações do DSC
ms.openlocfilehash: a4b5e688744b9a4519ce06d920ad8f11efeb99ad
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225697"
---
# <a name="writing-help-for-dsc-configurations"></a><span data-ttu-id="f6f93-103">Escrever a ajuda das configurações do DSC</span><span class="sxs-lookup"><span data-stu-id="f6f93-103">Writing help for DSC configurations</span></span>

><span data-ttu-id="f6f93-104">Aplica-se a: O Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f6f93-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="f6f93-105">Pode utilizar a ajuda baseada no comentário em configurações de DSC.</span><span class="sxs-lookup"><span data-stu-id="f6f93-105">You can use comment-based help in DSC configurations.</span></span> <span data-ttu-id="f6f93-106">Os usuários podem acessar a ajuda, chamando a função de configuração com `-?`, ou utilizando o [Get-Help](https://technet.microsoft.com/library/hh849696.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f6f93-106">Users can access the help by calling the configuration function with `-?`, or by using the [Get-Help](https://technet.microsoft.com/library/hh849696.aspx) cmdlet.</span></span> <span data-ttu-id="f6f93-107">Para obter mais informações sobre a ajuda de baseada no comentário do PowerShell, consulte [about_Comment_Based_Help](https://technet.microsoft.com/library/hh847834.aspx).</span><span class="sxs-lookup"><span data-stu-id="f6f93-107">For more information about PowerShell comment-based help, see [about_Comment_Based_Help](https://technet.microsoft.com/library/hh847834.aspx).</span></span>

<span data-ttu-id="f6f93-108">O exemplo seguinte mostra um script que contém uma configuração e a ajuda baseada no comentário para o mesmo:</span><span class="sxs-lookup"><span data-stu-id="f6f93-108">The following example shows a script that contains a configuration and comment-based help for it:</span></span>

```powershell
<#
.SYNOPSIS
A brief description of the function or script. This keyword can be used only once for each configuration.


.DESCRIPTION
A detailed description of the function or script. This keyword can be used only once for each configuration.


.PARAMETER ComputerName
The description of a parameter. Add a .PARAMETER keyword for each parameter in the function or script syntax.

Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter description on the lines following the .PARAMETER keyword.
Windows PowerShell interprets all text between the .PARAMETER line and the next keyword or the end of the comment block as part of the parameter description.
The description can include paragraph breaks.

The Parameter keywords can appear in any order in the comment block, but the function or script syntax determines the order in which the parameters
(and their descriptions) appear in help topic. To change the order, change the syntax.

.PARAMETER FilePath
Provide a PARAMETER section for each parameter that your script or function accepts.

.EXAMPLE
A sample command that uses the function or script, optionally followed by sample output and a description. Repeat this keyword for each example. If you have multiple examples,
there is no need to number them. PowerShell will number the examples in help text.

.EXAMPLE
This example will be labeled "EXAMPLE 2" when help is displayed to the user.
#>

configuration HelpSample1
{
    param([string]$ComputerName,[string]$FilePath)
    File f
    {
        Contents="Hello World"
        DestinationPath = "c:\Destination.txt"
    }
}
```

## <a name="viewing-configuration-help"></a><span data-ttu-id="f6f93-109">Ajuda da configuração de visualização</span><span class="sxs-lookup"><span data-stu-id="f6f93-109">Viewing configuration help</span></span>

<span data-ttu-id="f6f93-110">Para ver a ajuda para uma configuração, utilize o **Get-Help** o nome da função cmdlet com o nome da função ou tipo seguido `-?`.</span><span class="sxs-lookup"><span data-stu-id="f6f93-110">To view the help for a configuration, use the **Get-Help** cmdlet with the name of the function, or type the name of the function followed by `-?`.</span></span> <span data-ttu-id="f6f93-111">Segue-se a saída da função anterior quando transmitidos para **Get-Help**:</span><span class="sxs-lookup"><span data-stu-id="f6f93-111">The following is the output of the previous function when passed to **Get-Help**:</span></span>

```powershell
PS C:\> Get-Help HelpSample1

NAME
    HelpSample1

SYNOPSIS
    A brief description of the function or script. This keyword can be used only once for each configuration.


SYNTAX
    HelpSample1 [[-InstanceName] <String>] [[-DependsOn] <String[]>] [[-OutputPath] <String>] [[-ConfigurationData] <Hashtable>] [[-ComputerName]
    <String>] [[-FilePath] <String>] [<CommonParameters>]


DESCRIPTION
    A detailed description of the function or script. This keyword can be used only once for each configuration.


RELATED LINKS

REMARKS
    To see the examples, type: "get-help HelpSample1 -examples".
    For more information, type: "get-help HelpSample1 -detailed".
    For technical information, type: "get-help HelpSample1 -full".
```

## <a name="see-also"></a><span data-ttu-id="f6f93-112">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="f6f93-112">See Also</span></span>
* [<span data-ttu-id="f6f93-113">Configurações de DSC</span><span class="sxs-lookup"><span data-stu-id="f6f93-113">DSC Configurations</span></span>](configurations.md)