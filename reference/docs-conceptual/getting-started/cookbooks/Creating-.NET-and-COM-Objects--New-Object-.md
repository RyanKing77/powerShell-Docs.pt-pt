---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Criar novo objeto .NET e objetos COM
ms.assetid: 2057b113-efeb-465e-8b44-da2f20dbf603
ms.openlocfilehash: 1ffd8d4afa419ec0c24321e44aa4a2f41a9bee44
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953393"
---
# <a name="creating-net-and-com-objects-new-object"></a>Criação de .NET e objetos COM (novo objeto)

Existem componentes de software com o .NET Framework e COM interfaces que permitem-lhe executar muitas tarefas de administração do sistema. Windows PowerShell permite-lhe utilizar estes componentes, pelo que não está limitado às tarefas que podem ser efetuadas utilizando os cmdlets. Muitos dos cmdlets a edição inicial do Windows PowerShell não funcionam em relação a computadores remotos. Vamos demonstrar como contornar esta limitação ao gerir registos de eventos utilizando o .NET Framework **System.Diagnostics.EventLog** classe diretamente a partir do Windows PowerShell.

### <a name="using-new-object-for-event-log-access"></a>Utilizando o novo objeto para acesso de registo de eventos

A biblioteca de classe do .NET Framework inclui uma classe com o nome **System.Diagnostics.EventLog** que podem ser utilizados para gerir registos de eventos. Pode criar uma nova instância de uma classe de .NET Framework, utilizando o **New-Object** cmdlet com o **TypeName** parâmetro. Por exemplo, o comando seguinte cria uma referência de registo de eventos:

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

Embora o comando criou uma instância da classe de registo de eventos, a instância não inclui quaisquer dados. Isto acontece porque que não especificou um registo de eventos específico. Como a obter um registo de eventos real?

#### <a name="using-constructors-with-new-object"></a>Utilizar construtores com o novo objeto

Para fazer referência a um registo de eventos específico, tem de especificar o nome do registo. **Novo objeto** tem um **ArgumentList** parâmetro. Os argumentos que passar como valores para este parâmetro são utilizados por um método de arranque especial do objeto. O método é chamado um *construtor* porque é utilizado para construir o objeto. Por exemplo, para obter uma referência para o registo de aplicação, especifique a cadeia 'Aplicação' como um argumento:

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> Uma vez que a maioria das classes de núcleo do .NET Framework está contida no espaço de nomes de sistema, do Windows PowerShell irá automaticamente tentar encontrar as classes que especificou no espaço de nomes de sistema, se não é possível encontrar uma correspondência para typename que especificar. Isto significa que pode especificar Diagnostics.EventLog em vez de System.Diagnostics.EventLog.

#### <a name="storing-objects-in-variables"></a>Armazenar objetos em variáveis

Pode querer armazenar uma referência a um objeto, pelo que pode utilizá-lo na shell do atual. Apesar do Windows PowerShell permite-lhe fazer uma grande quantidade de trabalho com pipelines, lessening a necessidade de variáveis, por vezes, armazenar referências a objectos nas variáveis permite mais conveniente manipular esses objetos.

Windows PowerShell permite-lhe criar variáveis que são essencialmente com objetos. O resultado de quaisquer comandos do Windows PowerShell pode ser armazenado numa variável. Os nomes de variáveis começam sempre $. Se pretende armazenar a referência de registo de aplicação numa variável designada $AppLog, escreva o nome da variável, seguido por um sinal de igual e, em seguida, escreva o comando utilizado para criar o objeto de registo de aplicação:

```
PS> $AppLog = New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application
```

Se, em seguida, escrever $AppLog, pode ver que contém o registo de aplicações:

```
PS> $AppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
  16,384      7 OverwriteOlder          2,160 Application
```

#### <a name="accessing-a-remote-event-log-with-new-object"></a>Aceder a um registo de eventos remoto com o novo objeto

Os comandos utilizados na secção anterior do computador local; de destino o **Get-registo de eventos** cmdlet pode fazê-lo. Para aceder ao registo de aplicações num computador remoto, tem de fornecer tanto o nome do registo e um nome de computador (ou endereço IP) como argumentos.

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

Agora que temos uma referência a um registo de eventos armazenado na variável $RemoteAppLog, as tarefas podem, efetuar no mesmo?

#### <a name="clearing-an-event-log-with-object-methods"></a>Limpar um registo de eventos com métodos de objeto

Objetos geralmente têm métodos que podem ser chamados para efetuar tarefas. Pode utilizar **Get-membro** para visualizar os métodos associados a um objeto. O seguinte comando e de saída selecionada mostram alguns métodos da classe de registo de eventos:

