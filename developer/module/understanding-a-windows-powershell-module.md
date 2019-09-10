---
title: Compreendendo um módulo do Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4e38235-9987-4347-afd2-0f7d1dc8f64a
caps.latest.revision: 19
ms.openlocfilehash: b42ba6b2bf42a74213eb78f2db22e16de7e90583
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848060"
---
# <a name="understanding-a-windows-powershell-module"></a>Understanding a Windows PowerShell Module (Compreender um Módulo do Windows PowerShell)

Um *módulo* é um conjunto de funcionalidades do Windows PowerShell relacionadas, agrupadas em conjunto como uma unidade conveniente (geralmente salva em um único diretório). Ao definir um conjunto de arquivos de script relacionados, assemblies e recursos relacionados como um módulo, você pode fazer referência, carregar, persistir e compartilhar seu código de forma muito mais fácil do que seria.

A principal finalidade de um módulo é permitir a modularidade (IE, reutilização e abstração) do código do Windows PowerShell. Por exemplo, a maneira mais básica de criar um módulo é simplesmente salvar um script do Windows PowerShell como um arquivo. psm1. Isso permite que você controle (ou seja, torne público ou privado) as funções e variáveis contidas no script. Salvar o script como um arquivo. psm1 também permite que você controle o escopo de determinadas variáveis. Por fim, você também pode usar cmdlets como [install-Module](/powershell/module/PowershellGet/Install-Module) para organizar, instalar e usar seu script como blocos de construção para soluções maiores.

## <a name="module-components-and-types"></a>Componentes e tipos de módulo

Um módulo é composto de quatro componentes básicos:

1. Algum tipo de arquivo de código – geralmente um script do PowerShell ou um assembly de cmdlet gerenciado.

2. Qualquer outra coisa que o arquivo de código acima possa precisar, como assemblies adicionais, arquivos de ajuda ou scripts.

3. Um arquivo de manifesto que descreve os arquivos acima, bem como armazena metadados, como informações de criação e controle de versão.

4. Um diretório que contém todo o conteúdo acima e está localizado onde o PowerShell pode encontrá-lo razoavelmente.

   Observe que nenhum desses componentes, por si só, são realmente necessários. Por exemplo, um módulo tecnicamente pode ser apenas um script armazenado em um arquivo. psm1. Você também pode ter um módulo que não seja nada além de um arquivo de manifesto, que é usado principalmente para fins organizacionais. Você também pode escrever um script que cria um módulo dinamicamente e, como tal, não precisa realmente de um diretório para armazenar nada. As seções a seguir descrevem os tipos de módulos que você pode obter misturando e combinando as diferentes partes possíveis de um módulo juntos.

### <a name="script-modules"></a>Módulos de script

Como o nome indica, um *módulo de script* é um arquivo (. psm1) que contém qualquer código válido do Windows PowerShell. Os desenvolvedores e administradores de script podem usar esse tipo de módulo para criar módulos cujos membros incluem funções, variáveis e muito mais. No coração, um módulo de script é simplesmente um script do Windows PowerShell com uma extensão diferente, que permite aos administradores usarem funções de importação, exportação e gerenciamento nele.

Além disso, você pode usar um arquivo de manifesto para incluir outros recursos em seu módulo, como arquivos de dados, outros módulos dependentes ou scripts de tempo de execução. Os arquivos de manifesto também são úteis para controlar metadados, como informações de criação e controle de versão.

Por fim, um módulo de script, como qualquer outro módulo que não é criado dinamicamente, precisa ser salvo em uma pasta que o PowerShell pode descobrir razoavelmente. Normalmente, isso está no caminho do módulo do PowerShell; Mas, se necessário, você pode descrever explicitamente onde o módulo está instalado. Para obter mais informações, consulte [como escrever um módulo de script do PowerShell](./how-to-write-a-powershell-script-module.md).

### <a name="binary-modules"></a>Módulos binários

