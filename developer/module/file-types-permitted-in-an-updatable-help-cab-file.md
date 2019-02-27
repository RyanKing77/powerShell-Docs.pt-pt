---
title: Arquivo CAB de ajudar a tipos de arquivos permitidos num Atualizável | Documentos da Microsoft
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: acabdb93-c41a-4b8d-acbe-45cdab91e198
caps.latest.revision: 10
ms.openlocfilehash: 931383858c0b83f0a9a66026c215e16481b89e9e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851598"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a>File Types Permitted in an Updatable Help CAB File (Tipos de Ficheiro Permitidos num Ficheiro CAB de Ajuda Atualizável)

Este tópico apresenta e descreve os requisitos de conteúdo para os arquivos CAB ajuda Atualizável.

## <a name="updatable-help-cab-file-requirements"></a>Requisitos de arquivo CAB ajuda atualizável

O conteúdo do ficheiro CAB não comprimido é limitado a 1 GB por predefinição. Para ignorar este limite, os utilizadores têm de utilizar o **força** parâmetro do [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.
O conteúdo do ficheiro CAB não comprimido é limitado a 1 GB por predefinição. Para ignorar este limite, os utilizadores têm de utilizar o **força** parâmetro do [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.

Para garantir a segurança dos ficheiros de ajuda que são transferidos da Internet, um ficheiro CAB ajuda Atualizável pode incluir apenas os tipos de ficheiro listados abaixo. O [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet valida todos os ficheiros contra os esquemas de tópico de ajuda. Se o `Update-Help` cmdlet encontra um ficheiro que é inválido ou não é um tipo permitido, mas não instala o ficheiro inválido e interrompe a instalação de ficheiros CAB no computador do usuário.
Para garantir a segurança dos ficheiros de ajuda que são transferidos da Internet, um ficheiro CAB ajuda Atualizável pode incluir apenas os tipos de ficheiro listados abaixo. O [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet valida todos os ficheiros contra os esquemas de tópico de ajuda. Se o `Update-Help` cmdlet encontra um ficheiro que é inválido ou não é um tipo permitido, mas não instala o ficheiro inválido e interrompe a instalação de ficheiros CAB no computador do usuário.

- Com base em XML tópicos de ajuda para cmdlets.

- Com base em XML tópicos de ajuda para scripts e funções.

- Com base em XML tópicos de ajuda para fornecedores de Windows PowerShell.

- Baseado em texto ajuda tópicos, como sobre os tópicos.

O [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifica o conteúdo do CAB, quando ele desempacota o CAB. Se `Update-Help` localiza os tipos de ficheiro não é compatível com um ficheiro CAB ajuda Atualizável, gera um erro de terminação e interrompe a operação. Não instala quaisquer arquivos de ajuda do CAB, até mesmo aqueles de tipos de ficheiro em conformidade.
O [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifica o conteúdo do CAB, quando ele desempacota o CAB. Se `Update-Help` localiza os tipos de ficheiro não é compatível com um ficheiro CAB ajuda Atualizável, gera um erro de terminação e interrompe a operação. Não instala quaisquer arquivos de ajuda do CAB, até mesmo aqueles de tipos de ficheiro em conformidade.