```
PS> $RemoteAppLog | Get-Member -MemberType Method

   TypeName: System.Diagnostics.EventLog

Name                      MemberType Definition
----                      ---------- ----------
...
Clear                     Method     System.Void Clear()
Close                     Method     System.Void Close()
...
GetType                   Method     System.Type GetType()
...
ModifyOverflowPolicy      Method     System.Void ModifyOverflowPolicy(Overfl...
RegisterDisplayName       Method     System.Void RegisterDisplayName(String ...
...
ToString                  Method     System.String ToString()
WriteEntry                Method     System.Void WriteEntry(String message),...
WriteEvent                Method     System.Void WriteEvent(EventInstance in...
```

O **limpar** método pode ser utilizado para limpar o registo de eventos. Ao chamar um método, tem sempre de seguir o nome do método por parênteses, mesmo se o método não necessita de argumentos. Esta funcionalidade permite distinguir entre o método e uma propriedade potencial com o mesmo nome do Windows PowerShell. Escreva o seguinte para chamar o **limpar** método:

```
PS> $RemoteAppLog.Clear()
```

Escreva o seguinte para apresentar o registo. Verá que o registo de eventos foi limpo e agora tem 0 entradas em vez de 262:

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

### <a name="creating-com-objects-with-new-object"></a>Criar objectos COM o novo objeto
Pode utilizar **New-Object** para trabalhar com os componentes de modelo de objeto do componente (COM). Intervalo de componentes das bibliotecas vários incluído com Script de anfitrião para WSH (Windows) para aplicações de ActiveX, tais como o Internet Explorer que são instaladas na maioria dos sistemas.

**Novo objeto** utiliza Wrappers possível chamar EndRead Runtime do .NET Framework para criar objetos COM, pelo que tem as mesmas limitações que .NET Framework ao chamar objectos COM. Para criar um objecto COM, tem de especificar o **ComObject** parâmetro com o identificador programático ou *ProgId* da classe COM que pretende utilizar. Ver um debate completado das limitações de utilização de COM e determinar que estão disponíveis num sistema ProgIds está fora do âmbito do Guia do utilizador, mas objetos mais conhecidos dos ambientes, como para WSH podem ser utilizados no Windows PowerShell.

Pode criar os objetos para WSH especificando estes progids: **WScript.Shell**, **WScript.Network**, **Scripting.Dictionary**, e  **Scripting.FileSystemObject**. Os seguintes comandos criam estes objetos:

```powershell
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

Embora a maioria da funcionalidade destas classes é disponibilizado de outras formas no Windows PowerShell, algumas tarefas, tais como a criação do atalho estão ainda mais fácil utilizando as classes para WSH.

### <a name="creating-a-desktop-shortcut-with-wscriptshell"></a>Criar um atalho do ambiente de trabalho com WScript.Shell

Uma tarefa que pode ser executada rapidamente com um objecto COM está a criar um atalho. Suponha que pretende criar um atalho no ambiente de trabalho que as ligações para a pasta raiz para o Windows PowerShell. Terá primeiro de criar uma referência a **WScript.Shell**, que iremos armazenará numa variável designada **$WshShell**:

```powershell
$WshShell = New-Object -ComObject WScript.Shell
```

Get-membro funciona com objetos COM, pelo que pode explorar os membros de objeto, escrevendo:

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

**Get-membro** tem opcional **InputObject** parâmetro pode utilizar em vez de piping para fornecer dados para **Get-membro**. Teria de obter a mesma, conforme mostrado acima, se tiver utilizado, em vez disso, o comando de saída **membro Get - InputObject $WshShell**. Se utilizar **InputObject**, processa o respetivo argumento como um único item. Isto significa que, se tiver vários objetos numa variável, **Get-membro** trata-los como uma matriz de objetos. Por exemplo:

```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

O **WScript.Shell CreateShortcut** método aceita um argumento único, o caminho para o ficheiro de atalho para o criar. Iremos foi escreva o caminho completo para o ambiente de trabalho, mas não existe uma forma mais fácil. Ambiente de trabalho é normalmente representado por uma pasta com o nome de ambiente de trabalho para a pasta raiz do utilizador atual. Windows PowerShell tem uma variável **$Home** que contém o caminho para esta pasta. Iremos pode especificar o caminho para a pasta de raiz utilizando esta variável e, em seguida, adicione o nome da pasta de ambiente de trabalho e o nome para o atalho criar, escrevendo:

