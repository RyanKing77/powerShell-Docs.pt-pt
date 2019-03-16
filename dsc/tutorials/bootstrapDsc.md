---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Configurar uma máquina virtual no arranque inicial através da utilização de DSC
ms.openlocfilehash: f9634c330832e23fb2c6f08c5b299b55a5505ac9
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059427"
---
# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a>Configurar uma máquina virtual no arranque inicial através da utilização de DSC

> [!IMPORTANT]
> Aplica-se a: Windows PowerShell 5.0

## <a name="requirements"></a>Requisitos

> [!NOTE]
> O **DSCAutomationHostEnabled** chave de registo descrito neste tópico não está disponível no PowerShell 4.0.
> Para obter informações sobre como configurar novas máquinas virtuais no arranque inicial no PowerShell 4.0, consulte [pretende automaticamente configurar seu máquinas usando o DSC no arranque inicial de segurança?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)

Para executar estes exemplos, terá de:

- Um VHD de arranque para trabalhar com. Pode baixar uma imagem ISO com uma cópia de avaliação do Windows Server 2016 em [Centro de avaliação TechNet](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).
  Pode encontrar instruções sobre como criar um VHD a partir de uma imagem ISO na [criar suportes discos de rígido virtuais](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).
- Um computador anfitrião que tenha o Hyper-V ativada. Para obter informações, consulte [descrição geral do Hyper-V](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).

  Ao utilizar o DSC, pode automatizar a instalação de software e configuração para um computador no arranque inicial.
  Pode fazê-lo por qualquer um dos injetar um documento de MOF de configuração ou um metaconfiguration suportes de dados (por exemplo, um VHD) para que estas são executadas durante o processo de inicialização inicial.
  Este comportamento é especificado pela [de registo dscautomationhostenabled](DSCAutomationHostEnabled.md) chave de Registro em `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`.
  Por predefinição, o valor desta chave é 2, que permite a DSC ser executado no momento da inicialização.

  Se não pretender DSC para ser executado no momento da inicialização, defina o valor do [de registo dscautomationhostenabled](DSCAutomationHostEnabled.md) chave de registo para 0.

- Inserir um documento de MOF de configuração num VHD
- Injetar um metaconfiguration DSC num VHD
- Desativar o DSC no momento da inicialização

> [!NOTE]
> Pode injetar ambos `Pending.mof` e `MetaConfig.mof` num computador ao mesmo tempo.
> Se ambos os ficheiros estiverem presentes, as definições especificadas no `MetaConfig.mof` têm precedência.

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a>Inserir um documento de MOF de configuração num VHD

Adotar uma configuração no arranque inicial, pode injetar um documento MOF de configuração compilada no VHD como seu `Pending.mof` ficheiro.
Se o **DSCAutomationHostEnabled** chave de registo está definida como 2 (o valor predefinido), DSC irá aplicar a configuração definida por `Pending.mof` quando o computador é inicializado na primeira vez.

Neste exemplo, utilizamos a configuração seguinte, que irá instalar o IIS no novo computador:

```powershell
Configuration SampleIISInstall
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    node ('localhost')
    {
        WindowsFeature IIS
        {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }
    }
}
```

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a>Para inserir o documento de MOF de configuração no VHD

1. Montar o VHD para o qual deseja injetar a configuração ao chamar o [montagem VHD](/powershell/module/hyper-v/mount-vhd) cmdlet. Por exemplo:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. Num computador com o PowerShell 5.0 ou posterior, guarde a configuração acima (**SampleIISInstall**) como um ficheiro de script (. ps1) do PowerShell.

3. Na consola do PowerShell, navegue para a pasta onde guardou o ficheiro. ps1.

