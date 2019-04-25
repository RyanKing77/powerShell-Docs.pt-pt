---
title: Vista (GroupBy) de lista | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2e66c86-83a7-4148-8575-c28d6d429d4f
caps.latest.revision: 6
ms.openlocfilehash: c178c4a48f9595001bcc249d5f55886fa54bb9f2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065296"
---
# <a name="list-view-groupby"></a><span data-ttu-id="1198a-102">List View (GroupBy) (Vista de Lista [GroupBy])</span><span class="sxs-lookup"><span data-stu-id="1198a-102">List View (GroupBy)</span></span>

<span data-ttu-id="1198a-103">Este exemplo mostra como implementar uma vista de lista que separa as linhas da lista em grupos.</span><span class="sxs-lookup"><span data-stu-id="1198a-103">This example shows how to implement a list view that separates the rows of the list into groups.</span></span> <span data-ttu-id="1198a-104">Esta vista de lista apresenta as propriedades do [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objectos devolvidos pela [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1198a-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="1198a-105">Para obter mais informações sobre os componentes de uma vista de lista, consulte [criar uma vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="1198a-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="1198a-106">Para carregar este ficheiro de formatação</span><span class="sxs-lookup"><span data-stu-id="1198a-106">To load this formatting file</span></span>

1. <span data-ttu-id="1198a-107">Copie o XML da seção de exemplo deste tópico para um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="1198a-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="1198a-108">Guarde o ficheiro de texto.</span><span class="sxs-lookup"><span data-stu-id="1198a-108">Save the text file.</span></span> <span data-ttu-id="1198a-109">Certifique-se de que adicionar a `format.ps1xml` extensão para o ficheiro para identificá-lo como um ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="1198a-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="1198a-110">Abra o Windows PowerShell e execute o seguinte comando para carregar o ficheiro de formatação para a sessão atual: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="1198a-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="1198a-111">Esse arquivo formatação define a apresentação de um objeto que já esteja definida por um ficheiro de formatação do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1198a-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="1198a-112">Tem de utilizar o `prependPath` parâmetro ao executar o cmdlet, e não é possível carregar essa formatação de ficheiros como um módulo.</span><span class="sxs-lookup"><span data-stu-id="1198a-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="1198a-113">Demonstra</span><span class="sxs-lookup"><span data-stu-id="1198a-113">Demonstrates</span></span>

<span data-ttu-id="1198a-114">Este ficheiro de formatação demonstra os seguintes elementos XML:</span><span class="sxs-lookup"><span data-stu-id="1198a-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="1198a-115">O [nome](./name-element-for-view-format.md) elemento para a vista.</span><span class="sxs-lookup"><span data-stu-id="1198a-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="1198a-116">O [ViewSelectedBy](./viewselectedby-element-format.md) elemento que define os objetos que são apresentados pela exibição.</span><span class="sxs-lookup"><span data-stu-id="1198a-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="1198a-117">O [GroupBy](./viewselectedby-element-format.md) elemento que define a forma como é apresentado um novo grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="1198a-117">The [GroupBy](./viewselectedby-element-format.md) element that defines how a new group of objects is displayed.</span></span>

- <span data-ttu-id="1198a-118">O [ListControl](./listcontrol-element-format.md) elemento que define a propriedade de que é apresentada pela vista.</span><span class="sxs-lookup"><span data-stu-id="1198a-118">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="1198a-119">O [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) elemento que define o que é exibido numa linha da exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="1198a-119">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="1198a-120">O [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento que define a propriedade é apresentada.</span><span class="sxs-lookup"><span data-stu-id="1198a-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="1198a-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1198a-121">Example</span></span>

<span data-ttu-id="1198a-122">O XML a seguir define uma vista de lista que começa um novo grupo sempre que o valor do [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) alterações de propriedade.</span><span class="sxs-lookup"><span data-stu-id="1198a-122">The following XML defines a list view that starts a new group whenever the value of the [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) property changes.</span></span> <span data-ttu-id="1198a-123">Quando é iniciado a cada grupo, é apresentada uma etiqueta personalizada que inclui o novo valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="1198a-123">When each group is started, a custom label is displayed that includes the new value of the property.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <Name>System.ServiceProcess.ServiceController</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <PropertyName>Status</PropertyName>
        <Label>New Service Status</Label>
      </GroupBy>
      <ListControl>
        <ListEntries>
          <ListEntry>
            <ListItems>
              <ListItem>
                <PropertyName>Name</PropertyName>
              </ListItem>
              <ListItem>
                <PropertyName>DisplayName</PropertyName>
              </ListItem>
              <ListItem>
                <PropertyName>ServiceType</PropertyName>
              </ListItem>
            </ListItems>
          </ListEntry>
        </ListEntries>
      </ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

<span data-ttu-id="1198a-124">O exemplo seguinte mostra como o Windows PowerShell apresenta o [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objetos depois deste ficheiro de formato é carregado.</span><span class="sxs-lookup"><span data-stu-id="1198a-124">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span> <span data-ttu-id="1198a-125">As linhas em branco adicionadas antes e depois o rótulo de grupo são adicionadas automaticamente pelo Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1198a-125">The blank lines added before and after the group label are automatically added by Windows PowerShell.</span></span>

```powershell
Get-Service f*
```

```output
   New Service Status: Stopped

Name        : Fax
DisplayName : Fax
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
ServiceType : Win32OwnProcess

   New Service Status: Stopped

Name        : fdPHost
DisplayName : Function Discovery Provider Host
ServiceType : Win32ShareProcess

   New Service Status: Running

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
ServiceType : Win32ShareProcess

   New Service Status: Stopped

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="1198a-126">Veja Também</span><span class="sxs-lookup"><span data-stu-id="1198a-126">See Also</span></span>

[<span data-ttu-id="1198a-127">Exemplos de arquivos de formatação</span><span class="sxs-lookup"><span data-stu-id="1198a-127">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="1198a-128">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="1198a-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
