---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Gerir Unidades do Windows PowerShell
ms.assetid: bd809e38-8de9-437a-a250-f30a667d11b4
ms.openlocfilehash: cfc5418e9d2efb1a786817e1b941d75e22291742
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951873"
---
# <a name="managing-windows-powershell-drives"></a>Gerir Unidades do Windows PowerShell

A *unidade do Windows PowerShell* for uma localização de arquivo de dados que pode aceder a como uma unidade de sistema de ficheiros no Windows PowerShell. Os fornecedores do Windows PowerShell criar algumas unidades para si, tais como unidades de sistema de ficheiros (incluindo c e d:), o registo unidades (HKCU: e HKLM:) e a unidade de certificado (Cert:), e pode criar as seus próprios unidades do Windows PowerShell. Estas unidades são muito úteis, mas estão disponíveis apenas dentro do Windows PowerShell. Não é possível aceder-lhes com outras ferramentas do Windows, tais como o Explorador de ficheiros ou Cmd.exe.

O Windows PowerShell utiliza o substantivo **PSDrive**, para comandos que funcionam com o Windows PowerShell unidades. Para obter uma lista do Windows PowerShell unidades na sessão do Windows PowerShell, utilize o **Get-PSDrive** cmdlet.

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

Embora as unidades na apresentação do variar de acordo com as unidades no seu sistema, a listagem terá um aspeto semelhante à saída do **Get-PSDrive** comando mostrado acima.

Unidades de sistema de ficheiros são um subconjunto das unidades do Windows PowerShell. Pode identificar as unidades de sistema de ficheiros pela entrada de sistema de ficheiros na coluna de fornecedor. (As unidades de sistema de ficheiros no Windows PowerShell são suportadas pelo fornecedor de sistema de ficheiros do Windows PowerShell).

Para ver a sintaxe do **Get-PSDrive** cmdlet, escreva um **Get-Command** comando com o **sintaxe** parâmetro:

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

O **PSProvider** permite parâmetro apresentar apenas as unidades do Windows PowerShell que é suportados por um fornecedor específico. Por exemplo, para visualizar apenas as unidades do Windows PowerShell que são suportadas pelo fornecedor de sistema de ficheiros do Windows PowerShell, digite um **Get-PSDrive** comando com o **PSProvider** parâmetro e o  **Sistema de ficheiros** valor:

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

Para ver as unidades do Windows PowerShell que representam nos ramos de registo, utilize o **PSProvider** parâmetro para visualizar apenas as unidades do Windows PowerShell que são suportados pelo fornecedor de registo do Windows PowerShell:

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

### <a name="adding-new-windows-powershell-drives-new-psdrive"></a>Adicionar novo do Windows PowerShell unidades (novo PSDrive)

Pode adicionar as seus próprios unidades do Windows PowerShell utilizando o **New-PSDrive** comando. Para obter a sintaxe para o **New-PSDrive** de comandos, introduza o **Get-Command** comando com o **sintaxe** parâmetro:

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

Para criar uma nova unidade do Windows PowerShell, tem de fornecer três parâmetros:

- Um nome para a unidade (pode utilizar qualquer nome válido do Windows PowerShell)

- O PSProvider (utilize "Sistema de ficheiros" para as localizações do sistema de ficheiros e "Registo de" para as localizações de registo)

- A raiz, ou seja, o caminho para a raiz da unidade de novo

Por exemplo, pode criar uma unidade com o nome "Office" que está mapeado para a pasta que contém as aplicações do Microsoft Office no seu computador, tal como **c:\\os ficheiros de programa\\Microsoft Office\\OFFICE11**. Para criar a unidade, escreva o seguinte comando:

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Micr
osoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> Em geral, os caminhos não são maiúsculas e minúsculas.

Consulte para a nova unidade do Windows PowerShell de forma que todas as unidades do Windows PowerShell – pelo respetivo nome seguido de dois pontos (**:**).

Uma unidade do Windows PowerShell pode efetuar muitas tarefas muito mais simples. Por exemplo, algumas das chaves mais importantes no registo do Windows têm caminhos extremamente longos, torná-los complexa para o acesso e difíceis de lembrar-se. Informações de configuração críticas residem em **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**. Para ver e alterar os itens na chave do registo CurrentVersion, pode criar uma unidade do Windows PowerShell que é ROOT nessa chave escrevendo:

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

O cmdlet New-PsDrive adiciona a nova unidade, apenas para a sessão atual do Windows PowerShell. Se fechar a janela do Windows PowerShell, a nova unidade é perdida. Para guardar uma unidade do Windows PowerShell, utilize o cmdlet Export-consola para exportar a sessão atual do Windows PowerShell e, em seguida, utilize o PowerShell.exe **PSConsoleFile** parâmetro importá-la. Em alternativa, adicionar a unidade de novo para o seu perfil do Windows PowerShell.

### <a name="deleting-windows-powershell-drives-remove-psdrive"></a>A eliminação do Windows PowerShell unidades (remover-PSDrive)

Pode eliminar unidades do Windows PowerShell utilizando o **remover PSDrive** cmdlet. O **remover PSDrive** cmdlet é fácil de utilizar; para eliminar a unidade do Windows PowerShell específica, basta fornecer o nome da unidade do Windows PowerShell.

Por exemplo, se tiver adicionado o **Office:** unidade do Windows PowerShell, conforme mostrado no **New-PSDrive** tópico, que pode eliminá-lo escrevendo:

```powershell
Remove-PSDrive -Name Office
```

Para eliminar o **cvkey:** do Windows PowerShell de unidade, também apresentado no **New-PSDrive** tópico, utilize o seguinte comando:

```powershell
Remove-PSDrive -Name cvkey
```

É mais fácil eliminar uma unidade do Windows PowerShell, mas não é possível eliminar enquanto estiver na unidade. Por exemplo:

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

### <a name="adding-and-removing-drives-outside-windows-powershell"></a>Adicionar e remover unidades fora do Windows PowerShell

Windows PowerShell Deteta as unidades do sistema de ficheiros que são adicionadas ou removidas no Windows, incluindo unidades de rede que estão mapeadas, unidades USB ligadas e unidades são eliminadas utilizando o **net utilize** comando ou o  **WScript.NetworkMapNetworkDrive** e **RemoveNetworkDrive** métodos de um script de Script anfitrião para WSH (Windows).