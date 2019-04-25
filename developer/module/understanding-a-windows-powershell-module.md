---
title: Noções básicas sobre um módulo do Windows PowerShell | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4e38235-9987-4347-afd2-0f7d1dc8f64a
caps.latest.revision: 19
ms.openlocfilehash: 77d328bc1cb8cb42d5a10f107a149c05ab270ce3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082112"
---
# <a name="understanding-a-windows-powershell-module"></a>Understanding a Windows PowerShell Module (Compreender um Módulo do Windows PowerShell)

R *módulo* é um conjunto de funcionalidades do Windows PowerShell relacionados, agrupados em conjunto como uma unidade conveniente (normalmente, salva num único diretório). Ao definir um conjunto de arquivos de script relacionados, assemblies e recursos relacionados como um módulo, pode referenciar, carregar, manter e compartilhar seu código muito mais fácil do que faria com outra forma.

A principal finalidade de um módulo é permitir que a modularização (ie, reutilização e abstração) de código do Windows PowerShell. Por exemplo, a forma mais básica de criação de um módulo é simplesmente guardar um script do Windows PowerShell como um ficheiro. psm1. Ao fazê-lo por isso, permite-lhe controlar (ie, marca pública ou privada) as funções e variáveis contidas no script. A guardar o script como um ficheiro. psm1 também permite-lhe controlar o âmbito de certas variáveis. Por fim, pode também utilizar os cmdlets, como [Install-Module](/powershell/module/PowershellGet/Install-Module) para organizar, instalar e utilizar o script como blocos de construção para soluções maiores.

## <a name="module-components-and-types"></a>Componentes de módulo e tipos

Um módulo é constituído por quatro componentes básicos:

1. Algum tipo de arquivo de código – normalmente, um script do PowerShell ou um assembly de cmdlet geridas.

2. Tudo o que o arquivo de código acima pode precisa, tais como assemblies adicionais, ajudam a ficheiros ou scripts.

3. Um arquivo de manifesto que descreve os ficheiros acima, bem como armazena metadada como autor e controlo de versões de informações....

4. Um diretório que contém todo o conteúdo acima e está localizado onde PowerShell pode razoavelmente encontrá-la.

   Tenha em atenção de que nenhum desses componentes, por si só, é realmente necessário. Por exemplo, um módulo tecnicamente pode ser apenas um script armazenado num ficheiro. psm1. Também pode ter um módulo que é nada além de um arquivo de manifesto, que é utilizado principalmente para fins de organização. Também pode escrever um script que cria dinamicamente um módulo e, como tal, na verdade, não precisa um diretório para armazenar qualquer item. As secções seguintes descrevem os tipos de módulos, que pode obter misturar e combinar as diferentes partes possíveis de um módulo em conjunto.

### <a name="script-modules"></a>Módulos de script

Como o nome indica, um *módulo de script* é um ficheiro (. psm1), que contém qualquer código válido do Windows PowerShell. Script de desenvolvedores e administradores podem utilizar este tipo de módulo para criar módulos cujos membros incluem funções, variáveis e muito mais. Em seu cerne, um módulo de script é simplesmente um script do Windows PowerShell com uma extensão diferente, que permite aos administradores utilizar funções de gestão, exportação e importação no mesmo.

Além disso, pode utilizar um ficheiro de manifesto para incluir outros recursos no seu módulo, como arquivos de dados, outros módulos dependentes ou tempo de execução scripts. Ficheiros de manifesto também são úteis para metadados, tais como informações de criação e o controle de versão de controlo.

Por fim, um módulo de script, como qualquer outro módulo que não é criado dinamicamente, precisa ser salvo numa pasta que PowerShell razoavelmente pode detetar. Normalmente, este é o caminho de módulo do PowerShell; mas se for necessário pode descrever explicitamente onde seu módulo está instalado. Para obter mais informações, consulte [como escrever um módulo de Script do PowerShell](./how-to-write-a-powershell-script-module.md).

### <a name="binary-modules"></a>Módulos binários

