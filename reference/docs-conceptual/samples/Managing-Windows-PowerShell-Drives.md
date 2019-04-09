---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Gerir Unidades do Windows PowerShell
ms.assetid: bd809e38-8de9-437a-a250-f30a667d11b4
ms.openlocfilehash: 9ac5136fb28b450ea6397cab2f36082c50f22e1f
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293253"
---
# <a name="managing-windows-powershell-drives"></a>Gerir Unidades do Windows PowerShell

R *unidade do Windows PowerShell* for uma localização de arquivo de dados que pode acessar como uma unidade de sistema de ficheiros no Windows PowerShell. Os fornecedores de Windows PowerShell criar algumas unidades, tais como unidades de sistema de ficheiros (incluindo c: e d:), o registro unidades (HKCU: e HKLM:) e a unidade de certificado (Cert:), e pode criar suas próprias unidades do Windows PowerShell. Estas unidades são muito úteis, mas estão disponíveis apenas no Windows PowerShell. Não é possível acessá-los com outras ferramentas do Windows, como o Explorador de ficheiros ou Cmd.exe.

Windows PowerShell utiliza o substantivo **PSDrive**, para os comandos que funcionam com o Windows PowerShell unidades. Para unidades de uma lista do Windows PowerShell na sua sessão do Windows PowerShell, utilize o **Get-PSDrive** cmdlet.

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

Embora as unidades na exibição variam com as unidades no seu sistema, a listagem terá um aspeto semelhante à saída dos **Get-PSDrive** comando mostrado acima.

Unidades de sistema de ficheiros são um subconjunto das unidades do Windows PowerShell. Pode identificar as unidades de sistema de ficheiros pela entrada de sistema de ficheiros na coluna de fornecedor. (As unidades de sistema de ficheiros no Windows PowerShell são suportadas pelo fornecedor de sistema de ficheiros do Windows PowerShell.)

Para ver a sintaxe do **Get-PSDrive** cmdlet, escreva um **Get-Command** comando com o **sintaxe** parâmetro:

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

O **PSProvider** permite parâmetro apresentar apenas o Windows PowerShell unidades que é suportados por um fornecedor específico. Por exemplo, para apresentar apenas as unidades do Windows PowerShell que são suportadas pelo fornecedor de sistema de ficheiros do Windows PowerShell, escreva um **Get-PSDrive** comando com o **PSProvider** parâmetro e o  **Sistema de ficheiros** valor:

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

Para ver as unidades do Windows PowerShell que representam os hives do Registro, utilize o **PSProvider** parâmetro para visualizar apenas o Windows PowerShell unidades que são suportados pelo fornecedor de registo do Windows PowerShell:

```
PS> Get-PSDrive -PSProvider Registry

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
```

Também pode utilizar os cmdlets de localização padrão com as unidades do Windows PowerShell:

```
PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location

Path
----
HKLM:\SOFTWARE\Microsoft
```

## <a name="adding-new-windows-powershell-drives-new-psdrive"></a>Adicionar nova do Windows PowerShell unidades (novo PSDrive)

Pode adicionar suas próprias unidades do Windows PowerShell utilizando o **New-PSDrive** comando. Para obter a sintaxe para o **New-PSDrive** comando, introduza o **Get-Command** comando com o **sintaxe** parâmetro:

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

Para criar uma nova unidade do Windows PowerShell, deve fornecer três parâmetros:

- Um nome para a unidade (pode usar qualquer nome válido do Windows PowerShell)

- O PSProvider (utilize "Sistema de ficheiros" para localizações de sistema de ficheiros e "Registro" para localizações de registo)

- A raiz, ou seja, o caminho para a raiz da unidade de novo

Por exemplo, pode criar uma unidade com o nome "Office", que é mapeado para a pasta que contém os aplicativos do Microsoft Office no seu computador, tal como **c:\\arquivos de programas\\Microsoft Office\\OFFICE11**. Para criar a unidade, escreva o seguinte comando:

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Micr
osoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> Em geral, os caminhos não diferenciam maiúsculas de minúsculas.

Consultar a nova unidade do Windows PowerShell, tal como sucede todas as unidades do Windows PowerShell – pelo respetivo nome seguido de dois pontos (**:**).

Uma unidade do Windows PowerShell pode fazer muitas tarefas muito mais simples. Por exemplo, algumas as chaves mais importantes no registo do Windows têm caminhos extremamente longos, tornando-os complicado para o acesso e difícil lembrar-se. Informações de configuração críticas residem sob **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**. Para ver e alterar itens na chave do registo de CurrentVersion, pode criar uma unidade do Windows PowerShell que está enraizada nessa chave ao escrever:

```
PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\W
indows\CurrentVersion

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...
```

Em seguida, pode alterar a localização para o **cvkey:** unidade como faria com qualquer outra unidade: '

`PS> cd cvkey:`

ou:

```
PS> Set-Location cvkey: -PassThru

Path
----
cvkey:\
```

O novo cmdlet PsDrive adiciona o novo disco apenas à sessão atual do Windows PowerShell. Se fechar a janela do Windows PowerShell, a nova unidade é perdida. Para guardar uma unidade do Windows PowerShell, utilize o cmdlet Export-Console para exportar a sessão atual do Windows PowerShell e, em seguida, utilize o PowerShell.exe **PSConsoleFile** parâmetro importá-lo. Em alternativa, adicione a nova unidade ao seu perfil do Windows PowerShell.

## <a name="deleting-windows-powershell-drives-remove-psdrive"></a>A eliminar o Windows PowerShell unidades (remover-PSDrive)

Pode eliminar unidades do Windows PowerShell utilizando o **Remove-PSDrive** cmdlet. O **Remove-PSDrive** cmdlet é fácil de usar; para eliminar uma unidade específica do Windows PowerShell, apenas que fornecer o nome de unidade do Windows PowerShell.

Por exemplo, se tiver adicionado o **Office:** Unidade do Windows PowerShell, como mostra a **New-PSDrive** tópico, pode eliminá-la digitando:

```powershell
Remove-PSDrive -Name Office
```

Para eliminar o **cvkey:** Windows PowerShell de unidade, também mostra a **New-PSDrive** tópico, utilize o seguinte comando:

```powershell
Remove-PSDrive -Name cvkey
```

É mais fácil eliminar uma unidade do Windows PowerShell, mas não é possível eliminá-lo enquanto estiver na unidade. Por exemplo:

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

## <a name="adding-and-removing-drives-outside-windows-powershell"></a>Adicionar e remover unidades fora do Windows PowerShell

Windows PowerShell Deteta as unidades de sistema de ficheiros que são adicionadas ou removidas do Windows, incluindo unidades de rede mapeadas, unidades USB que estão ligadas e unidades de que são eliminadas utilizando o **net use** comando ou o  **WScript.NetworkMapNetworkDrive** e **RemoveNetworkDrive** métodos de um script do Windows Script Host (WSH).