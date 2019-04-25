---
title: Criação de um Cmdlet sem parâmetros | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmers Guide], creating
- cmdlets [PowerShell Programmers Guide], basic cmdlet
ms.assetid: 54236ef3-82db-45f8-9114-1ecb7ff65d3e
caps.latest.revision: 8
ms.openlocfilehash: c380b28570c955de6f41152fd617f5c1b0f9e4bd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068339"
---
# <a name="creating-a-cmdlet-without-parameters"></a><span data-ttu-id="4e0f9-102">Creating a Cmdlet without Parameters (Criar um Cmdlet sem Parâmetros)</span><span class="sxs-lookup"><span data-stu-id="4e0f9-102">Creating a Cmdlet without Parameters</span></span>

<span data-ttu-id="4e0f9-103">Esta secção descreve como criar um cmdlet que obtém informações do computador local sem o uso de parâmetros e, em seguida, escreve as informações para o pipeline.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-103">This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span> <span data-ttu-id="4e0f9-104">O cmdlet descrito aqui é um cmdlet de Get-Proc que obtém informações sobre os processos do computador local e, em seguida, exibe essas informações na linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-104">The cmdlet described here is a Get-Proc cmdlet that retrieves information about the processes of the local computer, and then displays that information at the command line.</span></span>

<span data-ttu-id="4e0f9-105">Os tópicos nesta secção incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="4e0f9-105">Topics in this section include the following:</span></span>