Um *módulo binário* é um assembly .NET Framework (. dll) que contém código compilado, como C#. Os desenvolvedores de cmdlets podem usar esse tipo de módulo para compartilhar cmdlets, provedores e muito mais. (Os snap-ins existentes também podem ser usados como módulos binários.) Em comparação com um módulo de script, um módulo binário permite que você crie cmdlets que são mais rápidos ou usam recursos (como multithreading) que não são tão fáceis de codificar em scripts do Windows PowerShell.

Assim como acontece com os módulos de script, você pode incluir um arquivo de manifesto para descrever os recursos adicionais usados pelo seu módulo e controlar os metadados sobre o módulo. Da mesma forma, você provavelmente deve instalar o módulo binário em uma pasta em algum lugar ao longo do caminho do módulo do PowerShell. Para obter mais informações, consulte como [escrever um módulo binário do PowerShell](./how-to-write-a-powershell-binary-module.md).

### <a name="manifest-modules"></a>Módulos de manifesto

Um *módulo de manifesto* é um módulo que usa um arquivo de manifesto para descrever todos os seus componentes, mas não tem nenhum tipo de assembly ou script de núcleo. (Formalmente, um módulo de manifesto deixa `ModuleToProcess` o `RootModule` elemento ou do manifesto vazio.) No entanto, você ainda pode usar os outros recursos de um módulo, como a capacidade de carregar assemblies dependentes ou executar automaticamente determinados scripts de pré-processamento. Você também pode usar um módulo de manifesto como uma maneira conveniente de empacotar recursos que outros módulos usarão, como módulos aninhados, assemblies, tipos ou formatos. Para obter mais informações, consulte [como escrever um manifesto de módulo do PowerShell](./how-to-write-a-powershell-module-manifest.md).

### <a name="dynamic-modules"></a>Módulos dinâmicos

Um *módulo dinâmico* é um módulo que não é carregado de um arquivo ou salvo nele. Em vez disso, eles são criados dinamicamente por um script, usando o cmdlet [New-Module](/powershell/module/Microsoft.PowerShell.Core/New-Module) . Esse tipo de módulo permite que um script crie um módulo sob demanda que não precise ser carregado nem salvo no armazenamento persistente. Por sua natureza, um módulo dinâmico deve ser de curta duração e, portanto, não pode ser acessado `Get-Module` pelo cmdlet. Da mesma forma, eles geralmente não precisam de manifestos de módulo, nem eles provavelmente precisam de pastas permanentes para armazenar seus assemblies relacionados.

## <a name="module-manifests"></a>Manifestos de módulo

Um *manifesto de módulo* é um arquivo. psd1 que contém uma tabela de hash. As chaves e os valores na tabela de hash fazem o seguinte:

- Descreva o conteúdo e os atributos do módulo.

- Defina os pré-requisitos.

- Determine como os componentes são processados.

  Os manifestos não são necessários para um módulo. Os módulos podem referenciar arquivos de script (. ps1), arquivos de módulo de script (. psm1), arquivos de manifesto (. psd1), arquivos de formatação e tipo (. ps1xml), assemblies de cmdlet e provedor (. dll), arquivos de recursos, arquivos de ajuda, arquivos de localização ou qualquer outro tipo de arquivo ou recurso que é agrupado como parte do módulo. Para um script internacionalizado, a pasta de módulo também contém um conjunto de arquivos de catálogo de mensagens. Se você adicionar um arquivo de manifesto à pasta do módulo, poderá fazer referência a vários arquivos como uma única unidade referenciando o manifesto.

  O próprio manifesto descreve as seguintes categorias de informações:

- Metadados sobre o módulo, como o número de versão do módulo, o autor e a descrição.

- Os pré-requisitos necessários para importar o módulo, como a versão do Windows PowerShell, a versão Common Language Runtime (CLR) e os módulos necessários.

- Diretivas de processamento, como os scripts, formatos e tipos a serem processados.

