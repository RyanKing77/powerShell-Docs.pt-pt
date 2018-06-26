---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Utilizar dados de configuração
ms.openlocfilehash: 9b0b213e2d71bfdb473fd98f8080de5c874c70e2
ms.sourcegitcommit: 68093cc12a7a22c53d11ce7d33c18622921a0dd1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/26/2018
ms.locfileid: "36940383"
---
# <a name="using-configuration-data-in-dsc"></a>A utilização de dados de configuração DSC

> Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

Ao utilizar o DSC incorporada **ConfigurationData** parâmetro, pode definir os dados que podem ser utilizados dentro de uma configuração.
Isto permite-lhe criar uma configuração única que pode ser utilizada para vários nós ou para os diferentes ambientes.
Por exemplo, se estiver a desenvolver uma aplicação, pode utilizar uma configuração para ambientes de desenvolvimento e de produção e utilizar dados de configuração para especificar os dados para cada ambiente.

Este tópico descreve a estrutura do **ConfigurationData** tabela hash.
Para obter exemplos de como utilizar os dados de configuração, consulte [separação de dados de configuração e ambiente](separatingEnvData.md).

## <a name="the-configurationdata-common-parameter"></a>O parâmetro comum de ConfigurationData

Uma configuração de DSC assume um parâmetro comum, **ConfigurationData**, que especifica quando compilar a configuração.
Para obter informações sobre configurações de compilação, consulte [configurações de DSC](configurations.md).

O **ConfigurationData** parâmetro é uma tabela hash que têm de ter, pelo menos, uma chave denominada **AllNodes**.
Também pode ter uma ou mais chaves.

> [!NOTE]
> Os exemplos neste tópico utilizam uma única chave adicional (que não seja o nomeado **AllNodes** chave) com o nome `NonNodeData`, mas pode incluir qualquer número de chaves adicionais e nome que pretende.

```powershell
$MyData =
@{
    AllNodes = @()
    NonNodeData = ""
}
```

O valor da **AllNodes** chave é uma matriz. Cada elemento da matriz deste também é uma tabela hash que têm de ter, pelo menos, uma chave denominada **NodeName**:

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

Pode adicionar outras chaves para cada tabela hash, bem como:

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
Por exemplo, para cada nó de dar um `LogPath` propriedade, pode efetuar este procedimento:

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

Este é o equivalente da adição de uma propriedade com um nome de `LogPath` com um valor de `"C:\Logs"` para cada um dos outros blocos de (`VM-1`, `VM-2`, e `VM-3`).

## <a name="defining-the-configurationdata-hashtable"></a>Definir a tabela hash ConfigurationData

Pode definir **ConfigurationData** como uma variável no mesmo ficheiro de script como um configuration (tal como nos nossos exemplos anteriores) ou um separado `.psd1` ficheiro.
Para definir **ConfigurationData** num `.psd1` de ficheiros, criar um ficheiro que contém apenas a tabela hash que representa os dados de configuração.

Por exemplo, pode criar um ficheiro denominado `MyData.psd1` com o seguinte conteúdo:

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

Para compilar uma configuração para o qual definiu os dados de configuração, transmitir os dados de configuração como o valor de **ConfigurationData** parâmetro.

Esta ação irá criar um ficheiro MOF para cada entrada no **AllNodes** matriz.
Cada ficheiro MOF será nomeado com o `NodeName` propriedade da entrada de matriz correspondentes.

Por exemplo, se definir dados de configuração como no `MyData.psd1` ficheiro acima, compilar uma configuração criaria ambos `VM-1.mof` e `VM-2.mof` ficheiros.

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a>Compilar uma configuração com os dados de configuração utilizando uma variável

Para utilizar dados de configuração que estão definidos como uma variável na mesma `.ps1` ficheiros como a configuração, transmitir o nome da variável como o valor a **ConfigurationData** parâmetro ao compilar a configuração:

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a>Compilar uma configuração com os dados de configuração através de um ficheiro de dados

Para utilizar dados de configuração que estão definidos num ficheiro. psd1, passar o caminho e nome desse ficheiro como o valor de **ConfigurationData** parâmetro ao compilar a configuração:

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a>Utilizar variáveis de ConfigurationData numa configuração

O DSC fornece três variáveis especiais que podem ser utilizadas um script de configuração: **$AllNodes**, **$Node**, e **$ConfigurationData**.

- **$AllNodes** refere-se para o conjunto completo de nós definido no **ConfigurationData**. Pode filtrar o **AllNodes** coleção utilizando **. WHERE()** e **. ForEach()**.
- **Nó** refere-se a uma entrada específico no **AllNodes** coleção depois-é filtrado utilizando **. WHERE()** ou **. ForEach()**.
  - Pode ler mais sobre estes métodos em [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)
- **ConfigurationData** refere-se a tabela hash completo que é transmitida como o parâmetro ao compilar uma configuração.

## <a name="using-non-node-data"></a>Utilização de dados do nó não

Como podemos viu nos exemplos anteriores, o **ConfigurationData** tabela hash pode ter uma ou mais chaves para além de necessários **AllNodes** chave.
Nos exemplos neste tópico, podemos ter utilizado apenas um único nó adicional e com o mesmo nome `NonNodeData`.
No entanto, pode definir qualquer número de chaves adicionais e nome tudo o que pretende.

Para obter um exemplo de utilização de dados do nó não, consulte [separação de dados de configuração e ambiente](separatingEnvData.md).

## <a name="see-also"></a>Consulte Também

- [Opções de credenciais nos dados de configuração](configDataCredentials.md)
- [Configurações de DSC](configurations.md)