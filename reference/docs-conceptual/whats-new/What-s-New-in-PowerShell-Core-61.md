---
title: Quais são as novidades no PowerShell Core 6.1
description: Novos recursos e alterações lançadas no PowerShell Core 6.1
ms.date: 09/13/2018
ms.openlocfilehash: 3d836a24b494df9c7f6ebe994386e2a0297521fa
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984515"
---
# <a name="whats-new-in-powershell-core-61"></a>Quais são as novidades no PowerShell Core 6.1

Segue-se uma seleção de alguns dos principais novos recursos e alterações que foram introduzidas no PowerShell Core 6.1.

Também há **toneladas** de "aborrecida" que tornam o PowerShell mais rápido e mais estável (além de muitas e várias correções de erros)!
Para obter uma lista completa das alterações, confira nossos [registo de alterações no GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).

E embora o que chamamos de alguns nomes abaixo, obrigado a [todos os contribuintes da Comunidade](https://github.com/PowerShell/PowerShell/graphs/contributors) que possibilitado nesta versão.

## <a name="net-core-21"></a>.NET core 2.1

PowerShell Core 6.1 movido para .NET Core 2.1 após era [lançado em Maio](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/), o que resulta numa série de aprimoramentos para o PowerShell, incluindo:

- melhorias de desempenho (consulte [abaixo](#performance-improvements))
- Suporte de Alpine Linux (pré-visualização)
- [Suporte de ferramenta global de .NET](/dotnet/core/tools/global-tools) - próximos em breve para o PowerShell
- [`Span<T>`](/dotnet/api/system.span-1?view=netcore-2.1)

## <a name="windows-compatibility-pack-for-net-core"></a>Pacote de compatibilidade do Windows para .NET Core

No Windows, a equipe .NET fornecido a [Windows Compatibility Pack para .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/), removido de um conjunto de assemblies que adicionar um número de APIs ao .NET Core no Windows.

Adicionámos o Compatibility Pack do Windows para a versão 6.1 do PowerShell Core, para que quaisquer módulos ou scripts que usam essas APIs podem basear nas mesmas estejam disponíveis.

O pacote de compatibilidade do Windows permite que o PowerShell Core usar **mais de 1900 cmdlets que vêm com o Windows 10 de Outubro de 2018 Update e Windows Server 2019**.

## <a name="support-for-application-whitelisting"></a>Suporte para permissões de aplicação

6.1 do PowerShell Core tem paridade com suporte do Windows PowerShell 5.1 [AppLocker](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) e [Device Guard](https://docs.microsoft.com/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) permissões de aplicação.
Permissões de aplicação permite que um controle granular do que binários têm permissão para ser executado utilizado com o PowerShell [modo de idioma restrita](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/).

## <a name="performance-improvements"></a>Melhoramentos de desempenho

PowerShell Core 6.0 feitas algumas melhorias de desempenho significativas.
PowerShell Core 6.1 continua a melhorar a velocidade de determinadas operações.

Por exemplo, `Group-Object` acelera 66%:

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|              | Windows PowerShell 5.1 | O PowerShell Core 6.0 | O PowerShell Core 6.1 |
|--------------|------------------------|---------------------|---------------------|
| Tempo (seg)   | 25.178                 | 19.653              | 6.641               |
| Aceleração (%) | N/A                    | 21.9%               | 66.2%               |

Da mesma forma, os cenários de classificação como esta melhoraram por mais de 15%:

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|              | Windows PowerShell 5.1 | O PowerShell Core 6.0 | O PowerShell Core 6.1 |
|--------------|------------------------|---------------------|---------------------|
| Tempo (seg)   | 12.170                 | 8.493               | 7.08                |
| Aceleração (%) | N/A                    | 30.2%               | 16.6%               |

`Import-Csv` tem também foi acelera significativamente após uma regressão do Windows PowerShell.
O exemplo seguinte utiliza um teste de CSV com 26,616 linhas e colunas de seis:

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|              | Windows PowerShell 5.1 | O PowerShell Core 6.0 | O PowerShell Core 6.1    |
|--------------|------------------------|---------------------|------------------------|
| Tempo (seg)   | 0.441                  | 1.069               | 0.268                  |
| Aceleração (%) | N/A                    | -142.4%             | 74.9% de (39.2% de WPS) |

Por último, a conversão de JSON em `PSObject` tem sido acelera por mais de 50% desde o Windows PowerShell.
O exemplo seguinte utiliza um ficheiro JSON de teste de ~ 2MB:

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|              | Windows PowerShell 5.1 | O PowerShell Core 6.0 | O PowerShell Core 6.1    |
|--------------|------------------------|---------------------|------------------------|
| Tempo (seg)   | 0.259                  | 0.577               | 0.125                  |
| Aceleração (%) | N/A                    | -122.8%             | 78.3% de (51.7% de WPS) |

## <a name="check-system32-for-compatible-in-box-modules-on-windows"></a>Verificar `system32` para compatíveis módulos de incluído no Windows

Na atualização do Windows 10 1809 e Windows Server 2019, atualizámos um número de módulos do PowerShell incluído para marcá-los como compatível com o PowerShell Core.

Quando o PowerShell Core 6.1 é iniciado, ele incluirá automaticamente `$windir\System32` como parte do `PSModulePath` variável de ambiente.
No entanto, ele expõe apenas dos módulos `Get-Module` e `Import-Module` se sua `CompatiblePSEdition` está marcado como compatível com o `Core`.


```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> Poderá ver diferentes módulos disponíveis, dependendo de que funções e funcionalidades são instaladas.

```Output
...
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, Get-AppxPackage, Get-AppxPacka...
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, Suspend-BitLocker, Resume-Bit...
Manifest   1.0.0.0    DnsClient                           Core,Desk {Resolve-DnsName, Clear-DnsClientCache, Get-DnsC...
Manifest   1.0.0.0    HgsDiagnostics                      Core,Desk {New-HgsTraceTarget, Get-HgsTrace, Get-HgsTraceF...
Binary     2.0.0.0    Hyper-V                             Core,Desk {Add-VMAssignableDevice, Add-VMDvdDrive, Add-VMF...
Binary     1.1        Hyper-V                             Core,Desk {Add-VMDvdDrive, Add-VMFibreChannelHba, Add-VMHa...
Manifest   2.0.0.0    NetAdapter                          Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetEventPacketCapture               Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                             Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                              Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                              Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                         Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam                       Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetWNV                              Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   2.0.0.0    TrustedPlatformModule               Core,Desk {Get-Tpm, Initialize-Tpm, Clear-Tpm, Unblock-Tpm...
...
```

Pode substituir este comportamento para mostrar todos os módulos com o `-SkipEditionCheck` mudar o parâmetro.
Também adicionámos um `PSEdition` propriedade para a saída de tabela.

```powershell
Get-Module Net* -ListAvailable -SkipEditionCheck
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                        PSEdition ExportedCommands
---------- -------    ----                        --------- ----------------
Manifest   2.0.0.0    NetAdapter                  Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetConnection               Core,Desk {Get-NetConnectionProfile, Set-NetConnectionProf...
Manifest   1.0.0.0    NetDiagnostics              Desk      Get-NetView
Manifest   1.0.0.0    NetEventPacketCapture       Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                     Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                      Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                      Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                 Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam               Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetTCPIP                    Core,Desk {Get-NetIPAddress, Get-NetIPInterface, Get-NetIP...
Manifest   1.0.0.0    NetWNV                      Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   1.0.0.0    NetworkConnectivityStatus   Core,Desk {Get-DAConnectionStatus, Get-NCSIPolicyConfigura...
Manifest   1.0.0.0    NetworkSwitchManager        Core,Desk {Disable-NetworkSwitchEthernetPort, Enable-Netwo...
Manifest   1.0.0.0    NetworkTransition           Core,Desk {Add-NetIPHttpsCertBinding, Disable-NetDnsTransi...
```

Para obter mais informações sobre este comportamento, confira [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md).

## <a name="markdown-cmdlets-and-rendering"></a>Cmdlets de markdown e composição

Markdown é um padrão para criar documentos de texto sem formatação legível com formatação básica que pode ser processado em HTML.

Adicionamos alguns cmdlets 6.1 que permitem que converta e compor Markdown de documentos na consola, incluindo:

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

Por exemplo, `Show-Markdown` processa um ficheiro de Markdown no console:

![Exemplo de show Markdown](./images/markdown_example.png)

Para obter mais informações sobre o funcionamento destes cmdlets, confira [este RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md).

## <a name="experimental-feature-flags"></a>Sinalizadores de funcionalidade experimental

Ativámos o suporte para [funcionalidades experimentais][]. Isso permite aos desenvolvedores PowerShell ofereça novas funcionalidades e receba comentários antes da conclusão do design. Desta forma podemos evitar fazer alterações de última hora, como o design se desenvolve.

Utilize `Get-ExperimentalFeature` para obter uma lista das funcionalidades experimentais disponíveis. Pode ativar ou desativar estas funcionalidades com `Enable-ExperimentalFeature` e `Disable-ExperimentalFeature`.

Pode saber mais sobre esta funcionalidade no [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md).

## <a name="web-cmdlet-improvements"></a>Melhorias de cmdlet da Web

Graças à [ @markekraus ](https://github.com/markekraus), uma grande quantidade de melhorias foram feitas aos nossos cmdlets web: [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)
e [ `Invoke-RestMethod` ](/powershell/module/microsoft.powershell.utility/invoke-restmethod).

- [6109 de n. º de PR](https://github.com/PowerShell/PowerShell/pull/6109) -padrão de codificação definida como UTF-8 para `application-json` respostas
- [PR #6018](https://github.com/PowerShell/PowerShell/pull/6018)  -  `-SkipHeaderValidation` parâmetro para permitir `Content-Type` cabeçalhos que não são compatíveis com padrões
- [PR #5972](https://github.com/PowerShell/PowerShell/pull/5972)  -  `Form` simplificado de parâmetro para suportar `multipart/form-data` de suporte
- [PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) – em conformidade, maiúsculas de minúsculas manipulação das chaves de relação
- [PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) -adicionar `-Resume` parâmetro para cmdlets de web

## <a name="remoting-improvements"></a>Melhorias de comunicação remota

### <a name="powershell-direct-for-containers-tries-to-use-powershell-core-first"></a>PowerShell Direct para contentores tenta utilizar o PowerShell Core primeiro

[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) é uma funcionalidade do PowerShell e o Hyper-V que permite-lhe ligar a uma VM de Hyper-V ou o contentor sem conectividade de rede ou outros serviços de gestão remota.

No passado, o PowerShell Direct ligados utilizando a instância do Windows PowerShell de caixa de entrada no contentor.
Agora, PowerShell Direct primeiro tenta se conectar usando qualquer disponíveis `pwsh.exe` sobre o `PATH` variável de ambiente.
Se `pwsh.exe` não estiver disponível, PowerShell Direct retrocede para utilizar `powershell.exe`.

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a>`Enable-PSRemoting` agora cria pontos de extremidade de comunicação remota separado para versões de pré-visualização

`Enable-PSRemoting` Agora, cria duas configurações de sessão de comunicação remota:

- Uma para a versão principal do PowerShell. Por exemplo, `PowerShell.6`. Este ponto de extremidade que pode ser utilizado em atualizações de versão secundária como a configuração de sessão do PowerShell 6 "todo o sistema"
- Uma configuração de sessão específicas da versão, por exemplo: `PowerShell.6.1.0`

Este comportamento é útil se pretender ter várias versões do PowerShell 6 instaladas e acessíveis na mesma máquina.

Além disso, as versões de pré-visualização do PowerShell agora obtém seus próprios comunicação remota de configurações de sessão após a execução do `Enable-PSRemoting` cmdlet:

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

A saída pode ser diferente se não tiver configurado o WinRM antes.

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

Em seguida, pode ver as configurações de sessão do PowerShell separadas para a pré-visualização e estável baseia-se do PowerShell 6 e para cada versão específica.

```powershell
Get-PSSessionConfiguration
```

```Output
Name          : PowerShell.6.2-preview.1
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6-preview
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6.1.0
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

### <a name="userhostport-syntax-supported-for-ssh"></a>`user@host:port` sintaxe suportada para SSH

SSH clientes normalmente suportam uma cadeia de ligação no formato `user@host:port`.
Com a adição do SSH como um protocolo de comunicação remota do PowerShell, adicionámos suporte para esse formato de cadeia de ligação:

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a>Opção de MSI para adicionar o menu de contexto de shell do explorer no Windows

Graças à [ @bergmeister ](https://github.com/bergmeister), agora pode ativar um menu de contexto no Windows. Agora pode abrir a instalação de todo o sistema do PowerShell 6.1 de qualquer pasta no Explorador do Windows:

![Menu de contexto do shell do PowerShell 6](./images/shell_context_menu.png)

## <a name="goodies"></a>Coisas boas

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a>"Executar como administrador" da lista de atalhos de atalho do Windows

Graças à [ @bergmeister ](https://github.com/bergmeister), lista de atalhos no atalho PowerShell Core inclui agora "Executar como administrador":

![Executar como administrador na lista de atalhos do PowerShell 6](./images/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a>`cd -` Devolve a diretório anterior

```powershell
C:\Windows\System32> cd C:\
C:\> cd -
C:\Windows\System32>
```

Ou no Linux:

```ShellSession
PS /etc> cd /usr/bin
PS /usr/bin> cd -
PS /etc>
```

Além disso, `cd` e `cd --` alterar para `$HOME`.

### `Test-Connection`

Graças à [ @iSazonov ](https://github.com/iSazonov), o [ `Test-Connection` ](/powershell/module/microsoft.powershell.management/test-connection) cmdlet tem sido transportado para o PowerShell Core.

### <a name="update-help-as-non-admin"></a>`Update-Help` como não-administrador

Por demanda popular, `Update-Help` já não precisa ser executado como administrador.
`Update-Help` agora usa como padrão salvar ajuda para uma pasta no âmbito do utilizador.

### <a name="new-methodsproperties-on-pscustomobject"></a>Novos métodos/as propriedades no `PSCustomObject`

Graças à [ @iSazonov ](https://github.com/iSazonov), adicionamos novos métodos e propriedades para `PSCustomObject`.
`PSCustomObject` inclui agora uma `Count` / `Length` propriedade como outros objetos.

```powershell
$PSCustomObject = [pscustomobject]@{foo = 1}

$PSCustomObject.Length
```

```Output
1
```

```powershell
$PSCustomObject.Count
```

```Output
1
```

Este trabalho também inclui `ForEach` e `Where` métodos que permitem operar e filtrar `PSCustomObject` itens:

```powershell
$PSCustomObject.ForEach({$_.foo + 1})
```

```Output
2
```

```powershell
$PSCustomObject.Where({$_.foo -gt 0})
```

```Output
foo
---
  1
```

### `Where-Object -Not`

Graças à @SimonWahlin, adicionamos o `-Not` parâmetro para `Where-Object`.
Agora pode filtrar um objeto no pipeline, a não existência de uma propriedade ou um valor de propriedade de nulo/vazio.

Por exemplo, este comando devolve todos os serviços que não têm quaisquer serviços dependentes definidos:

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a>`New-ModuleManifest` cria um documento sem BOM UTF-8

Considerando nossa mudança para BOM sem UTF-8 no PowerShell 6.0, atualizámos o `New-ModuleManifest` cmdlet para criar um documento sem BOM UTF-8, em vez de um UTF-16 um.

### <a name="conversions-from-psmethod-to-delegate"></a>Conversões de PSMethod ao delegado

Graças à [ @powercode ](https://github.com/powercode), agora, suportamos a conversão de um `PSMethod` num delegado.
Isso permite que faça coisas como passagem `PSMethod` `[M]::DoubleStrLen` como um valor de delegado em `[M]::AggregateString`:

```powershell
class M {
    static [int] DoubleStrLen([string] $value) { return 2 * $value.Length }

    static [long] AggregateString([string[]] $values, [func[string, int]] $selector) {
        [long] $res = 0
        foreach($s in $values){
            $res += $selector.Invoke($s)
        }
        return $res
    }
}

[M]::AggregateString((gci).Name, [M]::DoubleStrLen)
```

Para obter mais informações sobre esta alteração, confira [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287).

### <a name="standard-deviation-in-measure-object"></a>Desvio padrão no `Measure-Object`

Graças à [ @CloudyDino ](https://github.com/CloudyDino), adicionamos uma `StandardDeviation` propriedade `Measure-Object`:

```powershell
Get-Process | Measure-Object -Property CPU -AllStats
```

```Output
Count             : 308
Average           : 31.3720576298701
Sum               : 9662.59375
Maximum           : 4416.046875
Minimum           :
StandardDeviation : 264.389544720926
Property          : CPU
```

### `GetPfxCertificate -Password`

Graças à [ @maybe-hello-world ](https://github.com/maybe-hello-world), `Get-PfxCertificate` tem agora o `Password` parâmetro, que assume um `SecureString`. Isto permite-lhe utilizá-lo de forma não interativa:

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a>Remoção do `more` função

No passado, PowerShell foi lançado uma função no Windows chamado `more` que encapsulada `more.com`.
Essa função agora foi removida.

Além disso, o `help` função alterado para utilizar `more.com` no Windows ou pager de padrão do sistema especificado pelo `$env:PAGER` em plataformas não Windows.

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a>`cd DriveName:` Devolve agora os utilizadores para o diretório de trabalho atual nessa unidade

Anteriormente, utilizando `Set-Location` ou `cd` para regressar a uma PSDrive enviada aos utilizadores para a localização predefinida para essa unidade.

Graças à [ @mcbobke ](https://github.com/mcbobke), os usuários agora são enviados para o último conhecido atual diretório de trabalho da sessão.

### <a name="windows-powershell-type-accelerators"></a>Aceleradores de tipo do Windows PowerShell

No Windows PowerShell, incluímos os Aceleradores de tipo seguintes para que seja mais fácil trabalhar com seus respectivos tipos:

- `[adsi]`: `System.DirectoryServices.DirectoryEntry`
- `[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`
- `[wmi]`: `System.Management.ManagementObject`
- `[wmiclass]`: `System.Management.ManagementClass`
- `[wmisearcher]`: `System.Management.ManagementObjectSearcher`

Estes aceleradores de tipo não foram incluídos no PowerShell 6, mas foram adicionados ao 6.1 do PowerShell em execução no Windows.

Esses tipos são úteis para construir facilmente AD e objetos WMI.

Por exemplo, pode consultar ao utilizar o LDAP:

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

Exemplo seguinte cria um objeto de Win32_OperatingSystem CIM:

```powershell
[wmi]"Win32_OperatingSystem=@"
```

```Output
SystemDirectory : C:\WINDOWS\system32
Organization    : Contoso IT
BuildNumber     : 18234
RegisteredUser  : Contoso Corp.
SerialNumber    : 12345-67890-ABCDE-F0123
Version         : 10.0.18234
```

Este exemplo retorna um objeto de ManagementClass para a classe Win32_OperatingSystem.

```powershell
[wmiclass]"Win32_OperatingSystem"
```

```Output
   NameSpace: ROOT\cimv2

Name                                Methods              Properties
----                                -------              ----------
Win32_OperatingSystem               {Reboot, Shutdown... {BootDevice, BuildNumber, BuildType, Caption...}
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a>`-lp` alias de todos os `-LiteralPath` parâmetros

Graças à [ @kvprasoon ](https://github.com/kvprasoon), agora temos um alias de parâmetro `-lp` todos os incorporada cmdlets do PowerShell que tenham um `-LiteralPath` parâmetro.

## <a name="breaking-changes"></a>Alterações Interruptivas

### <a name="msi-based-installation-paths-on-windows"></a>Caminhos de instalação baseada em MSI no Windows

No Windows, o pacote MSI instala agora para o seguinte caminho:

- `$env:ProgramFiles\PowerShell\6\` para a instalação estável do 6.x
- `$env:ProgramFiles\PowerShell\6-preview\` para a instalação de pré-visualização do 6.x

Esta alteração garante que o PowerShell Core pode ser atualizado/atendido pelo Microsoft Update.

Para obter mais informações, confira [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md).

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a>Telemetria só pode ser desativada com uma variável de ambiente

O PowerShell Core envia dados de telemetria básico para a Microsoft quando é iniciado. Os dados incluem o nome do SO, versão do SO e versão do PowerShell. Estes dados permite-nos compreender melhor os ambientes nos quais o PowerShell é utilizado e permite-nos atribuir prioridades a novas funcionalidades e correções.

Para sair desta telemetria, defina a variável de ambiente `POWERSHELL_TELEMETRY_OPTOUT` para `true`, `yes`, ou `1`. Já não suportamos a eliminação do ficheiro `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` para desativar a telemetria.

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a>Não são permitidas autenticação básica através de HTTP na comunicação remota do PowerShell em plataformas de Unix

Para impedir a utilização de tráfego não criptografado, a comunicação remota do PowerShell em plataformas Unix agora requer a utilização de NTLM/negociar ou HTTPS.

Para obter mais informações sobre estas alterações, confira [problema #6779](https://github.com/PowerShell/PowerShell/issues/6779).

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a>Removido `VisualBasic` como um idioma suportado no Add-Type

No passado, poderia compilar código do Visual Basic utilizando o `Add-Type` cmdlet.
Visual Basic foi raramente utilizado com `Add-Type`. Removemos esta funcionalidade para reduzir o tamanho do PowerShell.

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a>Limpos usos de `CommandTypes.Workflow` e `WorkflowInfoCleaned`

Para obter mais informações sobre estas alterações, confira [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708).

### <a name="group-object-now-sorts-the-groups"></a>Os grupos ordena agora de objeto de grupo

Como parte da melhoria no desempenho, `Group-Object` agora retorna uma lista classificada dos grupos.
Embora não deve confiar na ordem, poderia ser quebrada por esta alteração se quisesse que o primeiro grupo. Decidimos que essa melhoria de desempenho era que vale a pena a alteração, uma vez que o impacto de ser dependentes do comportamento anterior é baixo.

Para obter mais informações sobre esta alteração, consulte [problema #7409](https://github.com/PowerShell/PowerShell/issues/7409).

<!-- URL references -->
[Funcionalidades experimentais]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
