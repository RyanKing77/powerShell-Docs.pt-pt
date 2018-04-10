---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Saber Mais sobre os Nomes do Windows PowerShell
ms.assetid: b4d0fd22-8298-4ee6-82ae-9b6f2907c986
ms.openlocfilehash: 381aa619a41ccacb2ff3a4cdbc2b75b7f04282d1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="learning-windows-powershell-names"></a>Saber Mais sobre os Nomes do Windows PowerShell
Nomes de aprendizagem dos comandos e parâmetros de comando é um investimento de muito tempo com a maioria das interfaces de linha de comandos. O problema é que existem padrões muito poucos, pelo que é a única forma de saber por memorizing cada comando e cada um dos parâmetros que tem de utilizar regularmente.

Quando trabalha com um novo comando ou um parâmetro, geralmente, não é possível utilizar o que já sabe; tem de localizar e obter um novo nome. Se observar como interfaces aumentam a partir de um pequeno conjunto de ferramentas com adições incrementais de funcionalidade, é fácil de ver por que razão a estrutura não padrão. Com nomes de comandos em particular, isto poderá som lógico, uma vez que cada comando é uma ferramenta separada, mas não existe uma melhor forma de lidar com os nomes de comando.

São criadas maioria dos comandos para gerir os elementos do sistema operativo ou aplicações, tais como serviços ou os processos. Os comandos de tem uma variedade de nomes que podem ou não pode ajustar uma família. Por exemplo, nos sistemas operativos Windows, pode utilizar o **net start** e **net stop** comandos para iniciar e parar um serviço. Há outra ferramenta de controlo de serviço mais generalizada para o Windows que tem um nome completamente diferente, **sc**, que não se ajusta o padrão de nomenclatura para o **net** comandos de serviço. Para a gestão de processo, o Windows tem o **tasklist** comando para processos de lista e o **taskkill** comando para eliminar os processos.

Comandos que demoram parâmetros têm especificações de parâmetro de dados. Não é possível utilizar o **net start** comando para iniciar um serviço num computador remoto. O **sc** comando irá iniciar um serviço num computador remoto, mas para especificar o computador remoto, terá de preceder o respetivo nome com uma barra invertida duplo. Por exemplo, para iniciar o serviço spooler num computador remoto com o nome DC01, teria de escrever **sc \\ \\DC01 iniciar spooler**. A lista de tarefas em execução no DC01, tem de utilizar o **/S** parâmetro (para o "sistema") e forneça o nome DC01 sem barras invertidas, como esta: **tasklist /S DC01**.

Apesar de existirem distinctions técnicas importantes entre um serviço e um processo, estes são ambos os exemplos de elementos geríveis num computador que têm um ciclo de vida bem definido. Poderá iniciar ou parar um serviço ou processo ou obter uma lista de todos os atualmente em execução os serviços ou os processos. Por outras palavras, embora um serviço e um processo de diversos elementos, as ações que executar um serviço ou de um processo são muitas vezes, essencialmente, os mesmos. Além disso, as escolhas que pode efetuar para personalizar uma ação, especificando os parâmetros podem ser, conceptualmente, semelhantes bem.

Windows PowerShell exploits estes semelhanças para reduzir o número de nomes distintos que precisa de saber para compreender e utilizar cmdlets.

### <a name="cmdlets-use-verb-noun-names-to-reduce-command-memorization"></a>Nomes de verbo-nome de utilização de cmdlets para reduzir Memorization de comando
O Windows PowerShell utiliza um sistema de nomenclatura de "verbo-nome", em que cada nome do cmdlet é composta por um verbo padrão hifenizado com um nome específico. Verbos do Windows PowerShell não são sempre verbos em inglês, mas estes express ações específicas no Windows PowerShell. Os substantivos são muito semelhante substantivos em qualquer idioma, descrevem tipos específicos de objetos que são importantes na administração do sistema. É fácil demonstrar como estes nomes de duas partes reduzir o esforço de aprendizagem observando alguns exemplos de verbos e substantivos.

Os substantivos são menos restritos, mas deve sempre descrevem o que funciona um comando após. Windows PowerShell tem comandos como **Get-Process**, **Stop-Process**, **Get-Service**, e **Stop-Service**.