R *módulo binário* é um assembly do .NET Framework (. dll) que contém o código compilado, como C#. Os desenvolvedores de cmdlet podem utilizar este tipo de módulo para partilhar cmdlets, fornecedores e muito mais. (Snap-ins existentes também pode ser utilizados como módulos binários.) Em comparação com um módulo de script, um módulo binário permite-lhe criar cmdlets que são mais rápidos ou utilizar funcionalidades (como multithreading) que não são tão fáceis de código em scripts do Windows PowerShell.

Como com módulos de script, pode incluir um arquivo de manifesto para descrever os recursos adicionais que utiliza o seu módulo e para controlar metadados sobre seu módulo. Da mesma forma, provavelmente deve instalar seu módulo binário numa pasta em algum lugar no caminho do módulo do PowerShell. Para obter mais informações, consulte como [como escrever um módulo do PowerShell binário](./how-to-write-a-powershell-binary-module.md).

### <a name="manifest-modules"></a>Módulos de manifestos

R *manifesto de módulo* é um módulo que usa um arquivo de manifesto para descrever todos os respetivos componentes, mas não tem qualquer tipo de principal assembly ou script. (Formalmente, um módulo de manifesto deixa a `ModuleToProcess` ou `RootModule` elemento do manifesto vazio.) No entanto, ainda pode utilizar os outros recursos de um módulo, como a capacidade de carregar conjuntos de módulos dependentes ou executar automaticamente certos scripts de pré-processamento. Também pode utilizar um módulo de manifesto como uma forma conveniente de empacotar os recursos que utilizam outros módulos, como módulos aninhados, assemblies, tipos ou formatos. Para obter mais informações, consulte [como escrever um manifesto de módulo de PowerShell](./how-to-write-a-powershell-module-manifest.md).

### <a name="dynamic-modules"></a>Módulos dinâmicos

R *dynamického modulu* é um módulo não foi carregado ou salva num arquivo. Em vez disso, eles são criados dinamicamente por um script, utilizando o [New-Module](/powershell/module/Microsoft.PowerShell.Core/New-Module) cmdlet. Este tipo de módulo permite que um script para criar um módulo sob demanda e que não precisa de ser carregados ou guardada para armazenamento persistente. Por sua natureza, um módulo dinâmico se destina a ser curta duração e, portanto, não podem ser acedido pelo `Get-Module` cmdlet. Da mesma forma, normalmente, não têm de manifestos de módulo, e eles nem provavelmente precisam permanentes pastas para armazenar seus assemblies relacionados.

## <a name="module-manifests"></a>Manifestos de módulo

R *manifesto do módulo* é um ficheiro. psd1, que contém uma tabela de hash. As chaves e valores na tabela de hash, efetue os seguintes procedimentos:

- Descreva o conteúdo e os atributos do módulo.

- Defina os pré-requisitos.

- Determine como os componentes são processados.

  Manifestos não são necessários para um módulo. Módulos podem referenciar arquivos de script (. ps1), módulo arquivos (. psm1), ficheiros de manifesto (. psd1), formatação de script e escreva ficheiros (.ps1xml), assemblies do cmdlet e do fornecedor (. dll), arquivos de recursos, arquivos de ajuda, arquivos de localização ou qualquer outro tipo de ficheiro ou recurso que é fornecido como parte do módulo. Para obter um script internacionalizado, da pasta do módulo contém também um conjunto de arquivos de catálogo de mensagem. Se adicionar um arquivo de manifesto para a pasta de módulo, pode referenciar os vários arquivos como uma única unidade referenciando o manifesto.

  O manifesto do próprio descreve as seguintes categorias de informações:

- Metadados sobre o módulo, tal como o número de versão do módulo, o autor e a descrição.

- Pré-requisitos necessários para importar o módulo, como a versão do Windows PowerShell, a versão de runtime (CLR) de linguagem comum e os módulos necessários.

- Processamento de diretivas, como os scripts, formatos e tipos para processar.

