---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Novos cenários e funcionalidades no WMF 5.1
ms.openlocfilehash: 77b439e61c5802f8ddbc4a0f39923cc8c0c36fe9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190320"
---
# <a name="new-scenarios-and-features-in-wmf-51"></a>Novos cenários e funcionalidades no WMF 5.1

> Nota: Estas informações são preliminares e estão sujeitos a alterações.

## <a name="powershell-editions"></a>Edições do PowerShell

Começando na versão 5.1, o PowerShell está disponível nas diferentes edições que denotam conjuntos de funcionalidade e compatibilidade de plataforma variados.

- **Edição Desktop:** incorporada no .NET Framework e fornece compatibilidade com scripts e módulos de filtragem de versões do PowerShell a executar edições de requisitos de espaço total do Windows, tais como Server Core e o Ambiente de trabalho do Windows.
- **Edição Core:** incorporada no .NET Core e fornece compatibilidade com scripts e módulos de filtragem de versões do PowerShell a executar edições de requisitos de espaço reduzido do Windows, tais como Servidor Nano e o IoT do Windows.

**Saiba mais sobre como utilizar as edições do PowerShell**

- [Determinar a edição em execução do PowerShell com $PSVersionTable](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [Filtrar os resultados de Get-Module pelos CompatiblePSEditions utilizando o parâmetro PSEdition](/powershell/module/microsoft.powershell.core/get-module)
- [Impedir a execução do script, exceto se executar uma edição compatíveis do PowerShell](/powershell/gallery/psget/script/scriptwithpseditionsupport)
- [Declarar a compatibilidade com um módulo versões específicas do PowerShell](/powershell/gallery/psget/module/modulewithpseditionsupport)

## <a name="catalog-cmdlets"></a>Cmdlets de catálogo

Foram adicionados dois novos cmdlets no [Microsoft.PowerShell.Security](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security) módulo; estas gerar e validar os ficheiros de catálogo do Windows.

### <a name="new-filecatalog"></a>New-FileCatalog
--------------------------------

Novo FileCatalog cria um ficheiro de catálogo do Windows para o conjunto de ficheiros e pastas.
Este ficheiro de catálogo contém hashes para todos os ficheiros em caminhos especificados.
Os utilizadores possam distribuir o conjunto de pastas, juntamente com o ficheiro de catálogo correspondente que representa essas pastas.
Estas informações são úteis para validar se todas as alterações foram efetuadas às pastas desde a hora de criação do catálogo.

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

São suportadas versões do catálogo 1 e 2.
Versão 1 utiliza o algoritmo de hash SHA1 para criar os hashes de ficheiro; versão 2 utiliza SHA256.
Versão 2 do catálogo não é suportada em *Windows Server 2008 R2* ou *Windows 7*.
Deve utilizar a versão 2 do catálogo em *Windows 8*, *Windows Server 2012*e sistemas operativos posteriores.

![](../images/NewFileCatalog.jpg)

Esta ação cria o ficheiro de catálogo.

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

Para verificar a integridade dos ficheiros de catálogo (Pester.cat no acima exemplo), inicie sessão com [conjunto AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.

### <a name="test-filecatalog"></a>Teste FileCatalog
--------------------------------

Teste FileCatalog valida o catálogo que representa um conjunto de pastas.

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

Este cmdlet compara todos os hashes de ficheiros e os respetivos caminhos relativos encontrado na *catálogo* com aqueles no *disco*.
Se detetar qualquer erro de correspondência entre os hashes de ficheiros e caminhos devolve o estado como *ValidationFailed*.
Os utilizadores podem obter todos os estas informações ao utilizar o *-detalhadas* parâmetro.
Também apresenta assinatura estado do catálogo no *assinatura* propriedade que é equivalente a chamar [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) cmdlet no ficheiro de catálogo.
Os utilizadores também podem ignorar qualquer ficheiro durante a validação utilizando o *- FilesToSkip* parâmetro.

## <a name="module-analysis-cache"></a>Cache de análise do módulo

A partir do WMF 5.1, PowerShell fornece controlo sobre o ficheiro que é utilizado para sobre um módulo, tal como os comandos que exporta os dados em cache.

Por predefinição, esta cache é armazenado no ficheiro `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
A cache, ao procurar um comando, normalmente é lido no arranque e é escrito num thread em segundo plano algum tempo depois de um módulo é importado.

Para alterar a localização predefinida da cache, defina o `$env:PSModuleAnalysisCachePath` variável de ambiente antes de iniciar o PowerShell.
As alterações a esta variável de ambiente só afetarão processos subordinados.
O valor deve nome um caminho completo (incluindo filename) PowerShell tem permissão para criar e escrever em ficheiros.
Para desativar a cache de ficheiros, defina este valor para uma localização inválida, por exemplo:

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

Define o caminho para um dispositivo inválido.
Se o PowerShell não é possível escrever o caminho, não é devolvido nenhum erro, mas pode ver através da utilização de uma análise do relatório de erros:

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

Ao escrever a saída da cache, o PowerShell irá verificar para módulos que já não existem para evitar uma cache desnecessariamente grande.
Por vezes, estas verificações não são desejável, caso em que pode desativá-los através da definição:

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

A definição desta variável de ambiente entrarão em vigor imediatamente no processo atual.

## <a name="specifying-module-version"></a>Especificar a versão do módulo

No WMF 5.1, `using module` comporta-se da mesma forma que outras construções relacionados com o módulo do PowerShell.
Anteriormente, era necessário uma forma para especificar uma versão do módulo específico; Se existirem várias versões presentes, este resultou num erro.

No WMF 5.1:

- Pode utilizar [ModuleSpecification construtor (tabela hash)](https://msdn.microsoft.com/library/jj136290).
Esta tabela hash tem o mesmo formato que `Get-Module -FullyQualifiedName`.

**Exemplo:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

- Se existirem várias versões do módulo, PowerShell utiliza o **mesma lógica resolução** como `Import-Module` e não devolve um erro - o mesmo comportamento de `Import-Module` e `Import-DscResource`.

## <a name="improvements-to-pester"></a>Melhoramentos à Pester

No WMF 5.1, a versão do Pester que é fornecido com o PowerShell foi atualizada de 3.3.5 para 3.4.0, com a adição de consolidação https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, que permite uma maior comportamento para Pester no servidor de nano for apresentado.

Pode rever as alterações em versões 3.3.5 para 3.4.0 ao inspecionar o ficheiro de ChangeLog.md em: https://github.com/pester/Pester/blob/master/CHANGELOG.md
