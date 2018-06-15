# <a name="installing-powershell-core-on-windows"></a>Instalar o PowerShell Core no Windows

## <a name="msi"></a>MSI

Para instalar o PowerShell num cliente Windows ou Windows Server (funciona no Windows 7 SP1, Server 2008 R2 e posterior), transfira o pacote MSI da nossa página do GitHub [versões] [].

O ficheiro MSI aspeto- `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

Depois de transferido, faça duplo clique o instalador e siga as instruções.

Não há um atalho colocado no Menu Iniciar após a instalação.

- Por predefinição, o pacote está instalado para `$env:ProgramFiles\PowerShell\<version>`
- Pode iniciar PowerShell através do Menu Iniciar ou `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`

### <a name="prerequisites"></a>Pré-requisitos

Para ativar a comunicação remota do PowerShell através de WSMan, os seguintes pré-requisitos tem de ser cumpridos:

- Instalar o [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) nas versões do Windows antes do Windows 10.
  Está disponível através de transferência direta ou o Windows Update.
  Totalmente aplicado (incluindo pacotes opcionais), sistemas suportados já terão isto instalado.
- Instale o Windows Management Framework (WMF) 4.0 ou mais recente no Windows 7 e Windows Server 2008 R2.

## <a name="zip"></a>ZIP

PowerShell binários ZIP arquivos são fornecidos para ativar cenários de implementação avançada.
É de salientar que, ao utilizar o arquivo ZIP, não irá obter a verificação de pré-requisitos, como o pacote MSI.
Por isso ordem para a gestão remota através de WSMan funcione corretamente no Windows versões anteriores ao Windows 10, terá de certificar-se do [pré-requisitos](#prerequisites) são cumpridos.

## <a name="deploying-on-windows-iot"></a>A implementar em Windows IoT

Windows IoT é fornecido com o Windows PowerShell que iremos utilizar para implementar PowerShell Core 6.

1. Criar `PSSession` para o dispositivo de destino

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. Copie o pacote ZIP para o dispositivo

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-6.0.2-win-arm32.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. Ligar ao dispositivo e expanda o arquivo

   ```powershell
   Enter-PSSession $s
   cd u:\users\administrator\downloads
   Expand-Archive .\PowerShell-6.0.2-win-arm32.zip
   ```

4. Configurar a comunicação remota do PowerShell Core 6

   ```powershell
   cd .\PowerShell-6.0.2-win-arm32
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. Ligar ao ponto final de PowerShell Core 6 no dispositivo

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.6.0.2
   ```

## <a name="deploying-on-nano-server"></a>Implementar no servidor de Nano

Estas instruções partem do princípio de que uma versão do PowerShell já está em execução a imagem de servidor Nano e que foi gerado pelo [construtor de imagens do servidor Nano](/windows-server/get-started/deploy-nano-server).
Servidor de nano for um SO "sem interface". Os binários de núcleos pode implementar utilizando dois métodos diferentes.

1. Offline - montar o VHD de servidor Nano e deszipe o conteúdo do ficheiro zip à sua localização escolhida dentro da imagem montada.
2. Online - transferir o ficheiro zip através de uma sessão do PowerShell e deszipe-lo na sua localização escolhida.

Em ambos os casos, terá da versão do Windows 10 x64 ZIP do pacote e terá de executar os comandos dentro de uma instância do PowerShell do "Administrador".

### <a name="offline-deployment-of-powershell-core"></a>Implementação offline do PowerShell Core

1. Utilize o utilitário de favorito zip para descomprimir o pacote para um diretório na imagem de servidor Nano montada.
2. Desmontar a imagem e efetuar o arranque-lo.
3. Ligar à instância da pasta a receber do Windows PowerShell.
4. Siga as instruções para criar um ponto final de gestão remota utilizando o ["outra técnica de instância"](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

### <a name="online-deployment-of-powershell-core"></a>Implementação online do PowerShell Core

Os seguintes passos guiá-lo através da implementação do PowerShell Core para uma instância em execução de servidor Nano e a configuração do seu ponto final remoto.

- Ligar à instância da pasta a receber do Windows PowerShell

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

- Extrair o ficheiro ZIP

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- Se pretender que o sistema de interação remota com base em WSMan, siga as instruções para criar um ponto final de gestão remota utilizando o ["outra técnica de instância"](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).

## <a name="instructions-to-create-a-remoting-endpoint"></a>Instruções para criar um ponto final de gestão remota

PowerShell Core suporta o protocolo de comunicação remota do PowerShell (PSRP) através de SSH e WSMan.
Para mais informações, consulte:

- [SSH comunicação remota do PowerShell Core] [ssh-gestão remota]
- [WSMan sistema de interação remota no PowerShell Core] [wsman-sistema de interação remota]

## <a name="artifact-installation-instructions"></a>Instruções de instalação de artefactos

Está a publicar um arquivo com CoreCLR bits em cada compilação CI com [AppVeyor] [-].

Para instalar o PowerShell Core de artefacto CoreCLR:

1. Transferir o pacote ZIP da **artefactos** separador de compilação do específica.
2. Ficheiro ZIP de desbloqueio: rato no Explorador de ficheiros -> propriedades -> Aplicar 'Desbloquear' -> a caixa de verificação
3. Extrair o ficheiro zip para `bin` diretório
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO --> [versões]: https://github.com/PowerShell/PowerShell/releases [ssh-gestão remota]:... /Core-PowerShell/SSH-Remoting-in-PowerShell-Core.MD [wsman-sistema de interação remota]:... /Core-PowerShell/wsman-Remoting-in-PowerShell-Core.MD [AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell