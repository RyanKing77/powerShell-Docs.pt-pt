---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Problemas conhecidos no WMF 5.1
ms.openlocfilehash: d53031bea978087c68fcb22989c7cd2e2cf2d9fa
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219458"
---
# <a name="known-issues-in-wmf-51"></a>Problemas conhecidos no WMF 5.1 #

> Nota: Estas informações estão sujeitas a alterações.

## <a name="starting-powershell-shortcut-as-administrator"></a>Iniciar o atalho do PowerShell como administrador
Após instalar o WMF, se tentar inicie o PowerShell como administrador a partir do atalho, poderá receber uma mensagem de "Erro não especificado".
Reabra o atalho como não administrador e o atalho funciona agora mesmo como administrador.

## <a name="pester"></a>Pester
Nesta versão, existem dois problemas que deve ter conhecimento ao utilizar Pester num servidor de Nano:

* A execução de testes no Pester próprio pode resultar em algumas falhas devido às diferenças entre CLR completas e NÚCLEO CLR. Em particular, o método Validate não está disponível no tipo XmlDocument. Testes de seis que tentarem validar o esquema dos registos de saída NUnit são conhecidos falhar.
* Um teste de cobertura de código atualmente falha porque o *WindowsFeature* recursos de DSC não existe no servidor de nano for apresentado. No entanto, estas falhas são geralmente benignas e podem ser ignoradas.

## <a name="operation-validation"></a>Validação da operação

* Update-Help falha por Microsoft.PowerShell.Operation.Validation módulo devido a ajuda de descanso URI

## <a name="dsc-after-uninstall-wmf"></a>DSC após desinstalar WMF
* Desinstalar o WMF não eliminar documentos DSC MOF da pasta de configuração. DSC não irão funcionar corretamente se os documentos MOF contêm propriedades mais recentes que não estão disponíveis nos sistemas operativos mais antigos. Neste caso, execute o seguinte script na consola do PowerShell elevada para limpar os Estados de DSC.
 ```powershell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )

    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
 ```

## <a name="jea-virtual-accounts"></a>Contas de Virtual JEA
Pontos finais JEA e configurações de sessão configuradas para utilizar as contas virtual no WMF 5.0 não serão configuradas para utilizar uma conta virtual após a atualização para o WMF 5.1.
Isto significa que os comandos executados em sessões JEA serão executados com a ligação identidade do utilizador em vez de uma conta de administrador temporário, potencialmente a impedir que o utilizador executar comandos que precise de privilégios elevados.
Para restaurar as contas virtuais, terá de anular o registo e volte a registar as configurações de sessão que utilizem contas virtuais.

```powershell
# Find the JEA endpoint by its name
$jea = Get-PSSessionConfiguration -Name MyJeaEndpoint

# Copy the cached PSSC file so it can be re-registered
$pssc = Copy-Item $jea.ConfigFilePath $env:temp -PassThru

# Unregister the current PSSC
Unregister-PSSessionConfiguration -Name $jea.Name

# Re-register the PSSC
Register-PSSessionConfiguration -Name $jea.Name -Path $pssc.FullName -Force

# Ensure the access policies remain the same
Set-PSSessionConfiguration -Name $newjea.Name -SecurityDescriptorSddl $jea.SecurityDescriptorSddl
```
