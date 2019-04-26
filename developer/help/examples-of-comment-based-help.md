---
title: Exemplos de ajuda baseada no comentário | Documentos da Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 868194a2-17e9-4184-bc36-c04a33f26494
caps.latest.revision: 4
ms.openlocfilehash: 30e98bfcf06b1720005a73ee8294aeba7e1ae066
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083506"
---
# <a name="examples-of-comment-based-help"></a><span data-ttu-id="b9cdd-102">Examples of Comment-Based Help (Exemplos de Ajuda Baseada em Comentários)</span><span class="sxs-lookup"><span data-stu-id="b9cdd-102">Examples of Comment-Based Help</span></span>

<span data-ttu-id="b9cdd-103">Este tópico inclui o exemplo que demonstram como utilizar a ajuda baseada no comentário para scripts e funções.</span><span class="sxs-lookup"><span data-stu-id="b9cdd-103">This topic includes example that demonstrate how to use comment-based help for scripts and functions.</span></span>

## <a name="example-1-comment-based-help-for-a-function"></a><span data-ttu-id="b9cdd-104">Exemplo 1: Ajuda baseada no comentário para uma função</span><span class="sxs-lookup"><span data-stu-id="b9cdd-104">Example 1: Comment-Based Help for a Function</span></span>

 <span data-ttu-id="b9cdd-105">A seguinte função de exemplo inclui ajuda baseada no comentário.</span><span class="sxs-lookup"><span data-stu-id="b9cdd-105">The following sample function includes comment-based Help.</span></span>

```powershell
function Add-Extension
{
    param ([string]$Name,[string]$Extension = "txt")
    $name = $name + "." + $extension
    $name

    <#
        .SYNOPSIS
        Adds a file name extension to a supplied name.

        .DESCRIPTION
        Adds a file name extension to a supplied name.
        Takes any strings for the file name or extension.

        .PARAMETER Name
        Specifies the file name.

        .PARAMETER Extension
        Specifies the extension. "Txt" is the default.

        .INPUTS
        None. You cannot pipe objects to Add-Extension.

        .OUTPUTS
        System.String. Add-Extension returns a string with the extension or file name.

        .EXAMPLE
        C:\PS> extension -name "File"
        File.txt

        .EXAMPLE
        C:\PS> extension -name "File" -extension "doc"
        File.doc

        .EXAMPLE
        C:\PS> extension "File" "doc"
        File.doc

        .LINK
        Online version: http://www.fabrikam.com/extension.html

        .LINK
        Set-Item
    #>
}
```

<span data-ttu-id="b9cdd-106">O resultado seguinte mostra os resultados de um comando Get-Help, que apresenta a ajuda para a função de adicionar a extensão.</span><span class="sxs-lookup"><span data-stu-id="b9cdd-106">The following output shows the results of a Get-Help command that displays the help for the Add-Extension function.</span></span>

```powershell
C:\PS> get-help add-extension -full
```

```output
        NAME
            Add-Extension

        SYNOPSIS
            Adds a file name extension to a supplied name.

        SYNTAX
            Add-Extension [[-Name] <String>] [[-Extension] <String>] [<CommonParameters>]

        DESCRIPTION
            Adds a file name extension to a supplied name. Takes any strings for the file name or extension.

        PARAMETERS
           -Name
               Specifies the file name.

               Required?                    false
               Position?                    0
               Default value
               Accept pipeline input?       false
               Accept wildcard characters?

           -Extension
               Specifies the extension. "Txt" is the default.

               Required?                    false
               Position?                    1
               Default value
               Accept pipeline input?       false
               Accept wildcard characters?

            <CommonParameters>
               This cmdlet supports the common parameters: -Verbose, -Debug,
               -ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
               -OutBuffer and -OutVariable. For more information, type
               "get-help about_commonparameters".

        INPUTS
            None. You cannot pipe objects to Add-Extension.

        OUTPUTS
            System.String. Add-Extension returns a string with the extension or file name.

            -------------------------- EXAMPLE 1 --------------------------

            C:\PS> extension -name "File"
            File.txt

            -------------------------- EXAMPLE 2 --------------------------

            C:\PS> extension -name "File" -extension "doc"
            File.doc

            -------------------------- EXAMPLE 3 --------------------------

            C:\PS> extension "File" "doc"
            File.doc

        RELATED LINKS
            Online version: http://www.fabrikam.com/extension.html
            Set-Item
```

## <a name="example-2-comment-based-help-for-a-script"></a><span data-ttu-id="b9cdd-107">Exemplo 2: Baseada no comentário ajuda para obter um Script</span><span class="sxs-lookup"><span data-stu-id="b9cdd-107">Example 2: Comment-Based Help for a Script</span></span>

<span data-ttu-id="b9cdd-108">A seguinte função de exemplo inclui ajuda baseada no comentário.</span><span class="sxs-lookup"><span data-stu-id="b9cdd-108">The following sample function includes comment-based Help.</span></span>

