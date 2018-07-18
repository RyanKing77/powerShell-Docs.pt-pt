---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recurso de pacote de DSC
ms.openlocfilehash: 3046ba7d57776a996a0b917348a0e863db6cd0c8
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093808"
---
# <a name="dsc-package-resource"></a>Recurso de pacote de DSC

> Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

O **pacote** recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para instalar ou desinstalar pacotes, como pacotes de instalador do Windows e setup.exe, num nó de destino.

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
| productId| Indica o ID de produto que identifica exclusivamente o pacote.|
| Argumentos| Lista de argumentos que será passada para o pacote exatamente como fornecida uma cadeia de caracteres.|
| Credencial| Fornece acesso ao pacote de sobre uma origem remota. Esta propriedade não é utilizada para instalar o pacote. O pacote é sempre instalado no sistema local.|
| Certifique-se| Indica se o pacote está instalado. Defina esta propriedade como "Ausente", certifique-se de que o pacote não está instalado (ou desinstalar o pacote se estiver instalado). Defina-o para "Apresentar" (o valor predefinido) para garantir que o pacote está instalado.|
| LogPath| Indica o caminho completo onde pretende que o fornecedor para guardar um ficheiro de registo para instalar ou desinstalar o pacote.|
| DependsOn | Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será **ResourceName** e seu tipo é **ResourceType**, a sintaxe para utilizar esta propriedade é "DependsOn ="[ ResourceName ResourceType]"'.|
| ReturnCode| Indica o código de retorno esperado. Se o código de retorno real não corresponde ao que valor esperado fornecido aqui, que a configuração irá devolver um erro.|

## <a name="example"></a>Exemplo

Este exemplo é executado o instalador. msi, que está localizado no caminho especificado e tem o ID de produto especificada.

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