---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Criar recursos de configuração do estado pretendido do PowerShell de personalizada do Windows"
ms.openlocfilehash: 75b494db4ee6e381491decb11d35b60105217a0f
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
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

