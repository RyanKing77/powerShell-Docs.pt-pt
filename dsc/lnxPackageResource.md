---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: DSC de Linux nxPackage recursos
ms.openlocfilehash: 64bb89a95bd6cbaea4e74b8a9979de52428fef3f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218710"
---
# <a name="dsc-for-linux-nxpackage-resource"></a>DSC de Linux nxPackage recursos

O **nxPackage** recursos no PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para gerir pacotes num nó de Linux.

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
| Certifique-se| Determina se deve verificar se o pacote existir. Defina esta propriedade para "Presente" para garantir que o pacote existir. Defina-o para "Ausente", certifique-se de que o pacote não existe. O valor predefinido é "Presente".|
| PackageManager| Os valores suportados são "yum", "apt" e "zypper". Especifica o Gestor de pacotes a utilizar ao instalar pacotes. Se **FilePath** for especificado, o caminho fornecido será utilizado para instalar o pacote. Caso contrário, um Gestor de pacote será utilizado para instalar o pacote a partir de um repositório de pré-configurado. Se nenhum dos **PackageManager** nem **FilePath** são fornecidos, o Gestor de pacote predefinido para o sistema irá ser utilizado.|
| filePath| O caminho do ficheiro onde reside o pacote|
| PackageGroup| Se **$true**, a **nome** deve ser o nome de um grupo do pacote para utilização com um **PackageManager**. **PacakgeGroup** não é válido quando fornecer um **FilePath**.|
| Argumentos| Uma cadeia de argumentos que serão transmitidas ao pacote exatamente como fornecido.|
| ReturnCode| O código de retorno esperado. Se o código de retorno de real não coincide com que o valor esperado indicado aqui, que a configuração irá devolver um erro.|
| dependsOn | Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado. Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e o respetivo tipo é **ResourceType**, a sintaxe para utilizar esta a propriedade é `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Exemplo

O exemplo seguinte assegura que o pacote designado "httpd" é instalado num computador Linux, utilizando o Gestor de pacote "Yum".

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