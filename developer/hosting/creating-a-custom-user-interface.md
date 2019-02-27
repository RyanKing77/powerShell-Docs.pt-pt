---
title: Criando uma interface do usuário personalizada | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d7286443-eed4-43d5-b809-50cdcdcba088
caps.latest.revision: 4
ms.openlocfilehash: 23518c625fe1138e1bd2bcc895274cb21d7daf8a
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/25/2019
ms.locfileid: "56852214"
---
# <a name="creating-a-custom-user-interface"></a>Creating a custom user interface (Criar uma interface de utilizador personalizada)

Windows PowerShell fornece classes abstratas e interfaces que permitem-lhe criar uma interface de Usuário interativa personalizado que hospeda o mecanismo do Windows PowerShell. Para criar uma interface do Usuário personalizada, deve implementar o [System.Management.Automation.Host.PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) classe. Opcionalmente, também pode implementar o [System.Management.Automation.Host.Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)e [System.Management.Automation.Host.Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) classes e o [System.Management.Automation.Host.Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) e [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) interfaces.
