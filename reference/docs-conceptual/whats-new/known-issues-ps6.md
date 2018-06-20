---
ms.date: 05/17/2018
keywords: PowerShell, core
title: Problemas conhecidos para o PowerShell 6.0
ms.openlocfilehash: 6ad1bcaf1de06f204b57eb8ce23b3053ba4a5b38
ms.sourcegitcommit: 2d9cf1ccb9a653db7726a408ebcb65530dcb1522
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/19/2018
ms.locfileid: "34309583"
---
# <a name="known-issues-for-powershell-60"></a>Problemas conhecidos para o PowerShell 6.0

## <a name="known-issues-for-powershell-on-non-windows-platforms"></a>Problemas conhecidos do PowerShell em plataformas não sejam Windows

Alpha versões do PowerShell no Linux e macOS principalmente estão funcionais, mas tem algumas limitações importantes e problemas de usabilidade. Versões beta do PowerShell no Linux e macOS são mais funcional e estável que alfa versões, mas ainda pode ser lacking algumas conjunto de funcionalidades e pode conter erros. Em alguns casos, estes problemas são simplesmente os erros que ainda não foram corrigidos ainda. Noutros casos (tal como com os aliases de predefinido para ls, cp, etc.), iremos estiver à procura de comentários da Comunidade sobre as escolhas podemos fazer.

Nota: Devido a semelhanças de muitos subsistemas subjacentes, PowerShell no Linux e macOS tendem a partilhar o mesmo nível de maturidade em funcionalidades e erros. Exceto conforme indicado abaixo, os problemas nesta secção aplicam-se para ambos os sistemas operativos.

### <a name="case-sensitivity-in-powershell"></a>Sensibilidade no PowerShell

Historicamente, o PowerShell foi uniformemente sensível, com algumas exceções. Em sistemas de operativos da família UNIX, o sistema de ficheiros é predominantemente maiúsculas e minúsculas e os respeita PowerShell padrão do sistema de ficheiros; Isto é exposto através de diversas formas, óbvias e não óbvios.

#### <a name="directly"></a>diretamente

- Quando especificar um ficheiro no PowerShell, tem de utilizar as maiúsculas e minúsculas corretas.

#### <a name="indirectly"></a>Indiretamente

- Se um script tenta carregar um módulo e o nome do módulo não está corretamente, cased, a carregar o módulo irá falhar. Isto pode provocar um problema com os scripts existentes, se o nome pelo qual o módulo é referenciado não corresponde ao nome de ficheiro real.
- Conclusão de separador irá não conclusão automática se as maiúsculas e minúsculas de nome de ficheiro estão errada. O fragmento para concluir tem de ser cased corretamente. (Conclusão é sensível para o nome do tipo e conclusões de membro de tipo.)

### <a name="ps1-file-extensions"></a>. PS1 As extensões de ficheiro

Scripts do PowerShell devem terminar em `.ps1` para o interpretador compreender como carregar e executá-los no processo atual. A execução de scripts no processo atual é o comportamento esperado habitual para o PowerShell. O `#!` número pode ser adicionado a um script que não tem um `.ps1` extensão, mas Isto fará com que o script a ser executada numa nova instância do PowerShell a impedir o script de trabalhar corretamente quando interchanging objetos. (Nota: Isto poderá ser o comportamento desejável ao executar um script do PowerShell do `bash` ou outro shell.)

### <a name="missing-command-aliases"></a>Aliases de comandos em falta

No Linux/macOS, "aliases conveniência" para os comandos básicos `ls`, `cp`, `mv`, `rm`, `cat`, `man`, `mount`, `ps` foram removidos. No Windows, o PowerShell fornece um conjunto de aliases que mapeiam para os nomes de comando do Linux para comodidade do utilizador. Estes aliases foram removidos da predefinição PowerShell distribuições de Linux/macOS, permitindo que o executável nativo a ser executada sem especificar um caminho.

Existem os profissionais de TI e contras para fazê-lo. Remover os aliases expõe a experiência de comando nativo para o utilizador do PowerShell, mas reduz a funcionalidade na shell porque os comandos nativos devolvem cadeias em vez de objetos.

