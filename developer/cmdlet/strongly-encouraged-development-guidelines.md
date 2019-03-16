---
title: Altamente favorável diretrizes de desenvolvimento | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d68a8f3-fba0-44c5-97b9-9fc191d269a5
caps.latest.revision: 13
ms.openlocfilehash: 0906d0d37c66b8c1538a0b2e9e0f1ff2fba12ac0
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057727"
---
# <a name="strongly-encouraged-development-guidelines"></a>Strongly Encouraged Development Guidelines (Diretrizes de Desenvolvimento Altamente Recomendadas)

Esta secção descreve as diretrizes que deve seguir quando escreve seus cmdlets. Eles são separados em diretrizes para a criação de cmdlets e diretrizes para escrever seu código de cmdlet. Pode achar que essas diretrizes não são aplicáveis para cada cenário. Contudo, se aplicam-se e não seguir estas diretrizes, os utilizadores podem ter uma experiência ruim quando utilizarem seus cmdlets.

## <a name="design-guidelines"></a>Diretrizes de design

- [Utilizar um substantivo específico para um nome de Cmdlet (SD01)](./strongly-encouraged-development-guidelines.md#use-a-specific-noun-for-a-cmdlet-name-sd01)

- [Utilização em Pascal Case para nomes de Cmdlet (SD02)](./strongly-encouraged-development-guidelines.md#use-pascal-case-for-cmdlet-names-sd02)

- [Diretrizes de Design de parâmetro (SD03)](./strongly-encouraged-development-guidelines.md#parameter-design-guidelines-sd03)

- [Fornecer comentários para o usuário (SD04)](./strongly-encouraged-development-guidelines.md#provide-feedback-to-the-user-sd04)

- [Crie um ficheiro de ajuda do Cmdlet (SD05)](./strongly-encouraged-development-guidelines.md#create-a-cmdlet-help-file-sd05)

## <a name="code-guidelines"></a>Diretrizes de código

- [Parâmetros de codificação (SC01)](./strongly-encouraged-development-guidelines.md#coding-parameters-sc01)

- [Suporte a entrada de Pipeline bem definido (chaves SC02)](./strongly-encouraged-development-guidelines.md#support-well-defined-pipeline-input-sc02)

- [Escrever os registos de únicos para o Pipeline (SC03)](./strongly-encouraged-development-guidelines.md#write-single-records-to-the-pipeline-sc03)

- [Tornar os Cmdlets maiúsculas de minúsculas e preservação caso (SC04)](./strongly-encouraged-development-guidelines.md#make-cmdlets-case-insensitive-and-case-preserving-sc04)

## <a name="design-guidelines"></a>Diretrizes de design

Devem ser seguidas as seguintes diretrizes durante a criação de cmdlets para garantir uma experiência de usuário consistente entre o uso de seus cmdlets e os outros cmdlets. Quando encontrar uma diretriz de Design que se aplica à sua situação, certifique-se de que examinar as diretrizes de código para obter diretrizes semelhantes.

### <a name="use-a-specific-noun-for-a-cmdlet-name-sd01"></a>Utilizar um substantivo específico para um nome de Cmdlet (SD01)

Substantivos usados na nomeação do cmdlet tem de ser muito específicos para que o utilizador pode detetar os seus cmdlets. Prefixo substantivos genéricos, como "server", com uma versão abreviada do nome do produto. Por exemplo, se um substantivo refere-se a um servidor que está a executar uma instância do Microsoft SQL Server, use um substantivo, como "SQLServer". A combinação de substantivos específicos e a pequena lista de verbos aprovados permitir ao utilizador detetar e prever sua funcionalidade, evitando duplicação entre nomes de cmdlet rapidamente.

Para melhorar a experiência do usuário, o substantivo que escolher para um nome de cmdlet deve ser único. Por exemplo, utilize o nome `Get-Process` em vez de **Get-processos**. É melhor seguir esta regra para todos os nomes de cmdlet, mesmo quando um cmdlet é provável que agir em mais de um item.

### <a name="use-pascal-case-for-cmdlet-names-sd02"></a>Utilização em Pascal Case para nomes de Cmdlet (SD02)

Utilize em Pascal case para nomes de parâmetro. Em outras palavras, tire partido da primeira letra de verbo e todos os termos utilizados no substantivo. Por exemplo, "`Clear-ItemProperty`".

### <a name="parameter-design-guidelines-sd03"></a>Diretrizes de Design de parâmetro (SD03)

Precisa de um cmdlet parâmetros que recebem os dados em que ele deve operar e os parâmetros que indicar informações que são utilizadas para determinar as características da operação. Por exemplo, um cmdlet pode ter uma `Name` parâmetro que recebe dados a partir do pipeline e o cmdlet pode ter um `Force` parâmetro para indicar que o cmdlet pode ser forçado para efetuar a operação. Não existe nenhum limite para o número de parâmetros que pode definir um cmdlet.

#### <a name="use-standard-parameter-names"></a>Utilize os nomes de parâmetros padrão

O cmdlet deve utilizar nomes de parâmetro padrão para que o utilizador possa determinar rapidamente o que significa que um parâmetro específico. Se um nome mais específico é necessário, utilize um nome de parâmetro padrão e, em seguida, especifique um nome mais específico como um alias. Por exemplo, o `Get-Service` cmdlet tem um parâmetro que tem um nome genérico (`Name`) e um alias mais específico (`ServiceName`). Os dois termos podem ser utilizados para especificar o parâmetro.

Para obter mais informações sobre os nomes de parâmetros e os tipos de dados, consulte [nome do parâmetro de Cmdlet e diretrizes de funcionalidade](./standard-cmdlet-parameter-names-and-types.md).

#### <a name="use-singular-parameter-names"></a>Utilizar nomes de parâmetro Singular

Evite utilizar nomes plurais para os parâmetros cujo valor é um único elemento. Isso inclui parâmetros que tomar as matrizes ou lista porque o usuário pode fornecer uma matriz ou lista com apenas um elemento.

Os nomes dos parâmetros plural devem ser usados apenas nos casos em que o valor do parâmetro é sempre um valor de elemento múltiplo. Nestes casos, o cmdlet deve verificar que vários elementos são fornecidos e o cmdlet deve apresentar um aviso ao utilizador se vários elementos não são fornecidos.

#### <a name="use-pascal-case-for-parameter-names"></a>Utilização em Pascal Case para nomes de parâmetro

Utilize em Pascal case para nomes de parâmetro. Em outras palavras, em maiúsculas a primeira letra de cada palavra no nome do parâmetro, incluindo a primeira letra do nome. Por exemplo, o nome do parâmetro `ErrorAction` utiliza a capitalização correta. Os seguintes nomes de parâmetro utilizam capitalização incorreta:

- `errorAction`

- `erroraction`

#### <a name="parameters-that-take-a-list-of-options"></a>Parâmetros que levam uma lista de opções

Existem duas formas de criar um parâmetro cujo valor pode ser selecionado a partir de um conjunto de opções.

- Definir um tipo de enumeração (ou usar um tipo de enumeração existente) Especifica que os valores válidos. Em seguida, utilize o tipo de enumeração para criar um parâmetro desse tipo.

- Adicionar a **ValidateSet** atributo para a declaração de parâmetro. Para obter mais informações sobre este atributo, consulte [declaração de atributo ValidateSet](./validateset-attribute-declaration.md).

#### <a name="use-standard-types-for-parameters"></a>Tipos de padrão de utilização para os parâmetros

Para garantir a consistência com outros cmdlets, utilize tipos padrão para os parâmetros em que sempre é possível. Para obter mais informações sobre os tipos que deve ser utilizado para o parâmetro diferente, consulte [nomes de parâmetro de Cmdlet padrão e tipos](./standard-cmdlet-parameter-names-and-types.md). Este tópico fornece ligações para vários tópicos que descrevem os nomes e tipos do .NET Framework para grupos de parâmetros padrão, como os parâmetros"atividades".

#### <a name="use-strongly-typed-net-framework-types"></a>Usar tipos de Framework .NET rigidez de tipos

Parâmetros devem ser definidos como tipos do .NET Framework para fornecer a melhor validação de parâmetro. Por exemplo, os parâmetros que estão restritas a um valor de um conjunto de valores devem ser definidos como um tipo de enumeração. Para suportar um valor de identificador de recurso uniforme (URI), defina o parâmetro como uma [System](/dotnet/api/System.Uri) tipo. Evite os parâmetros de cadeia básica para propriedades de tudo, mas textos livres.

#### <a name="use-consistent-parameter-types"></a>Usar tipos de parâmetro consistente

Quando o mesmo parâmetro é utilizado por vários cmdlets, utilize sempre o mesmo tipo de parâmetro.  Por exemplo, se o `Process` parâmetro é um [System.Int16](/dotnet/api/System.Int16) tipo para um cmdlet, não faça o `Process` parâmetro para outro cmdlet um [System.Uint16](/dotnet/api/System.UInt16) tipo.

#### <a name="parameters-that-take-true-and-false"></a>Parâmetros que efetuar True e False

Se o parâmetro demora `true` e `false`, defina o parâmetro como tipo [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter). Um parâmetro de mudança é tratado como `true` quando é especificado com um comando. Se o parâmetro não estiver incluído num comando, o Windows PowerShell considera o valor do parâmetro como ser `false`. Não defina parâmetros booleanos.

Se o parâmetro tem de diferenciar os 3 valores: $true, $false e "não especificado,", em seguida, definir um parâmetro do tipo Nullable\<bool >.  A necessidade de um 3rd, valor de "não especificado" normalmente ocorre quando o cmdlet pode modificar uma propriedade booleana de um objeto. Neste caso, "não especificado" significa que não alterar o valor atual da propriedade.

#### <a name="support-arrays-for-parameters"></a>Matrizes de suporte para parâmetros

Com freqüência, os utilizadores tem de efetuar a mesma operação em relação a vários argumentos. Para estes utilizadores, um cmdlet deve aceitar uma matriz como parâmetro de entrada para que um usuário pode passar os argumentos para o parâmetro como uma variável do Windows PowerShell. Por exemplo, o [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet utiliza uma matriz de cadeias de caracteres que identificam os nomes dos processos para obter.

#### <a name="support-the-passthru-parameter"></a>Suporta o parâmetro PassThru

Por padrão, muitos cmdlets que modificar o sistema, como o [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet, atuar como "sinks" para objetos e não devolveu um resultado. Estes cmdlet deve implementar o `PassThru` parâmetro para forçar o cmdlet para retornar um objeto. Quando o `PassThru` parâmetro for especificado, o cmdlet retorna um objeto ao utilizar uma chamada para o [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) método. Por exemplo, o seguinte comando para o processo de cálculo e transmite o processo resultante para o pipeline.

```powershell
Stop-Process calc -passthru
```

Na maioria dos casos, deve dar suporte a cmdlets New, definição e adicionar um `PassThru` parâmetro.

#### <a name="support-parameter-sets"></a>Conjuntos de parâmetros de suporte

Destina-se um cmdlet para realizar uma única finalidade. No entanto, com freqüência é mais do que uma forma de descrever a operação ou o destino da operação. Por exemplo, um processo poderá ser identificado pelo respetivo nome, pelo respetivo identificador ou por um objeto de processo. O cmdlet deve dar suporte a todas as representações razoáveis seus destinos. Normalmente, o cmdlet satisfaça este requisito, especificando os conjuntos de parâmetros (referidos como conjuntos de parâmetros) que funcionam em conjunto. Um único parâmetro pode pertencer a qualquer número de conjuntos de parâmetros. Para obter mais informações sobre conjuntos de parâmetros, consulte [define o parâmetro de Cmdlet](./cmdlet-parameter-sets.md).

Quando especificar conjuntos de parâmetros, defina apenas um parâmetro no conjunto para ValueFromPipeline. Para obter mais informações sobre como declarar o **parâmetro** de atributos, consulte [ParameterAttribute declaração](./parameter-attribute-declaration.md).

Quando são utilizados os conjuntos de parâmetros, o conjunto de parâmetros padrão é definido pela **Cmdlet** atributo. O conjunto de parâmetros de predefinição deve incluir os parâmetros mais probabilidades de ser usado numa sessão interativa do Windows PowerShell. Para obter mais informações sobre como declarar o **Cmdlet** de atributos, consulte [declaração CmdletAttribute](./cmdlet-attribute-declaration.md).

### <a name="provide-feedback-to-the-user-sd04"></a>Fornecer comentários para o usuário (SD04)

Utilize as diretrizes nesta secção para fornecer comentários ao utilizador. Estes comentários permitem ao utilizador para ter em consideração o que está ocorrendo no sistema de e para tomar decisões de administrativas melhor.

O tempo de execução do Windows PowerShell permite que um usuário especifique como lidar com a saída de cada chamada para o `Write` método, definindo uma variável de preferência. O utilizador pode definir várias variáveis de preferência, incluindo uma variável que determina se o sistema deve apresentar informações e uma variável que determina se o sistema deve consultar o utilizador antes de efetuar qualquer ação.

#### <a name="support-the-writewarning-writeverbose-and-writedebug-methods"></a>Suporte a WriteWarning, WriteVerbose e métodos de WriteDebug

Um cmdlet deve chamar o [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) método quando o cmdlet está prestes a realizar uma operação que poderá ter um resultado de não-intencionais. Por exemplo, um cmdlet deve invocar este método se o cmdlet está prestes a substituir um ficheiro só de leitura.

Um cmdlet deve chamar o [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) método quando o utilizador necessita de alguns detalhes sobre o que está fazendo o cmdlet. Por exemplo, um cmdlet deve chamar estas informações se o autor de cmdlet, parece que há cenários que poderão necessitar de mais informações sobre o que está fazendo o cmdlet.

O cmdlet deve chamar o [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) método quando um engenheiro de suporte programador ou produto tem de compreender o que corrompeu a operação de cmdlet. Não é necessário para o cmdlet para chamar o [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) método no mesmo código que chama o [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) método uma vez que o `Debug` parâmetro apresenta os dois conjuntos de informações.

#### <a name="support-writeprogress-for-operations-that-take-a-long-time"></a>WriteProgress de suporte para operações que demoram muito tempo

Operações de cmdlet que demoram muito tempo a concluir e que não pode ser executado em segundo plano deve suportar progresso relatórios por meio de chamadas periódicas para o [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) método.

#### <a name="use-the-host-interfaces"></a>Usar as Interfaces de anfitrião

Ocasionalmente, um cmdlet têm de comunicar diretamente com o utilizador em vez de ao utilizar as várias escrever ou devem métodos suportados pelos [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe. Neste caso, o cmdlet deve derivar do [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) de classe e utilizar os [System.Management.Automation.PSCmdlet.Host*](/dotnet/api/System.Management.Automation.PSCmdlet.Host) propriedade. Esta propriedade suporta diferentes níveis de tipo de comunicação, incluindo os tipos de PromptForChoice, linha de comandos e WriteLine/ReadLine. Nível o que é mais específico, ele também fornece formas de ler e escrever chaves individuais e lidar com os buffers.

A menos que um cmdlet foi especificamente desenvolvido para gerar uma interface gráfica (GUI), ele não deve ignorar o anfitrião utilizando o [System.Management.Automation.PSCmdlet.Host*](/dotnet/api/System.Management.Automation.PSCmdlet.Host) propriedade. Um exemplo de um cmdlet que foi concebido para gerar uma GUI é o [Out-GridView](/powershell/module/Microsoft.PowerShell.Utility/Out-GridView) cmdlet.

> [!NOTE]
> Cmdlets não deve utilizar o [System. Console](/dotnet/api/System.Console) API.

### <a name="create-a-cmdlet-help-file-sd05"></a>Crie um ficheiro de ajuda do Cmdlet (SD05)

Para cada assembly de cmdlet, crie um ficheiro de Help.xml que contém informações sobre o cmdlet. Estas informações incluem uma descrição do cmdlet, descrições dos parâmetros do cmdlet, exemplos de utilização do cmdlet e muito mais.

## <a name="code-guidelines"></a>Diretrizes de código

Devem ser seguidas as seguintes diretrizes durante a codificação de cmdlets para garantir uma experiência de usuário consistente entre o uso de seus cmdlets e os outros cmdlets. Quando encontrar uma diretriz de código que se aplica à sua situação, certifique-se de que examinar as diretrizes de Design para obter diretrizes semelhantes.

### <a name="coding-parameters-sc01"></a>Parâmetros de codificação (SC01)

Definir um parâmetro ao declarar uma propriedade pública da classe cmdlet que está decorada com o **parâmetro** atributo. Parâmetros não têm de ser membros estáticos da classe derivada do .NET Framework para o cmdlet. Para obter mais informações sobre como declarar o **parâmetro** de atributos, consulte [declaração de atributo de parâmetro](./parameter-attribute-declaration.md).

#### <a name="support-windows-powershell-paths"></a>Suporte a caminhos do Windows PowerShell

O caminho do Windows PowerShell é o mecanismo para normalizar o acesso aos espaços de nomes. Quando atribui um caminho do Windows PowerShell para um parâmetro no cmdlet, o usuário pode definir um personalizado "unidade", que atua como um atalho para um caminho específico. Quando um utilizador designa uma unidade de tal, dados armazenados, tais como os dados no registo, podem servir-se de uma forma consistente.

Se seu cmdlet permite que o usuário especificar um ficheiro ou uma origem de dados, ele deve definir um parâmetro do tipo [System. String](/dotnet/api/System.String). Se for suportada mais de uma unidade, o tipo deve ser uma matriz. O nome do parâmetro deve ser `Path`, com um alias de `PSPath`. Além disso, o `Path` parâmetro deve suporta carateres universais. Se o suporte para carateres universais não é necessária, definir um `LiteralPath` parâmetro.

Se os dados que o cmdlet lê ou escreve tem de ser um arquivo, o cmdlet deve aceitar entrada de caminho do Windows PowerShell e o cmdlet deve utilizar o [System.Management.Automation.Sessionstate.Path](/dotnet/api/System.Management.Automation.SessionState.Path) propriedade traduzir o Windows Caminhos de PowerShell em caminhos que reconhece o sistema de ficheiros. Os mecanismos específicos incluem os seguintes métodos:

- [System.Management.Automation.PSCmdlet.GetResolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PSCmdlet.GetResolvedProviderPathFromPSPath)

- [System.Management.Automation.PSCmdlet.GetUnresolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PSCmdlet.GetUnresolvedProviderPathFromPSPath)

- [System.Management.Automation.PathIntrinsics.GetResolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetResolvedProviderPathFromPSPath)

- [System.Management.Automation.PathIntrinsics.GetUnresolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetUnresolvedProviderPathFromPSPath)

Se os dados que o cmdlet lê ou escreve são apenas um conjunto de cadeias de caracteres em vez de um arquivo, o cmdlet deve utilizar as informações de conteúdo do fornecedor (`Content` membro) para ler e escrever. Esta informação é obtida a partir da [System.Management.Automation.Provider.CmdletProvider.InvokeProvider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.InvokeProvider) propriedade. Estes mecanismos permitem que os outros arquivos de dados participar na leitura e gravação de dados.

#### <a name="support-wildcard-characters"></a>Suporta carateres universais

Um cmdlet deve suportar, se possível, carateres universais. Suporte para carateres universais ocorre em muitos locais num cmdlet (especialmente quando um parâmetro usa uma cadeia de caracteres para identificar um objeto de um conjunto de objetos). Por exemplo, o exemplo **Stop-Proc** cmdlet a partir do [StopProc Tutorial](./stopproc-tutorial.md) define um `Name` parâmetro para manipular cadeias de caracteres que representam nomes de processo. Este parâmetro suporta carateres universais para que o utilizador possa especificar facilmente os processos para parar.

Quando suporte para carateres universais carateres está disponível, uma operação do cmdlet normalmente produz uma matriz. Ocasionalmente, ele não faz sentido para suportar uma matriz, uma vez que o usuário poderia utilizar apenas um único item por vez. Por exemplo, o [Set-Location](/powershell/module/Microsoft.PowerShell.Management/Set-Location) cmdlet não precisa de uma matriz de suporte, porque o utilizador é definir apenas uma única localização. Neste caso, o cmdlet ainda suporta carateres universais, mas ela força a resolução para um único local.

Para obter mais informações sobre os padrões de caráter universal, consulte [suporte a caracteres curinga nos parâmetros de Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md).

#### <a name="defining-objects"></a>Definição de objetos

Esta secção contém diretrizes para a definição de objetos para os cmdlets e para estender objetos existentes.

##### <a name="define-standard-members"></a>Definir membros padrão

Defina membros padrão para estender um tipo de objeto num arquivo Types.ps1xml personalizado (utilize o ficheiro do Windows PowerShell Types.ps1xml como um modelo). Membros padrão são definidos por um nó com o nome PSStandardMembers. Estas definições permitem que os outros cmdlets e o tempo de execução do Windows PowerShell para trabalhar com o seu objeto de maneira consistente.

##### <a name="define-objectmembers-to-be-used-as-parameters"></a>Definir ObjectMembers para serem utilizadas como parâmetros

Se está Projetando um objeto para um cmdlet, certifique-se de que seus membros são mapeados diretamente para os parâmetros de cmdlets que irá utilizá-lo. Este mapeamento permite que o objeto facilmente sejam enviados para o pipeline e a passar de um cmdlet para outro.

Preexistentes objetos do .NET Framework que são devolvidos por cmdlets frequentemente faltam alguns membros importantes ou convenientes que são necessários para o desenvolvedor de script ou do usuário. Esses membros em falta podem ser particularmente importantes para exibição e para criar o membro correto nomes, de modo a que o objeto pode ser transmitido corretamente para o pipeline. Crie um arquivo Types.ps1xml personalizado documentar esses membros necessários. Quando cria este ficheiro, recomendamos a seguinte convenção de nomenclatura: *< Your_Product_Name >*. Types.ps1xml.

Por exemplo, poderia adicionar um `Mode` propriedade do script da [FILEINFO](/dotnet/api/System.IO.FileInfo) tipo para apresentar os atributos de um ficheiro mais clareza. Além disso, poderia adicionar um `Count` propriedade de alias para o [Array](/dotnet/api/System.Array) tipo para permitir a utilização consistente com esse nome de propriedade (em vez de `Length`).

##### <a name="implement-the-icomparable-interface"></a>Implementar a Interface IComparable

Implementar um [System.IComparable](/dotnet/api/System.IComparable) interface em todos os objetos de saída. Isso permite que os objetos de saída a ser facilmente inseridos em vários cmdlets de classificação e análise.

##### <a name="update-display-information"></a>Apresentar as informações de atualização

Se a exibição para um objeto não fornecer os resultados esperados, crie um personalizado  *\<YourProductName >*. Ficheiro de Format.ps1xml para esse objeto.

### <a name="support-well-defined-pipeline-input-sc02"></a>Suporte a entrada de Pipeline bem definido (chaves SC02)

#### <a name="implement-for-the-middle-of-a-pipeline"></a>Implementar para o meio de um Pipeline

Implementar um cmdlet, partindo do princípio de que ele será chamado do meio de um pipeline (ou seja, outros cmdlets irá produzir entrada ou consumir o respetivo resultado). Por exemplo, pode pressupor que o `Get-Process` cmdlet, uma vez que ele gera dados, é utilizado apenas como o primeiro cmdlet num pipeline. No entanto, uma vez que este cmdlet foi concebido para o meio de um pipeline, este cmdlet permite cmdlets anteriores ou de dados no pipeline para especificar os processos para recuperar.

#### <a name="support-input-from-the-pipeline"></a>Suporte de entrada do Pipeline

Em cada parâmetro definido para um cmdlet, inclua, pelo menos, um parâmetro que oferece suporte a entrada do pipeline. Suporte para entrada de pipeline permite que o utilizador a obter dados ou objetos, para enviá-los para o conjunto de parâmetros corretos e, para passar os resultados diretamente para um cmdlet.

Um parâmetro aceita entrada do pipeline, se o **parâmetro** atributo inclui a `ValueFromPipeline` palavra-chave, o `ValueFromPipelineByPropertyName` atributo de palavra-chave, ou ambas as palavras-chave na sua declaração. Se nenhum dos parâmetros num parâmetro definido que suporte o `ValueFromPipeline` ou `ValueFromPipelineByPropertyName` forma significativa não não possível colocar palavras-chave, o cmdlet depois de outro cmdlet porque ele irá ignorar qualquer entrada do pipeline.

#### <a name="support-the-processrecord-method"></a>Suporta o método ProcessRecord

Para aceitar todos os registros do cmdlet anterior no pipeline, seu cmdlet tem de implementar o [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método. Windows PowerShell chama esse método várias vezes, uma vez para todos os registos que são enviados ao seu cmdlet.

### <a name="write-single-records-to-the-pipeline-sc03"></a>Escrever os registos de únicos para o Pipeline (SC03)

Quando um cmdlet devolve objetos, o cmdlet deve gravar os objetos imediatamente à medida que são gerados. O cmdlet não deve contê-los de modo a memória intermédia-los numa matriz de combinada. Os cmdlets que recebem os objetos como entrada, em seguida, será capazes de processar, apresentar, ou processar e exibir os objetos de saída sem demora. Um cmdlet que gera a saída objetos de uma de cada vez deve chamar o [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) método. Um cmdlet que gera a saída de objetos em lotes (por exemplo, como uma API subjacente retorna uma matriz de objetos de saída) deve chamar o [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) método com o segundo parâmetro definido para `true`.

### <a name="make-cmdlets-case-insensitive-and-case-preserving-sc04"></a>Tornar os Cmdlets maiúsculas de minúsculas e preservação caso (SC04)

Por predefinição, o próprio Windows PowerShell diferencia maiúsculas de minúsculas. No entanto, como ela lida com muitos sistemas preexistentes, o Windows PowerShell preservar caso para facilidade de operação e de compatibilidade. Em outras palavras, se um caractere é fornecido em letras maiúsculas, o Windows PowerShell mantém-o em letras maiúsculas. Para sistemas de funcionar bem, um cmdlet tem de cumprir esta Convenção. Se possível, ele deverá operar de maneira maiúsculas de minúsculas. No entanto, ele deve, preservar o caso original para cmdlets que ocorrer mais tarde com um comando ou no pipeline.

## <a name="see-also"></a>Veja Também

[Diretrizes de desenvolvimento necessárias](./required-development-guidelines.md)

[Diretrizes de desenvolvimento de consultoria](./advisory-development-guidelines.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
