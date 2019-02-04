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
# <a name="creating-net-and-com-objects-new-object"></a><span data-ttu-id="5bbe9-103">Criar objetos .NET e COM (New-Object)</span><span class="sxs-lookup"><span data-stu-id="5bbe9-103">Creating .NET and COM Objects (New-Object)</span></span>

<span data-ttu-id="5bbe9-104">Existem componentes de software com o .NET Framework e COM interfaces que permitem-lhe realizar muitas tarefas de administração do sistema.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-104">There are software components with .NET Framework and COM interfaces that enable you to perform many system administration tasks.</span></span> <span data-ttu-id="5bbe9-105">Windows PowerShell permite-lhe utilizar estes componentes, para que não está limitado às tarefas que podem ser executadas utilizando os cmdlets.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-105">Windows PowerShell lets you use these components, so you are not limited to the tasks that can be performed by using cmdlets.</span></span> <span data-ttu-id="5bbe9-106">Muitos dos cmdlets na versão inicial do Windows PowerShell não funcionam em computadores remotos.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-106">Many of the cmdlets in the initial release of Windows PowerShell do not work against remote computers.</span></span> <span data-ttu-id="5bbe9-107">Nós demonstraremos como contornar esta limitação ao gerir os registos de eventos utilizando o .NET Framework **Eventlog** classe diretamente a partir do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-107">We will demonstrate how to get around this limitation when managing event logs by using the .NET Framework **System.Diagnostics.EventLog** class directly from Windows PowerShell.</span></span>

### <a name="using-new-object-for-event-log-access"></a><span data-ttu-id="5bbe9-108">Utilizando o novo objeto para acesso de registo de eventos</span><span class="sxs-lookup"><span data-stu-id="5bbe9-108">Using New-Object for Event Log Access</span></span>

<span data-ttu-id="5bbe9-109">A biblioteca de classes do .NET Framework inclui uma classe chamada **Eventlog** que pode ser utilizado para gerir registos de eventos.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-109">The .NET Framework Class Library includes a class named **System.Diagnostics.EventLog** that can be used to manage event logs.</span></span> <span data-ttu-id="5bbe9-110">Pode criar uma nova instância de uma classe do .NET Framework com o **New-Object** cmdlet com o **TypeName** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-110">You can create a new instance of a .NET Framework class by using the **New-Object** cmdlet with the **TypeName** parameter.</span></span> <span data-ttu-id="5bbe9-111">Por exemplo, o comando seguinte cria uma referência de registo de eventos:</span><span class="sxs-lookup"><span data-stu-id="5bbe9-111">For example, the following command creates an event log reference:</span></span>

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

<span data-ttu-id="5bbe9-112">Embora o comando criou uma instância da classe de registo de eventos, a instância não inclui quaisquer dados.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-112">Although the command has created an instance of the EventLog class, the instance does not include any data.</span></span> <span data-ttu-id="5bbe9-113">Isso ocorre porque, não especificamos um determinado registo de eventos.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-113">That is because we did not specify a particular event log.</span></span> <span data-ttu-id="5bbe9-114">Como obtém um registo de eventos real?</span><span class="sxs-lookup"><span data-stu-id="5bbe9-114">How do you get a real event log?</span></span>

#### <a name="using-constructors-with-new-object"></a><span data-ttu-id="5bbe9-115">Usando construtores com New-Object</span><span class="sxs-lookup"><span data-stu-id="5bbe9-115">Using Constructors with New-Object</span></span>

