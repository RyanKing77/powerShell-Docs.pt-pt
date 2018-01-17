---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Criação de um recurso de DSC em c#"
ms.openlocfilehash: 2fc6b8c127bca29e8f66fc7bd8d2828fdfe39f3c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="authoring-a-dsc-resource-in-c"></a><span data-ttu-id="2c6d0-103">Criação de um recurso de DSC em c#</span><span class="sxs-lookup"><span data-stu-id="2c6d0-103">Authoring a DSC resource in C#</span></span>

> <span data-ttu-id="2c6d0-104">Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="2c6d0-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="2c6d0-105">Normalmente, um recurso personalizado de configuração de estado pretendido do Windows PowerShell (DSC) é implementado num script do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2c6d0-105">Typically, a Windows PowerShell Desired State Configuration (DSC) custom resource is implemented in a PowerShell script.</span></span> <span data-ttu-id="2c6d0-106">No entanto, também pode implementar a funcionalidade de um recurso personalizado de DSC escrevendo cmdlets em c#.</span><span class="sxs-lookup"><span data-stu-id="2c6d0-106">However, you can also implement the functionality of a DSC custom resource by writing cmdlets in C#.</span></span> <span data-ttu-id="2c6d0-107">Para uma introdução sobre como escrever cmdlets em c#, consulte [escrever um Cmdlet do Windows PowerShell](https://technet.microsoft.com/en-us/library/dd878294.aspx).</span><span class="sxs-lookup"><span data-stu-id="2c6d0-107">For an introduction on writing cmdlets in C#, see [Writing a Windows PowerShell Cmdlet](https://technet.microsoft.com/en-us/library/dd878294.aspx).</span></span>

<span data-ttu-id="2c6d0-108">Para além de implementar o recurso em c# que cmdlets, o processo de criar o esquema MOF, a estrutura da pasta a criar, importar e utilizar o recurso personalizado de DSC são os mesmos conforme descrito em [escrever um recurso personalizado de DSC com MOF](authoringResourceMOF.md).</span><span class="sxs-lookup"><span data-stu-id="2c6d0-108">Aside from implementing the resource in C# as cmdlets, the process of creating the MOF schema, creating the folder structure, importing and using your custom DSC resource are the same as described in [Writing a custom DSC resource with MOF](authoringResourceMOF.md).</span></span>

## <a name="writing-a-cmdlet-based-resource"></a><span data-ttu-id="2c6d0-109">Escrever um recurso baseada em cmdlet</span><span class="sxs-lookup"><span data-stu-id="2c6d0-109">Writing a cmdlet-based resource</span></span>
<span data-ttu-id="2c6d0-110">Neste exemplo, iremos irá implementar um recurso simple que gere um ficheiro de texto e o respetivo conteúdo.</span><span class="sxs-lookup"><span data-stu-id="2c6d0-110">For this example, we will implement a simple resource that manages a text file and its contents.</span></span>

### <a name="writing-the-mof-schema"></a><span data-ttu-id="2c6d0-111">Escrever o esquema MOF</span><span class="sxs-lookup"><span data-stu-id="2c6d0-111">Writing the MOF schema</span></span>

<span data-ttu-id="2c6d0-112">Segue-se a definição do recurso MOF.</span><span class="sxs-lookup"><span data-stu-id="2c6d0-112">The following is the MOF resource definition.</span></span>

```
[ClassVersion("1.0.0"), FriendlyName("xDemoFile")]
class MSFT_XDemoFile : OMI_BaseResource
{
                [Key, Description("path")] String Path;
                [Write, Description("Should the file be present"), ValueMap{"Present","Absent"}, Values{"Present","Absent"}] String Ensure;
                [Write, Description("Contentof file.")] String Content;                   
};
```

### <a name="setting-up-the-visual-studio-project"></a><span data-ttu-id="2c6d0-113">Configurar o projeto do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2c6d0-113">Setting up the Visual Studio project</span></span>
#### <a name="setting-up-a-cmdlet-project"></a><span data-ttu-id="2c6d0-114">Configurar um projeto do cmdlet</span><span class="sxs-lookup"><span data-stu-id="2c6d0-114">Setting up a cmdlet project</span></span>

