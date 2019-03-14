---
ms.date: 08/27/2018
keywords: PowerShell, o cmdlet
title: Obter Informações de Ajuda Detalhadas
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: e58814f512aa2c5914f92f942cf2a4a76956ee20
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794574"
---
# <a name="getting-detailed-help-information"></a>Obter informações de ajuda detalhadas

PowerShell inclui artigos de ajuda detalhados que explicam conceitos do PowerShell e a linguagem do PowerShell. Também existem artigos de ajuda para cada cmdlet e o fornecedor e para muitas funções e scripts.

Pode exibir esses artigos de ajuda no prompt de comando ou vista atualizada mais recentemente versões dos seguintes artigos no [PowerShell](/powershell/scripting/overview) documentação online.

## <a name="getting-help-for-cmdlets"></a>Obter ajuda para cmdlets

Para obter ajuda sobre cmdlets do PowerShell, utilize o [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) cmdlet. Por exemplo, para obter ajuda para o `Get-ChildItem` cmdlet, tipo:

```powershell
Get-Help Get-ChildItem
```

ou

```powershell
Get-ChildItem -?
```

Pode até mesmo obter ajuda sobre o cmdlet Get-Help. Por exemplo:

```powershell
Get-Help Get-Help
```

Para obter uma lista de todos os o cmdlet artigos de ajuda na sua sessão, escreva:

```powershell
Get-Help -Category Cmdlet
```

Para apresentar uma página de cada artigo de ajuda ao mesmo tempo, utilize o `help` função ou o respetivo alias `man`.
Por exemplo, para apresentar a ajuda para o `Get-ChildItem` cmdlet, tipo

```powershell
man Get-ChildItem
```

ou

```powershell
help Get-ChildItem
```

Para visualizar informações detalhadas, utilizar o **Detailed** parâmetro do `Get-Help` cmdlet. Por exemplo, para obter informações detalhadas o `Get-ChildItem` cmdlet, tipo:

```powershell
Get-Help Get-ChildItem -Detailed
```

Para exibir todo o conteúdo do artigo de ajuda, utilize o **completo** parâmetro do `Get-Help` cmdlet. Por exemplo, para exibir todo o conteúdo do artigo de ajuda para o `Get-ChildItem` cmdlet, tipo:

```powershell
Get-Help Get-ChildItem -Full
```

Para obter detalhadas ajuda sobre os parâmetros de um cmdlet, utilize o **parâmetro** parâmetro do `Get-Help` cmdlet. Por exemplo obter detalhadas ajuda para todos os parâmetros do `Get-ChildItem` cmdlet, tipo:

```powershell
Get-Help Get-ChildItem -Parameter *
```

Para apresentar apenas os exemplos num artigo de ajuda, utilize o **exemplos** parâmetro do `Get-Help`.
Por exemplo, para apresentar apenas os exemplos neste artigo de ajuda para o `Get-ChildItem` cmdlet, tipo:

```powershell
Get-Help Get-ChildItem -Examples
```

Para obter informações sobre como escrever artigos de ajuda para os cmdlets que escreva, consulte [como escrever ajuda do Cmdlet](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets).

## <a name="getting-conceptual-help"></a>Obter ajuda conceitual

O `Get-Help` cmdlet também apresenta informações sobre artigos conceptuais no PowerShell, inclusive artigos sobre a linguagem do PowerShell. Ajuda conceitual artigos começam com o prefixo "about_", como about_line_editing. (O nome do artigo conceitual deve ser inserido em inglês mesmo em versões não inglesas do PowerShell.)

Para apresentar uma lista de artigos conceptuais, escreva:

```powershell
Get-Help about_*
```

Para apresentar um determinado artigo de ajuda, escreva o nome de artigo, por exemplo:

```powershell
Get-Help about_command_syntax
```

Os parâmetros da `Get-Help`, tal como **Detailed**, **parâmetro**, e **exemplos**, não têm efeito na exibição de artigos de ajuda conceituais.

