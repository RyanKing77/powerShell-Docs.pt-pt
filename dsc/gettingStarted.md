---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Configuração do estado pretendido de introdução do PowerShell
ms.openlocfilehash: b5aff5008db5a5e45b77d8094b0e48ad98dc63fa
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="getting-started-with-powershell-desired-state-configuration"></a>Configuração do estado pretendido de introdução do PowerShell #

Este guia descreve como começar a criar documentos de configuração de estado pretendido do PowerShell e aplicá-las nos computadores. Pressupõe familiaridade básica com cmdlets do PowerShell, módulos e funções.


## <a name="create-a-configuration"></a>Criar uma configuração ##

[**Configurações** ](https://msdn.microsoft.com/powershell/dsc/configurations) são documentos que descrevem um ambiente. Consistem em ambientes "**nós**", que são frequentemente máquinas virtuais ou físicas.

Configurações podem ter uma variedade de formulários. É a forma mais fácil de criar uma nova configuração para criar um ficheiro de (script do PowerShell). ps1. Para tal, abra o editor de eleição. ISE do PowerShell é uma boa opção, uma vez que compreende o DSC nativamente. Guarde o seguinte como um PS1:

```powershell
configuration MyFirstConfiguration
{
    Import-DscResource -Name WindowsFeature

    Node localhost
    {
        WindowsFeature IIS
        {
            Name = "IIS"

        }

    }

}
```
## <a name="parts-of-a-configuration"></a>Partes de uma configuração ##
**Configuração** é uma palavra-chave que tenha sido adicionada ao PowerShell 4.0. -Representa um tipo especial de função de PowerShell utilizados pela configuração de estado pretendido. Neste exemplo, a função é denominada myFirstConfiguration.

A linha seguinte é uma instrução de importação, semelhante a importar um módulo. Irá ser abordada mais tarde.

"Nó" define o nome da máquina que esta configuração irá atuar. Embora esta configuração é editada localmente, configurações podem aceder a nós remotos e configurá-los.

Nós podem ser nomes de computador ou endereços IP. Pode ter vários nós de um documento de configuração única. Utilizar [dados de configuração](https://msdn.microsoft.com/powershell/dsc/configdata), também pode ter a mesma configuração que se aplicam a vários nós. Neste caso, o nó é "localhost" - significa que o computador local.

O item seguinte é um [ **recursos**](https://msdn.microsoft.com/powershell/dsc/resources). Os recursos são os blocos modulares de configurações. Cada recurso é um módulo que define a lógica de implementação de um único aspeto de uma máquina. Pode ver todos os recursos no seu computador, executando **Get-DscResource** no PowerShell. Recursos deve estar presentes no computador local e importado antes de poderem ser utilizados numa configuração com **importação DscResource** que é a segunda linha desta configuração.

**Enacting uma configuração**

Se o script acima é guardado e executado, não será produzida nenhuma saída. Esta é uma vez que uma configuração é apenas uma função e o script acima tem a função definida pelo mas ainda não foram executá-la. Depois da função estiver definida, tem de ser invocado:
```powershell
myFirstConfiguration
```

Quando executada, as funções de configuração valide a configuração é válido. Não deve ter não existem erros de sintaxe, recursos devem ter todos os parâmetros obrigatórios definidos e todos os recursos devem ser importados antes da execução.

Depois da configuração é executada, cria uma pasta com o nome de configuração que contém um **. Ficheiro MOF** para cada nó na configuração. O. Ficheiro MOF é um formato de gestão baseada em normas que é utilizado pelo PowerShell DSC para comunicar através da rede.

Para enact a configuração:
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration
```
Esta ação cria um trabalho do PowerShell que acede a nós na configuração e configura-as. Para ver o resultado da tarefa, utilize o-espera.
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration -Wait
```