---
title: Como criar e carregar arquivos CAB | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d35f233-5447-48a2-a961-9fbca763262b
caps.latest.revision: 7
ms.openlocfilehash: 9928a0b31a57d42eb39cea1af0509613c483caf7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082384"
---
# <a name="how-to-create-and-upload-cab-files"></a>How to Create and Upload CAB Files (Como Criar e Carregar Ficheiros CAB)

Este tópico explica como criar arquivos CAB ajuda Atualizável e carregá-los para a localização onde os cmdlets ajuda Atualizável pode encontrá-los.

## <a name="how-to-create-and-upload-updatable-help-cab-files"></a>Como criar e carregar os arquivos CAB ajuda Atualizável

Pode utilizar a funcionalidade de ajuda Atualizável para entregar os ficheiros de ajuda de novas ou atualizadas para um módulo em vários idiomas e culturas. Um pacote de ajuda Atualizável de mensagens em fila para um módulo consiste num arquivo de HelpInfo XML e um ou mais cabinet (. Ficheiros CAB). Cada ficheiro CAB contém arquivos de ajuda para o módulo numa cultura da interface do Usuário. Utilize o procedimento seguinte para criar ficheiros CAB para ajuda Atualizável.

1. Organize os arquivos de ajuda para o módulo por cultura da interface do Usuário. Cada ficheiro CAB ajuda Atualizável contém os ficheiros de ajuda para um módulo numa cultura da interface do Usuário. Poderá fornecer ajuda de vários ficheiros CAB para o módulo, cada uma para uma cultura da interface do Usuário diferente.

2. Certifique-se de que arquivos incluem apenas os tipos de ficheiro permitidos para ajuda Atualizável e validá-los num esquema de ficheiro de ajuda da ajuda. Se o `Update-Help` cmdlet encontra um ficheiro que é inválido ou não é um tipo permitido, mas não instala o ficheiro inválido e interrompe a instalação de ficheiros CAB. Para obter uma lista dos tipos de ficheiro permitidas, consulte [tipos de ficheiro permitido num arquivo de CAB ajuda Atualizável](./file-types-permitted-in-an-updatable-help-cab-file.md).

3. Assine digitalmente os arquivos da ajuda. Assinaturas digitais não são necessárias, mas são uma prática recomendada.

4. Inclua a totalidade da ajuda de ficheiros para o módulo na interface do Usuário de cultura, não apenas os ficheiros que são novos ou foram alterados. Se o arquivo CAB estiver incompleto, os utilizadores que transferir arquivos de ajuda pela primeira vez ou não transferir todas as atualizações, não terá todos os arquivos de ajuda do módulo.

5. Utilize um utilitário que cria arquivos cab, como MakeCab.exe. Windows PowerShell não inclui cmdlets que criam ficheiros CAB.

6. Nomes aos ficheiros CAB. Para obter mais informações, consulte [como nome de um arquivo de CAB ajuda Atualizável](./how-to-name-an-updatable-help-cab-file.md).

7. Carregar os ficheiros CAB para o módulo para a localização especificada pelos **HelpContentUri** elemento no arquivo XML de HelpInfo para o módulo. Em seguida, carregue o ficheiro XML de HelpInfo para a localização especificada pelos **HelpInfoUri** chave de manifesto do módulo. O **HelpContentUri** e **HelpInfoUri** pode apontar para a mesma localização.

> [!CAUTION]
> O valor do **HelpInfoUri** chave e o **HelpContentUri** elemento tem de começar com "http" ou "https". O valor tem de indicar uma localização de Internet e não tem de incluir um nome de ficheiro.