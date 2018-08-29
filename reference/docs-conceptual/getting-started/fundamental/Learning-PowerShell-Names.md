---
ms.date: 08/24/2018
keywords: PowerShell, o cmdlet
title: Os nomes do PowerShell de aprendizagem
ms.assetid: b4d0fd22-8298-4ee6-82ae-9b6f2907c986
ms.openlocfilehash: d4e374530c8628df0d53fd860c4b7a149c58eb60
ms.sourcegitcommit: 59727f71dc204785a1bcdedc02716d8340a77aeb
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/28/2018
ms.locfileid: "43134197"
---
# <a name="learning-powershell-names"></a>Os nomes do PowerShell de aprendizagem

Nomes de comandos e parâmetros de aprendizagem exige um investimento de tempo significativo com a maioria das interfaces de linha de comandos. O problema é que existem alguns padrões. Só é memorization forma de aprender os comandos e parâmetros que tem de utilizar todos regularmente.

Quando trabalha com um novo comando ou um parâmetro, é possível utilizar sempre o que já conhece. Tem de localizar e aprender um novo nome. Tradicionalmente, interfaces de linha de comandos começar com um pequeno conjunto de ferramentas e crescer com adições incrementais. É fácil ver por que não há nenhuma estrutura padrão.
Isso parece lógico os nomes dos comando uma vez que cada comando é uma ferramenta separada. PowerShell tem uma maneira melhor de lidar com nomes de comandos.

## <a name="learning-command-names-in-traditional-shells"></a>Nomes de comandos de shells tradicionais de aprendizagem

Baseiam-se a maioria dos comandos para gerir os elementos do sistema operacional ou aplicativos, como serviços ou processos. Os comandos têm nomes que podem ou não podem caber numa família. Por exemplo, em sistemas Windows, pode utilizar o `net start` e `net stop` comandos para iniciar e parar um serviço. **SC. EXE** é outra ferramenta de controlo de serviço para Windows. Esse nome não se encaixa o padrão de nomenclatura para o `net` comandos de serviço. Para gestão de processos, o Windows tem o `tasklist` comando para processos de lista e o `taskkill` comando para interrompe processos.

Além disso, estes comandos têm especificações de parâmetro irregular. Não é possível utilizar o `net start` comando para iniciar um serviço num computador remoto. O `sc` comando pode iniciar um serviço num computador remoto.
Mas, para especificar o computador remoto, terá de preceder o nome com uma barra invertida duplo. Para iniciar o serviço de spooler num computador remoto denominado DC01, escreva `sc \\DC01 start spooler`. A lista de tarefas em execução no DC01, utilize o **/S** parâmetro e o nome de computador sem as barras invertidas. Por exemplo, `tasklist /S DC01`.

Serviços e processos são exemplos de elementos gerenciáveis num computador que tenham ciclos de vida bem definidos. Pode iniciar ou parar serviços e processos ou obter uma lista de todos os atualmente em execução os serviços ou processos. Embora existam diferenças técnicas importantes entre eles, as ações que efetuar em serviços e processos conceitualmente são os mesmos. Além disso, as opções que podemos fazer para personalizar uma ação, especificando os parâmetros podem ser um conceito semelhantes também.

PowerShell explora essas semelhanças para reduzir o número de nomes distintos que precisa saber para compreender e utilizar os cmdlets.

## <a name="cmdlets-use-verb-noun-names-to-reduce-command-memorization"></a>Cmdlets utilizar nomes de verbo-substantivo para reduzir memorization de comando

PowerShell utiliza um sistema de nomenclatura de "verbo-substantivo". Cada nome do cmdlet é constituído por um verbo padrão hyphenated com um substantivo específico. Verbos de PowerShell nem sempre são verbos em inglês, mas eles express ações específicas no PowerShell. Os substantivos são muito parecido com nomes em qualquer idioma. Eles descrevem determinados tipos de objetos que são importantes na administração de sistema. É fácil demonstrar como estes nomes de duas partes reduzem o esforço de aprendizagem ao observar alguns exemplos.

PowerShell possui um conjunto recomendado de verbos padrão. Os substantivos são menos restritos, mas sempre descrevem o que toma o verbo. PowerShell tem de comandos como `Get-Process`, `Stop-Process`, `Get-Service`, e `Stop-Service`.

