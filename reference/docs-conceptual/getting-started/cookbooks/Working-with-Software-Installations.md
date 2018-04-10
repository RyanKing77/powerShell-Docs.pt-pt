---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Trabalhar com Instalações de Software
ms.assetid: 51a12fe9-95f6-4ffc-81a5-4fa72a5bada9
ms.openlocfilehash: bb97ad37c4295351c0fc2e3c6e1209c8dd673f06
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="working-with-software-installations"></a>Trabalhar com Instalações de Software

As aplicações que foram concebidas para utilizar o Windows Installer podem ser acedidas através do WMI **Win32_Product** classe, mas nem todas as aplicações em utilização atualmente utilizam o Windows Installer. Porque o Windows Installer fornece o intervalo ser técnicas padrão para trabalhar com aplicações instaláveis, iremos irá focar-se principalmente nessas aplicações. As aplicações que utilizam rotinas de configuração alternativa, geralmente, não serão geridas pelo Windows Installer. Técnicas específicas para trabalhar com essas aplicações dependerá os instalador de software e as decisões tomadas pelo programador da aplicação.

> [!NOTE]
> As aplicações que são instaladas por copiar os ficheiros de aplicação para o computador, normalmente, não podem ser geridas utilizando técnicas de abordados aqui. Pode gerir estas aplicações, como ficheiros e pastas utilizando as técnicas abordadas na secção "Trabalhar com ficheiros e pastas".

### <a name="listing-windows-installer-applications"></a>Lista de aplicações do Windows Installer

Para listar as aplicações instaladas com o Windows Installer num sistema local ou remoto, utilize a seguinte consulta WMI simple:

```
PS> Get-WmiObject -Class Win32_Product -ComputerName .

IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
Name              : Microsoft .NET Framework 2.0
Vendor            : Microsoft Corporation
Version           : 2.0.50727
Caption           : Microsoft .NET Framework 2.0
```

Para apresentar todas as propriedades do objeto Win32_Product para a apresentação, utilize o parâmetro de propriedades dos cmdlets de formatação, por exemplo, o cmdlet de formato-lista, com um valor de \* (todos).

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

Em alternativa, pode utilizar o **Get-WmiObject filtro** parâmetro para selecionar apenas o Microsoft .NET Framework 2.0. Como o filtro utilizado neste comando é um filtro WMI, utiliza sintaxe de linguagem WQL (WMI Query), não a sintaxe do Windows PowerShell. Em vez disso:

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='Microsoft .NET Framework 2.0'"| Format-List -Property *
```

Tenha em atenção que os consultas WQL com frequência, carateres de utilização, tais como espaços nem igual inicia, que têm um significado especial no Windows PowerShell. Por este motivo, é recomendada uma investigação sempre coloque o valor do parâmetro filtro aspas. Também pode utilizar o caráter de escape do Windows PowerShell, uma backtick (\`), apesar de não-lo pode melhorar a legibilidade. O seguinte comando é equivalente ao comando anterior e devolve os mesmos resultados, mas utiliza o backtick para o escape carateres especiais, em vez de colocar entre aspas a cadeia de filtro de todo.

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter Name`=`'Microsoft` .NET` Framework` 2.0`' | Format-List -Property *
```

Para listar apenas as propriedades que lhe interessarem, utilize o parâmetro de propriedade de formatação cmdlets para listar as propriedades pretendidas.

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

Por fim localizar apenas os nomes das aplicações instaladas, simples **em todo o formato** simplifica a declaração de saída:

```powershell
Get-WmiObject -Class Win32_Product -ComputerName .  | Format-Wide -Column 1
```

Embora temos, agora, várias formas para ver as aplicações que utilizar o Windows Installer para a instalação, não podemos ter considerados outras aplicações. Porque as aplicações mais padrão registar o seu programa de desinstalação com o Windows, iremos pode trabalhar com os localmente ao localizá-los no registo do Windows.

### <a name="listing-all-uninstallable-applications"></a>Listar todas as aplicações Uninstallable

Apesar de não é possível garantida para localizar todas as aplicações num sistema, é possível localizar todos os programas com listagens apresentadas na caixa de diálogo Adicionar ou remover programas. Adicionar ou remover programas localiza estas aplicações na chave de registo seguinte:

**HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall**.

Também iremos pode examinar esta chave para encontrar aplicações. Para tornar mais fácil ver a chave de desinstalação, iremos pode mapear uma unidade do Windows PowerShell para esta localização de registo:

