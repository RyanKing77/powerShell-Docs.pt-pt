---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Utilizar Classes e Métodos Estáticos
ms.assetid: 418ad766-afa6-4b8c-9a44-471889af7fd9
ms.openlocfilehash: e4caff63a1ec7295b6fe450c2915baf0cc7e31af
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293117"
---
# <a name="using-static-classes-and-methods"></a>Utilizar Classes e Métodos Estáticos

Nem todas as classes do .NET Framework podem ser criadas usando **New-Object**. Por exemplo, se tentar criar uma **System.Environment** ou uma **Math** objeto com **New-Object**, irá obter as mensagens de erro seguinte:

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

Estes erros ocorrerem porque não é possível criar um novo objeto dessas classes. Essas classes são bibliotecas de referência de métodos e propriedades que não alterar o estado. Não precisa de criá-los, simplesmente usá-los. Classes e métodos como esses são chamados *classes estáticas* porque eles não forem criados, destruído ou alterados. Para tornar isso claro, forneceremos exemplos que usam classes estáticas.

## <a name="getting-environment-data-with-systemenvironment"></a>Obter dados de ambiente com System.Environment

Normalmente, a primeira etapa ao trabalhar com um objeto no Windows PowerShell é usar o Get-Member para saber quais os membros contém. Com as classes estáticas, o processo é um pouco diferente porque a classe real não é um objeto.

### <a name="referring-to-the-static-systemenvironment-class"></a>Que faça referência à classe System.Environment estático

Pode consultar a uma classe estática, ao nome da classe com Parênteses Retos. Por exemplo, pode consultar **System.Environment** digitando o nome entre parênteses. Se o fizer, apresenta algumas informações de tipo genérico:

```
PS> [System.Environment]

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     False    Environment                              System.Object
```

> [!NOTE]
> Como mencionado anteriormente, Windows PowerShell automaticamente acrescenta '**System.**' digitar nomes ao utilizar **New-Object**. A mesma coisa acontece quando utilizar um nome de tipo entre parênteses, então, pode especificar  **\[System.Environment]** como  **\[ambiente]**.

O **System.Environment** classe contém informações gerais sobre o ambiente de trabalho para o processo atual, o que é powershell.exe quando trabalhar dentro do Windows PowerShell.

Se tentar ver os detalhes dessa classe, escrevendo  **\[System.Environment] | Get-Member**, o tipo de objeto é comunicado como sendo **System.RuntimeType** , e não **System.Environment**:

```
PS> [System.Environment] | Get-Member

   TypeName: System.RuntimeType
```

Para ver os membros estáticos com Get-Member, especifique a **estático** parâmetro:

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

Agora podemos selecionar as propriedades para ver a partir System.Environment.

### <a name="displaying-static-properties-of-systemenvironment"></a>Exibir propriedades estáticas da System.Environment

As propriedades de System.Environment também são estáticas e tem de ser especificadas de outra forma de propriedades normais. Usamos **::** para indicar ao Windows PowerShell que queremos trabalhar com um método estático ou uma propriedade. Para ver o comando que utilizou para iniciar o Windows PowerShell, verificamos os **CommandLine** propriedade digitando:

```
PS> [System.Environment]::Commandline
"C:\Program Files\Windows PowerShell\v1.0\powershell.exe"
```

Para verificar a versão do sistema operativo, exiba a propriedade OSVersion digitando:

```
PS> [System.Environment]::OSVersion

           Platform ServicePack         Version             VersionString
           -------- -----------         -------             -------------
            Win32NT Service Pack 2      5.1.2600.131072     Microsoft Windows...
```

Podemos verificar se o computador está no processo de encerramento ao apresentar o **HasShutdownStarted** propriedade:

```
PS> [System.Environment]::HasShutdownStarted
False
```

## <a name="doing-math-with-systemmath"></a>Fazer cálculos com Math

A classe estática System é útil para realizar algumas operações matemáticas. Os membros importantes **Math** são principalmente métodos, que podemos exibir usando **Get-Member**.

> [!NOTE]
> Math tem vários métodos com o mesmo nome, mas eles são distinguidos pelo tipo de seus parâmetros.

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

Esta ação apresenta vários métodos de matemáticos. Aqui está uma lista de comandos que demonstram como alguns dos métodos comuns funcionam:

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