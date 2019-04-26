---
title: Estado de sessão do Windows PowerShell | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlets [PowerShell], session state
- session state [PowerShell]
ms.assetid: 74912940-2b10-4a76-b174-6d035d71c02b
caps.latest.revision: 8
ms.openlocfilehash: fa207130bbb120750780bb0aa9b32150a32daaa2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066979"
---
# <a name="windows-powershell-session-state"></a><span data-ttu-id="0f288-102">Windows PowerShell Session State (Estado da Sessão do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="0f288-102">Windows PowerShell Session State</span></span>

<span data-ttu-id="0f288-103">Estado da sessão refere-se para a configuração atual de uma sessão do Windows PowerShell ou o módulo.</span><span class="sxs-lookup"><span data-stu-id="0f288-103">Session state refers to the current configuration of a Windows PowerShell session or module.</span></span> <span data-ttu-id="0f288-104">Uma sessão do Windows PowerShell é o ambiente operacional que é utilizado de forma interativa pelo utilizador da linha de comandos ou por meio de programação por um aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="0f288-104">A Windows PowerShell session is the operational environment that is used interactively by the command-line user or programmatically by a host application.</span></span> <span data-ttu-id="0f288-105">O estado da sessão para uma sessão é referido como o estado da sessão global.</span><span class="sxs-lookup"><span data-stu-id="0f288-105">The session state for a session is referred to as the global session state.</span></span>

<span data-ttu-id="0f288-106">Da perspectiva do desenvolvedor, refere-se uma sessão do Windows PowerShell para o tempo entre quando um aplicativo host é aberto um espaço de execução do Windows PowerShell e quando ele fecha o espaço de execução.</span><span class="sxs-lookup"><span data-stu-id="0f288-106">From a developer perspective, a Windows PowerShell session refers to the time between when a host application opens a Windows PowerShell runspace and when it closes the runspace.</span></span> <span data-ttu-id="0f288-107">Observado outra forma, a sessão é o tempo de vida de uma instância do motor do PowerShell de Windows que é invocada enquanto o espaço de execução existe.</span><span class="sxs-lookup"><span data-stu-id="0f288-107">Looked at another way, the session is the lifetime of an instance of the Windows PowerShell engine that is invoked while the runspace exists.</span></span>

## <a name="module-session-state"></a><span data-ttu-id="0f288-108">Estado da sessão de módulo</span><span class="sxs-lookup"><span data-stu-id="0f288-108">Module Session State</span></span>

<span data-ttu-id="0f288-109">Estados de sessão do módulo são criados sempre que o módulo ou um dos respectivos módulos aninhados é importado para a sessão.</span><span class="sxs-lookup"><span data-stu-id="0f288-109">Module session states are created whenever the module or one of its nested modules is imported into the session.</span></span> <span data-ttu-id="0f288-110">Quando um módulo exporta um elemento como um cmdlet, função ou script, uma referência a esse elemento é adicionada para o estado da sessão global da sessão.</span><span class="sxs-lookup"><span data-stu-id="0f288-110">When a module exports an element such as a cmdlet, function, or script, a reference to that element is added to the global session state of the session.</span></span> <span data-ttu-id="0f288-111">No entanto, quando o elemento é executado, ele é executado dentro do Estado da sessão do módulo.</span><span class="sxs-lookup"><span data-stu-id="0f288-111">However, when the element is run, it is executed within the session state of the module.</span></span>

## <a name="session-state-data"></a><span data-ttu-id="0f288-112">Dados de estado da sessão</span><span class="sxs-lookup"><span data-stu-id="0f288-112">Session-State Data</span></span>

<span data-ttu-id="0f288-113">Dados de estado da sessão podem ser público ou privado.</span><span class="sxs-lookup"><span data-stu-id="0f288-113">Session state data can be public or private.</span></span> <span data-ttu-id="0f288-114">Dados públicos estão disponíveis para chamadas a partir de fora o estado da sessão, enquanto os dados privados só estão disponíveis para chamadas a partir do Estado da sessão.</span><span class="sxs-lookup"><span data-stu-id="0f288-114">Public data is available to calls from outside the session state while private data is available only to calls from within the session state.</span></span> <span data-ttu-id="0f288-115">Por exemplo, um módulo pode ter uma função privada que pode ser chamada apenas pelo módulo ou apenas internamente por um elemento público que tenha sido exportado.</span><span class="sxs-lookup"><span data-stu-id="0f288-115">For example, a module can have a private function that can be called only by the module or only internally by a public element that has been exported.</span></span> <span data-ttu-id="0f288-116">Isso é semelhante para os membros privados e públicos de um tipo de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0f288-116">This is similar to the private and public members of a .NET Framework type.</span></span>

