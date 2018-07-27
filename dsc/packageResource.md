---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recurso de pacote de DSC
ms.openlocfilehash: 9285df71a303c9a53dd50d450272575a64e962e7
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268675"
---
# <a name="dsc-package-resource"></a>Recurso de pacote de DSC

_Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0_

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

| Propriedade | Descrição |
| --- | --- |
| Nome| Indica o nome do pacote para o qual pretende garantir um estado específico.|
| Caminho| Indica o caminho onde reside o pacote.|
| productId| Indica o ID de produto que identifica exclusivamente o pacote.|
| Argumentos| Lista de argumentos que será passada para o pacote exatamente como fornecida uma cadeia de caracteres.|
| Credencial| Fornece acesso ao pacote de sobre uma origem remota. Esta propriedade não é utilizada para instalar o pacote. O pacote é sempre instalado no sistema local.|
| Certifique-se| Indica se o pacote está instalado. Defina esta propriedade como "Ausente", certifique-se de que o pacote não está instalado (ou desinstalar o pacote se estiver instalado). Defina-o para "Apresentar" (o valor predefinido) para garantir que o pacote está instalado.|
| LogPath| Indica o caminho completo onde pretende que o fornecedor para guardar um ficheiro de registo para instalar ou desinstalar o pacote.|
| DependsOn | Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será **ResourceName** e seu tipo é **ResourceType**, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.|
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