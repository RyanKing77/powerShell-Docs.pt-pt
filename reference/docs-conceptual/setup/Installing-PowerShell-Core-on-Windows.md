---
title: Instalar o PowerShell Core no Windows
description: Informações sobre como instalar o PowerShell Core no Windows
ms.date: 08/06/2018
ms.openlocfilehash: 2b21908c38796117308f2ac1219db00ff9086408
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850984"
---
# <a name="installing-powershell-core-on-windows"></a>Instalar o PowerShell Core no Windows

## <a name="msi"></a>MSI

Para instalar o PowerShell num cliente Windows ou Windows Server (funciona no Windows 7 SP1, Server 2008 R2 e posterior), transferir o pacote MSI a partir do nosso GitHub [versões][] página.

O arquivo MSI é semelhante a esta- `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

Depois de transferido, clique duas vezes o instalador e siga as instruções.

Existe um atalho colocado no Menu Iniciar, após a instalação.

- Por predefinição, o pacote está instalado para `$env:ProgramFiles\PowerShell\<version>`
- Pode iniciar o PowerShell, no menu Iniciar ou `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`

### <a name="prerequisites"></a>Pré-requisitos

Para ativar a comunicação remota do PowerShell em WSMan, é necessário ser cumpridos os seguintes pré-requisitos:

- Instalar o [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) em versões do Windows antes do Windows 10.
  Está disponível através de transferência direta ou atualização do Windows.
  Com todos os patches (incluindo pacotes opcionais), sistemas suportados já terá esta instalado.
- Instale o Windows Management Framework (WMF) 4.0 ou mais recente no Windows 7 e Windows Server 2008 R2.

## <a name="zip"></a>ZIP

Arquivos ZIP binários do PowerShell são fornecidos para ativar cenários de implementação avançada.
Se observar que ao usar o arquivo ZIP, não obtém a verificação de pré-requisitos, tal como o pacote MSI.
Portanto, para a gestão remota em WSMan funcione corretamente em versões do Windows antes do Windows 10, tem de certificar-se a [pré-requisitos](#prerequisites) são cumpridos.

## <a name="deploying-on-windows-iot"></a>Implantando o Windows IoT

Windows IoT já vem com o Windows PowerShell que vamos utilizar para implementar o PowerShell Core 6.

1. Criar `PSSession` dispositivo de destino

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. Copiar o pacote ZIP para o dispositivo

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-6.1.0-win-arm32.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. Ligar ao dispositivo e expanda o arquivo

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-6.1.0-win-arm32.zip
   ```

4. Configurar a comunicação remota do PowerShell Core 6

   ```powershell
   Set-Location .\PowerShell-6.1.0-win-arm32
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. Ligar ao ponto final do PowerShell Core 6 no dispositivo

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.6.1.0
   ```

## <a name="deploying-on-nano-server"></a>Implementar no servidor Nano

Estas instruções partem do princípio de que uma versão do PowerShell já está em execução na imagem do servidor Nano e que tenha sido gerado pela [construtor de imagens do servidor Nano](/windows-server/get-started/deploy-nano-server).
O servidor nano é um sistema operacional "sem interface". Os binários do principal pode implementar através de dois métodos diferentes.

1. Offline - Monte o VHD do servidor Nano e Descompacte o conteúdo do ficheiro zip para a sua localização escolhida dentro da imagem montada.
2. Online - transferir o ficheiro zip através de uma sessão do PowerShell e Descompacte-o em seu local escolhido.

Em ambos os casos, terá da versão x64 do Windows 10 ZIP do pacote e será necessário executar os comandos dentro de uma instância do PowerShell de "Administrador".

### <a name="offline-deployment-of-powershell-core"></a>Implantação offline do PowerShell Core

1. Utilize o utilitário zip Favoritos para descomprimir o pacote para um diretório dentro da imagem montada do servidor Nano.
2. Desmonte a imagem e inicializá-la.
3. Ligue à instância da caixa de entrada do Windows PowerShell.
4. Siga as instruções para criar um ponto de extremidade de comunicação remota utilizando o ["outra técnica de instância"](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

### <a name="online-deployment-of-powershell-core"></a>Implantação online do PowerShell Core

Os seguintes passos guiá-lo por meio da implantação do PowerShell Core para uma instância em execução do servidor Nano e a configuração do seu ponto final remoto.

- Ligue à instância da caixa de entrada do Windows PowerShell

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- Copie o ficheiro para a instância de servidor Nano

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- Introduza a sessão

  ```powershell
  Enter-PSSession $session
  ```

- Extraia o ficheiro ZIP

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- Se pretender que a comunicação remota baseada em WSMan, siga as instruções para criar um ponto de extremidade de comunicação remota utilizando o ["outra técnica de instância"](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

## <a name="instructions-to-create-a-remoting-endpoint"></a>Instruções para criar um ponto de extremidade de comunicação remota

O PowerShell Core suporta o protocolo de comunicação remota do PowerShell (PSRP) através de WSMan e SSH.
Para mais informações, consulte:

- [SSH comunicação remota no PowerShell Core][ssh-remoting]
- [Comunicação remota do WSMan no PowerShell Core][wsman-remoting]

## <a name="artifact-installation-instructions"></a>Instruções de instalação do artefacto

Publicamos um arquivo morto com bits de CoreCLR em todas as compilações CI com [AppVeyor][].

Para instalar o PowerShell Core a partir do artefacto de CoreCLR:

1. Transferir o pacote ZIP da **artefactos** separador da compilação específica.
2. Ficheiro ZIP de desbloqueio: botão direito do rato no Explorador de ficheiros -> Properties -> aplica "Desbloquear" -> a caixa de verificação
3. Extrair o ficheiro zip para `bin` diretório
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO -->

[versões]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
