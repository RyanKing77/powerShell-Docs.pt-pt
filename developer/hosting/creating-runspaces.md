---
title: Criação de espaços de execução | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082945"
---
# <a name="creating-runspaces"></a>Creating Runspaces (Criar Espaços de Execução)

Um espaço de execução é o ambiente operacional para os comandos que são invocados por um aplicativo host. Esse ambiente inclui os comandos e dados que estão atualmente presentes e as restrições de idioma que se aplicam-se atualmente.

 Alojar aplicações podem utilizar o espaço de execução padrão fornecido pelo Windows PowerShell, que inclui todos os comandos de núcleos disponíveis, ou criar um espaço de execução personalizado que inclui apenas um subconjunto dos comandos disponíveis. Para criar um espaço de execução personalizado, crie uma [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) de objeto e atribuí-la ao seu espaço de execução.

## <a name="runspace-tasks"></a>Espaço de execução tarefas

1. [Criar um InitialSessionState](./creating-an-initialsessionstate.md)

2. [Criar um espaço de execução restrito](./creating-a-constrained-runspace.md)

3. [Criação de vários espaços de execução](./creating-multiple-runspaces.md)

## <a name="see-also"></a>Veja Também
