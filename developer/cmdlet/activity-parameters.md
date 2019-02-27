---
title: Parâmetros de atividades | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e4e0cf6-19e0-44b8-8b40-d6f6075276cf
caps.latest.revision: 5
ms.openlocfilehash: 32e2b8acf33bc733c5e4cab94a721076ff46225d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849092"
---
# <a name="activity-parameters"></a><span data-ttu-id="9dc6b-102">Parâmetros de Atividades</span><span class="sxs-lookup"><span data-stu-id="9dc6b-102">Activity Parameters</span></span>

<span data-ttu-id="9dc6b-103">A tabela seguinte lista os nomes recomendados e a funcionalidade para parâmetros de atividades.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-103">The following table lists the recommended names and functionality for activity parameters.</span></span>

<span data-ttu-id="9dc6b-104">Acrescente o tipo de dados: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9dc6b-104">Append Data type: SwitchParameter</span></span>

<span data-ttu-id="9dc6b-105">Implemente este parâmetro para que o utilizador pode adicionar conteúdo ao final de um recurso quando o parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-105">Implement this parameter so that the user can add content to the end of a resource when the parameter is specified.</span></span>

<span data-ttu-id="9dc6b-106">Tipo de dados de CaseSensitive: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9dc6b-106">CaseSensitive Data type: SwitchParameter</span></span>

<span data-ttu-id="9dc6b-107">Implemente este parâmetro para que o utilizador pode exigir a maiúsculas e minúsculas, quando o parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-107">Implement this parameter so the user can require case sensitivity when the parameter is specified.</span></span>

<span data-ttu-id="9dc6b-108">Tipo de dados de comando: Cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="9dc6b-108">Command Data type: String</span></span>

<span data-ttu-id="9dc6b-109">Implemente este parâmetro para que o utilizador pode especificar uma cadeia de caracteres de comando para executar.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-109">Implement this parameter so the user can specify a command string to run.</span></span>

<span data-ttu-id="9dc6b-110">Tipo de dados de CompatibleVersion: Objeto de ter</span><span class="sxs-lookup"><span data-stu-id="9dc6b-110">CompatibleVersion Data type: System.Version object</span></span>

<span data-ttu-id="9dc6b-111">Implemente este parâmetro para que o utilizador pode especificar a semântica que o cmdlet tem de ser compatível com para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-111">Implement this parameter so the user can specify the semantics that the cmdlet must be compatible with for compatibility with previous versions.</span></span>

<span data-ttu-id="9dc6b-112">Comprima o tipo de dados: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9dc6b-112">Compress Data type: SwitchParameter</span></span>

<span data-ttu-id="9dc6b-113">Implemente este parâmetro para que a compressão de dados é utilizada quando o parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-113">Implement this parameter so that data compression is used when the parameter is specified.</span></span>

<span data-ttu-id="9dc6b-114">Comprima o tipo de dados: Palavra-chave</span><span class="sxs-lookup"><span data-stu-id="9dc6b-114">Compress Data type: Keyword</span></span>

<span data-ttu-id="9dc6b-115">Implemente este parâmetro para que o utilizador pode especificar o algoritmo a utilizar para compressão de dados.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-115">Implement this parameter so that the user can specify the algorithm to use for data compression.</span></span>

<span data-ttu-id="9dc6b-116">Tipo de dados contínuos: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9dc6b-116">Continuous Data type: SwitchParameter</span></span>

<span data-ttu-id="9dc6b-117">Implemente este parâmetro, de modo a que os dados são processados até que o usuário termina o cmdlet quando o parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-117">Implement this parameter so that data is processed until the user terminates the cmdlet when the parameter is specified.</span></span> <span data-ttu-id="9dc6b-118">Se o parâmetro não for especificado, o cmdlet processa uma quantidade predefinida de dados e, em seguida, termina a operação.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-118">If the parameter is not specified, the cmdlet processes a predefined amount of data and then terminates the operation.</span></span>

<span data-ttu-id="9dc6b-119">Crie tipo de dados: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9dc6b-119">Create Data type: SwitchParameter</span></span>

<span data-ttu-id="9dc6b-120">Implemente este parâmetro para indicar que um recurso é criado se ainda não existir quando é especificado o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-120">Implement this parameter to indicate that a resource is created if one does not already exist when the parameter is specified.</span></span>

<span data-ttu-id="9dc6b-121">Elimine tipo de dados: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9dc6b-121">Delete Data type: SwitchParameter</span></span>

