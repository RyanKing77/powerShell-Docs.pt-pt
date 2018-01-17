---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Criar recursos de configuração do estado pretendido do PowerShell de personalizada do Windows"
ms.openlocfilehash: 4751bcaab1996ee3164bd2a2f430c3b188712860
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a>Criar recursos de configuração do estado pretendido do PowerShell de personalizada do Windows

> Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

Configuração de estado pretendido do Windows PowerShell (DSC) tem recursos incorporados que pode utilizar para configurar o ambiente. (Para obter mais informações, consulte [incorporada Windows PowerShell pretendido estado configuração recursos](builtInResource.md).) Este tópico fornece uma descrição geral do desenvolvimento de recursos e ligações para tópicos com informações específicas e exemplos.

## <a name="dsc-resource-components"></a>Componentes de recursos de DSC

Um recurso de DSC é um módulo do Windows PowerShell. O módulo contém o esquema (a definição das propriedades configuráveis) e a implementação (o código que suporta o trabalho real uma configuração especificado) para o recurso. Um esquema de recursos de DSC pode ser definido num ficheiro MOF e a implementação é efetuada por um módulo de script. A partir do suporte de classes do PowerShell na versão 5, o esquema e de implementação podem ambos ser definidos numa classe. Os tópicos seguintes descrevem como criar recursos de DSC mais detalhadamente.

* [Escrever um recurso personalizado de DSC com MOF](authoringResourceMOF.md)
* [Implementar um recurso de DSC em c#](authoringResourceMofCS.md)
* [Escrever um recurso personalizado de DSC com classes de PowerShell](authoringResourceClass.md)
* [Recursos compostos: utilizar uma configuração de DSC como um recurso](authoringResourceComposite.md)
* [Utilizar a ferramenta do Designer de recursos](authoringResourceMofDesigner.md)

