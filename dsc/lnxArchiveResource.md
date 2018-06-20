---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: DSC de Linux nxArchive recursos
ms.openlocfilehash: 800954478f149e29c22d1a88304c3be9950f109a
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188671"
---
# <a name="dsc-for-linux-nxarchive-resource"></a>DSC de Linux nxArchive recursos

O **nxArchive** recursos no PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para descompactar os ficheiros de arquivo (. tar,. zip) de um caminho específico num nó de Linux.

## <a name="syntax"></a>Sintaxe

```
nxArchive <string> #ResourceName
{
    SourcePath = <string>
    DestinationPath = <string>
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Force = <bool> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>Propriedades

|  Propriedade |  Descrição |
|---|---|
| SourcePath| Especifica o caminho de origem do ficheiro de arquivo. Isto deve ser um tar. zip, ou. ficheiro.tar.GZ. |
| DestinationPath| Especifica a localização onde pretende Certifique-se de que o conteúdo de arquivo é extraído.|
| Soma de verificação| Define o tipo a utilizar ao determinar se o arquivo de origem tiver sido atualizado. Os valores são: "ctime", "mtime" ou "md5". O valor predefinido é "md5".|
| Force| Determinadas operações de ficheiros (como substituir um ficheiro ou eliminar um diretório que não está vazio) resultará num erro. Utilizar o **Force** propriedade substitui esses erros. O valor predefinido é **$false**.|
| dependsOn | Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado. Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e o respetivo tipo é **ResourceType**, a sintaxe para utilizar esta a propriedade é `DependsOn = "[ResourceType]ResourceName"`.|
| Certifique-se| Determina se deve verificar se o conteúdo do arquivo existe no **destino**. Defina esta propriedade para "Presente" para garantir que existe o conteúdo. Defina-o para "Ausente", certifique-se de que não existam. O valor predefinido é "Presente".|

## <a name="example"></a>Exemplo

O exemplo seguinte mostra como utilizar o **nxArchive** recursos para se certificar de que o conteúdo de um ficheiro de arquivo chamado `website.tar` existe e que são extraídos num destino indicado.

```
Import-DSCResource -Module nx

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = “http://release.contoso.com/releases/website.tar”
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = “mtime”
}

nxArchive SyncWebDir
{
   SourcePath = “/usr/release/staging/website.tar”
   DestinationPath = “/usr/local/apache2/htdocs/”
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
}
```