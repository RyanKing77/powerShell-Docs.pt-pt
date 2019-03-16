---
title: Instalar um módulo do PowerShell | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb82827e-fdb7-4cbf-b3d4-093e72b3ff0e
caps.latest.revision: 28
ms.openlocfilehash: 7c2bfca50de4645676eafc01bbf23d9797e8b758
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059784"
---
# <a name="installing-a-powershell-module"></a>Installing a PowerShell Module (Instalar um Módulo do PowerShell)

Depois de criar o módulo do PowerShell, provavelmente desejará instalar o módulo num sistema, para que ou outros poderão utilizá-lo. Em termos gerais, isso simplesmente consiste em copiar os módulo arquivos (ie, psm1, ou a assemblagem binária, o manifesto de módulo e todos os outros ficheiros associados) num diretório nesse computador. Para um projeto muito pequeno, isso pode ser tão simples quanto copiar e colar os ficheiros com o Explorador do Windows num único computador remoto; No entanto, para soluções maiores poderá querer utilizar um processo de instalação mais sofisticado. Independentemente de como obter o seu módulo no sistema, o PowerShell pode usar várias técnicas que permitirá que os usuários a encontrar e utilizar os módulos. (Para obter mais informações, consulte [importar um módulo do PowerShell](./importing-a-powershell-module.md).) Por conseguinte, o problema principal para a instalação é garantir que o PowerShell poderá encontrar seu módulo.

Este tópico contém as seguintes secções:

- Regras para a instalação de módulos

- Onde instalar os módulos

- Instalação de várias versões de um módulo

- Manipulação de conflitos de nomes de comando

## <a name="rules-for-installing-modules"></a>Regras para a instalação de módulos

As seguintes informações pertence a todos os módulos, incluindo módulos que criar para o seu próprio uso, módulos que obtém a partir de outras entidades e módulos que distribui a outras pessoas.

### <a name="install-modules-in-psmodulepath"></a>Instalar os módulos no PSModulePath

Sempre que possível, instale todos os módulos num caminho que está listado na **PSModulePath** variável de ambiente ou adicionar o caminho do módulo para o **PSModulePath** valor da variável de ambiente.

O **PSModulePath** variável de ambiente ($Env: PSModulePath) contém os locais dos módulos do Windows PowerShell. Cmdlets baseiam-se no valor desta variável de ambiente para localizar os módulos.

Por predefinição, o **PSModulePath** valor da variável de ambiente contém o sistema seguinte e os diretórios de módulo de usuário, mas pode adicionar e editar o valor.

- $PSHome\Modules (% Windir%\System32\WindowsPowerShell\v1.0\Modules)

  > [!WARNING]
  > Esta localização é reservada para módulos que acompanham o Windows. Não instale módulos para esta localização.

- $Home\Documents\WindowsPowerShell\Modules (%UserProfile%\Documents\WindowsPowerShell\Modules)

