---
ms.date: 09/11/2018
contributor: JKeithB
keywords: Galeria do powershell, psgallery
title: Transferência manual de pacotes
ms.openlocfilehash: 57baa14089b803f58c42ccb54553ecace841e34b
ms.sourcegitcommit: e24525046dd37166b9d83eeecdc534726316f429
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2018
ms.locfileid: "52742827"
---
# <a name="manual-package-download"></a>Transferência manual de pacotes

A galeria do Powershell suporta baixar um pacote do Web site diretamente, sem utilizar os cmdlets do PowerShellGet. Pode baixar qualquer pacote como um ficheiro de pacote (. nupkg) do NuGet, que, em seguida, pode copiar para um repositório interno.

> [!NOTE]
> A transferência de pacotes manual é **não** pretende ser uma substituição para o cmdlet Install-Module.
> Download do pacote não instala o módulo ou script. As dependências não são incluídas no pacote NuGet transferido. As instruções seguintes são fornecidas para efeitos de referência apenas.

## <a name="using-manual-download-to-acquire-a-package"></a>Utilizar transferência manual para adquirir um pacote

Cada página tem uma ligação para transferir o Manual, como mostrado aqui:

![Transferência manual](../../Images/packagedisplaypagewithpseditions.png)

Para transferir manualmente, clique em **transfira o ficheiro raw nupkg**. Uma cópia do pacote copiados para a pasta de transferência para o seu navegador com o nome `<name>.<version>.nupkg`.

Um pacote de NuGet é um arquivo ZIP com ficheiros adicionais, que contém informações sobre o conteúdo do pacote. Alguns browsers, como o Internet Explorer, substituem automaticamente a `.nupkg` extensão com o ficheiro `.zip`. Para expandir o pacote, mudar o nome da `.nupkg` de ficheiros para `.zip`, se necessário, em seguida, extraia os conteúdos para uma pasta local.

Um ficheiro de pacote NuGet inclui os seguintes elementos do NuGet específicas que não fazem parte do código em pacote original:

- Uma pasta denominada `_rels` -contém um `.rels` ficheiro que lista as dependências
- Uma pasta denominada `package` -contém os dados específicos do NuGet
- Um arquivo chamado `[Content_Types].xml` -descreve como extensões, como o PowerShellGet funcionam com o NuGet
- Um arquivo chamado `<name>.nuspec` -contém a maior parte dos metadados

## <a name="installing-powershell-modules-from-a-nuget-package"></a>Instalar módulos do PowerShell a partir de um pacote de NuGet

> [!NOTE]
> Estas instruções **não fazer** apresentam o mesmo resultado como executar `Install-Module`. Estas instruções satisfazem os requisitos mínimos. Estas não recomendações pretendem ser uma substituição para `Install-Module`. Alguns passos realizados por `Install-Module` não estão incluídos.

A abordagem mais fácil é remover os elementos de NuGet específico a partir da pasta. Isso deixa o código de PowerShell criado pelo autor do pacote. Os passos são:

1. Extraia o conteúdo do pacote NuGet para uma pasta local.
2. Elimine os elementos de NuGet específico a partir da pasta.
3. Renomeie a pasta. O nome da pasta predefinida é normalmente `<name>.<version>`. Pode incluir a versão "-pré-lançamento" se o módulo é identificado como uma versão de pré-lançamento. Renomeie a pasta para apenas o nome do módulo. Por exemplo, "azurerm.storage.5.0.4-pré-visualização" torna-se "azurerm. Storage".
4. Copie a pasta para uma das pastas no `$env:PSModulePath value`. `$env:PSModulePath` é um conjunto de ponto e vírgula delimitados por de caminhos em que PowerShell deveria procurar módulos.

> [!IMPORTANT]
> A transferência manual não inclui todas as dependências necessárias pelo módulo. Se o pacote tiver dependências, tem de estar instalados no sistema para este módulo funcione corretamente. A galeria do PowerShell mostra todas as dependências necessárias pelo pacote.

## <a name="installing-powershell-scripts-from-a-nuget-package"></a>Instalar Scripts do PowerShell a partir de um pacote NuGet

> [!NOTE]
> Estas instruções **não fazer** apresentam o mesmo resultado como executar `Install-Script`. Estas instruções satisfazem os requisitos mínimos. Estas não recomendações pretendem ser uma substituição para `Install-Script`.

A abordagem mais fácil é para extrair o pacote NuGet, em seguida, utilize o script diretamente. Os passos são:

1. Extraia o conteúdo do pacote NuGet.
2. O `.PS1` ficheiro na pasta pode ser utilizado diretamente a partir desta localização.
3. Pode eliminar os elementos específicos do NuGet na pasta.

> [!IMPORTANT]
> A transferência manual não inclui todas as dependências necessárias pelo módulo. Se o pacote tiver dependências, tem de estar instalados no sistema para este módulo funcione corretamente. A galeria do PowerShell mostra todas as dependências necessárias pelo pacote.