<span data-ttu-id="9dc6b-122">Implemente este parâmetro, de modo a que os recursos são eliminados quando o cmdlet concluiu sua operação quando o parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-122">Implement this parameter so that resources are deleted when the cmdlet has completed its operation when the parameter is specified.</span></span>

<span data-ttu-id="9dc6b-123">Drenar o tipo de dados: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9dc6b-123">Drain Data type: SwitchParameter</span></span>

<span data-ttu-id="9dc6b-124">Implemente este parâmetro para indicar que os itens de trabalho pendentes são processados antes do cmdlet processa novos dados, quando o parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-124">Implement this parameter to indicate that outstanding work items are processed before the cmdlet processes new data when the parameter is specified.</span></span> <span data-ttu-id="9dc6b-125">Se o parâmetro não for especificado, os itens de trabalho são processados imediatamente.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-125">If the parameter is not specified, the work items are processed immediately.</span></span>

<span data-ttu-id="9dc6b-126">Apagar o tipo de dados: Int32</span><span class="sxs-lookup"><span data-stu-id="9dc6b-126">Erase Data type: Int32</span></span>

<span data-ttu-id="9dc6b-127">Implemente este parâmetro para que o utilizador pode especificar o número de vezes que um recurso é apagado antes de ser eliminado.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-127">Implement this parameter so that the user can specify the number of times a resource is erased before it is deleted.</span></span>

<span data-ttu-id="9dc6b-128">Tipo de dados de nível de erro: Int32</span><span class="sxs-lookup"><span data-stu-id="9dc6b-128">ErrorLevel Data type: Int32</span></span>

<span data-ttu-id="9dc6b-129">Implemente este parâmetro para que o utilizador pode especificar o nível de erros ao relatório.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-129">Implement this parameter so that the user can specify the level of errors to report.</span></span>

<span data-ttu-id="9dc6b-130">Exclua o tipo de dados: String[]</span><span class="sxs-lookup"><span data-stu-id="9dc6b-130">Exclude Data type: String[]</span></span>

<span data-ttu-id="9dc6b-131">Implemente este parâmetro para que o usuário pode excluir algo de uma atividade.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-131">Implement this parameter so that the user can exclude something from an activity.</span></span> <span data-ttu-id="9dc6b-132">Para obter mais informações sobre como utilizar filtros de entrada, consulte [parâmetros de filtro de entrada](./input-filter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="9dc6b-132">For more information about how to use input filters, see [Input Filter Parameters](./input-filter-parameters.md).</span></span>

<span data-ttu-id="9dc6b-133">Tipo de dados de filtro: Palavra-chave</span><span class="sxs-lookup"><span data-stu-id="9dc6b-133">Filter Data type: Keyword</span></span>

<span data-ttu-id="9dc6b-134">Implemente este parâmetro para que o utilizador pode especificar um filtro que seleciona os recursos no qual executar a ação de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-134">Implement this parameter so that the user can specify a filter that selects the resources upon which to perform the cmdlet action.</span></span> <span data-ttu-id="9dc6b-135">Para obter mais informações sobre como utilizar filtros de entrada, consulte [parâmetros de filtro de entrada](./input-filter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="9dc6b-135">For more information about how to use input filters, see [Input Filter Parameters](./input-filter-parameters.md).</span></span>

<span data-ttu-id="9dc6b-136">Siga o tipo de dados: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9dc6b-136">Follow Data type: SwitchParameter</span></span>

<span data-ttu-id="9dc6b-137">Implemente este parâmetro, de modo a que o progresso é controlado quando o parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-137">Implement this parameter so that progress is tracked when the parameter is specified.</span></span>

<span data-ttu-id="9dc6b-138">Força o tipo de dados: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9dc6b-138">Force Data type: SwitchParameter</span></span>

<span data-ttu-id="9dc6b-139">Implemente este parâmetro para indicar que o usuário pode executar uma ação, mesmo que restrições são encontradas quando o parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-139">Implement this parameter to indicate that the user can perform an action even if restrictions are encountered when the parameter is specified.</span></span> <span data-ttu-id="9dc6b-140">O parâmetro não permite a segurança ser comprometido.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-140">The parameter does not allow security to be compromised.</span></span> <span data-ttu-id="9dc6b-141">Por exemplo, este parâmetro permite que um utilizador substituir um ficheiro só de leitura.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-141">For example, this parameter lets a user overwrite a read-only file.</span></span>

