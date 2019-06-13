---
ms.date: 08/27/2018
keywords: PowerShell, o cmdlet
title: Utilizar Variáveis para Armazenar Objetos
ms.openlocfilehash: 2d20d84e48d3f68cab5c1ffa05d689b46415ebc8
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030363"
---
# <a name="using-variables-to-store-objects"></a>Utilizar variáveis para armazenar objetos

PowerShell funciona com objetos. PowerShell permite-lhe criar objetos nomeados, conhecidos como variáveis.
Os nomes das variáveis podem incluir o caráter de sublinhado e quaisquer carateres alfanuméricos. Quando utilizado no PowerShell, uma variável é sempre especificada usando a \$ caracteres seguido pelo nome da variável.

## <a name="creating-a-variable"></a>Criar uma variável

Pode criar uma variável, escrevendo um nome de variável válido:

```
PS> $loc
PS>
```

Neste exemplo não retornará nenhum resultado porque `$loc` não tem um valor. Pode criar uma variável e atribua-lhe um valor na mesma etapa. PowerShell cria a variável apenas se não existir.
Caso contrário, atribui o valor especificado para a variável existente. O exemplo seguinte armazena a localização atual na variável `$loc`:

```powershell
$loc = Get-Location
```

PowerShell não apresenta nenhuma saída quando digitar este comando. PowerShell envia a saída de Get-Location para `$loc`. No PowerShell, os dados que não estão atribuídos ou redirecionados são enviados para o ecrã. Escrever `$loc` mostra sua localização atual:

```
PS> $loc

Path
----
C:\temp
```

Pode usar `Get-Member` para apresentar informações sobre o conteúdo das variáveis. `Get-Member` mostra-lhe que `$loc` é um **PathInfo** objeto, assim como a saída do `Get-Location`:

```powershell
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

## <a name="manipulating-variables"></a>Manipulação de variáveis

PowerShell fornece vários comandos para manipular as variáveis. Pode ver uma lista completa num formato legível digitando:

```powershell
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

PowerShell também cria várias variáveis definidas pelo sistema. Pode utilizar o `Remove-Variable` cmdlet para remover as variáveis, que não são controladas pelo PowerShell, da sessão atual. Escreva o seguinte comando para limpar todas as variáveis:

```powershell
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

Depois de executar o comando anterior, o `Get-Variable` cmdlet mostra as variáveis de sistema do PowerShell.

PowerShell também cria uma unidade de variável. Utilize o exemplo a seguir para exibir todas as variáveis do PowerShell usando a unidade de variável:

```powershell
Get-ChildItem variable:
```

## <a name="using-cmdexe-variables"></a>Usando variáveis cmd.exe

PowerShell, pode utilizar as variáveis de ambiente mesmo disponíveis a qualquer processo do Windows, incluindo **cmd.exe**. Estas variáveis são expostas por meio de uma unidade chamada `env:`. Pode ver estas variáveis, escrevendo o seguinte comando:

```powershell
Get-ChildItem env:
```

O padrão `*-Variable` cmdlets não são concebidos para trabalhar com variáveis de ambiente. Variáveis de ambiente são acessadas usando o `env:` prefixo de unidade. Por exemplo, o **% SystemRoot %** variável **cmd.exe** contém o nome de diretório de raiz do sistema operacional. No PowerShell, utilize `$env:SystemRoot` para acessar o mesmo valor.

```
PS> $env:SystemRoot
C:\WINDOWS
```

Também pode criar e modificar variáveis de ambiente a partir do PowerShell. Variáveis de ambiente no PowerShell, siga as mesmas regras para variáveis de ambiente utilizadas em outro lugar no sistema operativo. O exemplo seguinte cria uma nova variável de ambiente:

```powershell
$env:LIB_PATH='/usr/local/lib'
```

Embora não obrigatório, é comum para nomes de variáveis de ambiente utilizar todas as letras maiúsculas.
