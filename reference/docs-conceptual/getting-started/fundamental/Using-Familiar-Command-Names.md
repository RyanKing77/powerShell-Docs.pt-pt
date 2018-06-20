---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Utilizar Nomes de Comandos Familiares
ms.assetid: 021e2424-c64e-4fa5-aa98-aa6405758d5d
ms.openlocfilehash: 37fc6dfad5a2f1363254744141dcab1e13aa5066
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952686"
---
# <a name="using-familiar-command-names"></a>Utilizar Nomes de Comandos Familiares
Utilizar um mecanismo chamado *aliasing*, do Windows PowerShell permite que os utilizadores fazer referência aos comandos por nomes alternativos. Aliasing permite aos utilizadores com a experiência de outros shells reutilizar nomes comuns do comando que já conhecem para efetuar operações similares no Windows PowerShell. Apesar de não, vamos abordar os aliases de Windows PowerShell em detalhe, pode ainda utilizá-los como começar com o Windows PowerShell.

Aliasing associa um nome de comando que escrever outro comando. Por exemplo, o Windows PowerShell tem uma função interna com o nome **limpar anfitrião** que limpa a janela de saída. Se escrever um o **conformidade com cls** ou **limpar** interpreta de comando numa linha de comandos, do Windows PowerShell que se trata de um alias para o **limpar anfitrião** funcionar e executa o  **Limpar anfitrião** função.

Esta funcionalidade ajuda os utilizadores para saber o Windows PowerShell. Primeiro, maior parte dos utilizadores Cmd.exe e UNIX tem uma grande repertoire de comandos de que os utilizadores já conhece o nome e, embora os Windows PowerShell equivalentes não poderão produzir resultados idênticos, são suficientemente fechar no formulário que os utilizadores podem utilizá-los para trabalhar sem ter de memorize primeiro os nomes do Windows PowerShell. Segundo, a origem principais frustration na aprendizagem da shell de novo quando o utilizador já estiver familiarizado com outro shell, é os erros que são causados por "memória mas". Se tiver utilizado o Cmd.exe anos, quando tiver um ecrã completo de saída e pretende limpá-lo, reflexively teria de escrever o **cls** de comandos e prima a tecla ENTER. Sem o alias para o **limpar anfitrião** função no Windows PowerShell, basta teria de obter a mensagem de erro "**'cls' não é reconhecido como um cmdlet, a função, programa operável ou ficheiro de script.**" e ficar com nenhuma ideia do que fazer para limpar a saída.

Segue-se uma listagem breve comuns Cmd.exe e UNIX comandos que pode utilizar dentro do Windows PowerShell:

|||||
|-|-|-|-|
|cat|Dir|montagem|RM|
|cd|echo|Mover|rmdir|
|chdir|apagar|popd|modo de suspensão|
|Limpar|h|ps|Ordenação|
|cls|histórico|pushd|Tee|
|Copiar|kill|pwd|tipo|
|del|LP|r|escrita|
|diff|ls|ren||

Caso se utilizar um destes comandos reflexively e pretende obter o nome real do comando do Windows PowerShell nativo, pode utilizar o **Get-Alias** comando:

```
PS> Get-Alias cls

CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

Para tornar os exemplos mais legível, guia do utilizador do Windows PowerShell, geralmente, evita a utilizar aliases. No entanto, saber mais sobre aliases de isto antecipadamente pode ainda ser útil se estiver a trabalhar com arbitrários fragmentos de código do Windows PowerShell de outra origem ou se pretende definir as suas próprias aliases. As restantes desta secção abordar aliases padrão e como definir os seus próprios aliases.

### <a name="interpreting-standard-aliases"></a>Interpretar os Aliases padrão
Ao contrário os aliases descritos acima, que foram concebidos para nome de compatibilidade com outras interfaces, os aliases incorporados no Windows PowerShell, geralmente, são concebidos de uma forma abreviada. Estes nomes mais curtos podem ser digitados rapidamente, mas são impossíveis se não souber que consultarem de leitura.

Tenta comprometer entre efeitos de clareza e uma forma abreviada, fornecendo um conjunto de aliases padrão que se baseiam em nomes de expressão compacta para comuns verbos e substantivos do Windows PowerShell. Isto permite que um conjunto de núcleos de alias para cmdlets comuns que são legíveis quando sabe os nomes de expressão compacta. Por exemplo, num padrão aliases o verbo **obter** é abreviado para **g**, o verbo **definir** é abreviado para **s**, o substantivo **Item** é abreviado para **posso**, o substantivo **localização** é abreviado para **l**e o substantivo comando é abreviado para **cm**.

Eis um breve exemplo para ilustrar como isto funciona. O alias padrão para o Get-Item provém de combinar **g** para o Get e **posso** para o Item: **gi**. O alias de Item de conjunto padrão provém de combinar **s** para o conjunto e **posso** para o Item: **Tama**. O alias padrão para a localização de Get provém de combinar **g** para o Get e **l** para a localização, **gl**. O alias padrão para a localização do conjunto é proveniente de combinar **s** para o conjunto e **l** para a localização, **sl**. O alias padrão para Get-Command provém de combinar **g** para o Get e **cm** para o comando, **gcm**. Não há nenhum cmdlet Set-Command, mas se existirem, iremos conseguiriam adivinhar que o alias padrão provenientes de **s** para o conjunto e **cm** para o comando: **scm**. Além disso, as pessoas familiarizado com o aliasing de Windows PowerShell que encontrar **scm** seria capaz de adivinhar que o alias refere-se ao comando Set.

### <a name="creating-new-aliases"></a>Criar novo alias
Pode criar os seus próprios aliases utilizando o cmdlet Set-Alias. Por exemplo, as seguintes declarações de criar os aliases de padrão de cmdlet abordados interpretar Aliases padrão:

```
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

Internamente, o Windows PowerShell utiliza comandos nestes durante o arranque, mas estes aliases não são das partições. Se tentar executar, na verdade, uma destes comandos, obterá um erro explicar que o alias não pode ser modificado. Por exemplo:

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```