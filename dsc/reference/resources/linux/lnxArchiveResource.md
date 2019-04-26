---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: DSC para Linux nxArchive recursos
ms.openlocfilehash: 800954478f149e29c22d1a88304c3be9950f109a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078049"
---
# <a name="dsc-for-linux-nxarchive-resource"></a>DSC para Linux nxArchive recursos

O **nxArchive** recursos no PowerShell Desired State Configuration (DSC) fornece um mecanismo para descompactar os ficheiros de arquivo (. tar,. zip) num caminho específico num nó de Linux.

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
| SourcePath| Especifica o caminho de origem do ficheiro de arquivo. Isso deve ser um. tar,. zip, ou. GZ. |
| DestinationPath| Especifica a localização onde pretende Certifique-se de que o conteúdo do arquivo é extraído.|
| Checksum| Define o tipo a utilizar ao determinar se o arquivo de origem foi atualizado. Os valores são: "ctime", "mtime", ou "md5". O valor predefinido é "md5".|
| Force| Determinadas operações de arquivo (como substituir um ficheiro ou eliminar um diretório que não está vazio) irão resultar num erro. Utilizar o **força** propriedade substitui esses erros. O valor predefinido é **$false**.|
| DependsOn | Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e seu tipo é **ResourceType**, a sintaxe para usar isso a propriedade é `DependsOn = "[ResourceType]ResourceName"`.|
| Certifique-se| Determina se deve verificar se o conteúdo do arquivo existe no **destino**. Defina esta propriedade para "Presente" para garantir que existe o conteúdo. Defini-lo como "Ausente", certifique-se de que não existam. O valor predefinido é "Presente".|

## <a name="example"></a>Exemplo

O exemplo seguinte mostra como utilizar o **nxArchive** recurso para garantir que o conteúdo de um ficheiro de arquivo chamado `website.tar` existem e são extraídos num determinado destino.

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