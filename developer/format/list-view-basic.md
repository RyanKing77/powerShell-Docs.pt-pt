---
title: Vista (básico) de lista | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 918f381c-43e6-4594-a468-a40bfa8a16d6
caps.latest.revision: 7
ms.openlocfilehash: 3c94d8e98f179286112a417230fce659dc0b614c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065313"
---
# <a name="list-view-basic"></a><span data-ttu-id="7b876-102">List View (Basic) (Vista de Lista [Básica])</span><span class="sxs-lookup"><span data-stu-id="7b876-102">List View (Basic)</span></span>

<span data-ttu-id="7b876-103">Este exemplo mostra como implementar uma vista de lista básico que exibe o [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objectos devolvidos pela [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7b876-103">This example shows how to implement a basic list view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="7b876-104">Para obter mais informações sobre os componentes de uma vista de lista, consulte [criar uma vista de lista](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="7b876-104">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="7b876-105">Para carregar este ficheiro de formatação</span><span class="sxs-lookup"><span data-stu-id="7b876-105">To load this formatting file</span></span>

1. <span data-ttu-id="7b876-106">Copie o XML da seção de exemplo deste tópico para um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="7b876-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="7b876-107">Guarde o ficheiro de texto.</span><span class="sxs-lookup"><span data-stu-id="7b876-107">Save the text file.</span></span> <span data-ttu-id="7b876-108">Certifique-se de que adicionar a `format.ps1xml` extensão para o ficheiro para identificá-lo como um ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="7b876-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="7b876-109">Abra o Windows PowerShell e execute o seguinte comando para carregar o ficheiro de formatação para a sessão atual: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="7b876-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="7b876-110">Esse arquivo formatação define a apresentação de um objeto que já esteja definida por um ficheiro de formatação do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7b876-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="7b876-111">Tem de utilizar o `prependPath` parâmetro ao executar o cmdlet, e não é possível carregar essa formatação de ficheiros como um módulo.</span><span class="sxs-lookup"><span data-stu-id="7b876-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="7b876-112">Demonstra</span><span class="sxs-lookup"><span data-stu-id="7b876-112">Demonstrates</span></span>

<span data-ttu-id="7b876-113">Este ficheiro de formatação demonstra os seguintes elementos XML:</span><span class="sxs-lookup"><span data-stu-id="7b876-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="7b876-114">O [nome](./name-element-for-view-format.md) elemento para a vista.</span><span class="sxs-lookup"><span data-stu-id="7b876-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="7b876-115">O [ViewSelectedBy](./viewselectedby-element-format.md) elemento que define os objetos que são apresentados pela exibição.</span><span class="sxs-lookup"><span data-stu-id="7b876-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="7b876-116">O [ListControl](./listcontrol-element-format.md) elemento que define a propriedade de que é apresentada pela vista.</span><span class="sxs-lookup"><span data-stu-id="7b876-116">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="7b876-117">O [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) elemento que define o que é exibido numa linha da exibição de lista.</span><span class="sxs-lookup"><span data-stu-id="7b876-117">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="7b876-118">O [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) elemento que define a propriedade é apresentada.</span><span class="sxs-lookup"><span data-stu-id="7b876-118">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="7b876-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7b876-119">Example</span></span>

<span data-ttu-id="7b876-120">O XML a seguir define uma vista de lista que exibe as quatro propriedades do [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objeto.</span><span class="sxs-lookup"><span data-stu-id="7b876-120">The following XML defines a list view that displays four properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="7b876-121">Em cada linha, é apresentado o nome da propriedade seguido o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="7b876-121">In each row, the name of the property is displayed followed by the value of the property.</span></span>

```xml
<Configuration>
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
              <PropertyName>Name</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>DisplayName</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>Status</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>ServiceType</PropertyName>
            </ListItem>
          </ListItems>
        </ListEntry>
      </ListEntries>
    </ListControl>
  </View>
</Configuration>
```

<span data-ttu-id="7b876-122">O exemplo seguinte mostra como o Windows PowerShell apresenta o [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objetos depois deste ficheiro de formato é carregado.</span><span class="sxs-lookup"><span data-stu-id="7b876-122">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
Name        : Fax
DisplayName : Fax
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
Status      : Running
ServiceType : Win32OwnProcess

Name        : fdPHost
DisplayName : Function Discovery Provider Host
Status      : Stopped
ServiceType : Win32ShareProcess

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
Status      : Running
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
Status      : Running
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="7b876-123">Veja Também</span><span class="sxs-lookup"><span data-stu-id="7b876-123">See Also</span></span>

[<span data-ttu-id="7b876-124">Exemplos de arquivos de formatação</span><span class="sxs-lookup"><span data-stu-id="7b876-124">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="7b876-125">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="7b876-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
