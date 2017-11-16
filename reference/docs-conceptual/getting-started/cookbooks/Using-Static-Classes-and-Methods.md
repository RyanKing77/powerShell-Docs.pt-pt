---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: "Utilizar Classes estáticas e métodos"
ms.assetid: 418ad766-afa6-4b8c-9a44-471889af7fd9
ms.openlocfilehash: fe41c7d6b45564e7b5bc2b922a18587c9745e26d
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2017
---
# <a name="using-static-classes-and-methods"></a>Utilizar Classes estáticas e métodos
Nem todas as classes de .NET Framework podem ser criadas utilizando **New-Object**. Por exemplo, se tentar criar um **System.Environment** ou um **Math** objeto com **New-Object**, obterá as seguintes mensagens de erro:

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

Estes erros ocorrerem porque não é possível criar um novo objeto a partir destas classes. Estas classes são bibliotecas de referência de métodos e propriedades que não alteram o estado. Não precisa de criá-los, basta utilizar. Classes e métodos de como estas são designadas por *classes estáticas* porque não são criados, destruído ou alterados. Para tornar esta limpar fornecemos exemplos que utilizem as classes estáticas.

### <a name="getting-environment-data-with-systemenvironment"></a>Obter dados de ambiente com System.Environment
Normalmente, o primeiro passo para trabalhar com um objeto no Windows PowerShell é Utilize Get-membro para saber quais os membros contém. Classes estático, o processo é ligeiramente diferente, porque a classe real não é um objeto.

#### <a name="referring-to-the-static-systemenvironment-class"></a>Referência para a classe de System.Environment estático
Pode fazer referência a uma classe estática por envolvente o nome de classe com Parênteses Retos. Por exemplo, pode fazer referência a **System.Environment** , escrevendo o nome entre parênteses Retos. Se o fizer, apresenta algumas informações de tipo genérico:

```
PS> [System.Environment]

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     False    Environment                              System.Object
```

> [!NOTE]
> Tal como foi mencionado anteriormente, do Windows PowerShell automaticamente prepends '**System.**' para o tipo de nomes ao utilizar **New-Object**. A mesma coisa ocorre ao utilizar um nome de tipo entre parênteses, pelo que pode especificar  **\[System.Environment]** como  **\[ambiente]**.

O **System.Environment** classe contém informações gerais sobre o ambiente de trabalho para o processo atual, o que é o powershell.exe quando a funcionar dentro do Windows PowerShell.

Se tentar ver os detalhes desta classe, escrevendo  **\[System.Environment] | Get-membro**, o tipo de objeto é reportado como estando **RuntimeType** , não **System.Environment**:

```
PS> [System.Environment] | Get-Member

   TypeName: System.RuntimeType
```

Para ver os membros estáticos com membro Get, especifique o **estático** parâmetro:

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

Agora, pode selecionar propriedades para ver de System.Environment.

#### <a name="displaying-static-properties-of-systemenvironment"></a>Apresentar as propriedades estáticas de System.Environment
As propriedades de System.Environment também são estáticas e tem de ser especificadas de forma diferente de propriedades normais. Utilizamos **::** para indicar ao Windows PowerShell que queremos para trabalhar com um método estático ou uma propriedade. Para ver o comando que foi utilizado para iniciar o Windows PowerShell, verifique o **CommandLine** propriedade escrevendo:

```
PS> [System.Environment]::Commandline
"C:\Program Files\Windows PowerShell\v1.0\powershell.exe"
```

Para verificar a versão do sistema operativo, apresenta a propriedade OSVersion escrevendo:

```
PS> [System.Environment]::OSVersion

           Platform ServicePack         Version             VersionString
           -------- -----------         -------             -------------
            Win32NT Service Pack 2      5.1.2600.131072     Microsoft Windows...
```

Iremos pode verificar se o computador está no processo de encerramento, apresentando o **HasShutdownStarted** propriedade:

```
PS> [System.Environment]::HasShutdownStarted
False
```

### <a name="doing-math-with-systemmath"></a>Se o fizer bibliotecas com Math
A classe estática Math é útil para a execução de algumas operações matemática. Os membros importantes **Math** são principalmente métodos, que iremos pode apresentar usando **Get-membro**.

> [!NOTE]
> Math tem vários métodos com o mesmo nome, mas são distinguidos pelo tipo dos respetivos parâmetros.

Escreva o seguinte comando para listar os métodos do **Math** classe.

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

Esta ação apresenta os vários métodos matemática. Eis uma lista de comandos que demonstram como alguns dos métodos comuns funcionam:

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