Para este exemplo de dois substantivos e verbos, consistência não simplificar muito de aprendizado. Expanda essa lista para um conjunto padronizado de 10 verbos e 10 substantivos. Agora precisa apenas 20 palavras para compreender.
Mas essas palavras podem ser combinadas para nomes de comando distintos 100 do formulário.

É fácil de entender o que faz um comando do PowerShell ao ler o seu nome. O comando para desligar um computador é `Stop-Computer`. O comando para listar todos os computadores numa rede é `Get-Computer`.
O comando para obter a data do sistema é `Get-Date`.

Pode listar todos os comandos que incluem um determinado verbo com o **verbo** parâmetro para `Get-Command`. Por exemplo, para ver todos os cmdlets que usam o verbo `Get`, tipo:

```
PS> Get-Command -Verb Get

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Acl                         Get-Acl [[-Path] <String[]>]...
Cmdlet          Get-Alias                       Get-Alias [[-Name] <String[]...
Cmdlet          Get-AuthenticodeSignature       Get-AuthenticodeSignature [-...
Cmdlet          Get-ChildItem                   Get-ChildItem [[-Path] <Stri...
...
```

Utilize o **substantivo** parâmetro para ver uma família de comandos que afetam o mesmo tipo de objeto. Por exemplo, execute o comando para ver os comandos disponíveis para o gerenciamento de serviços a seguir:

```
PS> Get-Command -Noun Service

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Service                     Get-Service [[-Name] <String...
Cmdlet          New-Service                     New-Service [-Name] <String>...
Cmdlet          Restart-Service                 Restart-Service [-Name] <Str...
Cmdlet          Resume-Service                  Resume-Service [-Name] <Stri...
Cmdlet          Set-Service                     Set-Service [-Name] <String>...
Cmdlet          Start-Service                   Start-Service [-Name] <Strin...
Cmdlet          Stop-Service                    Stop-Service [-Name] <String...
Cmdlet          Suspend-Service                 Suspend-Service [-Name] <Str...
...
```

## <a name="cmdlets-use-standard-parameters"></a>Cmdlets utilizam parâmetros padrão

Conforme observado anteriormente, comandos utilizados nas interfaces de linha de comandos tradicionais sempre não tem os nomes dos parâmetros consistentes. Os parâmetros são, muitas vezes, caráter ou abreviado palavras que são fáceis de escrever, mas não são facilmente compreendidas pelos novos utilizadores.

Ao contrário da maioria das outras interfaces de linha de comandos tradicionais, PowerShell processa parâmetros diretamente e, utiliza este acesso direto aos parâmetros juntamente com a orientação para programadores para padronizar os nomes de parâmetros. Esta orientação incentiva, mas não garante que cada cmdlet está em conformidade com o padrão.

PowerShell também uniformiza o separador de parâmetro. Os nomes de parâmetros sempre terá um "-" anexado aos mesmos com um comando do PowerShell. Considere o exemplo a seguir:

```powershell
Get-Command -Name Clear-Host
```

É o nome do parâmetro **Name**, mas ele é digitado como `-Name` quando utilizado na linha de comandos como um parâmetro.

Aqui estão algumas das características gerais dos nomes de parâmetros padrão e utilizações.

### <a name="the-help-parameter-"></a>O parâmetro de ajuda (?)

Quando especificar a `-Help` ou `-?` parâmetro sobre qualquer cmdlet, PowerShell apresenta a ajuda do cmdlet. O cmdlet não é executado.

### <a name="common-parameters"></a>Parâmetros comuns

PowerShell tem várias *parâmetros comuns de*. Esses parâmetros são controlados pelo mecanismo do PowerShell. Parâmetros comuns de sempre se comporte da mesma forma. Os parâmetros comuns são **WhatIf**, **confirmar**, **verboso**, **depurar**, **Warn**, **ErrorAction**, **ErrorVariable**, **OutVariable**, e **OutBuffer**.

### <a name="recommended-parameter-names"></a>Nomes dos parâmetros recomendados

Os cmdlets do PowerShell core utilizar nomes de standard para os parâmetros semelhante. A utilização destes nomes padrão não é imposta, mas há orientação explícita para incentivar a padronização.

Por exemplo, o nome recomendado para um parâmetro que se refere a um computador é **ComputerName**, em vez de servidor, o anfitrião, o sistema, o nó ou o alguma outra alternativa comum. Outros nomes de parâmetro recomendada importante são **força**, **excluir**, **incluir**, **PassThru**, **caminho**, e **CaseSensitive**.