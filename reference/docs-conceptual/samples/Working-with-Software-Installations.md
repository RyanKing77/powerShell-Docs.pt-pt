---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Trabalhar com Instalações de Software
ms.assetid: 51a12fe9-95f6-4ffc-81a5-4fa72a5bada9
ms.openlocfilehash: 9369e3c5ac670895cd4fbd3ebc895c50efd02051
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293236"
---
# <a name="working-with-software-installations"></a>Trabalhar com Instalações de Software

Aplicativos que são projetados para usar o Windows Installer podem ser acedidos através do WMI **Win32_Product** classe, mas nem todos os aplicativos em uso atualmente utilizam o instalador do Windows. Uma vez que o instalador do Windows oferece uma gama mais ampla de técnicas padrão para trabalhar com aplicativos instaláveis, nos concentraremos principalmente nesses aplicativos. Aplicativos que usam as rotinas de instalação alternativa em geral, não serão geridos pelo instalador do Windows. Técnicas específicas para trabalhar com esses aplicativos dependerá do software de instalador e as decisões tomadas pelo desenvolvedor do aplicativo.

> [!NOTE]
> Aplicativos que são instalados por copiar os ficheiros de aplicação para o computador normalmente não podem ser geridos utilizando técnicas discutidas aqui. Pode gerir estas aplicações, como ficheiros e pastas utilizando as técnicas discutidas na seção "A trabalhar com ficheiros e pastas".

## <a name="listing-windows-installer-applications"></a>A listagem de aplicações do Windows Installer

Para listar os aplicativos instalados com o instalador do Windows num sistema local ou remoto, utilize a seguinte consulta WMI simple:

```
PS> Get-WmiObject -Class Win32_Product -ComputerName .

IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
Name              : Microsoft .NET Framework 2.0
Vendor            : Microsoft Corporation
Version           : 2.0.50727
Caption           : Microsoft .NET Framework 2.0
```

Para exibir todas as propriedades do objeto Win32_Product para a exibição, utilize o parâmetro de propriedades dos cmdlets de formatação, como o cmdlet Format-List, com um valor de \* (todos).

```
PS> Get-WmiObject -Class Win32_Product -ComputerName . | Where-Object -FilterScript {$_.Name -eq "Microsoft .NET Framework 2.0"} | Format-List -Property *

Name              : Microsoft .NET Framework 2.0
Version           : 2.0.50727
InstallState      : 5
Caption           : Microsoft .NET Framework 2.0
Description       : Microsoft .NET Framework 2.0
IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
InstallDate       : 20060506
InstallDate2      : 20060506000000.000000-000
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\619ab2.msi
SKUNumber         :
Vendor            : Microsoft Corporation
```

Em alternativa, pode utilizar o **filtro de Get-WmiObject** parâmetro para selecionar apenas o Microsoft .NET Framework 2.0. Como o filtro utilizado neste comando é um filtro WMI, ele usa a sintaxe de linguagem WQL (WMI Query), não o Windows PowerShell sintaxe. Em vez disso:

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='Microsoft .NET Framework 2.0'"| Format-List -Property *
```

Observe que consultas WQL com frequência, caracteres de uso, como espaços ou sinais de igual, que têm um significado especial no Windows PowerShell. Por esse motivo, é prudente sempre coloque o valor do parâmetro de filtro de aspas. Também pode utilizar o caráter de escape do Windows PowerShell, um acento grave (\`), apesar de não poder melhorar a legibilidade. O seguinte comando equivale ao comando anterior e retorna os mesmos resultados, mas utiliza o acento grave usar caracteres especiais, em vez de analisar a cadeia de filtro de todo.

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter Name`=`'Microsoft` .NET` Framework` 2.0`' | Format-List -Property *
```

Para listar apenas as propriedades que lhe interessam, utilize o parâmetro de propriedade dos cmdlets de formatação para listar as propriedades pretendidas.

```
Get-WmiObject -Class Win32_Product -ComputerName . | Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
...
Name              : HighMAT Extension to Microsoft Windows XP CD Writing Wizard
InstallDate       : 20051022
InstallLocation   : C:\Program Files\HighMAT CD Writing Wizard\
PackageCache      : C:\WINDOWS\Installer\113b54.msi
Vendor            : Microsoft Corporation
Version           : 1.1.1905.1
IdentifyingNumber : {FCE65C4E-B0E8-4FBD-AD16-EDCBE6CD591F}
...
```

Por fim localizar apenas os nomes dos aplicativos instalados, um simples **Format-Wide** instrução simplifica a saída:

```powershell
Get-WmiObject -Class Win32_Product -ComputerName .  | Format-Wide -Column 1
```

Apesar de agora, temos várias formas de considerar aplicações a utilizar o instalador do Windows para instalação, não levamos em outros aplicativos. Uma vez que aplicativos mais padrão registrar seus desinstalador com Windows, podemos trabalhar com esses localmente localizando-los no registo do Windows.

## <a name="listing-all-uninstallable-applications"></a>A listagem de todos os aplicativos desinstalados

Embora não existe nenhuma forma garantida para localizar todos os aplicativos num sistema, é possível localizar todos os programas com listagens apresentadas na caixa de diálogo Adicionar ou remover programas. Adicionar ou remover programas encontra esses aplicativos na seguinte chave do Registro:

**HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall**.

