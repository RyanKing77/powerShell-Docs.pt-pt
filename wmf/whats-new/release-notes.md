---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Notas de Versão do WMF 5.x
ms.openlocfilehash: 8924240a4bbedcd34bc68b7cacdd23189a3716d6
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848151"
---
# <a name="windows-management-framework-wmf-5x-release-notes"></a>Notas de versão do Windows Management Framework (WMF) 5. x

## <a name="wmf-50-changes"></a>Alterações do WMF 5,0

- O PowerShell 5,0 adiciona um novo fluxo de **informações** estruturadas
- Melhorias no DSC, incluindo quatro novos recursos de DSC:
  - WindowsFeatureSet
  - WindowsOptionalFeatureSet
  - ServiceSet
  - ProcessSet
- Adicionado apenas a administração suficiente para habilitar a administração baseada em funções por meio de comunicação remota do PowerShell
- O PowerShell 5,0 estende a linguagem para incluir classes e enumerações definidas pelo usuário
- Recursos de depuração aprimorados no ISE do PowerShell e adição de depuração remota
- Adicionados os módulos PowerShellGet e PackageManagement
- Log e transcrições de script do PowerShell aprimorados
- Adicionar cmdlets de sintaxe de mensagem criptográfica
- O WMF 5,0 inclui o módulo NetworkSwitchManager para Windows
- Adicionado o módulo Microsoft. PowerShell. ODataUtils
- Adicionado suporte para log de inventário de software (SIL)
- Cmdlets novo ou de atualização do servidor em resposta a solicitações e problemas do usuário

## <a name="wmf-51-changes"></a>Alterações do WMF 5,1

O WMF 5,1 inclui os componentes do PowerShell, WMI, WinRM e SIL (log de inventário de software) que foram lançados com o Windows Server 2016. O WMF 5,1 pode ser instalado no Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 e 2012 R2 e fornece várias melhorias em relação ao WMF 5,0, incluindo:

- Novos cmdlets
- Melhorias do PowerShellGet com a imposição de módulos assinados e a instalação de módulos JEA
- Adicionado suporte ao PackageManagement para Contentores, Configuração CBS, configuração com base em EXE, pacotes CAB
- Melhorias na depuração para classes DSC e PowerShell
- Melhorias de segurança, incluindo a imposição de módulos assinados de catálogo provenientes do Servidor de Solicitação e ao utilizar os cmdlets PowerShellGet
- Respostas a vários pedidos e problemas de utilizadores

> [!IMPORTANT]
> Antes de instalar o WMF 5,1 no Windows Server 2008 ou no Windows 7, confirme se o WMF 3,0 não está instalado. Para obter mais informações, consulte [pré-requisitos do WMF 5,1 para Windows Server 2008 R2 SP1 e Windows 7 SP1](../setup/install-configure.md#wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1).

## <a name="powershell-editions"></a>Edições do PowerShell

A partir da versão 5,1, o PowerShell está disponível em diferentes edições que denotam diversos conjuntos de recursos e compatibilidade de plataforma.

- **Edição de desktop:** Criado com base em .NET Framework e fornece compatibilidade com scripts e módulos que visam versões do PowerShell em execução em edições de superfície completa do Windows, como Server Core e Windows desktop.
- **Core Edition:** Criado com base no .NET Core e fornece compatibilidade com scripts e módulos destinados a versões do PowerShell em execução em edições de superfície reduzida do Windows, como nano Server e Windows IoT.

### <a name="learn-more-about-using-powershell-editions"></a>Saiba mais sobre como usar as edições do PowerShell

- [Determinar a edição em execução do PowerShell usando $PSVersionTable](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [Filtrar resultados de Get-Module por CompatiblePSEditions usando o parâmetro PSEdition](/powershell/module/microsoft.powershell.core/get-module)
- [Impedir a execução do script, a menos que seja executado em uma edição compatível do PowerShell](/powershell/gallery/concepts/script-psedition-support)
- [Declarar a compatibilidade de um módulo com versões específicas do PowerShell](/powershell/gallery/concepts/module-psedition-support)

## <a name="module-analysis-cache"></a>Cache de análise de módulo

A partir do WMF 5,1, o PowerShell fornece controle sobre o arquivo usado para armazenar em cache dados sobre um módulo, como os comandos que ele exporta.

Por padrão, esse cache é armazenado no arquivo `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`. O cache é normalmente lido na inicialização durante a pesquisa de um comando e é gravado em um thread em segundo plano depois que um módulo é importado.

Para alterar o local padrão do cache, defina a variável `$env:PSModuleAnalysisCachePath` de ambiente antes de iniciar o PowerShell. As alterações nessa variável de ambiente afetarão apenas os processos filhos. O valor deve nomear um caminho completo (incluindo o nome de arquivo) que o PowerShell tem permissão para criar e gravar arquivos. Para desabilitar o cache de arquivos, defina esse valor como um local inválido, por exemplo:

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

Isso define o caminho para um dispositivo inválido. Se o PowerShell não puder gravar no caminho, nenhum erro será retornado, mas você poderá ver o relatório de erros usando um rastreador:

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

Ao gravar o cache, o PowerShell verificará se há módulos que não existem mais para evitar um cache desnecessariamente grande. Às vezes, essas verificações não são desejáveis; nesse caso, você pode desativá-las definindo:

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

Definir essa variável de ambiente entrará em vigor imediatamente no processo atual.

## <a name="specifying-module-version"></a>Especificando a versão do módulo

No WMF 5,1, `using module` o se comporta da mesma forma que outras construções relacionadas ao módulo no PowerShell.
Anteriormente, não era possível especificar uma versão específica do módulo; Se houver várias versões presentes, isso resultaria em um erro.

No WMF 5,1:

- Você pode usar o [Construtor ModuleSpecification (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).

  Esta tabela de hash tem o mesmo formato `Get-Module -FullyQualifiedName`que.

  **Exemplo:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

- Se houver várias versões do módulo, o PowerShell usará a **mesma lógica** de resolução `Import-Module` que e não retornará um erro – `Import-Module` o mesmo comportamento de e `Import-DscResource`.

## <a name="improvements-to-pester"></a>Melhorias no Pester

No WMF 5,1, a versão do Pester que acompanha o PowerShell foi atualizada de 3.3.5 para 3.4.0.
Essa atualização permite um melhor comportamento para o Pester no nano Server.

Você pode examinar as alterações no pestware inspecionando o [changelog](https://github.com/pester/Pester/blob/master/CHANGELOG.md) no repositório do github.
