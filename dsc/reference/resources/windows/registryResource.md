---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recurso de registro de DSC
ms.openlocfilehash: e0ae1a4a27edc08c4e6ccd47786426917eb1ccb4
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048491"
---
# <a name="dsc-registry-resource"></a>Recurso de registro de DSC

_Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0_

O **Registro** recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para gerir as chaves de registro e os valores num nó de destino.

## <a name="syntax"></a>Sintaxe

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Present | Absent }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a>Propriedades

| Propriedade | Descrição |
| --- | --- |
| Tecla| Indica o caminho da chave do registo para o qual pretende garantir um estado específico. Este caminho tem de incluir o hive.|
| valueName| Indica o nome do valor do Registro. Para adicionar ou remover uma chave de registo, especifique esta propriedade como uma cadeia vazia sem especificar ValueType ou ValueData. Para modificar ou remover o valor predefinido de uma chave de registo, especifique esta propriedade como uma cadeia vazia ao especificar também o ValueType ou ValueData.|
| Certifique-se| Indica se a chave e valor existirem. Para garantir que eles fazem, defina esta propriedade para "Presente". Para garantir que não existam, defina a propriedade como "Ausente". O valor predefinido é "Presente".|
| Force| Se a chave de registo especificado estiver presente, **força** é substituído pelo novo valor. Se eliminar uma chave de registo com subchaves, esse processo precisa ser **$true** |
| Hexadecimal| Indica se os dados irão ser expressos em formato hexadecimal. Se for especificado, os dados do valor DWORD/QWORD são apresentados em formato hexadecimal. Não é válido para outros tipos. O valor predefinido é **$false**.|
| DependsOn| Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será **ResourceName** e seu tipo é **ResourceType**, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.|
| ValueData| Os dados para o valor de registo.|
| ValueType| Indica o tipo do valor. Os tipos suportados são: Cadeia (REG_SZ), o binário (REG binário), Dword de 32 bits (REG_DWORD), Qword 64-bit (REG_QWORD), cadeia de caracteres múltipla (REG_MULTI_SZ), (REG_EXPAND_SZ) de cadeia expansível |

## <a name="example"></a>Exemplo

Neste exemplo, garante que uma chave denominada "ExampleKey" está presente no **HKEY\_locais\_máquina** hive.

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

> [!NOTE]
> Alterar uma definição de registo no `HKEY\CURRENT\USER` hive requer que a configuração seja executado com credenciais do usuário, em vez de como o sistema. Pode utilizar o **PsDscRunAsCredential** propriedade para especificar as credenciais de utilizador para a configuração. Por exemplo, veja [a executar o DSC com as credenciais de utilizador](../../../configurations/runAsUser.md).
