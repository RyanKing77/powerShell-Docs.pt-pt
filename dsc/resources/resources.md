---
ms.date: 12/12/2018
keywords: DSC, powershell, configuração, a configuração
title: Recursos de DSC
ms.openlocfilehash: 02e1b9856942cf28e77d83dac89681a08cf6bb74
ms.sourcegitcommit: 9df29dfc637191b62ca591893c251c1e02d4eb4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54012454"
---
# <a name="dsc-resources"></a>Recursos de DSC

>Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

Desired State Configuration (DSC) recursos fornecem os blocos de construção para uma configuração de DSC. Um recurso expõe propriedades que podem ser configurada (esquema) e contém as funções de script do PowerShell que o Gestor de configuração Local (LCM) chama de "tornam isso".

Um recurso pode modelar algo como genérica como um ficheiro ou o mais específico como uma definição de servidor IIS.  Grupos de como os recursos são combinados em para um módulo de DSC, o que organiza a todos os ficheiros necessários para uma estrutura que é portátil e inclui metadados para identificar a forma como os recursos destinam-se a ser utilizado.

Cada recurso tem um * esquema que determina a sintaxe necessária para utilizar o recurso num [configuração](../configurations/configurations.md). Esquema de um recurso pode ser definida da seguinte maneira:

- **'Schema.Mof'** ficheiro: Definir a maioria dos recursos seus *esquema* num schema.mof de ficheiros, usando [formato de objeto gerenciado](/windows/desktop/wmisdk/managed-object-format--mof-).
- **'\<Nome do recurso\>. schema.psm1'** ficheiro: [Recursos compostos](../configurations/compositeConfigs.md) definir seus *esquema* num '<ResourceName>. schema.psm1' de ficheiros com um [bloco de parâmetro](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).
- **'\<Nome do recurso\>psm1 '** ficheiro: Classe de recursos de DSC com base definem seus *esquema* na definição de classe. Itens de sintaxe estão marcadas como propriedades de classe. Para obter mais informações, consulte [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).

Para obter a sintaxe de um recurso de DSC, utilize o [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet com o `-Syntax` parâmetro. Esse uso é semelhante à utilização [Get-Command](/powershell/module/microsoft.powershell.core/get-command) com o `-Syntax` parâmetro para obter a sintaxe de cmdlet. A saída que vir mostrará o modelo utilizado para um bloco de recursos para o recurso que especificar.

```powershell
Get-DscResource -Syntax Service
```

A saída que vir deve ser semelhante à saída abaixo, embora a sintaxe deste recurso foi alterado no futuro. Como a sintaxe de cmdlet, o *chaves* visto em parênteses Retos, são opcionais. Os tipos de especificar o tipo de dados que cada chave de espera.

> [!NOTE]
> O **Certifique-se** chave é opcional, pois é assumida como predefinição "Presente".

```output
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

Dentro de uma configuração, um **serviço** bloco de recurso pode ser assim para **Certifique-se** que está a executar o serviço de Spooler.

> [!NOTE]
> Antes de utilizar um recurso numa configuração, tem de importá-lo a utilizar [Import-DSCResource](../configurations/import-dscresource.md).

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }
    }
}
```

Configurações podem conter várias instâncias do mesmo tipo de recurso. Cada instância tem de ser chamada de exclusivamente. No exemplo a seguir, um segundo **serviço** bloco de recurso é adicionado para configurar o serviço de "DHCP".

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }

        # To configure a second service resource block, add another Service resource block and use a unique name.
        Service "DHCP:Running"
        {
            Name = "DHCP"
            State = "Running"
        }
    }
}
```

> [!NOTE]
> A partir do PowerShell 5.0, intellisense, foi adicionado para DSC. Esta nova funcionalidade permite-lhe utilizar \<SEPARADOR\> e \<Ctrl + espaço\> para nomes de chaves de preenchimento automático.

![Conclusão de tabulação de recursos](../media/resource-tabcompletion.png)
