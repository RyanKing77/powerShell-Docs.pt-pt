---
ms.date: 12/12/2018
keywords: DSC, powershell, configuração, a configuração
title: Configurações de DSC
ms.openlocfilehash: 6af27f442de3080facd65892c713c989d0e388c5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404968"
---
# <a name="dsc-configurations"></a>Configurações de DSC

> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

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

Guarde o script como um `.ps1` ficheiro.

## <a name="configuration-syntax"></a>Sintaxe de configuração

Um script de configuração consiste nas seguintes partes:

- O **configuração** bloco. Este é o bloco de scripts mais externo. Defini-lo utilizando o **configuração** palavra-chave e fornecer um nome. Neste caso, o nome da configuração é "MyDscConfiguration".
- Um ou mais **nó** blocos. Elas definem os nós (VMs ou computadores) que está a configurar. Na configuração acima, há um **nó** bloco que se destina a um computador com o nome "TEST-PC1". O bloco de nó pode aceitar vários nomes de computador.
- Um ou mais blocos de recursos. Trata-se em que a configuração define as propriedades dos recursos de que está a configurar. Neste caso, existem dois blocos de recursos, cada um dos quais chamar o recurso de "WindowsFeature".

Dentro de um **configuração** bloco, pode fazer tudo o que poderia normalmente numa função do PowerShell. Por exemplo, no exemplo anterior, se não quisesse duro codificar o nome do computador de destino na configuração, poderia adicionar um parâmetro para o nome do nó:

Neste exemplo, especificar o nome do nó, passando-o como o **ComputerName** parâmetro quando compilar a configuração. O nome padrão é "localhost".

```powershell
Configuration MyDscConfiguration
{
    param
    (
        [string[]]$ComputerName='localhost'
    )

    Node $ComputerName
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

O **nó** bloco também pode aceitar vários nomes de computador. No exemplo acima, pode utilizar o `-ComputerName` parâmetro ou pass um separados por vírgulas lista de computadores diretamente para o **nó** bloco.

```powershell
MyDscConfiguration -ComputerName "localhost", "Server01"
```

Quando especificar uma lista de computadores para o **nó** bloco, de dentro de uma configuração, precisa usar notação de matriz.

```powershell
Configuration MyDscConfiguration
{
    Node @('localhost', 'Server01')
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

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
  Se houver mais de um nó, será criado um ficheiro MOF para cada nó.

> [!NOTE]
> O ficheiro MOF contém todas as informações de configuração para o nó de destino. Por este motivo, é importante para mantê-lo seguro.
> Para obter mais informações, consulte [proteger o ficheiro MOF](../pull-server/secureMOF.md).

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

## <a name="using-new-resources-in-your-configuration"></a>Utilizar os novos recursos na sua configuração

Se tiver executado os exemplos anteriores, deve ter observado que foram avisado que estava a utilizar um recurso sem explicitamente importá-lo.
Hoje em dia, DSC é fornecido com 12 recursos como parte do módulo PSDesiredStateConfiguration.

O cmdlet [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), pode ser utilizado para determinar quais recursos estão instalados no sistema e disponível para utilização pelo LCM.
Depois destes módulos foram colocados num `$env:PSModulePath` e são reconhecidos corretamente pelo [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), ainda precisam ser carregadas na sua configuração.

**Import-DscResource** é uma palavra-chave dinâmica que só possa ser reconhecida dentro de um **configuração** bloco, ele não seja um cmdlet.
**Import-DscResource** suporta dois parâmetros:

- **ModuleName** é a forma recomendada de usar **Import-DscResource**. Ele aceita o nome do módulo que contém os recursos a serem importados (bem como uma matriz de cadeia de caracteres de nomes de módulos).
- **Nome** é o nome do recurso para importar. Não é o nome amigável retornado como "Name" ao [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), mas o nome da classe usado ao definir o esquema de recursos (retornados como **ResourceType** por [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).

Para obter mais informações sobre como usar `Import-DSCResource`, consulte [Import-DSCResource usando](import-dscresource.md)

## <a name="powershell-v4-and-v5-differences"></a>Diferenças de PowerShell v4 e v5

Existem diferenças no onde os recursos de DSC precisam ser armazenada no PowerShell 4.0. Para obter mais informações, consulte [localização do recurso](import-dscresource.md#resource-location).

## <a name="see-also"></a>Consulte Também

- [Windows PowerShell Desired State Configuration descrição-geral](../overview/overview.md)
- [Recursos de DSC](../resources/resources.md)
- [Configurar o Gestor de configuração Local](../managing-nodes/metaConfig.md)
