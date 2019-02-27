---
title: 'Updatable Help Authoring: Passo a passo | Documentos da Microsoft'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849834"
---
# <a name="updatable-help-authoring-step-by-step"></a>Updatable Help Authoring: Step-by-Step (Criação de Ajuda Atualizável: Passo a Passo)

Este documentos, lista os passos no processo de criação ajuda Atualizável.

## <a name="authoring-updatable-help-step-by-step"></a>Ajuda Atualizável de criação: Step-by-Step (Criação de Ajuda Atualizável: Passo a Passo)

Ajuda atualizável foi concebida para utilizadores finais, mas também proporciona significativos benefícios para os autores de módulo e gravadores de ajuda, incluindo a capacidade de adicionar conteúdo, corrija os erros, fornecem em várias culturas de interface do Usuário e respondem a comentários de utilizador e de pedidos, há muito tempo após o módulo foi enviada. Este tópico explica como empacotar e arquivos de ajuda de carregamento para que os utilizadores podem transferir e instalá-los utilizando o [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.

Os passos seguintes fornecem uma visão geral do processo de apoio ajuda Atualizável.

### <a name="step-1-find-an-internet-site-for-your-help-files"></a>Passo 1: Localizar um site da Internet para os seus ficheiros de ajuda

A primeira etapa na criação de ajuda atualizável é encontrar uma localização de Internet para arquivos de ajuda do seu módulo. Na verdade, pode usar duas localizações diferentes. Pode manter o arquivo de informações de ajuda do seu módulo (HelpInfo XML - descritos abaixo) num local de Internet e os arquivos CAB conteúdos da ajuda em outro local de Internet. Todos os conteúdos CAB arquivos de ajuda para um módulo tem de ser na mesma localização. Pode colocar arquivos CAB conteúdos de ajuda para módulos diferentes na mesma localização.

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a>Passo 2: Adicionar uma chave de HelpInfoURI a seu manifesto de módulo

Adicionar uma **HelpInfoURI** chave para o manifesto de módulo. O valor da chave é o identificador URI (Uniform Resource) da localização do ficheiro de informações HelpInfo XML para seu módulo. Para segurança, o endereço tem de começar com "http" ou "https". O URI deve especificar uma localização de Internet, mas não tem de incluir o nome do ficheiro XML de HelpInfo.

Por exemplo:

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a>Passo 3: Crie um ficheiro XML de HelpInfo

O ficheiro de informações HelpInfo XML contém o URI da localização de Internet de seus arquivos de ajuda e números de versão dos arquivos de ajuda mais recentes para seu módulo em cada cultura da interface do Usuário suportado. Cada módulo Windows PowerShell possui um arquivo XML de HelpInfo. Quando atualizar seus arquivos de ajuda, editar ou substituir o ficheiro XML de HelpInfo; não adicionar outro. Para obter mais informações, consulte [como criar um ficheiro XML de HelpInfo](./how-to-create-a-helpinfo-xml-file.md).

### <a name="step-4-sign-your-help-files"></a>Passo 4: Assinar seus arquivos de ajuda

Assinaturas digitais não são necessárias, mas eles são uma recomendação de melhores práticas, sempre que estão a partilhar ficheiros.

### <a name="step-5-create-cab-files"></a>Passo 5: Criar ficheiros CAB

Utilizar uma ferramenta que cria arquivos de Gabinete (. cab), como MakeCab.exe, para criar um. Arquivo CAB que contém os ficheiros de ajuda para seu módulo. Crie um arquivo CAB separado para os arquivos da ajuda em cada cultura da interface do Usuário suportada. Para obter mais informações, consulte [como preparar Atualizável CAB arquivos de ajuda do](./how-to-prepare-updatable-help-cab-files.md).

### <a name="step-6-upload-your-files"></a>Passo 6: Carregar os ficheiros

Para publicar os arquivos de ajuda de novos ou atualizados, carregue os ficheiros CAB para a localização de Internet que é especificada pela **HelpContentUri** elemento no arquivo XML de HelpInfo. Em seguida, carregue o ficheiro XML de HelpInfo para a localização de Internet que é especificada pelo valor da **HelpInfoUri** chave no manifesto do módulo.
