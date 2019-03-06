---
title: Compreender a codificação de ficheiros no VSCode e no PowerShell
description: Configurar a codificação do ficheiro no VSCode e no PowerShell
ms.date: 02/28/2019
ms.openlocfilehash: 9cf445ebd0c2bb2dbdf4438f02dafe3df3a5d1e2
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429810"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a>Compreender a codificação de ficheiros no VSCode e no PowerShell

Quando utilizar o VS Code para criar e editar scripts do PowerShell, é importante que os ficheiros são guardados com o formato de codificação de caracteres corretas.

## <a name="what-is-file-encoding-and-why-is-it-important"></a>O que é a codificação do ficheiro e por que é importante?

VSCode gerencia a interface entre um humano cadeias de caracteres de inserção de caracteres num buffer e blocos de leitura/gravação de bytes para o sistema de ficheiros. Quando o VSCode salva um arquivo, ele usa um codificação para fazer isso de texto.

Da mesma forma, quando PowerShell executa um script, tem de converter os bytes num arquivo de carateres para reconstruir o arquivo num programa do PowerShell. Uma vez que o VSCode escreve o ficheiro e PowerShell lê o arquivo, têm de utilizar o mesmo sistema de codificação. Este processo de analisar um script do PowerShell é: *bytes* -> *carateres* -> *tokens*  ->   *árvore de sintaxe abstrata* -> *execução*.

VSCode e PowerShell são instalados com uma configuração de codificação sensível predefinido. No entanto, a codificação padrão utilizado pelo PowerShell mudou com o lançamento do PowerShell Core (v6.x). Para garantir que tenha sem problemas com o PowerShell ou a extensão de PowerShell no VSCode, terá de configurar as definições de VSCode e o PowerShell corretamente.

## <a name="common-causes-of-encoding-issues"></a>Causas comuns de problemas de codificação

Problemas de codificação ocorrerem quando a codificação de VSCode ou o ficheiro de script não coincide com a codificação esperado do PowerShell. Não é possível para o PowerShell determinar automaticamente a codificação de ficheiro.

