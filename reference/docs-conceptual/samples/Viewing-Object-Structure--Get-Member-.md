---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Membro do Get de estrutura de objeto de visualização
ms.openlocfilehash: 80b36abd303a708195f12d96511e616178d11b5a
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030714"
---
# <a name="viewing-object-structure-get-member"></a>Ver a estrutura de objetos (Get-Member)

Porque objetos desempenham um papel central no Windows PowerShell, há vários comandos nativos concebidos para trabalhar com tipos de objetos arbitrários. O mais importante é o **Get-Member** comando.

A técnica mais simples para analisar os objetos que retorna um comando é encaminhar a saída do comando para o **Get-Member** cmdlet. O **Get-Member** cmdlet mostra-lhe o nome formal do tipo de objeto e uma lista completa dos seus membros. O número de elementos que são devolvidos às vezes, pode ser absurdo. Por exemplo, um objeto de processo pode ter mais de 100 membros.

Para ver todos os membros de um objeto de processo e a saída de página, para que pode ver todos os-lo, escreva:

```powershell
Get-Process | Get-Member | Out-Host -Paging
```

O resultado deste comando será algo parecido com isto:

```output
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

Podemos fazer essa longa lista de informações mais utilizável ao filtrar para elementos que queremos ver. O **Get-Member** comando permite que listar apenas os membros que são propriedades. Existem várias formas de propriedades. O cmdlet apresenta as propriedades de qualquer tipo, se definirmos os **Get-Member MemberType** parâmetro para o valor **propriedades**. A lista resultante ainda é muito longo, mas um pouco mais fáceis de gerir:

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
> Os valores permitidos de MemberType pedidos são AliasProperty, CodeProperty, propriedade, NoteProperty, ScriptProperty, propriedades, PropertySet, método, CodeMethod, ScriptMethod, métodos, ParameterizedProperty, MemberSet e tudo.

Existem mais de 60 propriedades para um processo. O motivo pelo qual que Windows PowerShell, muitas vezes, mostra que apenas algumas poucas propriedades para qualquer objeto conhecido é que mostrando todos eles produziria uma impossível de gerenciar quantidade de informações.

> [!NOTE]
> Windows PowerShell determina como exibir um tipo de objeto ao utilizar as informações armazenadas em arquivos XML que têm nomes que terminem em. format.ps1xml. Os dados de formatação para objetos de processo, o que são objetos .NET Diagnostics, são armazenados no DotNetTypes.format.ps1xml.

Se precisar de ver propriedades além das que o Windows PowerShell apresenta por predefinição, terá de formatar os dados de saída por conta própria. Isso pode ser feito utilizando os cmdlets de formato.
