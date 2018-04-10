---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Utilizar Variáveis para Armazenar Objetos
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: e52f0a344d0ad13db42b34bed912d584c99b0e30
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="using-variables-to-store-objects"></a>Utilizar Variáveis para Armazenar Objetos
PowerShell funciona com objetos. PowerShell permite-lhe criar variáveis, essencialmente com o nome de objetos, para preservar a saída para utilização posterior. Se forem utilizados para trabalhar com variáveis noutras shells Lembre-se de que as variáveis de PowerShell são objetos, não texto.

Variáveis são sempre especificadas com o caráter inicial $ e podem incluir quaisquer carateres alfanuméricos ou o caráter de sublinhado nos respetivos nomes.

### <a name="creating-a-variable"></a>Criar uma variável
Pode criar uma variável, escrevendo um nome de variável válido:

```
PS> $loc
PS>
```

Esta ação não devolve nenhum resultado porque **$loc** não tem um valor. Pode criar uma variável e atribua-lhe um valor no mesmo passo. PowerShell apenas cria a variável se não existir; caso contrário, atribui o valor especificado para a variável existente. Para armazenar a sua localização atual na variável **$loc**, tipo:

```
$loc = Get-Location
```

Não há nenhuma saída apresentada quando escreva este comando porque o resultado é enviado para $loc. No PowerShell, o resultado apresentado é um efeito de facto de dados, que não é; caso contrário, direcionado, sempre são enviados para o ecrã. Escrever $loc mostrará a sua localização atual:

```
PS> $loc

Path
----
C:\temp
```

Pode utilizar **Get-membro** para apresentar informações sobre o conteúdo das variáveis. Encaminhando $loc Get-membro irá mostrar-lhe que é um **PathInfo** objeto, tal como o resultado de Get-localização:

```
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

### <a name="manipulating-variables"></a>Manipulação de variáveis
PowerShell fornece vários comandos para manipular variáveis. Pode ver uma lista completa num formulário legível escrevendo:

```
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

Para além das variáveis de que criar na sua sessão atual do PowerShell, existem várias variáveis definidas pelo sistema. Pode utilizar o **Remove-Variable** cmdlet para limpar terminar todas as variáveis que não são controladas através do PowerShell. Escreva o seguinte comando para limpar todas as variáveis:

```
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

Isto produzirá o pedido de confirmação, que veja a seguir.

```
Confirm
Are you sure you want to perform this action?
Performing operation "Remove Variable" on Target "Name: Error".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):A
```

Se, em seguida, executar o **Get-Variable** cmdlet, verá as variáveis de PowerShell restantes. Uma vez que também é uma variável de unidade do PowerShell, também pode apresentar todas as variáveis de PowerShell, escrevendo:

```
Get-ChildItem variable:
```

### <a name="using-cmdexe-variables"></a>Utilizar variáveis Cmd.exe
Apesar de PowerShell não Cmd.exe, é executado num ambiente de shell de comandos e pode utilizar as variáveis mesmas disponíveis em qualquer ambiente do Windows. Estas variáveis são expostas através de uma unidade com o nome **env**:. Pode ver estas variáveis, escrevendo:

```
Get-ChildItem env:
```

Embora os cmdlets de variável padrão não foram concebidos para funcionar com **env:** variáveis, pode continuar a utilizá-los, especificando o **env:** prefixo. Por exemplo, para ver o diretório de raiz do sistema operativo, pode utilizar a shell de comandos **% SystemRoot %** variável do PowerShell, escrevendo:

```
PS> $env:SystemRoot
C:\WINDOWS
```

Também pode criar e modificar variáveis de ambiente de PowerShell. Variáveis de ambiente acedidas a partir do Windows PowerShell está em conformidade com as regras normais nas variáveis de ambiente noutro local do Windows.