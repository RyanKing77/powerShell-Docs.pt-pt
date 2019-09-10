---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
contributor: keithb
title: Instalar e configurar o WMF 5.1
ms.openlocfilehash: 241f52be011e1afc87d25c9a934db0c1e0361b76
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848127"
---
# <a name="install-and-configure-wmf-51"></a>Instalar e configurar o WMF 5,1

> [!IMPORTANT]
> O WMF 5,0 é substituído pelo WMF 5,1. Os usuários com o WMF 5,0 devem atualizar para o WMF 5,1 para receber suporte.
> **O WMF 5,1 requer o .NET Framework 4.5.2** (ou acima). A instalação terá êxito, mas os principais recursos falharão se o .NET 4.5.2 (ou superior) não estiver instalado.

## <a name="download-and-install-the-wmf-51-package"></a>Baixar e instalar o pacote WMF 5,1

Baixe o pacote do WMF 5,1 para o sistema operacional e a arquitetura em que você deseja instalá-lo:

| Sistema Operativo       | Pré-requisitos           | Links de pacote                          |
|------------------------|-------------------------|----------------------------------------|
| Windows Server 2012 R2 |                         | [Win8.1AndW2K12R2-KB3191564-x64.msu][] |
| Windows Server 2012    |                         | [W2K12-KB3191565-x64.msu][]            |
| Windows Server 2008 R2 | [.NET Framework 4.5.2][]| [Win7AndW2K8R2-KB3191566-x64.ZIP][]    |
| Windows 8.1            |                         | **x86** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</br>**x86** [Win8.1-KB3191564-x86.msu][] |
| Windows 7 SP1          | [.NET Framework 4.5.2][]| **x86** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</br>**x86** [Win7-KB3191566-x86.ZIP][] |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

- O WMF 5,1 Preview deve ser desinstalado antes da instalação do WMF 5,1 RTM.
- O WMF 5,1 pode ser instalado diretamente no WMF 5,0 ou no WMF 4,0.
- Não é **necessário** instalar o WMF 4,0 antes de instalar o WMF 5,1 no Windows 7 e no windows Server 2008 R2.

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a>Instalar o WMF 5,1 para Windows Server 2008 R2 e Windows 7

> [!NOTE]
> As instruções de instalação do Windows Server 2008 R2 e do Windows 7 foram alteradas e são diferentes das instruções para os outros pacotes. As instruções de instalação do Windows Server 2012 R2, do Windows Server 2012 e do Windows 8.1 estão abaixo.

### <a name="wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1"></a>Pré-requisitos do WMF 5,1 para Windows Server 2008 R2 SP1 e Windows 7 SP1

A instalação do WMF 5,1 no Windows Server 2008 R2 SP1 ou no Windows 7 SP1 requer o seguinte:

- Os service pack mais recentes devem ser instalados.
- O WMF 3,0 **não deve** ser instalado. A instalação do WMF 5,1 sobre o WMF 3,0 resultará na perda do PSModulePath`$env:PSModulePath`(), que pode causar falha em outros aplicativos. Antes de instalar o WMF 5,1, você deve desinstalar o WMF 3,0 ou salvar o **PSModulePath** e restaurá-lo manualmente após a conclusão da instalação do WMF 5,1.
- O WMF 5,1 requer pelo menos [.NET Framework 4.5.2](https://www.microsoft.com/download/details.aspx?id=42642).
  Você pode instalar o Microsoft .NET Framework 4.5.2 seguindo as instruções no local de download.

### <a name="installing-wmf-51-on-windows-server-2008-r2-and-windows-7"></a>Instalando o WMF 5,1 no Windows Server 2008 R2 e no Windows 7

1. Navegue até a pasta na qual você baixou o arquivo ZIP.

2. Clique com o botão direito do mouse no arquivo ZIP e selecione **extrair tudo...** . O arquivo zip contém dois arquivos: um MSU e o `Install-WMF5.1.ps1` arquivo de script. Depois de descompactar o arquivo ZIP, você poderá copiar o conteúdo para qualquer computador que esteja executando o Windows 7 ou o Windows Server 2008 R2.

3. Depois de extrair o conteúdo do arquivo ZIP, abra o PowerShell como administrador e, em seguida, navegue até a pasta que contém o conteúdo do arquivo ZIP.

4. Execute o `Install-WMF5.1.ps1` script nessa pasta e siga as instruções. Esse script verificará os pré-requisitos no computador local e instalará o WMF 5,1 se os pré-requisitos tiverem sido atendidos. Os pré-requisitos estão listados abaixo.

   `Install-WMF5.1.ps1`o usa os seguintes parâmetros para facilitar a automatização da instalação no Windows Server 2008 R2 e no Windows 7:

   - **AcceptEula**: Quando esse parâmetro é incluído, o EULA é automaticamente aceito e não será exibido.
   - **AllowRestart**: Esse parâmetro só poderá ser usado se AcceptEula for especificado. Se esse parâmetro estiver incluído e uma reinicialização for necessária após a instalação do WMF 5,1, a reinicialização ocorrerá sem avisar imediatamente após a conclusão da instalação.

## <a name="winrm-dependency"></a>Dependência do WinRM

A DSC (configuração de estado desejado) do Windows PowerShell depende do WinRM. O WinRM não está habilitado por padrão no Windows Server 2008 R2 e no Windows 7. Execute `Set-WSManQuickConfig`, em uma sessão com privilégios elevados do Windows PowerShell, para habilitar o WinRM.

## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a>Instalar o WMF 5,1 para Windows Server 2012 R2, Windows Server 2012 e Windows 8.1

### <a name="install-from-windows-file-explorer"></a>Instalar do explorador de arquivos do Windows

1. Navegue até a pasta na qual você baixou o arquivo MSU.
2. Clique duas vezes na MSU para executá-la.

### <a name="installing-from-the-command-prompt"></a>Instalando no prompt de comando

1. Depois de baixar o pacote correto para a arquitetura do seu computador, abra uma janela do prompt de comando com direitos de usuário elevados (executar como administrador). Nas opções de instalação Server Core do Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1, o prompt de comando é aberto com direitos de usuário elevados por padrão.
2. Altere os diretórios para a pasta na qual você baixou ou copiou o pacote de instalação do WMF 5,1.
3. Execute um dos seguintes comandos:
   - Em computadores que executam o Windows Server 2012 R2 ou Windows 8.1 x64, `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`execute.
   - Em computadores que executam o Windows Server 2012, `W2K12-KB3191565-x64.msu /quiet`execute.
   - Em computadores que executam o Windows 8.1 x86, `Win8.1-KB3191564-x86.msu /quiet`execute.

> [!NOTE]
> A instalação do WMF 5,1 requer uma reinicialização. O uso `/quiet` da opção reiniciará o sistema sem aviso. Use a `/norestart` opção para evitar a reinicialização. No entanto, o WMF 5,1 não será instalado até que você tenha reinicializado.