4. Execute os seguintes comandos do PowerShell para compilar o documento MOF (para obter informações sobre como compilar configurações de DSC, veja [configurações de DSC](../configurations/configurations.md):

   ```powershell
   . .\SampleIISInstall.ps1
   SampleIISInstall
   ```

5. Esta ação irá criar um `localhost.mof` arquivo numa nova pasta chamada `SampleIISInstall`.
   Mudar o nome e mover esse arquivo para a localização correta no VHD como `Pending.mof` utilizando o [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet. Por exemplo:

   ```powershell
       Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
   ```

6. Desmonte o VHD ao chamar o [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet. Por exemplo:

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

7. Crie uma VM com o VHD onde instalou o documento MOF de DSC.

Depois de inicial de segurança de arranque e instalação do sistema operativo, será instalado o IIS.
Pode verificar isto ao chamar o [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a>Injetar um metaconfiguration DSC num VHD

Também pode configurar um computador para solicitar uma configuração no arranque inicial injetando um metaconfiguration (consulte [configurar o Gestor de configuração Local (LCM)](../managing-nodes/metaConfig.md)) no VHD como seu `MetaConfig.mof` ficheiro.
Se o **DSCAutomationHostEnabled** chave de registo é definida como 2 (o valor predefinido), DSC irá aplicar metaconfiguration definido pelo `MetaConfig.mof` para o LCM quando o computador arranca tendo em vista a primeira vez.
Se o metaconfiguration Especifica que o LCM deve solicitar configurações a partir de um servidor de solicitação, o computador irá tentar extrair uma configuração a partir desse servidor de solicitação no arranque inicial.
Para obter informações sobre como configurar um servidor de solicitação de DSC, veja [como configurar um servidor de solicitação do DSC web](../pull-server/pullServer.md).

Neste exemplo, utilizamos os dois a configuração descrita na secção anterior (**SampleIISInstall**) e o metaconfiguration seguinte:

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientBootstrap
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('SampleIISInstall')
        }
    }
}
```

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a>Para inserir o documento MOF metaconfiguration no VHD

1. Montar o VHD para o qual deseja injetar o metaconfiguration ao chamar o [montagem VHD](/powershell/module/hyper-v/mount-vhd) cmdlet. Por exemplo:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. [Configurar um servidor de solicitação da web de DSC](../pull-server/pullServer.md)e guarde o **SampleIISInstall** configuração para a pasta adequada.

3. Num computador com o PowerShell 5.0 ou posterior, guarde o metaconfiguration acima (**PullClientBootstrap**) como um ficheiro de script (. ps1) do PowerShell.

4. Na consola do PowerShell, navegue para a pasta onde guardou o ficheiro. ps1.

5. Execute os seguintes comandos do PowerShell para compilar o documento MOF metaconfiguration (para obter informações sobre como compilar configurações de DSC, veja [configurações de DSC](../configurations/configurations.md):

   ```powershell
   . .\PullClientBootstrap.ps1
   PullClientBootstrap
   ```

6. Esta ação irá criar um `localhost.meta.mof` arquivo numa nova pasta chamada `PullClientBootstrap`.
   Mudar o nome e mover esse arquivo para a localização correta no VHD como `MetaConfig.mof` utilizando o [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet.

   ```powershell
   Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\System32\Configuration\MetaConfig.mof
   ```

7. Desmonte o VHD ao chamar o [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet. Por exemplo:

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

8. Crie uma VM com o VHD onde instalou o documento MOF de DSC.

Depois de inicial de segurança de arranque e instalação do sistema operativo, DSC irá fazer com que a configuração do servidor de solicitação e IIS será instalado.
Pode verificar isto ao chamar o [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.

## <a name="disable-dsc-at-boot-time"></a>Desativar o DSC no momento da inicialização

Por predefinição, o valor da `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled` chave está definida como 2, que permite uma configuração de DSC para ser executada se o computador está no estado atual ou pendente. Se não pretender que uma configuração de executar no arranque inicial, por isso, precisa definir o valor desta chave como 0:

1. Montar o VHD ao chamar o [montagem VHD](/powershell/module/hyper-v/mount-vhd) cmdlet. Por exemplo:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. Carregar o Registro `HKLM\Software` subchave de VHD chamando `reg load`.

   ```powershell
   reg load HKLM\Vhd E:\Windows\System32\Config\Software`
   ```

3. Navegue para o `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` utilizando o fornecedor de registo do PowerShell.

   ```powershell
   Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies\System`
   ```

4. Alterar o valor de `DSCAutomationHostEnabled` como 0.

   ```powershell
   Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
   ```

5. Descarrega o registo ao executar os comandos seguintes:

   ```powershell
   [gc]::Collect()
   reg unload HKLM\Vhd
   ```

## <a name="see-also"></a>Veja Também

[Configurações de DSC](../configurations/configurations.md)

[Chave de registo DSCAutomationHostEnabled](DSCAutomationHostEnabled.md)

[Configurar o Gestor de Configuração Local (LCM)](../managing-nodes/metaConfig.md)

[Como configurar um servidor de solicitação da web de DSC](../pull-server/pullServer.md)