<span data-ttu-id="5bbe9-116">Para fazer referência a um registo de eventos específico, tem de especificar o nome do registo.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-116">To refer to a specific event log, you need to specify the name of the log.</span></span> <span data-ttu-id="5bbe9-117">**New-Object** tem uma **ArgumentList** parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-117">**New-Object** has an **ArgumentList** parameter.</span></span> <span data-ttu-id="5bbe9-118">Os argumentos que passar como valores para este parâmetro são utilizados por um método de inicialização especial do objeto.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-118">The arguments you pass as values to this parameter are used by a special startup method of the object.</span></span> <span data-ttu-id="5bbe9-119">O método é chamado um *construtor* porque é utilizada para construir o objeto.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-119">The method is called a *constructor* because it is used to construct the object.</span></span> <span data-ttu-id="5bbe9-120">Por exemplo, para obter uma referência para o registo de aplicação, especifique a cadeia 'Application' como um argumento:</span><span class="sxs-lookup"><span data-stu-id="5bbe9-120">For example, to get a reference to the Application log, you specify the string 'Application' as an argument:</span></span>

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> <span data-ttu-id="5bbe9-121">Uma vez que a maioria das classes de núcleo do .NET Framework está contida no System namespace, o Windows PowerShell tentará automaticamente localizar classes que especificar no System namespace se não for possível encontrar uma correspondência para o typename que especificar.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-121">Since most of the .NET Framework core classes are contained in the System namespace, Windows PowerShell will automatically attempt to find classes you specify in the System namespace if it cannot find a match for the typename you specify.</span></span> <span data-ttu-id="5bbe9-122">Isso significa que pode especificar Diagnostics.EventLog em vez de EventLog.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-122">This means that you can specify Diagnostics.EventLog instead of System.Diagnostics.EventLog.</span></span>

#### <a name="storing-objects-in-variables"></a><span data-ttu-id="5bbe9-123">Armazenamento de objetos em variáveis</span><span class="sxs-lookup"><span data-stu-id="5bbe9-123">Storing Objects in Variables</span></span>

<span data-ttu-id="5bbe9-124">Convém armazenar uma referência a um objeto, para que possa utilizá-lo no shell atual.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-124">You might want to store a reference to an object, so you can use it in the current shell.</span></span> <span data-ttu-id="5bbe9-125">Embora o Windows PowerShell permite que faça muito trabalho com os pipelines, diminuindo a necessidade de variáveis, por vezes, armazenando referências a objetos em variáveis faz com que seja mais conveniente para manipular esses objetos.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-125">Although Windows PowerShell lets you do a lot of work with pipelines, lessening the need for variables, sometimes storing references to objects in variables makes it more convenient to manipulate those objects.</span></span>

<span data-ttu-id="5bbe9-126">Windows PowerShell lhe permite criar variáveis que são essencialmente objetos nomeadas.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-126">Windows PowerShell lets you create variables that are essentially named objects.</span></span> <span data-ttu-id="5bbe9-127">A saída de qualquer comando válido do Windows PowerShell pode ser armazenada numa variável.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-127">The output from any valid Windows PowerShell command can be stored in a variable.</span></span> <span data-ttu-id="5bbe9-128">Os nomes de variáveis sempre começam com $.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-128">Variable names always begin with $.</span></span> <span data-ttu-id="5bbe9-129">Se quiser armazenar a referência de log do aplicativo numa variável chamada $AppLog, escreva o nome de variável, seguido por um sinal de igual e, em seguida, escreva o comando utilizado para criar o objeto de log do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="5bbe9-129">If you want to store the Application log reference in a variable named $AppLog, type the name of the variable, followed by an equal sign and then type the command used to create the Application log object:</span></span>

```
PS> $AppLog = New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application
```

<span data-ttu-id="5bbe9-130">Se, em seguida, escrever $AppLog, pode ver que ele contém o registo de aplicação:</span><span class="sxs-lookup"><span data-stu-id="5bbe9-130">If you then type $AppLog, you can see that it contains the Application log:</span></span>

```
PS> $AppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
  16,384      7 OverwriteOlder          2,160 Application
```

#### <a name="accessing-a-remote-event-log-with-new-object"></a><span data-ttu-id="5bbe9-131">Aceder a um registo de eventos remoto com o novo objeto</span><span class="sxs-lookup"><span data-stu-id="5bbe9-131">Accessing a Remote Event Log with New-Object</span></span>

<span data-ttu-id="5bbe9-132">Os comandos utilizados na secção anterior de destino no computador local; o **Get-EventLog** cmdlet pode fazer isso.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-132">The commands used in the preceding section target the local computer; the **Get-EventLog** cmdlet can do that.</span></span> <span data-ttu-id="5bbe9-133">Para aceder ao registo de aplicações num computador remoto, tem de indicar tanto o nome do registo e um nome de computador (ou endereço IP) como argumentos.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-133">To access the Application log on a remote computer, you must supply both the log name and a computer name (or IP address) as arguments.</span></span>

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