Também podemos examinar esta chave para encontrar aplicações. Para facilitar ver a chave de desinstalação, podemos mapear uma unidade do Windows PowerShell para esta localização de registo:

```
PS> New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

> [!NOTE]
> O **HKLM:** unidade está mapeada para a raiz do **HKEY_LOCAL_MACHINE**, por isso, usamos essa unidade no caminho para a chave de desinstalação. Em vez de **HKLM:** poderia especificamos o caminho do registo através de um **HKLM** ou **HKEY_LOCAL_MACHINE**. A vantagem de utilizar uma unidade de registo existente é que podemos utilizar conclusão de tabulação para preencher os nomes de chaves, pelo que não é necessário para escrevê-los.

Agora, temos uma unidade com o nome "Desinstalar", que pode ser usado de maneira rápida e conveniente, procurar as instalações de aplicativos. Que podemos encontrar o número de aplicativos instalados por contar o número de chaves de registro na desinstalação: Unidade do Windows PowerShell:

```
PS> (Get-ChildItem -Path Uninstall:).Count
459
```

Poderemos pesquisar esta lista de aplicativos ainda mais usando uma variedade de técnicas, a partir **Get-ChildItem**. Para obter uma lista de aplicativos e guardá-los no **$UninstallableApplications** variável, utilize o seguinte comando:

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

> [!NOTE]
> Estamos a utilizar um demorado nome de variável aqui por motivos de clareza. Na utilização real, não há motivo para usar nomes longos. Embora seja possível usar a conclusão de tabulação para nomes de variáveis, também pode utilizar nomes de caracteres de 1 a 2 para a velocidade. Nomes de mais tempo e descritivos são mais úteis quando estiver a desenvolver o código para reutilização.

Para apresentar os valores das entradas de registro nas chaves de registo em desinstalar, utilize o método GetValue das chaves de registo. O valor do método é o nome da entrada do Registro.

Por exemplo, para localizar os nomes a apresentar dos aplicativos na chave Uninstall, utilize o seguinte comando:

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

Não é garantido que estes valores são exclusivos. No exemplo seguinte, dois itens instalados são apresentadas como "Windows Media Encoder 9 série":

```
PS> Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion\Uninstall

SKC  VC Name                           Property
---  -- ----                           --------
  0   3 Windows Media Encoder 9        {DisplayName, DisplayIcon, UninstallS...
  0  24 {E38C00D0-A68B-4318-A8A6-F7... {AuthorizedCDFPrefix, Comments, Conta...
```

## <a name="installing-applications"></a>Instalação de aplicativos

Pode utilizar o **Win32_Product** classe para instalar pacotes de instalador do Windows, localmente ou remotamente.

> [!NOTE]
> No Windows Vista, Windows Server 2008 e versões posteriores do Windows, para instalar uma aplicação, tem de iniciar Windows PowerShell com a opção "Executar como administrador".

Ao instalar remotamente, utilize um caminho de rede de convenção de Nomenclatura Universal (UNC) para especificar o caminho para o pacote. msi, uma vez que o subsistema WMI não compreende caminhos do Windows PowerShell. Por exemplo instalar o pacote de NewPackage.msi localizados na partilha de rede \\ \\AppServ\\dsp no computador remoto PC01, escreva o seguinte comando na linha de comandos do Windows PowerShell:

```powershell
(Get-WMIObject -ComputerName PC01 -List | Where-Object -FilterScript {$_.Name -eq 'Win32_Product'}).Install(\\AppSrv\dsp\NewPackage.msi)
```

Aplicativos que não utilizam a tecnologia Windows Installer podem ter métodos específicos de aplicações disponíveis para implementação automatizada. Para determinar se existe um método para a automatização de implementação, consulte a documentação para o aplicativo ou consulte o sistema de suporte do fornecedor do aplicativo. Em alguns casos, mesmo que o fornecedor do aplicativo não ter um design do aplicativo para a automatização da instalação, o fabricante de software do instalador pode ter algumas técnicas de automação.

## <a name="removing-applications"></a>Remoção de aplicativos

Remover um pacote do Windows Installer com o Windows PowerShell funciona em aproximadamente da mesma forma que a instalação de um pacote. Eis um exemplo que seleciona o pacote para desinstalar com base no respetivo nome; em alguns casos poderá ser mais fácil de filtrar com o **IdentifyingNumber**:

```powershell
(Get-WmiObject -Class Win32_Product -Filter "Name='ILMerge'" -ComputerName . ).Uninstall()
```

Remoção de outras aplicações não é tão simples, mesmo quando feito localmente. Que podemos encontrar as cadeias de caracteres de desinstalação de linha de comandos para estas aplicações ao extrair os **UninstallString** propriedade. Este método funciona para aplicações do Windows Installer e para programas mais antigos que aparece sob a chave de desinstalação:

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Pode filtrar a saída com o nome a apresentar, se assim o desejar:

```powershell
Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

No entanto, essas cadeias de caracteres não podem ser diretamente utilizáveis no prompt do Windows PowerShell sem algumas modificações.

## <a name="upgrading-windows-installer-applications"></a>Atualizando aplicativos do Windows Installer

Para atualizar uma aplicação, terá de saber o nome da aplicação e o caminho para o pacote de atualização de aplicação. Com essas informações, pode atualizar uma aplicação com um único comando do Windows PowerShell:

```powershell
(Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='OldAppName'").Upgrade(\\AppSrv\dsp\OldAppUpgrade.msi)
```