- $Env: ProgramFiles\WindowsPowerShell\Modules (% ProgramFiles%\WindowsPowerShell\Modules)

  Para obter o valor do **PSModulePath** variável de ambiente, utilizar qualquer um dos seguintes comandos.

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  Para adicionar um caminho de módulo ao valor do **PSModulePath** variável de ambiente de valor, utilize o seguinte formato de comando. Este formato utiliza o **SetEnvironmentVariable** método da **System.Environment** classe fazer uma alteração de sessão independente para o **PSModulePath** ambiente variável.

  ```powershell

  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > Depois de adicionar o caminho para **PSModulePath**, deve difundir uma mensagem de ambiente sobre a alteração. A alteração a difundir permite que os outros aplicativos, como o shell, captará a alteração. Para a alteração de difusão, ter seu código de instalação do produto enviar um **WM_SETTINGCHANGE** mensagem com `lParam` definido como a cadeia de caracteres "Ambiente". Certifique-se de que enviar a mensagem depois do seu código de instalação do módulo atualizou **PSModulePath**.

### <a name="use-the-correct-module-directory-name"></a>Utilize o nome de diretório de módulo correto

Um módulo "bem formado" é um módulo que esteja armazenado num diretório com o mesmo nome que o nome de base pelo menos um ficheiro no diretório de módulo. Se um módulo não está formado, Windows PowerShell não o reconhece como um módulo.

O "nome de base" de um ficheiro é o nome sem a extensão de nome de ficheiro. Num módulo bem formado, o nome do diretório que contém os ficheiros de módulo tem de corresponder ao nome de base pelo menos um ficheiro no módulo.

Por exemplo, o módulo da Fabrikam de exemplo, o diretório que contém os ficheiros de módulo com o nome "Fabrikam" e pelo menos um ficheiro com o nome de base de "Fabrikam". Neste caso, Fabrikam.psd1 e Fabrikam.dll tem o nome de base "Fabrikam".

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a>Efeito da instalação incorreta

Se o módulo não está bem formado e a localização não está incluída no valor dos **PSModulePath** variável de ambiente, funcionalidades de deteção básica do Windows PowerShell, como a seguir, não funcionam.

- A funcionalidade de carregamento de módulo automática não é possível importar o módulo automaticamente.

- O `ListAvailable` parâmetro do [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet não é possível localizar o módulo.

- O [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet não é possível localizar o módulo. Para importar o módulo, tem de fornecer o caminho completo para o ficheiro do módulo de raiz ou o ficheiro de manifesto de módulo.

  Recursos adicionais, como o seguinte, não funcionam, a menos que o módulo é importado para a sessão. Em módulos bem formados no **PSModulePath** variável de ambiente, esses recursos funcionam, mesmo quando o módulo não é importado para a sessão.

- O [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet não consegue encontrar os comandos no módulo.

- O [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets não é possível atualizar ou guardar ajuda para o módulo.

- O [comando Show](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet não é possível localizar e apresentar os comandos no módulo.

  Os comandos no módulo estão em falta o `Show-Command` janela no Windows PowerShell Integrated Scripting Environment (ISE).

## <a name="where-to-install-modules"></a>Onde instalar os módulos

Esta secção explica onde no sistema de ficheiros para instalar os módulos do Windows PowerShell. O local depende de como o módulo é utilizado.

### <a name="installing-modules-for-a-specific-user"></a>Instalar módulos para um utilizador específico

Se criar seu próprio módulo ou obter um módulo de terceiros, como um site da Comunidade do Windows PowerShell, e pretender que o módulo esteja disponível para a sua conta de utilizador apenas, instale o módulo no seu diretório de módulos específicos do usuário.

```
$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

O diretório de módulos específicos do usuário é adicionado ao valor do **PSModulePath** variável de ambiente, por predefinição.

### <a name="installing-modules-for-all-users-in-program-files"></a>Instalar módulos para todos os utilizadores em arquivos de programas

Se pretender que um módulo para estar disponível para todas as contas de utilizador no computador, instale o módulo na localização de ficheiros de programa.

```
$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

> [!NOTE]
> A localização de arquivos de programas é adicionada ao valor da variável de ambiente PSModulePath por predefinição no Windows PowerShell 4.0 e posterior. Para versões anteriores do Windows PowerShell, pode criar os arquivos de programas localização ((%ProgramFiles%\WindowsPowerShell\Modules) e adicionar este caminho à sua variável de ambiente de PSModulePath, conforme descrito acima manualmente.

### <a name="installing-modules-in-a-product-directory"></a>Instalar módulos num diretório de produtos

Se está a distribuir o módulo a outras partes, utilize a localização de arquivos de programas padrão descrita acima, ou criar seu próprio subdiretório específico da empresa ou específicos de produtos do diretório % ProgramFiles %.

Por exemplo, Fabrikam tecnologias, uma empresa fictícia, está a ser enviado um módulo do Windows PowerShell para o seu produto Fabrikam Manager. O instalador do módulo cria um subdiretório de módulos no subdiretório de produto do Gestor da Fabrikam.

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

Para ativar as funcionalidades de deteção de módulo do Windows PowerShell localizar o módulo da Fabrikam, o instalador do módulo de Fabrikam adiciona a localização do módulo para o valor do **PSModulePath** variável de ambiente.

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += "C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a>Instalar módulos no diretório de ficheiros comuns

Se um módulo é utilizado por vários componentes de um produto ou por várias versões de um produto, instale o módulo num subdiretório específicos de módulo de subdiretório de Files\Modules %ProgramFiles%\Common.

No exemplo a seguir, o módulo de Fabrikam é instalado num subdiretório de subdiretório de Files\Modules %ProgramFiles%\Common Fabrikam. Tenha em atenção que cada módulo reside no seu próprio subdiretório no subdiretório módulos.

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)

```