<span data-ttu-id="5bbe9-134">Agora que temos uma referência a um registo de eventos armazenada na variável $RemoteAppLog, quais as tarefas podem realizar no mesmo?</span><span class="sxs-lookup"><span data-stu-id="5bbe9-134">Now that we have a reference to an event log stored in the $RemoteAppLog variable, what tasks can we perform on it?</span></span>

#### <a name="clearing-an-event-log-with-object-methods"></a><span data-ttu-id="5bbe9-135">Limpar um registo de eventos com os métodos do objeto</span><span class="sxs-lookup"><span data-stu-id="5bbe9-135">Clearing an Event Log with Object Methods</span></span>

<span data-ttu-id="5bbe9-136">Os objetos têm, muitas vezes, os métodos que podem ser chamados para executar tarefas.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-136">Objects often have methods that can be called to perform tasks.</span></span> <span data-ttu-id="5bbe9-137">Pode usar **Get-Member** para apresentar os métodos associados um objeto.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-137">You can use **Get-Member** to display the methods associated with an object.</span></span> <span data-ttu-id="5bbe9-138">O seguinte comando e a saída selecionada mostram alguns métodos da classe de registo de eventos:</span><span class="sxs-lookup"><span data-stu-id="5bbe9-138">The following command and selected output show some the methods of the EventLog class:</span></span>

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

<span data-ttu-id="5bbe9-139">O **limpar ()** método pode ser utilizado para limpar o registo de eventos.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-139">The **Clear()** method can be used to clear the event log.</span></span> <span data-ttu-id="5bbe9-140">Ao chamar um método, sempre devem seguir o nome do método por parênteses, mesmo que o método não necessita de argumentos.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-140">When calling a method, you must always follow the method name by parentheses, even if the method does not require arguments.</span></span> <span data-ttu-id="5bbe9-141">Isso permite que o PowerShell de Windows distinguir entre o método e uma propriedade potencial com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-141">This lets Windows PowerShell distinguish between the method and a potential property with the same name.</span></span> <span data-ttu-id="5bbe9-142">Escreva o seguinte para chamar o **clara** método:</span><span class="sxs-lookup"><span data-stu-id="5bbe9-142">Type the following to call the **Clear** method:</span></span>

```
PS> $RemoteAppLog.Clear()
```

<span data-ttu-id="5bbe9-143">Escreva o seguinte para apresentar o registo.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-143">Type the following to display the log.</span></span> <span data-ttu-id="5bbe9-144">Verá que o registo de eventos foi limpo e agora tem 0 entradas em vez de 262:</span><span class="sxs-lookup"><span data-stu-id="5bbe9-144">You will see that the event log was cleared, and now has 0 entries instead of 262:</span></span>

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

### <a name="creating-com-objects-with-new-object"></a><span data-ttu-id="5bbe9-145">Criação de objetos COM o novo objeto</span><span class="sxs-lookup"><span data-stu-id="5bbe9-145">Creating COM Objects with New-Object</span></span>
<span data-ttu-id="5bbe9-146">Pode usar **New-Object** para trabalhar com componentes do modelo COM (Component Object).</span><span class="sxs-lookup"><span data-stu-id="5bbe9-146">You can use **New-Object** to work with Component Object Model (COM) components.</span></span> <span data-ttu-id="5bbe9-147">Intervalo de componentes das várias bibliotecas incluídos com o Windows Script Host (WSH) para aplicativos de ActiveX como o Internet Explorer que são instalados na maioria dos sistemas.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-147">Components range from the various libraries included with Windows Script Host (WSH) to ActiveX applications such as Internet Explorer that are installed on most systems.</span></span>