- Restrições sobre os membros do módulo para exportar, como os aliases, funções, variáveis e cmdlets para exportar.

  Para obter mais informações, consulte [como escrever um manifesto de módulo de PowerShell](./how-to-write-a-powershell-module-manifest.md).

## <a name="storing-and-installing-a-module"></a>Armazenar e instalar um módulo

Depois de criar um script, o módulo de manifesto ou binário, pode guardar o trabalho num local que outras pessoas podem aceder ao mesmo. Por exemplo, seu módulo pode ser armazenado na pasta de sistema em que o Windows PowerShell está instalado, ou podem ser armazenado numa pasta de usuário.

Em termos gerais, pode determinar onde deve instalar o módulo utilizando um dos caminhos armazenados no `$ENV:PSModulePath` variável. Usando um desses meios de caminhos que PowerShell automaticamente pode localizar e carregar seu módulo, quando um usuário faz uma chamada a ele em seu código. Se armazenar seu módulo em algum lugar, pode deixar PowerShell saber ao transmitir a localização do seu módulo como um parâmetro, quando chama explicitamente `Install-Module`.

Seja como for, o caminho da pasta é referido como o *base* do módulo (ModuleBase) e o nome do script, ficheiro binário ou manifesto de módulo deve ser o mesmo que o nome da pasta do módulo, com as seguintes exceções:

- Módulos dinâmicos que são criados pela `New-Module` cmdlet pode ser nomeado usando o `Name` parâmetro do cmdlet.

- Módulos importados a partir de objetos de assembly pela  **`Import-Module` -assemblagem** comando são nomeados, de acordo com a seguinte sintaxe: `"dynamic_code_module_" + assembly.GetName()`.

  Para obter mais informações, consulte [instalar um módulo do PowerShell](./installing-a-powershell-module.md) e [modificar o caminho de instalação PSModulePath](./modifying-the-psmodulepath-installation-path.md).

## <a name="module-cmdlets-and-variables"></a>Cmdlets do módulo e as variáveis

Os seguintes cmdlets e variáveis são fornecidas pelo Windows PowerShell para a criação e gestão de módulos.

[Novo módulo](/powershell/module/Microsoft.PowerShell.Core/New-Module) cmdlet este cmdlet cria um novo módulo dinâmico que existe apenas na memória. O módulo é criado a partir de um bloco de scripts e seus membros exportados, tais como suas funções e variáveis, estão imediatamente disponíveis na sessão e permanecem disponíveis até a sessão é fechada.

[Novo ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet este cmdlet cria um novo ficheiro de manifesto (. psd1) do módulo, preenche seus valores e salva o arquivo de manifesto para o caminho especificado. Este cmdlet também pode ser utilizado para criar um modelo de manifesto de módulo que pode ser preenchido manualmente.

[Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet este cmdlet adiciona um ou mais módulos para a sessão atual.

[Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet este cmdlet obtém informação sobre os módulos que tenham sido ou que podem ser importados para a sessão atual.

[Exportação ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) cmdlet este cmdlet Especifica os membros de módulo (por exemplo, cmdlets, funções, variáveis e aliases) que são exportados a partir de um ficheiro de script do módulo (. psm1) ou a partir de um módulo dinâmico criado utilizando o `New-Module` cmdlet.

[Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) cmdlet este cmdlet Remove módulos da sessão atual.

[Teste ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest) cmdlet este cmdlet verifica que um manifesto de módulo descreve com precisão os componentes de um módulo ao verificar que os ficheiros que estão listados no ficheiro de manifesto de módulo (. psd1), na verdade, existem em caminhos especificados.

$PSScriptRoot esta variável contiver o diretório a partir do qual o módulo de script está a ser executado. Permite que scripts para utilizar o caminho do módulo para aceder a outros recursos.

$env: PSModulePath esta variável de ambiente contém uma lista de diretórios na qual do Windows PowerShell módulos são armazenados. Windows PowerShell utiliza o valor da variável quando importar os módulos automaticamente e tópicos de ajuda para módulos de atualização.

## <a name="see-also"></a>Veja Também

[Escrever um módulo do Windows PowerShell](./writing-a-windows-powershell-module.md)
