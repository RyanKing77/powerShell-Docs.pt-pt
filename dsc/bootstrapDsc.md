---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Configurar uma máquinas virtuais em cima de arranque inicial através da utilização de DSC"
ms.openlocfilehash: c793e36eb9caa194104f9dda2aa1d335b21b676c
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2017
---
>Aplica-se a: O Windows PowerShell 5.0

>**Nota:** o **DSCAutomationHostEnabled** chave de registo descrito neste tópico não está disponível no PowerShell 4.0.
Para obter informações sobre como configurar novas máquinas virtuais em cima de arranque inicial no PowerShell 4.0, consulte [pretende automaticamente configurar seu máquinas utilizando DSC no arranque inicial de segurança?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)

# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a>Configurar uma máquinas virtuais em cima de arranque inicial através da utilização de DSC

## <a name="requirements"></a>Requisitos

Para executar estes exemplos, necessitará de:

- Um VHD de arranque para trabalhar com. Pode transferir uma imagem ISO com uma cópia de avaliação do Windows Server 2016 em [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016). Pode encontrar instruções sobre como criar um VHD a partir de uma imagem ISO na [criar suportes os discos rígidos virtuais](https://technet.microsoft.com/en-us/library/gg318049.aspx).
- Um computador anfitrião que tenha o Hyper-V ativada. Para informações, consulte [descrição geral do Hyper-V](https://technet.microsoft.com/library/hh831531.aspx).

Ao utilizar o DSC, pode automatizar a instalação de software e configuração para um computador em cima de arranque inicial.
Fazê-lo ao ou inserirem-se um documento MOF de configuração ou uma configuração meta para suportes de dados (por exemplo, um VHD) para que forem executadas durante o processo de arranque de segurança inicial.
Este comportamento é especificado pelo [chave de registo DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) chave de registo em **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies**.
Por predefinição, o valor desta chave é 2, que lhe permite DSC executar no momento do arranque.

Se não pretender DSC para executar no momento do arranque, defina o valor da [chave de registo DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) chave de registo para 0.

- Inserir um documento MOF de configuração num VHD
- Inserir uma configuração meta do DSC num VHD
- Desativar o DSC no momento do arranque

>**Nota:** pode inserir ambos `Pending.mof` e `MetaConfig.mof` para um computador ao mesmo tempo.
Se ambos os ficheiros estiverem presentes, as definições especificadas no `MetaConfig.mof` têm precedência.

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a>Inserir um documento MOF de configuração num VHD

Para enact uma configuração de segurança de arranque inicial, pode inserir um documento MOF configuração compilados num VHD como respetivo `Pending.mof` ficheiro.
Se o **DSCAutomationHostEnabled** chave de registo está definida como 2 (o valor predefinido), DSC será aplicada a configuração definida pelo `Pending.mof` quando o computador arranca para a primeira vez.

Neste exemplo, utilizamos a seguinte configuração, irá instalar o IIS no novo computador:

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

1. Montar o VHD para o qual pretende inserir a configuração ao chamar o [montar VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet. Por exemplo:

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```
2. Num computador com o PowerShell 5.0 ou posterior, guarde a configuração de acima (**SampleIISInstall**) como um ficheiro de script (. ps1) do PowerShell.

3. Na consola do PowerShell, navegue para a pasta onde guardou o ficheiro. ps1.

4. Execute os seguintes comandos do PowerShell para compilar o documento MOF (para obter informações sobre configurações de DSC a compilação, consulte [configurações de DSC](configurations.md):

    ```powershell
    . .\SampleIISInstall.ps1
    SampleIISInstall
    ```

5. Esta ação irá criar um `localhost.mof` ficheiros numa pasta nova denominada `SampleIISInstall`.
Mudar o nome e mover esse ficheiro para a localização correta no VHD como `Pending.mof` utilizando o [Mover Item](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet. Por exemplo:

    ```powershell
        Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
    ```
6. Desmontar o VHD ao chamar o [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx) cmdlet. Por exemplo:

    ```powershell
    Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

7. Crie uma VM utilizando o VHD onde instalou o documento de DSC MOF. Depois de iniciais existentes de segurança de arranque e instalação do sistema operativo, será instalado o IIS.
Pode verificar isto ao chamar o [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a>Inserir uma configuração meta do DSC num VHD

Também pode configurar um computador para solicitar uma configuração no arranque iniciais existentes-se ao inserirem uma configuração meta do (consulte [configurar o Gestor de configuração Local (MMC)](metaConfig.md)) para o VHD como respetivo `MetaConfig.mof` ficheiro.
Se o **DSCAutomationHostEnabled** chave de registo está definida como 2 (o valor predefinido), DSC será aplicada a configuração meta do definido pelo `MetaConfig.mof` para MMC quando o computador arranca para a primeira vez.
Se a configuração meta Especifica que o MMC deve solicitar a configurações de um servidor de solicitação, o computador irá tentar solicitar uma configuração a partir desse servidor de solicitação em cima de arranque inicial.
Para obter informações sobre como configurar um servidor de solicitação do DSC, consulte [configurar um servidor de solicitação do DSC web](pullServer.md).

Neste exemplo, utilizamos ambas a configuração descrita na secção anterior (**SampleIISInstall**) e a configuração meta do seguinte:

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

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a>Para inserir o documento MOF configuração meta no VHD

1. Montar o VHD para o qual pretende inserir a configuração meta ao chamar o [montar VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet. Por exemplo:

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

2. [Configurar um servidor de solicitação do DSC web](pullServer.md)e guarde o **SampleIISInistall** configuração para a pasta adequada.

3. Num computador com o PowerShell 5.0 ou posterior, guarde a configuração meta do acima (**PullClientBootstrap**) como um ficheiro de script (. ps1) do PowerShell.

4. Na consola do PowerShell, navegue para a pasta onde guardou o ficheiro. ps1.

5. Execute os seguintes comandos do PowerShell para compilar o documento MOF configuração meta (para obter informações sobre configurações de DSC a compilação, consulte [configurações de DSC](configurations.md):

    ```powershell
    . .\PullClientBootstrap.ps1
    PullClientBootstrap
    ```

6. Esta ação irá criar um `localhost.meta.mof` ficheiros numa pasta nova denominada `PullClientBootstrap`.
Mudar o nome e mover esse ficheiro para a localização correta no VHD como `MetaConfig.mof` utilizando o [Mover Item](https://technet.microsoft.comlibrary/hh849852.aspx) cmdlet.

    ```powershell
    Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\Sytem32\Configuration\MetaConfig.mof
    ```

7. Desmontar o VHD ao chamar o [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx) cmdlet. Por exemplo:

    ```powershell
    Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

8. Crie uma VM utilizando o VHD onde instalou o documento de DSC MOF.
Depois de iniciais existentes de segurança de arranque e instalação do sistema operativo, DSC irá solicitar a configuração do servidor de solicitação e IIS será instalado.
Pode verificar isto ao chamar o [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx) cmdlet.

## <a name="disable-dsc-at-boot-time"></a>Desativar o DSC no momento do arranque

Por predefinição, o valor da **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled** chave está definida como 2, que permite uma configuração de DSC executar se o computador está pendente ou atual Estado. Se não pretender que uma configuração para ser executada em cima de arranque inicial, por isso, tem de definir o valor desta chave como 0:

1. Montar o VHD ao chamar o [montar VHD](https://technet.microsoft.com/library/hh848551.aspx) cmdlet. Por exemplo:

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

2. Carregar o registo **HKLM\Software** subchave do VHD chamando `reg load`.

    ```
    reg load HKLM\Vhd E:\Windows\System32\Config\Software`
    ```

3. Navegue para o **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\***  utilizando o fornecedor de registo do PowerShell.

    ```powershell
    Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies`
    ```

4. Altere o valor de `DSCAutomationHostEnabled` como 0.

    ```powershell
    Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
    ```

5. Descarregar o registo executando os seguintes comandos:

    ```powershell
    [gc]::Collect()
    reg unload HKLM\Vhd
    ```

## <a name="see-also"></a>Consulte Também

- [Configurações de DSC](configurations.md)
- [Chave de registo DSCAutomationHostEnabled](DSCAutomationHostEnabled.md)
- [Configurar o Gestor de Configuração Local (LCM)](metaConfig.md)
- [Configurar um servidor de solicitação do DSC web](pullServer.md)

