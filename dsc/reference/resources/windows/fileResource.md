---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recurso do ficheiro de DSC
ms.openlocfilehash: e5f7a91e5f19c8c7bbada090804d8f29a7cfedd5
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048750"
---
# <a name="dsc-file-resource"></a>Recurso do ficheiro de DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

O recurso de arquivo no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para gerir ficheiros e pastas no nó de destino.

>**Nota:** Se o **MatchSource** estiver definida como **$false** (que é o valor predefinido), o conteúdo seja copiado é colocadas em cache na primeira vez que a configuração é aplicada.
>Aplicativos subsequentes da configuração não verifica para ficheiros atualizados e/ou pastas no caminho especificado por **SourcePath**. Se pretende procurar atualizações para os ficheiros de e/ou pastas no **SourcePath** sempre que a configuração é aplicada, defina **MatchSource** para **$true**.

## <a name="syntax"></a>Sintaxe
```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
}
```

## <a name="properties"></a>Propriedades

|  Propriedade  |  Descrição   |
|---|---|
| DestinationPath| Indica a localização onde pretende garantir que o estado para um ficheiro ou diretório.|
| Atributos| Especifica o estado pretendido dos atributos do ficheiro de destino ou diretório.|
| Soma de verificação| Indica o tipo de soma de verificação a utilizar ao determinar se dois arquivos são os mesmos. Se __soma de verificação__ não for especificada, apenas o nome de ficheiro ou diretório é utilizado para comparação. Valores válidos incluem: SHA-1, SHA-256, SHA-512, colunas createdDate e modifiedDate.|
| Conteúdos| Especifica o conteúdo de um arquivo, como uma determinada cadeia de caracteres.|
| Credencial| Indica as credenciais que são necessárias para aceder aos recursos, tais como ficheiros de origem, se esse acesso for necessário.|
| Certifique-se| Indica se o ficheiro ou diretório existe. Defina esta propriedade como "Ausente", certifique-se de que o ficheiro ou diretório não existe. Defini-lo como "Presente" para se certificar de que o ficheiro ou diretório existe. A predefinição é "Presente".|
| Force| Determinadas operações de arquivo (como substituir um ficheiro ou eliminar um diretório que não está vazio) irão resultar num erro. Usando a propriedade de força substitui esses erros. O valor predefinido é __$false__.|
| Recurse| Indica se são incluídos os subdiretórios. Defina esta propriedade como __$true__ para indicar que pretende que o subdiretórios a serem incluídos. A predefinição é __$false__. **Tenha em atenção**: Esta propriedade só é válida quando o tipo de propriedade é definido como diretório.|
| DependsOn | Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será __ResourceName__ e seu tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.|
| SourcePath| Indica o caminho a partir da qual pretende copiar o recurso de ficheiro ou pasta.|
| Tipo| Indica se o recurso a ser configurado é um diretório ou de um ficheiro. Defina esta propriedade para o "Diretório" para indicar que o recurso é um diretório. Defini-lo como "File" para indicar que o recurso é um ficheiro. O valor predefinido é "Arquivo".|
| MatchSource| Se definido como o valor predefinido __$false__, em seguida, todos os ficheiros de origem (por exemplo, ficheiros A, B e C) serão adicionados para o destino na primeira vez que a configuração é aplicada. Se for adicionado um novo ficheiro (D) para a origem, este será não ser adicionado para o destino, mesmo quando a configuração é novamente aplicada mais tarde. Se o valor for __$true__, em seguida, sempre que a configuração é aplicada, são adicionados novos ficheiros, em seguida, foi encontrados na origem (por exemplo, ficheiro D neste exemplo) para o destino. O valor predefinido é **$false**.|

## <a name="example"></a>Exemplo

O exemplo seguinte mostra como usar o recurso de ficheiro para garantir que um diretório com o caminho `C:\Users\Public\Documents\DSCDemo\DemoSource` numa origem de computador (por exemplo, o servidor de "pull") também está presente (juntamente com todos os subdiretórios) no nó de destino. Ele também escreve uma mensagem confirmatory para o log quando estiver concluído e inclui uma instrução para se certificar de que a operação de verificação de ficheiros é executada antes da operação de registo.

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File".
            Recurse = $true # Ensure presence of subdirectories, too
            SourcePath = "C:\Users\Public\Documents\DSCDemo\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # This means run "DirectoryCopy" first.
        }
    }
}
```