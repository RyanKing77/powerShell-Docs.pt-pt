---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Configurações de DSC
ms.openlocfilehash: 171068acb51f44e31c81e63f6640222ef71bee38
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093699"
---
# <a name="dsc-configurations"></a>Configurações de DSC

> Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

As configurações de DSC são scripts do PowerShell que definem um tipo especial de função.
Para definir uma configuração, use a palavra-chave do PowerShell **configuração**.

```powershell
Configuration MyDscConfiguration {
    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = 'Present'
            Name = 'RSAT'
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}
MyDscConfiguration
```

Salve o script como um ficheiro. ps1.

## <a name="configuration-syntax"></a>Sintaxe de configuração

Um script de configuração consiste nas seguintes partes:

- O **configuração** bloco. Este é o bloco de scripts mais externo. Defini-lo utilizando o **configuração** palavra-chave e fornecer um nome. Neste caso, o nome da configuração é "MyDscConfiguration".
- Um ou mais **nó** blocos. Elas definem os nós (VMs ou computadores) que está a configurar. Na configuração acima, há um **nó** bloco que se destina a um computador com o nome "TEST-PC1".
- Um ou mais blocos de recursos. Trata-se em que a configuração define as propriedades dos recursos de que está a configurar. Neste caso, existem dois blocos de recursos, cada um dos quais chamar o recurso de "WindowsFeature".

Dentro de um **configuração** bloco, pode fazer tudo o que poderia normalmente numa função do PowerShell. Por exemplo, no exemplo anterior, se não quisesse duro codificar o nome do computador de destino na configuração, poderia adicionar um parâmetro para o nome do nó:

```powershell
Configuration MyDscConfiguration {
    param(
        [string[]]$ComputerName='localhost'
    )
    Node $ComputerName {
        WindowsFeature MyFeatureInstance {
            Ensure = 'Present'
            Name = 'RSAT'
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}
MyDscConfiguration -ComputerName $ComputerName
```

Neste exemplo, especificar o nome do nó, passando-o como o **ComputerName** parâmetro quando compilar a configuração. O nome padrão é "localhost".

## <a name="compiling-the-configuration"></a>Compilar a configuração

Antes de pode aplicá uma configuração, deve compilá-lo num documento do MOF.
Pode fazê-lo ao chamar a configuração, como chamaria uma função do PowerShell.
A última linha do exemplo que contém apenas o nome da configuração, chama a configuração.

> [!NOTE]
> Para chamar uma configuração, a função deve estar no âmbito global (tal como acontece com qualquer outra função do PowerShell).
> Pode fazer esta acontecer tanto por "dot sourcing" o script, ou ao executar o script de configuração usando F5 ou clicar no **executar Script** botão no ISE.
> A origem de ponto o script, execute o comando `. .\myConfig.ps1` onde `myConfig.ps1` é o nome do ficheiro de script que contém a configuração.

Quando chama a configuração, ele:

- Resolve todas as variáveis
- Cria uma pasta no diretório atual com o mesmo nome que a configuração.
- Cria um ficheiro denominado _NodeName_arquivos. MOF no novo diretório, onde _NodeName_ é o nome do nó de destino da configuração.
  Se houver mais do que um de nós, será criado um ficheiro MOF para cada nó.

> [!NOTE]
> O ficheiro MOF contém todas as informações de configuração para o nó de destino. Por este motivo, é importante para mantê-lo seguro.
> Para obter mais informações, consulte [proteger o ficheiro MOF](secureMOF.md).

Compilar a configuração do primeiro acima resultados na estrutura da pasta seguinte:

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

Se a configuração assume um parâmetro, como no segundo exemplo, que deve ser fornecida no momento da compilação. Aqui está como que teria o aspeto:

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

## <a name="using-dependson"></a>Usando DependsOn

É uma palavra-chave de DSC útil **DependsOn**. Normalmente, (embora não necessariamente sempre), DSC aplica-se os recursos na ordem em que aparecem na configuração do.
No entanto, **DependsOn** Especifica qual a que recursos dependem de outros recursos e o LCM assegura que são aplicadas na ordem correta, independentemente da ordem na qual o recurso instâncias são definidas.
Por exemplo, uma configuração pode especificá-lo uma instância do **usuário** recurso depende da existência de um **grupo** instância:

```powershell
Configuration DependsOnExample {
    Node Test-PC1 {
        Group GroupExample {
            Ensure = 'Present'
            GroupName = 'TestGroup'
        }

        User UserExample {
            Ensure = 'Present'
            UserName = 'TestUser'
            FullName = 'TestUser'
            DependsOn = '[Group]GroupExample'
        }
    }
}
```

## <a name="using-new-resources-in-your-configuration"></a>Utilizar os novos recursos na sua configuração

Se tiver executado os exemplos anteriores, deve ter observado que foram avisado que estava a utilizar um recurso sem explicitamente importá-lo.
Hoje em dia, DSC é fornecido com 12 recursos como parte do módulo PSDesiredStateConfiguration.
Outros recursos em módulos externos têm de ser colocados num `$env:PSModulePath` para ser reconhecido pelo LCM.
Um novo cmdlet [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), pode ser utilizado para determinar quais recursos estão instalados no sistema e disponível para utilização pelo LCM.
Depois destes módulos foram colocados num `$env:PSModulePath` e são reconhecidos corretamente pelo [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), ainda precisam ser carregadas na sua configuração.
**Import-DscResource** é uma palavra-chave dinâmica que só possa ser reconhecida dentro de um **configuração** bloco (ou seja, não é um cmdlet).
**Import-DscResource** suporta dois parâmetros:

- **ModuleName** é a forma recomendada de usar **Import-DscResource**. Ele aceita o nome do módulo que contém os recursos a serem importados (bem como uma matriz de cadeia de caracteres de nomes de módulos).
- **Nome** é o nome do recurso para importar. Não é o nome amigável retornado como "Name" ao [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), mas o nome da classe usado ao definir o esquema de recursos (retornados como **ResourceType** por [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx)).

## <a name="see-also"></a>Consulte Também

- [Windows PowerShell Desired State Configuration descrição-geral](overview.md)
- [Recursos de DSC](resources.md)
- [Configurar o Gestor de configuração Local](metaConfig.md)