---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Criar objetos .NET e COM novo objeto
ms.assetid: 2057b113-efeb-465e-8b44-da2f20dbf603
ms.openlocfilehash: 1ffd8d4afa419ec0c24321e44aa4a2f41a9bee44
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684130"
---
# <a name="creating-net-and-com-objects-new-object"></a>Criar objetos .NET e COM (New-Object)

Existem componentes de software com o .NET Framework e COM interfaces que permitem-lhe realizar muitas tarefas de administração do sistema. Windows PowerShell permite-lhe utilizar estes componentes, para que não está limitado às tarefas que podem ser executadas utilizando os cmdlets. Muitos dos cmdlets na versão inicial do Windows PowerShell não funcionam em computadores remotos. Nós demonstraremos como contornar esta limitação ao gerir os registos de eventos utilizando o .NET Framework **Eventlog** classe diretamente a partir do Windows PowerShell.

### <a name="using-new-object-for-event-log-access"></a>Utilizando o novo objeto para acesso de registo de eventos

A biblioteca de classes do .NET Framework inclui uma classe chamada **Eventlog** que pode ser utilizado para gerir registos de eventos. Pode criar uma nova instância de uma classe do .NET Framework com o **New-Object** cmdlet com o **TypeName** parâmetro. Por exemplo, o comando seguinte cria uma referência de registo de eventos:

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

Embora o comando criou uma instância da classe de registo de eventos, a instância não inclui quaisquer dados. Isso ocorre porque, não especificamos um determinado registo de eventos. Como obtém um registo de eventos real?

#### <a name="using-constructors-with-new-object"></a>Usando construtores com New-Object

Para fazer referência a um registo de eventos específico, tem de especificar o nome do registo. **New-Object** tem uma **ArgumentList** parâmetro. Os argumentos que passar como valores para este parâmetro são utilizados por um método de inicialização especial do objeto. O método é chamado um *construtor* porque é utilizada para construir o objeto. Por exemplo, para obter uma referência para o registo de aplicação, especifique a cadeia 'Application' como um argumento:

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> Uma vez que a maioria das classes de núcleo do .NET Framework está contida no System namespace, o Windows PowerShell tentará automaticamente localizar classes que especificar no System namespace se não for possível encontrar uma correspondência para o typename que especificar. Isso significa que pode especificar Diagnostics.EventLog em vez de EventLog.

#### <a name="storing-objects-in-variables"></a>Armazenamento de objetos em variáveis

Convém armazenar uma referência a um objeto, para que possa utilizá-lo no shell atual. Embora o Windows PowerShell permite que faça muito trabalho com os pipelines, diminuindo a necessidade de variáveis, por vezes, armazenando referências a objetos em variáveis faz com que seja mais conveniente para manipular esses objetos.

Windows PowerShell lhe permite criar variáveis que são essencialmente objetos nomeadas. A saída de qualquer comando válido do Windows PowerShell pode ser armazenada numa variável. Os nomes de variáveis sempre começam com $. Se quiser armazenar a referência de log do aplicativo numa variável chamada $AppLog, escreva o nome de variável, seguido por um sinal de igual e, em seguida, escreva o comando utilizado para criar o objeto de log do aplicativo:

```
PS> $AppLog = New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application
```

Se, em seguida, escrever $AppLog, pode ver que ele contém o registo de aplicação:

```
PS> $AppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
  16,384      7 OverwriteOlder          2,160 Application
```

#### <a name="accessing-a-remote-event-log-with-new-object"></a>Aceder a um registo de eventos remoto com o novo objeto

Os comandos utilizados na secção anterior de destino no computador local; o **Get-EventLog** cmdlet pode fazer isso. Para aceder ao registo de aplicações num computador remoto, tem de indicar tanto o nome do registo e um nome de computador (ou endereço IP) como argumentos.

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

Agora que temos uma referência a um registo de eventos armazenada na variável $RemoteAppLog, quais as tarefas podem realizar no mesmo?

#### <a name="clearing-an-event-log-with-object-methods"></a>Limpar um registo de eventos com os métodos do objeto