- Restrições sobre os membros do módulo a serem exportados, como aliases, funções, variáveis e cmdlets a serem exportados.

  Para obter mais informações, consulte [como escrever um manifesto de módulo do PowerShell](./how-to-write-a-powershell-module-manifest.md).

## <a name="storing-and-installing-a-module"></a>Armazenando e instalando um módulo

Depois de criar um módulo script, binário ou manifesto, você pode salvar seu trabalho em um local que outras pessoas possam acessá-lo. Por exemplo, o módulo pode ser armazenado na pasta do sistema em que o Windows PowerShell está instalado ou pode ser armazenado em uma pasta de usuário.

Em termos gerais, você pode determinar onde você deve instalar o módulo usando um dos caminhos armazenados na `$ENV:PSModulePath` variável. Usar um desses caminhos significa que o PowerShell pode localizar e carregar automaticamente seu módulo quando um usuário fizer uma chamada para ele em seu código. Se você armazenar seu módulo em outro lugar, poderá explicitamente permitir que o PowerShell saiba passando o local do seu módulo como um parâmetro quando você chamar `Install-Module`.

Independentemente, o caminho da pasta é chamado de *base* do módulo (ModuleBase), e o nome do arquivo de módulo script, binário ou manifesto deve ser o mesmo que o nome da pasta do módulo, com as seguintes exceções:

- Módulos dinâmicos criados pelo `New-Module` cmdlet podem ser nomeados usando o `Name` parâmetro do cmdlet.

- Os `"dynamic_code_module_" + assembly.GetName()` **`Import-Module`** módulos importados de objetos de assembly pelo comando-assembly são nomeados de acordo com a seguinte sintaxe:.

  Para obter mais informações, consulte [instalando um módulo do PowerShell](./installing-a-powershell-module.md) e [modificando o caminho de instalação do PSModulePath](./modifying-the-psmodulepath-installation-path.md).

## <a name="module-cmdlets-and-variables"></a>Cmdlets e variáveis de módulo

Os cmdlets e variáveis a seguir são fornecidos pelo Windows PowerShell para a criação e o gerenciamento de módulos.

Cmdlet [New-Module](/powershell/module/Microsoft.PowerShell.Core/New-Module) esse cmdlet cria um novo módulo dinâmico que existe apenas na memória. O módulo é criado a partir de um bloco de script, e seus membros exportados, como suas funções e variáveis, estão imediatamente disponíveis na sessão e permanecem disponíveis até que a sessão seja fechada.

Cmdlet [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) esse cmdlet cria um novo arquivo de manifesto de módulo (. psd1), popula seus valores e salva o arquivo de manifesto no caminho especificado. Esse cmdlet também pode ser usado para criar um modelo de manifesto de módulo que pode ser preenchido manualmente.

Cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) esse cmdlet adiciona um ou mais módulos à sessão atual.

Cmdlet [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) este cmdlet recupera informações sobre os módulos que foram ou que podem ser importados para a sessão atual.

Cmdlet [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) este cmdlet especifica os membros do módulo (como cmdlets, funções, variáveis e aliases) que são exportados de um arquivo de módulo de script (. psm1) ou de um módulo dinâmico criado usando `New-Module` o cmdlet.

Cmdlet [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) este cmdlet Remove módulos da sessão atual.

Cmdlet [Test-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest) esse cmdlet verifica se um manifesto de módulo descreve precisamente os componentes de um módulo verificando se os arquivos listados no arquivo de manifesto de módulo (. psd1) realmente existem nos caminhos especificados.

$PSScriptRoot essa variável contém o diretório do qual o módulo de script está sendo executado. Ele permite que os scripts usem o caminho do módulo para acessar outros recursos.

$env:P SModulePath essa variável de ambiente contém uma lista dos diretórios nos quais os módulos do Windows PowerShell estão armazenados. O Windows PowerShell usa o valor dessa variável ao importar módulos automaticamente e atualizar tópicos de ajuda para módulos.

## <a name="see-also"></a>Veja Também

[Escrevendo um módulo do Windows PowerShell](./writing-a-windows-powershell-module.md)
