---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Utilizar dados de configuração
ms.openlocfilehash: f2d25b9ced805fb4c91378ebfe840104eb6ce52a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684424"
---
# <a name="using-configuration-data-in-dsc"></a>Utilizar os dados de configuração no DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

Ao utilizar o DSC incorporada **ConfigurationData** parâmetro, pode definir os dados que podem ser utilizados dentro de uma configuração.
Isto permite-lhe criar uma configuração única que pode ser utilizada para vários nós ou para ambientes diferentes.
Por exemplo, se estiver a desenvolver uma aplicação, pode utilizar uma configuração para ambientes de desenvolvimento e produção e utilizar dados de configuração para especificar os dados para cada ambiente.

Este tópico descreve a estrutura do **ConfigurationData** hashtable.
Para obter exemplos de como utilizar os dados de configuração, consulte [separação de dados de configuração e ambiente](separatingEnvData.md).

## <a name="the-configurationdata-common-parameter"></a>O parâmetro comum de ConfigurationData

Uma configuração de DSC assume um parâmetro comum, **ConfigurationData**, que especifica quando compilar a configuração.
Para obter informações sobre como compilar configurações, consulte [configurações de DSC](configurations.md).

O **ConfigurationData** parâmetro é uma tabela de hash tem de ter pelo menos uma chave denominada **AllNodes**.
Ele também pode ter uma ou mais chaves.

> [!NOTE]
> Os exemplos neste tópico utilizam uma única chave adicional (que não seja o nomeado **AllNodes** chave) com o nome `NonNodeData`, mas pode incluir qualquer número de chaves adicionais e nomeá-los que quiser.

```powershell
$MyData =
@{
    AllNodes = @()
    NonNodeData = ""
}
```

O valor do **AllNodes** chave é uma matriz. Cada elemento dessa matriz também é uma tabela de hash que tem de ter pelo menos uma chave com o nome **NodeName**:

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
        },


        @{
            NodeName = "VM-2"
        },


        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""
}
```

Pode adicionar outras chaves para cada tabela de hash também:

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
        },


        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },


        @{
            NodeName = "VM-3"
            Role     = "WebServer"
        }
    );

    NonNodeData = ""
}
```

Para aplicar uma propriedade a todos os nós, pode criar um membro do **AllNodes** matriz que tenha um **NodeName** de `*`.
Por exemplo, para dar a cada nó um `LogPath` propriedade, pode fazer isso:

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName     = "*"
            LogPath      = "C:\Logs"
        },


        @{
            NodeName     = "VM-1"
            Role         = "WebServer"
            SiteContents = "C:\Site1"
            SiteName     = "Website1"
        },


        @{
            NodeName     = "VM-2"
            Role         = "SQLServer"
        },


        @{
            NodeName     = "VM-3"
            Role         = "WebServer"
            SiteContents = "C:\Site2"
            SiteName     = "Website3"
        }
    );
}
```

Isso é o equivalente da adição de uma propriedade com o nome `LogPath` com um valor de `"C:\Logs"` a cada um dos outros blocos de (`VM-1`, `VM-2`, e `VM-3`).

## <a name="defining-the-configurationdata-hashtable"></a>Definir a tabela de hash de ConfigurationData

Pode definir **ConfigurationData** como uma variável dentro do mesmo arquivo de script como uma configuração (tal como nos nossos exemplos anteriores) ou num separado `.psd1` ficheiro.
Para definir **ConfigurationData** num `.psd1` de ficheiros, crie um ficheiro que contém apenas a tabela de hash que representa os dados de configuração.

Por exemplo, pode criar um arquivo chamado `MyData.psd1` com o seguinte conteúdo:

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        },

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

## <a name="compiling-a-configuration-with-configuration-data"></a>Compilar uma configuração com dados de configuração

Para compilar uma configuração para o qual definiu dados de configuração, tem de transmitir os dados de configuração como o valor do **ConfigurationData** parâmetro.

Esta ação irá criar um ficheiro MOF para cada entrada o **AllNodes** matriz.
Cada ficheiro MOF será nomeado com o `NodeName` propriedade de entrada de matriz correspondentes.

Por exemplo, se definir dados de configuração, como mostra a `MyData.psd1` ficheiro acima, compilar uma configuração criaria ambos `VM-1.mof` e `VM-2.mof` ficheiros.

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a>Compilar uma configuração com os dados de configuração usando uma variável

Utilizar dados de configuração que estão definidos como uma variável no mesmo `.ps1` ficheiro como a configuração, passa o nome da variável como o valor do **ConfigurationData** parâmetro ao compilar a configuração:

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a>Compilar uma configuração com os dados de configuração através de um ficheiro de dados

Para utilizar dados de configuração que são definidos num ficheiro. psd1, passe o caminho e nome de arquivo como o valor do **ConfigurationData** parâmetro ao compilar a configuração:

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a>Usando variáveis de ConfigurationData numa configuração

DSC fornece as seguintes variáveis especiais que podem ser usadas num script de configuração:

- **$AllNodes** refere-se a toda a coleção de nós definida no **ConfigurationData**. Pode filtrar os **AllNodes** coleção utilizando **. WHERE()** e **. Foreach ()**.
- **ConfigurationData** refere-se a tabela de hash de inteiro que é passada como parâmetro ao compilar uma configuração.
- **MyTypeName** contém o [configuração](configurations.md) nome de variável é utilizado. Por exemplo, na configuração do `MyDscConfiguration`, o `$MyTypeName` terá um valor de `MyDscConfiguration`.
- **Nó** refere-se para uma entrada no **AllNodes** coleção depois que ele é filtrado através da utilização **. WHERE()** ou **. Foreach ()**.
  - Pode ler mais sobre estes métodos em [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)

## <a name="using-non-node-data"></a>Utilizar os dados de nós não

Como vimos nos exemplos anteriores, o **ConfigurationData** hashtable pode ter uma ou mais chaves para além do necessário **AllNodes** chave.
Nos exemplos neste tópico, temos usado apenas um único nó adicional e o nome de `NonNodeData`.
No entanto, pode definir qualquer número de chaves adicionais e nomeá-los que quiser.

Para obter um exemplo da utilização de dados não-nó, veja [separação de dados de configuração e ambiente](separatingEnvData.md).

## <a name="see-also"></a>Consulte Também

- [Opções de credenciais nos dados de configuração](configDataCredentials.md)
- [Configurações de DSC](configurations.md)