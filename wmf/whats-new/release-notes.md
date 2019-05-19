---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Notas de versão do WMF 5.x
ms.openlocfilehash: 8bdc423234cf0b104b72b1bee1de35e50783d8a4
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856400"
---
# <a name="windows-management-framework-wmf-5x-release-notes"></a>Notas de versão do Windows Management Framework (WMF) 5.x

## <a name="wmf-50-changes"></a>Altera o WMF 5.0

- PowerShell 5.0 adiciona um novo estruturado **informações** stream
- Melhorias do DSC, incluindo quatro novos recursos de DSC:
  - WindowsFeatureSet
  - WindowsOptionalFeatureSet
  - ServiceSet
  - ProcessSet
- Foi adicionado a administração apenas suficiente para ativar a administração baseada em funções por meio de comunicação remota do PowerShell
- PowerShell 5.0 estende a linguagem para incluir classes definidas pelo utilizador e enumerações
- Recursos do ISE do PowerShell e a depuração remota foi adicionado de depuração aprimorada
- Adicionados os módulos do PowerShellGet e PackageManagement
- O registo melhorado do script de PowerShell e transcrições
- Adição de cmdlets de sintaxe de mensagem criptográfica
- WMF 5.0 inclui o módulo de NetworkSwitchManager para Windows
- Adicionado o módulo de Microsoft.PowerShell.ODataUtils
- Foi adicionado suporte para Software de registo de inventário (SIL)
- Novo servidor ou ao atualizar cmdlets em resposta a pedidos de utilizador e problemas

## <a name="wmf-51-changes"></a>Alterações do WMF 5.1

WMF 5.1 inclui os componentes PowerShell, WMI, WinRM e registo de inventário de Software (SIL) que foram lançados com o Windows Server 2016. WMF 5.1 pode ser instalado no Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 e 2012 R2 e fornece vários melhoramentos relativamente WMF 5.0 incluindo:

- Novos cmdlets
- Melhorias do PowerShellGet com a imposição de módulos assinados e a instalação de módulos JEA
- Adicionado suporte ao PackageManagement para Contentores, Configuração CBS, configuração com base em EXE, pacotes CAB
- Melhorias na depuração para classes DSC e PowerShell
- Melhorias de segurança, incluindo a imposição de módulos assinados de catálogo provenientes do Servidor de Solicitação e ao utilizar os cmdlets PowerShellGet
- Respostas a vários pedidos e problemas de utilizadores

## <a name="powershell-editions"></a>Edições do PowerShell

A partir da versão 5.1, o PowerShell está disponível nas diferentes edições que denotam conjuntos diferentes de recursos e compatibilidade de plataforma.

- **Edição Desktop:** Criado no .NET Framework e fornece compatibilidade com scripts e módulos de filtragem de versões do PowerShell a executar edições de requisitos de espaço total do Windows como núcleo de servidor e Desktop do Windows.
- **Edição Core:** Incorporada no .NET Core e fornece compatibilidade com scripts e módulos de filtragem de versões do PowerShell a executar edições de requisitos de espaço reduzido do Windows, como o servidor Nano e o Windows IoT.

### <a name="learn-more-about-using-powershell-editions"></a>Saiba mais sobre como utilizar as edições do PowerShell

- [Determinar a edição em execução do PowerShell com $PSVersionTable](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [Filtrar os resultados de Get-Module por CompatiblePSEditions utilizando o parâmetro PSEdition](/powershell/module/microsoft.powershell.core/get-module)
- [Impedir a execução do script, a menos que execute numa edição compatível do PowerShell](/powershell/gallery/concepts/script-psedition-support)
- [Declarar a compatibilidade de um módulo para versões específicas do PowerShell](/powershell/gallery/concepts/module-psedition-support)

## <a name="module-analysis-cache"></a>Cache de análise de módulo

A partir do WMF 5.1, o PowerShell fornece controlo sobre o ficheiro que é utilizado para sobre um módulo, tal como os comandos que exporta os dados em cache.

Por predefinição, esta cache é armazenado no arquivo `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`. A cache, durante a pesquisa por um comando, normalmente é lidos na inicialização e é escrita num thread em segundo plano algum tempo, após a importação de um módulo.

Para alterar a localização predefinida da cache, defina o `$env:PSModuleAnalysisCachePath` variável de ambiente antes de iniciar o PowerShell. As alterações a esta variável de ambiente só afetarão a processos filhos. O valor deve atribuir um nome um caminho completo (incluindo filename) que o PowerShell tem permissão para criar e escrever ficheiros. Para desativar a cache de ficheiros, defina este valor para uma localização inválida, por exemplo:

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

Isso define o caminho para um dispositivo inválido. Se o PowerShell não é possível escrever para o caminho, não é devolvido nenhum erro, mas pode ver o relatório através de uma análise de erros:

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

Quando o gravar o cache, o PowerShell irá verificar para módulos que não existem mais para evitar uma cache de grande desnecessariamente. Por vezes, essas verificações não são desejáveis, caso em que pode desativá-las através da definição:

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

A definição desta variável de ambiente entrarão em vigor imediatamente no processo atual.

## <a name="specifying-module-version"></a>Especificar a versão do módulo

No WMF 5.1, `using module` se comporta da mesma forma que outras construções relacionados com o módulo do PowerShell.
Anteriormente, tinha que há como especificar uma versão do módulo específico; Se existirem várias versões de presentes, isso resultou num erro.

No WMF 5.1:

- Pode usar [ModuleSpecification construtor (tabela de hash)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).
  Esta tabela de hash tem o mesmo formato que `Get-Module -FullyQualifiedName`.

  **Exemplo:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

- Se existirem várias versões do módulo, PowerShell utiliza a **mesma lógica de resolução** como `Import-Module` e não retorna um erro - o mesmo comportamento `Import-Module` e `Import-DscResource`.

## <a name="improvements-to-pester"></a>Melhorias à Pester

No WMF 5.1, a versão do Pester que é fornecido com o PowerShell foi atualizada de 3.3.5 para 3.4.0.
Esta atualização permite que o melhor comportamento para Pester no servidor Nano.

Pode rever as alterações no pestes inspecionando o [registo de alterações](https://github.com/pester/Pester/blob/master/CHANGELOG.md) no repositório do GitHub.
