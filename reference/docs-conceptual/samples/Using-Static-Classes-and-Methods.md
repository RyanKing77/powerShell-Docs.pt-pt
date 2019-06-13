---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Utilizar Classes e Métodos Estáticos
ms.openlocfilehash: 437e7b430f37224de7c617e120e37c3efcd7787a
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030744"
---
# <a name="using-static-classes-and-methods"></a><span data-ttu-id="5917b-103">Utilizar Classes e Métodos Estáticos</span><span class="sxs-lookup"><span data-stu-id="5917b-103">Using Static Classes and Methods</span></span>

<span data-ttu-id="5917b-104">Nem todas as classes do .NET Framework podem ser criadas usando **New-Object**.</span><span class="sxs-lookup"><span data-stu-id="5917b-104">Not all .NET Framework classes can be created by using **New-Object**.</span></span> <span data-ttu-id="5917b-105">Por exemplo, se tentar criar uma **System.Environment** ou uma **Math** objeto com **New-Object**, irá obter as mensagens de erro seguinte:</span><span class="sxs-lookup"><span data-stu-id="5917b-105">For example, if you try to create a **System.Environment** or a **System.Math** object with **New-Object**, you will get the following error messages:</span></span>

```
PS> New-Object System.Environment
New-Object : Constructor not found. Cannot find an appropriate constructor for
type System.Environment.
At line:1 char:11
+ New-Object  <<<< System.Environment

PS> New-Object System.Math
New-Object : Constructor not found. Cannot find an appropriate constructor for
type System.Math.
At line:1 char:11
+ New-Object  <<<< System.Math
```

<span data-ttu-id="5917b-106">Estes erros ocorrerem porque não é possível criar um novo objeto dessas classes.</span><span class="sxs-lookup"><span data-stu-id="5917b-106">These errors occur because there is no way to create a new object from these classes.</span></span> <span data-ttu-id="5917b-107">Essas classes são bibliotecas de referência de métodos e propriedades que não alterar o estado.</span><span class="sxs-lookup"><span data-stu-id="5917b-107">These classes are reference libraries of methods and properties that do not change state.</span></span> <span data-ttu-id="5917b-108">Não precisa de criá-los, simplesmente usá-los.</span><span class="sxs-lookup"><span data-stu-id="5917b-108">You don't need to create them, you simply use them.</span></span> <span data-ttu-id="5917b-109">Classes e métodos como esses são chamados *classes estáticas* porque eles não forem criados, destruído ou alterados.</span><span class="sxs-lookup"><span data-stu-id="5917b-109">Classes and methods such as these are called *static classes* because they are not created, destroyed, or changed.</span></span> <span data-ttu-id="5917b-110">Para tornar isso claro, forneceremos exemplos que usam classes estáticas.</span><span class="sxs-lookup"><span data-stu-id="5917b-110">To make this clear we will provide examples that use static classes.</span></span>

## <a name="getting-environment-data-with-systemenvironment"></a><span data-ttu-id="5917b-111">Obter dados de ambiente com System.Environment</span><span class="sxs-lookup"><span data-stu-id="5917b-111">Getting Environment Data with System.Environment</span></span>

<span data-ttu-id="5917b-112">Normalmente, a primeira etapa ao trabalhar com um objeto no Windows PowerShell é usar o Get-Member para saber quais os membros contém.</span><span class="sxs-lookup"><span data-stu-id="5917b-112">Usually, the first step in working with an object in Windows PowerShell is to use Get-Member to find out what members it contains.</span></span> <span data-ttu-id="5917b-113">Com as classes estáticas, o processo é um pouco diferente porque a classe real não é um objeto.</span><span class="sxs-lookup"><span data-stu-id="5917b-113">With static classes, the process is a little different because the actual class is not an object.</span></span>

### <a name="referring-to-the-static-systemenvironment-class"></a><span data-ttu-id="5917b-114">Que faça referência à classe System.Environment estático</span><span class="sxs-lookup"><span data-stu-id="5917b-114">Referring to the Static System.Environment Class</span></span>

<span data-ttu-id="5917b-115">Pode consultar a uma classe estática, ao nome da classe com Parênteses Retos.</span><span class="sxs-lookup"><span data-stu-id="5917b-115">You can refer to a static class by surrounding the class name with square brackets.</span></span> <span data-ttu-id="5917b-116">Por exemplo, pode consultar **System.Environment** digitando o nome entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="5917b-116">For example, you can refer to **System.Environment** by typing the name within brackets.</span></span> <span data-ttu-id="5917b-117">Se o fizer, apresenta algumas informações de tipo genérico:</span><span class="sxs-lookup"><span data-stu-id="5917b-117">Doing so displays some generic type information:</span></span>

```
PS> [System.Environment]

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     False    Environment                              System.Object
```