## <a name="getting-help-about-providers"></a>Obter ajuda sobre os fornecedores

O `Get-Help` cmdlet apresenta informações sobre fornecedores do PowerShell. Para obter ajuda para um fornecedor, escreva `Get-Help` seguido pelo nome do fornecedor. Por exemplo, para obter ajuda para o fornecedor de registo, escreva:

```powershell
Get-Help registry
```

Para obter uma lista de todos os fornecedor de artigos de ajuda na sua sessão, escreva

```powershell
Get-Help -Category provider
```

Os parâmetros da `Get-Help`, tal como **Detailed**, **parâmetro**, e **exemplos**, não têm efeito na exibição de artigos de ajuda do fornecedor.

## <a name="getting-help-about-scripts-and-functions"></a>Obter ajuda sobre scripts e funções

Muitos scripts e funções do PowerShell têm artigos de ajuda. Utilize o `Get-Help` cmdlet para ver os artigos de ajuda para scripts e funções.

Para apresentar a ajuda para uma função, escreva `Get-Help` seguido do nome de função. Por exemplo, para obter ajuda para o `Disable-PSRemoting` de função, escreva:

```powershell
Get-Help Disable-PSRemoting
```

Para apresentar a ajuda para obter um script, escreva o caminho para o ficheiro de script. Se o script não estiver num caminho listado na variável de ambiente Path, tem de utilizar o caminho totalmente qualificado.

Por exemplo, se tiver um script chamado "TestScript.ps1" na sua unidade c:\\directory PS e teste, para exibir o artigo de ajuda para o script, tipo:

```powershell
Get-Help c:\ps-test\TestScript.ps1
```

Os parâmetros que foram concebidos para exibir o trabalho de ajuda do cmdlet para o script e a função, também ajudam. No entanto, a ajuda para funções e scripts não é apresentada quando executa `Get-Help *`.

Para obter informações sobre como escrever artigos de ajuda para seus scripts e funções, consulte os artigos seguintes:

- [about_Functions](/powershell/module/microsoft.powershell.core/about/about_functions)
- [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)

## <a name="getting-help-online"></a>Obter ajuda online

Visualizar os artigos de ajuda online é uma das melhores formas de obter ajuda. Artigos online são mais fáceis de atualizar e fornecer o conteúdo mais recente.

Para obter ajuda online, utilize o **Online** parâmetro do `Get-Help` cmdlet. Todos os artigos de ajuda que vêm com o PowerShell, incluindo o fornecedor de ajuda e conceitual (sobre), artigos de ajuda, estão disponíveis online na [PowerShell](/powershell/scripting/powershell-scripting) documentação.

> [!NOTE]
> Não é possível utilizar o **Online** parâmetro com conceitual (about_\*) ou artigos de ajuda do fornecedor.
> Ajuda online é opcional, para que ele não funciona para cada cmdlet, função ou script.

Por exemplo, para obter a versão online do artigo de ajuda o `Get-ChildItem` cmdlet, tipo:

```powershell
Get-Help Get-ChildItem -Online
```

PowerShell abre o artigo no seu browser predefinido. Se a ajuda online é suportada para um artigo de ajuda, também pode ver o URL do artigo de ajuda. O URL é apresentado na seção Links relacionados de um artigo de ajuda.

Por exemplo, para ver o URL para a versão online do cmdlet Add-Computer, escreva:

```powershell
Get-Help Add-Computer
```

A primeira linha na seção Links relacionados do artigo é mostrada abaixo.

```Output
Online version: http://go.microsoft.com/fwlink/?LinkId=821564
```

Para obter informações sobre como fornecer suporte online para seus artigos de ajuda, consulte [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

## <a name="see-also"></a>Consulte também

- [about_Functions](/powershell/module/microsoft.powershell.core/about/about_functions)
- [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- [Get-Help](/powershell/module/microsoft.powershell.core/get-help)
