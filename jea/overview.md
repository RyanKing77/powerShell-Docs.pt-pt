---
ms.date: 07/10/2019
keywords: jea, powershell, segurança
title: Descrição geral da administração Just Enough
ms.openlocfilehash: 4b74e5be9558810748a8844a325c8213e1b3ebc9
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726646"
---
# <a name="just-enough-administration"></a>Administração Apenas Suficiente

Just Enough Administration (JEA) é uma tecnologia de segurança que permite a qualquer coisa geridos pelo PowerShell administração delegada. Com JEA, pode:

- **Reduzir o número de administradores nos seus computadores** utilizar contas virtuais ou contas de serviço gerida de grupo para efetuar ações privilegiadas em nome do usuários regulares.
- **Limitar o que os utilizadores podem fazer** , especificando quais cmdlets, funções e comandos externos podem executar.
- **Compreender melhor o que os usuários estão fazendo** com transcrições e registos que mostram-lhe exatamente os comandos que um utilizador durante a sessão.

**Por que motivo é importante JEA?**

Contas com privilégios bastante elevados utilizadas para administrar servidores representam um grave risco de segurança. Deve um invasor comprometer uma destas contas, elas podem iniciar [lateral ataques](https://aka.ms/pth) na sua organização. Cada conta comprometida dá acesso um invasor nem mesmo mais contas e recursos e os coloca um passo mais perto de roubo de segredos da empresa, iniciar um ataque de negação de serviço e muito mais.

Nem sempre é fácil remover os privilégios administrativos, tanto. Considere o cenário comum onde a função de DNS é instalada no mesmo computador que o controlador de domínio do Active Directory. Os administradores DNS requerem privilégios de administrador local para corrigir problemas com o servidor DNS. Mas para fazer isso, deve fazê-las membros de altamente privilegiados **Admins do domínio** grupo de segurança. Essa abordagem efetivamente dá controle aos administradores de DNS ao longo do seu domínio inteiro e o acesso a todos os recursos nessa máquina.

JEA resolve este problema através do princípio de **menor privilégio**. Com JEA, pode configurar um ponto de final de gestão para administradores DNS que lhes dá acesso apenas para os comandos do PowerShell que precisam para fazer seu trabalho. Isso significa que pode fornecer o acesso apropriado para reparar um cache do inviabilizada DNS ou reiniciar o servidor DNS sem fornecer acidentalmente direitos do Active Directory ou para procurar o sistema de ficheiros ou executar scripts potencialmente perigosas. Melhor ainda, quando a sessão JEA está configurada para utilizar contas temporárias de virtual com privilégios, os administradores DNS podem ligar-se para o servidor utilizando **não-administrador** credenciais e ainda execute comandos que exigem, normalmente, o administrador privilégios. JEA permite-lhe remover os utilizadores de funções de administrador de domínio/local amplamente com privilégios e controlar cuidadosamente o que podem fazer em cada máquina.

## <a name="next-steps"></a>Passos Seguintes

Para saber mais sobre os requisitos para utilizar a JEA, consulte a [pré-requisitos](prerequisites.md) artigo.

## <a name="samples-and-dsc-resource"></a>Exemplos e recursos de DSC

Configurações de JEA de exemplo e o recurso de DSC de JEA podem ser encontrados na [repositório do GitHub de JEA](https://github.com/PowerShell/JEA).
