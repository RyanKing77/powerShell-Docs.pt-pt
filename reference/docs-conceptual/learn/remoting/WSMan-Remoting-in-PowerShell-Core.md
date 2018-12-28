---
title: Comunicação Remota do WS-Management (WSMan) no PowerShell Core
description: Comunicação remota do PowerShell Core através de WSMan
ms.date: 08/06/2018
ms.openlocfilehash: ce58ed88f59f32b0f83951e55de36e829f7fa3f4
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405566"
---
# <a name="ws-management-wsman-remoting-in-powershell-core"></a>Comunicação Remota do WS-Management (WSMan) no PowerShell Core

## <a name="instructions-to-create-a-remoting-endpoint"></a>Instruções para criar um ponto de extremidade de comunicação remota

O pacote do PowerShell Core para Windows inclui um plug-in de WinRM (`pwrshplugin.dll`) e um script de instalação (`Install-PowerShellRemoting.ps1`) no `$PSHome`.
Estes ficheiros ativar o PowerShell aceitar ligações remotas recebidas do PowerShell quando é especificado o seu ponto de extremidade.

### <a name="motivation"></a>Motivação

Uma instalação do PowerShell pode estabelecer sessões do PowerShell para computadores remotos utilizando `New-PSSession` e `Enter-PSSession`.
Para ativá-la aceitar ligações remotas recebidas do PowerShell, o utilizador tem de criar um ponto de extremidade de comunicação remota do WinRM.
Este é um explícito Inscreva-se no cenário em que o usuário executa Install-PowerShellRemoting.ps1 para criar o ponto de extremidade do WinRM.
O script de instalação é uma solução de curto prazo, até que podemos adicionar funcionalidade adicional para `Enable-PSRemoting` para executar a mesma ação.
Para obter mais detalhes, consulte problema [#1193](https://github.com/PowerShell/PowerShell/issues/1193).

### <a name="script-actions"></a>Ações de script

O script

1. Cria um diretório para o plug-in dentro %windir%\System32\PowerShell
1. Copia pwrshplugin.dll para essa localização
1. Gera um ficheiro de configuração
1. Registros ou plug-ins do WinRM

### <a name="registration"></a>Registo

O script tem de ser executado dentro de uma sessão do PowerShell de nível de administrador e é executado em dois modos.

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a>Executado pela instância do PowerShell que serão registados

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a>Executado por outra instância do PowerShell em nome da instância que serão registados

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

Por exemplo:

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

**NOTA:** O script de registro de comunicação remota reiniciará o WinRM, para que todas as sessões PSRP existentes serão encerrado imediatamente após o script é executado. Se executar durante uma sessão remota, isso irá terminar a ligação.

## <a name="how-to-connect-to-the-new-endpoint"></a>Como se pode ligar para o novo ponto final

Criar uma sessão de PowerShell para o novo ponto de final do PowerShell, especificando `-ConfigurationName "some endpoint name"`. Para ligar à instância do PowerShell do exemplo acima, utilize qualquer um dos seguintes itens:

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

Tenha em atenção que `New-PSSession` e `Enter-PSSession` invocações de que não especificam `-ConfigurationName` destina-se o ponto de final do PowerShell de predefinido, `microsoft.powershell`.