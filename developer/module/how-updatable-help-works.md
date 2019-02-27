---
title: Funciona de ajuda Atualizável como | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7674636e-a0f2-4587-bfc5-dd3e6ce5489e
caps.latest.revision: 6
ms.openlocfilehash: 8874cc18416937c4d3cb30d801f2714410304c8c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850226"
---
# <a name="how-updatable-help-works"></a>How Updatable Help Works (Como Funciona a Ajuda Atualizável)

Este tópico explica como processos ajuda Atualizável o ficheiro XML de HelpInfo e CAB de ficheiros para cada módulo e instala atualizada ajuda para os utilizadores.

## <a name="the-update-help-process"></a>O processo de atualização-Help

A lista seguinte descreve as ações do [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet quando um utilizador executa um comando para atualizar os ficheiros de ajuda para um módulo numa determinada cultura da interface do Usuário.
A lista seguinte descreve as ações do [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet quando um utilizador executa um comando para atualizar os ficheiros de ajuda para um módulo numa determinada cultura da interface do Usuário.

1. `Update-Help` obtém o ficheiro XML de HelpInfo remoto do local especificado pelo valor da **HelpInfoURI** da chave no manifesto do módulo e valida o ficheiro no esquema. (Para ver o esquema, consulte [esquema de XML HelpInfo](./helpinfo-xml-schema.md).) Em seguida, `Update-Help` procura um ficheiro XML de HelpInfo local para o módulo no diretório de módulo no computador do usuário.

2. `Update-Help` compara o número de versão de arquivos de ajuda para a cultura da interface do Usuário especificado nos arquivos de XML de HelpInfo remotos e locais para o módulo. Se o número de versão do ficheiro remoto é superior ao número de versão no arquivo local, ou se não há nenhum ficheiro XML de HelpInfo local para o módulo, `Update-Help` prepara a transferência de arquivos da ajuda de novo.

3. `Update-Help` Seleciona o ficheiro CAB para o módulo na localização especificada pela **HelpContentUri** elemento no arquivo XML de HelpInfo remoto. Utiliza o nome do módulo, o GUID de módulo e a cultura da interface do Usuário para identificar o arquivo CAB.

4. `Update-Help` transfere o ficheiro CAB, desempacota-lo, valida os ficheiros de conteúdo de ajuda e guarda a ajuda ficheiros de conteúdo no subdiretório do idioma específico do diretório de módulo no computador do usuário.

5. `Update-Help` cria um ficheiro XML de HelpInfo local ao copiar o ficheiro XML de HelpInfo remoto. Ele edita o ficheiro XML de HelpInfo local para que ele inclui elementos apenas para o arquivo CAB que tenha instalado. Em seguida, guarda o ficheiro XML de HelpInfo local no diretório de módulo e conclui a atualização.

## <a name="the-save-help-process"></a>O processo de Save-Help

A lista seguinte descreve as ações do [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) e [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlets quando um utilizador executa comandos para atualizar os arquivos da ajuda numa partilha de ficheiros e, em seguida, utilizar esses ficheiros para atualizar os ficheiros de ajuda sobre o computador do usuário.
A lista seguinte descreve as ações do [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) e [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlets quando um utilizador executa comandos para atualizar os arquivos da ajuda numa partilha de ficheiros e, em seguida, utilizar esses ficheiros para atualizar os ficheiros de ajuda sobre o computador do usuário.

O `Save-Help` cmdlet executa as seguintes ações em resposta a um comando para salvar os arquivos de ajuda para um módulo numa partilha de ficheiros especificada pela **DestinationPath** parâmetro.

1. `Save-Help` obtém o ficheiro XML de HelpInfo remoto do local especificado pelo valor da **HelpInfoURI** da chave no manifesto do módulo e valida o ficheiro no esquema. (Para ver o esquema, consulte [esquema de XML HelpInfo](./helpinfo-xml-schema.md).) Em seguida, `Save-Help` procura um ficheiro XML de HelpInfo local no diretório especificado pela **DestinationPath** parâmetro no `Save-Help` comando.

2. `Save-Help` compara o número de versão de arquivos de ajuda para a cultura da interface do Usuário especificado nos arquivos de XML de HelpInfo remotos e locais para o módulo. Se o número de versão do ficheiro remoto é superior ao número de versão no arquivo local, ou se não há nenhum ficheiro XML de HelpInfo local para o módulo no **DestinationPath** diretório, `Save-Help` prepara a transferência de arquivos da ajuda de novo.

3. `Save-Help` Seleciona o ficheiro CAB para o módulo na localização especificada pela **HelpContentUri** elemento no arquivo XML de HelpInfo remoto. Utiliza o nome do módulo, o GUID de módulo e a cultura da interface do Usuário para identificar o arquivo CAB.

4. `Save-Help` transfere o ficheiro CAB e o salva no **DestinationPath** diretório. (Não cria todos os subdiretórios específicos de idioma.)

5. `Save-Help` cria um ficheiro XML de HelpInfo local ao copiar o ficheiro XML de HelpInfo remoto. Ele edita o ficheiro XML de HelpInfo local para que ele inclui elementos apenas para o arquivo CAB que foram. Em seguida, ele salva o arquivo XML de HelpInfo local no **DestinationPath** diretório e conclui a atualização.

   O `Update-Help` cmdlet executa as seguintes ações em resposta a um comando para atualizar os arquivos da ajuda no computador de um usuário a partir dos ficheiros numa partilha de ficheiros especificada pela **SourcePath** parâmetro.

1. `Update-Help` obtém o ficheiro XML de HelpInfo remoto a partir da **SourcePath** diretório. Em seguida, ele procura por um ficheiro XML de HelpInfo local no diretório de módulo no computador do usuário.

2. `Update-Help` compara o número de versão de arquivos de ajuda para a cultura da interface do Usuário especificado nos arquivos de XML de HelpInfo remotos e locais para o módulo. Se o número de versão do ficheiro remoto é superior ao número de versão no arquivo local, ou se não há nenhum ficheiro XML de HelpInfo local, `Update-Help` prepara a instalação de novos ficheiros de ajuda.

3. `Update-Help` Seleciona o arquivo CAB para o módulo a partir da **SourcePath** diretório. Utiliza o nome do módulo, o GUID de módulo e a cultura da interface do Usuário para identificar o arquivo CAB.

4. `Update-Help` descompacta o ficheiro CAB, valida os ficheiros de conteúdo de ajuda e guarda a ajuda ficheiros de conteúdo no subdiretório do idioma específico do diretório de módulo no computador do usuário.

5. `Update-Help` cria um ficheiro XML de HelpInfo local ao copiar o ficheiro XML de HelpInfo remoto. Ele edita o ficheiro XML de HelpInfo local para que ele inclui elementos apenas para o arquivo CAB que tenha instalado. Em seguida, guarda o ficheiro XML de HelpInfo local no diretório de módulo e conclui a atualização.