<span data-ttu-id="9dc6b-142">Inclua o tipo de dados: String[]</span><span class="sxs-lookup"><span data-stu-id="9dc6b-142">Include Data type: String[]</span></span>

<span data-ttu-id="9dc6b-143">Implemente este parâmetro para que o utilizador pode incluir algo numa atividade.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-143">Implement this parameter so that the user can include something in an activity.</span></span> <span data-ttu-id="9dc6b-144">Para obter mais informações sobre como utilizar filtros de entrada, consulte [parâmetros de filtro de entrada](./input-filter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="9dc6b-144">For more information about how to use input filters, see [Input Filter Parameters](./input-filter-parameters.md).</span></span>

<span data-ttu-id="9dc6b-145">Tipo de dados incrementais: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9dc6b-145">Incremental Data type: SwitchParameter</span></span>

<span data-ttu-id="9dc6b-146">Implemente este parâmetro para indicar que o processamento é efetuado incrementalmente quando o parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-146">Implement this parameter to indicate that processing is performed incrementally when the parameter is specified.</span></span> <span data-ttu-id="9dc6b-147">Por exemplo, este parâmetro permite que um utilizador efetuar cópias de segurança incrementais de que fazer backup de arquivos apenas desde a última cópia de segurança.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-147">For example, this parameter lets a user perform incremental backups that back up files only since the last backup.</span></span>

<span data-ttu-id="9dc6b-148">Tipo de dados de InputObject: Objeto</span><span class="sxs-lookup"><span data-stu-id="9dc6b-148">InputObject Data type: Object</span></span>