No caso de dois substantivos e dois verbos, consistência simplificar não learning que tanto que. No entanto, se observar um conjunto padrão de 10 verbos e 10 substantivos, em seguida, tiver 20 apenas palavras compreender, mas essas palavras podem ser utilizadas para formar 100 nomes de comando distintos.

Frequentemente, pode reconhecer que um comando faz ao ler o respetivo nome, e é aparente, normalmente, o nome deve ser utilizado para um novo comando. Por exemplo, um comando de encerramento do computador pode ser **Stop-Computer**. Poderá ser um comando que lista todos os computadores numa rede **Get-computador**. O comando que obtém a data do sistema é **Get-Data**.

Pode listar todos os comandos que incluem um determinado verbo com o **-verbo** parâmetro **Get-Command** (, vamos abordar **Get-Command** detalhadamente na secção seguinte). Por exemplo, para ver todos os cmdlets que utilizam o verbo **obter**, tipo:

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

O **-substantivo** parâmetro é ainda mais útil porque permite-lhe ver uma família de comandos que afetam o mesmo tipo de objeto. Por exemplo, se quiser ver quais os comandos estão disponíveis para gerir serviços, tipo de comando a seguir:

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

Um comando não é necessariamente um cmdlet, apenas porque tem um esquema de nomenclatura de verbo-nome. Um exemplo de um comando do Windows PowerShell nativo que não é um cmdlet, mas tem um nome de verbo-nome, o comando para limpar uma janela da consola, desmarque-anfitrião. O comando de Clear-anfitrião é, na verdade, uma função interna, como pode ver se executar Get-Command nele:

```
PS> Get-Command -Name Clear-Host

CommandType     Name                            Definition
-----------     ----                            ----------
Function        Clear-Host                      $spaceType = [System.Managem...
```

### <a name="cmdlets-use-standard-parameters"></a>Parâmetros de padrão de utilização de cmdlets
Conforme indicado anteriormente, comandos utilizados em interfaces tradicionais de linha de comandos não tem, geralmente, os nomes dos parâmetros consistente. Por vezes, parâmetros não têm nomes de todo. Quando são, muitas vezes, são caráter ou abreviado palavras que podem ser digitadas rapidamente, mas não são facilmente compreendidas pelo novos utilizadores.

Ao contrário da maioria dos outros tradicionais interfaces de linha de comandos, do Windows PowerShell processa parâmetros diretamente e utiliza este acesso direto aos parâmetros, bem como orientações para programadores para normalizar os nomes dos parâmetros. Apesar de Isto garante que cada cmdlet irá sempre está em conformidade com as normas, encorajá-lo.

> [!NOTE]
> Os nomes dos parâmetros têm sempre um '-' prepended aos mesmos quando utilizá-los, para permitir que o Windows PowerShell para identificá-las claramente como parâmetros. No **Get-Command - nome Clear-Host** exemplo, é o nome do parâmetro **nome**, mas é introduzido como -**nome**.

Seguem-se algumas das características gerais dos nomes de parâmetro padrão e utilizações.

#### <a name="the-help-parameter-"></a>O parâmetro de ajuda (?)
Quando especificar o **-?** o parâmetro para qualquer cmdlet, o cmdlet não foi executado. Em vez disso, o Windows PowerShell mostra ajuda para o cmdlet.

#### <a name="common-parameters"></a>Parâmetros comuns
Windows PowerShell tem vários parâmetros conhecidos como *parâmetros comuns de*. Porque estes parâmetros são controlados pelo motor do Windows PowerShell, sempre que são implementados por um cmdlet, será sempre comportar-se da mesma forma. Os parâmetros comuns são **WhatIf**, **confirmar**, **verboso**, **depurar**, **aviso**, **ErrorAction**, **ErrorVariable**, **OutVariable**, e **OutBuffer**.

#### <a name="suggested-parameters"></a>Parâmetros sugeridos
Os cmdlets de núcleo do Windows PowerShell utilizar nomes de standard para os parâmetros semelhantes. Embora a utilização de nomes de parâmetro não é imposta, há explícita orientações para a utilização a encorajar uniformização.

Por exemplo, a documentação de orientação recomenda nomenclatura um parâmetro que refere-se a um computador pelo nome como **ComputerName**, em vez de servidor, anfitrião, sistema, nó ou outras palavras alternativas comuns. Entre o parâmetro sugerido importante são nomes **Force**, **excluir**, **incluir**, **PassThru**, **caminho**, e **CaseSensitive**.