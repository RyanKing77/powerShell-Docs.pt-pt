---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Recurso de pacote DSC
ms.openlocfilehash: 16f7f1b8fa7b84bcfdeb09fdc46db9c93113e70c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188535"
---
# <a name="dsc-package-resource"></a>Recurso de pacote DSC

> Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

O **pacote** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para instalar ou desinstalar pacotes, tais como pacotes do Windows Installer e setup.exe, num nó de destino.

## <a name="syntax"></a>Sintaxe

```
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ ReturnCode = [UInt32[]] ]
}
```

## <a name="properties"></a>Propriedades
|  Propriedade  |  Descrição   |
|---|---|
| Nome| Indica o nome do pacote para o qual pretende garantir um estado específico.|
| Caminho| Indica o caminho onde reside o pacote.|
| ProductId| Indica o ID de produto que identifica exclusivamente o pacote.|
| Argumentos| Apresenta uma lista de uma cadeia de argumentos que serão transmitidas ao pacote exatamente como fornecido.|
| credencial| Fornece acesso ao pacote de uma origem remota. Esta propriedade não é utilizada para instalar o pacote. O pacote é sempre instalado no sistema local.|
| Certifique-se| Indica se o pacote está instalado. Defina esta propriedade para "Ausente", certifique-se de que o pacote não está instalado (ou desinstalar o pacote, caso esteja instalada). Defina-o para "Apresentar" (o valor predefinido) para garantir que o pacote está instalado.|
| LogPath| Indica o caminho completo onde pretende que o fornecedor para guardar um ficheiro de registo para instalar ou desinstalar o pacote.|
| dependsOn | Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado. Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é **ResourceName** e o respetivo tipo é **ResourceType**, a sintaxe para utilizar esta propriedade é ' DependsOn = "[ ResourceName ResourceType]"'.|
| ReturnCode| Indica o código de retorno esperado. Se o código de retorno de real não coincide com que o valor esperado indicado aqui, que a configuração irá devolver um erro.|

## <a name="example"></a>Exemplo

Neste exemplo executa o instalador. msi, que está localizado no caminho especificado e tem o ID de produto especificada.

```powershell
Configuration PackageTest
{
    Package PackageExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Path        = "$Env:SystemDrive\TestFolder\TestProject.msi"
        Name        = "TestPackage"
        ProductId   = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
    }
}
```