<span data-ttu-id="b9cdd-109">Tenha em atenção as linhas em branco entre o fecho **#>** e o `Param` instrução.</span><span class="sxs-lookup"><span data-stu-id="b9cdd-109">Notice the blank lines between the closing **#>** and the `Param` statement.</span></span> <span data-ttu-id="b9cdd-110">Num script que não tenha um `Param` instrução, tem de existir pelo menos duas linhas em branco entre o comentário final no tópico de ajuda e a primeira declaração de função.</span><span class="sxs-lookup"><span data-stu-id="b9cdd-110">In a script that does not have a `Param` statement, there must be at least two blank lines between the final comment in the Help topic and the first function declaration.</span></span> <span data-ttu-id="b9cdd-111">Sem essas linhas em branco, o Get-Help associa o tópico de ajuda com a função, em vez do script.</span><span class="sxs-lookup"><span data-stu-id="b9cdd-111">Without these blank lines, Get-Help associates the Help topic with the function, instead of the script.</span></span>

```powershell
<#
  .SYNOPSIS
  Performs monthly data updates.

  .DESCRIPTION
  The Update-Month.ps1 script updates the registry with new data generated
  during the past month and generates a report.

  .PARAMETER InputPath
  Specifies the path to the CSV-based input file.

  .PARAMETER OutputPath
  Specifies the name and path for the CSV-based output file. By default,
  MonthlyUpdates.ps1 generates a name from the date and time it runs, and
  saves the output in the local directory.

  .INPUTS
  None. You cannot pipe objects to Update-Month.ps1.

  .OUTPUTS
  None. Update-Month.ps1 does not generate any output.

  .EXAMPLE
  C:\PS> .\Update-Month.ps1

  .EXAMPLE
  C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

  .EXAMPLE
  C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath C:\Reports\2009\January.csv
#>

param ([string]$InputPath, [string]$OutPutPath)

function Get-Data { }
```

<span data-ttu-id="b9cdd-112">O comando seguinte obtém o script ajuda.</span><span class="sxs-lookup"><span data-stu-id="b9cdd-112">The following command gets the script Help.</span></span> <span data-ttu-id="b9cdd-113">Uma vez que o script não é n um diretório que está listado na variável de ambiente Path, o comando Get-Help, que obtém o ajuda de script tem de especificar o caminho do script.</span><span class="sxs-lookup"><span data-stu-id="b9cdd-113">Because the script is not n a directory that is listed in the Path environment variable, the Get-Help command that gets the script Help must specify the script path.</span></span>

```powershell
C:\PS> get-help c:\ps-test\update-month.ps1 -full
```

```output
            NAME
                C:\ps-test\Update-Month.ps1

            SYNOPSIS
                Performs monthly data updates.

            SYNTAX
                C:\ps-test\Update-Month.ps1 [-InputPath] <String> [[-OutputPath]
                <String>] [<CommonParameters>]

            DESCRIPTION
                The Update-Month.ps1 script updates the registry with new data
                generated during the past month and generates a report.

            PARAMETERS
               -InputPath
                   Specifies the path to the CSV-based input file.

                   Required?                    true
                   Position?                    0
                   Default value
                   Accept pipeline input?       false
                   Accept wildcard characters?

               -OutputPath
                   Specifies the name and path for the CSV-based output file. By
                   default, MonthlyUpdates.ps1 generates a name from the date
                   and time it runs, and saves the output in the local directory.

                   Required?                    false
                   Position?                    1
                   Default value
                   Accept pipeline input?       false
                   Accept wildcard characters?

               <CommonParameters>
                   This cmdlet supports the common parameters: -Verbose, -Debug,
                   -ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
                   -OutBuffer and -OutVariable. For more information, type,
                   "get-help about_commonparameters".

            INPUTS
                   None. You cannot pipe objects to Update-Month.ps1.

            OUTPUTS
                   None. Update-Month.ps1 does not generate any output.

            -------------------------- EXAMPLE 1 --------------------------

            C:\PS> .\Update-Month.ps1

            -------------------------- EXAMPLE 2 --------------------------

            C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

            -------------------------- EXAMPLE 3 --------------------------

            C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath
            C:\Reports\2009\January.csv

            RELATED LINKS
```

## <a name="example-3-parameter-descriptions-in-a-param-statement"></a><span data-ttu-id="b9cdd-114">Exemplo 3: Descrições de parâmetros numa instrução Param</span><span class="sxs-lookup"><span data-stu-id="b9cdd-114">Example 3: Parameter Descriptions in a Param Statement</span></span>

<span data-ttu-id="b9cdd-115">Este exemplo mostra como inserir parameterdescriptions no `Param` declaração do Estado de uma função ou script.</span><span class="sxs-lookup"><span data-stu-id="b9cdd-115">This example show how to insert parameterdescriptions in the `Param` statement of a function or script.</span></span> <span data-ttu-id="b9cdd-116">Este formato é mais útil quando as descrições de parâmetro são breves.</span><span class="sxs-lookup"><span data-stu-id="b9cdd-116">This format is most useful when the parameter descriptions are brief.</span></span>

```powershell
function Add-Extension
{
    param
    (
        [string]
        # Specifies the file name.
        $name,

        [string]
        # Specifies the file name extension. "Txt" is the default.
        $extension = "txt"
    )
    $name = $name + "." + $extension
    $name

    <#
        .SYNOPSIS
        Adds a file name extension to a supplied name.
...
    #>
```

