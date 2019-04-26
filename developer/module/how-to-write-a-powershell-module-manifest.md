---
title: Como escrever um manifesto de módulo do PowerShell | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e082c2e3-12ce-4032-9caf-bf6b2e0dcf81
caps.latest.revision: 23
ms.openlocfilehash: 93a8c11099a9883127bca87422e1acaebfd2c093
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082301"
---
# <a name="how-to-write-a-powershell-module-manifest"></a>How to Write a PowerShell Module Manifest (Como Escrever um Manifesto de Módulo do PowerShell)

Uma vez ter escrito o módulo do Windows PowerShell, opcionalmente, pode adicionar um manifesto de módulo. Um manifesto de módulo é um ficheiro de script do PowerShell que pode utilizar para incluir informações sobre o módulo. Por exemplo, pode descrever o autor, especificar os ficheiros no módulo (como módulos aninhados), executados scripts para personalizar o ambiente do utilizador, carregar o tipo e arquivos de formatação, definem os requisitos de sistema e limitam os membros que exporta o módulo.

## <a name="creating-a-module-manifest"></a>Criar um manifesto de módulo

R *manifesto do módulo* é um arquivo de dados do Windows PowerShell (. psd1) que descreve o conteúdo de um módulo e determina a forma como um módulo é processado. O próprio arquivo de manifesto é um arquivo de texto que contém uma tabela de hash de chaves e valores. Vai ligar a um arquivo de manifesto para um módulo, nomeando-o mesmo que o módulo e colocá-lo na raiz do diretório de módulo.

Para obter módulos simples que contêm apenas um único psm1 ou um assembly binário, um manifesto de módulo é opcional. No entanto, é recomendado que utilize um manifesto de módulo sempre que possível, pois eles são úteis para ajudar a organizar seu código e para manter informações de controlo de versões. Além disso, um manifesto de módulo é necessária para exportar um assembly que está instalado no cache de assemblies global. Um manifesto de módulo também é necessário para módulos que suportam a funcionalidade de ajuda Atualizável. Ou seja, ajuda Atualizável utiliza a **HelpInfoUri** chave no manifesto do módulo para localizar o ficheiro de informações (HelpInfo XML) de ajuda que contém a localização dos ficheiros de ajuda atualizada para o módulo. Para obter mais informações sobre Ajuda Atualizável, consulte [apoio ajuda Atualizável](./supporting-updatable-help.md).

### <a name="to-create-and-use-a-module-manifest"></a>Criar e utilizar um manifesto de módulo

