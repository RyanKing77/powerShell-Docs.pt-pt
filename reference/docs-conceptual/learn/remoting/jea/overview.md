---
ms.date: 07/10/2019
keywords: Jea, PowerShell, segurança
title: Visão geral da administração apenas suficiente
ms.openlocfilehash: 4b74e5be9558810748a8844a325c8213e1b3ebc9
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017861"
---
# <a name="just-enough-administration"></a>Administração Apenas Suficiente

A JEA (administração suficiente) é uma tecnologia de segurança que permite a administração delegada para qualquer coisa gerenciada pelo PowerShell. Com o JEA, você pode:

- **Reduza o número de administradores em seus computadores** usando contas virtuais ou contas de serviço gerenciadas por grupo para executar ações privilegiadas em nome de usuários regulares.
- **Limite o que os usuários podem fazer** especificando quais cmdlets, funções e comandos externos eles podem executar.
- **Entenda melhor o que os usuários estão fazendo** com transcrições e logs que mostram exatamente quais comandos um usuário executou durante sua sessão.

**Por que o JEA é importante?**

Contas altamente privilegiadas usadas para administrar seus servidores apresentam um sério risco de segurança. Caso um invasor comprometa uma dessas contas, ele poderia iniciar [ataques laterais](https://aka.ms/pth) em toda a sua organização. Cada conta comprometida dá a um invasor acesso a ainda mais contas e recursos e os coloca um passo mais próximo de roubar os segredos da empresa, lançar um ataque de negação de serviço e muito mais.

Nem sempre é fácil remover privilégios administrativos. Considere o cenário comum em que a função DNS está instalada no mesmo computador que o controlador de Domínio do Active Directory. Os administradores de DNS exigem privilégios de administrador local para corrigir problemas com o servidor DNS. Mas, para fazer isso, você deve torná-los membros do grupo de segurança **Administradores de domínio** altamente privilegiados. Essa abordagem efetivamente fornece aos administradores de DNS o controle sobre todo o domínio e o acesso a todos os recursos nesse computador.

JEA resolve esse problema por meio do princípio de **privilégios mínimos**. Com o JEA, você pode configurar um ponto de extremidade de gerenciamento para administradores de DNS que concede acesso apenas aos comandos do PowerShell que eles precisam para realizar seu trabalho. Isso significa que você pode fornecer o acesso apropriado para reparar um cache DNS inviabilizada ou reiniciar o servidor DNS sem conceder a eles direitos de Active Directory, ou procurar o sistema de arquivos, ou executar scripts potencialmente perigosos. Melhor ainda, quando a sessão JEA é configurada para usar contas virtuais com privilégios temporários, os administradores de DNS podem se conectar ao servidor usando credenciais **não administrativas** e ainda executar comandos que normalmente exigem privilégios de administrador. O JEA permite que você remova usuários de funções de administrador de domínio/local com privilégios elevados e controle cuidadosamente o que eles podem fazer em cada computador.

## <a name="next-steps"></a>Passos Seguintes

Para saber mais sobre os requisitos para usar o JEA, consulte o artigo [pré-requisitos](prerequisites.md) .

## <a name="samples-and-dsc-resource"></a>Exemplos e recurso de DSC

As configurações de JEA de exemplo e o recurso de DSC JEA podem ser encontrados no [repositório GitHub do Jea](https://github.com/PowerShell/JEA).
