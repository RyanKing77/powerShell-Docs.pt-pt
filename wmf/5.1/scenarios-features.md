---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Novos cenários e funcionalidades no WMF 5.1
ms.openlocfilehash: b00069aad7422f86d1462a62a6c4bc8a91e46705
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085457"
---
# <a name="new-scenarios-and-features-in-wmf-51"></a>Novos cenários e funcionalidades no WMF 5.1

> Nota: Estas informações são preliminares e estão sujeitas a alterações.

## <a name="powershell-editions"></a>Edições do PowerShell

Começando na versão 5.1, o PowerShell está disponível nas diferentes edições que denotam conjuntos de funcionalidade e compatibilidade de plataforma variados.

- **Edição Desktop:** Criado no .NET Framework e fornece compatibilidade com scripts e módulos de filtragem de versões do PowerShell a executar edições de requisitos de espaço total do Windows como núcleo de servidor e Desktop do Windows.
- **Edição Core:** Incorporada no .NET Core e fornece compatibilidade com scripts e módulos de filtragem de versões do PowerShell a executar edições de requisitos de espaço reduzido do Windows, como o servidor Nano e o Windows IoT.

**Saiba mais sobre como utilizar as edições do PowerShell**

- [Determinar a edição em execução do PowerShell com $PSVersionTable](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [Filtrar os resultados de Get-Module por CompatiblePSEditions utilizando o parâmetro PSEdition](/powershell/module/microsoft.powershell.core/get-module)
- [Impedir a execução do script, a menos que execute numa edição compatível do PowerShell](/powershell/gallery/concepts/script-psedition-support)
- [Declarar a compatibilidade de um módulo para versões específicas do PowerShell](/powershell/gallery/concepts/module-psedition-support)

## <a name="catalog-cmdlets"></a>Cmdlets Catalog

Foram adicionados dois cmdlets novos no [Microsoft.PowerShell.Security](/powershell/module/microsoft.powershell.security) módulo; eles gerar e validar os arquivos de catálogo do Windows.

### <a name="new-filecatalog"></a>New-FileCatalog
--------------------------------

Novo FileCatalog cria um ficheiro de catálogo do Windows para o conjunto de pastas e arquivos.
Este ficheiro de catálogo contém hashes para todos os ficheiros em caminhos especificados.
Os utilizadores possam distribuir o conjunto de pastas, juntamente com o correspondente arquivo de catálogo que representa essas pastas.
Estas informações são úteis para validar se foram efetuadas quaisquer alterações às pastas desde o momento de criação do catálogo.

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

Versões de catálogo 1 e 2 são suportadas.
Versão 1 utiliza o algoritmo de hash SHA1 para criar hashes de ficheiro; versão 2 usa SHA256.
Versão de catálogo 2 não é suportada no *Windows Server 2008 R2* ou *Windows 7*.
Deve utilizar a versão de catálogo 2 em *Windows 8*, *Windows Server 2012*e sistemas operativos posteriores.

![](../images/NewFileCatalog.jpg)

Esta ação cria o arquivo de catálogo.

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

Para verificar a integridade do arquivo de catálogo (Pester.cat no acima exemplo), inicie sessão usando [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) cmdlet.

### <a name="test-filecatalog"></a>Test-FileCatalog
--------------------------------

Teste FileCatalog valida o catálogo que representa um conjunto de pastas.

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

Este cmdlet compara todos os hashes de ficheiros e os caminhos relativos encontrado na *catálogo* com aqueles na *disco*.
Se detetar qualquer erro de correspondência entre os caminhos de hashes de ficheiro e devolve o estado como *ValidationFailed*.
Os utilizadores podem obter todas essas informações utilizando o *-detalhadas* parâmetro.
Ele também apresenta o estado de assinatura de catálogo na *assinatura* propriedade que é equivalente a chamar [Get-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Get-AuthenticodeSignature) cmdlet no arquivo de catálogo.
Os utilizadores também podem ignorar qualquer ficheiro durante a validação utilizando o *- FilesToSkip* parâmetro.

## <a name="module-analysis-cache"></a>Cache de análise de módulo

A partir do WMF 5.1, o PowerShell fornece controlo sobre o ficheiro que é utilizado para sobre um módulo, tal como os comandos que exporta os dados em cache.

Por predefinição, esta cache é armazenado no arquivo `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
A cache, durante a pesquisa por um comando, normalmente é lidos na inicialização e é escrita num thread em segundo plano algum tempo, após a importação de um módulo.

Para alterar a localização predefinida da cache, defina o `$env:PSModuleAnalysisCachePath` variável de ambiente antes de iniciar o PowerShell.
As alterações a esta variável de ambiente só afetarão a processos filhos.
O valor deve atribuir um nome um caminho completo (incluindo filename) que o PowerShell tem permissão para criar e escrever ficheiros.
Para desativar a cache de ficheiros, defina este valor para uma localização inválida, por exemplo:

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

Isso define o caminho para um dispositivo inválido.
Se o PowerShell não é possível escrever para o caminho, não é devolvido nenhum erro, mas pode ver o relatório através de uma análise de erros:

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

Quando o gravar o cache, o PowerShell irá verificar para módulos que não existem mais para evitar uma cache de grande desnecessariamente.
Por vezes, essas verificações não são desejáveis, caso em que pode desativá-las através da definição:

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

No WMF 5.1, a versão do Pester que é fornecido com o PowerShell foi atualizada de 3.3.5 para 3.4.0, com a adição de consolidação https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, que permite uma maior comportamento para Pester no servidor Nano.

Pode rever as alterações nas versões 3.3.5 para 3.4.0 ao inspecionar o ficheiro de ChangeLog.md em: https://github.com/pester/Pester/blob/master/CHANGELOG.md
