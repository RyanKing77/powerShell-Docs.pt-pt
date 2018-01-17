---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Recursos de DSC ficheiro
ms.openlocfilehash: 54d01bf0769eeed0354606eb3543973b0f850a6f
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-file-resource"></a>Recursos de DSC ficheiro

> Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

O recurso de ficheiros no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para gerir ficheiros e pastas no nó de destino.

>**Nota:** se o **MatchSource** propriedade está definida como **$false** (que é o valor predefinido), o conteúdo a ser copiado é colocadas em cache na primeira vez que a configuração é aplicada. 
>Aplicações subsequentes da configuração não verifica os ficheiros atualizados e/ou pastas no caminho especificado por **SourcePath**. Se quiser verificar a existência de atualizações a ficheiros e/ou pastas **SourcePath** sempre que a configuração é aplicada, defina **MatchSource** para **$true**. 

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
| DestinationPath| Indica a localização onde pretende garantir o estado de um ficheiro ou diretório.| 
| Atributos| Especifica o estado pretendido de atributos para o destino de ficheiro ou diretório.| 
| Soma de verificação| Indica o tipo de soma de verificação a utilizar ao determinar se os dois ficheiros são as mesmas. Se __soma de verificação__ não for especificado, apenas o nome de ficheiro ou diretório é utilizado para comparação. Os valores válidos incluem: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.| 
| Conteúdos| Especifica o conteúdo de um ficheiro, como uma cadeia específica.| 
| credencial| Indica as credenciais que são necessárias para aceder a recursos, tais como ficheiros de origem, se for necessário esse acesso.| 
| Certifique-se| Indica se o ficheiro ou diretório existe. Defina esta propriedade para "Ausente", certifique-se de que o ficheiro ou diretório não existe. Defina-o para "Presente" para se certificar de que o ficheiro ou diretório existe. A predefinição é "Presente".| 
| Force| Determinadas operações de ficheiros (como substituir um ficheiro ou eliminar um diretório que não está vazio) resultará num erro. Utilizando a propriedade de imposição substitui esses erros. O valor predefinido é __$false__.| 
| Recurse| Indica se subdiretórios estão incluídos. Defina esta propriedade como __$true__ para indicar que pretende que o subdiretórios a incluir. A predefinição é __$false__. **Tenha em atenção**: Esta propriedade só é válida quando a propriedade Type é definida ao diretório.| 
| dependsOn | Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado. Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.| 
| SourcePath| Indica o caminho a partir dos quais pretende copiar o recurso do ficheiro ou pasta.| 
| Tipo| Indica se o recurso que está a ser configurado um diretório ou um ficheiro. Defina esta propriedade para "Diretório" para indicar que o recurso é um diretório. Defina-o para "Ficheiro" para indicar que o recurso é um ficheiro. O valor predefinido é "Ficheiro".| 
| MatchSource| Se definir o valor predefinido de __$false__, em seguida, todos os ficheiros de origem (diga, os ficheiros A, B e C) serão adicionados para o destino na primeira vez que a configuração é aplicada. Se for adicionado um novo ficheiro (D) para a origem, que será não ser adicionado para o destino, mesmo quando a configuração é novamente aplicada mais tarde. Se o valor for __$true__, em seguida, sempre que a configuração é aplicada, são adicionados novos ficheiros, subsequentemente, foi encontrados na origem (por exemplo, o ficheiro D neste exemplo) para o destino. O valor predefinido é **$false**.| 

## <a name="example"></a>Exemplo

O exemplo seguinte mostra como utilizar o recurso do ficheiro para garantir que um diretório com o caminho `C:\Users\Public\Documents\DSCDemo\DemoSource` numa origem de computador (por exemplo, o servidor "solicitação") encontra-se também (juntamente com todos os subdiretórios) no nó de destino. Também escreve uma mensagem confirmatory no registo concluído e inclui uma instrução para se certificar de que a operação de verificação do ficheiro é executado antes da operação de registo.

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

