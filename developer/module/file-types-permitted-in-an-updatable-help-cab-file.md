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
ms.openlocfilehash: 3562804157ebdfca561445a8671d726b55cc4efd
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794251"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a><span data-ttu-id="4ce83-102">File Types Permitted in an Updatable Help CAB File (Tipos de Ficheiro Permitidos num Ficheiro CAB de Ajuda Atualizável)</span><span class="sxs-lookup"><span data-stu-id="4ce83-102">File Types Permitted in an Updatable Help CAB File</span></span>

<span data-ttu-id="4ce83-103">Este tópico apresenta e descreve os requisitos de conteúdo para os arquivos CAB ajuda Atualizável.</span><span class="sxs-lookup"><span data-stu-id="4ce83-103">This topics lists and describes the content requirements for Updatable Help CAB files.</span></span>

## <a name="updatable-help-cab-file-requirements"></a><span data-ttu-id="4ce83-104">Requisitos de arquivo CAB ajuda atualizável</span><span class="sxs-lookup"><span data-stu-id="4ce83-104">Updatable Help CAB File Requirements</span></span>

<span data-ttu-id="4ce83-105">O conteúdo do ficheiro CAB não comprimido é limitado a 1 GB por predefinição.</span><span class="sxs-lookup"><span data-stu-id="4ce83-105">Uncompressed CAB file content is limited to 1 GB by default.</span></span> <span data-ttu-id="4ce83-106">Para ignorar este limite, os utilizadores têm de utilizar o **força** parâmetro do [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span><span class="sxs-lookup"><span data-stu-id="4ce83-106">To bypass this limit, users have to use the **Force** parameter of the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="4ce83-107">Para garantir a segurança dos ficheiros de ajuda que são transferidos da Internet, um ficheiro CAB ajuda Atualizável pode incluir apenas os tipos de ficheiro listados abaixo.</span><span class="sxs-lookup"><span data-stu-id="4ce83-107">To assure the security of help files that are downloaded from the Internet, an Updatable Help CAB file can include only the file types listed below.</span></span> <span data-ttu-id="4ce83-108">O [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet valida todos os ficheiros contra os esquemas de tópico de ajuda.</span><span class="sxs-lookup"><span data-stu-id="4ce83-108">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet validates all files against the help topic schemas.</span></span> <span data-ttu-id="4ce83-109">Se o `Update-Help` cmdlet encontra um ficheiro que é inválido ou não é um tipo permitido, mas não instala o ficheiro inválido e interrompe a instalação de ficheiros CAB no computador do usuário.</span><span class="sxs-lookup"><span data-stu-id="4ce83-109">If the `Update-Help` cmdlet encounters a file that is invalid or is not a permitted type, it does not install the invalid file and stops installing files from the CAB on the user's computer.</span></span>

- <span data-ttu-id="4ce83-110">Com base em XML tópicos de ajuda para cmdlets.</span><span class="sxs-lookup"><span data-stu-id="4ce83-110">XML-based help topics for cmdlets.</span></span>

- <span data-ttu-id="4ce83-111">Com base em XML tópicos de ajuda para scripts e funções.</span><span class="sxs-lookup"><span data-stu-id="4ce83-111">XML-based help topics for scripts and functions.</span></span>

- <span data-ttu-id="4ce83-112">Com base em XML tópicos de ajuda para fornecedores de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4ce83-112">XML-based help topics for Windows PowerShell providers.</span></span>

- <span data-ttu-id="4ce83-113">Baseado em texto ajuda tópicos, como sobre os tópicos.</span><span class="sxs-lookup"><span data-stu-id="4ce83-113">Text-based help topics, such as About topics.</span></span>

<span data-ttu-id="4ce83-114">O [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifica o conteúdo do CAB, quando ele desempacota o CAB.</span><span class="sxs-lookup"><span data-stu-id="4ce83-114">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifies the CAB contents when it unpacks the CAB.</span></span> <span data-ttu-id="4ce83-115">Se `Update-Help` localiza os tipos de ficheiro não é compatível com um ficheiro CAB ajuda Atualizável, gera um erro de terminação e interrompe a operação.</span><span class="sxs-lookup"><span data-stu-id="4ce83-115">If `Update-Help` finds non-compliant file types in an Updatable Help CAB file, it generates a terminating error and stops the operation.</span></span> <span data-ttu-id="4ce83-116">Não instala quaisquer arquivos de ajuda do CAB, até mesmo aqueles de tipos de ficheiro em conformidade.</span><span class="sxs-lookup"><span data-stu-id="4ce83-116">It does not install any help files from the CAB, even those of compliant file types.</span></span>