<span data-ttu-id="9dc6b-149">Implemente este parâmetro quando o cmdlet pega a entrada de outros cmdlets.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-149">Implement this parameter when the cmdlet takes input from other cmdlets.</span></span> <span data-ttu-id="9dc6b-150">Quando define um `InputObject` parâmetro, sempre especificar o `ValueFromPipeline` palavra-chave quando declara a **parâmetro** atributo.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-150">When you define an `InputObject` parameter, always specify the `ValueFromPipeline` keyword when you declare the **Parameter** attribute.</span></span> <span data-ttu-id="9dc6b-151">Para obter mais informações sobre como utilizar filtros de entrada, consulte [parâmetros de filtro de entrada](./input-filter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="9dc6b-151">For more information about using input filters, see [Input Filter Parameters](./input-filter-parameters.md).</span></span>

<span data-ttu-id="9dc6b-152">Insira o tipo de dados: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9dc6b-152">Insert Data type: SwitchParameter</span></span>

<span data-ttu-id="9dc6b-153">Implemente este parâmetro para que o cmdlet insere um item quando o parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-153">Implement this parameter so that the cmdlet inserts an item when the parameter is specified.</span></span>

<span data-ttu-id="9dc6b-154">Tipo de dados interativos: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9dc6b-154">Interactive Data type: SwitchParameter</span></span>

<span data-ttu-id="9dc6b-155">Implemente este parâmetro para que o cmdlet interativamente funciona com o utilizador de quando o parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-155">Implement this parameter so that the cmdlet works interactively with the user when the parameter is specified.</span></span>

<span data-ttu-id="9dc6b-156">Tipo de dados de intervalo: HashTable</span><span class="sxs-lookup"><span data-stu-id="9dc6b-156">Interval Data type: HashTable</span></span>

<span data-ttu-id="9dc6b-157">Implemente este parâmetro para que o utilizador pode especificar uma tabela de hash de palavras-chave que contém os valores.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-157">Implement this parameter so that the user can specify a hash table of keywords that contains the values.</span></span> <span data-ttu-id="9dc6b-158">O exemplo seguinte mostra os valores de exemplo para o `Interval` parâmetro: `-interval @{ResumeScan=15; Retry=3}`.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-158">The following example shows sample values for the `Interval` parameter: `-interval @{ResumeScan=15; Retry=3}`.</span></span>

<span data-ttu-id="9dc6b-159">Tipo de dados de registo: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9dc6b-159">Log Data type: SwitchParameter</span></span>

<span data-ttu-id="9dc6b-160">Implemente esta auditoria de parâmetro as ações do cmdlet, quando o parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-160">Implement this parameter audit the actions of the cmdlet when the parameter is specified.</span></span>

<span data-ttu-id="9dc6b-161">Tipo de dados de NoClobber: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9dc6b-161">NoClobber Data type: SwitchParameter</span></span>

<span data-ttu-id="9dc6b-162">Implemente este parâmetro para que o recurso não será substituído quando o parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-162">Implement this parameter so that the resource will not be overwritten when the parameter is specified.</span></span> <span data-ttu-id="9dc6b-163">Este parâmetro aplica-se geralmente aos cmdlets de criar novos objetos para que eles podem ser impedidos de substituição de objetos existentes com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-163">This parameter generally applies to cmdlets that create new objects so that they can be prevented from overwriting existing objects with the same name.</span></span>

<span data-ttu-id="9dc6b-164">Notificar o tipo de dados: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9dc6b-164">Notify Data type: SwitchParameter</span></span>

<span data-ttu-id="9dc6b-165">Implemente este parâmetro para que o utilizador será notificado que a atividade foi concluída quando o parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-165">Implement this parameter so that the user will be notified that the activity is complete when the parameter is specified.</span></span>

<span data-ttu-id="9dc6b-166">Tipo de dados de NotifyAddress: Endereço de E-mail</span><span class="sxs-lookup"><span data-stu-id="9dc6b-166">NotifyAddress Data type: E-mail address</span></span>

<span data-ttu-id="9dc6b-167">Implementar este parâmetro para que o utilizador pode especificar o endereço de e-mail a utilizar para enviar uma notificação quando o `Notify` parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-167">Implement this parameter so that the user can specify the e-mail address to use to send a notification when the `Notify` parameter is specified.</span></span>

<span data-ttu-id="9dc6b-168">Substitua o tipo de dados: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9dc6b-168">Overwrite Data type: SwitchParameter</span></span>

<span data-ttu-id="9dc6b-169">Implemente este parâmetro para que o cmdlet substitui qualquer dado existente quando o parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-169">Implement this parameter so that the cmdlet overwrites any existing data when the parameter is specified.</span></span>

<span data-ttu-id="9dc6b-170">Tipo de dados de linha de comandos: Cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="9dc6b-170">Prompt Data type: String</span></span>

<span data-ttu-id="9dc6b-171">Implemente este parâmetro para que o utilizador pode especificar uma linha de comandos para o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-171">Implement this parameter so that the user can specify a prompt for the cmdlet.</span></span>

<span data-ttu-id="9dc6b-172">Tipo de dados silencioso: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9dc6b-172">Quiet Data type: SwitchParameter</span></span>

<span data-ttu-id="9dc6b-173">Implemente este parâmetro para que o cmdlet suprime os comentários dos utilizadores durante suas ações quando é especificado o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-173">Implement this parameter so that the cmdlet suppresses user feedback during its actions when the parameter is specified.</span></span>

<span data-ttu-id="9dc6b-174">Recurse o tipo de dados: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9dc6b-174">Recurse Data type: SwitchParameter</span></span>

<span data-ttu-id="9dc6b-175">Implemente este parâmetro para que o cmdlet recursivamente executa suas ações nos recursos quando o parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-175">Implement this parameter so that the cmdlet recursively performs its actions on resources when the parameter is specified.</span></span>

<span data-ttu-id="9dc6b-176">Repare o tipo de dados: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9dc6b-176">Repair Data type: SwitchParameter</span></span>

<span data-ttu-id="9dc6b-177">Implemente este parâmetro para que o cmdlet irá tentar corrigir algo a partir de um estado danificado quando o parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-177">Implement this parameter so that the cmdlet will attempt to correct something from a broken state when the parameter is specified.</span></span>

<span data-ttu-id="9dc6b-178">Tipo de dados de RepairString: Cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="9dc6b-178">RepairString Data type: String</span></span>

<span data-ttu-id="9dc6b-179">Implementar este parâmetro para que o utilizador pode especificar uma cadeia de caracteres a utilizar quando o `Repair` parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-179">Implement this parameter so that the user can specify a string to use when the `Repair` parameter is specified.</span></span>

<span data-ttu-id="9dc6b-180">Repita o tipo de dados: Int32</span><span class="sxs-lookup"><span data-stu-id="9dc6b-180">Retry Data type: Int32</span></span>

<span data-ttu-id="9dc6b-181">Implemente este parâmetro para que o utilizador pode especificar o número de vezes que o cmdlet irá tentar uma ação.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-181">Implement this parameter so the user can specify the number of times the cmdlet will attempt an action.</span></span>

<span data-ttu-id="9dc6b-182">Selecione o tipo de dados: Matriz de palavra-chave</span><span class="sxs-lookup"><span data-stu-id="9dc6b-182">Select Data type: Keyword array</span></span>

<span data-ttu-id="9dc6b-183">Implemente este parâmetro para que o utilizador pode especificar uma matriz de tipos de itens.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-183">Implement this parameter so that the user can specify an array of the types of items.</span></span>

<span data-ttu-id="9dc6b-184">Tipo de dados do Stream: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9dc6b-184">Stream Data type: SwitchParameter</span></span>

<span data-ttu-id="9dc6b-185">Implemente este parâmetro para que o utilizador pode transmitir vários objetos de resultado através do pipeline, quando o parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-185">Implement this parameter so the user can stream multiple output objects through the pipeline when the parameter is specified.</span></span>

<span data-ttu-id="9dc6b-186">Tipo de dados Strict: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9dc6b-186">Strict Data type: SwitchParameter</span></span>

<span data-ttu-id="9dc6b-187">Implemente este parâmetro para que todos os erros são tratados como erros de terminação quando o parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-187">Implement this parameter so that all errors are handled as terminating errors when the parameter is specified.</span></span>

<span data-ttu-id="9dc6b-188">Tipo de dados de TempLocation: Cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="9dc6b-188">TempLocation Data type: String</span></span>

<span data-ttu-id="9dc6b-189">Implemente este parâmetro para que o utilizador pode especificar a localização de dados temporárias que são utilizados durante a operação do cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-189">Implement this parameter so the user can specify the location of temporary data that is used during the operation of the cmdlet.</span></span>

<span data-ttu-id="9dc6b-190">Tipo de dados de tempo limite: Int32</span><span class="sxs-lookup"><span data-stu-id="9dc6b-190">Timeout Data type: Int32</span></span>

<span data-ttu-id="9dc6b-191">Implemente este parâmetro para que o utilizador pode especificar o intervalo de tempo limite (em milissegundos).</span><span class="sxs-lookup"><span data-stu-id="9dc6b-191">Implement this parameter so that the user can specify the timeout interval (in milliseconds).</span></span>

<span data-ttu-id="9dc6b-192">Truncar o tipo de dados: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9dc6b-192">Truncate Data type: SwitchParameter</span></span>

<span data-ttu-id="9dc6b-193">Implemente este parâmetro para que o cmdlet irá truncar suas ações quando é especificado o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-193">Implement this parameter so that the cmdlet will truncate its actions when the parameter is specified.</span></span> <span data-ttu-id="9dc6b-194">Se o parâmetro não for especificado, o cmdlet executa outra ação.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-194">If the parameter is not specified, the cmdlet performs another action.</span></span>

<span data-ttu-id="9dc6b-195">Verifique se o tipo de dados: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9dc6b-195">Verify Data type: SwitchParameter</span></span>

<span data-ttu-id="9dc6b-196">Implemente este parâmetro para que o cmdlet irá testar para determinar se uma ação tenha ocorrido quando o parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-196">Implement this parameter so that the cmdlet will test to determine whether an action has occurred when the parameter is specified.</span></span>

<span data-ttu-id="9dc6b-197">Aguarde o tipo de dados: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="9dc6b-197">Wait Data type: SwitchParameter</span></span>

<span data-ttu-id="9dc6b-198">Implemente este parâmetro para que o cmdlet irá aguardar pela intervenção do utilizador antes de continuar quando o parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-198">Implement this parameter so that the cmdlet will wait for user input before continuing when the parameter is specified.</span></span>

<span data-ttu-id="9dc6b-199">Tipo de dados de tempo de espera: Int32</span><span class="sxs-lookup"><span data-stu-id="9dc6b-199">WaitTime Data type: Int32</span></span>

<span data-ttu-id="9dc6b-200">Implementar este parâmetro para que o utilizador pode especificar a duração (em segundos) que o cmdlet irá esperar para o utilizador de entrada quando a `Wait` parâmetro for especificado.</span><span class="sxs-lookup"><span data-stu-id="9dc6b-200">Implement this parameter so that the user can specify the duration (in seconds) that the cmdlet will wait for user input when the `Wait` parameter is specified.</span></span>

## <a name="see-also"></a><span data-ttu-id="9dc6b-201">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="9dc6b-201">See Also</span></span>

[<span data-ttu-id="9dc6b-202">Parâmetros do cmdlet</span><span class="sxs-lookup"><span data-stu-id="9dc6b-202">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="9dc6b-203">Escrever um Cmdlet do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9dc6b-203">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="9dc6b-204">SDK do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9dc6b-204">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
