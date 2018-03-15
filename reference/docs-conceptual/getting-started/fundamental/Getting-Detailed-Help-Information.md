---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: "Obter Informações de Ajuda Detalhadas"
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: 67e02b503acf4d683c5a190d6642dea384bbfad2
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/15/2018
---
# <a name="getting-detailed-help-information"></a>Obter Informações de Ajuda Detalhadas
O Windows PowerShell inclui tópicos de ajuda detalhada que explicam conceitos do Windows PowerShell e o idioma do Windows PowerShell. Também existem tópicos de ajuda para cada fornecedor e o cmdlet e tópicos de ajuda para muitas funções e scripts.

Pode apresentar estes tópicos de ajuda na linha de comandos ou visualizar as versões mais recentemente atualizadas destes tópicos em do Microsoft TechNet Library. Muitos programas que alojam o Windows PowerShell, como o Windows PowerShell Integrated Scripting ambiente, fornecem funcionalidades adicionais de ajuda, tais como ajuda sensível ao contexto e compilar o ficheiro de ajuda (*.chm).

## <a name="getting-help-for-cmdlets"></a>Obter ajuda para Cmdlets
Para obter ajuda sobre cmdlets do Windows PowerShell, utilize o [Get-Help [m2]](https://technet.microsoft.com/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2) cmdlet. Por exemplo, para obter ajuda para o [Get-ChildItem [m2]](https://technet.microsoft.com/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc) cmdlet, tipo:

```
get-help get-childitem
```

ou

```
get-childitem -?
```

Ainda pode obter ajuda sobre o cmdlet Get-Help. Por exemplo:

```
get-help get-help
```

Para obter uma lista de todos os tópicos de ajuda do cmdlet na sua sessão, escreva:

```
get-help -category cmdlet
```

Para apresentar uma página de cada tópico de ajuda num momento, utilize o **ajudar** função ou o seu alias **man**. Por exemplo, para apresentar a ajuda do cmdlet Get-ChildItem, escreva

```
man get-childitem
```

ou

```
help get-childitem
```

Para ver informações detalhadas sobre um cmdlet, a função ou script, incluindo as descrições dos respetivos parâmetros e exemplos da sua utilização, utilize o *detalhados* parâmetros do cmdlet Get-Help. Por exemplo, para obter informações detalhadas sobre o cmdlet Get-ChildItem, escreva:

```
get-help get-childitem -detailed
```

Para apresentar todo o conteúdo no tópico de ajuda, utilize o *completa* parâmetros do cmdlet Get-Help. Por exemplo, para apresentar todo o conteúdo no tópico de ajuda do cmdlet Get-ChildItem, escreva:

```
get-help get-childitem -full
```

Para obter ajuda de detalhado sobre os parâmetros de um cmdlet, utilize o *parâmetro* parâmetros do cmdlet Get-Help. Por exemplo obter ajuda para todos os parâmetros do cmdlet Get-ChildItem, tipo de detalhado:

```
get-help get-childitem -parameter *
```

Para apresentar apenas os exemplos de um tópico de ajuda, utilize o *exemplo* parâmetro de Get-Help. Por exemplo, para apresentar apenas os exemplos de tópico de ajuda para o cmdlet Get-ChildItem, escreva:

```
get-help get-childitem -examples
```

Para obter informações sobre como escrever tópicos de ajuda para os cmdlets que escreve, consulte [como escrever ajuda do Cmdlet](https://go.microsoft.com/fwlink/?LinkID=123415) na biblioteca da MSDN.

## <a name="getting-conceptual-help"></a>Obter Ajuda Conceptual
O cmdlet Get-Help também apresenta informações sobre tópicos conceptuais no Windows PowerShell, incluindo tópicos sobre o idioma do Windows PowerShell. Tópicos de ajuda conceptuais começar com o prefixo "about_", tais como about_line_editing. (O tópico conceptual deve ser introduzido o nome em inglês, mesmo em versões não inglesas do Windows PowerShell.)

Para apresentar uma lista de tópicos conceptuais, escreva:

```
get-help about_*
```

Para apresentar um determinado tópico de ajuda, escreva o nome de tópico, por exemplo:

```
get-help about_command_syntax
```

Os parâmetros de Get-Help, tais como *detalhados*, *parâmetro*, e *exemplos*, não tem qualquer efeito no ecrã de conceptual tópicos de ajuda.

## <a name="getting-help-about-providers"></a>Obter ajuda sobre fornecedores
O cmdlet Get-Help apresenta informações sobre fornecedores do Windows PowerShell. Para obter ajuda para um fornecedor, escreva "Get-Help" seguido do nome do fornecedor. Por exemplo, para obter ajuda para o fornecedor de registo, escreva:

```
get-help registry
```

Para obter uma lista de todos os tópicos de ajuda de fornecedor na sua sessão, escreva

```
get-help -category provider
```

Os parâmetros de Get-Help, tais como *detalhados*, *parâmetro*, e *exemplos*, não tem qualquer efeito no ecrã dos tópicos de ajuda do fornecedor.

## <a name="getting-help-about-scripts-and-functions"></a>Obter ajuda sobre Scripts e funções
Tópicos de ajuda de ter muitos scripts e funções no Windows PowerShell. Utilize o cmdlet Get-Help para apresentar os tópicos de ajuda para scripts e funções.

Para apresentar a ajuda para uma função, escreva "get-help" seguido do nome de função. Por exemplo, para obter ajuda para a função de Disable-PSRemoting, escreva:

```
get-help disable-psremoting
```

Para apresentar a ajuda para um script, escreva o caminho completamente qualificado para o ficheiro de script. Se o script estiver num caminho listado na variável de ambiente Path, pode omitir o caminho do comando.

Por exemplo, se tiver um script designado "TestScript.ps1" no seu c\\diretório de teste de PS, para visualizar o tópico de ajuda para o script, tipo:

```
get-help c:\ps-test\TestScript.ps1
```

Os parâmetros que foram concebidos para apresentar cmdlet ajudam, tais como *detalhados*, *completa*, *exemplos*, e *parâmetro*, funcionam para as funções e scripts ajuda ajudam, demasiado. No entanto, quando apresentar todos os ajuda, escrevendo "get-help \*", a ajuda para as funções e scripts não é apresentada.

Para obter informações sobre como escrever tópicos de ajuda para as suas funções e scripts, consulte [about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af), e [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf).

## <a name="getting-help-online"></a>Obter Ajuda Online
Se estiver ligado à Internet, uma das formas melhor para obter ajuda é ver tópicos de ajuda online. Porque tópicos online são fáceis de atualização, é provável que forneça o conteúdo mais recente.

Para obter ajuda online, experimente o *Online* parâmetros do cmdlet Get-Help. O *Online* parâmetro funciona de cmdlet Get-Help apenas para o cmdlet ajuda, funcionar ajuda e ajuda o script. Não é possível utilizar o *Online* parâmetro com conceptual (sobre) ou tópicos de ajuda do fornecedor. Além disso, porque esta funcionalidade é opcional, não funciona para cada cmdlet, a função ou o tópico de ajuda de script.

No entanto, todos os tópicos de ajuda que vêm com o Windows PowerShell, incluindo o fornecedor de ajuda e conceptual (tópicos de ajuda sobre) estão disponíveis online no [do Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) secção do Microsoft TechNet Library.

Para utilizar o *Online* parâmetros do cmdlet Get-Help, utilize o seguinte formato de comando.

```
get-help <command-name> -online
```

Por exemplo, para obter a versão online do tópico de ajuda sobre o cmdlet Get-ChildItem, escreva:

```
get-help get-childitem -online
```

Se estiver disponível uma versão online do tópico de ajuda, será aberto no seu browser predefinido.

Se a ajuda online é suportada para um tópico de ajuda, também pode ver o endereço de Internet (URL) do tópico de ajuda. O endereço Internet é apresentada na secção ligações relacionadas um tópico de ajuda.

Por exemplo, para ver o URL para a versão online do cmdlet Add-Computer, escreva:

```
get-help add-computer
```

A primeira linha na secção do tópico ligações relacionadas é mostrada abaixo.

```
Online version: http://go.microsoft.com/fwlink/?LinkID=135194
```

Para obter informações sobre como fornecer suporte online para os tópicos de ajuda, consulte [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)e ver [como escrever ajuda do Cmdlet](https://go.microsoft.com/fwlink/?LinkID=123415) na biblioteca da MSDN.

## <a name="see-also"></a>Consulte Também
- [about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105)
- [about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af)
- [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)
- [Get-Help [m2]](https://technet.microsoft.com/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2)

