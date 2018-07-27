---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recurso WindowsProcess de DSC
ms.openlocfilehash: cee93ab283ded407d6e032161125aa6d6ac98827
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/26/2018
ms.locfileid: "39267962"
---
# <a name="dsc-windowsprocess-resource"></a>Recurso WindowsProcess de DSC

_Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0_

O **WindowsProcess** recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para configurar os processos num nó de destino.

## <a name="syntax"></a>Sintaxe

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ DependsOn = [string[]] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
}
```

## <a name="properties"></a>Propriedades

| Propriedade | Descrição |
| --- | --- |
| Argumentos| Indica uma cadeia de argumentos transmitidos para o processo como-é. Se precisar de passar argumentos vários, colocá-los nessa cadeia de caracteres.|
| Caminho| O caminho para o executável do processo. Se esta o nome de ficheiro do ficheiro executável (não o caminho totalmente qualificado), o recurso de DSC irá procurar o ambiente **caminho** variável (`$env:Path`) para localizar o ficheiro executável. Se o valor desta propriedade é um caminho totalmente qualificado, DSC não irá utilizar o **caminho** variável de ambiente para encontrar o ficheiro e irá gerar um erro se o caminho não existir. Não são permitidos caminhos relativos.|
| Credencial| Indica as credenciais para iniciar o processo.|
| Certifique-se| Indica se o processo exista. Defina esta propriedade para "Presente" para garantir que existe o processo. Caso contrário, defina-o como "Ausente". A predefinição é "Presente".|
| DependsOn | Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será **ResourceName** e seu tipo é **ResourceType**, a sintaxe para utilizar esta propriedade é `DependsOn = "[ResourceType]ResourceName"` .|
| StandardErrorPath| Indica o caminho do diretório para escrever o erro padrão. Qualquer arquivo existente será substituído.|
| StandardInputPath| Indica a localização de entrada padrão.|
| StandardOutputPath| Indica a localização para guardar a saída padrão. Qualquer arquivo existente será substituído.|
| WorkingDirectory| Indica a localização que será utilizada como diretório de trabalho atual para o processo.|