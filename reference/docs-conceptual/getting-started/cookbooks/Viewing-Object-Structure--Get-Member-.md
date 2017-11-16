---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: "Membro de Get de estrutura de objeto de visualização"
ms.assetid: a1819ed2-2ef3-453a-b2b0-f3589c550481
ms.openlocfilehash: 618f34bca7bfb76ce5d48ada642a687e279c8aad
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/31/2017
---
# <a name="viewing-object-structure-get-member"></a>Visualizar a estrutura de objeto (Get-membro)
Porque os objetos reproduzir essa uma função central no Windows PowerShell, existem vários comandos nativos concebidos para trabalhar com os tipos de objeto arbitrários. O mais importante é o **Get-membro** comando.

A técnica mais simples para analisar os objetos que um comando devolve é para encaminhar a saída desse comando para o **Get-membro** cmdlet. O **Get-membro** cmdlet mostra-lhe o nome do tipo de objeto formal e uma lista completa dos seus membros. O número de elementos que são devolvidos por vezes, pode ser muito confuso. Por exemplo, um objeto de processo pode ter mais de 100 membros.

Para ver todos os membros de um objeto de processo e a saída de página, para que possa visualizar todos, escreva:

```
PS> Get-Process | Get-Member | Out-Host -Paging
```

O resultado deste comando será algo semelhante ao seguinte:

```
TypeName: System.Diagnostics.Process

Name                           MemberType     Definition
----                           ----------     ----------
Handles                        AliasProperty  Handles = Handlecount
Name                           AliasProperty  Name = ProcessName
NPM                            AliasProperty  NPM = NonpagedSystemMemorySize
PM                             AliasProperty  PM = PagedMemorySize
VM                             AliasProperty  VM = VirtualMemorySize
WS                             AliasProperty  WS = WorkingSet
add_Disposed                   Method         System.Void add_Disposed(Event...
...
```

Iremos pode tornar esta longa lista de informações mais utilizável através de filtragem para elementos que queremos ver. O **Get-membro** comando permite-lhe listar apenas os membros que são propriedades. Existem várias formas de propriedades. O cmdlet apresenta as propriedades de qualquer tipo, se definimos os **Get-membro MemberType** parâmetro para o valor **propriedades**. A lista resultante ainda está a ser muito longas, mas um pouco mais fácil gerir:

```
PS> Get-Process | Get-Member -MemberType Properties

   TypeName: System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Handles                    AliasProperty  Handles = Handlecount
Name                       AliasProperty  Name = ProcessName
...
ExitCode                   Property       System.Int32 ExitCode {get;}
...
Handle                     Property       System.IntPtr Handle {get;}
...
CPU                        ScriptProperty System.Object CPU {get=$this.Total...
...
Path                       ScriptProperty System.Object Path {get=$this.Main...
...
```

> [!NOTE]
> Os valores permitidos de MemberType são AliasProperty, CodeProperty, propriedade, NoteProperty, ScriptProperty, propriedades, PropertySet, método, CodeMethod, ScriptMethod, métodos, ParameterizedProperty, MemberSet e todos os.

Existem mais de 60 propriedades para um processo. O motivo que do Windows PowerShell, muitas vezes, mostra que apenas alguns a propriedades de qualquer objecto bem conhecido é o facto de que todos eles mostra produziria uma unmanageable quantidade de informações.

> [!NOTE]
> Windows PowerShell determina como apresentar um tipo de objeto através da utilização de informações armazenadas em ficheiros XML com nomes terminados em. format.ps1xml. Os dados de formatação de objetos do processo, que são objetos System .NET, são armazenados no DotNetTypes.format.ps1xml.

Se precisar de ver as propriedades além das que do Windows PowerShell apresenta por predefinição, terá de formatar os dados de saída por si. Isto pode ser feito utilizando os cmdlets de formato.