<span data-ttu-id="b9cdd-117">Os resultados são os mesmos, como os resultados, por exemplo 1.</span><span class="sxs-lookup"><span data-stu-id="b9cdd-117">The results are the same as the results for Example 1.</span></span> <span data-ttu-id="b9cdd-118">Get-Help interpreta as descrições de parâmetros, como se eles foram acompanhados pelo `.Parameter` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="b9cdd-118">Get-Help interprets the parameter descriptions as though they were accompanied by the `.Parameter` keyword.</span></span>

## <a name="example-4--redirecting-to-an-xml-file"></a><span data-ttu-id="b9cdd-119">Exemplo 4:  Redirecionar para um ficheiro XML</span><span class="sxs-lookup"><span data-stu-id="b9cdd-119">Example 4:  Redirecting to an XML File</span></span>

<span data-ttu-id="b9cdd-120">Pode escrever tópicos de ajuda baseados em XML para funções e scripts.</span><span class="sxs-lookup"><span data-stu-id="b9cdd-120">You can write XML-based Help topics for functions and scripts.</span></span> <span data-ttu-id="b9cdd-121">Embora seja mais fácil de implementar a ajuda baseada no comentário, ajuda baseados em XML é necessária se pretender que o controle mais preciso sobre o conteúdo de ajuda ou se esteja traduzindo o tópicos de ajuda em vários idiomas. O exemplo seguinte mostra as primeiras linhas do script Month.ps1 de atualização.</span><span class="sxs-lookup"><span data-stu-id="b9cdd-121">Although comment-based Help is easier to implement, XML-based Help is required if you want more precise control over Help content or if you are translating Help topics into multiple languages.The following example shows the first few lines of the Update-Month.ps1 script.</span></span> <span data-ttu-id="b9cdd-122">O script utiliza o `.ExternalHelp` palavra-chave para especificar o caminho para um tópico de ajuda baseados em XML para o script.</span><span class="sxs-lookup"><span data-stu-id="b9cdd-122">The script uses the `.ExternalHelp` keyword to specify the path to an XML-based Help topic for the script.</span></span>

```powershell
#  .ExternalHelp C:\MyScripts\Update-Month-Help.xml

    param ([string]$InputPath, [string]$OutPutPath)

    function Get-Data { }
```

<span data-ttu-id="b9cdd-123">O exemplo seguinte mostra a utilização do `.ExternalHelp` palavra-chave numa função.</span><span class="sxs-lookup"><span data-stu-id="b9cdd-123">The following example shows the use of the `.ExternalHelp` keyword in a function.</span></span>

```powershell
function Add-Extension
{
    param ([string] $name, [string]$extension = "txt")
    $name = $name + "." + $extension
    $name

    # .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

## <a name="example-5--redirecting-to-a-different-help-topic"></a><span data-ttu-id="b9cdd-124">Exemplo 5:  Redirecionar para um tópico de ajuda diferentes</span><span class="sxs-lookup"><span data-stu-id="b9cdd-124">Example 5:  Redirecting to a Different Help Topic</span></span>

<span data-ttu-id="b9cdd-125">O código a seguir é um extrato do início do incorporada `Help` função no Windows PowerShell, que exibe uma tela de texto de ajuda de cada vez.</span><span class="sxs-lookup"><span data-stu-id="b9cdd-125">The following code is an excerpt from the beginning of the built-in `Help` function in Windows PowerShell, which displays one screen of Help text at a time.</span></span> <span data-ttu-id="b9cdd-126">Uma vez que o tópico de ajuda para o cmdlet Get-Help descreve a função de ajuda, a função de ajuda utiliza a `.ForwardHelpTargetName` e `.ForwardHelpCategory` palavras-chave para redirecionar o utilizador para o tópico de ajuda do cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="b9cdd-126">Because the Help topic for the Get-Help cmdlet describes the Help function, the Help function uses the `.ForwardHelpTargetName` and `.ForwardHelpCategory` keywords to redirect the user to the Get-Help cmdlet Help topic.</span></span>

```powershell
function help
{

    <#
      .FORWARDHELPTARGETNAME Get-Help
      .FORWARDHELPCATEGORY Cmdlet
    #>
    [CmdletBinding(DefaultParameterSetName='AllUsersView')]
    param(
            [Parameter(Position=0, ValueFromPipelineByPropertyName=$true)]
            [System.String]
            ${Name},
    ...
```

<span data-ttu-id="b9cdd-127">O comando seguinte utiliza esta funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="b9cdd-127">The following command uses this feature.</span></span> <span data-ttu-id="b9cdd-128">Quando um usuário digita um comando Get-Help para a função de ajuda, Get-Help apresenta o tópico de ajuda para o cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="b9cdd-128">When a user types a Get-Help command for the Help function, Get-Help displays the Help topic for the Get-Help cmdlet.</span></span>

```powershell
C:\PS> get-help help
```

```output
            NAME
                Get-Help

            SYNOPSIS
                Displays information about Windows PowerShell cmdlets and concepts.
            ...
```