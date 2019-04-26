---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recurso do ficheiro de DSC
ms.openlocfilehash: b5bc2c305b8cfccbd044274811df631264a24279
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077335"
---
# <a name="dsc-file-resource"></a>Recurso do ficheiro de DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

O recurso de arquivo no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para gerir ficheiros e pastas no nó de destino. O **DestinationPath** e **SourcePath** têm ambos de estar acessíveis pelo nó de destino.

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

|Propriedade       |Descrição                                                                   |Necessária|Predefinido|
|---------------|------------------------------------------------------------------------------|--------|-------|
|DestinationPath|A localização, no nó de destino, deseja garantir é `Present` ou `Absent`.|Sim|Não|
|Atributos     |O estado pretendido dos atributos do ficheiro de destino ou diretório. Os valores válidos são **arquivo**, **Hidden**, **só de leitura**, e **sistema**.|Não|Nenhum|
|Checksum      |O tipo de soma de verificação a utilizar ao determinar se dois arquivos são os mesmos. Valores válidos incluem: SHA-1, SHA-256, SHA-512, colunas createdDate e modifiedDate.|Não|Apenas o nome de ficheiro ou diretório é comparado.|
|Conteúdos       |Só é válida quando utilizada com `File` tipo. Indica o conteúdo para Certifique-se está `Present` ou `Absent` do ficheiro de destino. |Não|Nenhum|
|Credencial     |As credenciais que são necessárias para aceder aos recursos, tais como ficheiros de origem.|Não|Conta de computador do nó de destino. (*consulte nota*)|
|Certifique-se         |O estado pretendido do ficheiro de destino ou diretório. |Não|**Presente**|
|Force          |Substitui as operações de acesso que resultariam num erro (como substituir um ficheiro ou eliminar um diretório que não está vazio).|Não|`$false`|
|Recurse        |Só é válida quando utilizada com `Directory` tipo. Executa o recursivamente de operação de estado para todos os subdiretórios.|Não|`$false`|
|DependsOn      |Define uma dependência de recursos especificados. Este recurso só será executado após a execução bem-sucedida de todos os recursos dependentes. Pode especificar recursos dependentes, utilizando a sintaxe `"[ResourceType]ResourceName"`. Consulte [about_DependsOn](../../../configurations/resource-depends-on.md)|Não|Nenhum|
|SourcePath     |O caminho a partir da qual pretende copiar o recurso de ficheiro ou pasta.|Não|Nenhum|
|Tipo           |O tipo de recurso que está a ser configurado. Os valores válidos são `Directory` e `File`.|Não|`File`|
|MatchSource    |Determina se o recurso deve monitorizar para novos ficheiros adicionados para o diretório de origem após a cópia inicial. Um valor de `$true` indica que, após a cópia inicial, quaisquer novos ficheiros de origem devem ser copiados para o destino. Se definido como `$False`, o recurso coloca em cache o conteúdo do diretório de origem e ignora todos os ficheiros adicionados após a cópia inicial.|Não|`$false`|

> [!WARNING]
> Se não especificar um valor para `Credential` ou `PSRunAsCredential` (PS V.5), o recurso irá utilizar a conta de computador do nó de destino para aceder a `SourcePath`.  Quando o `SourcePath` é um UNC da partilha, isto pode resultar num erro "Acesso negado". Certifique-se as suas permissões são definidas em conformidade ou utilizam o `Credential` ou `PSRunAsCredential` propriedades para especificar a conta que deve ser utilizada.

## <a name="present-vs-absent"></a>Apresentar vs. Ausente

Cada recurso de DSC realiza operações diferentes com base no valor especificado para o `Ensure` propriedade. Os valores que especifica para as propriedades acima determina a operação de estado executada.

### <a name="existence"></a>Existência

Quando apenas especificar uma `DestinationPath`, o recurso garante que o caminho existe (`Present`) ou não existe (`Absent`).

### <a name="copy-operations"></a>Operações de cópia

Quando especificar uma `SourcePath` e uma `DestinationPath` com um `Type` o valor de **Directory**, o diretório de origem de cópias de recursos para o caminho de destino. As propriedades `Recurse`, `Force`, e `MatchSource` alterar o tipo de operação de cópia efetuada, embora `Credential` determina a conta a utilizar para aceder ao diretório de origem.

### <a name="limitations"></a>Limitações

Se tiver especificado um valor de `ReadOnly` para o `Attributes` propriedade em conjunto com um `DestinationPath`, `Ensure = "Present"` criaria o caminho especificado, enquanto `Contents` definiria o conteúdo do ficheiro.  Uma `Absent` ignorará a operação de estado a `Attributes` propriedade totalmente e remover qualquer ficheiro no caminho especificado.

## <a name="example"></a>Exemplo

O exemplo seguinte copia um diretório e respetivos subdiretórios de um servidor de solicitação para um nó de destino usando o recurso do ficheiro. Se a operação for bem-sucedida, o recurso de Log escreve uma mensagem de confirmação para o registo de eventos.

O diretório de origem é um caminho UNC (`\\PullServer\DemoSource`) partilhado do servidor de solicitação. O `Recurse` propriedade garante que todos os subdiretórios são copiados também.

> [!IMPORTANT]
> O LCM no nó de destino é executado no contexto da conta do sistema local por predefinição. Para conceder acesso para o **SourcePath**, conceder permissões adequadas de conta de computador do nó de destino. O **credencial** e **PSDSCRunAsCredential** (v5) alterar ambas as utilizações de contexto o LCM para acessar o **SourcePath**. Ainda tem de conceder acesso à conta que será utilizado para aceder a **SourcePath**.

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present" # Ensure the directory is Present on the target node.
            Type = "Directory" # The default is File.
            Recurse = $true # Recursively copy all subdirectories.
            SourcePath = "\\PullServer\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # Depends on successful execution of the File resource.
        }
    }
}
```

Para outros, usando on **credenciais** Consulte DSC [executar como usuário](../../../configurations/runAsUser.md) ou [credenciais de dados de configuração](../../../configurations/configDataCredentials.md).
