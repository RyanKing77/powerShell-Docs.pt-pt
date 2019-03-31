---
title: Quais são as novidades no PowerShell Core 6.2
description: Novos recursos e alterações lançadas no PowerShell Core 6.2
ms.date: 03/28/2019
ms.openlocfilehash: 2224d23a244175059a705c07001e8ad8d6ab3aa0
ms.sourcegitcommit: 8dd4394cf867005a8b9ef0bb74b744c964fbc332
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/30/2019
ms.locfileid: "58750037"
---
# <a name="whats-new-in-powershell-core-62"></a><span data-ttu-id="7773b-103">Quais são as novidades no PowerShell Core 6.2</span><span class="sxs-lookup"><span data-stu-id="7773b-103">What's New in PowerShell Core 6.2</span></span>

<span data-ttu-id="7773b-104">Segue-se uma seleção de alguns dos principais novos recursos e alterações que foram introduzidas no PowerShell Core 6.2.</span><span class="sxs-lookup"><span data-stu-id="7773b-104">Below is a selection of some of the major new features and changes that have been introduced in PowerShell Core 6.2.</span></span>

<span data-ttu-id="7773b-105">Também há **toneladas** de "aborrecida" que tornam o PowerShell mais rápido e mais estável (além de muitas e várias correções de erros)!</span><span class="sxs-lookup"><span data-stu-id="7773b-105">There's also **tons** of "boring stuff" that make PowerShell faster and more stable (plus lots and lots of bug fixes)!</span></span>
<span data-ttu-id="7773b-106">Para obter uma lista completa das alterações, confira nossos [registo de alterações no GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span><span class="sxs-lookup"><span data-stu-id="7773b-106">For a full list of changes, check out our [changelog on GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span></span>

<span data-ttu-id="7773b-107">E embora o que chamamos de alguns nomes abaixo, obrigado a [todos os contribuintes da Comunidade](https://github.com/PowerShell/PowerShell/graphs/contributors) que possibilitado nesta versão.</span><span class="sxs-lookup"><span data-stu-id="7773b-107">And while we call out some names below, thank you to [all of the community contributors](https://github.com/PowerShell/PowerShell/graphs/contributors) that made this release possible.</span></span>

## <a name="engine-updates-and-fixes"></a><span data-ttu-id="7773b-108">Atualizações de mecanismos e correções</span><span class="sxs-lookup"><span data-stu-id="7773b-108">Engine Updates and Fixes</span></span>

- <span data-ttu-id="7773b-109">Adicionar mensagens de aviso de cmdlet do PowerShell remoting Ativar/desativar ([#9203][])</span><span class="sxs-lookup"><span data-stu-id="7773b-109">Add PowerShell remoting enable/disable cmdlet warning messages ([#9203][])</span></span>
- <span data-ttu-id="7773b-110">Correção para `FormatTable` regressão de desserialização remoto ([#9116][])</span><span class="sxs-lookup"><span data-stu-id="7773b-110">Fix for `FormatTable` remote deserialization regression ([#9116][])</span></span>
- <span data-ttu-id="7773b-111">Atualizar o baseado em tarefas `async` APIs adicionadas para o PowerShell para retornar um objeto de tarefa diretamente ([#9079][])</span><span class="sxs-lookup"><span data-stu-id="7773b-111">Update the task-based `async` APIs added to PowerShell to return a Task object directly ([#9079][])</span></span>
- <span data-ttu-id="7773b-112">Adicionar 5 `InvokeAsync` sobrecargas e `StopAsync` para o `PowerShell` tipo ([#8056][]) (obrigado @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="7773b-112">Add 5 `InvokeAsync` overloads and `StopAsync` to the `PowerShell` type ([#8056][]) (Thanks @KirkMunro!)</span></span>

## <a name="general-cmdlet-updates-and-fixes"></a><span data-ttu-id="7773b-113">Geral Cmdlet atualizações e correções</span><span class="sxs-lookup"><span data-stu-id="7773b-113">General Cmdlet Updates and Fixes</span></span>

- <span data-ttu-id="7773b-114">Ativar `SecureString` cmdlets para não-Windows-armazenando o texto simples ([#9199][])</span><span class="sxs-lookup"><span data-stu-id="7773b-114">Enable `SecureString` cmdlets for non-Windows by storing the plain text ([#9199][])</span></span>
- <span data-ttu-id="7773b-115">Adicionar a mensagem obsoleta `Send-MailMessage` ([#9178][])</span><span class="sxs-lookup"><span data-stu-id="7773b-115">Add Obsolete message to `Send-MailMessage` ([#9178][])</span></span>
- <span data-ttu-id="7773b-116">Corrigir `Restart-Computer` trabalhar `localhost` quando o WinRM não está presente ([#9160][])</span><span class="sxs-lookup"><span data-stu-id="7773b-116">Fix `Restart-Computer` to work on `localhost` when WinRM is not present ([#9160][])</span></span>
- <span data-ttu-id="7773b-117">Tornar `Start-Job` lançar o erro de terminação quando PowerShell está sendo hospedado ([#9128][])</span><span class="sxs-lookup"><span data-stu-id="7773b-117">Make `Start-Job` throw terminating error when PowerShell is being hosted ([#9128][])</span></span>
- <span data-ttu-id="7773b-118">Versão de atualização para `PowerShell.Native` e testes de hospedagem ([#8983][])</span><span class="sxs-lookup"><span data-stu-id="7773b-118">Update version for `PowerShell.Native` and hosting tests ([#8983][])</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="7773b-119">Alterações Interruptivas</span><span class="sxs-lookup"><span data-stu-id="7773b-119">Breaking Changes</span></span>

<span data-ttu-id="7773b-120">Corrija o comportamento de - NoEnumerate no Write-Output para ser consistente com o Windows PowerShell ([#9069][]) (obrigado @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="7773b-120">Fix -NoEnumerate behavior in Write-Output to be consistent with Windows PowerShell ([#9069][]) (Thanks @vexx32!)</span></span>

<!-- Link references -->
[#8056]: https://github.com/PowerShell/PowerShell/pull/8056
[#8983]: https://github.com/PowerShell/PowerShell/pull/8983
[#9069]: https://github.com/PowerShell/PowerShell/pull/9069
[#9079]: https://github.com/PowerShell/PowerShell/pull/9079
[#9116]: https://github.com/PowerShell/PowerShell/pull/9116
[#9128]: https://github.com/PowerShell/PowerShell/pull/9128
[#9160]: https://github.com/PowerShell/PowerShell/pull/9160
[#9178]: https://github.com/PowerShell/PowerShell/pull/9178
[#9199]: https://github.com/PowerShell/PowerShell/pull/9199
[#9203]: https://github.com/PowerShell/PowerShell/pull/9203
