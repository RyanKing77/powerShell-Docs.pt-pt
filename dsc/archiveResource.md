---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Recursos de DSC arquivo
ms.openlocfilehash: 458b4f0f20dc96dab62e709183c25ff57d971aae
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219475"
---
# <a name="dsc-archive-resource"></a>Recursos de DSC arquivo

> Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

O recurso de arquivo no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para descompactar os ficheiros de arquivo (. zip) de um caminho específico.

## <a name="syntax"></a>Sintaxe
```MOF
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
}
```

## <a name="properties"></a>Propriedades

|  Propriedade  |  Descrição   |
|---|---|
| Destino| Especifica a localização onde pretende Certifique-se de que o conteúdo de arquivo é extraído.|
| Caminho| Especifica o caminho de origem do ficheiro de arquivo.|
| __Soma de verificação__| Define o tipo a utilizar ao determinar se os dois ficheiros são as mesmas. Se __soma de verificação__ não for especificado, apenas o nome de ficheiro ou diretório é utilizado para comparação. Os valores válidos incluem: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate, none (predefinição). Se especificar __soma de verificação__ sem __validar__, a configuração irá falhar.|
| Certifique-se| Determina se deve verificar se o conteúdo do arquivo existe no __destino__. Defina esta propriedade como __presente__ para garantir que existe o conteúdo. Defina-o como __ausente__ para garantir que não existam. O valor predefinido é __presente__.|
| dependsOn | Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado. Por exemplo, se o ID do bloco de script de configuração de recursos que pretende executar primeiro ResourceName e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.|
| Validar| Utiliza a propriedade de soma de verificação para determinar se o arquivo corresponde à assinatura. Se especificar sem validar de soma de verificação, a configuração irá falhar. Se especificar validar sem soma de verificação, uma soma de verificação de SHA-256 é utilizada por predefinição.|
| Force| Determinadas operações de ficheiros (como substituir um ficheiro ou eliminar um diretório que não está vazio) resultará num erro. Utilizando a propriedade de imposição substitui esses erros. O valor predefinido é falso.|

## <a name="example"></a>Exemplo

O exemplo seguinte mostra como utilizar o recurso de arquivo para garantir que os conteúdos de um ficheiro de arquivo chamado Test.zip existem e que são extraídos num destino indicado.

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```