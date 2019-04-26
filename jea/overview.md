---
ms.date: 06/12/2017
keywords: jea, powershell, segurança
title: Descrição geral da administração Just Enough
ms.openlocfilehash: c097838fb25a63d42502eebf751c64c537bdd077
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084917"
---
# <a name="just-enough-administration"></a>Administração Apenas Suficiente

Just Enough Administration (JEA) é uma tecnologia de segurança que permite a administração delegada para tudo o que pode ser gerenciada com o PowerShell.
Com JEA, pode:

- **Reduzir o número de administradores nos seus computadores** ao tirar partidas de contas virtuais ou grupo de contas de serviço que efetuar ações privilegiadas em nome do usuários regulares de geridas.
- **Limitar o que os utilizadores podem fazer** , especificando quais cmdlets, funções e comandos externos podem executar.
- **Compreender melhor o que os usuários estão fazendo** com transcrições e registos que mostram-lhe exatamente os comandos que um utilizador durante a sessão.

**Por que motivo é importante?**

Contas com privilégios bastante elevados utilizadas para administrar servidores representam um grave risco de segurança.
Deve um invasor comprometer uma destas contas, elas podem iniciar [lateral ataques](http://aka.ms/pth) na sua organização.
Cada conta comprometidos por eles pode lhes dar acesso nem mesmo mais contas e recursos, colocando-os um passo mais perto de roubo de segredos da empresa, iniciar um ataque de negação de serviço e muito mais.

Nem sempre é fácil remover os privilégios administrativos, tanto.
Considere o cenário comum onde a função de DNS é instalada no mesmo computador que o controlador de domínio do Active Directory.
Os administradores DNS requerem privilégios de administrador local para corrigir problemas com o servidor DNS, mas para isso para que tenha para torná-los membros do grupo de segurança "Admins do domínio" com privilégios elevados.
Essa abordagem efetivamente dá controle aos administradores de DNS ao longo do seu domínio inteiro e o acesso a todos os recursos nessa máquina.

JEA ajuda a resolver esse problema, ajudando a adotar o princípio dos *menor privilégio*.
Com JEA, pode configurar um ponto de final de gestão para administradores DNS que lhes concede acesso a todos os comandos do PowerShell de que precisam para fazer seu trabalho, mas nada mais.
Isso significa que pode fornecer o acesso apropriado para reparar um cache do inviabilizada DNS ou reiniciar o servidor DNS sem fornecer acidentalmente direitos do Active Directory ou para procurar o sistema de ficheiros ou executar scripts potencialmente perigosas.
Melhor ainda, quando a sessão JEA está configurada para utilizar contas temporárias de virtual com privilégios, os administradores DNS podem ligar-se para o servidor utilizando *não-administrador* credenciais e ainda conseguir executar comandos que exigem, normalmente, privilégios de administrador.
Esta capacidade permite-lhe remover os utilizadores de funções de administrador de domínio local/amplamente com privilégios e em vez disso, controlar cuidadosamente o que são capazes de fazer em cada máquina.

## <a name="get-started-with-jea"></a>Introdução ao JEA

Pode começar a utilizar a JEA hoje mesmo em qualquer máquina com o Windows Server 2016 ou Windows 10.
Também pode executar JEA em sistemas de operativos mais antigos com uma atualização do Windows Management Framework.
Para saber mais sobre os requisitos para utilizar a JEA e para saber como criar, utilizar e um ponto final JEA de auditoria, consulte os tópicos seguintes:

- [Pré-requisitos](prerequisites.md) -explica como configurar o ambiente para utilizar a JEA.
- [Funcionalidades de função](role-capabilities.md) -explica como criar funções que determinam o que um utilizador tem permissão para fazer numa sessão JEA.
- [Configurações de sessão](session-configurations.md) -explica como configurar pontos finais JEA que mapeiam os utilizadores a funções e definir a identidade JEA
- [Registar a JEA](register-jea.md) - criar um ponto final JEA e disponibilizá-la para os utilizadores liguem aos.
- [Utilizar a JEA](using-jea.md) -aprender as várias formas que pode utilizar a JEA.
- [Considerações de segurança](security-considerations.md) -rever as melhores práticas de segurança e as implicações de opções de configuração JEA.
- [Auditar e criar relatórios na JEA](audit-and-report.md) -Aprenda a auditoria e relatórios sobre pontos finais JEA.

## <a name="samples-and-dsc-resource"></a>Exemplos e recursos de DSC

Configurações de JEA de exemplo e o recurso de DSC de JEA podem ser encontrados na [repositório do GitHub de JEA](https://github.com/PowerShell/JEA).