1. <span data-ttu-id="2c6d0-115">Abra o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2c6d0-115">Open Visual Studio.</span></span>
1. <span data-ttu-id="2c6d0-116">Criar um projeto c# e forneça o nome.</span><span class="sxs-lookup"><span data-stu-id="2c6d0-116">Create a C# project and provide the name.</span></span>
1. <span data-ttu-id="2c6d0-117">Selecione **biblioteca de classes** entre os modelos de projeto disponível.</span><span class="sxs-lookup"><span data-stu-id="2c6d0-117">Select **Class Library** from the available project templates.</span></span>
1. <span data-ttu-id="2c6d0-118">Click **Ok**.</span><span class="sxs-lookup"><span data-stu-id="2c6d0-118">Click **Ok**.</span></span>
1. <span data-ttu-id="2c6d0-119">Adicione uma referência de assemblagem para System.Automation.Management.dll ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="2c6d0-119">Add an assembly reference to System.Automation.Management.dll to your project.</span></span>
1. <span data-ttu-id="2c6d0-120">Altere o nome de assemblagem para corresponder ao nome do recurso.</span><span class="sxs-lookup"><span data-stu-id="2c6d0-120">Change the assembly name to match the resource name.</span></span> <span data-ttu-id="2c6d0-121">Neste caso, a assemblagem deve ter o nome **MSFT_XDemoFile**.</span><span class="sxs-lookup"><span data-stu-id="2c6d0-121">In this case, the assembly should be named **MSFT_XDemoFile**.</span></span>

### <a name="writing-the-cmdlet-code"></a><span data-ttu-id="2c6d0-122">Escrever o código de cmdlet</span><span class="sxs-lookup"><span data-stu-id="2c6d0-122">Writing the cmdlet code</span></span>

<span data-ttu-id="2c6d0-123">O seguinte código c# implementa o **Get-TargetResource**, **conjunto TargetResource**, e **TargetResource de teste** cmdlets.</span><span class="sxs-lookup"><span data-stu-id="2c6d0-123">The following C# code implements the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** cmdlets.</span></span>

```C#


namespace cSharpDSCResourceExample
{
    using System;
    using System.Collections.Generic;
    using System.IO;
    using System.Management.Automation;  // Windows PowerShell assembly.

    #region Get-TargetResource

    [OutputType(typeof(System.Collections.Hashtable))]
    [Cmdlet(VerbsCommon.Get, "TargetResource")]
    public class GetTargetResource : PSCmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        /// <summary>
        /// Implement the logic to return the current state of the resource as a hashtable with keys being the resource properties 
        /// and the values are the corresponding current value on the machine.
        /// </summary>
        protected override void ProcessRecord()
        {
            var currentResourceState = new Dictionary<string, string>();
            if (File.Exists(Path))
            {
                currentResourceState.Add("Ensure", "Present");

                // read current content 
                string CurrentContent = "";
                using (var reader = new StreamReader(Path))
                {
                    CurrentContent = reader.ReadToEnd();
                }
                currentResourceState.Add("Content", CurrentContent);
            }
            else
            {
                currentResourceState.Add("Ensure", "Absent");
                currentResourceState.Add("Content", "");
            }
            // write the hashtable in the PS console.
            WriteObject(currentResourceState);
        }
    }
    
    # endregion

    #region Set-TargetResource
    [OutputType(typeof(void))]
    [Cmdlet(VerbsCommon.Set, "TargetResource")]
    public class SetTargetResource : PSCmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        [Parameter(Mandatory = false)]
        
        [ValidateSet("Present", "Absent", IgnoreCase = true)]
        public string Ensure {
            get
            {
                // set the default to present.
               return (this._ensure ?? "Present") ;
            }
            set
            {
                this._ensure = value;
            }
        }

        [Parameter(Mandatory = false)]
        public string Content {
            get { return (string.IsNullOrEmpty(this._content) ? "" : this._content); }
            set { this._content = value; }
        }

        private string _ensure;
        private string _content;

        /// <summary>
        /// Implement the logic to set the state of the machine to the desired state.
        /// </summary>
        protected override void ProcessRecord()
        {
            WriteVerbose(string.Format("Running set with parameters {0}{1}{2}", Path, Ensure, Content));
            if (File.Exists(Path))
            {
                if (Ensure.Equals("absent", StringComparison.InvariantCultureIgnoreCase))
                {
                    File.Delete(Path);
                }
                else
                {
                    // file already exist and ensure "present" is specified. start writing the content to a file
                    if (!string.IsNullOrEmpty(Content))
                    {
                        string existingContent = null;
                        using (var reader = new StreamReader(Path))
                        {
                            existingContent = reader.ReadToEnd();
                        }
                        // check if the content of the file mathes the content passed 
                        if (!existingContent.Equals(Content, StringComparison.InvariantCultureIgnoreCase))
                        {
                            WriteVerbose("Existing content did not match with desired content updating the content of the file");
                            using (var writer = new StreamWriter(Path))
                            {
                                writer.Write(Content);
                                writer.Flush();
                            }
                        }
                    }
                }

            }
            else
            {
                if (Ensure.Equals("present", StringComparison.InvariantCultureIgnoreCase))
                {
                    // if nothing is passed for content just write "" otherwise write the content passed.
                    using (var writer = new StreamWriter(Path))
                    {
                        WriteVerbose(string.Format("Creating a file under path {0} with content {1}", Path, Content));
                        writer.Write(Content);
                    }
                }

            }
            
            /* if you need to reboot the VM. please add the following two line of code.
            PSVariable DscMachineStatus = new PSVariable("DSCMachineStatus", 1, ScopedItemOptions.AllScope);
            this.SessionState.PSVariable.Set(DscMachineStatus);
             */     

        }

    }

    # endregion

    #region Test-TargetResource

    [Cmdlet("Test", "TargetResource")]
    [OutputType(typeof(Boolean))]
    public class TestTargetResource : PSCmdlet
    {   
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        [Parameter(Mandatory = false)]

        [ValidateSet("Present", "Absent", IgnoreCase = true)]
        public string Ensure
        {
            get
            {
                // set the default to present.
                return (this._ensure ?? "Present");
            }
            set
            {
                this._ensure = value;
            }
        }

        [Parameter(Mandatory = false)]
        public string Content
        {
            get { return (string.IsNullOrEmpty(this._content) ? "" : this._content); }
            set { this._content = value; }
        }

        private string _ensure;
        private string _content;

        /// <summary>
        /// Return a boolean value which indicates wheather the current machine is in desired state or not.
        /// </summary>
        protected override void ProcessRecord()
        {
            if (File.Exists(Path)) 
            {
                if( Ensure.Equals("absent", StringComparison.InvariantCultureIgnoreCase))
                {
                    WriteObject(false);
                }
                else
                {
                    // check if the content matches

                    string existingContent = null;
                    using (var stream = new StreamReader(Path))
                    {
                        existingContent = stream.ReadToEnd();
                    }

                    WriteObject(Content.Equals(existingContent, StringComparison.InvariantCultureIgnoreCase));
                }
            }
            else
            {
                WriteObject(Ensure.Equals("Absent", StringComparison.InvariantCultureIgnoreCase));
            }
        }        
    }

    # endregion

}
```

