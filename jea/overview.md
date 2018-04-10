---
ms.date: 06/12/2017
author: rpsqrd
ms.topic: conceptual
keywords: jea, powershell, segurança
title: Descrição geral da administração Just Enough
ms.openlocfilehash: fd5b97b7a483908f10cec6460d4e803740f064a8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="just-enough-administration"></a>Administração Apenas Suficiente

Apenas suficiente administração (JEA) é uma tecnologia de segurança que permite delegado administração para tudo o que pode ser gerida com o PowerShell.
Com o JEA, pode:

- **Reduza o número de administradores no seu máquinas** por aproveitamento das contas virtuais ou grupo de contas de serviço que efetuar ações privilegiadas em nome dos utilizadores regulares geridas.
- **Limitar a que os utilizadores podem fazer** especificando os cmdlets, funções e comandos externos podem executar.
- **Compreender melhor a que os utilizadores estão a fazer** com os registos e transcrições que mostram-lhe exatamente comandos que um utilizador executado durante a sessão.

**Por que motivo é importante?**

As contas privilegiadas utilizadas para administrar os servidores apresentam um risco de segurança grave.
Deve um atacante comprometer uma destas contas, foi possível iniciar a [lateral ataques](http://aka.ms/pth) na sua organização.
Cada conta que possam comprometer pode conceder-lhes acesso ao mesmo mais contas e recursos, colocando-los próximos roubarem os segredos da empresa, iniciando um ataque denial of service e muito mais.

Não sempre é fácil remover os privilégios administrativos, quer.
Considere o cenário comum, onde a função de DNS é instalada no mesmo computador como o controlador de domínio do Active Directory.
Os administradores DNS requerem privilégios de administrador local para corrigir problemas com o servidor DNS, mas para o efeito, pelo que terá de se tornar membros do grupo de segurança "Admins do domínio" altamente privilegiado.
Esta abordagem proporciona eficazmente o controlo de administradores de DNS ao longo do seu domínio todo e acesso a todos os recursos em que a máquina.

JEA ajuda a resolver este problema, ajudando-o a adotar o princípio de *menor privilégio*.
Com o JEA, pode configurar um ponto final de gestão para administradores DNS que lhes concede acesso a todos os comandos do PowerShell que precisam para o trabalho feito, mas nada mais.
Isto significa que pode fornecer o acesso adequado para reparar a uma cache DNS nocivas ou reinicie o servidor DNS sem concedendo-lhes inadvertidamente de direitos do Active Directory ou para procurar o sistema de ficheiros ou executar scripts potencialmente perigosos.
Melhor ainda, quando a sessão JEA é configurada para utilizar temporárias virtuais as contas com privilégios, os administradores DNS podem ligar-se para o servidor utilizando *não admin* credenciais e continuará a poder executar comandos que geralmente necessitam privilégios de administrador.
Esta capacidade permite-lhe remover utilizadores de funções de administrador local/domínio amplamente com privilégios e em vez disso, controlar cuidadosamente o que são efetuar em cada máquina.

## <a name="get-started-with-jea"></a>Introdução ao JEA

Começar a utilizar atualmente o JEA em qualquer computador com o Windows Server 2016 ou o Windows 10.
Também pode executar JEA em sistemas operativos mais antigos com uma atualização do Windows Management Framework.
Para mais informações sobre os requisitos para utilizar o JEA e para saber como criar, utilizar e um ponto final JEA de auditoria, consulte os tópicos seguintes:

- [Pré-requisitos](prerequisites.md) -explica como configurar o ambiente para utilizar o JEA.
- [Capacidades de função](role-capabilities.md) -explica como criar funções que determinam a que um utilizador tem permissão para efetuar numa sessão JEA.
- [Configurações de sessão](session-configurations.md) -explica como configurar pontos finais JEA mapeiam os utilizadores a funções e defina a identidade JEA
- [Registar JEA](register-jea.md) - criar um ponto final JEA e disponibilizá-lo para os utilizadores liguem.
- [Utilizar JEA](using-jea.md) -aprender as várias formas, pode utilizar JEA.
- [Considerações de segurança](security-considerations.md) -rever as melhores práticas de segurança e as implicações JEA das opções de configuração.
- [Auditoria e elaborar relatórios sobre JEA](audit-and-report.md) -aprender a auditoria e elaborar relatórios sobre os pontos finais JEA.

## <a name="samples-and-dsc-resource"></a>Exemplos e recursos de DSC

Configurações de JEA de exemplo e os recursos de JEA DSC podem ser encontrados no [repositório do JEA GitHub](https://github.com/PowerShell/JEA).