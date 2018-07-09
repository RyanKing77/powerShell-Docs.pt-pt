---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Problemas conhecidos no WMF 5.1
ms.openlocfilehash: 74e5a6763a8a780000bf876f34caa9646a2a416a
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892142"
---
# <a name="known-issues-in-wmf-51"></a>Problemas conhecidos no WMF 5.1

> [!Note]
> Estas informações estão sujeitas a alterações.

## <a name="starting-powershell-shortcut-as-administrator"></a>A iniciar o atalho para o PowerShell como administrador

Após a instalação de WMF, se tentar iniciar o PowerShell como administrador a partir do atalho, poderá receber uma mensagem de "Erro não especificado".
Reabra o atalho como não-administrador e o atalho agora funciona até mesmo como administrador.

## <a name="pester"></a>Pester

Nesta versão, há dois problemas que deve estar ciente de quando utilizar Pester no servidor Nano:

- Execução de testes no Pester em si pode resultar em algumas falhas devido às diferenças entre o CLR completa e CORE CLR. Em particular, o método Validate não está disponível no tipo XmlDocument. Testes de seis que tentam validar o esquema dos registos de saída do NUnit são conhecidos para efetuar a ativação.
- Um teste de cobertura de código atualmente falha porque o *WindowsFeature* recursos de DSC não existe no servidor Nano. No entanto, estas falhas são geralmente benignas e podem ser ignoradas com segurança.

## <a name="operation-validation"></a>Validação da operação

- `Update-Help` Falha do módulo de Microsoft.PowerShell.Operation.Validation devido a URI de ajuda de descanso

## <a name="dsc-after-uninstall-wmf"></a>DSC depois de desinstalar o WMF

- Desinstalar o WMF não elimina os documentos de MOF de DSC a partir da pasta de configuração. DSC não funcionará corretamente se os documentos MOF contenham propriedades mais recentes que não estão disponíveis nos sistemas mais antigos. Neste caso, execute o seguinte script de consola elevada do PowerShell para limpar os Estados de DSC.

  ```powershell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )
    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
  ```

## <a name="jea-virtual-accounts"></a>Contas de Virtual de JEA

Pontos finais JEA e configurações de sessão configuradas para utilizar contas virtuais no WMF 5.0 não irão ser configuradas para utilizar uma conta virtual após a atualização para o WMF 5.1.
Isso significa que os comandos são executados em sessões JEA serão executado na identidade do usuário conectado, em vez de uma conta de administrador temporário, potencialmente a impedir que o utilizador executar comandos que requerem privilégios elevados.
Para restaurar as contas virtuais, terá de anular o registo e voltar a registar quaisquer configurações de sessão que utilizam contas virtuais.

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