---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Recursos de registo DSC
ms.openlocfilehash: 1e73e4275c0d9db5d8fac7641514ea8190f719ca
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-registry-resource"></a>Recursos de registo DSC

> Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

O **registo** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para gerir as chaves de registo e valores num nó de destino.

## <a name="syntax"></a>Sintaxe

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a>Propriedades
|  Propriedade  |  Descrição   | 
|---|---| 
| Tecla| Indica o caminho da chave do registo para o qual pretende garantir um estado específico. Este caminho tem de incluir o ramo de registo.| 
| ValueName| Indica o nome do valor de registo. Para adicionar ou remover uma chave de registo, especificar esta propriedade como uma cadeia vazia sem a especificação ValueType ou ValueData. Para modificar ou remover o valor predefinido de uma chave de registo, ao especificar também um ValueType ou ValueData de especificar esta propriedade como uma cadeia vazia.| 
| Certifique-se| Indica se a chave e valor existem. Para garantir que fazem, defina esta propriedade para "Presente". Para garantir que estes não existirem, defina a propriedade "Ausente". O valor predefinido é "Presente".| 
| Force| Se a chave de registo especificado estiver presente, __Force__ substitui-lo com o novo valor. Se eliminar uma chave de registo com subchaves, este tem de ser __$true__| 
| Hexadecimal| Indica se os dados irão ser expressos numa formato hexadecimal. Se for especificado, os dados do valor DWORD/QWORD são apresentados no formato hexadecimal. Não é válido para outros tipos. O valor predefinido é __$false__.| 
| dependsOn| Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado. Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"`.| 
| ValueData| Os dados para o valor de registo.| 
| ValueType| Indica o tipo do valor. Os tipos suportados são: 
<ul><li>String (REG_SZ)</li>


<li>Binário (REG binário)</li>


<li>DWORD 32 bits (REG_DWORD)</li>


<li>QWORD 64-bit (REG_QWORD)</li>


<li>Multi-string (REG_MULTI_SZ)</li>


<li>Cadeia expansível (REG_EXPAND_SZ)</li></ul>

## <a name="example"></a>Exemplo
Neste exemplo garante que uma chave denominada "ExampleKey" está presente no **HKEY\_LOCAL\_máquina** ramo de registo.
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

>**Nota:** alterar uma definição de registo no **HKEY\_atual\_utilizador** hive requer que a configuração é executada com as credenciais de utilizador, em vez do sistema.
>Pode utilizar o **PsDscRunAsCredential** propriedade para especificar as credenciais de utilizador para a configuração. Por exemplo, consulte [DSC em execução com as credenciais do utilizador](runAsUser.md)