<span data-ttu-id="5bbe9-148">**Novo objeto** utiliza Wrappers que pode ser chamado tempo de execução do .NET Framework para criar objetos COM, pelo que tem as mesmas limitações que o .NET Framework faz ao chamar objetos COM.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-148">**New-Object** uses .NET Framework Runtime-Callable Wrappers to create COM objects, so it has the same limitations that .NET Framework does when calling COM objects.</span></span> <span data-ttu-id="5bbe9-149">Para criar um objeto COM, tem de especificar o **ComObject** parâmetro com o identificador de programação ou *ProgId* da classe COM que pretende utilizar.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-149">To create a COM object, you need to specify the **ComObject** parameter with the Programmatic Identifier or *ProgId* of the COM class you want to use.</span></span> <span data-ttu-id="5bbe9-150">Uma discussão completa sobre as limitações de utilização de COM e determinar quais ProgIds estão disponíveis num sistema está além do escopo guia deste utilizador, mas objetos conhecidos dos ambientes, tais como o WSH podem ser utilizados dentro do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-150">A complete discussion of the limitations of COM use and determining what ProgIds are available on a system is beyond the scope of this user's guide, but most well-known objects from environments such as WSH can be used within Windows PowerShell.</span></span>

<span data-ttu-id="5bbe9-151">Pode criar os objetos WSH ao especificar essas progids: **WScript. Shell**, **WScript**, **Scripting.Dictionary**, e **FileSystemObject**.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-151">You can create the WSH objects by specifying these progids: **WScript.Shell**, **WScript.Network**, **Scripting.Dictionary**, and **Scripting.FileSystemObject**.</span></span> <span data-ttu-id="5bbe9-152">Os comandos seguintes criam esses objetos:</span><span class="sxs-lookup"><span data-stu-id="5bbe9-152">The following commands create these objects:</span></span>

```powershell
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

<span data-ttu-id="5bbe9-153">Embora a maior parte da funcionalidade dessas classes é disponibilizada de outras formas no Windows PowerShell, algumas tarefas, tais como a criação do atalho são ainda mais fácil fazer usando as classes do WSH.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-153">Although most of the functionality of these classes is made available in other ways in Windows PowerShell, a few tasks such as shortcut creation are still easier to do using the WSH classes.</span></span>

### <a name="creating-a-desktop-shortcut-with-wscriptshell"></a><span data-ttu-id="5bbe9-154">Criar um atalho de Desktop com Wscript. Shell</span><span class="sxs-lookup"><span data-stu-id="5bbe9-154">Creating a Desktop Shortcut with WScript.Shell</span></span>

<span data-ttu-id="5bbe9-155">Uma tarefa que pode ser realizada rapidamente com um objeto COM é a criação de um atalho.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-155">One task that can be performed quickly with a COM object is creating a shortcut.</span></span> <span data-ttu-id="5bbe9-156">Suponha que desejar criar um atalho no ambiente de trabalho que liga na pasta raiz para o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-156">Suppose you want to create a shortcut on your desktop that links to the home folder for Windows PowerShell.</span></span> <span data-ttu-id="5bbe9-157">Tem primeiro de criar uma referência a **Wscript. Shell**, que armazenamos numa variável chamada **$WshShell**:</span><span class="sxs-lookup"><span data-stu-id="5bbe9-157">You first need to create a reference to **WScript.Shell**, which we will store in a variable named **$WshShell**:</span></span>

```powershell
$WshShell = New-Object -ComObject WScript.Shell
```

<span data-ttu-id="5bbe9-158">Get-Member funciona com objetos COM, para que possa explorar os membros do objeto ao escrever:</span><span class="sxs-lookup"><span data-stu-id="5bbe9-158">Get-Member works with COM objects, so you can explore the members of the object by typing:</span></span>

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

<span data-ttu-id="5bbe9-159">**Get-Member** tem opcional **InputObject** parâmetro, pode utilizar em vez de piping fornecer entradas **Get-Member**.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-159">**Get-Member** has an optional **InputObject** parameter you can use instead of piping to provide input to **Get-Member**.</span></span> <span data-ttu-id="5bbe9-160">Obtém a mesma saída conforme mostrado acima, se tiver utilizado, em vez disso, o comando **Get-Member - InputObject $WshShell**.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-160">You would get the same output as shown above if you instead used the command **Get-Member -InputObject $WshShell**.</span></span> <span data-ttu-id="5bbe9-161">Se usar **InputObject**, ele trata o respetivo argumento como um único item.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-161">If you use **InputObject**, it treats its argument as a single item.</span></span> <span data-ttu-id="5bbe9-162">Isso significa que, se tiver vários objetos numa variável **Get-Member** trata-los como uma matriz de objetos.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-162">This means that if you have several objects in a variable, **Get-Member** treats them as an array of objects.</span></span> <span data-ttu-id="5bbe9-163">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="5bbe9-163">For example:</span></span>

```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

