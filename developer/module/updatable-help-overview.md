---
title: Descrição geral de ajuda atualizável | Documentos da Microsoft
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: 3f7388a9-9fa8-42bc-b294-538c9a01e30a
caps.latest.revision: 12
ms.openlocfilehash: 4e962890fa1d5c282a02a89f0ae2e263844c635e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847489"
---
# <a name="updatable-help-overview"></a>Updatable Help Overview (Ajuda Atualizável: Descrição Geral)

Este documento fornece uma introdução básica a conceção e operação do recurso ajuda Atualizável do Windows PowerShell. Foi concebido para os autores de módulo e outros que fornecer tópicos de ajuda do Windows PowerShell para os utilizadores.

## <a name="introduction"></a>Introdução

Tópicos de ajuda do Windows PowerShell são uma parte integral da experiência do Windows PowerShell. Como módulos do Windows PowerShell, os tópicos de ajuda são continuamente atualizados e melhorados aos autores e as contribuições da Comunidade de usuários do Windows PowerShell.

O *ajuda Atualizável* funcionalidade, introduzida no Windows PowerShell 3.0, garante que os utilizadores têm as versões mais recentes dos tópicos de ajuda no prompt de comando, mesmo para comandos internos do Windows PowerShell, sem baixar novos módulos ou a executar a atualização do Windows. Ajuda atualizável facilita a atualização simples, fornecendo cmdlets que transferir as versões mais recentes dos tópicos de ajuda a partir da Internet e instalá-los nos subdiretórios corretos no computador local do usuário. Até mesmo os usuários estejam atrás de firewalls podem utilizar os novos cmdlets para obter ajuda atualizada a partir de uma partilha de ficheiros internos.

Ajuda atualizável é totalmente suportada por todos os módulos do Windows PowerShell no Windows® 8 e Windows Server® 2012 e seus recursos estão disponíveis para todos os autores de módulo do Windows PowerShell. Ajuda atualizável suporta apenas os arquivos de ajuda baseados em XML. Não suporta a ajuda baseada no comentário.

Ajuda atualizável inclui as seguintes funcionalidades.

- O [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet, que determina se os utilizadores têm a ajuda mais recente de ficheiros para um módulo e, se não estiver, transferir os ficheiros de ajuda mais recentes a partir da Internet, a Desempacote-los e instala-os nos subdiretórios módulo correto no computador do usuário. Os utilizadores podem utilizar o [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet para ver os tópicos de ajuda recém-instalado imediatamente. Não é necessário reiniciar o Windows PowerShell.

- O [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet, que transfere a ajuda mais recente ficheiros a partir da Internet e salva-os num diretório de sistema de ficheiros. Os utilizadores podem utilizar o `Update-Help` cmdlet para obter os ficheiros de ajuda do diretório do sistema de ficheiros e Descompacte e instalá-los nos subdiretórios de módulo no computador do usuário. O `Save-Help` cmdlet foi concebido para utilizadores que têm limitados ou sem acesso à Internet e para as empresas que preferem limitar o acesso à Internet.

- **Ajuda para um módulo**. Arquivos de ajuda para um módulo são geridos e fornecidos como uma unidade, para que os usuários podem obter todos os arquivos de ajuda para módulos que utilizam. Ajuda atualizável só é suportada para módulos, não para o snap-ins do Windows PowerShell.

- **Suporte para a versão**. Ajuda atualizável utiliza standard quatro posição (N1. N2. N3. Números de versão N4). Ajuda atualizável transfere arquivos de ajuda, quando o número de versão da ajuda do ficheiros no computador do usuário (ou no `Save-Help` diretório) é menor do que o número de versão dos arquivos da ajuda disponíveis na localização de Internet.

- **Suporte a vários idiomas**. Ajuda atualizável oferece suporte a arquivos de ajuda do módulo em várias culturas de interface do Usuário. Ajuda atualizável nomes de ficheiros incluem códigos de idioma padrão, como "en-US" e "ja-JP" e o `Update-Help` e `Save-Help` cmdlets colocar os arquivos da ajuda em subdiretórios específicos do idioma do diretório de módulo.

- **Gerado automaticamente ajuda**. O [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet apresenta básica ajuda para comandos que não têm arquivos de ajuda. A ajuda de gerado automaticamente inclui a sintaxe de comando e aliases e as instruções para utilizar a ajuda online e ajuda Atualizável.

- **Melhorada a Ajuda Online**. Acesso fácil a ajuda online já não necessita de arquivos de ajuda. O **Online** parâmetro do `Get-Help` cmdlet agora obtém o URL de um tópico de ajuda online do valor da **HelpUri** propriedade de todos os comandos, se ele não é possível localizar o URL de ajuda online num arquivo de ajuda. Pode preencher o **HelpUri** propriedade adicionando um **HelpUri** atributo para o código de cmdlets, funções e comandos CIM, ou utilizando o **. Ligação** diretiva baseada no comentário ajuda em fluxos de trabalho e scripts.

  Para tornar nossos arquivos de ajuda atualizável, os módulos do Windows PowerShell no Windows 8 e Windows Server vNext vem com arquivos de ajuda. Os utilizadores podem utilizar a ajuda Atualizável de mensagens em fila para instalar arquivos de ajuda e atualizá-los. Os autores de outros módulos podem incluir arquivos de ajuda em módulos ou omiti-los. Suporte para ajuda Atualizável é opcional mas recomendado.