- [<span data-ttu-id="4e0f9-106">O Cmdlet de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="4e0f9-106">Naming the Cmdlet</span></span>](#Naming-the-Cmdlet)

- [<span data-ttu-id="4e0f9-107">Definir a classe Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4e0f9-107">Defining the Cmdlet Class</span></span>](#Defining-the-Cmdlet-Class)

- [<span data-ttu-id="4e0f9-108">Substituir uma método de processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="4e0f9-108">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="4e0f9-109">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="4e0f9-109">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="4e0f9-110">Definir tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="4e0f9-110">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="4e0f9-111">Criando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4e0f9-111">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="4e0f9-112">O Cmdlet de teste</span><span class="sxs-lookup"><span data-stu-id="4e0f9-112">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

> [!NOTE]
> <span data-ttu-id="4e0f9-113">Lembre-se de que ao escrever cmdlets, os assemblies de referência Windows PowerShell® são transferidos para o disco (por predefinição em C:\Program arquivos Assemblies\Microsoft\WindowsPowerShell\v1.0). Não estiverem instalados no Cache de Assembly Global (GAC).</span><span class="sxs-lookup"><span data-stu-id="4e0f9-113">Be aware that when writing cmdlets, the Windows PowerShell® reference assemblies are downloaded onto disk (by default at C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).They are not installed in the Global Assembly Cache (GAC).</span></span>

## <a name="naming-the-cmdlet"></a><span data-ttu-id="4e0f9-114">O Cmdlet de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="4e0f9-114">Naming the Cmdlet</span></span>

<span data-ttu-id="4e0f9-115">Um nome de cmdlet é constituído por um verbo que indica que a ação, o cmdlet aceita e um substantivo que indica os itens que o cmdlet age sobre.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-115">A cmdlet name consists of a verb that indicates the action the cmdlet takes and a noun that indicates the items that the cmdlet acts upon.</span></span> <span data-ttu-id="4e0f9-116">Uma vez que este cmdlet de Get-Proc de exemplo obtém objetos de processo, ele usa o verbo "Get", definido pela [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumeração e o substantivo "Procedimento" para indicar que o cmdlet funciona nos itens de processo.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-116">Because this sample Get-Proc cmdlet retrieves process objects, it uses the verb "Get", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumeration, and the noun "Proc" to indicate that the cmdlet works on process items.</span></span>

<span data-ttu-id="4e0f9-117">Quando atribuir nomes cmdlets, não use nenhum dos seguintes carateres: #, () {} [] & - / \ $;: "" <> &#124; ?</span><span class="sxs-lookup"><span data-stu-id="4e0f9-117">When naming cmdlets, do not use any of the following characters: # , () {} [] & - /\ $ ; : " '<> &#124; ?</span></span> <span data-ttu-id="4e0f9-118">@ \` .</span><span class="sxs-lookup"><span data-stu-id="4e0f9-118">@ \` .</span></span>

### <a name="choosing-a-noun"></a><span data-ttu-id="4e0f9-119">Escolher um substantivo</span><span class="sxs-lookup"><span data-stu-id="4e0f9-119">Choosing a Noun</span></span>

<span data-ttu-id="4e0f9-120">Deve escolher um substantivo específicos.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-120">You should choose a noun that is specific.</span></span> <span data-ttu-id="4e0f9-121">É melhor usar um substantivo singular prefixado com uma versão abreviada do nome do produto.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-121">It is best to use a singular noun prefixed with a shortened version of the product name.</span></span> <span data-ttu-id="4e0f9-122">Um nome de cmdlet de exemplo deste tipo é "`Get-SQLServer`".</span><span class="sxs-lookup"><span data-stu-id="4e0f9-122">An example cmdlet name of this type is "`Get-SQLServer`".</span></span>

### <a name="choosing-a-verb"></a><span data-ttu-id="4e0f9-123">Escolher um verbo</span><span class="sxs-lookup"><span data-stu-id="4e0f9-123">Choosing a Verb</span></span>

<span data-ttu-id="4e0f9-124">Deve usar um verbo do conjunto de nomes de verbo do cmdlet aprovados.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-124">You should use a verb from the set of approved cmdlet verb names.</span></span> <span data-ttu-id="4e0f9-125">Para obter mais informações sobre os verbos aprovados cmdlet, consulte [nomes de verbo do Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="4e0f9-125">For more information about the approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="4e0f9-126">Definir a classe Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4e0f9-126">Defining the Cmdlet Class</span></span>

<span data-ttu-id="4e0f9-127">Depois de escolher um nome de cmdlet, defina uma classe do .NET para implementar o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-127">Once you have chosen a cmdlet name, define a .NET class to implement the cmdlet.</span></span> <span data-ttu-id="4e0f9-128">Segue-se a definição de classe para este cmdlet de Get-procedimento de exemplo:</span><span class="sxs-lookup"><span data-stu-id="4e0f9-128">Here is the class definition for this sample Get-Proc cmdlet:</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

<span data-ttu-id="4e0f9-129">Tenha em atenção que anteriormente a definição de classe, o [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) atributo, com a sintaxe `[Cmdlet(verb, noun, ...)]`, é utilizado para identificar esta classe como um cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-129">Notice that previous to the class definition, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute, with the syntax `[Cmdlet(verb, noun, ...)]`, is used to identify this class as a cmdlet.</span></span> <span data-ttu-id="4e0f9-130">Este é o único atributo obrigatório para todos os cmdlets e permite que o tempo de execução do Windows PowerShell para chamá-los corretamente.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-130">This is the only required attribute for all cmdlets, and it allows the Windows PowerShell runtime to call them correctly.</span></span> <span data-ttu-id="4e0f9-131">Pode definir palavras-chave de atributo ainda mais declarar a classe, se necessário.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-131">You can set attribute keywords to further declare the class if necessary.</span></span> <span data-ttu-id="4e0f9-132">Lembre-se de que a declaração de atributo para nossa classe de GetProcCommand exemplo declara apenas os nome próprio e o verbo nomes para o cmdlet Get-Proc.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-132">Be aware that the attribute declaration for our sample GetProcCommand class declares only the noun and verb names for the Get-Proc cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="4e0f9-133">Para todas as classes de atributo do Windows PowerShell, as palavras-chave que pode definir correspondem às propriedades da classe de atributo.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-133">For all Windows PowerShell attribute classes, the keywords that you can set correspond to properties of the attribute class.</span></span>

<span data-ttu-id="4e0f9-134">Quando atribuir nomes a classe do cmdlet, é uma boa prática para refletir o nome do cmdlet do nome da classe.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-134">When naming the class of the cmdlet, it is a good practice to reflect the cmdlet name in the class name.</span></span> <span data-ttu-id="4e0f9-135">Para fazer isso, use o formulário "VerbNounCommand" e substitua "Verbo" e "Substantivo" com o verbo e substantivo usado no nome do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-135">To do this, use the form "VerbNounCommand" and replace "Verb" and "Noun" with the verb and noun used in the cmdlet name.</span></span> <span data-ttu-id="4e0f9-136">Como é mostrado na definição de classe anterior, o cmdlet Get-procedimento de exemplo define uma classe chamada GetProcCommand, que deriva de [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe base.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-136">As is shown in the previous class definition, the sample Get-Proc cmdlet defines a class called GetProcCommand, which derives from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) base class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4e0f9-137">Se quiser definir um cmdlet que acede diretamente ao tempo de execução do Windows PowerShell, sua classe do .NET deve derivar a partir da [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe base.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-137">If you want to define a cmdlet that accesses the Windows PowerShell runtime directly, your .NET class should derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span> <span data-ttu-id="4e0f9-138">Para obter mais informações sobre essa classe, consulte [criar um Cmdlet que conjuntos de parâmetros define](./adding-parameter-sets-to-a-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="4e0f9-138">For more information about this class, see [Creating a Cmdlet that Defines Parameter Sets](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

> [!NOTE]
> <span data-ttu-id="4e0f9-139">A classe para um cmdlet deve ser marcada explicitamente como pública.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-139">The class for a cmdlet must be explicitly marked as public.</span></span> <span data-ttu-id="4e0f9-140">As classes que não estão marcadas como pública serão predefinido para interno e não serão encontradas pelo tempo de execução do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-140">Classes that are not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="4e0f9-141">Windows PowerShell utiliza a [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) espaço de nomes para suas classes de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-141">Windows PowerShell uses the [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) namespace for its cmdlet classes.</span></span> <span data-ttu-id="4e0f9-142">É recomendado colocar suas classes de cmdlet num espaço de nomes de comandos do seu espaço de nomes de API, por exemplo, xxx.PS.Commands.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-142">It is recommended to place your cmdlet classes in a Commands namespace of your API namespace, for example, xxx.PS.Commands.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="4e0f9-143">Substituir uma método de processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="4e0f9-143">Overriding an Input Processing Method</span></span>

<span data-ttu-id="4e0f9-144">O [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe fornece três métodos de processamento de entrada principal, pelo menos um dos quais deve substituir seu cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-144">The [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class provides three main input processing methods, at least one of which your cmdlet must override.</span></span> <span data-ttu-id="4e0f9-145">Para obter mais informações sobre como o Windows PowerShell processa os registos, consulte [como o Windows PowerShell funciona](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).</span><span class="sxs-lookup"><span data-stu-id="4e0f9-145">For more information about how Windows PowerShell processes records, see [How Windows PowerShell Works](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).</span></span>

<span data-ttu-id="4e0f9-146">Para todos os tipos de entrada, o tempo de execução do Windows PowerShell chama [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) para ativar o processamento.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-146">For all types of input, the Windows PowerShell runtime calls [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) to enable processing.</span></span> <span data-ttu-id="4e0f9-147">Se seu cmdlet tem de efetuar alguns pré-processamento ou a configuração, pode fazer isso substituindo esse método.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-147">If your cmdlet must perform some preprocessing or setup, it can do this by overriding this method.</span></span>

> [!NOTE]
> <span data-ttu-id="4e0f9-148">Windows PowerShell utiliza o termo "Registro" para descrever o conjunto de valores de parâmetro fornecido quando é chamado um cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-148">Windows PowerShell uses the term "record" to describe the set of parameter values supplied when a cmdlet is called.</span></span>

<span data-ttu-id="4e0f9-149">Se seu cmdlet aceita entrada do pipeline, deve substituir a [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método e, opcionalmente, o [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)método.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-149">If your cmdlet accepts pipeline input, it must override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, and optionally the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="4e0f9-150">Por exemplo, um cmdlet pode substituir os dois métodos se ele reúne todas as entradas usando [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) e, em seguida, funciona sobre a entrada como um todo, em vez de um elemento por vez, como o `Sort-Object` cmdlet faz.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-150">For example, a cmdlet might override both methods if it gathers all input using [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) and then operates on the input as a whole rather than one element at a time, as the `Sort-Object` cmdlet does.</span></span>

<span data-ttu-id="4e0f9-151">Se seu cmdlet não der entrada do pipeline, deve substituir a [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-151">If your cmdlet does not take pipeline input, it should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="4e0f9-152">Lembre-se de que este método é frequentemente utilizado em vez de [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) quando o cmdlet não é possível operar num elemento por vez, como no caso de um cmdlet de classificação.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-152">Be aware that this method is frequently used in place of [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) when the cmdlet cannot operate on one element at a time, as is the case for a sorting cmdlet.</span></span>

<span data-ttu-id="4e0f9-153">Uma vez que este cmdlet de Get-procedimento de exemplo tem de receber entrada do pipeline, substitui o [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método e utiliza as implementações predefinidas para [ System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) e [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span><span class="sxs-lookup"><span data-stu-id="4e0f9-153">Because this sample Get-Proc cmdlet must receive pipeline input, it overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method and uses the default implementations for [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) and [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span></span> <span data-ttu-id="4e0f9-154">O [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) substituição obtém processos e escreve-as para a linha de comandos utilizando o [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) método.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-154">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override retrieves processes and writes them to the command line using the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Get the current processes
  Process[] processes = Process.GetProcesses();

  // Write the processes to the pipeline making them available
  // to the next cmdlet. The second parameter of this call tells
  // PowerShell to enumerate the array, and send one process at a
  // time to the pipeline.
  WriteObject(processes, true);
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ Get the current processes.
    Dim processes As Process()
    processes = Process.GetProcesses()

    '/ Write the processes to the pipeline making them available
    '/ to the next cmdlet. The second parameter of this call tells
    '/ PowerShell to enumerate the array, and send one process at a
    '/ time to the pipeline.
    WriteObject(processes, True)

End Sub 'ProcessRecord
```

#### <a name="things-to-remember-about-input-processing"></a><span data-ttu-id="4e0f9-155">Coisas a serem lembrados sobre o processamento de entrada</span><span class="sxs-lookup"><span data-stu-id="4e0f9-155">Things to Remember About Input Processing</span></span>

- <span data-ttu-id="4e0f9-156">A origem de padrão para entrada é um objeto explícito (por exemplo, uma cadeia de caracteres) fornecido pelo usuário na linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-156">The default source for input is an explicit object (for example, a string) provided by the user on the command line.</span></span> <span data-ttu-id="4e0f9-157">Para obter mais informações, consulte [criação de um Cmdlet para entrada de linha de comandos do processo](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="4e0f9-157">For more information, see [Creating a Cmdlet to Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

- <span data-ttu-id="4e0f9-158">Uma método de processamento de entrada também pode receber a entrada do objeto de saída de um cmdlet a montante no pipeline.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-158">An input processing method can also receive input from the output object of an upstream cmdlet on the pipeline.</span></span> <span data-ttu-id="4e0f9-159">Para obter mais informações, consulte [criação de um Cmdlet para entrada de Pipeline de processo](./adding-parameters-that-process-pipeline-input.md).</span><span class="sxs-lookup"><span data-stu-id="4e0f9-159">For more information, see [Creating a Cmdlet to Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="4e0f9-160">Tenha em atenção que seu cmdlet pode recebam entrada de uma combinação de linha de comandos e um pipeline de origens.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-160">Be aware that your cmdlet can receive input from a combination of command-line and pipeline sources.</span></span>

- <span data-ttu-id="4e0f9-161">O cmdlet downstream pode não devolver durante muito tempo ou nada.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-161">The downstream cmdlet might not return for a long time, or not at all.</span></span> <span data-ttu-id="4e0f9-162">Por esse motivo, a entrada a processar o método no seu cmdlet não deve manter bloqueios em durante chamadas para [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especialmente os bloqueios para o qual o escopo ultrapassa a instância de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-162">For that reason, the input processing method in your cmdlet should not hold locks during calls to [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especially locks for which the scope extends beyond the cmdlet instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4e0f9-163">Cmdlets nunca deve chamar [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) ou seu equivalente.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-163">Cmdlets should never call [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) or its equivalent.</span></span>

- <span data-ttu-id="4e0f9-164">Seu cmdlet pode ter variáveis de objeto a ser limpo quando terminar de processamento (por exemplo, se abrir um identificador de arquivo no [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método e mantém o identificador aberto para utilização por [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span><span class="sxs-lookup"><span data-stu-id="4e0f9-164">Your cmdlet might have object variables to clean up when it is finished processing (for example, if it opens a file handle in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span></span> <span data-ttu-id="4e0f9-165">É importante lembrar-se de que o tempo de execução do Windows PowerShell não sempre chamar o [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método, que deve efetuar a limpeza do objeto.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-165">It is important to remember that the Windows PowerShell runtime does not always call the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method, which should perform object cleanup.</span></span>

<span data-ttu-id="4e0f9-166">Por exemplo, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) não podem ser chamados se o cmdlet foi cancelado midway ou se acabar o erro ocorre em qualquer parte do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-166">For example, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) might not be called if the cmdlet is canceled midway or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="4e0f9-167">Por conseguinte, um cmdlet que necessita de limpeza do objeto deve implementar o concluída [System.IDisposable](/dotnet/api/System.IDisposable) padrão, incluindo o finalizador, para que o tempo de execução possa chamar ambos [ System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) e [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) no final do processamento.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-167">Therefore, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including the finalizer, so that the runtime can call both [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) at the end of processing.</span></span>

## <a name="code-sample"></a><span data-ttu-id="4e0f9-168">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="4e0f9-168">Code Sample</span></span>

<span data-ttu-id="4e0f9-169">Para o completa C# código de exemplo, consulte [exemplo de GetProcessSample01](./getprocesssample01-sample.md).</span><span class="sxs-lookup"><span data-stu-id="4e0f9-169">For the complete C# sample code, see [GetProcessSample01 Sample](./getprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="4e0f9-170">Definir tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="4e0f9-170">Defining Object Types and Formatting</span></span>

<span data-ttu-id="4e0f9-171">Windows PowerShell passa informações entre cmdlets com objetos .NET.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-171">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="4e0f9-172">Consequentemente, um cmdlet poderá ter de definir seu próprio tipo, ou o cmdlet poderá ter de expandir um tipo existente fornecido pelo outro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-172">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="4e0f9-173">Para obter mais informações sobre definir novos tipos ou estendendo tipos existentes, consulte [estendendo tipos de objeto e formatação](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="4e0f9-173">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="4e0f9-174">Criando o Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4e0f9-174">Building the Cmdlet</span></span>

<span data-ttu-id="4e0f9-175">Depois de implementar um cmdlet, tem de registá-lo com o Windows PowerShell através de um snap-in do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-175">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="4e0f9-176">Para obter mais informações sobre como registar os cmdlets, consulte [como registrar Cmdlets, fornecedores e alojar aplicações](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="4e0f9-176">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="4e0f9-177">O Cmdlet de teste</span><span class="sxs-lookup"><span data-stu-id="4e0f9-177">Testing the Cmdlet</span></span>

<span data-ttu-id="4e0f9-178">Quando seu cmdlet foi registado com o Windows PowerShell, pode testá-lo executando-a na linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-178">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="4e0f9-179">O código para o cmdlet de Get-Proc nosso exemplo é pequeno, mas ele ainda usa o tempo de execução do Windows PowerShell e um objeto .NET existente, que é o suficiente para torná-lo útil.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-179">The code for our sample Get-Proc cmdlet is small, but it still uses the Windows PowerShell runtime and an existing .NET object, which is enough to make it useful.</span></span> <span data-ttu-id="4e0f9-180">Vamos testá-lo para compreender melhor o Get-Proc pode fazer e como sua saída pode ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-180">Let's test it to better understand what Get-Proc can do and how its output can be used.</span></span> <span data-ttu-id="4e0f9-181">Para obter mais informações sobre como utilizar cmdlets da linha de comando, consulte a [introdução ao Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="4e0f9-181">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

1. <span data-ttu-id="4e0f9-182">Inicie o Windows PowerShell e obtenha os processos atuais em execução no computador.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-182">Start Windows PowerShell, and get the current processes running on the computer.</span></span>

    ```powershell
    get-proc
    ```

    <span data-ttu-id="4e0f9-183">O resultado seguinte é apresentada.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-183">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. <span data-ttu-id="4e0f9-184">Atribua uma variável para os resultados do cmdlet para facilitar a manipulação.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-184">Assign a variable to the cmdlet results for easier manipulation.</span></span>

    ```powershell
    $p=get-proc
    ```

3. <span data-ttu-id="4e0f9-185">Obter o número de processos.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-185">Get the number of processes.</span></span>

    ```powershell
    $p.length
    ```

    <span data-ttu-id="4e0f9-186">O resultado seguinte é apresentada.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-186">The following output appears.</span></span>

    ```output
    63
    ```

4. <span data-ttu-id="4e0f9-187">Obter um processo específico.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-187">Retrieve a specific process.</span></span>

    ```powershell
    $p[6]
    ```

    <span data-ttu-id="4e0f9-188">O resultado seguinte é apresentada.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-188">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. <span data-ttu-id="4e0f9-189">Obter a hora de início deste processo.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-189">Get the start time of this process.</span></span>

    ```powershell
    $p[6].starttime
    ```

    <span data-ttu-id="4e0f9-190">O resultado seguinte é apresentada.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-190">The following output appears.</span></span>

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. <span data-ttu-id="4e0f9-191">Obtenha os processos para o qual a contagem de identificador é superior a 500 e ordenar o resultado.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-191">Get the processes for which the handle count is greater than 500, and sort the result.</span></span>

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    <span data-ttu-id="4e0f9-192">O resultado seguinte é apresentada.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-192">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. <span data-ttu-id="4e0f9-193">Utilize o `Get-Member` cmdlet para listar as propriedades disponíveis para cada processo.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-193">Use the `Get-Member` cmdlet to list the properties available for each process.</span></span>

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    <span data-ttu-id="4e0f9-194">O resultado seguinte é apresentada.</span><span class="sxs-lookup"><span data-stu-id="4e0f9-194">The following output appears.</span></span>

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a><span data-ttu-id="4e0f9-195">Veja Também</span><span class="sxs-lookup"><span data-stu-id="4e0f9-195">See Also</span></span>

[<span data-ttu-id="4e0f9-196">Criação de um Cmdlet para processar a entrada de linha de comandos</span><span class="sxs-lookup"><span data-stu-id="4e0f9-196">Creating a Cmdlet to Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="4e0f9-197">Criação de um Cmdlet para processar a entrada do Pipeline</span><span class="sxs-lookup"><span data-stu-id="4e0f9-197">Creating a Cmdlet to Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="4e0f9-198">Como criar um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4e0f9-198">How to Create a Windows PowerShell Cmdlet</span></span>](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="4e0f9-199">Estendendo tipos de objeto e formatação</span><span class="sxs-lookup"><span data-stu-id="4e0f9-199">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="4e0f9-200">Como funciona o Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4e0f9-200">How Windows PowerShell Works</span></span>](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[<span data-ttu-id="4e0f9-201">Como registar os Cmdlets, fornecedores e alojar aplicações</span><span class="sxs-lookup"><span data-stu-id="4e0f9-201">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="4e0f9-202">Referência do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4e0f9-202">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="4e0f9-203">Exemplos de cmdlet</span><span class="sxs-lookup"><span data-stu-id="4e0f9-203">Cmdlet Samples</span></span>](./cmdlet-samples.md)