<span data-ttu-id="5bbe9-164">O **Wscript. Shell CreateShortcut** método aceita um único argumento, o caminho para o ficheiro de atalho para criar.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-164">The **WScript.Shell CreateShortcut** method accepts a single argument, the path to the shortcut file to create.</span></span> <span data-ttu-id="5bbe9-165">Podemos poderia digitar o caminho completo para a área de trabalho, mas há uma maneira mais fácil.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-165">We could type in the full path to the desktop, but there is an easier way.</span></span> <span data-ttu-id="5bbe9-166">A área de trabalho normalmente é representada por uma pasta denominada área de trabalho dentro da pasta raiz do utilizador atual.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-166">The desktop is normally represented by a folder named Desktop inside the home folder of the current user.</span></span> <span data-ttu-id="5bbe9-167">Windows PowerShell tem uma variável **$Home** que contém o caminho para esta pasta.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-167">Windows PowerShell has a variable **$Home** that contains the path to this folder.</span></span> <span data-ttu-id="5bbe9-168">Podemos especificar o caminho para a pasta raiz ao utilizar esta variável e, em seguida, adicione o nome da pasta ambiente de trabalho e o nome para o atalho criar digitando:</span><span class="sxs-lookup"><span data-stu-id="5bbe9-168">We can specify the path to the home folder by using this variable, and then add the name of the Desktop folder and the name for the shortcut to create by typing:</span></span>