Os objetos têm, muitas vezes, os métodos que podem ser chamados para executar tarefas. Pode usar **Get-Member** para apresentar os métodos associados um objeto. O seguinte comando e a saída selecionada mostram alguns métodos da classe de registo de eventos:

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

O **limpar ()** método pode ser utilizado para limpar o registo de eventos. Ao chamar um método, sempre devem seguir o nome do método por parênteses, mesmo que o método não necessita de argumentos. Isso permite que o PowerShell de Windows distinguir entre o método e uma propriedade potencial com o mesmo nome. Escreva o seguinte para chamar o **clara** método:

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

### <a name="creating-com-objects-with-new-object"></a>Criação de objetos COM o novo objeto
Pode usar **New-Object** para trabalhar com componentes do modelo COM (Component Object). Intervalo de componentes das várias bibliotecas incluídos com o Windows Script Host (WSH) para aplicativos de ActiveX como o Internet Explorer que são instalados na maioria dos sistemas.

**Novo objeto** utiliza Wrappers que pode ser chamado tempo de execução do .NET Framework para criar objetos COM, pelo que tem as mesmas limitações que o .NET Framework faz ao chamar objetos COM. Para criar um objeto COM, tem de especificar o **ComObject** parâmetro com o identificador de programação ou *ProgId* da classe COM que pretende utilizar. Uma discussão completa sobre as limitações de utilização de COM e determinar quais ProgIds estão disponíveis num sistema está além do escopo guia deste utilizador, mas objetos conhecidos dos ambientes, tais como o WSH podem ser utilizados dentro do Windows PowerShell.

Pode criar os objetos WSH ao especificar essas progids: **WScript. Shell**, **WScript**, **Scripting.Dictionary**, e **FileSystemObject**. Os comandos seguintes criam esses objetos:

```powershell
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

Embora a maior parte da funcionalidade dessas classes é disponibilizada de outras formas no Windows PowerShell, algumas tarefas, tais como a criação do atalho são ainda mais fácil fazer usando as classes do WSH.

### <a name="creating-a-desktop-shortcut-with-wscriptshell"></a>Criar um atalho de Desktop com Wscript. Shell

Uma tarefa que pode ser realizada rapidamente com um objeto COM é a criação de um atalho. Suponha que desejar criar um atalho no ambiente de trabalho que liga na pasta raiz para o Windows PowerShell. Tem primeiro de criar uma referência a **Wscript. Shell**, que armazenamos numa variável chamada **$WshShell**:

```powershell
$WshShell = New-Object -ComObject WScript.Shell
```

Get-Member funciona com objetos COM, para que possa explorar os membros do objeto ao escrever:

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

**Get-Member** tem opcional **InputObject** parâmetro, pode utilizar em vez de piping fornecer entradas **Get-Member**. Obtém a mesma saída conforme mostrado acima, se tiver utilizado, em vez disso, o comando **Get-Member - InputObject $WshShell**. Se usar **InputObject**, ele trata o respetivo argumento como um único item. Isso significa que, se tiver vários objetos numa variável **Get-Member** trata-los como uma matriz de objetos. Por exemplo:

```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

O **Wscript. Shell CreateShortcut** método aceita um único argumento, o caminho para o ficheiro de atalho para criar. Podemos poderia digitar o caminho completo para a área de trabalho, mas há uma maneira mais fácil. A área de trabalho normalmente é representada por uma pasta denominada área de trabalho dentro da pasta raiz do utilizador atual. Windows PowerShell tem uma variável **$Home** que contém o caminho para esta pasta. Podemos especificar o caminho para a pasta raiz ao utilizar esta variável e, em seguida, adicione o nome da pasta ambiente de trabalho e o nome para o atalho criar digitando:

