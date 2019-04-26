---
title: (Etiquetas) de vista de lista | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53442bb1-74a3-49f9-9150-3bc3081a7565
caps.latest.revision: 6
ms.openlocfilehash: 27de41c88e224f7610c10a764e51524016ecc8cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065279"
---
# <a name="list-view-labels"></a><span data-ttu-id="d50cb-102">List View (Basic) (Vista de Lista [Etiquetas])</span><span class="sxs-lookup"><span data-stu-id="d50cb-102">List View (Labels)</span></span>

<span data-ttu-id="d50cb-103">Este exemplo mostra como implementar uma vista de lista que apresente uma etiqueta personalizada para cada linha da lista.</span><span class="sxs-lookup"><span data-stu-id="d50cb-103">This example shows how to implement a list view that displays a custom label for each row of the list.</span></span> <span data-ttu-id="d50cb-104">Esta vista de lista apresenta as propriedades do [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objeto devolvido pela [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d50cb-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="d50cb-105">Para obter mais informações sobre os componentes de uma vista de lista, consulte [criar uma vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="d50cb-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="d50cb-106">Para carregar este ficheiro de formatação</span><span class="sxs-lookup"><span data-stu-id="d50cb-106">To load this formatting file</span></span>

1. <span data-ttu-id="d50cb-107">Copie o XML da seção de exemplo deste tópico para um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="d50cb-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="d50cb-108">Guarde o ficheiro de texto.</span><span class="sxs-lookup"><span data-stu-id="d50cb-108">Save the text file.</span></span> <span data-ttu-id="d50cb-109">Certifique-se de que adicionar a `format.ps1xml` extensão para o ficheiro para identificá-lo como um ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="d50cb-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="d50cb-110">Abra o Windows PowerShell e execute o seguinte comando para carregar o ficheiro de formatação para a sessão atual: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="d50cb-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="d50cb-111">Esse arquivo formatação define a apresentação de um objeto que já esteja definida por um ficheiro de formatação do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d50cb-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="d50cb-112">Tem de utilizar o `prependPath` parâmetro ao executar o cmdlet, e não é possível carregar essa formatação de ficheiros como um módulo.</span><span class="sxs-lookup"><span data-stu-id="d50cb-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="d50cb-113">Demonstra</span><span class="sxs-lookup"><span data-stu-id="d50cb-113">Demonstrates</span></span>

<span data-ttu-id="d50cb-114">Este ficheiro de formatação demonstra os seguintes elementos XML:</span><span class="sxs-lookup"><span data-stu-id="d50cb-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="d50cb-115">O [nome](./name-element-for-view-format.md) elemento para a vista.</span><span class="sxs-lookup"><span data-stu-id="d50cb-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="d50cb-116">O [ViewSelectedBy](./viewselectedby-element-format.md) elemento que define os objetos que são apresentados pela exibição.</span><span class="sxs-lookup"><span data-stu-id="d50cb-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="d50cb-117">O [ListControl](./listcontrol-element-format.md) elemento que define a propriedade de que é apresentada pela vista.</span><span class="sxs-lookup"><span data-stu-id="d50cb-117">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="d50cb-118">O [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) elemento que define o que é exibido numa linha da exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="d50cb-118">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="d50cb-119">O [etiqueta](./label-element-for-listitem-for-listcontrol-format.md) elemento que define o que é exibido numa linha da exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="d50cb-119">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="d50cb-120">O [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento que define a propriedade é apresentada.</span><span class="sxs-lookup"><span data-stu-id="d50cb-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="d50cb-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d50cb-121">Example</span></span>

<span data-ttu-id="d50cb-122">O XML a seguir define uma vista de lista que exibe uma etiqueta personalizada em cada linha.</span><span class="sxs-lookup"><span data-stu-id="d50cb-122">The following XML defines a list view that displays a custom label in each row.</span></span> <span data-ttu-id="d50cb-123">Neste caso, a etiqueta inclui o nome da propriedade a cada letra em maiúsculas e a palavra "property".</span><span class="sxs-lookup"><span data-stu-id="d50cb-123">In this case, the label includes the property name with each letter capitalized and the word "property".</span></span> <span data-ttu-id="d50cb-124">Em cada linha, é apresentado o nome da propriedade seguido o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="d50cb-124">In each row, the name of the property is displayed followed by the value of the property.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <Label>NAME property</Label>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <Label>DISPLAYNAME property</Label>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <Label>STATUS property</Label>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <Label>SERVICETYPE property</Label>
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

<span data-ttu-id="d50cb-125">O exemplo seguinte mostra como o Windows PowerShell apresenta o [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objetos depois deste ficheiro de formato é carregado.</span><span class="sxs-lookup"><span data-stu-id="d50cb-125">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
NAME property        : Fax
DISPLAYNAME property : Fax
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FCSAM
DISPLAYNAME property : Microsoft Antimalware Service
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : fdPHost
DISPLAYNAME property : Function Discovery Provider Host
STATUS property      : Stopped
SERVICETYPE property : Win32ShareProcess

NAME property        : FDResPub
DISPLAYNAME property : Function Discovery Resource Publication
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache
DISPLAYNAME property : Windows Font Cache Service
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache3.0.0.0
DISPLAYNAME property : Windows Presentation Foundation Font Cache 3.0.0.0
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FSysAgent
DISPLAYNAME property : Microsoft Forefront System Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : FwcAgent
DISPLAYNAME property : Firewall Client Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="d50cb-126">Veja Também</span><span class="sxs-lookup"><span data-stu-id="d50cb-126">See Also</span></span>

[<span data-ttu-id="d50cb-127">Exemplos de arquivos de formatação</span><span class="sxs-lookup"><span data-stu-id="d50cb-127">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="d50cb-128">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d50cb-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
