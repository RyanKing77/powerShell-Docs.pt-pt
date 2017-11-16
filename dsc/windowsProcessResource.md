---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Recursos do DSC WindowsProcess
ms.openlocfilehash: c34d3cb1d4d9b899b45fba7b4b148a7c977f5365
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-windowsprocess-resource"></a>Recursos do DSC WindowsProcess

> Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

O **WindowsProcess** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para configurar processos num nó de destino.

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
|  Propriedade  |  Descrição   | 
|---|---| 
| Argumentos| Indica uma cadeia de argumentos transmitidos para o processo que-é. Se tiver de passar vários argumentos, colocá-los a todos nesta cadeia.| 
| Caminho| O caminho para o executável do processo. Se o nome de ficheiro do executável (não o caminho completamente qualificado), os recursos de DSC irá procurar o ambiente **caminho** variável (`$env:Path`) para localizar o ficheiro executável. Se o valor desta propriedade é um caminho completamente qualificado, DSC não utilizará o **caminho** variável de ambiente para localizar o ficheiro e irá gerar um erro se o caminho não existe. Não são permitidos caminhos relativos.| 
| credencial| Indica as credenciais para iniciar o processo.| 
| Certifique-se| Indica se o processo exista. Defina esta propriedade para "Presente" para se certificar de que o processo exista. Caso contrário, defina-o para "Ausente". A predefinição é "Presente".| 
| dependsOn | Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado. Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é __ResourceName__ e o respetivo tipo é __ResourceType__, a sintaxe para utilizar esta propriedade é ' DependsOn = "[ ResourceName ResourceType]"'.| 
| StandardErrorPath| Indica o caminho do diretório para escrever o erro padrão. Não existe qualquer ficheiro existente será substituído.| 
| StandardInputPath| Indica a localização de entrada padrão.| 
| StandardOutputPath| Indica a localização para guardar a saída padrão. Não existe qualquer ficheiro existente será substituído.| 
| WorkingDirectory| Indica a localização que será utilizada como o atual diretório de trabalho para o processo.| 