```
PS> New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

> [!NOTE]
> O **HKLM:** unidade está mapeada para a raiz do **HKEY_LOCAL_MACHINE**, pelo que a unidade é utilizado no caminho para a chave de desinstalação. Em vez de **HKLM:** foi especificámos o caminho do registo utilizando **HKLM** ou **HKEY_LOCAL_MACHINE**. A vantagem de utilizar uma unidade de registo existente é que podemos utilizar conclusão de separador para preencher os nomes de chaves, pelo que não temos escrevê-las.

Temos, agora, uma unidade com o nome "Desinstalar", que pode ser utilizado de forma rápida e convenientemente serve para instalações da aplicação. Iremos pode encontrar o número de aplicações instaladas, o número de chaves de registo na desinstalação de contagem: unidade do Windows PowerShell:

```
PS> (Get-ChildItem -Path Uninstall:).Count
459
```

Iremos pode procurar esta lista de aplicações mais utilizando uma variedade de técnicas, começando com **Get-ChildItem**. Para obter uma lista de aplicações e guardá-las no **$UninstallableApplications** variável, utilize o seguinte comando:

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

> [!NOTE]
> Estamos a utilizar um demorado nome da variável aqui para efeitos de clareza. Em utilização real, não há nenhuma razão para utilizar nomes de comprimento. Apesar de poder utilizar conclusão de separador para nomes de variáveis, também pode utilizar nomes de caráter de 1-2 de velocidade. Os nomes de tempo e descritivos são mais úteis quando estiver a desenvolver o código para reutilização.

Para apresentar os valores das entradas de registo nas chaves de registo em desinstalação, utilize o método GetValue das chaves de registo. O valor do método é o nome da entrada de registo.

Por exemplo, para localizar os nomes a apresentar de aplicações na chave de desinstalação, utilize o seguinte comando:

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

Não há nenhuma garantia de que estes valores são exclusivos. No exemplo seguinte, dois itens instaladas são apresentadas como "Série de 9 codificador de multimédia do Windows":

```
PS> Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion\Uninstall

SKC  VC Name                           Property
---  -- ----                           --------
  0   3 Windows Media Encoder 9        {DisplayName, DisplayIcon, UninstallS...
  0  24 {E38C00D0-A68B-4318-A8A6-F7... {AuthorizedCDFPrefix, Comments, Conta...
```

### <a name="installing-applications"></a>Instalar aplicações

Pode utilizar o **Win32_Product** classe para instalar pacotes do Windows Installer, remota ou localmente.

> [!NOTE]
> No Windows Vista, Windows Server 2008 e versões posteriores do Windows, para instalar uma aplicação, tem de iniciar do Windows PowerShell com a opção "Executar como administrador".

Ao instalar remotamente, utilize um caminho de rede de convenção de Nomenclatura Universal (UNC) para especificar o caminho para o pacote. msi, porque o subsistema WMI não compreende caminhos do Windows PowerShell. Por exemplo instalar o pacote de NewPackage.msi localizados na partilha de rede \\ \\AppServ\\dsp no computador remoto PC01, escreva o seguinte comando na linha de comandos da Windows PowerShell:

```powershell
(Get-WMIObject -ComputerName PC01 -List | Where-Object -FilterScript {$_.Name -eq 'Win32_Product'}).Install(\\AppSrv\dsp\NewPackage.msi)
```

As aplicações que não utilizam a tecnologia do Windows Installer podem ter métodos específicos da aplicação disponíveis para implementação automática. Para determinar se existe um método para a automatização da implementação, consulte a documentação para a aplicação ou consulte o sistema de suporte do fornecedor da aplicação. Em alguns casos, mesmo que o fornecedor da aplicação não foi possível estruturar especificamente a aplicação para a automatização de instalação, o fabricante de software do instalador pode ter alguns técnicas para a automatização.

### <a name="removing-applications"></a>Remover aplicações

Remover um pacote do Windows Installer através do Windows PowerShell funciona em aproximadamente da mesma forma que a instalar um pacote. Eis um exemplo que seleciona o pacote para desinstalar com base no respetivo nome; em alguns casos poderá ser mais fácil de filtro com o **IdentifyingNumber**:

```powershell
(Get-WmiObject -Class Win32_Product -Filter "Name='ILMerge'" -ComputerName . ).Uninstall()
```

Remoção de outras aplicações não é bastante, por isso, simple, mesmo quando efetuada localmente. Pode encontrar as cadeias de desinstalação de linha de comandos para estas aplicações, a extrair o **UninstallString** propriedade. Este método funciona para aplicações do Windows Installer e para programas mais antigos apresentação sob a chave de desinstalação:

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Pode filtrar os resultados pelo nome a apresentar, se assim o desejar:

```powershell
Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

No entanto, estas cadeias não podem ser diretamente utilizáveis da linha de comandos da Windows PowerShell sem alguns modificação.

### <a name="upgrading-windows-installer-applications"></a>Atualizar aplicações do Windows Installer

Para atualizar uma aplicação, terá de saber o nome da aplicação e o caminho para o pacote de atualização da aplicação. Com essa informação, pode atualizar uma aplicação com um único comando do Windows PowerShell:

```powershell
(Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='OldAppName'").Upgrade(\\AppSrv\dsp\OldAppUpgrade.msi)
```