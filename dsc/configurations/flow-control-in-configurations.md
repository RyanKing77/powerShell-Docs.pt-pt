---
ms.date: 12/12/2018
keywords: DSC, powershell, configuração, a configuração
title: Instruções condicionais e loops em configurações
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404770"
---
# <a name="conditional-statements-and-loops-in-configurations"></a>Instruções condicionais e loops em configurações

Pode fazer sua [configurações](configurations.md) mais dinâmicos com palavras-chave de controle de fluxo de PowerShell. Este artigo irá mostrar como pode usar instruções condicionais e loops para tornar suas configurações mais dinâmicos. Combinar condicional e loops com [parâmetros](add-parameters-to-a-configuration.md) e [dados de configuração](configData.md) permite-lhe mais flexibilidade e controle ao compilar suas configurações.

Tal como uma função ou um bloco de scripts, pode usar qualquer linguagem de PowerShell dentro de uma configuração. As instruções que utilizar apenas serão avaliadas quando chama a sua configuração para compilar um arquivo de ". MOF". Os exemplos abaixo mostram cenários simples para demonstrar conceitos. Condicionais são loops com mais frequência são utilizados com parâmetros e dados de configuração.

Neste exemplo simples, o **serviço** bloco de recurso obtém o estado atual de um serviço em tempo de compilação para gerar um arquivo de ". MOF" que mantém o estado atual.

> [!NOTE]
> Utilizar blocos de recursos dinâmicos antecipará a eficácia do Intellisense. O analisador do PowerShell não é possível determinar se os valores especificados são aceitáveis até que a configuração é compilada.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Service Spooler
        {
            Name = "Spooler"
            State = $(Get-Service -Name 'spooler').Status
            StartType = $(Get-Service -Name 'spooler').StartType
        }
    }
}
```

Além disso, poderia criar uma **serviço** bloquear recursos para cada serviço no computador atual, usando um `foreach` loop.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Foreach ($service in $(Get-Service))
        {
            Service $service.Name
            {
                Name = $service.Name
                State = $service.Status
                StartType = $service.StartType
            }
        }
    }
}
```

Também só pode criar as configurações para as máquinas que estiverem online, através de um simples `if` instrução.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    Foreach ($computer in @('Server01', 'Server02', 'Server03'))
    {
        if (Test-Connection -ComputerName $computer)
        {
            Node $computer
            {
                Service "Spooler"
                {
                    Name = "Spooler"
                    State = "Started"
                }
            }
        }
    }
}
```

> [!NOTE]
> O recurso dinâmico bloqueia, a referência de exemplos acima, a máquina atual. Neste caso, o que seria a máquina estiver a criar a configuração no, não o nó de destino.

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a>Resumo

Em resumo, pode usar qualquer linguagem de PowerShell dentro de uma configuração.

Isto inclui coisas como:

- Objetos personalizados
- Tabelas hash
- Manipulação de cadeias
- Comunicação remota
- WMI e CIM
- Objetos do Active Directory
- e muito mais...

Qualquer código de PowerShell definido numa configuração será avaliado um tempo de compilação, mas também é possível colocar código no script que contém a sua configuração. Nenhum código além do bloco de configuração será executado quando importar a configuração.

## <a name="see-also"></a>Consulte também

- [Adicionar parâmetros a uma configuração](add-parameters-to-a-configuration.md)
- [Separar dados de configuração de configurações](configData.md)
