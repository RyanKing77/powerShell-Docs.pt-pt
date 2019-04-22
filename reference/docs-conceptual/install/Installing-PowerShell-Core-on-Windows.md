---
title: Instalar o PowerShell Core no Windows
description: Informações sobre como instalar o PowerShell Core no Windows
ms.date: 08/06/2018
ms.openlocfilehash: 910ee5a653fc1703bfddaf6367225f3b654d600f
ms.sourcegitcommit: 17ce42f97e13e8b3286779dc3f583474b0357023
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/18/2019
ms.locfileid: "59293015"
---
# <a name="installing-powershell-core-on-windows"></a>Instalar o PowerShell Core no Windows

Existem várias formas de instalar o PowerShell Core no Windows.

## <a name="prerequisites"></a>Pré-requisitos

Para ativar a comunicação remota do PowerShell em WSMan, é necessário ser cumpridos os seguintes pré-requisitos:

- Instalar o [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) em versões do Windows antes do Windows 10. Está disponível através de transferência direta ou atualização do Windows. Com todos os patches (incluindo pacotes opcionais), sistemas suportados já terá esta instalado.
- Instale o Windows Management Framework (WMF) 4.0 ou mais recente no Windows 7 e Windows Server 2008 R2.

## <a name="a-idmsi-installing-the-msi-package"></a><a id="msi" />Instalar o pacote MSI

Para instalar o PowerShell num cliente Windows ou Windows Server (funciona no Windows 7 SP1, Server 2008 R2 e posterior), transfira o pacote MSI da nossa página do GitHub [versões] []. Desloque para baixo para o **ativos** secção da versão que pretende instalar. A seção de recursos pode ser fechada, por isso terá de clicar para expandi-lo.

O arquivo MSI é semelhante a esta- `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

Depois de transferido, clique duas vezes o instalador e siga as instruções.

O instalador cria um atalho no Menu Iniciar do Windows.

- Por predefinição, o pacote está instalado para `$env:ProgramFiles\PowerShell\<version>`
- Pode iniciar o PowerShell, no menu Iniciar ou `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`

### <a name="administrative-install-from-the-command-line"></a>Instalar administrativa a partir da linha de comandos

Podem ser instalados pacotes MSI na linha de comando. Isso permite que os administradores implantem pacotes sem interação do utilizador. O pacote do MSI para o PowerShell inclui as seguintes propriedades para controlar as opções de instalação:

- **ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** -esta propriedade controla a opção para adicionar a **PowerShell aberto** item ao menu de contexto no Windows Explorer.
- **ENABLE_PSREMOTING** -esta propriedade controla a opção para ativar a comunicação remota do PowerShell durante a instalação.
- **REGISTER_MANIFEST** -esta propriedade controla a opção para registar o manifesto de registo de eventos do Windows.

Os exemplos a seguir mostra como instalar automaticamente o PowerShell Core com todas as opções de instalação ativadas.

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

Para obter uma lista completa de opções de linha de comandos para Msiexec.exe, consulte [opções de linha de comandos](/windows/desktop/Msi/command-line-options).

## <a name="a-idzip-installing-the-zip-package"></a><a id="zip" />Instalar o pacote ZIP

Arquivos ZIP binários do PowerShell são fornecidos para ativar cenários de implementação avançada. Se observar que ao usar o arquivo ZIP, não obtém a verificação de pré-requisitos, tal como o pacote MSI. Para a gestão remota em WSMan funcione corretamente, certifique-se de que cumpriu os [pré-requisitos](#prerequisites).

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
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. Ligar ao dispositivo e expanda o arquivo

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. Configurar a comunicação remota do PowerShell Core 6

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. Ligar ao ponto final do PowerShell Core 6 no dispositivo

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
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
4. Siga as instruções para criar um ponto de extremidade de comunicação remota utilizando o ["outra técnica de instância"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

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

- Se pretender que a comunicação remota baseada em WSMan, siga as instruções para criar um ponto de extremidade de comunicação remota utilizando o ["outra técnica de instância"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

## <a name="how-to-create-a-remoting-endpoint"></a>Como criar um ponto de extremidade de comunicação remota

O PowerShell Core suporta o protocolo de comunicação remota do PowerShell (PSRP) através de WSMan e SSH. Para mais informações, consulte:

- [SSH comunicação remota no PowerShell Core] [ssh-comunicação remota]
- [WSMan comunicação remota no PowerShell Core] [wsman remoting]

<!-- [download-center]: TODO -->
[versões]: https://github.com/PowerShell/PowerShell/releases [ssh-comunicação remota]:.... /Core-PowerShell/SSH-Remoting-in-PowerShell-Core.MD [wsman remoting]:.... /Core-PowerShell/wsman-Remoting-in-PowerShell-Core.MD [AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
