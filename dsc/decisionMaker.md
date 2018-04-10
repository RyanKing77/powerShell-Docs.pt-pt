---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Descrição Geral do Desired State Configuration para Decisores
ms.openlocfilehash: 8b410420ef30b066a32864a0d08a12a8485eaa4b
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a>Descrição Geral do Desired State Configuration para Decisores

Este documento descreve as vantagens de negócio da utilização pretendida Estado Configuration (DSC) do PowerShell. Não é um guia técnico.

## <a name="what-is-desired-state-configuration"></a>O que é a configuração do estado pretendido?

Configuração de estado pretendido do Windows PowerShell (DSC) é uma plataforma de gestão de configuração incorporada no Windows que é baseada nas normas de abertura. DSC é flexível o suficiente para funcionar de forma fiável e consistentemente em cada fase do ciclo de vida de implementação (desenvolvimento, teste, pré-produção, produção), bem como durante Escalamento horizontal.

DSC centra-se "[configurações](https://msdn.microsoft.com/powershell/dsc/configurations)".
Uma configuração é um documento de fácil leitura que descreve um ambiente efetuado cópias de segurança de computadores "(nós) com características específicas.
Estas características podem ser tão simples como garantir que uma funcionalidade específica do Windows está ativado ou como complexos como implementar o SharePoint.

DSC tem também de monitorização e relatórios incorporados.
Se um sistema já não for conforme, DSC pode emitir um alerta e atuar para corrigir o sistema.

## <a name="benefits-of-using-desired-state-configuration"></a>Vantagens da utilização da configuração do estado pretendido

Configurações foram concebidas para ser facilmente ler, armazenados e atualizado.
Configurações de declarar que os dispositivos de destino de Estado devem ser, em vez de escrever instruções sobre como colocar esse Estado.
Isto torna muito menos dispendiosos de saber mais, adotar, implementar e manter a configuração através de DSC.

Criação de configurações significa que os passos de implementação complexas são capturados como uma "origem única de truth" numa única localização.
Isto torna muito menos propensas ao erro repetidas implementações de um conjunto específico de computadores.
Por sua vez, tornando mais rápidas e mais fiáveis de implementações que permite uma rápido resposta mais rápida em implementações complexas.

Configurações também são partilhável através de [galeria do PowerShell](https://powershellgallery.com) significado cenários comuns e melhores práticas poderá já existir para o trabalho tem de terminar.


## <a name="desired-state-configuration-and-devops"></a>Configuração do estado pretendido e DevOps

[DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) é uma combinação de pessoas, processos e ferramentas que permitem para implementação rápida e iteração concentra-se em permitir o valor para os utilizadores finais se internos ou externos.
DSC foi concebido com DevOps em mente.
Ter uma configuração única definir um ambiente significa que os programadores podem codificar os respetivos requisitos para uma configuração, verifique que a configuração para o controlo de origem e equipas de operações podem facilmente implementar código sem ter de passar por propensas ao erro processos manuais.

Configurações são também [condicionada por dados](https://msdn.microsoft.com/powershell/dsc/configdata), que torna mais fácil para as equipas de ops identificar e alterar ambientes sem a intervenção do programador.

## <a name="desired-state-configuration-on--and-off-premises"></a>Configuração do estado pretendido e desativar-no local

DSC pode ser utilizado para gerir implementações no local e fora do local.
Para soluções no local, DSC tem um [do servidor de solicitação](https://msdn.microsoft.com/powershell/dsc/pullserver) que podem ser utilizados para centralizar a gestão das máquinas e comunicar no respetivo estado.
Para soluções de nuvem, DSC é utilizável onde quer que Windows utilizável.
Também existem ofertas específicas do Azure incorporado numa configuração de estado pretendido, tais como [da automatização do Azure](https://azure.microsoft.com/en-us/documentation/services/automation/), que centraliza reporting do DSC.

## <a name="dsc-and-compatibility"></a>Compatibilidade e DSC

Apesar de DSC foi introduzido no Windows Server 2012 R2, está disponível para sistemas operativos de nível inferior através do pacote do Windows Management Framework (WMF).
Podem encontrar mais informações sobre o WMF no [home page do PowerShell](https://msdn.microsoft.com/en-us/powershell/).

DSC também pode ser utilizado para gerir o Linux. Para obter mais informações, consulte [introdução DSC para Linux](https://msdn.microsoft.com/en-us/powershell/dsc/lnxgettingstarted).