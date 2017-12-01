---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Configurações de DSC"
ms.openlocfilehash: c0cf0e7aa1d18898c50a0662e4fc76ab02932f08
ms.sourcegitcommit: 7bb75bfb8d12aaa6b6071dcb2ca639d4ecceef26
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2017
---
# <a name="dsc-configurations"></a>Configurações de DSC

>Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

Configurações de DSC são scripts do PowerShell que definem um tipo especial de função. Para definir uma configuração, pode utilizar a palavra-chave do PowerShell **configuração**.

```powershell
Configuration MyDscConfiguration {

    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
MyDscConfiguration

```

Guarde o script como um ficheiro. ps1.

## <a name="configuration-syntax"></a>Sintaxe de configuração

Um script de configuração consiste dos seguintes partes:

- O **configuração** bloco. Este é o bloco de scripts mais exterior. Defini-lo utilizando o **configuração** palavra-chave e fornecer um nome. Neste caso, o nome da configuração é "MyDscConfiguration".
- Um ou mais **nó** blocos. Estes definem os nós (computadores ou VMs) que está a configurar. Na configuração acima, há um **nó** bloco destina-se um computador com o nome "PC1 de teste".
- Um ou mais bloqueios de recursos. Este é onde a configuração define as propriedades de recursos que está a configurar. Neste caso, existem dois blocos de recursos, cada um dos quais chamar o recurso "WindowsFeature".

Dentro de um **configuração** bloco, que pode fazer tudo o que lhe foi normalmente de uma função do PowerShell. Por exemplo, no exemplo anterior, se não pretender rígido code o nome do computador de destino na configuração, pode adicionar um parâmetro para o nome de nó:

```powershell
Configuration MyDscConfiguration {

    param(
        [string[]]$ComputerName="localhost"
    )
    Node $ComputerName {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
MyDscConfiguration

```

Neste exemplo, especifique o nome do nó transferindo-a como o **ComputerName** parâmetro ao compilar o configuraton. A nome assume a predefinição "localhost".

## <a name="compiling-the-configuration"></a>Compilar a configuração

Antes de pode enact uma configuração, tem de compilá-la para um documento MOF. Fazê-lo ao chamar a configuração como faria com uma função do PowerShell.  
A última linha do exemplo que contém apenas o nome da configuração, chama a configuração.

>**Nota:** para chamar uma configuração, a função tem de ser no âmbito global (tal como acontece com qualquer outra função do PowerShell). 
>Pode efetuar esta acontecer optar por "dot-sourcing" o script, ou ao executar o script de configuração ao utilizar F5 ou clicando no **executar Script** botão no ISE do. 
>A origem de ponto de script, execute o comando `. .\myConfig.ps1` onde `myConfig.ps1` é o nome do ficheiro de script que contém a configuração.

Quando chamar a configuração,-lo:

- Resolve todas as variáveis 
- Cria uma pasta no diretório atual com o mesmo nome que a configuração.
- Cria um ficheiro denominado _NodeName_. MOF no novo diretório, onde _NodeName_ é o nome do nó de destino da configuração. 
    Se existir mais do que um de nós, será criado um ficheiro MOF para cada nó.

>**Tenha em atenção**: ficheiro MOF o contém todas as informações de configuração para o nó de destino. Por este motivo, é importante manter segura. 
>Para obter mais informações, consulte [proteger o ficheiro MOF](secureMOF.md).

Compilar a configuração do primeiro acima resultados na estrutura da pasta seguintes:

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name                                                                                              
----                -------------         ------ ----                                                                                         
-a----       10/23/2015   4:32 PM           2842 localhost.mof
```  

Se a configuração utiliza um parâmetro, como no exemplo segundo, que tem de ser fornecido no momento da compilação. Segue-se que seria aspeto:

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration -ComputerName 'MyTestNode'
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name                                                                                              
----                -------------         ------ ----                                                                                         
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```      

## <a name="using-dependson"></a>Utilizar DependsOn

É uma palavra-chave de DSC útil **DependsOn**. Normalmente, (embora, não necessariamente sempre), DSC aplica-se os recursos na ordem em que aparecem dentro da configuração. No entanto, **DependsOn** Especifica qual a que recursos dependem de outros recursos e o MMC assegura que são aplicadas pela ordem correta, independentemente da ordem pela qual o recurso instâncias são definidas. Por exemplo, de uma configuração poderá especificar que uma instância do **utilizador** recursos dependem da existência de um **grupo** instância:

```powershell
Configuration DependsOnExample {
    Node Test-PC1 {
        Group GroupExample {
            Ensure = "Present"
            GroupName = "TestGroup"
        }

        User UserExample {
            Ensure = "Present"
            UserName = "TestUser"
            FullName = "TestUser"
            DependsOn = "[Group]GroupExample"
        }
    }
}

```

## <a name="using-new-resources-in-your-configuration"></a>Utilização de novos recursos na sua configuração

Se tiver executado os exemplos anteriores, poderá ter reparado que foram avisado que estava a utilizar um recurso sem explicitamente importá-lo.
Hoje em dia, DSC é fornecido com 12 recursos como parte do módulo PSDesiredStateConfiguration. Outros recursos em módulos externos tem de ser colocados numa `$env:PSModulePath` para poder ser reconhecido pelo MMC. Um novo cmdlet [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), pode ser utilizado para determinar os recursos que estão instalados no sistema e disponível para utilização pelo MMC. Depois destes módulos foram colocados no `$env:PSModulePath` e corretamente são reconhecidos pelo [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), têm de ser carregado dentro da sua configuração. 
**Importar DscResource** é uma palavra-chave dinâmica que só pode ser reconhecida dentro de um **configuração** blocos (ou seja, não é um cmdlet). 
**Importar DscResource** suporta dois parâmetros:
- **ModuleName** é a forma recomendada de utilização **importação DscResource**. Aceita o nome do módulo que contém os recursos a serem importados (bem como uma matriz de cadeia de nomes de módulo). 
- **Nome** é o nome do recurso para importar. Não é o nome amigável devolvido como "Name" por [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), mas o nome de classe utilizado quando definir o esquema de recursos (devolvido como **ResourceType** por [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)). 

## <a name="see-also"></a>Consulte Também
* [Descrição geral da configuração do estado pretendido do Windows PowerShell](overview.md)
* [Recursos de DSC](resources.md)
* [Configurar o Gestor de configuração Local](metaConfig.md)

