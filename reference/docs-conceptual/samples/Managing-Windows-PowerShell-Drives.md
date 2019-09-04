---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Gerir Unidades do Windows PowerShell
ms.openlocfilehash: 5d1aba459caeaab2542e17e74534da6713b0faa9
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215518"
---
# <a name="managing-windows-powershell-drives"></a>Gerir Unidades do Windows PowerShell

Uma *unidade do Windows PowerShell* é um local de armazenamento de dados que você pode acessar como uma unidade do sistema de arquivos no Windows PowerShell. Os provedores do Windows PowerShell criam algumas unidades para você, como as unidades do sistema de arquivos (incluindo C: e D:), as unidades do registro (HKCU: e HKLM:), e a unidade de certificado (CERT:), e você pode criar suas próprias unidades do Windows PowerShell. Essas unidades são muito úteis, mas estão disponíveis apenas no Windows PowerShell. Você não pode acessá-los usando outras ferramentas do Windows, como o explorador de arquivos ou cmd. exe.

O Windows PowerShell usa o substantivo, **PSDrive**, para comandos que funcionam com unidades do Windows PowerShell. Para obter uma lista das unidades do Windows PowerShell na sua sessão do Windows PowerShell, use o cmdlet **Get-PSDrive** .

```
PS> Get-PSDrive

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
Alias      Alias
C          FileSystem    C:\                                 ...And Settings\me
cert       Certificate   \
D          FileSystem    D:\
Env        Environment
Function   Function
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
Variable   Variable
```

Embora as unidades na exibição variem de acordo com as unidades no seu sistema, a listagem será semelhante à saída do comando **Get-PSDrive** mostrado acima.

As unidades do sistema de arquivos são um subconjunto das unidades do Windows PowerShell. Você pode identificar as unidades do sistema de arquivos pela entrada FileSystem na coluna provedor. (As unidades do sistema de arquivos no Windows PowerShell são suportadas pelo provedor do sistema de arquivos do Windows PowerShell.)

Para ver a sintaxe do cmdlet **Get-PSDrive** , digite um comando **Get-Command** com o parâmetro **Syntax** :

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

O parâmetro **PSProvider** permite exibir apenas as unidades do Windows PowerShell com suporte em um provedor específico. Por exemplo, para exibir apenas as unidades do Windows PowerShell com suporte no provedor do sistema de arquivos do Windows PowerShell, digite um comando **Get-PSDrive** com o parâmetro **PSProvider** e o valor **FileSystem** :

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

Para exibir as unidades do Windows PowerShell que representam os hives do registro, use o parâmetro **PSProvider** para exibir apenas as unidades do Windows PowerShell com suporte no provedor de registro do Windows PowerShell:

```
PS> Get-PSDrive -PSProvider Registry

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
```

Você também pode usar os cmdlets de local padrão com as unidades do Windows PowerShell:

```
PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location

Path
----
HKLM:\SOFTWARE\Microsoft
```

## <a name="adding-new-windows-powershell-drives-new-psdrive"></a>Adicionando novas unidades do Windows PowerShell (New-PSDrive)

Você pode adicionar suas próprias unidades do Windows PowerShell usando o comando **New-PSDrive** . Para obter a sintaxe para o comando **New-PSDrive** , insira o comando **Get-Command** com o parâmetro **Syntax** :

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

Para criar uma nova unidade do Windows PowerShell, você deve fornecer três parâmetros:

- Um nome para a unidade (você pode usar qualquer nome do Windows PowerShell válido)

- O PSProvider (use "FileSystem" para locais de sistema de arquivos e "registro" para locais de registro)

- A raiz, ou seja, o caminho para a raiz da nova unidade

Por exemplo, você pode criar uma unidade chamada "Office" que é mapeada para a pasta que contém os aplicativos Microsoft Office em seu computador, como **C:\\arquivos\\de programas Microsoft Office\\OFFICE11**. Para criar a unidade, digite o seguinte comando:

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Microsoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> Em geral, os caminhos não diferenciam maiúsculas de minúsculas.

Você faz referência à nova unidade do Windows PowerShell à medida que todas as unidades do Windows PowerShell, por seu nome, seguido por dois-pontos ( **:** ).

Uma unidade do Windows PowerShell pode tornar muitas tarefas muito mais simples. Por exemplo, algumas das chaves mais importantes no registro do Windows têm caminhos extremamente longos, tornando-os difíceis de serem acessados e difíceis de se lembrar. As informações de configuração críticas residem **em\\HKEY_LOCAL_MACHINE\\software\\Microsoft\\Windows CurrentVersion**. Para exibir e alterar itens na chave do registro CurrentVersion, você pode criar uma unidade do Windows PowerShell com raiz nessa chave digitando:

```
PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\Windows\CurrentVersion

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...
```

Em seguida, você pode alterar o local para a unidade **unidade cvkey:** como faria com qualquer outra unidade:

```
PS> cd cvkey:
```

ou:

```
PS> Set-Location cvkey: -PassThru

Path
----
cvkey:\
```

O cmdlet New-PsDrive adiciona a nova unidade somente à sessão atual do Windows PowerShell. Se você fechar a janela do Windows PowerShell, a nova unidade será perdida. Para salvar uma unidade do Windows PowerShell, use o cmdlet Export-Console para exportar a sessão atual do Windows PowerShell e, em seguida, use o parâmetro **PSConsoleFile** do PowerShell. exe para importá-la. Ou adicione a nova unidade ao seu perfil do Windows PowerShell.

## <a name="deleting-windows-powershell-drives-remove-psdrive"></a>Excluindo unidades do Windows PowerShell (Remove-PSDrive)

Você pode excluir unidades do Windows PowerShell usando o cmdlet **Remove-PSDrive** . O cmdlet **Remove-PSDrive** é fácil de usar; para excluir uma unidade específica do Windows PowerShell, basta fornecer o nome da unidade do Windows PowerShell.

Por exemplo, se você adicionou o **escritório:** Unidade do Windows PowerShell, conforme mostrado no tópico **New-PSDrive** , você pode excluí-lo digitando:

```powershell
Remove-PSDrive -Name Office
```

Para excluir o **unidade cvkey:** Unidade do Windows PowerShell, também mostrada no tópico **New-PSDrive** , use o seguinte comando:

```powershell
Remove-PSDrive -Name cvkey
```

É fácil excluir uma unidade do Windows PowerShell, mas você não pode excluí-la enquanto estiver na unidade. Por exemplo:

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

## <a name="adding-and-removing-drives-outside-windows-powershell"></a>Adicionando e removendo unidades fora do Windows PowerShell

O Windows PowerShell detecta unidades de sistema de arquivos que são adicionadas ou removidas no Windows, incluindo unidades de rede mapeadas, unidades USB que são anexadas e unidades que são excluídas usando o comando **net use** ou o  **Métodos WScript. NetworkMapNetworkDrive** e **RemoveNetworkDrive** de um script do WSH (Windows Script Host).
