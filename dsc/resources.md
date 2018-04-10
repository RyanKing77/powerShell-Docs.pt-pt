---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Recursos de DSC
ms.openlocfilehash: e393c8fe2e1ba8d68ba9aa1b656d1e5ebfad30e8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-resources"></a>Recursos de DSC

>Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

Pretendido que recursos de configuração de estado (DSC) fornecem os blocos modulares para uma configuração de DSC. Um recurso expõe propriedades que podem ser configurada (esquema) e contém as funções de script do PowerShell que chama o Gestor de configuração Local (MMC) para "torná-lo,".

Um recurso pode modelo algo como genérica como um ficheiro ou uma definição de servidor IIS tão específico.  Grupos de como recursos são combinados para um módulo de DSC, que organiza todos os ficheiros necessários na uma estrutura que é portátil e inclui os metadados para identificar a forma como os recursos destinam-se a ser utilizado.

Os tópicos seguintes descrevem os recursos de DSC:

- [Recursos de DSC incorporados](builtInResource.md)
- [Criar recursos de DSC personalizados](authoringResource.md)
- [Recursos de DSC incorporados para Linux](lnxBuiltInResources.md)