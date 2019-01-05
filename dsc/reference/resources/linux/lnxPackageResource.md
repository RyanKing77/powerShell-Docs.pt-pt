---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: DSC para Linux nxPackage recursos
ms.openlocfilehash: 64bb89a95bd6cbaea4e74b8a9979de52428fef3f
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048407"
---
# <a name="dsc-for-linux-nxpackage-resource"></a>DSC para Linux nxPackage recursos

O **nxPackage** recursos no PowerShell Desired State Configuration (DSC) fornece um mecanismo para gerir pacotes num nó de Linux.

## <a name="syntax"></a>Sintaxe

```
nxPackage <string> #ResourceName
{
    Name = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ LogPath = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Propriedades

|  Propriedade |  Descrição |
|---|---|
| Nome| O nome do pacote para o qual pretende garantir um estado específico.|
| Certifique-se| Determina se deve verificar se o pacote existe. Defina esta propriedade para "Presente" para garantir que o pacote existe. Defini-lo como "Ausente", certifique-se de que o pacote não existe. O valor predefinido é "Presente".|
| PackageManager| Os valores suportados são "yum", "apt" e "zypper". Especifica o Gestor de pacotes a utilizar ao instalar pacotes. Se **FilePath** for especificado, o caminho fornecido vai ser utilizado para instalar o pacote. Caso contrário, um Gestor de pacotes será utilizado para instalar o pacote a partir de um repositório previamente configurado. Se nenhum desses **PackageManager** nem **FilePath** são fornecidas, o Gestor de pacotes padrão para o sistema será usado.|
| Caminho do ficheiro| O caminho do ficheiro onde reside o pacote|
| PackageGroup| Se **$true**, o **nome** deve ser o nome de um grupo de pacote para utilização com um **PackageManager**. **PacakgeGroup** não é válido quando fornecer um **FilePath**.|
| Argumentos| Uma cadeia de argumentos que será passada para o pacote exatamente como fornecida.|
| ReturnCode| O código de retorno esperado. Se o código de retorno real não corresponde ao que valor esperado fornecido aqui, que a configuração irá devolver um erro.|
| DependsOn | Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e seu tipo é **ResourceType**, a sintaxe para usar isso a propriedade é `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Exemplo

O exemplo seguinte garante que o pacote com o nome "httpd" está instalado num computador Linux, utilizando o Gestor de pacotes "Yum".

```
Import-DSCResource -Module nx

Node $node {
nxPackage httpd
{
    Name = "httpd"
    Ensure = "Present"
    PackageManager = "Yum"
}
}
```