> [!NOTE]
> <span data-ttu-id="5917b-118">Como mencionado anteriormente, Windows PowerShell automaticamente acrescenta '**System.** '</span><span class="sxs-lookup"><span data-stu-id="5917b-118">As we mentioned previously, Windows PowerShell automatically prepends '**System.**'</span></span> <span data-ttu-id="5917b-119">digitar nomes ao utilizar **New-Object**.</span><span class="sxs-lookup"><span data-stu-id="5917b-119">to type names when you use **New-Object**.</span></span> <span data-ttu-id="5917b-120">A mesma coisa acontece quando utilizar um nome de tipo entre parênteses, então, pode especificar  **\[System.Environment]** como  **\[ambiente]** .</span><span class="sxs-lookup"><span data-stu-id="5917b-120">The same thing happens when using a bracketed type name, so you can specify **\[System.Environment]** as **\[Environment]**.</span></span>

<span data-ttu-id="5917b-121">O **System.Environment** classe contém informações gerais sobre o ambiente de trabalho para o processo atual, o que é powershell.exe quando trabalhar dentro do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5917b-121">The **System.Environment** class contains general information about the working environment for the current process, which is powershell.exe when working within Windows PowerShell.</span></span>

<span data-ttu-id="5917b-122">Se tentar ver os detalhes dessa classe, escrevendo  **\[System.Environment] | Get-Member**, o tipo de objeto é comunicado como sendo **System.RuntimeType** , e não **System.Environment**:</span><span class="sxs-lookup"><span data-stu-id="5917b-122">If you try to view details of this class by typing **\[System.Environment] | Get-Member**, the object type is reported as being **System.RuntimeType** , not **System.Environment**:</span></span>

```
PS> [System.Environment] | Get-Member

   TypeName: System.RuntimeType
```

<span data-ttu-id="5917b-123">Para ver os membros estáticos com Get-Member, especifique a **estático** parâmetro:</span><span class="sxs-lookup"><span data-stu-id="5917b-123">To view static members with Get-Member, specify the **Static** parameter:</span></span>

```
PS> [System.Environment] | Get-Member -Static

   TypeName: System.Environment

Name                       MemberType Definition
----                       ---------- ----------
Equals                     Method     static System.Boolean Equals(Object ob...
Exit                       Method     static System.Void Exit(Int32 exitCode)
...
CommandLine                Property   static System.String CommandLine {get;}
CurrentDirectory           Property   static System.String CurrentDirectory ...
ExitCode                   Property   static System.Int32 ExitCode {get;set;}
HasShutdownStarted         Property   static System.Boolean HasShutdownStart...
MachineName                Property   static System.String MachineName {get;}
NewLine                    Property   static System.String NewLine {get;}
OSVersion                  Property   static System.OperatingSystem OSVersio...
ProcessorCount             Property   static System.Int32 ProcessorCount {get;}
StackTrace                 Property   static System.String StackTrace {get;}
SystemDirectory            Property   static System.String SystemDirectory {...
TickCount                  Property   static System.Int32 TickCount {get;}
UserDomainName             Property   static System.String UserDomainName {g...
UserInteractive            Property   static System.Boolean UserInteractive ...
UserName                   Property   static System.String UserName {get;}
Version                    Property   static System.Version Version {get;}
WorkingSet                 Property   static System.Int64 WorkingSet {get;}
TickCount                               ExitCode
```

<span data-ttu-id="5917b-124">Agora podemos selecionar as propriedades para ver a partir System.Environment.</span><span class="sxs-lookup"><span data-stu-id="5917b-124">We can now select properties to view from System.Environment.</span></span>

### <a name="displaying-static-properties-of-systemenvironment"></a><span data-ttu-id="5917b-125">Exibir propriedades estáticas da System.Environment</span><span class="sxs-lookup"><span data-stu-id="5917b-125">Displaying Static Properties of System.Environment</span></span>

<span data-ttu-id="5917b-126">As propriedades de System.Environment também são estáticas e tem de ser especificadas de outra forma de propriedades normais.</span><span class="sxs-lookup"><span data-stu-id="5917b-126">The properties of System.Environment are also static, and must be specified in a different way than normal properties.</span></span> <span data-ttu-id="5917b-127">Usamos **::** para indicar ao Windows PowerShell que queremos trabalhar com um método estático ou uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="5917b-127">We use **::** to indicate to Windows PowerShell that we want to work with a static method or property.</span></span> <span data-ttu-id="5917b-128">Para ver o comando que utilizou para iniciar o Windows PowerShell, verificamos os **CommandLine** propriedade digitando:</span><span class="sxs-lookup"><span data-stu-id="5917b-128">To see the command that was used to launch Windows PowerShell, we check the **CommandLine** property by typing:</span></span>

```
PS> [System.Environment]::Commandline
"C:\Program Files\Windows PowerShell\v1.0\powershell.exe"
```

<span data-ttu-id="5917b-129">Para verificar a versão do sistema operativo, exiba a propriedade OSVersion digitando:</span><span class="sxs-lookup"><span data-stu-id="5917b-129">To check the operating system version, display the OSVersion property by typing:</span></span>

