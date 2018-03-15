---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 510e1baa2933932cfd4c3bcb4e0973f3eb8095f3
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/15/2018
---
# <a name="system-requirements"></a>System Requirements (Requisitos do Sistema)

- Instale as atualizações mais recentes do Windows antes de instalar o WMF 5.0 RTM.
- Pode instalar o WMF 5.0 RTM apenas nos seguintes sistemas operativos:

    | Sistema Operativo       | Edições         | Pré-requisitos        |  Ligações de pacote |
    |------------------------|--------------|------------------|----------------------| --------------|
    | Windows Server 2012 R2 |  |  | [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
    | Windows Server 2012    |  |  | [W2K12-KB3134759-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717506) |
    | Windows Server 2008 R2 SP1 | Tudo, exceto IA64 | [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) e [.NET Framework 4.5 ou superior](https://msdn.microsoft.com/library/5a4x27ek.aspx) estão instalados| [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504)|
    | Windows 8.1 | Pro, Enterprise | | **x64:**  [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) </br> **x86:**  [Win8.1-KB3134758-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717963)|
    | Windows 7 SP1 | Todos | [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) e [.NET Framework 4.5 ou superior](https://msdn.microsoft.com/library/5a4x27ek.aspx) estão instalados | **x64:**  [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504)  </br> **x86:**  [Win7-KB3134760-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717962)|

# <a name="installation-instructions"></a>Instruções de instalação

### <a name="to-install-wmf-50-from-windows-explorer-or-file-explorer"></a>Para instalar o WMF 5.0 do Explorador do Windows (ou o Explorador de ficheiros):

1. Navegue para a pasta na qual transferiu o ficheiro MSU.

2. Faça duplo clique MSU executá-la.

### <a name="to-install-wmf-50-from-command-prompt"></a>Para instalar o WMF 5.0 da linha de comandos:

1. Depois de transferir o pacote correto para a arquitetura do seu computador, abra uma janela de linha de comandos com direitos de utilizador elevados (executar como administrador). Nas opções de instalação Server Core do Windows Server 2012 R2 ou Windows Server 2012 ou Windows Server 2008 R2 SP1, linha de comandos é aberto com direitos de utilizador elevados por predefinição.

2. Altere os diretórios para a pasta na qual tem de transferir ou copiar o pacote de instalação do WMF 5.0.

3. Execute um dos seguintes comandos:
    - Em computadores que estejam a executar o Windows Server 2012 R2 ou Windows 8.1 x64, execute **Win8.1AndW2K12R2-KB3134758-x64.msu /quiet**.
    - Em computadores que estejam a executar o Windows Server 2012, execute **W2K12-KB3134759-x64.msu /quiet**.
    - Em computadores que estejam a executar o Windows Server 2008 R2 SP1 ou Windows 7 SP1 x64, execute **Win7AndW2K8R2-KB3134760-x64.msu /quiet**.
    - Em computadores que estejam a executar o Windows 8.1 x86, execute **Win8.1-KB3134758-x86.msu /quiet**.
    - Em computadores que estejam a executar o Windows 7 SP1 x86, execute **Win7-KB3134760-x86.msu /quiet**.

### <a name="additional-installation-notes-for-windows-server-2008-r2-sp1-and-windows-7-sp1"></a>Notas de instalação adicionais para o Windows Server 2008 R2 SP1 e Windows 7 SP1:

Certifique-se de que os seguintes pré-requisitos foram cumpridos:
- Service pack mais recente está instalado.
- [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) está instalado.
- [.NET framework 4.5 ou superior](https://msdn.microsoft.com/library/5a4x27ek.aspx) está instalado.

**O WMF 4.0 dependência**

Sistemas Windows Server 2008 R2 SP1 e Windows 7 SP1 tem incorporadas do PowerShell 2.0, WinRM e WMI. Foram lançados pacotes WMF 3.0 e o WMF 4.0, que atualiza estes componentes incorporados, após o lançamento do Windows Server 2008 R2 SP1 e Windows 7 SP1. Instalar/desinstalar WMF 3.0 e o WMF 4.0 pacotes detetados pelo alguns problemas no seguinte caminho de atualização:

- Incorporado--> WMF 4.0
- Incorporado--> WMF 3.0--> WMF4.0. 

Iremos fixo, todos os estes problemas em pacotes do WMF 4.0. Por conseguinte, não há um pré-requisito do WMF 4.0 para a instalação do WMF 5.0 no Windows Server 2008 R2 SP1 e Windows 7 SP1. Seguem-se os problemas específicos que poderá encontrar se não instalar WMF 4.0 antes de atualizar para o WMF 5.0:

- Registo de eventos reencaminhado não está disponível e EventCollector registo não é apresentado no Visualizador de eventos depois de desinstalar o WMF 3.0 ou WMF 5.0 (sem o pré-requisito WMF 4.0 instalado) no Windows 7 SP1 e no Windows Server 2008 R2 SP1 ([KB2809215](https://support.microsoft.com/en-us/kb/2809215)).
- A personalização *PSModulePath* obtém repor variável de ambiente para o valor predefinido, quando atualizar diretamente a partir do PowerShell 2.0 incorporada para o WMF 5.0 ([KB2872035](https://support.microsoft.com/en-us/kb/2872035)) ou a partir do WMF 3.0 para o WMF 5.0. ([KB2872047](https://support.microsoft.com/en-us/kb/2872047)) no Windows 7 SP1 e no Windows Server 2008 R2 SP1.

**Dependência de WinRM**

Configuração de estado pretendido do Windows PowerShell (DSC) depende do WinRM. WinRM não está ativado por predefinição no Windows Server 2008 R2 SP1 e Windows 7 SP1. Para ativar o WinRM, num Windows PowerShell elevada sessão, execute **Set-WSManQuickConfig**.

# <a name="uninstallation-instructions"></a>Instruções de desinstalação

### <a name="using-command-prompt"></a>Utilizando a linha de comandos

1.  Abra **linha de comandos.**

2.  Execute o [iniciador de autónomo do Windows Update](https://support.microsoft.com/en-us/kb/934307) conforme mostrado abaixo:

No Windows Server 2012 R2 e Windows 8.1:
```powershell
wusa /uninstall /kb:3134758
```
On Windows Server 2012:
```powershell
wusa /uninstall /kb:3134759
```
No Windows Server 2008 R2 SP1 e Windows 7 SP1:
```powershell
wusa /uninstall /kb:3134760
```

### <a name="using-control-panel"></a>Utilizando o painel de controlo

1.  Abra **painel de controlo.**

2.  Abrir **programas**, em seguida, abra **desinstalar um programa.**

3.  Clique em **ver atualizações instaladas.**

4.  Selecione **Windows Management Framework 5.0** da lista de atualizações instaladas. Isto corresponde à *KB3134758*, *KB3134759*, ou *KB3134760*. Clique em **desinstalar.**

