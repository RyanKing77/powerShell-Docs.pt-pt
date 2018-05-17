---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: DSC de Linux nxFileLine recursos
ms.openlocfilehash: 6b927839c23478aa9916a5d23836b31fccc58484
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-for-linux-nxfileline-resource"></a>DSC de Linux nxFileLine recursos

O **nxFileLine** recursos no PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para gerir linhas dentro de um ficheiro de configuração num nó de Linux.

## <a name="syntax"></a>Sintaxe

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Propriedades

|  Propriedade |  Descrição |
|---|---|
| filePath| O caminho completo para o ficheiro para gerir linhas no nó de destino.|
| ContainsLine| Uma linha para garantir que existe no ficheiro. Esta linha será anexada ao ficheiro se não existir no ficheiro. **ContainsLine** é obrigatório, mas pode ser definido como uma cadeia vazia ("ContainsLine = ' ') se não for necessário.|
| DoesNotContainPattern| Um padrão de expressão regular para as linhas que não deve existir no ficheiro. Para as linhas de que existe no ficheiro que correspondem a esta expressão regular, a linha será removida do ficheiro.|
| dependsOn | Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado. Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e o respetivo tipo é **ResourceType**, a sintaxe para utilizar esta a propriedade é `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Exemplo

Este exemplo mostra como utilizar o **nxFileLine** recursos para configurar o `/etc/sudoers` ficheiro, garantindo que o utilizador: monuser está configurado para não requiretty.

```
Import-DSCResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```