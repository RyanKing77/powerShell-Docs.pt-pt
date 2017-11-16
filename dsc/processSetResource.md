---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: Recursos do DSC ProcessSet
ms.openlocfilehash: b713d1a9c34eab6966de4f342991ead32c19df5d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-windowsprocess-resource"></a>Recursos do DSC WindowsProcess

> Aplica-se a: O Windows PowerShell 5.0

O **ProcessSet** recursos no Windows PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para configurar processos num nó de destino. Este recurso é um [recursos composto](authoringResourceComposite.md) que chama o [WindowsProcess recursos](windowsProcessResource.md) para cada grupo especificado no `GroupName` parâmetro.

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
| Argumentos| Uma cadeia que contém os argumentos transmitidos para o processo que-é. Se tiver de passar vários argumentos, colocá-los a todos nesta cadeia.| 
| Caminho| Os caminhos para o processo de executáveis. Se estes são os nomes dos ficheiros executáveis (caminhos completamente qualificados), os recursos de DSC pesquisará o ambiente **caminho** variável (`$env:Path`) para localizar os ficheiros. Se os valores desta propriedade caminhos completamente qualificados, DSC não utilizará o **caminho** variável de ambiente para encontrar os ficheiros e irá gerar um erro se qualquer um dos caminhos de não existir. Não são permitidos caminhos relativos.| 
| credencial| Indica as credenciais para iniciar o processo.| 
| Certifique-se| Especifica se os processos existe. Defina esta propriedade para "Presente" para se certificar de que o processo exista. Caso contrário, defina-o para "Ausente". A predefinição é "Presente".| 
| StandardErrorPath| O caminho para os quais os processos de escrita de erro padrão. Não existe qualquer ficheiro existente será substituído.| 
| StandardInputPath| O fluxo a partir do qual o processo recebe entrada padrão.| 
| StandardOutputPath| O caminho do ficheiro para que os processos de escrever a saída padrão. Não existe qualquer ficheiro existente será substituído.| 
| WorkingDirectory| A localização utilizada como o atual diretório de trabalho para processos.| 
| dependsOn | Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado. Por exemplo, se o ID da configuração do recurso de script bloco de que pretende executar primeiro é **ResourceName** e o respetivo tipo é **_ResourceType**, a sintaxe para utilizar esta propriedade é ' DependsOn = "[ ResourceName ResourceType]"'.| 

