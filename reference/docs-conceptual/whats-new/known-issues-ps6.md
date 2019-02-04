---
ms.date: 05/17/2018
keywords: PowerShell, core
title: Problemas conhecidos para o PowerShell 6.0
ms.openlocfilehash: ce40a1925e564fbd2c661e70ec36d3842d915dfe
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686762"
---
# <a name="known-issues-for-powershell-60"></a>Problemas conhecidos para o PowerShell 6.0

## <a name="known-issues-for-powershell-on-non-windows-platforms"></a>Problemas conhecidos para o PowerShell em plataformas não Windows

Lançamentos alfa do PowerShell no Linux e macOS são predominantemente funcionais, mas têm algumas limitações consideráveis e problemas de usabilidade. Versões beta do PowerShell no Linux e macOS mais funcional e estável do que os lançamentos alfa, mas ainda pode ser na falta de um conjunto de funcionalidades e pode conter bugs. Em alguns casos, esses problemas são simplesmente os erros que ainda não tiverem sido corrigidos ainda. Em outros casos (tal como com os aliases de padrão para ls, cp, etc.), estamos procurando comentários da Comunidade sobre as opções que podemos fazer.

Nota: Devido às semelhanças dos vários subsistemas subjacentes, o PowerShell no Linux e macOS tendem partilhar o mesmo nível de maturidade em recursos e bugs. Exceto conforme indicado abaixo, os problemas nesta secção aplicam-se para sistemas operacionais.

### <a name="case-sensitivity-in-powershell"></a>Sensibilidade do PowerShell

Historicamente, o PowerShell tem sido uniformemente maiúsculas de minúsculas, com algumas exceções. Em sistemas de operativos da família UNIX, o sistema de ficheiros é predominantemente maiúsculas e minúsculas e PowerShell segue o padrão de sistema de arquivos; Isso é exposto por meio de diversas formas, óbvias e não óbvias.

#### <a name="directly"></a>Diretamente

- Ao especificar um ficheiro no PowerShell, tem de utilizar as maiúsculas e minúsculas corretas.

#### <a name="indirectly"></a>Indiretamente

- Se um script tenta carregar um módulo e o nome do módulo não está corretamente, Case, em seguida, o carregamento do módulo irá falhar. Isso pode causar um problema com scripts existentes se o nome pelo qual o módulo é referenciado não corresponde ao nome de ficheiro real.
- Conclusão de tabulação será não preenchimento automático se o caso de nome de ficheiro é errado. O fragmento para concluir tem de ser Case corretamente. (Conclusão diferencia maiúsculas de minúsculas para o nome do tipo e conclusões de membro do tipo).

### <a name="ps1-file-extensions"></a>. PS1 Extensões de ficheiro

Scripts do PowerShell tem de terminar em `.ps1` para o interpretador compreender como carregar e executá-los no processo atual. Execução de scripts no processo atual é o comportamento esperado habitual para o PowerShell. O `#!` mágica podem ser adicionada a um script que não tem um `.ps1` extensão, mas isso fará com que o script seja executado numa nova instância do PowerShell a impedir que o script funcionar corretamente quando intercambiando objetos. (Nota: Isto pode ser o comportamento desejável ao executar um script do PowerShell do `bash` ou shell do outro.)

### <a name="missing-command-aliases"></a>Aliases de comandos em falta

No Linux/macOS, os "aliases de conveniência" para os comandos básicos `ls`, `cp`, `mv`, `rm`, `cat`, `man`, `mount`, `ps` foram removidos. No Windows, o PowerShell fornece um conjunto de aliases que mapeiam para nomes de comandos do Linux para comodidade do utilizador. Estes aliases foram removidos da predefinição do PowerShell em distribuições de Linux/macOS, permitindo que o executável nativo ser executado sem especificar um caminho.

Há prós e contras em fazer isso. Remover os aliases expõe a experiência de comando nativo para o usuário do PowerShell, mas reduz a funcionalidade no shell, pois os comandos nativos retornam cadeias de caracteres em vez de objetos.

