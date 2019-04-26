---
title: Importar um módulo do PowerShell | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 697791b3-2135-4a39-b9d7-8566ed67acf2
caps.latest.revision: 13
ms.openlocfilehash: bb5d036e5658c365a4fafa2cac05c0bba9f87019
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082250"
---
# <a name="importing-a-powershell-module"></a>Importing a PowerShell Module (Importar um Módulo do PowerShell)

Uma vez o tiver instalado um módulo num sistema, provavelmente desejará importar o módulo. A importação é o processo que carrega o módulo na memória do Active Directory, para que um usuário pode acessar esse módulo na sua sessão do PowerShell. No PowerShell 2.0, pode importar um módulo do PowerShell instalado recentemente com uma chamada para [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet. No PowerShell 3.0, o PowerShell é capaz de importar implicitamente um módulo quando uma das funções ou cmdlets no módulo é chamada por um utilizador. Tenha em atenção que as duas versões partem do princípio de que instale o módulo num local em que o PowerShell é capaz de encontrá-lo. Para obter mais informações, consulte [instalar um módulo do PowerShell](./installing-a-powershell-module.md). Pode utilizar um manifesto de módulo para restringir que partes do seu módulo são exportadas, e pode usar parâmetros do `Import-Module` chamada para restringir que partes são importados.

## <a name="importing-a-snap-in-powershell-10"></a>Importação de um Snap-In (PowerShell 1.0)

Módulos não existia no PowerShell 1.0: em vez disso, tinha que registar e utilizar o snap-ins. No entanto, não é recomendado que utilize essa tecnologia neste momento, como módulos são geralmente mais fáceis de instalar e importar. Para obter mais informações, consulte [como criar um Snap-in do PowerShell Windows](../cmdlet/how-to-create-a-windows-powershell-snap-in.md).

## <a name="importing-a-module-with-import-module-powershell-20"></a>Importar um módulo com Import-Module (PowerShell 2.0)

PowerShell 2.0 usa o adequadamente nomeados [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet para importar módulos. Quando este cmdlet é executado, o Windows PowerShell procura o módulo especificado em diretórios especificados no `PSModulePath` variável. Quando é encontrado no diretório especificado, o Windows PowerShell procura ficheiros pela seguinte ordem: os ficheiros de manifesto de módulo (. psd1), ficheiros de módulo (. psm1), ficheiros de módulo binário (. dll) do script. Para obter mais informações sobre como adicionar diretórios para a pesquisa, consulte [modificar o caminho de instalação PSModulePath](./modifying-the-psmodulepath-installation-path.md). O código a seguir descreve como importar um módulo:

```powershell
Import-Module myModule
```

Supondo que myModule encontrava-se no `PSModulePath`, PowerShell carrega myModule na memória do Active Directory. Se myModule não foi localizado num `PSModulePath` caminho, pode ainda explicitamente dizer ao PowerShell onde encontrá-lo:

```powershell
Import-Module -Name C:\myRandomDirectory\myModule -Verbose
```

Também pode utilizar o opção - verboso parâmetro para identificar o que está a ser exportado fora o módulo e o que está a ser importado para a memória do Active Directory. Exportações e importações de restringem o que é exposto ao utilizador: a diferença é que controla a visibilidade. Essencialmente, exportações são controladas por código dentro do módulo. Por outro lado, imports são controladas mediante a `Import-Module` chamar. Para obter mais informações, consulte **restringir os membros que são importados**, abaixo.

## <a name="implicitly-importing-a-module-powershell-30"></a>Implicitamente importar um módulo (PowerShell 3.0)

A partir do Windows PowerShell 3.0, os módulos são importados automaticamente quando qualquer cmdlet ou uma função no módulo é utilizada num comando. Esta funcionalidade funciona em qualquer módulo num diretório que isso incluídos no valor dos **PSModulePath** variável de ambiente. Se não salvar seu módulo num caminho válido no entanto, pode ainda carregá-las usando o explícita [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) opção, descrita acima.

As seguintes ações acionam a importação automática de um módulo, também conhecido como "módulo de carregamento automático."

- Utilizando um cmdlet num comando. Por exemplo, se escrever `Get-ExecutionPolicy` importa o módulo de Microsoft.PowerShell.Security que contém o `Get-ExecutionPolicy` cmdlet.

- Utilizar o [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet para obter o comando.  Por exemplo, se escrever `Get-Command Get-JobTrigger` importa os **PSScheduledJob** módulo que contém o `Get-JobTrigger` cmdlet. A `Get-Command` comando que inclui carateres universais é considerado como estando a deteção e não aciona a importação de um módulo.

- Utilizar o [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet para obter ajuda para um cmdlet. Por exemplo, se escrever `Get-Help Get-WinEvent` importa o módulo de Microsoft.PowerShell.Diagnostics que contém o `Get-WinEvent` cmdlet.

Para suportar a importação automática de módulos, o `Get-Command` cmdlet obtém todos os cmdlets e funções em todos os módulos instalados, mesmo que o módulo não é importado para a sessão. Para obter mais informações, consulte o tópico de ajuda para o [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet.

## <a name="the-importing-process"></a>O processo de importação

Quando um módulo é importado, um Estado de sessão novo é criado para o módulo e um [System.Management.Automation.PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) objeto é criado na memória. Um Estado de sessão é criado para cada módulo que é importado (Isto inclui o módulo de raiz e quaisquer módulos aninhados). Os membros que são exportados a partir do módulo de raiz, incluindo quaisquer membros que foram exportados para o módulo de raiz por quaisquer módulos aninhados, em seguida, são importados para o estado da sessão do chamador.

Os metadados de membros que são exportados a partir de um módulo de ter uma propriedade de ModuleName. Esta propriedade é preenchida com o nome do módulo que exportou-los.

> [!WARNING]
> Se o nome de um membro exportado utiliza um verbo não aprovado ou se o nome do membro utiliza caracteres restritos, é apresentado um aviso quando o [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet é executado.

Por predefinição, o [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet não devolve quaisquer objetos para o pipeline. No entanto, o cmdlet suporta um `PassThru` parâmetro pode ser utilizado para devolver uma [System.Management.Automation.PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) objeto para cada módulo que é importado. Para enviar a saída para o anfitrião, os utilizadores devem executar o [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet.

## <a name="restricting--the-members-that-are-imported"></a>Restringir os membros que são importados

Quando um módulo é importado, utilizando o [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet, por predefinição, o módulo exportado todos os membros são importados para a sessão, incluindo quaisquer comandos exportados para o módulo por um módulo aninhado. Por predefinição, variáveis e aliases não são exportados. Para restringir os membros que são exportados, utilize um [manifesto do módulo](./how-to-write-a-powershell-module-manifest.md). Para restringir os membros que são importados, utilize os seguintes parâmetros do `Import-Module` cmdlet.

- `Function`: Este parâmetro limita as funções que são exportadas. (Se estiver a utilizar um manifesto de módulo, consulte a chave de FunctionsToExport.)

- `Cmdlet`: Este parâmetro restringe os cmdlets que são exportados (se estiver a utilizar uma veja manifesto, módulo a chave de CmdletsToExport.)

- `Variable`: Este parâmetro restringe as variáveis que são exportadas (se estiver a utilizar uma veja manifesto, módulo a chave de VariablesToExport.)

- `Alias`: Este parâmetro restringe os aliases que são exportados (se estiver a utilizar uma veja manifesto, módulo a chave de AliasesToExport.)

## <a name="see-also"></a>Veja Também

[Escrever um módulo do Windows PowerShell](./writing-a-windows-powershell-module.md)