```powershell
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

<span data-ttu-id="5bbe9-169">Quando usar algo como um nome de variável dentro de aspas duplas, o Windows PowerShell tenta substituir um valor correspondente.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-169">When you use something that looks like a variable name inside double-quotes, Windows PowerShell tries to substitute a matching value.</span></span> <span data-ttu-id="5bbe9-170">Se usar aspas único, o Windows PowerShell não tentando substitua o valor da variável.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-170">If you use single-quotes, Windows PowerShell does not try to substitute the variable value.</span></span> <span data-ttu-id="5bbe9-171">Por exemplo, experimente escrever os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="5bbe9-171">For example, try typing the following commands:</span></span>

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

<span data-ttu-id="5bbe9-172">Agora, temos uma variável chamada **$lnk** que contém uma nova referência de atalho.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-172">We now have a variable named **$lnk** that contains a new shortcut reference.</span></span> <span data-ttu-id="5bbe9-173">Se quiser ver seus membros, pode encaminhá-la para **Get-Member**.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-173">If you want to see its members, you can pipe it to **Get-Member**.</span></span> <span data-ttu-id="5bbe9-174">O resultado abaixo mostra os membros, precisamos usar para concluir a criação de nosso atalho:</span><span class="sxs-lookup"><span data-stu-id="5bbe9-174">The output below shows the members we need to use to finish creating our shortcut:</span></span>

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

<span data-ttu-id="5bbe9-175">Precisamos especificar os **TargetPath**, que é a pasta de aplicativos para o Windows PowerShell e, em seguida, guarde o atalho **$lnk** chamando o **guardar** método.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-175">We need to specify the **TargetPath**, which is the application folder for Windows PowerShell, and then save the shortcut **$lnk** by calling the **Save** method.</span></span> <span data-ttu-id="5bbe9-176">O caminho de pasta de aplicação do Windows PowerShell é armazenado na variável **$PSHome**, pelo que podemos fazer isso digitando:</span><span class="sxs-lookup"><span data-stu-id="5bbe9-176">The Windows PowerShell application folder path is stored in the variable **$PSHome**, so we can do this by typing:</span></span>

```powershell
$lnk.TargetPath = $PSHome
$lnk.Save()
```

### <a name="using-internet-explorer-from-windows-powershell"></a><span data-ttu-id="5bbe9-177">Usando o Internet Explorer do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5bbe9-177">Using Internet Explorer from Windows PowerShell</span></span>

<span data-ttu-id="5bbe9-178">Muitos aplicativos (incluindo a família do Microsoft Office de aplicativos e o Internet Explorer) podem ser automatizados usando COM.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-178">Many applications (including the Microsoft Office family of applications and Internet Explorer) can be automated by using COM.</span></span> <span data-ttu-id="5bbe9-179">Internet Explorer ilustra alguns dos problemas envolvidos ao trabalhar com aplicativos baseados em e técnicas comuns.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-179">Internet Explorer illustrates some of the typical techniques and issues involved in working with COM-based applications.</span></span>

<span data-ttu-id="5bbe9-180">Criar uma instância do Internet Explorer, especificando o Internet Explorer ProgId, **InternetExplorer. Application**:</span><span class="sxs-lookup"><span data-stu-id="5bbe9-180">You create an Internet Explorer instance by specifying the Internet Explorer ProgId, **InternetExplorer.Application**:</span></span>

```powershell
$ie = New-Object -ComObject InternetExplorer.Application
```

<span data-ttu-id="5bbe9-181">Este comando inicia o Internet Explorer, mas não a tornar visível.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-181">This command starts Internet Explorer, but does not make it visible.</span></span> <span data-ttu-id="5bbe9-182">Se digitar Get-Process, pode ver que um processo denominado iexplore está em execução.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-182">If you type Get-Process, you can see that a process named iexplore is running.</span></span> <span data-ttu-id="5bbe9-183">Na verdade, se sair do Windows PowerShell, o processo irá continuar a executar.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-183">In fact, if you exit Windows PowerShell, the process will continue to run.</span></span> <span data-ttu-id="5bbe9-184">Tem de reiniciar o computador ou usar uma ferramenta como o Gerenciador de tarefas para terminar o processo de iexplore.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-184">You must reboot the computer or use a tool like Task Manager to end the iexplore process.</span></span>

> [!NOTE]
> <span data-ttu-id="5bbe9-185">Objetos COM que inicie o como processos separados, geralmente designada *ActiveX executáveis*; pode ou não pode exibir uma janela de interface do usuário durante o arranque.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-185">COM objects that start as separate processes, commonly called *ActiveX executables*, may or may not display a user interface window when they start up.</span></span> <span data-ttu-id="5bbe9-186">Se criar uma janela mas não a tornar visível, como o Internet Explorer, o foco em geral será movido para a área de trabalho do Windows e deve fazer a janela visíveis para interagir com ele.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-186">If they create a window but do not make it visible, like Internet Explorer, the focus will generally move to the Windows desktop and you must make the window visible to interact with it.</span></span>

<span data-ttu-id="5bbe9-187">Ao escrever **$ie | Get-Member**, pode ver as propriedades e métodos para o Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-187">By typing **$ie | Get-Member**, you can view properties and methods for Internet Explorer.</span></span> <span data-ttu-id="5bbe9-188">Para ver a janela do Internet Explorer, defina a propriedade Visible como $true digitando:</span><span class="sxs-lookup"><span data-stu-id="5bbe9-188">To see the Internet Explorer window, set the Visible property to $true by typing:</span></span>

```powershell
$ie.Visible = $true
```

<span data-ttu-id="5bbe9-189">Em seguida, pode navegar para um endereço específico da Web usando o método Navigate:</span><span class="sxs-lookup"><span data-stu-id="5bbe9-189">You can then navigate to a specific Web address by using the Navigate method:</span></span>

```powershell
$ie.Navigate("http://www.microsoft.com/technet/scriptcenter/default.mspx")
```

<span data-ttu-id="5bbe9-190">Com outros membros do modelo de objeto do Internet Explorer, é possível obter o conteúdo de texto da página da Web.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-190">Using other members of the Internet Explorer object model, it is possible to retrieve text content from the Web page.</span></span> <span data-ttu-id="5bbe9-191">O comando seguinte irá apresentar o texto HTML no corpo da página da Web atual:</span><span class="sxs-lookup"><span data-stu-id="5bbe9-191">The following command will display the HTML text in the body of the current Web page:</span></span>

```powershell
$ie.Document.Body.InnerText
```

<span data-ttu-id="5bbe9-192">Para fechar o Internet Explorer a partir do PowerShell, chame seu método Quit():</span><span class="sxs-lookup"><span data-stu-id="5bbe9-192">To close Internet Explorer from within PowerShell, call its Quit() method:</span></span>

```powershell
$ie.Quit()
```

<span data-ttu-id="5bbe9-193">Isso obrigará a fechar.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-193">This will force it to close.</span></span> <span data-ttu-id="5bbe9-194">A variável $ie já não contém uma referência válida, apesar de ainda parece ser um objeto COM.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-194">The $ie variable no longer contains a valid reference even though it still appears to be a COM object.</span></span> <span data-ttu-id="5bbe9-195">Se tentar usá-lo, obterá um erro de automatização:</span><span class="sxs-lookup"><span data-stu-id="5bbe9-195">If you attempt to use it, you will get an automation error:</span></span>

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

<span data-ttu-id="5bbe9-196">Pode remover o restante de referência com um comando como $ie = $null ou remover completamente a variável digitando:</span><span class="sxs-lookup"><span data-stu-id="5bbe9-196">You can either remove the remaining reference with a command like $ie = $null, or completely remove the variable by typing:</span></span>

```powershell
Remove-Variable ie
```

> [!NOTE]
> <span data-ttu-id="5bbe9-197">Não existe nenhuma padrão comum para se executáveis de ActiveX saiam ou continuam a executar quando remove uma referência a um.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-197">There is no common standard for whether ActiveX executables exit or continue to run when you remove a reference to one.</span></span> <span data-ttu-id="5bbe9-198">Dependendo das circunstâncias, como se a aplicação tem visível, se um documento editado está em execução no mesmo e até mesmo se Windows PowerShell ainda está em execução, a aplicação pode ou não pode sair.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-198">Depending on circumstances such as whether the application is visible, whether an edited document is running in it, and even whether Windows PowerShell is still running, the application may or may not exit.</span></span> <span data-ttu-id="5bbe9-199">Por esse motivo, deve testar o comportamento de terminação para cada ActiveX executável que pretende utilizar no Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-199">For this reason, you should test termination behavior for each ActiveX executable you want to use in Windows PowerShell.</span></span>

### <a name="getting-warnings-about-net-framework-wrapped-com-objects"></a><span data-ttu-id="5bbe9-200">Avisos sobre os objetos do .NET Framework-encapsuladas COM a obter</span><span class="sxs-lookup"><span data-stu-id="5bbe9-200">Getting Warnings About .NET Framework-Wrapped COM Objects</span></span>

<span data-ttu-id="5bbe9-201">Em alguns casos, um objeto COM pode ter um associados do .NET Framework *Runtime Callable Wrapper* ou RCW e esta vai ser utilizado por **New-Object**.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-201">In some cases, a COM object might have an associated .NET Framework *Runtime-Callable Wrapper* or RCW, and this will be used by **New-Object**.</span></span> <span data-ttu-id="5bbe9-202">Uma vez que o comportamento do RCW pode ser diferente do comportamento do objeto COM normal **New-Object** tem uma **Strict** parâmetro para o avisar sobre o acesso RCW.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-202">Since the behavior of the RCW may be different from the behavior of the normal COM object, **New-Object** has a **Strict** parameter to warn you about RCW access.</span></span> <span data-ttu-id="5bbe9-203">Se especificar a **Strict** parâmetro e, em seguida, criar um objeto COM que utiliza um RCW, receberá uma mensagem de aviso:</span><span class="sxs-lookup"><span data-stu-id="5bbe9-203">If you specify the **Strict** parameter and then create a COM object that uses an RCW, you get a warning message:</span></span>

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

<span data-ttu-id="5bbe9-204">Embora o objeto ainda está a ser criado, é avisado que não é um objeto COM padrão.</span><span class="sxs-lookup"><span data-stu-id="5bbe9-204">Although the object is still created, you are warned that it is not a standard COM object.</span></span>