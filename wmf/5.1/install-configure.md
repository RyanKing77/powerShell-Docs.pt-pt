---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
contributor: keithb
title: Instalar e configurar o WMF 5.1
ms.openlocfilehash: 74c19d2eb04b77b1e2b1c8d8977f9b4db6e94e4f
ms.sourcegitcommit: 9910675e8758042b5949c99b381a926d2b4e8c21
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/03/2017
---
# <a name="install-and-configure-wmf-51"></a>Instalar e configurar o WMF 5.1 #


## <a name="download-and-install-the-wmf-51-package"></a>Transfira e instale o pacote do WMF 5.1

Transferir o pacote do WMF 5.1 para o sistema operativo e a arquitetura que pretende instalá-lo:

| Sistema Operativo       | Pré-requisitos       | Ligações de pacote             |
|------------------------|---------------------|---------------------------|
| Windows Server 2012 R2 | | [Win8.1AndW2K12R2-KB3191564-x64.msu](https://go.microsoft.com/fwlink/?linkid=839516)|
| Windows Server 2012    | | [W2K12-KB3191565-x64.msu](https://go.microsoft.com/fwlink/?linkid=839513)|
| Windows Server 2008 R2 | [.NET framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642) | [Win7AndW2K8R2-KB3191566-x64.ZIP](https://go.microsoft.com/fwlink/?linkid=839523) | 
| Windows 8.1            |  | **x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu](https://go.microsoft.com/fwlink/?linkid=839516) </br> **x86:** [Win8.1-KB3191564-x86.msu](https://go.microsoft.com/fwlink/?linkid=839521) |
| Windows 7 SP1          | [.NET framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642) | **x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP](https://go.microsoft.com/fwlink/?linkid=839523) </br> **x86:** [Win7-KB3191566-x86.ZIP](https://go.microsoft.com/fwlink/?linkid=839522)



## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a>Instalar o WMF 5.1 para Windows Server 2008 R2 e Windows 7

> **Nota:** instruções de instalação para o Windows Server 2008 R2 e Windows 7 foram alterados e diferem das instruções para os outros pacotes. As instruções de instalação para o Windows Server 2012 R2, Windows Server 2012 e Windows 8.1 são abaixo.

**Instalar o WMF 5.1 no Windows Server 2008 R2 e Windows 7**

1. Navegue para a pasta na qual transferiu o ficheiro ZIP. 

2. Clique com o botão direito no ficheiro ZIP e selecione "Extrair todos os...". Zip contém 2 ficheiros: um MSU e o ficheiro de script de instalação WMF5.1.PS1. Após a descompactação o ficheiro ZIP, pode copiar o conteúdo a qualquer máquina com o Windows 7 ou Windows Server 2008 R2.  

3. Depois do ZIP a extrair conteúdo de ficheiros, abra o PowerShell como administrador, em seguida, navegue para a pasta que contém o  
conteúdo do ficheiro ZIP. 

4. Execute o script de instalação Wmf5.1.ps1 nessa pasta e siga as instruções. Este script irá verificar os pré-requisitos no computador local e instale o WMF 5.1 se os pré-requisitos tiverem sido cumpridos. Os pré-requisitos estão listados abaixo. 

Instalação WMF5.1.ps1 utiliza os parâmetros seguintes para facilitar a automatizar a instalação no Windows Server 2008 R2 e Windows 7:

- AcceptEula: Quando este parâmetro é incluído, o EULA é aceite automaticamente e não será apresentado.
- AllowRestart: Este parâmetro só pode ser utilizado se AcceptEula for especificado. Se este parâmetro é incluído e for necessário um reinício após a instalação do WMF 5.1, o reinício acontecerá sem pedir confirmação imediatamente após a instalação estiver concluída. 

**WMF 5.1 pré-requisitos para o Windows Server 2008 R2 SP1 e Windows 7 SP1**

Instalação do WMF 5.1 no Windows Server 2008 R2 SP1 ou Windows 7 SP1, necessita do seguinte:
- Deve ser instalado o service pack mais recente.
- WMF 3.0 **tem não** ser instalado. Instalar o WMF 5.1 ao longo do WMF 3.0 resultará na perda de PSModulePath, que pode fazer com que outras aplicações falhar. Antes de instalar o WMF 5.1, tem do desinstalar WMF 3.0, ou guardar o PSModulePath e, em seguida, restaurá-lo manualmente após a conclusão da instalação do WMF 5.1. 
- WMF 5.1 requer, pelo menos, [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642).
Pode instalar o Microsoft .NET Framework 4.5.2 ao seguir as instruções na localização de transferência.

**Dependência de WinRM** 

Configuração de estado pretendido do Windows PowerShell (DSC) depende do WinRM. WinRM não está ativado por predefinição no Windows Server 2008 R2 e Windows 7. Executar `Set-WSManQuickConfig`, num Windows PowerShell elevada sessão, para ativar o WinRM.


## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a>Instalar o WMF 5.1 para Windows Server 2012 R2, Windows Server 2012 e Windows 8.1
**Instalar a partir do Explorador do Windows (ou o Explorador de ficheiros no Windows Server 2012 R2 ou Windows 8.1)**

1. Navegue para a pasta na qual transferiu o ficheiro MSU.

2. Faça duplo clique MSU executá-la.

**Instalar a partir da linha de comandos**

1. Depois de transferir o pacote correto para a arquitetura do seu computador, abra uma janela de linha de comandos com direitos de utilizador elevados (executar como administrador). Nas opções de instalação Server Core do Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1, linha de comandos é aberto com direitos de utilizador elevados por predefinição.

2. Altere os diretórios para a pasta na qual tem de transferir ou copiar o pacote de instalação do WMF 5.1.

3. Execute um dos seguintes comandos:
    - Em computadores que estejam a executar o Windows Server 2012 R2 ou Windows 8.1 x64, execute `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.
    - Em computadores que estejam a executar o Windows Server 2012, execute `W2K12-KB3191565-x64.msu /quiet`.
    - Em computadores que estejam a executar o Windows 8.1 x86, execute `Win8.1-KB3191564-x86.msu /quiet`.
    