É mais provável ter problemas de codificação quando estiver a utilizar carateres não os [conjunto de carateres ASCII de 7 bits](https://ascii.cl/). Por exemplo:

- Accented carateres latinos (`É`, `ü`)
- Carateres não latinos, como Cirílico (`Д`, `Ц`)
- Chinês Han (`脚`, `本`)

Motivos comuns para problemas de codificação são:

- As codificações de VSCode e o PowerShell não tiverem sido alteradas nas predefinições. Para PowerShell 5.1 e abaixo, a predefinição de codificação é diferente do VSCode.
- Outro editor abriu e substituir o arquivo numa codificação de novo. Muitas vezes, isso acontece com o ISE.
- O ficheiro é verificado no controle de fonte numa codificação que é diferente do que VSCode ou PowerShell espera. Isto pode acontecer quando os funcionários utilizam editores com configurações de codificação diferentes.

### <a name="how-to-tell-when-you-have-encoding-issues"></a>Como descobrir se tiver problemas de codificação

Erros de codificação, muitas vezes, apresentam próprios como analisar erros nos scripts. Se encontrar seqüências de caracteres estranho em seu script, isso pode ser o problema. No exemplo abaixo, en-dash (`–`) é apresentado como os caracteres `â€“`:

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

Este problema ocorre porque o VSCode codifica o caráter `–` em UTF-8, como os bytes `0xE2 0x80 0x93`.
Quando esses bytes são descodificados como Windows 1252, eles são interpretados como os caracteres `â€“`.

Algumas seqüências de caracteres estranho que poderá ver incluem:

- `â€“` em vez de `–`
- `â€”` em vez de `—`
- `Ã„2` em vez de `Ä`
- `Â` em vez de ` ` (um espaço sem quebra)
- `Ã©` em vez de `é`

Neste útil [referência](https://www.i18nqa.com/debug/utf8-debug.html) apresenta uma lista de padrões comuns que indicar um problema de codificação UTF-8/Windows-1252.

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a>Como a extensão de PowerShell no VSCode interage com codificações

A extensão de PowerShell interage com os scripts de diversas formas:

1. Quando os scripts são editados no VSCode, o conteúdo será enviado por VSCode para a extensão. O [Protocolo de servidor de idioma][] estipula que este conteúdo é transferido em UTF-8. Por conseguinte, não é possível que a extensão obter a codificação errada.
2. Quando os scripts são executados diretamente na consola do integrada, eles estão lida no arquivo do PowerShell diretamente. Se a codificação do PowerShell difere do VSCode, algo pode dar errado aqui.
3. Quando um script que está aberto no VSCode faz referência a outro script que não está aberto no VSCode, a extensão é retrocede para carregar o conteúdo desse script do sistema de arquivos. A extensão de PowerShell está predefinido para a codificação UTF-8, mas usa [marca de ordem de byte][], ou BOM, deteção seleciona a codificação correta.

O problema ocorre quando partindo do princípio de que a codificação de formatos de BOM sem (como [UTF-8][] com nenhuma BOM e [Windows-1252][]).
A extensão de PowerShell padrão é UTF-8. A extensão não é possível alterar as definições de codificação do VSCode.
Para obter mais informações, consulte [emitir #824](https://github.com/Microsoft/vscode/issues/824).

## <a name="choosing-the-right-encoding"></a>Escolher a codificação correta

Aplicativos e sistemas diferentes, podem utilizar diferentes codificações:

- No .NET Standard na web e no mundo do Linux, UTF-8 é agora a codificação dominante.
- Muitas aplicações de .NET Framework utilizam [UTF-16][]. Por motivos históricos, às vezes, isso é chamado de "Unicode", um termo que agora se refere a uma ampla [padrão](https://en.wikipedia.org/wiki/Unicode) que inclui o UTF-8 e UTF-16.
- No Windows, muitos aplicativos nativos que são anteriores às Unicode continuam a utilizar o Windows 1252 por predefinição.

Codificações Unicode também tem o conceito de uma ordem de byte marcar (BOM). BOMs ocorrerem no início do texto para dizer um Decodificador qual codificação é usando o texto. Para codificações de multi-bytes, o BOM também indica [ordenação de bits](https://en.wikipedia.org/wiki/Endianness) da codificação. BOMs destinam-se para ser bytes que ocorrem raramente no texto não-Unicode, permitindo uma estimativa razoável de que o texto é Unicode quando uma BOM está presente.

BOMs são opcionais e adoção não é tão popular do mundo do Linux como uma convenção confiável do UTF-8 é utilizada em qualquer lugar. A maioria dos aplicativos de Linux presumem que a entrada de texto está codificada em UTF-8. Embora muitos aplicativos de Linux irão reconhecer e processar corretamente uma BOM, um número não o fizer, levando a artefactos no texto manipulado com esses aplicativos.

**Por conseguinte**:

- Se trabalha principalmente com aplicativos do Windows e Windows PowerShell, deve preferir uma codificação como UTF-8 com BOM ou UTF-16.
- Se trabalha em todas as plataformas, deve preferir UTF-8 com BOM.
- Se trabalha principalmente em contextos associados ao Linux, deve preferir UTF-8, sem BOM.
- Windows 1252 e latin 1 são codificações herdadas, essencialmente, deve evitar se possível.
  No entanto, alguns aplicativos mais antigos do Windows poderão depender nos mesmos.
- Também vale a pena observar que a assinatura de script é [dependentes da codificação](https://github.com/PowerShell/PowerShell/issues/3466), que significa que uma alteração da codificação num script assinado exigirá resigning.

## <a name="configuring-vscode"></a>Configurar o VSCode

Do VSCode codificação padrão é UTF-8, sem BOM.

Para definir [Codificação do VSCode][], aceda às definições VSCode (<kbd>Ctrl<kbd>+</kbd>,</kbd>) e defina o `"files.encoding"` definição:

```json
"files.encoding": "utf8bom"
```

Alguns valores possíveis são:

- `utf8`: [UTF-8] sem BOM
- `utf8bom`: [UTF-8] com BOM
- `utf16le`: Little endian [UTF-16]
- `utf16be`: Big endian [UTF-16]
- `windows1252`: [Windows-1252]

Deve obter uma lista pendente para isso, na vista de GUI ou ver conclusões para ele no JSON.

Também pode adicionar o seguinte para deteção automática de codificação sempre que possível:

```json
"files.autoGuessEncoding": true
```

Se não pretender que estas definições afetam todos os tipos de ficheiros, VSCode também permite que configurações por idioma. Criar uma definição de idioma específico ao colocar configurações `[<language-name>]` campo. Por exemplo:

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a>Configurar o PowerShell

Do PowerShell codificação padrão varia dependendo da versão:

- No PowerShell 6 +, a codificação predefinida é UTF-8, sem BOM em todas as plataformas.
- No Windows PowerShell, a codificação predefinida é normalmente Windows-1252, uma extensão da [latin 1][], também conhecido como ISO 8859-1.

No PowerShell 5 + pode encontrar a codificação padrão com isto:

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

O seguinte procedimento [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) pode ser utilizado para determinar o que a codificação de sua sessão do PowerShell infere para um script sem um BOM.

```powershell
$badBytes = [byte[]]@(0xC3, 0x80)
$utf8Str = [System.Text.Encoding]::UTF8.GetString($badBytes)
$bytes = [System.Text.Encoding]::ASCII.GetBytes('Write-Output "') + [byte[]]@(0xC3, 0x80) + [byte[]]@(0x22)
$path = Join-Path ([System.IO.Path]::GetTempPath()) 'encodingtest.ps1'

try
{
    [System.IO.File]::WriteAllBytes($path, $bytes)

    switch (& $path)
    {
        $utf8Str
        {
            return 'UTF-8'
            break
        }

        default
        {
            return 'Windows-1252'
            break
        }
    }
}
finally
{
    Remove-Item $path
}
```

É possível configurar o PowerShell para usar uma codificação de determinado mais normalmente, através de definições de perfil. Consulte os seguintes artigos:

- [@mklement0]da [resposta sobre codificação do PowerShell no StackOverflow](https://stackoverflow.com/a/40098904).
- [@rkeithhill]da [mensagem de blogue sobre como lidar com entrada de BOM sem UTF-8 no PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).

Não é possível forçar o PowerShell para utilizar uma codificação específica de entrada. PowerShell 5.1 e abaixo padrão para Windows-1252 codificação quando não existe nenhum BOM. Por motivos de interoperabilidade, é melhor guardar os scripts num formato Unicode com um BOM.

> [!IMPORTANT]
> Quaisquer outras ferramentas, tem esse touch PowerShell scripts podem ser afetados pelas suas escolhas de codificação ou codificar seus scripts para outra codificação.

### <a name="existing-scripts"></a>Scripts existentes

Scripts já no sistema de ficheiros poderão ter de ser codificada novamente para a codificação escolhida novo. Na barra de VSCode na parte inferior, verá o rótulo UTF-8. Clique nele para abrir a barra de ação e selecione **guardar com codificação**. Agora pode selecionar uma nova codificação do ficheiro em questão. Ver [Codificação do VSCode][] para obter instruções completas.

Se precisar de codificar vários ficheiros, pode utilizar o seguinte script:

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a>O PowerShell integrado Scripting Environment (ISE)

Se também pode editar scripts com o ISE do PowerShell, tem de sincronizar as definições de codificação aqui.

O ISE deve honrar uma BOM, mas também é possível usar a reflexão para [definir a codificação](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).
Tenha em atenção que isto não sejam persistentes entre as start-UPS.

### <a name="source-control-software"></a>Software de controlo de origem

Algumas ferramentas de controle de origem, como o git, ignorar codificações; o Git monitoriza apenas os bytes.
Outros, como o TFS ou Mercurial, podem não ter. Até mesmo algumas ferramentas baseada no git contam com a descodificação de texto.

Quando for este o caso, certifique-se de que:

- Configure o em seu controle de origem para corresponder à sua configuração de VSCode de codificação do texto.
- Certifique-se de que todos os seus ficheiros são verificados no controle de fonte na codificação relevante.
- Ter cautela alterações para a codificação recebido por meio do controle de origem. Um sinal de chave isso é uma diferença que indica as alterações, mas onde nada parece ter alterado (porque têm de bytes, mas não o tiver feito carateres).

### <a name="collaborators-environments"></a>Ambientes dos funcionários

Na parte superior, configurando o controle de origem, certifique-se de que os seus colaboradores em qualquer partilha de ficheiros não têm configurações que substituem a codificação por recodificar ficheiros do PowerShell.

### <a name="other-programs"></a>Outros programas

Qualquer outro programa que lê ou escreve um script do PowerShell novamente poderá codificá-lo.

Alguns exemplos são:

- Usando a área de transferência para copiar e colar um script. Isso é comum em cenários como:
  - Copiar um script para uma VM
  - Copiar um script fora de um e-mail ou a página Web
  - Copiar um script para dentro ou fora de um documento do Microsoft Word ou PowerPoint
- Outros editores de texto, tais como:
  - Bloco de notas
  - vim
  - Qualquer outro editor de script do PowerShell
- Texto da edição de utilitários, como:
  - `Get-Content`/`Set-Content`/`Out-File`
  - Operadores de redirecionamento do PowerShell, como `>` e `>>`
  - `sed`/`awk`
- Transferência de programas, do ficheiro, como:
  - Um navegador da web, durante o download de scripts
  - Uma partilha de ficheiros

Algumas dessas ferramentas lidam em bytes, em vez de texto, mas outros oferecem configurações de codificação. Nesses casos em que terá de configurar uma codificação, terá de fazer o mesmo que o seu editor de codificação para evitar problemas.

## <a name="other-resources-on-encoding-in-powershell"></a>Outros recursos na codificação no PowerShell

Existem algumas outras boas postagens sobre codificação e configurar a codificação do PowerShell que vale a pena uma leitura:

- [@mklement0]do [resumo de codificação do PowerShell no StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)
- Edições anteriores aberta no vscode-PowerShell para problemas de codificação:
  - [#1308](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [#1628](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [#1680](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [#1744](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [#1751](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [O clássico *Joel on Software* escrever sobre Unicode](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [Codificação no .NET Standard](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[latin 1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[marca de ordem de byte]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[Protocolo de servidor de idioma]: https://microsoft.github.io/language-server-protocol/
[Codificação do VSCode]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