1. Para criar um manifesto de módulo, tem várias opções:

   1. Diretamente criar a tabela de hash com as informações mínimas necessárias e guarde-o para um ficheiro. psd1, que tem o mesmo nome que módulo. Assim que tiver feito isso, pode abrir o ficheiro e adicionar manualmente os valores adequados.

      `'@{ModuleVersion="1.0"}' > myModuleName.psd1`

   2. Ou ligue a [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet, com uma ou mais dos valores predefinidos passados como parâmetros. (Tenha em atenção que o apenas o nome do ficheiro é necessário para gerar um manifesto, no entanto.) Isto irá criar um manifesto de módulo com todos os manifestos valores que forneceu declarados explicitamente e com o resto que contém o valor padrão apropriado.

      `New-ModuleManifest myModuleName.psd1 -ModuleVersion "2.0" -Author "YourNameHere"`

   3. Por fim, também pode criar um ficheiro. psd1 vazia e copiar o modelo na parte inferior deste tópico para o ficheiro e preencha os valores relevantes. O único requisito real nesse caso seria Certifique-se de que o ficheiro foi com o mesmo nome do módulo.

2. Adicione quaisquer elementos adicionais para que deseja ter no ficheiro de manifesto.

   Em termos gerais, isso provavelmente será feito em qualquer editor de texto que preferir, como o bloco de notas. No entanto tecnicamente este é um ficheiro de script que contém o código, pelo que pode ser útil editá-lo num ambiente de desenvolvimento ou de script real, como o ISE do PowerShell. Novamente, tenha em atenção de que todos os elementos de um arquivo de manifesto são opcionais, exceto para o número de ModuleVersion.

   Para obter descrições de chaves e valores, pode ter num manifesto de módulo, consulte a **elementos de manifesto de módulo** abaixo. Para obter mais informações, veja as descrições de parâmetros nos [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet.

3. Opcionalmente, pode optar por adicionar mais código para o manifesto de módulo, para lidar com qualquer cenários que não devem ser abrangidos pelos elementos de manifesto do módulo de base.

   Devido a preocupações com a segurança, o PowerShell irá executar apenas um pequeno subconjunto das operações disponíveis num arquivo de manifesto do módulo. Em geral, pode utilizar o **se** instrução, operadores e comparação de média aritmética e os tipos de dados básicos do PowerShell.

4. Assim que tiver criado o manifesto de módulo, pode testá-lo (para confirmar que qualquer caminhos descritos o manifesto estão corretas) com uma chamada para [teste ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest).

   `Test-ModuleManifest myModuleName.psd1`

5. Certifique-se de que o manifesto de módulo está localizado no nível superior do diretório que contém seu módulo.

   Quando copiar seu módulo num sistema e importá-lo, o PowerShell irá utilizar o manifesto de módulo para importar o módulo.

6. Opcionalmente, pode testar diretamente o manifesto de módulo com uma chamada para [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) por dot sourcing o manifesto em si.

   `Import-Module .\myModuleName.psd1`

## <a name="module-manifest-elements"></a>Elementos de manifesto de módulo

A tabela seguinte descreve os elementos que pode ter num manifesto de módulo

|Elemento|Predefinido|Descrição|
|-------------|-------------|-----------------|
|RootModule<br /><br /> Type: string|' '|Módulo ou binário módulo ficheiro de script associado a esse manifesto. As versões anteriores do PowerShell chamado este elemento o ModuleToProcess.<br /><br /> Tipos possíveis para o módulo de raiz podem estar vazios (que fará com que isso uma **manifesto** módulo), o nome de um módulo de script (. psm1, o que torna isso um **Script** módulo), ou o nome de um módulo binário (.exe ou. dll, o que faz isso uma **binário** módulo). Colocar o nome de um manifesto de módulo (. psd1) ou um ficheiro de script (. ps1) neste elemento fará com que um erro ocorra.|
|ModuleVersion<br /><br /> Type: string|1.0|Número da versão deste módulo. A cadeia tem de ser capaz de converter em [ter]. Ou seja, ' #. #. #. #. #'. `Import-Module` irá carregar o módulo primeiro encontradas no **$psModulePath** que corresponde ao nome e tem, pelo menos, tão elevada um ModuleVersion, como o `-MinimumVersion` parâmetro. Para importar uma versão específica, utilize o`-RequiredVersion` parâmetro, em vez disso.<br /><br /> Exemplo: `ModuleVersion = '1.0'`|
|GUID<br /><br /> Type: string|GUID gerado automaticamente|ID utilizado para identificar exclusivamente este módulo. Tenha em atenção que atualmente não é possível importar um módulo pelo GUID.<br /><br /> Exemplo: `GUID = 'cfc45206-1e49-459d-a8ad-5b571ef94857'`|
|Autor<br /><br /> Type: string|Nenhum|Autor deste módulo.<br /><br /> Exemplo: `Author = 'AuthorNameHere'`|
|CompanyName<br /><br /> Type: string|Desconhecida|Empresa ou fabricante deste módulo.<br /><br /> Exemplo: `CompanyName = 'Fabrikam'`|
|Copyright<br /><br /> Type: string|(c) [currentYear] [autor]. Todos os direitos reservados.|Declaração de direitos autorais para este módulo.<br /><br /> Exemplo: `Copyright = '2016 AuthorName. All rights reserved.'`|
|Descrição<br /><br /> Type: string|' '|Descrição da funcionalidade fornecida por este módulo.<br /><br /> Exemplo: `Description = 'This is a description of a module.'`|
|PowerShellVersion<br /><br /> Type: string|' '|Versão mínima do motor do PowerShell de Windows exigido por este módulo. Atuais valores válidos são 1.0, 2.0, 3.0, 4.0 e 5.0.<br /><br /> Exemplo: `PowerShellVersion = '5.0'`|
|PowerShellHostName<br /><br /> Type: string|' '|Especifica o nome do anfitrião do Windows PowerShell que sejam necessários para o módulo. Este nome é fornecido pelo Windows PowerShell. Para localizar o nome de um programa de anfitrião, o programa, escreva: `$host.name` .<br /><br /> Exemplo: `PowerShellHostName = 'Windows PowerShell ISE Host'`|
|PowerShellHostVersion<br /><br /> Type: string|' '|Versão mínima do anfitrião necessário para este módulo Windows PowerShell.<br /><br /> Exemplo: `PowerShellHostVersion = '2.0'`|
|DotNetFrameworkVersion<br /><br /> Type: string|' '|Versão mínima do Microsoft .NET Framework necessária para este módulo.<br /><br /> Exemplo: `DotNetFrameworkVersion = '3.5'`|
|CLRVersion<br /><br /> Type: string|' '|Versão mínima do common language runtime (CLR) exigido por este módulo.<br /><br /> Exemplo: `CLRVersion = '3.5'`|
|ProcessorArchitecture<br /><br /> Type: string|' '|Arquitetura do processador (nenhum, X86, Amd64) exigida por este módulo. Os valores válidos são x86, AMD64 IA64 e nenhum (desconhecido ou não especificado).<br /><br /> Exemplo: `ProcessorArchitecture = 'x86'`|
|RequiredModules<br /><br /> Type: [string[]]|@()|Módulos que tem de ser importados para o ambiente global antes de importar este módulo. Isso será carregado qualquer módulos listados, a menos que elas já foram carregadas. (Por exemplo, alguns módulos podem já estar carregados por um módulo diferente.). Também é possível especificar uma versão específica para carregar usando `RequiredVersion` vez `ModuleVersion`. Quando utilizar `ModuleVersion` que irá carregar a versão mais recente disponível com um mínimo da versão especificada.<br /><br /> Exemplo: `RequiredModules = @(@{ModuleName="myDependentModule"; ModuleVersion="2.0"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`<br /><br /> Exemplo: `RequiredModules = @(@{ModuleName="myDependentModule"; RequiredVersion="1.5"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`|
|RequiredAssemblies<br /><br /> Type: [string[]]|@()|Assemblies que têm de ser carregados antes de importar este módulo.<br /><br /> Observe que, ao contrário de RequiredModules, PowerShell carregará o RequiredAssemblies se já não são carregadas.|
|ScriptsToProcess<br /><br /> Type: [string[]]|@()|Ficheiros de script (. ps1) que são executados no estado de sessão do chamador, quando o módulo é importado. Isto pode ser a sessão global, estada ou, para aninhados módulos, o estado da sessão de outro módulo. Pode utilizar estes scripts para preparar um ambiente, assim como pode usar um script de início de sessão.<br /><br /> Estes scripts são executados antes de qualquer um dos módulos listados no manifesto são carregados.|
|TypesToProcess<br /><br /> Type: [Object[]]|@()|Tipo de ficheiros (.ps1xml) a ser carregado quando importar este módulo.|
|FormatsToProcess<br /><br /> Type: [Object[]]|@()|Formato de ficheiros (.ps1xml) a ser carregado quando importar este módulo.|
|NestedModules<br /><br /> Type: [Object[]]|@()|Módulos importar como aninhados módulos do módulo especificado no RootModule/ModuleToProcess.<br /><br /> Adicionar um nome de módulo para este elemento é semelhante ao chamar `Import-Module` de dentro de seu código de script e o assembly. A principal diferença é que é mais fácil ver o que está a carregar aqui no arquivo de manifesto. Além disso, se um módulo não conseguir carregar aqui, irá ainda não ter foram carregados seu módulo real.<br /><br /> Além de outros módulos, também pode carregar ficheiros de script (. ps1) aqui. Estes ficheiros serão executadas no contexto do módulo de raiz. (Isto é equivalente ao ponto de origem do seu módulo de raiz, o script.)|
|FunctionsToExport<br /><br /> Tipo: Cadeia (de carateres)|'*'|Especifica as funções que o módulo exporta (carateres são permitidos carateres universais) para o estado de sessão do chamador. Por predefinição, todas as funções são exportadas. Pode utilizar esta chave para restringir as funções que são exportadas pelo módulo.<br /><br /> Estado da sessão do chamador pode ser a sessão global, estada ou, para aninhados módulos, o estado da sessão de outro módulo. Quando o encadeamento módulos aninhados, todas as funções que são exportadas por um módulo aninhado serão exportadas para o estado da sessão global, a menos que um módulo na cadeia restringe a função utilizando a chave de FunctionsToExport.<br /><br /> Se o manifesto também exporta aliases para as funções, esta chave pode remover as funções cujos aliases estão listados na chave do AliasesToExport, mas esta chave não é possível adicionar aliases de função à lista.|
|CmdletsToExport<br /><br /> Tipo: Cadeia (de carateres)|'*'|Especifica os cmdlets que o módulo exporta (carateres são permitidos carateres universais). Por predefinição, todos os cmdlets são exportados. Pode utilizar esta chave para restringir os cmdlets que são exportados pelo módulo.<br /><br /> Estado da sessão do chamador pode ser a sessão global, estada ou, para aninhados módulos, o estado da sessão de outro módulo. Quando são encadeamento módulos aninhados, todos os cmdlets que são exportados por um módulo aninhado serão, por fim, exportados para o estado da sessão global, a menos que um módulo na cadeia restringe o cmdlet utilizando a chave de CmdletsToExport.<br /><br /> Se o manifesto também exporta aliases para cmdlets, esta chave pode remover cmdlets cujos aliases estão listados na chave do AliasesToExport, mas esta chave não é possível adicionar aliases de cmdlet à lista.|
|VariablesToExport<br /><br /> Tipo: Cadeia (de carateres)|'*'|Especifica as variáveis que o módulo exporta (carateres são permitidos carateres universais) para o estado de sessão do chamador. Por predefinição, todas as variáveis são exportadas. Pode utilizar esta chave para restringir as variáveis que são exportadas pelo módulo.<br /><br /> Estado da sessão do chamador pode ser a sessão global, estada ou, para aninhados módulos, o estado da sessão de outro módulo. Quando são encadeamento módulos aninhados, todas as variáveis que são exportadas por um módulo aninhado serão exportadas para o estado da sessão global, a menos que um módulo na cadeia restringe a variável utilizando a chave de VariablesToExport.<br /><br /> Se o manifesto também exporta aliases para as variáveis, esta chave pode remover variáveis cujos aliases estão listados na chave do AliasesToExport, mas esta chave não é possível adicionar aliases variável à lista.|
|AliasesToExport<br /><br /> Tipo: Cadeia (de carateres)|'*'|Especifica os aliases que o módulo exporta (carateres são permitidos carateres universais) para o estado de sessão do chamador. Por predefinição, todos os aliases são exportados. Pode utilizar esta chave para restringir os aliases que são exportados pelo módulo.<br /><br /> Estado da sessão do chamador pode ser a sessão global, estada ou, para aninhados módulos, o estado da sessão de outro módulo. Quando são encadeamento módulos aninhados, todos os aliases que são exportados por um módulo aninhado serão, por fim, exportados para o estado da sessão global, a menos que um módulo na cadeia restringe o alias utilizando a chave de AliasesToExport.|
|ModuleList<br /><br /> Type: [string[]]|@()|Especifica a todos os módulos são empacotados com este módulo. Estes módulos podem ser introduzidos pelo nome (uma cadeia separada por vírgulas) ou como uma tabela de hash com chaves ModuleName e GUID. A tabela de hash também pode ter uma chave de ModuleVersion opcional. A chave de ModuleList foi concebida para funcionar como um inventário de módulo. Estes módulos não são processados automaticamente.|
|FileList<br /><br /> Type: [string[]]|@()|Lista de todos os arquivos empacotados com este módulo. Como com ModuleList, lista de ficheiros é para ajudá-lo como uma lista de inventário e caso contrário, não é processada.|
|PrivateData<br /><br /> Tipo: [object]|' '|Especifica a quaisquer dados privados que precisam de ser transmitidos para o módulo de raiz especificado pela chave RootModule/ModuleToProcess.|
|HelpInfoURI<br /><br /> Type: string|' '|URI de HelpInfo deste módulo.|
|DefaultCommandPrefix<br /><br /> Type: string|' '|Prefixo de padrão para comandos exportados a partir deste módulo. Substituir o prefixo de padrão usando `Import-Module` -prefixo.|

## <a name="sample-module-manifest"></a>Manifesto do módulo de exemplo

O manifesto de módulo de exemplo seguinte mostra as chaves e valores predefinidos num manifesto de módulo. Este exemplo foi criado utilizando o `New-ModuleManifest` cmdlet no Windows PowerShell 3.0. Ao criar vários módulos, pode utilizar este cmdlet para criar um modelo de manifesto que pode ser modificado para diferentes módulos.

```powershell
#
# Module manifest for module 'myManifest'
#
# Generated by: User01
#
# Generated on: 1/24/2012
#

@{

# Script module or binary module file associated with this manifest
#RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = 'd0a9150d-b6a4-4b17-a325-e3a24fed0aa9'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) 2012 User01. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the Windows PowerShell host required by this module
# PowerShellHostVersion = ''

# Minimum version of the .NET Framework required by this module
# DotNetFrameworkVersion = ''

# Minimum version of the common language runtime (CLR) required by this module
# CLRVersion = ''

# Processor architecture (None, X86, Amd64) required by this module
# ProcessorArchitecture = ''

# Modules that must be imported into the global environment prior to importing this module
# RequiredModules = @()

# Assemblies that must be loaded prior to importing this module
# RequiredAssemblies = @()

# Script files (.ps1) that are run in the caller's environment prior to importing this module
# ScriptsToProcess = @()

# Type files (.ps1xml) to be loaded when importing this module
# TypesToProcess = @()

# Format files (.ps1xml) to be loaded when importing this module
# FormatsToProcess = @()

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
# NestedModules = @()

# Functions to export from this module
FunctionsToExport = '*'

# Cmdlets to export from this module
CmdletsToExport = '*'

# Variables to export from this module
VariablesToExport = '*'

# Aliases to export from this module
AliasesToExport = '*'

# List of all modules packaged with this module
# ModuleList = @()

# List of all files packaged with this module
# FileList = @()

# Private data to pass to the module specified in RootModule/ModuleToProcess
# PrivateData = ''

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}

```

## <a name="see-also"></a>Veja Também

[Escrever um módulo do Windows PowerShell](./writing-a-windows-powershell-module.md)
