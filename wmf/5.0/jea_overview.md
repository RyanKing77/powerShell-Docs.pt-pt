---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: 4e0c1638bf10e57580a463c46595ac9bc142a5b4
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="just-enough-administration-jea"></a>Administração just Enough (JEA)
Apenas suficiente administração é uma funcionalidade nova do WMF 5.0 que permite a administração baseada em funções através de comunicação remota do PowerShell.  Se expande a infraestrutura existente do ponto final restrita, permitindo não administradores executar comandos específicos, scripts e executáveis como um administrador.  Isto permite-lhe reduzir o número de administradores completos no seu ambiente e melhorar a segurança.  JEA funciona para tudo o que gere através do PowerShell; se pode gerir algo com o PowerShell, o JEA pode ajudar a fazer, por isso, forma mais segura.  Para ver apenas suficiente Administração detalhada, consulte o [experiência guia](http://aka.ms/JEA).

Ao contrário dos pontos finais restrita antigos, JEA é poderosa e fácil de configurar.  Funções de utilizador no JEA podem ser granularly controladas, para restringir quais os conjuntos de parâmetros e valores podem ser fornecidos para um comando específico. Ações do utilizador são executadas no contexto de uma única conta virtual que tem os direitos para executar as ações de administrador.  Os comandos invocados pelo utilizador podem ser registados para as auditorias de segurança.

Funciona JEA, permitindo-lhe criar especial configurada restrita os pontos finais.  Estes pontos finais tem alguns características importantes:

1. Utilizadores ligados aos mesmos "Executar como" uma conta com privilégios Virtual que existe apenas durante a esta sessão remota.  Por predefinição, esta conta Virtual é um membro do grupo Administradores incorporado, bem como os administradores de domínio em controladores de domínio (Nota: estas permissões são configuráveis). Ao ligar-se como um utilizador e a ser executado como um utilizador diferente, com privilégios, pode permitir que utilizadores não privilegiados efetuar tarefas administrativas específicas sem conceder direitos administrativos nos seus sistemas.
2. O ponto final está a ser bloqueado.  Isto significa que a execução do PowerShell no modo de idioma não.  Apenas os comandos específicos, scripts e executáveis estão visíveis para o utilizador.
3. Os utilizadores de diferentes ligados são apresentados com um conjunto diferente de capacidades com base na associação de grupo.  Pode fornecer diferentes funções funcionalidades diferentes, o ponto final do mesmo.