```
PS> [System.Environment]::OSVersion

           Platform ServicePack         Version             VersionString
           -------- -----------         -------             -------------
            Win32NT Service Pack 2      5.1.2600.131072     Microsoft Windows...
```

<span data-ttu-id="5917b-130">Podemos verificar se o computador está no processo de encerramento ao apresentar o **HasShutdownStarted** propriedade:</span><span class="sxs-lookup"><span data-stu-id="5917b-130">We can check whether the computer is in the process of shutting down by displaying the **HasShutdownStarted** property:</span></span>

```
PS> [System.Environment]::HasShutdownStarted
False
```

## <a name="doing-math-with-systemmath"></a><span data-ttu-id="5917b-131">Fazer cálculos com Math</span><span class="sxs-lookup"><span data-stu-id="5917b-131">Doing Math with System.Math</span></span>

<span data-ttu-id="5917b-132">A classe estática System é útil para realizar algumas operações matemáticas.</span><span class="sxs-lookup"><span data-stu-id="5917b-132">The System.Math static class is useful for performing some mathematical operations.</span></span> <span data-ttu-id="5917b-133">Os membros importantes **Math** são principalmente métodos, que podemos exibir usando **Get-Member**.</span><span class="sxs-lookup"><span data-stu-id="5917b-133">The important members of **System.Math** are mostly methods, which we can display by using **Get-Member**.</span></span>

> [!NOTE]
> <span data-ttu-id="5917b-134">Math tem vários métodos com o mesmo nome, mas eles são distinguidos pelo tipo de seus parâmetros.</span><span class="sxs-lookup"><span data-stu-id="5917b-134">System.Math has several methods with the same name, but they are distinguished by the type of their parameters.</span></span>

<span data-ttu-id="5917b-135">Escreva o seguinte comando para listar os métodos do **Math** classe.</span><span class="sxs-lookup"><span data-stu-id="5917b-135">Type the following command to list the methods of the **System.Math** class.</span></span>

```
PS> [System.Math] | Get-Member -Static -MemberType Methods

   TypeName: System.Math

Name            MemberType Definition
----            ---------- ----------
Abs             Method     static System.Single Abs(Single value), static Sy...
Acos            Method     static System.Double Acos(Double d)
Asin            Method     static System.Double Asin(Double d)
Atan            Method     static System.Double Atan(Double d)
Atan2           Method     static System.Double Atan2(Double y, Double x)
BigMul          Method     static System.Int64 BigMul(Int32 a, Int32 b)
Ceiling         Method     static System.Double Ceiling(Double a), static Sy...
Cos             Method     static System.Double Cos(Double d)
Cosh            Method     static System.Double Cosh(Double value)
DivRem          Method     static System.Int32 DivRem(Int32 a, Int32 b, Int3...
Equals          Method     static System.Boolean Equals(Object objA, Object ...
Exp             Method     static System.Double Exp(Double d)
Floor           Method     static System.Double Floor(Double d), static Syst...
IEEERemainder   Method     static System.Double IEEERemainder(Double x, Doub...
Log             Method     static System.Double Log(Double d), static System...
Log10           Method     static System.Double Log10(Double d)
Max             Method     static System.SByte Max(SByte val1, SByte val2), ...
Min             Method     static System.SByte Min(SByte val1, SByte val2), ...
Pow             Method     static System.Double Pow(Double x, Double y)
ReferenceEquals Method     static System.Boolean ReferenceEquals(Object objA...
Round           Method     static System.Double Round(Double a), static Syst...
Sign            Method     static System.Int32 Sign(SByte value), static Sys...
Sin             Method     static System.Double Sin(Double a)
Sinh            Method     static System.Double Sinh(Double value)
Sqrt            Method     static System.Double Sqrt(Double d)
Tan             Method     static System.Double Tan(Double a)
Tanh            Method     static System.Double Tanh(Double value)
Truncate        Method     static System.Decimal Truncate(Decimal d), static...
```

<span data-ttu-id="5917b-136">Esta ação apresenta vários métodos de matemáticos.</span><span class="sxs-lookup"><span data-stu-id="5917b-136">This displays several mathematical methods.</span></span> <span data-ttu-id="5917b-137">Aqui está uma lista de comandos que demonstram como alguns dos métodos comuns funcionam:</span><span class="sxs-lookup"><span data-stu-id="5917b-137">Here is a list of commands that demonstrate how some of the common methods work:</span></span>

```
PS> [System.Math]::Sqrt(9)
3
PS> [System.Math]::Pow(2,3)
8
PS> [System.Math]::Floor(3.3)
3
PS> [System.Math]::Floor(-3.3)
-4
PS> [System.Math]::Ceiling(3.3)
4
PS> [System.Math]::Ceiling(-3.3)
-3
PS> [System.Math]::Max(2,7)
7
PS> [System.Math]::Min(2,7)
2
PS> [System.Math]::Truncate(9.3)
9
PS> [System.Math]::Truncate(-9.3)
-9
```
