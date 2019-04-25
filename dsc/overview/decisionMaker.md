---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Descrição Geral do Desired State Configuration para Decisores
ms.openlocfilehash: ce554d4bb994d4b1816d9d9c24599e4ef0e1c593
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079596"
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a>Descrição Geral do Desired State Configuration para Decisores

Este documento descreve os benefícios empresariais da utilização do Windows PowerShell Desired State Configuration (DSC). Não é um guia técnico.

## <a name="what-is-desired-state-configuration"></a>O que é a Desired State Configuration?

PowerShell Desired State Configuration é uma plataforma de gestão de configuração integrada no Windows com base em padrões abertos. DSC é flexível o suficiente para funcionar de maneira confiável e consistente em cada fase do ciclo de vida de implementação (desenvolvimento, teste, pré-produção, produção), bem como durante o Escalamento horizontal.

DSC centra-se em [configurações](../configurations/configurations.md).
Uma configuração é um documento de fácil leitura que descreve um ambiente composto de computadores ("nós") com características específicas.
Essas características podem ser tão simples como garantir que uma funcionalidade específica do Windows está ativado ou tão complexo como implantar o SharePoint.

DSC também tem monitorização e relatórios incorporados.
Se um sistema já não for compatível, DSC pode emitir um alerta e agir para corrigir o sistema.

## <a name="benefits-of-using-desired-state-configuration"></a>Vantagens da utilização do Desired State Configuration

Configurações foram concebidas para serem facilmente lidas, armazenados e atualizado.
Configurações de declarar que os dispositivos de destino de Estado devem ser, em vez de escrever instruções sobre como colocá-los com esse Estado.
Isso torna muito menos dispendiosa saber mais, adotar, implementar e manter a configuração através do DSC.

Criação de configurações, significa que os passos de implementação complexos são capturados como uma "única fonte de verdade" numa única localização.
Isso torna muito menos propenso a erros Implantações repetidas de um conjunto específico de máquinas.
Por sua vez, que torna as Implantações mais rápidas e confiáveis que permite um rápido retorno em implementações complexas.

As configurações também são partilhável através da [galeria do PowerShell](https://powershellgallery.com) que significa que cenários comuns e as melhores práticas poderá já existem para o trabalho que precisa ser feito.


## <a name="desired-state-configuration-and-devops"></a>Desired State Configuration e DevOps

DSC foi projetado tendo [DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) em mente, uma combinação de pessoas, processos e ferramentas que permitem a implementação rápida e de iteração focada no fornecimento de valor para os utilizadores finais se internos ou externos.
Ter uma única configuração definem um meio de ambiente que os desenvolvedores pode codificar seus requisitos numa configuração, verifique que a configuração no controle de fonte e as equipas de operação pode facilmente implementar código sem a necessidade de passar por propenso a erros processos manuais.

As configurações são também [condicionada por dados](../configurations/configData.md), que torna mais fácil para o ops identificar e alterar os ambientes sem a intervenção do desenvolvedor.

## <a name="desired-state-configuration-on-premises-and-off-premises"></a>Desired State Configuration no local e fora do local
DSC pode ser utilizado para gerir implementações no local e externamente.
Para soluções no local, DSC tem um [servidor de solicitação](../pull-server/pullServer.md) que podem ser utilizados para centralizar o gerenciamento de máquinas e gerar relatórios sobre o respetivo estado.
Para soluções de nuvem, DSC é-utilizável onde quer que o Windows é utilizável.
Também existem ofertas específicas do Azure criadas numa, Desired State Configuration, tais como [automatização do Azure](https://azure.microsoft.com/en-us/documentation/services/automation/), que centraliza a criação de relatórios de DSC.

## <a name="dsc-and-compatibility"></a>DSC e compatibilidade

Embora o DSC foi introduzida no Windows Server 2012 R2, está disponível para sistemas de operativos de nível inferior através do pacote do Windows Management Framework (WMF).
Podem encontrar mais informações sobre o WMF no [home page do PowerShell](/powershell/).

DSC também pode ser utilizado para gerir o Linux. Para obter mais informações, consulte [introdução ao DSC para Linux](../getting-started/lnxGettingStarted.md).
