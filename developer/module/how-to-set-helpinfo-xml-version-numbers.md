---
title: Como configurar números de versão HelpInfo XML | Documentos da Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93a00463-af58-41c8-b088-450909fa1d05
caps.latest.revision: 6
ms.openlocfilehash: b98e6879bbfe0e3ec1a9ab37496dde44caf523a4
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054140"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a>How to Set HelpInfo XML Version Numbers (Como Definir os Números de Versão de um Ficheiro XML HelpInfo)

Este tópico explica como configurar e aumentar os números de versão num arquivo de informações de ajuda Atualizável, comumente conhecido como "arquivo de HelpInfo XML".

## <a name="how-to-set-helpinfo-xml-version-numbers"></a>How to Set HelpInfo XML Version Numbers (Como Definir os Números de Versão de um Ficheiro XML HelpInfo)

Os números de versão num arquivo XML de HelpInfo são fundamentais para a operação de ajuda Atualizável.
O [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets transferir novos ficheiros de ajuda, apenas quando o número de versão para uma cultura da interface do Usuário no arquivo XML de HelpInfo remoto é superior ao número de versão para aquela cultura da interface do Usuário na local de HelpInfo de XML, ou não existe nenhum ficheiro XML de HelpInfo local.

O ficheiro XML de HelpInfo utiliza o número da versão de 4 partes que está definido no **ter** classe do Microsoft .NET Framework. O formato é `N1.N2.N3.N4`. Os autores de módulo, podem utilizar qualquer versão de esquema que é permitida de numeração a **ter** classe. Ajuda atualizável requer apenas que o número de versão para um aumento de cultura da interface do Usuário quando uma nova versão do ficheiro CAB para aquela cultura da interface do Usuário é carregada para a localização especificada pelos **HelpContentURI** elemento no arquivo XML de HelpInfo.

O exemplo seguinte mostra os elementos do ficheiro XML de HelpInfo para o alemão (Alemanha-DE) da interface do Usuário cultura quando a versão é 2.15.0.10.

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

O número de versão para uma cultura da interface do Usuário reflete a versão do ficheiro CAB para aquela cultura da interface do Usuário. O número da versão se aplica a todo o arquivo CAB. Não é possível definir os números de versão diferentes para diferentes arquivos no ficheiro CAB. O número de versão para cada cultura da interface do Usuário é avaliado de forma independente e não tem de estar relacionado aos números de versão para outras culturas de interface do Usuário que o módulo suporta.