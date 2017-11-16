---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Recursos de DSC
ms.openlocfilehash: 62bf352b929d661e585e145e5aab0f44f13010a1
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-resources"></a>Recursos de DSC

>Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

Pretendido que recursos de configuração de estado (DSC) fornecem os blocos modulares para uma configuração de DSC. Um recurso expõe propriedades que podem ser configurada (esquema) e contém as funções de script do PowerShell que chama o Gestor de configuração Local (MMC) para "torná-lo,".

Um recurso pode modelo algo como genérica como um ficheiro ou uma definição de servidor IIS tão específico.  Grupos de como recursos são combinados para um módulo de DSC, que organiza todos os ficheiros necessários na uma estrutura que é portátil e inclui os metadados para identificar a forma como os recursos destinam-se a ser utilizado.  

Os tópicos seguintes descrevem os recursos de DSC:

- [Recursos de DSC incorporados](builtInResource.md)
- [Criar recursos de DSC personalizados](authoringResource.md)
- [Recursos de DSC incorporados para Linux](lnxBuiltInResources.md)

