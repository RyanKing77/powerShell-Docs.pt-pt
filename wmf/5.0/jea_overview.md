---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 0bc085588190f134c4a687c952509aa256b5f840
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085206"
---
# <a name="just-enough-administration-jea"></a>Administração JEA (Just Enough Administration)
Administração just Enough é um novo recurso do WMF 5.0, que permite a administração baseada em funções por meio de comunicação remota do PowerShell.  Ele estende a infra-estrutura existente do ponto de extremidade restrita, permitindo que os não-administradores executar comandos específicos, scripts e executáveis como administrador.  Isto permite-lhe reduzir o número de administradores totais no seu ambiente e melhorar a segurança.  JEA funciona para tudo que gere através do PowerShell; se pudesse gerenciar algo com o PowerShell, JEA pode ajudá-lo a fazer então com mais segurança.  Para obter uma visão detalhada de administração Just Enough, confira o [guia de experiência](http://aka.ms/JEA).

Ao contrário dos antigos pontos de extremidade restritos, o JEA é poderoso e fácil de configurar.  Capacidades dos utilizadores na JEA podem ser granularmente controladas, para baixo para restringir quais conjuntos de parâmetros e valores podem ser fornecidos para um comando específico. Ações do usuário são executadas no contexto de uma única conta virtual que tem os direitos para executar as ações de administrador.  Os comandos invocados pelo utilizador podem ser registados para auditorias de segurança.

JEA funciona ao permitir-lhe criar pontos de extremidade restritos especialmente configurado.  Estes pontos finais tem algumas características importantes:

1. Utilizadores ligados aos mesmos "Executar como" uma conta com privilégios Virtual existente apenas para a duração desta sessão remota.  Por predefinição, esta conta Virtual é membro do grupo Administradores incorporado, bem como administrador de domínio em controladores de domínio (Nota: estas permissões são configuráveis). Ao ligar-se como um utilizador e a ser executado como um usuário diferente, com privilégios, pode permitir que utilizadores sem privilégios executar tarefas administrativas específicas sem conceder direitos administrativos em seus sistemas.
2. O ponto final é bloqueado.  Isso significa que é executado de PowerShell no modo de idioma não.  Apenas os comandos específicos, scripts e executáveis são visíveis para o utilizador.
3. Os utilizadores diferentes ligados são apresentados com um conjunto diferente de recursos com base na associação de grupo.  Pode fornecer diferentes funções diferentes capacidades no mesmo ponto final.
