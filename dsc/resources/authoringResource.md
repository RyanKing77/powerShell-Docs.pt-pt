---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Criar recursos do Windows personalizados do PowerShell Desired State Configuration
ms.openlocfilehash: 882b6efed4564d2354183d7472b301e1e1758335
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684592"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a>Criar recursos do Windows personalizados do PowerShell Desired State Configuration

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) tem recursos incorporados que pode utilizar para configurar o ambiente. Este tópico fornece uma visão geral do desenvolvimento de recursos e ligações para tópicos com informações específicas e exemplos.

## <a name="dsc-resource-components"></a>Componentes de recursos de DSC

Um recurso de DSC é um módulo do Windows PowerShell. O módulo contém o esquema (a definição das propriedades configuráveis) e a implementação (o código que faz o trabalho real de uma configuração especificado) para o recurso. Um esquema de recursos de DSC pode ser definido num ficheiro MOF e a implementação é executada por um módulo de script. A partir do suporte de classes do PowerShell na versão 5, o esquema e de implementação podem ser definidas numa classe. Os tópicos seguintes descrevem mais pormenorizadamente como criar recursos de DSC.

* [Escrever um recurso personalizado do DSC com o MOF](authoringResourceMOF.md)
* [Implementar um recurso de DSCC#](authoringResourceMofCS.md)
* [Escrever um recurso personalizado do DSC com classes do PowerShell](authoringResourceClass.md)
* [Recursos compostos: Utilizar uma configuração de DSC como um recurso](authoringResourceComposite.md)
* [Usando a ferramenta de Designer de recursos](../authoringResourceMofDesigner.md)