```powershell
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

Quando utilizar algo semelhante um nome de variável no interior de aspas duplas, tenta do Windows PowerShell substituir um valor correspondente. Se utilizar único aspas, do Windows PowerShell não tenta substituir o valor da variável. Por exemplo, experimente escrever os seguintes comandos:

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

Agora, temos uma variável com o nome **$lnk** que contém uma referência de atalho de novo. Se pretender ver os seus membros, pode encaminhar para **Get-membro**. O resultado abaixo mostra os membros que é necessário utilizar para concluir a criação da nossa atalho:

```
PS> $lnk | Get-Member
TypeName: System.__ComObject#{f935dc23-1cf0-11d0-adb9-00c04fd58a0b}
Name             MemberType   Definition
----             ----------   ----------
...
Save             Method       void Save ()
...
TargetPath       Property     string TargetPath () {get} {set}
```

É necessário especificar o **TargetPath**, que é a pasta de aplicação para o Windows PowerShell e, em seguida, guarde o atalho **$lnk** ao chamar o **guardar** método. O caminho de pasta de aplicação do Windows PowerShell é armazenado na variável **$PSHome**, por isso, podemos fazer isto, escrevendo:

```powershell
$lnk.TargetPath = $PSHome
$lnk.Save()
```

### <a name="using-internet-explorer-from-windows-powershell"></a>Utilizar o Internet Explorer a partir do Windows PowerShell

Muitas aplicações (incluindo a família do Microsoft Office de aplicações e do Internet Explorer) podem ser automatizadas utilizando COM. Internet Explorer ilustra alguns dos problemas ao trabalhar com aplicações baseadas em COM e técnicas comuns.

Criar uma instância do Internet Explorer, especificando o Internet Explorer ProgId **InternetExplorer.Application**:

```powershell
$ie = New-Object -ComObject InternetExplorer.Application
```

Este comando inicia o Internet Explorer, mas não torná-lo visível. Se escrever Get-Process, pode ver que um processo denominado iexplore está em execução. Na verdade, se sair do Windows PowerShell, o processo irá continuar a executar. Tem de reiniciar o computador ou utilize uma ferramenta como o Gestor de tarefas para terminar o processo de iexplore.

> [!NOTE]
> Os objetos COM que começam como processos separados, geralmente designada por *ActiveX executáveis*, poderá ou poderá não apresentar uma janela de interface de utilizador quando são iniciados. Se estes criar uma janela, mas não torná-lo visível, como o Internet Explorer, o foco, geralmente, irá mudar para o ambiente de trabalho do Windows e tem de se a janela visíveis para interagir com ele.

Escrevendo **$ie | Get-membro**, pode ver as propriedades e métodos para o Internet Explorer. Para ver a janela do Internet Explorer, defina a propriedade Visible para $true, escrevendo:

```powershell
$ie.Visible = $true
```

Em seguida, pode navegar para um endereço de Web específico utilizando o método de navegar:

```powershell
$ie.Navigate("http://www.microsoft.com/technet/scriptcenter/default.mspx")
```

Utilizar outros membros do modelo de objecto do Internet Explorer, é possível obter o conteúdo de texto da página Web. O comando seguinte irá apresentar o texto HTML no corpo da página Web atual:

```powershell
$ie.Document.Body.InnerText
```

Para fechar o Internet Explorer a partir do PowerShell, chame o respetivo método Quit():

```powershell
$ie.Quit()
```

Isto irá forçar a fechar. $Ie variável já não contém uma referência válida, apesar de ainda aparenta ser um objecto COM. Se tentar utilizá-lo, obterá um erro de automatização:

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

Pode remover o restante referenciar com um comando como $ie = $null ou remover por completo a variável escrevendo:

```powershell
Remove-Variable ie
```

> [!NOTE]
> Não há nenhuma padrão comum para se ActiveX executáveis sair ou continuam a executar quando remover uma referência a um. Dependendo das circunstâncias, como se a aplicação está visível, se um documento editado está em execução no mesmo e, mesmo se do Windows PowerShell ainda está em execução, a aplicação pode ou não pode sair. Por este motivo, deve testar o comportamento de terminação para cada ActiveX executável que pretende utilizar no Windows PowerShell.

### <a name="getting-warnings-about-net-framework-wrapped-com-objects"></a>Obter avisos sobre objetos do .NET Framework moldadas COM

Em alguns casos, um objeto COM pode ter um .NET Framework associado *Wrapper possível chamar EndRead Runtime* ou RCW e esta será utilizada pelo **New-Object**. Uma vez que o comportamento do RCW pode ser diferente do comportamento do objeto COM normal, **New-Object** tem um **Strict** parâmetro para o avisar sobre o acesso RCW. Se especificar o **Strict** parâmetro e, em seguida, criar um objecto COM que utiliza um RCW, receberá uma mensagem de aviso:

```
PS> $xl = New-Object -ComObject Excel.Application -Strict
New-Object : The object written to the pipeline is an instance of the type "Mic
rosoft.Office.Interop.Excel.ApplicationClass" from the component's primary inte
rop assembly. If this type exposes different members than the IDispatch members
, scripts written to work with this object might not work if the primary intero
p assembly is not installed.
At line:1 char:17
+ $xl = New-Object  <<<< -ComObject Excel.Application -Strict
```

Apesar do objeto ainda está a ser criado, são avisado que não se trata de um objecto COM padrão.