---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 9065315ef39129e6a28234d972fe350fd5e7e11d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="creating-and-connecting-to-a-jea-endpoint"></a>Criar e Estabelecer Ligação a um Ponto Final da JEA
Para criar um ponto final JEA, tem de criar e registar um ficheiro de configuração de sessão do PowerShell especial configurada, o que pode ser gerado com o **New-PSSessionConfigurationFile** cmdlet.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -TranscriptDirectory "C:\ProgramData\JEATranscripts" -RunAsVirtualAccount -RoleDefinitions @{ 'CONTOSO\NonAdmin_Operators' = @{ RoleCapabilities = 'Maintenance' }} -Path "$env:ProgramData\JEAConfiguration\Demo.pssc"
```

Isto irá criar um ficheiro de configuração de sessão que tem este aspeto:
```powershell
@{

# Version number of the schema used for this document
SchemaVersion = '2.0.0.0'

# ID used to uniquely identify this document
GUID = 'a384fdd3-5830-4a2c-ac86-cdd1822c3afd'

# Author of this document
Author = 'Administrator'

# Description of the functionality provided by these settings
# Description = ''

# Session type defaults to apply for this session configuration. Can be 'RestrictedRemoteServer' (recommended), 'Empty', or 'Default'
SessionType = 'RestrictedRemoteServer'

# Directory to place session transcripts for this session configuration
TranscriptDirectory = 'C:\ProgramData\JEATranscripts'

# Whether to run this session configuration as the machine's (virtual) administrator account
RunAsVirtualAccount = $true

# Groups associated with machine's (virtual) administrator account
# RunAsVirtualAccountGroups = 'Remote Desktop Users', 'Remote Management Users'

# Scripts to run when applied to a session
# ScriptsToProcess = 'C:\ConfigData\InitScript1.ps1', 'C:\ConfigData\InitScript2.ps1'

# User roles (security groups), and the Role Capabilities that should be applied to them when applied to a session
RoleDefinitions = @{
    'CONTOSO\NonAdmin_Operators' = @{
        'RoleCapabilities' = 'Maintenance' } }

}
```
Ao criar um ponto final JEA, os seguintes parâmetros de comando (e as correspondentes chaves no ficheiro) tem de ser definidos:
1.  SessionType para RestrictedRemoteServer
2.  RunAsVirtualAccount para **$true**
3.  TranscriptPath para o diretório onde "ombro o" transcrições serão guardadas após cada sessão
4.  RoleDefinitions para uma tabela hash que define quais os grupos têm acesso a quais "capacidades de função".  Este campo define **quem** pode fazer **que** neste ponto final.   Capacidades de função são ficheiros especiais que serão explicados em breve.


O campo de RoleDefinitions define os grupos que tinham acesso que capacidades de função.  Uma capacidade de função é um ficheiro que define um conjunto de capacidades que irá ser disponibilizado para os utilizadores a ligar.  Pode criar capacidades de função com o **New-PSRoleCapabilityFile** comando.

```powershell
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\DemoModule\RoleCapabilities\Maintenance.psrc"
```

Esta ação irá gerar uma capacidade de função de modelo que tem este aspeto:
```
@{

# ID used to uniquely identify this document
GUID = '9287a34f-3f0e-4fbe-9dd7-f1361ba9fd65'

# Author of this document
Author = 'Administrator'

# Description of the functionality provided by these settings
# Description = ''

# Company associated with this document
CompanyName = 'Unknown'

# Copyright statement for this document
Copyright = '(c) 2015 Administrator. All rights reserved.'

# Modules to import when applied to a session
# ModulesToImport = 'MyCustomModule', @{ ModuleName = 'MyCustomModule'; ModuleVersion = '1.0.0.0'; GUID = '4d30d5f0-cb16-4898-812d-f20a6c596bdf' }

# Aliases to make visible when applied to a session
# VisibleAliases = 'Item1', 'Item2'

# Cmdlets to make visible when applied to a session
# VisibleCmdlets = 'Invoke-Cmdlet1', @{ Name = 'Invoke-Cmdlet2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }

# Functions to make visible when applied to a session
# VisibleFunctions = 'Invoke-Function1', @{ Name = 'Invoke-Function2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }

# External commands (scripts and applications) to make visible when applied to a session
# VisibleExternalCommands = 'Item1', 'Item2'

# Providers to make visible when applied to a session
# VisibleProviders = 'Item1', 'Item2'

# Scripts to run when applied to a session
# ScriptsToProcess = 'C:\ConfigData\InitScript1.ps1', 'C:\ConfigData\InitScript2.ps1'

# Aliases to be defined when applied to a session
# AliasDefinitions = @{ Name = 'Alias1'; Value = 'Invoke-Alias1'}, @{ Name = 'Alias2'; Value = 'Invoke-Alias2'}

# Functions to define when applied to a session
# FunctionDefinitions = @{ Name = 'MyFunction'; ScriptBlock = { param($MyInput) $MyInput } }

# Variables to define when applied to a session
# VariableDefinitions = @{ Name = 'Variable1'; Value = { 'Dynamic' + 'InitialValue' } }, @{ Name = 'Variable2'; Value = 'StaticInitialValue' }

# Environment variables to define when applied to a session
# EnvironmentVariables = @{ Variable1 = 'Value1'; Variable2 = 'Value2' }

# Type files (.ps1xml) to load when applied to a session
# TypesToProcess = 'C:\ConfigData\MyTypes.ps1xml', 'C:\ConfigData\OtherTypes.ps1xml'

# Format files (.ps1xml) to load when applied to a session
# FormatsToProcess = 'C:\ConfigData\MyFormats.ps1xml', 'C:\ConfigData\OtherFormats.ps1xml'

# Assemblies to load when applied to a session
# AssembliesToLoad = 'System.Web', 'System.OtherAssembly, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'

}

```
Para ser utilizado por uma configuração de sessão JEA, capacidades de função tem de ser guardadas como um módulo do PowerShell válido num diretório com o nome "RoleCapabilities". Um módulo pode ter vários ficheiros de capacidade de função, se assim o desejar.

Para iniciar a configuração que os cmdlets, funções, aliases e scripts um utilizador pode aceder ao ligar a uma sessão JEA, adicione as suas próprias regras para o ficheiro de capacidade de função, seguindo o comentado os modelos. Para ver mais profundo na forma como pode configurar capacidades de função, veja o completo [experiência guia](http://aka.ms/JEA).

Por fim, assim que tiver concluído a personalizar a configuração de sessão e as capacidades de função relacionados, registar esta configuração de sessão e criar o ponto final executando **Register-PSSessionConfiguration**.

```powershell
Register-PSSessionConfiguration -Name Maintenance -Path "C:\ProgramData\JEAConfiguration\Demo.pssc"
```

## <a name="connect-to-a-jea-endpoint"></a>Ligar a um ponto final JEA
Ligar a um ponto final JEA funciona da mesma forma que a ligação a quaisquer outros trabalhos de ponto final do PowerShell.  Basta ter que dar o nome do ponto final JEA o parâmetro "ConfigurationName" **New-PSSession**, **Invoke-Command**, ou **Enter-PSSession**.

```powershell
Enter-PSSession -ConfigurationName Maintenance -ComputerName localhost
```
Assim que tiver estabelecido ligação à sessão JEA, será limitado em execução na lista de comandos permissões nas capacidades de função que tenha acesso. Se tentar executar qualquer comando não permitido para a sua função, irá encontrar um erro.