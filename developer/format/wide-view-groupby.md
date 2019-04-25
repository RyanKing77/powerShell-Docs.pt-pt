---
title: Vista alargada (GroupBy) | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39388197-4ff9-4889-aa32-526011afa1f6
caps.latest.revision: 6
ms.openlocfilehash: e95ec550a7815a76a8bd7f9526dfa405a9644360
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083659"
---
# <a name="wide-view-groupby"></a><span data-ttu-id="df6b3-102">Wide View (GroupBy) (Vista Ampla [GroupBy])</span><span class="sxs-lookup"><span data-stu-id="df6b3-102">Wide View (GroupBy)</span></span>

<span data-ttu-id="df6b3-103">Este exemplo mostra como implementar uma vista alargada, que apresenta os grupos de [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objectos devolvidos pelo `Get-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="df6b3-103">This example shows how to implement a wide view that displays groups of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="df6b3-104">Para obter mais informações sobre os componentes de uma vista alargada, consulte [criar uma vista alargada](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="df6b3-104">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="df6b3-105">Para carregar este ficheiro de formatação</span><span class="sxs-lookup"><span data-stu-id="df6b3-105">To load this formatting file</span></span>

1. <span data-ttu-id="df6b3-106">Copie o XML da seção de exemplo deste tópico para um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="df6b3-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="df6b3-107">Guarde o ficheiro de texto.</span><span class="sxs-lookup"><span data-stu-id="df6b3-107">Save the text file.</span></span> <span data-ttu-id="df6b3-108">Certifique-se de que adicionar a `format.ps1xml` extensão para o ficheiro para identificá-lo como um ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="df6b3-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="df6b3-109">Abra o Windows PowerShell e execute o seguinte comando para carregar o ficheiro de formatação para a sessão atual: `Update-formatdata -prependpath PathToFormattingFile`.</span><span class="sxs-lookup"><span data-stu-id="df6b3-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="df6b3-110">Esse arquivo formatação define a apresentação de um objeto que já esteja definida por do Windows PowerShell formatação ficheiros.</span><span class="sxs-lookup"><span data-stu-id="df6b3-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting files.</span></span> <span data-ttu-id="df6b3-111">Tem de utilizar o `prependPath` parâmetro ao executar o cmdlet, e não é possível carregar essa formatação de ficheiros como um módulo.</span><span class="sxs-lookup"><span data-stu-id="df6b3-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="df6b3-112">Demonstra</span><span class="sxs-lookup"><span data-stu-id="df6b3-112">Demonstrates</span></span>

<span data-ttu-id="df6b3-113">Este ficheiro de formatação demonstra os seguintes elementos XML:</span><span class="sxs-lookup"><span data-stu-id="df6b3-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="df6b3-114">O [nome](./name-element-for-view-format.md) elemento para a vista.</span><span class="sxs-lookup"><span data-stu-id="df6b3-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="df6b3-115">O [ViewSelectedBy](./viewselectedby-element-format.md) elemento que define os objetos que são apresentados pela exibição.</span><span class="sxs-lookup"><span data-stu-id="df6b3-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="df6b3-116">O [GroupBy](./groupby-element-for-view-format.md) elemento que define quando é apresentado um novo grupo.</span><span class="sxs-lookup"><span data-stu-id="df6b3-116">The [GroupBy](./groupby-element-for-view-format.md) element that defines when a new group is displayed.</span></span>

- <span data-ttu-id="df6b3-117">O [WideItem](./wideitem-element-for-widecontrol-format.md) elemento que define a propriedade de que é apresentada pela vista.</span><span class="sxs-lookup"><span data-stu-id="df6b3-117">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="df6b3-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df6b3-118">Example</span></span>

<span data-ttu-id="df6b3-119">O XML a seguir define uma vista alargada, que apresenta os grupos de objetos.</span><span class="sxs-lookup"><span data-stu-id="df6b3-119">The following XML defines a wide view that displays groups of objects.</span></span> <span data-ttu-id="df6b3-120">Cada novo grupo é iniciado quando o valor do [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) alterações de propriedade.</span><span class="sxs-lookup"><span data-stu-id="df6b3-120">Each new group is started when the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <Label>Service Type</Label>
        <PropertyName>ServiceType</PropertyName>
      </GroupBy>
      <WideControl>
        <WideEntries>
          <WideEntry>
            <WideItem>
              <PropertyName>ServiceName</PropertyName>
            </WideItem>
          </WideEntry>
        </WideEntries>
      </WideControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

<span data-ttu-id="df6b3-121">O exemplo seguinte mostra como o Windows PowerShell apresenta o [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objetos depois deste ficheiro de formato é carregado.</span><span class="sxs-lookup"><span data-stu-id="df6b3-121">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
   Service Type: Win32OwnProcess

Fax                             FCSAM

   Service Type: Win32ShareProcess

fdPHost                         FDResPub
FontCache

   Service Type: Win32OwnProcess

FontCache3.0.0.0                FSysAgent
FwcAgent
```

## <a name="see-also"></a><span data-ttu-id="df6b3-122">Veja Também</span><span class="sxs-lookup"><span data-stu-id="df6b3-122">See Also</span></span>

[<span data-ttu-id="df6b3-123">Exemplos de arquivos de formatação</span><span class="sxs-lookup"><span data-stu-id="df6b3-123">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="df6b3-124">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="df6b3-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