Em seguida, o instalador assegura o valor do **PSModulePath** variável de ambiente inclui o caminho do subdiretório de módulos de ficheiros comuns.

```powershell
$m = $env:ProgramFiles + '\Common Files\Modules'
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$q = $p -split ';'
if ($q -notContains $m) {
    $q += ";$m"
}
$p = $q -join ';'
[Environment]::SetEnvironmentVariable("PSModulePath", $p)
```

## <a name="installing-multiple-versions-of-a-module"></a>Instalação de várias versões de um módulo

Para instalar várias versões do mesmo módulo, utilize o procedimento seguinte.

1. Crie um diretório para cada versão do módulo. Inclua o número de versão no nome do diretório.

2. Crie um manifesto de módulo para cada versão do módulo. O valor do **ModuleVersion** da chave no manifesto, introduza o número de versão do módulo. Guarde o ficheiro de manifesto (. psd1) no diretório específico da versão para o módulo.

3. Adicionar o caminho de pasta de raiz do módulo para o valor do **PSModulePath** variável de ambiente, conforme mostrado nos exemplos a seguir.

Para importar uma versão específica do módulo, o utilizador final pode utilizar o `MinimumVersion` ou `RequiredVersion` parâmetros do [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.

Por exemplo, se o módulo de Fabrikam está disponível nas versões 8.0 e 9.0, a estrutura de diretório de módulo Fabrikam poderá assemelhar-se ao seguinte.

 ```
C:\Program Files
Fabrikam Manager
  Fabrikam8
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "8.0")
      Fabrikam.dll (module assembly)
  Fabrikam9
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "9.0")
      Fabrikam.dll (module assembly)
```

O instalador adiciona ambos os caminhos dos módulos para o **PSModulePath** valor da variável de ambiente.

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

Quando estes passos estiverem concluídos, o **ListAvailable** parâmetro do [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet obtém ambos os módulos da Fabrikam. Para importar um módulo específico, utilize o `MinimumVersion` ou `RequiredVersion` parâmetros do [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.

Se ambos os módulos são importados para a mesma sessão, e os módulos contêm cmdlets com os mesmos nomes, os cmdlets que são importados pela última vez são eficazes na sessão.

## <a name="handling-command-name-conflicts"></a>Manipulação de conflitos de nomes de comando

Quando os comandos que exporta um módulo de tem o mesmo nome como comandos numa sessão do utilizador, podem ocorrer conflitos de nome do comando.

Quando uma sessão contém dois comandos que têm o mesmo nome, o Windows PowerShell é executado com o tipo de comando que tem precedência. Quando uma sessão contém dois comandos que têm o mesmo nome e o mesmo tipo, o Windows PowerShell executa o comando que foi adicionado à sessão mais recentemente. Para executar um comando que não é executado por predefinição, os utilizadores podem qualificar o nome do comando com o nome do módulo.

Por exemplo, se a sessão contém um `Get-Date` função e o `Get-Date` cmdlet, o Windows PowerShell executa a função, por predefinição. Para executar o cmdlet, precede o comando com o nome do módulo, tal como:

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

Para evitar conflitos de nomes, os autores de módulo podem utilizar o **DefaultCommandPrefix** exportar chave no manifesto do módulo para especificar um prefixo do nome para todos os comandos do módulo.

Os utilizadores podem utilizar o **prefixo** parâmetro do `Import-Module` cmdlet para utilizar um prefixo de alternativo. O valor do **prefixo** parâmetro terão precedência sobre o valor da **DefaultCommandPrefix** chave.

## <a name="see-also"></a>Veja Também

[about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[Escrever um módulo do Windows PowerShell](./writing-a-windows-powershell-module.md)
