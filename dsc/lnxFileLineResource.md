---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: DSC para Linux nxFileLine recursos
ms.openlocfilehash: f2a989dd3a6746948e09ba94e279c02be8ebe2de
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893302"
---
# <a name="dsc-for-linux-nxfileline-resource"></a>DSC para Linux nxFileLine recursos

O **nxFileLine** recursos no PowerShell Desired State Configuration (DSC) fornece um mecanismo para a gerir linhas dentro de um ficheiro de configuração num nó de Linux.

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
| Caminho do ficheiro| O caminho completo para o ficheiro para gerir as linhas no nó de destino.|
| ContainsLine| Uma linha para garantir que existe no ficheiro. Essa linha será anexada ao ficheiro se não existir no ficheiro. **ContainsLine** é obrigatório, mas pode ser definido como uma cadeia vazia (`ContainsLine = ""`) se não for necessário.|
| DoesNotContainPattern| Um padrão de expressão regular para linhas que não deve existir no ficheiro. Para as linhas existentes no arquivo que correspondem essa expressão regular, a linha será removida do ficheiro.|
| DependsOn | Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e seu tipo é **ResourceType**, a sintaxe para usar isso a propriedade é `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Exemplo

Este exemplo demonstra como utilizar o **nxFileLine** recurso para configurar o `/etc/sudoers` arquivo, assegurando que o utilizador: monuser está configurado para não requiretty.

```powershell
Import-DscResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```