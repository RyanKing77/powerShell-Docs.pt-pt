---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recurso Archive de DSC
ms.openlocfilehash: d5ccd242d000a0907c6768f30923764be6bf20a3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077556"
---
# <a name="dsc-archive-resource"></a>Recurso Archive de DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

O recurso de arquivo no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para descompactar os ficheiros de arquivo (. zip) num caminho específico.

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
| Destino| Especifica a localização onde pretende Certifique-se de que o conteúdo do arquivo é extraído.|
| Caminho| Especifica o caminho de origem do ficheiro de arquivo.|
| __Checksum__| Define o tipo a utilizar ao determinar se dois arquivos são os mesmos. Se __soma de verificação__ não for especificada, apenas o nome de ficheiro ou diretório é utilizado para comparação. Valores válidos incluem: SHA-1, SHA-256, SHA-512, colunas createdDate e modifiedDate, nenhum (predefinição). Se especificar __soma de verificação__ sem __Validate__, a configuração irá falhar.|
| Certifique-se| Determina se deve verificar se o conteúdo do arquivo existe no __destino__. Defina esta propriedade como __presente__ para garantir que existe o conteúdo. Defina-o como __ausente__ para garantir que não existam. O valor predefinido é __presente__.|
| DependsOn | Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Por exemplo, se o ID de bloco de script de configuração de recursos que pretende executar primeiro for ResourceName e seu tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.|
| Validar| Usa a propriedade de soma de verificação para determinar se o arquivo corresponde à assinatura. Se especificar a soma de verificação sem validar, a configuração irá falhar. Se especificar validar sem a soma de verificação, uma soma de verificação de SHA-256 é utilizada por predefinição.|
| Force| Determinadas operações de arquivo (como substituir um ficheiro ou eliminar um diretório que não está vazio) irão resultar num erro. Usando a propriedade de força substitui esses erros. O valor predefinido é False.|

## <a name="example"></a>Exemplo

O exemplo seguinte mostra como usar o recurso de arquivo para garantir que o conteúdo de um ficheiro de arquivo chamado Test.zip existe e que é extraído num determinado destino.

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```