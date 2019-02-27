---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Noções básicas sobre a função do DSC num pipeline CI/CD
ms.openlocfilehash: 7aec414b3d8e61d1daa1ce796184ac34dbbb43ce
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/25/2019
ms.locfileid: "56803383"
---
# <a name="understanding-dscs-role-in-a-cicd-pipeline"></a>Noções básicas sobre a função do DSC num pipeline CI/CD

Este artigo descreve os tipos de abordagens disponíveis para a combinação de recursos e configurações.
O objetivo de cada cenário é o mesmo, para reduzir a complexidade quando várias configurações preferidas para atingir um servidor de estado de ponto de implantação.
Um exemplo disso seria várias equipes que contribuem para o resultado de uma implementação de servidor, como um proprietário da aplicação mantém o estado da aplicação e a uma equipa central lançar as alterações às linhas de base de segurança.
As nuances de cada abordagem, incluindo os benefícios e riscos são descritas aqui.

![Pipeline](../images/Pipeline.jpg)

## <a name="types-of-collaborative-authoring-techniques"></a>Tipos de técnicas de criação de colaboração

Existem duas soluções criadas com base Local o Gestor de configuração para ativar este conceito:

| Conceito | Informações detalhadas
|-|-
| Configurações Parciais | [Documentação](../pull-server/partialConfigs.md)
| Recursos compostos | [Documentação](../resources/authoringResourceComposite.md)

## <a name="understanding-the-impact-of-each-approach"></a>Compreender o impacto de cada abordagem

Uma destas soluções pode ser utilizada para gerir o resultado de uma implementação de servidor.
No entanto, há uma diferença significativa no impacto da utilização de cada abordagem.

## <a name="partial-configurations"></a>Configurações Parciais

Ao usar configurações parciais, o Gestor de configuração Local está configurado para gerir várias configurações de forma independente.
Configurações são compiladas de forma independente e, em seguida, são atribuídas ao nó.
Isso requer o MMC para ser configurado com antecedência com o nome de cada configuração.

![PartialConfiguration](../images/PartialConfiguration.jpg)

Configurações parciais fornecem dois ou mais, as equipes de controle completo sobre configuração de um servidor, geralmente sem o benefício de comunicação ou colaboração.

Os clientes forneceram comentários que isso pode levar a conflitos de recursos, as substituições não intencionais e, por fim, perda de controle de configuração verdadeiro do ativo.

Além disso, os clientes forneceram comentários que ao usar esse modelo, são pouco provável que ser totalmente testado por meio de um pipeline de lançamento, cada controlar alterações de configuração de equipas que leva a resultados inesperados na produção.

**É fundamental que um único pipeline ser utilizada para avaliar todos os de alterações de versão para servidores.**

Na ilustração abaixo, equipe B libera a respetiva configuração parcial para A equipe do Team A. em seguida, executa seus testes em relação a um servidor com ambas as configurações aplicadas.
Nesse modelo, apenas uma autoridade tem permissão para fazer alterações na produção.

![PartialSinglePipeline](../images/PartialSinglePipeline.jpg)

Quando as alterações são necessárias da Equipe B, deve enviar um pedido de solicitação contra o ambiente de controle de origem de equipe do.
Seria, em seguida, reveja as alterações usando a automação de teste e de versão para produção quando há certeza de que as alterações não causará erros em aplicações ou serviços hospedados pelo servidor.

## <a name="composite-resources"></a>Recursos compostos

Um recurso composto é simplesmente uma configuração de DSC empacotado como um recurso.
Não existem não requisitos especiais para configurar o LCM para aceitar recursos compostos.
Os recursos são utilizados dentro de uma nova configuração e uma única compilação resulta num arquivo MOF.

![CompositeResource](../images/CompositeResource.jpg)

Existem dois cenários comuns para recursos compostos.
A primeira é reduzir a complexidade e conceitos abstratos de exclusivos.
O segundo é para permitir que as linhas de base a serem empacotados para uma equipe de aplicativos implementar em segurança por meio do seu pipeline de lançamento para a produção depois de todos os testes foram aprovados.

```PowerShell
Configuration Name
{
  File 1
  {
    Ensure = “Present”
    Path = “c:\inetpub\file1.zip”
    Source = “http://uri/file1.zip”
  }
  Service A
  {
    Ensure = “Present”
    Name = “ServiceA”
    Status = “Running”
  }
  SecurityBaseline Settings
  {
    Ensure = “Present”
    Datacenter = “NorthAmerica”
  }
}
```

Recursos compostos promovem a composição e colaboração com um pipeline de durante a criação de maturidade operacional

Pode estar já a utilizar recursos compostos sem perceber.
Um exemplo é **ServiceSet**.
Este recurso gere o estado dos vários serviços do Windows sem listagem-los individualmente.
A propriedade Name aceita uma matriz de cadeias de caracteres para fornecer o nome de cada serviço.
Quando a configuração é compilada, o MOF irá conter uma seção de serviço exclusiva para cada um dos nomes passados para ServiceSet.

As organizações podem ter "agentes" ou "middleware", que deve ser instalado em cada servidor.
Um recurso composto é a melhor resposta para gerir as dependências, instalação e configuração dessas ferramentas e utilitários.

A pessoa ou equipe responsável por soluções que abrangem vários servidores cria uma configuração que contém os seus requisitos.
Em seguida, a configuração deverá ser empacotada como um recurso composto com base nas instruções fornecidas na documentação do recursos compostos.
Por fim, o novo recurso composto deve ser publicado para uma localização, como uma partilha de ficheiros ou NuGet feed onde o aplicativo as equipes possam consumi-la em suas configurações.

Sempre que a equipe de versões uma nova versão, eles seriam incrementar o número de versão no manifesto do módulo para seus recursos compostos.
As equipas de aplicações incluem o recurso composto na configuração criam para o gerenciamento de dependências de aplicações.
Quando as equipes de operações/segurança lançar uma nova versão de seus recursos, eles notificam as equipes de aplicação de uma nova alteração.

As equipes de aplicativo podem disparar uma versão para produção em que a única alteração é às linhas de base.
No entanto, isso fornece uma oportunidade de avaliar o impacto em aplicativos antes de risco de uma indisponibilidade do serviço.

Nota – enviar comentários sobre a utilização de recursos compostos incluiu críticas que efetuar alterações requer compilação e lançamento de um novo MOF.
Isto é propositado.
Cada nova versão de configuração deve incluir uma referência estática numa versão específica de cada recurso e deve ser validada por testes antes de chegar a nós do servidor de produção.
O processo de teste e lançar as alterações no controle da fonte cria um ambiente seguro para liberar a alteração em lotes de pequenas, mas frequentes.

Para obter mais informações sobre a utilização de pipelines de versão para gerir a infraestrutura básica, consulte o White Paper: [O modelo de Pipeline de lançamento](../further-reading/whitepapers.md).
