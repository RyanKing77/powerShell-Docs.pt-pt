---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Recurso ProcessSet de DSC
ms.openlocfilehash: d18d2c96239abd83cea735e0fbce198d0456cea6
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093995"
---
# <a name="dsc-windowsprocess-resource"></a>Recurso WindowsProcess de DSC

> Aplica-se a: O Windows PowerShell 5.0

O **ProcessSet** recursos no Windows PowerShell Desired State Configuration (DSC) fornece um mecanismo para configurar os processos num nó de destino. Este recurso é um [recursos compostos](authoringResourceComposite.md) que chama o [recurso WindowsProcess](windowsProcessResource.md) para cada grupo especificado no `GroupName` parâmetro.

## <a name="syntax"></a>Sintaxe

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Propriedades

|  Propriedade  |  Descrição   |
|---|---|
| Argumentos| Uma cadeia que contém os argumentos transmitidos para o processo como-é. Se precisar de passar argumentos vários, colocá-los nessa cadeia de caracteres.|
| Caminho| Os caminhos para os executáveis de processo. Se estes forem os nomes dos ficheiros executáveis (caminhos totalmente qualificados), o recurso de DSC irá procurar o ambiente **caminho** variável (`$env:Path`) para localizar os ficheiros. Se os valores dessa propriedade são caminhos totalmente qualificados, DSC não irá utilizar o **caminho** variável de ambiente para encontrar os arquivos e irá gerar um erro se qualquer um dos caminhos não existirem. Não são permitidos caminhos relativos.|
| Credencial| Indica as credenciais para iniciar o processo.|
| Certifique-se| Especifica se os processos existe. Defina esta propriedade para "Presente" para garantir que existe o processo. Caso contrário, defina-o como "Ausente". A predefinição é "Presente".|
| StandardErrorPath| O caminho para o qual os processos de escrever o erro padrão. Qualquer arquivo existente será substituído.|
| StandardInputPath| O fluxo a partir do qual o processo recebe a entrada padrão.|
| StandardOutputPath| O caminho do ficheiro para que os processos de escrever a saída padrão. Qualquer arquivo existente será substituído.|
| WorkingDirectory| A localização utilizada como diretório de trabalho atual para os processos.|
| DependsOn | Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Por exemplo, se o ID da configuração do recurso do bloco que pretende executar script primeiro será **ResourceName** e seu tipo é **_ResourceType**, a sintaxe para utilizar esta propriedade é "DependsOn ="[ ResourceName ResourceType]"'.|