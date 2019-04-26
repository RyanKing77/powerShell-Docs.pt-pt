---
title: Conceitos de Cmdlet do PowerShell do Windows | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b3ef3f4-c626-4679-884f-406a37412b3e
caps.latest.revision: 16
ms.openlocfilehash: 2f84c57da7429462c69b2a020d9f8ac04f8d0f35
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067084"
---
# <a name="windows-powershell-cmdlet-concepts"></a><span data-ttu-id="b1351-102">Windows PowerShell Cmdlet Concepts (Conceitos de Cmdlet do Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="b1351-102">Windows PowerShell Cmdlet Concepts</span></span>

<span data-ttu-id="b1351-103">Esta secção descreve como os cmdlets funcionam.</span><span class="sxs-lookup"><span data-stu-id="b1351-103">This section describes how cmdlets work.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="b1351-104">Nesta Secção</span><span class="sxs-lookup"><span data-stu-id="b1351-104">In This Section</span></span>

<span data-ttu-id="b1351-105">Esta secção inclui os tópicos seguintes:</span><span class="sxs-lookup"><span data-stu-id="b1351-105">This section includes the following topics.</span></span>

<span data-ttu-id="b1351-106">[Diretrizes de desenvolvimento do cmdlet](./cmdlet-development-guidelines.md) este tópico fornece diretrizes de desenvolvimento que podem ser utilizadas para produzir cmdlets bem formado.</span><span class="sxs-lookup"><span data-stu-id="b1351-106">[Cmdlet Development Guidelines](./cmdlet-development-guidelines.md) This topic provides development guidelines that can be used to produce well-formed cmdlets.</span></span>

<span data-ttu-id="b1351-107">[Declaração de classe cmdlet](./cmdlet-class-declaration.md) este tópico descreve a declaração de classe do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b1351-107">[Cmdlet Class Declaration](./cmdlet-class-declaration.md) This topic describes cmdlet class declaration.</span></span>

<span data-ttu-id="b1351-108">[Aprovado verbos para o Windows PowerShell comandos](./approved-verbs-for-windows-powershell-commands.md) este tópico lista os verbos de cmdlet predefinidas que podem ser usadas quando declara uma classe cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b1351-108">[Approved Verbs for Windows PowerShell Commands](./approved-verbs-for-windows-powershell-commands.md) This topic lists the predefined cmdlet verbs that you can use when you declare a cmdlet class.</span></span>

<span data-ttu-id="b1351-109">[Métodos de processamento de entrada de cmdlet](./cmdlet-input-processing-methods.md) este tópico descreve os métodos que permitem um cmdlet para efetuar operações de pré-processamento, as operações de processamento de entrada e publicar as operações de processamento.</span><span class="sxs-lookup"><span data-stu-id="b1351-109">[Cmdlet Input Processing Methods](./cmdlet-input-processing-methods.md) This topic describes the methods that allow a cmdlet to perform preprocessing operations, input processing operations, and post processing operations.</span></span>

<span data-ttu-id="b1351-110">[Parâmetros do cmdlet](./cmdlet-parameters.md) esta secção descreve os diferentes tipos de parâmetros que podem ser adicionados aos cmdlets.</span><span class="sxs-lookup"><span data-stu-id="b1351-110">[Cmdlet Parameters](./cmdlet-parameters.md) This section describes the different types of parameters that you can add to cmdlets.</span></span>

<span data-ttu-id="b1351-111">[Atributos de cmdlet](./cmdlet-attributes.md) esta secção descreve os atributos que são utilizados para declarar classes do .NET Framework como cmdlets, para declarar campos como parâmetros de cmdlet e, para declarar as regras de validação de entrada para os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="b1351-111">[Cmdlet Attributes](./cmdlet-attributes.md) This section describes the attributes that are used to declare .NET Framework classes as cmdlets, to declare fields as cmdlet parameters, and to declare input validation rules for parameters.</span></span>

<span data-ttu-id="b1351-112">[Aliases de cmdlet](./cmdlet-aliases.md) este tópico descreve os aliases de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b1351-112">[Cmdlet Aliases](./cmdlet-aliases.md) This topic describes cmdlet aliases.</span></span>

<span data-ttu-id="b1351-113">[Resultado do cmdlet](./cmdlet-output.md) esta secção descreve o tipo de saída que podem devolver cmdlets e como definir e apresentar os objetos que são devolvidos por cmdlets.</span><span class="sxs-lookup"><span data-stu-id="b1351-113">[Cmdlet Output](./cmdlet-output.md) This section describes the type of output that cmdlets can return and how to define and display the objects that are returned by cmdlets.</span></span>

<span data-ttu-id="b1351-114">[Registar os Cmdlets](./modules-and-snap-ins.md) esta secção descreve como registar cmdlets com módulos e snap-ins.</span><span class="sxs-lookup"><span data-stu-id="b1351-114">[Registering Cmdlets](./modules-and-snap-ins.md) This section describes how to register cmdlets by using modules and snap-ins.</span></span>

<span data-ttu-id="b1351-115">[Pedir confirmação](./requesting-confirmation-from-cmdlets.md) esta secção descreve como cmdlets pedir confirmação de um utilizador antes de eles fazer uma alteração no sistema.</span><span class="sxs-lookup"><span data-stu-id="b1351-115">[Requesting Confirmation](./requesting-confirmation-from-cmdlets.md) This section describes how cmdlets request confirmation from a user before they make a change to the system.</span></span>

<span data-ttu-id="b1351-116">[Relatório de erros do Windows PowerShell](./error-reporting-concepts.md) esta secção descreve como cmdlets para relatar erros de terminação e erros de não terminação, além de descrever como interpretar os registos de erro.</span><span class="sxs-lookup"><span data-stu-id="b1351-116">[Windows PowerShell Error Reporting](./error-reporting-concepts.md) This section describes how cmdlets report terminating errors and non-terminating errors, and it describes how to interpret error records.</span></span>

<span data-ttu-id="b1351-117">[Tarefas em segundo plano](./background-jobs.md) este tópico descreve como os cmdlets pode realizar seu trabalho nas tarefas em segundo plano que não interferem com os comandos que estão em execução na sessão atual.</span><span class="sxs-lookup"><span data-stu-id="b1351-117">[Background Jobs](./background-jobs.md) This topic describes how cmdlets can perform their work within background jobs that do not interfere with the commands that are executing in the current session.</span></span>

<span data-ttu-id="b1351-118">[Invocar Cmdlets e Scripts dentro de um Cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) este tópico descreve como cmdlets pode invocar a outros cmdlets e scripts a partir da respetiva entrada métodos de processamento.</span><span class="sxs-lookup"><span data-stu-id="b1351-118">[Invoking Cmdlets and Scripts Within a Cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) This topic describes how cmdlets can invoke other cmdlets and scripts from within their input processing methods.</span></span>

<span data-ttu-id="b1351-119">[Cmdlet define](./cmdlet-sets.md) este tópico descreve a utilização de base classes para criar conjuntos de cmdlets.</span><span class="sxs-lookup"><span data-stu-id="b1351-119">[Cmdlet Sets](./cmdlet-sets.md) This topic describes using base classes to create sets of cmdlets.</span></span>

<span data-ttu-id="b1351-120">[Estado de sessão do Windows PowerShell](./windows-powershell-session-state.md) este tópico descreve o estado de sessão do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b1351-120">[Windows PowerShell Session State](./windows-powershell-session-state.md) This topic describes Windows PowerShell session state.</span></span>
