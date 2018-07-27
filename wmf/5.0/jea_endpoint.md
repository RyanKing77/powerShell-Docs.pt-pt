---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 3acd266a75bc61ffe4bce467cfb804ac7865c629
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/26/2018
ms.locfileid: "39267927"
---
# <a name="creating-and-connecting-to-a-jea-endpoint"></a>Criar e Estabelecer Ligação a um Ponto Final da JEA

Para criar um ponto final JEA, terá de criar e registar um ficheiro de configuração de sessão do PowerShell especialmente configurado, o que pode ser gerado com o **New-PSSessionConfigurationFile** cmdlet.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -TranscriptDirectory "C:\ProgramData\JEATranscripts" -RunAsVirtualAccount -RoleDefinitions @{ 'CONTOSO\NonAdmin_Operators' = @{ RoleCapabilities = 'Maintenance' }} -Path "$env:ProgramData\JEAConfiguration\Demo.pssc"
```

Isto irá criar um ficheiro de configuração de sessão parecido com este:

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
    RoleDefinitions = @{ 'CONTOSO\NonAdmin_Operators' = @{ 'RoleCapabilities' = 'Maintenance' } }
}
```

Ao criar um ponto final JEA, tem de definir os seguintes parâmetros do comando (e as chaves correspondentes no arquivo):

1. SessionType para RestrictedRemoteServer
2. RunAsVirtualAccount para **$true**
3. TranscriptPath para o diretório em que "por cima do ombro" transcrições serão guardadas depois de cada sessão
4. RoleDefinitions para uma tabela de hash que define os grupos que têm acesso para qual "funcionalidades de função". Este campo define **quem** pode fazer **o que** neste ponto final. Funcionalidades de função são arquivos especiais que serão explicados brevemente.

O campo de RoleDefinitions define os grupos que tinham acesso para as funcionalidades de função. Um recurso de função é um ficheiro que define um conjunto de recursos que vão ser expostas para conectar usuários.
Pode criar capacidades de função com o **New-PSRoleCapabilityFile** comando.

```powershell
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\DemoModule\RoleCapabilities\Maintenance.psrc"
```

Esta ação irá gerar um recurso de função de modelo que tem esta aparência:

```powershell
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

Para ser utilizado por uma configuração de sessão JEA, funcionalidades de função tem de ser guardadas como um módulo do PowerShell válido num diretório chamado "RoleCapabilities". Um módulo pode ter vários arquivos de recurso de função, se assim o desejar.

Para começar a configurar os cmdlets, funções, aliases e scripts de um utilizador pode aceder ao ligar a uma sessão JEA, adicione suas próprias regras para o ficheiro de recurso de função a seguir o comentado modelos. Para obter uma visão mais profunda sobre como pode configurar funcionalidades de função, verifique o completo [guia de experiência](http://aka.ms/JEA).

Por fim, quando tiver terminado de personalizar a sua configuração de sessão e as capacidades de função relacionadas, registar esta configuração de sessão e criar o ponto final através da execução `Register-PSSessionConfiguration`.

```powershell
Register-PSSessionConfiguration -Name Maintenance -Path "C:\ProgramData\JEAConfiguration\Demo.pssc"
```

## <a name="connect-to-a-jea-endpoint"></a>Ligar a um ponto final JEA

Ligar a um ponto final JEA funciona da mesma forma, ligar a quaisquer outros trabalhos de ponto final do PowerShell.
Simplesmente tem que dar o parâmetro de "ConfigurationName" para o seu nome de ponto final JEA **New-PSSession**, **Invoke-Command**, ou **Enter-PSSession**.

```powershell
Enter-PSSession -ConfigurationName Maintenance -ComputerName localhost
```

Depois de ter ligado à sessão JEA, estará limitada em execução na lista de permissões a comandos nas capacidades de função tem acesso. Se tentar executar qualquer comando não é permitido para a sua função, irá encontrar um erro.