### <a name="deploying-the-resource"></a><span data-ttu-id="2c6d0-124">Implementar o recurso</span><span class="sxs-lookup"><span data-stu-id="2c6d0-124">Deploying the resource</span></span>

<span data-ttu-id="2c6d0-125">O ficheiro dll compilada deverá ser guardado numa estrutura de ficheiros semelhante a um recurso baseados em script.</span><span class="sxs-lookup"><span data-stu-id="2c6d0-125">The compiled dll file should be saved in a file structure similar to a script-based resource.</span></span> <span data-ttu-id="2c6d0-126">Segue-se a estrutura de pastas para este recurso.</span><span class="sxs-lookup"><span data-stu-id="2c6d0-126">The following is the folder structure for this resource.</span></span>

```
$env: psmodulepath (folder)
    |- MyDscResources (folder)
        |- MyDscResources.psd1 (file, required)     
        |- DSCResources (folder)
            |- MSFT_XDemoFile (folder)
                |- MSFT_XDemoFile.psd1 (file, optional)
                |- MSFT_XDemoFile.dll (file, required)
                |- MSFT_XDemoFile.schema.mof (file, required)
```

### <a name="see-also"></a><span data-ttu-id="2c6d0-127">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="2c6d0-127">See Also</span></span>
#### <a name="concepts"></a><span data-ttu-id="2c6d0-128">Conceitos</span><span class="sxs-lookup"><span data-stu-id="2c6d0-128">Concepts</span></span>
[<span data-ttu-id="2c6d0-129">Escrever um recurso personalizado de DSC com MOF</span><span class="sxs-lookup"><span data-stu-id="2c6d0-129">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
#### <a name="other-resources"></a><span data-ttu-id="2c6d0-130">Outros Recursos</span><span class="sxs-lookup"><span data-stu-id="2c6d0-130">Other Resources</span></span>
[<span data-ttu-id="2c6d0-131">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2c6d0-131">Writing a Windows PowerShell Cmdlet</span></span>](https://msdn.microsoft.com/en-us/library/dd878294.aspx)