> [!NOTE]
> Essa é uma área em que a equipe do PowerShell está à procura de comentários.
> O que é a solução preferida? Deve, deixá-lo tal como está ou adicione os aliases de conveniência novamente? Ver [emitir #929](https://github.com/PowerShell/PowerShell/issues/929).

### <a name="missing-wildcard-globbing-support"></a>Falta o caráter universal (globbing) suporte

Atualmente, o PowerShell faz apenas a expansão de caráter universal (globbing) para cmdlets incorporados no Windows e para comandos externos ou binários, bem como cmdlets no Linux. Isso significa que um comando como `ls
*.txt` irá falhar porque o asterisco não será expandido para comparar os nomes de ficheiro. Pode contornar isso ao fazê-lo `ls (gci *.txt | % name)` ou, mais simples, `gci *.txt` usando o equivalente de incorporada do PowerShell para `ls`.

Ver [#954](https://github.com/PowerShell/PowerShell/issues/954) nos enviar comentários sobre como melhorar a experiência de globbing em Linux/macOS.

### <a name="net-framework-vs-net-core-framework"></a>No .NET Core Framework do .NET framework vs

PowerShell no Linux/macOS usa o .NET Core, que é um subconjunto do .NET Framework completo no Microsoft Windows. Isso é significativo, como o PowerShell fornece acesso direto para os tipos de estrutura subjacente, métodos, etc. Como resultado, scripts que são executados no Windows podem não ser executadas em plataformas não Windows devido às diferenças em arquiteturas de. Para obter mais informações sobre o .NET Core Framework, consulte <https://dotnetfoundation.org/net-core>

Com o advento dos [.NET Standard2.0](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/), .NET Core 2.0 trará back muitos dos tipos tradicionais e métodos presentes no .NET Framework completo. Isso significa que o PowerShell Core poderão carregar muitos módulos tradicionais do Windows PowerShell sem modificação. Pode seguir o nosso .NET Standard 2.0 trabalho relacionados [aqui](https://github.com/PowerShell/PowerShell/projects/4).

### <a name="redirection-issues"></a>Problemas de redirecionamento

Redirecionamento de entrada não é suportado no PowerShell em qualquer plataforma.
[Problema #1629](https://github.com/PowerShell/PowerShell/issues/1629)

Utilize `Get-Content` para escrever o conteúdo de um ficheiro no pipeline.

Saída redirecionada irá conter a marca de ordem de byte Unicode (LM) quando a codificação UTF-8 padrão é usada. O BOM causará problemas ao trabalhar com utilitários que não espera ou quando anexando a um ficheiro. Utilize `-Encoding Ascii` para escrever texto ASCII (que, não estar Unicode, não terá uma BOM).

> [!Note]
> ver [RFC0020](https://github.com/PowerShell/PowerShell-RFC/issues/71) nos enviar comentários em melhorar a experiência de codificação para o PowerShell Core em todas as plataformas. Estamos trabalhando para dar suporte a UTF-8, sem uma BOM e potencialmente alterar as predefinições de codificação para vários cmdlets entre plataformas.

### <a name="job-control"></a>Controle de tarefa

Não há nenhum suporte de controlo de tarefa do PowerShell em Linux/macOS.
O `fg` e `bg` comandos não estão disponíveis.

Por enquanto, pode usar [tarefas do PowerShell](/powershell/module/microsoft.powershell.core/about/about_jobs) que funcionam em todas as plataformas.

### <a name="remoting-support"></a>Suporte de comunicação remota

Atualmente, o PowerShell Core suporta comunicação remota do PowerShell (PSRP) em WSMan com a autenticação básica no macOS e Linux e com a autenticação baseada em NTLM no Linux. (Autenticação com base em Kerberos não é suportada.)

O trabalho para a gestão remota com base em WSMan está a ser feito [fornecedor de omi psl](https://github.com/PowerShell/psl-omi-provider) repositório.

O PowerShell Core também suporta a comunicação remota do PowerShell (PSRP) através de SSH em todas as plataformas (Windows, macOS e Linux). Embora isto não é atualmente suportado em produção, pode saber mais sobre esta configuração [aqui](../core-powershell/ssh-remoting-in-powershell-core.md).

### <a name="just-enough-administration-jea-support"></a>Suporte de just Enough-administração (JEA)

A capacidade de criar pontos finais de comunicação remota (JEA) de administração restrita não está atualmente disponível no PowerShell em Linux/macOS. Esta funcionalidade não está atualmente no âmbito 6.0 e algo que possamos considerar post 6.0 porque requer trabalho de design significativos.

### <a name="sudo-exec-and-powershell"></a>`sudo`, `exec`e o PowerShell

Porque o PowerShell executa a maioria dos comandos na memória (como Python ou Ruby), não é possível utilizar o sudo diretamente com o PowerShell built-ins. (Pode, obviamente, executar `pwsh` de sudo.) Se for necessário executar um cmdlet do PowerShell a partir do PowerShell com sudo, por exemplo, `sudo Set-Date 8/18/2016`, em seguida, faria `sudo pwsh Set-Date 8/18/2016`. Da mesma forma, não é possível exec PowerShell incorporado diretamente. Em vez disso, teria que fazer `exec pwsh item_to_exec`.

Este problema está atualmente a ser controlado como parte da [#3232](https://github.com/PowerShell/PowerShell/issues/3232).

### <a name="missing-cmdlets"></a>Cmdlets em falta

Um grande número de comandos (cmdlets) normalmente disponíveis no PowerShell não está disponível no Linux/macOS. Em muitos casos, esses comandos não fazem sentido nessas plataformas (por exemplo, funcionalidades específicas do Windows como o Registro). Outros comandos, como os comandos de controlo de serviço (Get/Start/Stop-Service) estão presentes, mas não funcional. Versões futuras irão corrigir esses problemas, corrigir os cmdlets quebrados e adicionar novas ao longo do tempo.

### <a name="command-availability"></a>Disponibilidade de comando

A tabela seguinte lista os comandos que se sabe não funcionam no PowerShell em Linux/macOS.

|Comandos|Estado operacional|Notas|
|--------|-----------------|-----|
|`Get-Service`, `New-Service`, `Restart-Service`, `Resume-Service`, `Set-Service`, `Start-Service`, `Stop-Service`, `Suspend-Service`|Não está disponível.|Estes comandos não serão reconhecidos. Isso deve ser corrigido numa versão futura.|
|`Get-Acl`, `Set-Acl`|Não disponível.|Estes comandos não serão reconhecidos. Isso deve ser corrigido numa versão futura.|
|`Get-AuthenticodeSignature`, `Set-AuthenticodeSignature`|Não disponível.|Estes comandos não serão reconhecidos. Isso deve ser corrigido numa versão futura.|
|`Wait-Process`|Disponível, não funciona corretamente. |Por exemplo `Start-Process gvim -PassThru | Wait-Process` não funciona; falhar a aguardar o processo.|
|`Register-PSSessionConfiguration`, `Unregister-PSSessionConfiguration`, `Get-PSSessionConfiguration`|Disponível mas não funcionam.|Escreve uma mensagem de erro indicando que os comandos não estão a funcionar. Isso devem ser corrigidos numa versão futura.|
|`Get-Event`, `New-Event`, `Register-EngineEvent`, `Register-WmiEvent`, `Remove-Event`, `Unregister-Event`|Disponível, mas não existem origens de eventos estão disponíveis.|Os comandos de eventos do PowerShell estão presentes, mas a maioria das origens de eventos utilizadas com os comandos (por exemplo, o timer) não está disponível no Linux, fazendo com que os comandos inútil da versão Alpha.|
|`Set-ExecutionPolicy`|Disponível mas não funcionam.|Devolve uma mensagem a indicar não é suportada nesta plataforma. Política de execução é um voltada para o utilizador "segurança belt" que ajuda a impedir que o usuário erros Caro. Não é um limite de segurança.|
|`New-PSSessionOption`, `New-PSTransportOption`|Mas disponíveis `New-PSSession` não funciona.|`New-PSSessionOption` e `New-PSTransportOption` não são verificadas atualmente a trabalhar agora que `New-PSSession` funciona.|