> [!NOTE]
> Trata-se de uma área em que a equipa do PowerShell está à procura de comentários.
> O que é a solução preferida? Deve, deixá-lo tal como está ou adicione novamente os aliases de conveniência? Consulte [emitir #929](https://github.com/PowerShell/PowerShell/issues/929).

### <a name="missing-wildcard-globbing-support"></a>Falta o caráter universal (globbing) suporte

Atualmente, o PowerShell funciona apenas expansão de caráter universal (globbing) para os cmdlets incorporados no Windows e para comandos externos ou binários, bem como os cmdlets no Linux. Isto significa que um comando como `ls
*.txt` irá falhar porque o asterisco não será expandido para corresponder aos nomes de ficheiros. Pode contornar esta praticando `ls (gci *.txt | % name)` ou, mais simples, `gci *.txt` utilizando o equivalente incorporado do PowerShell para `ls`.

Consulte [#954](https://github.com/PowerShell/PowerShell/issues/954) para fornecer comentários sobre como melhorar a experiência de globbing no Linux/macOS.

### <a name="net-framework-vs-net-core-framework"></a>.NET framework vs .NET Core Framework

PowerShell no Linux/macOS utiliza .NET Core que é um subconjunto do .NET Framework completa no Microsoft Windows. O que é significativo porque PowerShell fornece acesso direto para os tipos de arquitetura subjacente, métodos, etc. Como resultado, scripts que são executados no Windows não podem executar em plataformas do Windows não devido às diferenças nas estruturas. Para obter mais informações sobre principais de .NET Framework, consulte <https://dotnetfoundation.org/net-core>

Com a introdução do [.NET 2.0 padrão](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/), 2.0 do .NET Core colocará back muitas das tradicionais tipos e métodos presente no .NET Framework completa. Isto significa que o PowerShell Core poderá carregar muitos módulos do Windows PowerShell tradicionais sem modificação. Pode seguir o nosso .NET padrão 2.0 trabalho relacionados [aqui](https://github.com/PowerShell/PowerShell/projects/4).

### <a name="redirection-issues"></a>Problemas de redirecionamento

Redirecionamento de entrada não é suportado no PowerShell em qualquer plataforma.
[Problema #1629](https://github.com/PowerShell/PowerShell/issues/1629)

Utilize `Get-Content` ao escrever o conteúdo de um ficheiro para o pipeline.

Saída redirecionada irá conter a marca de ordem de bytes Unicode (LM) quando a codificação UTF-8 predefinida é utilizada. O LM irá causar problemas quando trabalhar com utilitários que não a conta ou quando acrescente um ficheiro. Utilize `-Encoding Ascii` escrever texto ASCII (que, não a ser Unicode, não terá uma LM). (Nota: consulte [RFC0020](https://github.com/PowerShell/PowerShell-RFC/issues/71) para fornecer comentários em melhorar a experiência de codificação de PowerShell Core em todas as plataformas. Iremos estão a trabalhar para suporte UTF-8 sem um LM e potencialmente alterar as predefinições para os vários cmdlets codificação entre plataformas.)

### <a name="job-control"></a>Controlo de tarefa

Não há sem suporte de controlo de trabalho do PowerShell no Linux/macOS.
O `fg` e `bg` comandos não estão disponíveis.

Para o tempo a ser, pode utilizar [PowerShell tarefas](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_jobs) que funcionam em todas as plataformas.

### <a name="remoting-support"></a>Suporte do sistema de interação remota

Atualmente, PowerShell Core suporta a gestão remota do PowerShell (PSRP) através de WSMan com a autenticação básica no macOS e Linux e com a autenticação NTLM baseados no Linux. (Autenticação baseada em Kerberos não é suportada.)

O trabalho para a gestão remota baseada em WSMan está a ser efetuado [fornecedor de omi psl](https://github.com/PowerShell/psl-omi-provider) repositório.

PowerShell Core também suporta a gestão remota do PowerShell (PSRP) através de SSH em todas as plataformas (Windows, macOS e Linux). Embora isto não é atualmente suportado em produção, pode saber mais sobre esta configuração [aqui](../core-powershell/ssh-remoting-in-powershell-core.md).

### <a name="just-enough-administration-jea-support"></a>Suporte de just Enough-administração (JEA)

A capacidade de criar administração restrita pontos finais de sistema de interação remota (JEA) não está atualmente disponível no PowerShell no Linux/macOS. Esta funcionalidade não está atualmente no âmbito de 6.0 e algo iremos considerar post 6.0 porque requer o trabalho de design significativas.

### <a name="sudo-exec-and-powershell"></a>`sudo`, `exec`e o PowerShell

Porque o PowerShell executa a maioria dos comandos na memória (por exemplo, Python ou Ruby), não é possível utilizar o sudo diretamente com o PowerShell built-ins. (Pode, obviamente, executar `powershell` de sudo.) Se for necessário executar um cmdlet do PowerShell a partir do PowerShell com sudo, por exemplo, `sudo Set-Date 8/18/2016`, em seguida, efetue `sudo powershell Set-Date 8/18/2016`. Da mesma forma, não é possível exec um PowerShell incorporado diretamente. Em vez disso, terá de fazer `exec powershell item_to_exec`.

Este problema é atualmente a ser controlado por #3232.

### <a name="missing-cmdlets"></a>Cmdlets em falta

Um grande número de comandos (cmdlets) normalmente disponíveis no PowerShell não está disponível no Linux/macOS. Em muitos casos, estes comandos sentido não nas plataformas seguintes (por exemplo, funcionalidades específicas do Windows, como o registo). Outros comandos, como os comandos de controlo de serviço (Get/início/paragem-Service) não estiverem presentes, mas não funcional. Em versões futuras irão corrigir estes problemas, corrigir os cmdlets quebrados e adicionar novas ao longo do tempo.

### <a name="command-availability"></a>Disponibilidade de comando

A tabela seguinte lista os comandos que se sabe não funcionam no PowerShell no Linux/macOS.

<table>
<th>Comandos</th><th>Estado operacional</th><th>Notas</th>
<tr>
<td>Get-Service, novo serviço, reinicie o serviço, retoma-serviço Set-Service, serviço de início, parar serviço, suspender-Service
<td>Não disponível.
<td>Estes comandos não serão reconhecidos. Isto deve ser corrigido numa versão futura.
</tr>
<tr>
<td>Get-Acl, Acl do conjunto
<td>Não disponível.
<td>Estes comandos não serão reconhecidos. Isto deve ser corrigido numa versão futura.
</tr>
<tr>
<td>Get-AuthenticodeSignature, AuthenticodeSignature conjunto
<td>Não disponível.
<td>Estes comandos não serão reconhecidos. Isto deve ser corrigido numa versão futura.
</tr>
<tr>
<td>Processo de espera
<td>Disponível, não funciona corretamente. <td>Por exemplo `Start-Process gvim -PassThru | Wait-Process` não funciona; falhar a aguardar que o processo.
</tr>
<tr>
<td>Register-PSSessionConfiguration, anular o registo-PSSessionConfiguration, Get-PSSessionConfiguration
<td>Disponível mas não funcionam.
<td>Escreve uma mensagem de erro a indicar que os comandos não estão a funcionar. Estas devem ser corrigidas numa versão futura.
</tr>
<tr>
<td>Get-o evento, novo evento, registar EngineEvent, registe-WmiEvent, remova-o evento, eventos anular o registo
<td>Disponível, mas não existem origens de eventos estão disponíveis.
<td>Os comandos de eventos CCM do PowerShell estão presentes, mas a maioria das origens de eventos utilizadas com os comandos (por exemplo, System.Timers.Timer) não está disponível no Linux fazer os comandos inútil na versão Alpha.
</tr>
<tr>
<td>Set-ExecutionPolicy
<td>Disponível mas não funcionam.
<td>Devolve uma mensagem a indicar não é suportada nesta plataforma. Política de execução é um focado de utilizador "segurança conjunto" que ajuda a impedir que o utilizador efetuar prende dispendiosas. Não é um limite de segurança.
</tr>
<tr>
<td>Novo-PSSessionOption, novo PSTransportOption
<td>Disponível, mas New-PSSession não funciona.
<td>New-PSSessionOption e New-PSTransportOption não são verificadas atualmente funcione agora que New-PSSession funciona.
</tr>
</table>