```powershell
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

Quando usar algo como um nome de variável dentro de aspas duplas, o Windows PowerShell tenta substituir um valor correspondente. Se usar aspas único, o Windows PowerShell não tentando substitua o valor da variável. Por exemplo, experimente escrever os seguintes comandos:

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

Agora, temos uma variável chamada **$lnk** que contém uma nova referência de atalho. Se quiser ver seus membros, pode encaminhá-la para **Get-Member**. O resultado abaixo mostra os membros, precisamos usar para concluir a criação de nosso atalho:

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

Precisamos especificar os **TargetPath**, que é a pasta de aplicativos para o Windows PowerShell e, em seguida, guarde o atalho **$lnk** chamando o **guardar** método. O caminho de pasta de aplicação do Windows PowerShell é armazenado na variável **$PSHome**, pelo que podemos fazer isso digitando:

```powershell
$lnk.TargetPath = $PSHome
$lnk.Save()
```

### <a name="using-internet-explorer-from-windows-powershell"></a>Usando o Internet Explorer do Windows PowerShell

Muitos aplicativos (incluindo a família do Microsoft Office de aplicativos e o Internet Explorer) podem ser automatizados usando COM. Internet Explorer ilustra alguns dos problemas envolvidos ao trabalhar com aplicativos baseados em e técnicas comuns.

Criar uma instância do Internet Explorer, especificando o Internet Explorer ProgId, **InternetExplorer. Application**:

```powershell
$ie = New-Object -ComObject InternetExplorer.Application
```

Este comando inicia o Internet Explorer, mas não a tornar visível. Se digitar Get-Process, pode ver que um processo denominado iexplore está em execução. Na verdade, se sair do Windows PowerShell, o processo irá continuar a executar. Tem de reiniciar o computador ou usar uma ferramenta como o Gerenciador de tarefas para terminar o processo de iexplore.

> [!NOTE]
> Objetos COM que inicie o como processos separados, geralmente designada *ActiveX executáveis*; pode ou não pode exibir uma janela de interface do usuário durante o arranque. Se criar uma janela mas não a tornar visível, como o Internet Explorer, o foco em geral será movido para a área de trabalho do Windows e deve fazer a janela visíveis para interagir com ele.

Ao escrever **$ie | Get-Member**, pode ver as propriedades e métodos para o Internet Explorer. Para ver a janela do Internet Explorer, defina a propriedade Visible como $true digitando:

```powershell
$ie.Visible = $true
```

Em seguida, pode navegar para um endereço específico da Web usando o método Navigate:

```powershell
$ie.Navigate("http://www.microsoft.com/technet/scriptcenter/default.mspx")
```

Com outros membros do modelo de objeto do Internet Explorer, é possível obter o conteúdo de texto da página da Web. O comando seguinte irá apresentar o texto HTML no corpo da página da Web atual:

```powershell
$ie.Document.Body.InnerText
```

Para fechar o Internet Explorer a partir do PowerShell, chame seu método Quit():

```powershell
$ie.Quit()
```

Isso obrigará a fechar. A variável $ie já não contém uma referência válida, apesar de ainda parece ser um objeto COM. Se tentar usá-lo, obterá um erro de automatização:

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

Pode remover o restante de referência com um comando como $ie = $null ou remover completamente a variável digitando:

```powershell
Remove-Variable ie
```

> [!NOTE]
> Não existe nenhuma padrão comum para se executáveis de ActiveX saiam ou continuam a executar quando remove uma referência a um. Dependendo das circunstâncias, como se a aplicação tem visível, se um documento editado está em execução no mesmo e até mesmo se Windows PowerShell ainda está em execução, a aplicação pode ou não pode sair. Por esse motivo, deve testar o comportamento de terminação para cada ActiveX executável que pretende utilizar no Windows PowerShell.

### <a name="getting-warnings-about-net-framework-wrapped-com-objects"></a>Avisos sobre os objetos do .NET Framework-encapsuladas COM a obter

Em alguns casos, um objeto COM pode ter um associados do .NET Framework *Runtime Callable Wrapper* ou RCW e esta vai ser utilizado por **New-Object**. Uma vez que o comportamento do RCW pode ser diferente do comportamento do objeto COM normal **New-Object** tem uma **Strict** parâmetro para o avisar sobre o acesso RCW. Se especificar a **Strict** parâmetro e, em seguida, criar um objeto COM que utiliza um RCW, receberá uma mensagem de aviso:

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

Embora o objeto ainda está a ser criado, é avisado que não é um objeto COM padrão.