---
ms.date: 09/11/2018
contributor: JKeithB
keywords: Galeria, PowerShell, psgallery
title: Transferência manual de pacotes
ms.openlocfilehash: c0a96e866dfd27f9b2170ea540ec6dd0c67701fd
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215459"
---
# <a name="manual-package-download"></a>Transferência manual de pacotes

O Galeria do PowerShell dá suporte ao download de um pacote diretamente do site, sem usar os cmdlets do PowerShellGet. Você pode baixar qualquer pacote como um arquivo de pacote`.nupkg`NuGet (), que você pode copiar para um repositório interno.

> [!NOTE]
> O download do pacote manual **não** se destina como uma substituição `Install-Module` para o cmdlet.
> O download do pacote não instala o módulo ou o script. As dependências não estão incluídas no pacote NuGet baixado. As instruções a seguir são fornecidas apenas para fins de referência.

## <a name="using-manual-download-to-acquire-a-package"></a>Usando o download manual para adquirir um pacote

Cada página tem um link para download manual, como mostrado aqui:

![Download manual](../../Images/packagedisplaypagewithpseditions.png)

Para baixar manualmente, clique em **baixar o arquivo RAW nupkg**. Uma cópia do pacote é copiada para a pasta de download do seu navegador com o `<name>.<version>.nupkg`nome.

Um pacote NuGet é um arquivo ZIP com arquivos extras contendo informações sobre o conteúdo do pacote. Alguns navegadores, como o Internet Explorer, substituem automaticamente a `.zip`extensão de `.nupkg` arquivo por. Para expandir o pacote, renomeie `.nupkg` o `.zip`arquivo como, se necessário, e extraia o conteúdo para uma pasta local.

Um arquivo de pacote NuGet inclui os seguintes **elementos específicos do NuGet** que não fazem parte do código do pacote original:

- Uma pasta chamada `_rels` -contém um `.rels` arquivo que lista as dependências
- Uma pasta chamada `package` -contém os dados específicos do NuGet
- Um arquivo nomeado `[Content_Types].xml` -descreve como as extensões como o PowerShellGet funcionam com o NuGet
- Um arquivo chamado `<name>.nuspec` -contém a massa dos metadados

## <a name="installing-powershell-modules-from-a-nuget-package"></a>Instalando módulos do PowerShell de um pacote NuGet

> [!NOTE]
> Essas instruções **não** dão o mesmo resultado que a execução `Install-Module`. Essas instruções atendem aos requisitos mínimos. Eles não se destinam a ser `Install-Module`uma substituição para.
> Algumas etapas executadas pelo `Install-Module` não são incluídas.

A abordagem mais fácil é remover os elementos específicos do NuGet da pasta. A remoção dos elementos deixa o código do PowerShell criado pelo autor do pacote.
Para obter a lista de elementos específicos do NuGet, consulte [usando o download manual para adquirir um pacote](#using-manual-download-to-acquire-a-package).

Os passos são os seguintes:

1. Extraia o conteúdo do pacote NuGet para uma pasta local.
2. Exclua os elementos específicos do NuGet da pasta.
3. Renomeie a pasta. O nome da pasta padrão geralmente `<name>.<version>`é. A versão pode incluir `-prerelease` se o módulo estiver marcado como uma versão de pré-lançamento. Renomeie a pasta apenas para o nome do módulo. Por exemplo, `azurerm.storage.5.0.4-preview` torna `azurerm.storage`-se.
4. Copie a pasta para uma das pastas no `$env:PSModulePath value`. `$env:PSModulePath`é um conjunto delimitado por ponto-e-vírgula de caminhos nos quais o PowerShell deve procurar módulos.

> [!IMPORTANT]
> O download manual não inclui nenhuma dependência exigida pelo módulo. Se o pacote tiver dependências, eles deverão ser instalados no sistema para que este módulo funcione corretamente. O Galeria do PowerShell mostra todas as dependências exigidas pelo pacote.

## <a name="installing-powershell-scripts-from-a-nuget-package"></a>Instalando scripts do PowerShell de um pacote NuGet

> [!NOTE]
> Essas instruções **não** dão o mesmo resultado que a execução `Install-Script`. Essas instruções atendem aos requisitos mínimos. Eles não se destinam a ser `Install-Script`uma substituição para.

A abordagem mais fácil é extrair o pacote NuGet e, em seguida, usar o script diretamente.

Os passos são os seguintes:

1. Extraia o conteúdo do pacote NuGet.
2. O `.PS1` arquivo na pasta pode ser usado diretamente deste local.
3. Você pode excluir os elementos específicos do NuGet na pasta.

Para obter a lista de elementos específicos do NuGet, consulte [usando o download manual para adquirir um pacote](#using-manual-download-to-acquire-a-package).

> [!IMPORTANT]
> O download manual não inclui nenhuma dependência exigida pelo módulo. Se o pacote tiver dependências, eles deverão ser instalados no sistema para que este módulo funcione corretamente. O Galeria do PowerShell mostra todas as dependências exigidas pelo pacote.
