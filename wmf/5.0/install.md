---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 3679c13c2d28f28f3102b24f6369f1dc264d6884
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="installation-instructions"></a>Instruções de instalação

Transferir o pacote correto para a arquitetura e o sistema operativo:

| Sistema Operativo       | Arquitetura | Nome do pacote              |
|------------------------|--------------|---------------------------|
| Windows Server 2012 R2 | x64      | [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
| Windows Server 2012    | x64      | [W2K12-KB3134759-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717506) |
| Windows Server 2008 R2 | x64      | [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 8.1            | x64          | [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
| Windows 8.1            | x86          | [Win8.1-KB3134758-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717963) |
| Windows 7 SP1          | x64          | [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 7 SP1          | x86          | [Win7-KB3134760-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717962) |


**Para instalar o WMF 5.0 do Explorador do Windows (ou o Explorador de ficheiros no Windows Server 2012 R2 e Windows 8.1):**

1. Navegue para a pasta na qual transferiu o ficheiro MSU.

2. Faça duplo clique MSU executá-la.

**Para instalar o WMF 5.0 da linha de comandos:**

1. Depois de transferir o pacote correto para a arquitetura do seu computador, abra uma janela de linha de comandos com direitos de utilizador elevados (executar como administrador). Nas opções de instalação Server Core do Windows Server 2012 R2 ou Windows Server 2012 ou Windows Server 2008 R2 SP1, linha de comandos é aberto com direitos de utilizador elevados por predefinição.

2. Altere os diretórios para a pasta na qual tem de transferir ou copiar o pacote de instalação do WMF 5.0.

3. Execute um dos seguintes comandos:
    - Em computadores que estejam a executar o Windows Server 2012 R2 ou Windows 8.1 x64, execute **Win8.1AndW2K12R2-KB3134758-x64.msu /quiet**.
    - Em computadores que estejam a executar o Windows Server 2012, execute **W2K12-KB3134759-x64.msu /quiet**.
    - Em computadores que estejam a executar o Windows Server 2008 R2 SP1 ou Windows 7 SP1 x64, execute **Win7AndW2K8R2-KB3134760-x64.msu /quiet**.
    - Em computadores que estejam a executar o Windows 8.1 x86, execute **Win8.1-KB3134758-x86.msu /quiet**.
    - Em computadores que estejam a executar o Windows 7 SP1 x86, execute **Win7-KB3134760-x86.msu /quiet**.

**Notas de instalação adicionais para o Windows Server 2008 SP1 e Windows 7 SP1:**

Certifique-se de que os seguintes pré-requisitos foram cumpridos:
- Service pack mais recente está instalado.
- [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) está instalado

*Dependência de WinRM:* depende da configuração de estado pretendido do Windows PowerShell (DSC) em WinRM. WinRM não está ativado por predefinição no Windows Server 2008 R2 e Windows 7. Para ativar o WinRM, num Windows PowerShell elevada sessão, execute **Set-WSManQuickConfig**.