<span data-ttu-id="0f288-117">Dados de estado da sessão são armazenados por instância atual do motor de execução dentro do contexto da sessão atual do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0f288-117">Session-state data is stored by the current instance of the execution engine within the context of the current Windows PowerShell session.</span></span> <span data-ttu-id="0f288-118">Dados de estado da sessão inclui os seguintes itens:</span><span class="sxs-lookup"><span data-stu-id="0f288-118">Session-state data consists of the following items:</span></span>

- <span data-ttu-id="0f288-119">Informações de caminho</span><span class="sxs-lookup"><span data-stu-id="0f288-119">Path information</span></span>

- <span data-ttu-id="0f288-120">Informações da unidade</span><span class="sxs-lookup"><span data-stu-id="0f288-120">Drive information</span></span>

- <span data-ttu-id="0f288-121">Informações do fornecedor de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f288-121">Windows PowerShell provider information</span></span>

- <span data-ttu-id="0f288-122">Informações sobre as referências para os elementos de módulo (por exemplo, cmdlets, funções e scripts) que são exportados pelo módulo e módulos importados.</span><span class="sxs-lookup"><span data-stu-id="0f288-122">Information about the imported modules and references to the module elements (such as cmdlets, functions, and scripts) that are exported by the module.</span></span> <span data-ttu-id="0f288-123">Estas informações e estas referências são para o estado da sessão global apenas.</span><span class="sxs-lookup"><span data-stu-id="0f288-123">This information and these references are for the global session state only.</span></span>

- <span data-ttu-id="0f288-124">Informações de variáveis de estado da sessão</span><span class="sxs-lookup"><span data-stu-id="0f288-124">Session-state variable information</span></span>

## <a name="accessing-session-state-data-within-cmdlets"></a><span data-ttu-id="0f288-125">Aceder aos dados de estado da sessão dentro de Cmdlets</span><span class="sxs-lookup"><span data-stu-id="0f288-125">Accessing Session-State Data Within Cmdlets</span></span>

<span data-ttu-id="0f288-126">Cmdlets podem aceder a dados de estado da sessão ou indiretamente através do [System.Management.Automation.PSCmdlet.Sessionstate\*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) propriedade da classe cmdlet ou diretamente através do [ System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) classe.</span><span class="sxs-lookup"><span data-stu-id="0f288-126">Cmdlets can access session-state data either indirectly through the [System.Management.Automation.PSCmdlet.Sessionstate\*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) property of the cmdlet class or directly through the [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class.</span></span> <span data-ttu-id="0f288-127">O [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) classe fornece propriedades que podem ser utilizadas para investigar os diferentes tipos de dados de estado da sessão.</span><span class="sxs-lookup"><span data-stu-id="0f288-127">The [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class provides properties that can be used to investigate different types of session-state data.</span></span>

## <a name="see-also"></a><span data-ttu-id="0f288-128">Veja Também</span><span class="sxs-lookup"><span data-stu-id="0f288-128">See Also</span></span>

[<span data-ttu-id="0f288-129">System.Management.Automation.PSCmdlet.Sessionstate</span><span class="sxs-lookup"><span data-stu-id="0f288-129">System.Management.Automation.PSCmdlet.Sessionstate</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[<span data-ttu-id="0f288-130">System.Management.Automation.Sessionstate?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="0f288-130">System.Management.Automation.Sessionstate?Displayproperty=Fullname</span></span>](/dotnet/api/System.Management.Automation.SessionState)

[<span data-ttu-id="0f288-131">Cmdlets do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f288-131">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)

[<span data-ttu-id="0f288-132">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f288-132">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="0f288-133">Shell do Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="0f288-133">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
