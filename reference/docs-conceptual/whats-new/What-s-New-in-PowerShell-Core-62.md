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
# <a name="whats-new-in-powershell-core-62"></a>Quais são as novidades no PowerShell Core 6.2

Segue-se uma seleção de alguns dos principais novos recursos e alterações que foram introduzidas no PowerShell Core 6.2.

Também há **toneladas** de "aborrecida" que tornam o PowerShell mais rápido e mais estável (além de muitas e várias correções de erros)!
Para obter uma lista completa das alterações, confira nossos [registo de alterações no GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).

E embora o que chamamos de alguns nomes abaixo, obrigado a [todos os contribuintes da Comunidade](https://github.com/PowerShell/PowerShell/graphs/contributors) que possibilitado nesta versão.

## <a name="engine-updates-and-fixes"></a>Atualizações de mecanismos e correções

- Adicionar mensagens de aviso de cmdlet do PowerShell remoting Ativar/desativar ([#9203][])
- Correção para `FormatTable` regressão de desserialização remoto ([#9116][])
- Atualizar o baseado em tarefas `async` APIs adicionadas para o PowerShell para retornar um objeto de tarefa diretamente ([#9079][])
- Adicionar 5 `InvokeAsync` sobrecargas e `StopAsync` para o `PowerShell` tipo ([#8056][]) (obrigado @KirkMunro!)

## <a name="general-cmdlet-updates-and-fixes"></a>Geral Cmdlet atualizações e correções

- Ativar `SecureString` cmdlets para não-Windows-armazenando o texto simples ([#9199][])
- Adicionar a mensagem obsoleta `Send-MailMessage` ([#9178][])
- Corrigir `Restart-Computer` trabalhar `localhost` quando o WinRM não está presente ([#9160][])
- Tornar `Start-Job` lançar o erro de terminação quando PowerShell está sendo hospedado ([#9128][])
- Versão de atualização para `PowerShell.Native` e testes de hospedagem ([#8983][])

## <a name="breaking-changes"></a>Alterações Interruptivas

Corrija o comportamento de - NoEnumerate no Write-Output para ser consistente com o Windows PowerShell ([#9069][]) (obrigado @vexx32!)

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
