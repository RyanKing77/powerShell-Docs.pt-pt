---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
contributor: keithb
title: Instalar e configurar o WMF 5.1
ms.openlocfilehash: e5590d48d467506270ccef4089513e1afade07be
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795577"
---
# <a name="install-and-configure-wmf-51"></a>Instalar e configurar o WMF 5.1

## <a name="download-and-install-the-wmf-51-package"></a>Transfira e instale o pacote do WMF 5.1

Transferir o pacote de WMF 5.1 para o sistema operativo e a arquitetura que deseja instalá-lo em:

| Sistema Operativo       | Pré-requisitos           | Ligações de pacote                          |
|------------------------|-------------------------|----------------------------------------|
| Windows Server 2012 R2 |                         | [Win8.1AndW2K12R2-KB3191564-x64.msu][] |
| Windows Server 2012    |                         | [W2K12-KB3191565-x64.msu][]            |
| Windows Server 2008 R2 | [.NET Framework 4.5.2][]| [Win7AndW2K8R2-KB3191566-x64.ZIP][]    |
| Windows 8.1            |                         | **x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</br>**x86:** [Win8.1-KB3191564-x86.msu][] |
| Windows 7 SP1          | [.NET Framework 4.5.2][]| **x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</br>**x86:** [Win7-KB3191566-x86.ZIP][] |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a>Instale o WMF 5.1 para o Windows Server 2008 R2 e Windows 7

> **Nota:** Instruções de instalação para Windows Server 2008 R2 e Windows 7 foram alterados e diferem das instruções para os outros pacotes. Instruções de instalação para Windows Server 2012 R2, Windows Server 2012 e Windows 8.1 estão abaixo.

**Instalar o WMF 5.1 no Windows Server 2008 R2 e Windows 7**

1. Navegue para a pasta na qual transferiu o ficheiro ZIP.

2. Com o botão direito no ficheiro ZIP e selecione "Extrair todos os...". O Zip contém 2 ficheiros: um MSU e o ficheiro de script de instalação WMF5.1.PS1.
Depois de descompactação o ficheiro ZIP, pode copiar o conteúdo a qualquer máquina com o Windows 7 ou Windows Server 2008 R2.

3. Depois de extrair o conteúdo do ficheiro ZIP, abra o PowerShell como administrador, em seguida, navegue para a pasta que contenha o conteúdo do ficheiro ZIP.

4. Execute o script de instalação Wmf5.1.ps1 nessa pasta e siga as instruções. Este script irá verificar os pré-requisitos no computador local e instale o WMF 5.1 se os pré-requisitos tiverem sido cumpridos. Os pré-requisitos estão listados abaixo.

Instalação WMF5.1.ps1 precisa dos seguintes parâmetros para facilitar a automatizar a instalação no Windows Server 2008 R2 e Windows 7:

- AcceptEula: Quando este parâmetro está incluído, o EULA automaticamente é aceite e não será apresentado.
- AllowRestart: Este parâmetro só pode ser utilizado se não for especificado AcceptEula. Se este parâmetro está incluído e é necessário um reinício após a instalação do WMF 5.1, irá ocorrer o reinício sem pedir confirmação imediatamente após a instalação estiver concluída.

**WMF 5.1 pré-requisitos para o Windows Server 2008 R2 SP1 e Windows 7 SP1**

Instalação do WMF 5.1 no Windows Server 2008 R2 SP1 ou Windows 7 SP1, necessita do seguinte:
- Deve ser instalado o service pack mais recente.
- WMF 3.0 **não podem** ser instalado. Instalação do WMF 5.1 ao longo do WMF 3.0 resultará na perda de PSModulePath, que pode fazer com que outros aplicativos efetuar a ativação. Antes de instalar o WMF 5.1, tem do desinstalar WMF 3.0, ou guardar o PSModulePath e, em seguida, restaurá-lo manualmente após a conclusão da instalação do WMF 5.1.
- WMF 5.1 requer pelo menos [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642).
Pode instalar o Microsoft .NET Framework 4.5.2 ao seguir as instruções na localização de transferência.

**Dependência de WinRM**

Windows PowerShell Desired State Configuration (DSC) depende de WinRM.
WinRM não está ativado por padrão no Windows Server 2008 R2 e Windows 7.
Executar `Set-WSManQuickConfig`, no Windows PowerShell elevados sessão, para ativar o WinRM.

## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a>Instale o WMF 5.1 para o Windows Server 2012 R2, Windows Server 2012 e Windows 8.1

**Instalar a partir do Explorador do Windows (ou o Explorador de ficheiros no Windows Server 2012 R2 ou Windows 8.1)**

1. Navegue para a pasta na qual transferiu o ficheiro MSU.
2. Faça duplo clique MSU executá-lo.

**Instalar a partir da linha de comandos**

1. Depois de transferir o pacote correto para a arquitetura do seu computador, abra uma janela de linha de comandos com direitos de utilizador elevados (executar como administrador). Sobre as opções de instalação Server Core do Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1, linha de comandos é aberta com direitos de utilizador elevados por predefinição.
2. Altere os diretórios para a pasta em que tiver transferido ou copiado o pacote de instalação do WMF 5.1.
3. Execute um dos seguintes comandos:
   - Nos computadores que executem Windows Server 2012 R2 ou Windows 8.1 x64, execute `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.
   - Nos computadores que executem Windows Server 2012, execute `W2K12-KB3191565-x64.msu /quiet`.
   - Nos computadores que estejam a executar o Windows 8.1 x86, execute `Win8.1-KB3191564-x86.msu /quiet`.

> [!NOTE]
> A instalação de WMF 5.1 requer um reinício. Usando o `/quiet` opção irá reiniciar o sistema sem aviso.
> Utilize o `/norestart` opção para evitar o reinício. No entanto, WMF 5.1 não será instalado até que foram reiniciados.
