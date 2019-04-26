---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: O que há de novo no Windows PowerShell 5.0
ms.openlocfilehash: b2cb729948d4b53c5ea9a536dbeda04c7cb50997
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085954"
---
# <a name="whats-new-in-windows-powershell-50"></a>O que há de novo no Windows PowerShell 5.0

Windows PowerShell 5.0 inclui funcionalidades novas importantes que expandem a sua utilização, melhoram a usabilidade e permitem controlar e gerir ambientes baseados em Windows mais fácil e abrangente.

Windows PowerShell 5.0 é compatível. Cmdlets, fornecedores, módulos, snap-ins, scripts, funções e perfis que foram projetados para o Windows PowerShell 4.0, o Windows PowerShell 3.0 e o Windows PowerShell 2.0 geralmente funcionam no Windows PowerShell 5.0 sem alterações.

## <a name="installing-windows-powershell"></a>Instalar o Windows PowerShell

Windows PowerShell 5.0 é instalado por padrão no Windows Server 2016 Technical Preview e Windows 10.

Para instalar o Windows PowerShell 5.0 no Windows Server 2012 R2, Windows 8.1 Enterprise ou Windows 8.1 Pro, transfira e instale [Windows Management Framework 5.0](https://aka.ms/wmf5download). Certifique-se de que leia os detalhes de download e todos os requisitos de sistema, de cumprir antes de instalar o Windows Management Framework 5.0.

## <a name="in-this-topic"></a>Neste tópico

- [Atualizações do Windows PowerShell 4.0 DSC na KB 3000850](#windows-powershell-40-updates-in-november-2014-update-rollup-kb-3000850)
- [Novos recursos do Windows PowerShell 5.0](#new-features-in-windows-powershell-50)
- [Novos recursos do Windows PowerShell 4.0](#new-features-in-windows-powershell-40)
- [Novos recursos do Windows PowerShell 3.0](#new-features-in-windows-powershell-30)

## <a name="windows-powershell-40-updates-in-november-2014-update-rollup-kb-3000850"></a>Coletânea de atualizações do Windows PowerShell 4.0 em Novembro de 2014 (KB 3000850)

Muitas atualizações e melhorias para Windows PowerShell Desired State Configuration (DSC) no Windows PowerShell 4.0 estão disponíveis no [rollup da atualização de Novembro de 2014 para Windows RT 8.1, Windows 8.1 e Windows Server 2012 R2](https://support.microsoft.com/kb/3000850/) (KB 3000850 ). Pode determinar se o KB 3000850 está instalado no seu sistema, executando `Get-Hotfix -Id KB3000850` no Windows PowerShell.

- Atualizações para cmdlets existentes no [PSDesiredStateConfiguration](https://technet.microsoft.com/library/dn391651(v=wps.640).aspx) módulo
  - [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) é mais rápido (especialmente no ISE).
  - [Start-dscconfiguration para](https://technet.microsoft.com/library/dn521623.aspx) tem um novo parâmetro, - UseExisting, que volta a aplicar a última configuração aplicada.
  - [Start-dscconfiguration para](https://technet.microsoft.com/library/dn521623.aspx) -Force foi corrigido.
  - [Get-dsclocalconfigurationmanager para](https://technet.microsoft.com/library/dn407378.aspx) apresenta informações mais úteis sobre o estado do motor.
  - [Test-dscconfiguration para](https://technet.microsoft.com/library/dn407382.aspx) agora retorna o nome do computador, juntamente com o verdadeiro ou FALSO.
  - [Novo DscChecksum](https://technet.microsoft.com/library/dn521622.aspx) agora oferece suporte a caminhos UNC.

- Novos cmdlets no [PSDesiredStateConfiguration](https://technet.microsoft.com/library/dn391651(v=wps.640).aspx) módulo
  - [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541(v=wps.630).aspx):  Executa uma verificação de servidor de solicitação a pedido.
  - [Stop-DscConfiguration](https://technet.microsoft.com/library/mt143542(v=wps.630).aspx):  Deixa de uma configuração que já está em execução.
  - [Remove-DscConfigurationDocument](https://technet.microsoft.com/library/mt143544(v=wps.630).aspx):  Permite-lhe remover documentos de configuração em várias etapas (pendentes, anteriores ou atuais).

- Aprimoramentos da linguagem
  - DependsOn agora oferece suporte a recursos compostos.
  - DependsOn agora oferece suporte a números nos nomes de instância de recurso.
  - Expressões de nó que já não ser avaliado como vazio emitir erros.
  - Foi corrigido um erro que ocorre se uma expressão de nó for avaliada como vazio.
  - Configurações de chamar configurações agora trabalham na consola do Windows PowerShell.

- Aprimoramentos de modo de solicitação
  - Agora, o modo de solicitação suporta todos os ficheiros ZIP.
  - **AllowModuleOverwrite** agora funciona corretamente.

- Melhorias de resiliência
  - Novos **DebugMode** permite-lhe recarregar os módulos de recursos.
  - Se ocorrer uma falha de configuração, o ficheiro de pending.mof não é eliminado.
  - O Gestor de configuração Local (LCM) agora é mais resiliente quando as definições de metaconfiguration ficaram danificadas.

- Melhorias de diagnóstico
  - Um aviso é apresentado quando o LCM define o temporizador para diferentes definições que especificou.
  - Ficheiros de registo de erro contêm agora a pilha de chamadas para os recursos do Windows PowerShell.

- Aperfeiçoamentos de flexibilidade
  - O recurso de LocalConfigurationManager tem uma nova propriedade **ActionAfterReboot**.
    - ContinueConfiguration (valor predefinido): Retoma automaticamente uma configuração depois de um nó de destino ser reiniciado.
    - StopConfiguration: Não retomada automaticamente uma configuração depois de um nó é reiniciado.
  - Uma execução de consistência agora pode ocorrer com mais frequência do que uma operação de SOLICITAÇÃO, ou vice-versa.
  - Suporte de controlo de versões:  DSC agora pode reconhecer um documento que foi gerado num cliente mais recente (acompanha [WMF 5.0](https://aka.ms/wmf5download)).

- Melhorias de prevenção de erro
  - Versão do módulo foi aplicado antes de uma configuração é aplicada.
  - **DebugPreference** agora está corretamente definida para Get-, Set- ou chamadas de TargetResource de teste.

- Melhorias de manipulação de credencial
  - É utilizado um certificado agora, se os dois **certificado** e **PSDscAllowPlainTextPassword** são especificados.
  - As credenciais são desencriptadas, mesmo para Get-TargetResource.
  - Credenciais de Metaconfiguration são encriptadas e desencriptadas.
  - PSCredentials agora são desencriptadas quando eles estão num objeto incorporado.

- Aprimoramentos de recursos incorporadas
  - O recurso de pacote
    - Já não instala o pacote de errado (a partir do local ou de fontes da web).
    - Agora oferece suporte a HTTPS.
  - Existe agora suporte para HTTPS no [empacotar o recurso](https://technet.microsoft.com/library/dn282132.aspx).
  - [Arquivar o recurso](https://technet.microsoft.com/library/dn249917.aspx) agora suporta credenciais.

## <a name="new-features-in-windows-powershell-50"></a>Novos recursos do Windows PowerShell 5.0

- [Novos recursos do Windows PowerShell](#new-features-in-windows-powershell)
- [Novos recursos do Windows PowerShell Desired State Configuration](#new-features-in-windows-powershell-desired-state-configuration)
- [Novos recursos do Windows PowerShell ISE](#new-features-in-windows-powershell-ise)
- [Novos recursos nos serviços de Web do Windows PowerShell](#new-features-in-windows-powershell-web-services-management-odata-iis-extension)
- [Correções de erros importantes no Windows PowerShell 5.0](#notable-bug-fixes-in-windows-powershell-50)

### <a name="new-features-in-windows-powershell"></a>Novos recursos do Windows PowerShell

- A partir do Windows PowerShell 5.0, pode desenvolver usando classes, utilizando a sintaxe formal e a semântica que é semelhante a outras linguagens de programação orientada a objeto. **Classe**, **Enum**, e foram adicionados outros palavras-chave para o idioma do Windows PowerShell para suportar a nova funcionalidade. Para obter mais informações sobre como trabalhar com classes, consulte about_Classes.

- Windows PowerShell 5.0 introduz um fluxo de informações novos, estruturado que pode utilizar para transmitir dados estruturados entre um script e seus chamadores (ou ambiente de alojamento). Agora, pode utilizar o Write-Host para emitir a saída no fluxo de informações. Fluxos de informações também funcionam em PowerShell.Streams, tarefas, tarefas agendadas e fluxos de trabalho. As seguintes funcionalidades de suportar o fluxo de informações.
  - Um cmdlet de escrita-informações novas que permite que especifique como o Windows PowerShell manipula dados de fluxo de informações para um comando. Write-Host é um wrapper para informações de escrita. Informações de escrita também são uma atividade de fluxo de trabalho suportadas.
  - Dois novos parâmetros comuns de, InformationVariable e InformationAction, permitem-lhe determinar como os fluxos de informações de um comando são exibidos. Valores válidos para InformationAction são SilentlyContinue, parar, continuar, Inquire, ignorar ou suspender, com SilentlyContinue serem o padrão. InformationVariable Especifica uma cadeia de caracteres, como o nome de uma variável para o qual pretende que os dados de Write-Host de um comando guardado.
  - Uma nova variável de preferência, InformationPreference, especifica a sua preferência predefinida para os dados de fluxo de informações numa sessão do Windows PowerShell. O valor predefinido é SilentlyContinue.
  - Dois novos parâmetros comuns, PSInformation e InformationAction, foram adicionados.
  - Quando utiliza o comando Format-Table, colunas da tabela agora são automaticamente formatadas avaliando a primeira 300ms de dados que passa pelo fluxo.

- Em colaboração com [Microsoft Research](https://research.microsoft.com/), foi adicionado um novo cmdlet, ConvertFrom-cadeia. ConvertFrom-String permite-lhe extrair e analisar objetos estruturados do conteúdo de cadeias de caracteres de texto. Para obter mais informações, consulte ConvertFrom-cadeia de caracteres.
- Um novo cmdlet Convert-String automaticamente formata texto com base num exemplo que fornece um - parâmetro de exemplo.
- Um novo módulo, Microsoft.PowerShell.Archive, inclui cmdlets que permitem-lhe comprimir ficheiros e pastas para os ficheiros de arquivo (também conhecido como ZIP), extrair os arquivos de ficheiros existentes do ZIP e atualizar arquivos ZIP com as versões mais recentes de ficheiros comprimidos dentro dos mesmos.
- Um novo módulo, PackageManagement, permite-lhe detetar e instalar pacotes de software na Internet. O módulo PackageManagement (anteriormente conhecido como OneGet) é um gestor ou Multiplexador de gestores de pacotes existente (também chamados fornecedores de pacote) unificar a gestão de pacotes do Windows com uma única interface do Windows PowerShell.
- Um novo módulo, PowerShellGet, permite-lhe localizar, instalar, publicar e atualizar os módulos e recursos de DSC no [galeria do PowerShell](https://www.powershellgallery.com/), ou num repositório de módulo interno que pode configurar ao executar o cmdlet Register-PSRepository.
- Uma nova palavra-chave language, **Hidden**, foi adicionado para especificar que um membro (uma propriedade ou um método) não é apresentado por predefinição nos resultados de Get-Member (a menos que adicione o parâmetro - Force). Propriedades ou métodos que foram marcados ocultos também não aparecem nos resultados do IntelliSense, a menos que estejam num contexto em que o membro deve estar visível; Por exemplo, a variável $ automática Isto deve mostrar membros ocultados quando estiver a ser o método de classe.
- Novo Item, Remove-Item e Get-ChildItem foram aperfeiçoados para oferecer suporte a criar e gerir [links simbólicos](https://en.wikipedia.org/wiki/Symbolic_link). O **- ItemType** parâmetro para o novo Item aceita um novo valor **SymbolicLink**. Agora, pode criar links simbólicos numa única linha, executando o cmdlet New-Item.
- Get-ChildItem também tem um novo - profundidade parâmetro, que utiliza com o - parâmetro de recurso para limitar a recursão. Por exemplo, Get-ChildItem-Recurse - 2 de profundidade devolver resultados da pasta atual, todas as pastas filho dentro da pasta atual e todas as pastas no filho de pastas.
- Agora, vamos copiar ficheiros ou pastas a partir de uma sessão do Windows PowerShell para outro, o que significa que pode copiar ficheiros para sessões que estão ligadas a computadores remotos, copy-Item (incluindo computadores que executem [servidor Nano](https://blogs.technet.com/b/windowsserver/archive/2015/04/08/microsoft-announces-nano-server-for-modern-apps-and-cloud.aspx), e não tem, portanto, nenhuma outra interface). Para copiar arquivos, especificar os IDs de PSSession como o valor dos parâmetros - FromSession e - ToSession novo e adicione - caminho de e - de destino para especificar o caminho de origem e de destino, respectivamente. Por exemplo, Copy-Item-c: de caminho\\MyFile - ToSession $s-destino d:\\destinationFolder.
- Transcrição de Windows PowerShell foi melhorada para aplicar a todos os aplicativos de hospedagem (por exemplo, o Windows PowerShell ISE), além do host de console (**powershell.exe**). Opções de transcrição (incluindo a ativar uma transcrição de todo o sistema) podem ser configuradas, permitindo que o **ativar o PowerShell transcrição** definição de política de grupo, encontrada no administrativos componentes de modelos/Windows/Windows PowerShell.
- Um novo recurso de rastreamento detalhadas script permite-lhe ativar o controlo detalhado e análise de utilização de criação de scripts de Windows PowerShell num sistema. Depois de ativar o rastreio de detalhado de script, o Windows PowerShell regista todos os blocos de script para o registo de eventos de rastreio eventos para Windows (ETW), **Microsoft-Windows-PowerShell/Operational**.
- A partir do Windows PowerShell 5.0, novos cmdlets de sintaxe de mensagem criptográfica suportam a encriptação e desencriptação de conteúdo com o formato de padrão IETF para proteger criptograficamente mensagens conforme documentado [RFC5652](https://tools.ietf.org/html/rfc5652). Os cmdlets Get-CmsMessage, proteger CmsMessage e Unprotect-CmsMessage foram adicionados para o [Microsoft.PowerShell.Security](https://technet.microsoft.com/library/hh849807.aspx) módulo.
- Novos cmdlets no [Utility](https://technet.microsoft.com/library/hh849958.aspx) módulo, Get-Runspace, espaço de execução de depuração, Get-RunspaceDebug, Enable RunspaceDebug e Disable-RunspaceDebug, permitem-lhe definir as opções de depuração num espaço de execução e o início e fim depuração num espaço de execução. Para depuração arbitrários espaços de execução (ou seja, espaços de execução que não são o espaço de execução padrão para uma consola do Windows PowerShell ou a sessão do Windows PowerShell ISE) o Windows PowerShell permite-lhe definir pontos de interrupção num script e tiver adicionado o script de parar de pontos de interrupção em execução até que pode anexar um depurador para depurar o script de espaço de execução. Foi adicionado suporte de depuração aninhado para espaços de execução arbitrários para o depurador de script do Windows PowerShell para espaços de execução.
- Foi adicionado um novo cmdlet de formato hexadecimal para o [Utility](https://technet.microsoft.com/library/hh849958.aspx) módulo. Formato hexadecimal permite-lhe ver o texto ou dados binários em formato hexadecimal.
- Foram adicionados cmdlets Get-Clipboard e Set-área de transferência para o [Utility](https://technet.microsoft.com/library/hh849958.aspx) módulo; eles facilitam a transferência de conteúdo de e para uma sessão do Windows PowerShell. Os cmdlets de área de transferência suporta imagens, arquivos de áudio, listas de ficheiro e texto.
- Foi adicionado um novo cmdlet, Clear-RecycleBin, para o [Management](https://technet.microsoft.com/library/hh849827(v=wps.640).aspx) módulo; este cmdlet esvazia a Reciclagem de Discretização para uma unidade fixa, o que inclui unidades externas. Por predefinição, lhe for pedido para confirmar se um comando de Clear-RecycleBin, porque a propriedade ConfirmImpact do cmdlet está definida como ConfirmImpact.High.
- Um novo cmdlet, New-TemporaryFile, permite-lhe criar um arquivo temporário como parte do processamento de scripts. Por predefinição, o novo ficheiro temporário é criado na ```C:\Users\<user name>\AppData\Local\Temp```.
- O Out, Add-Content e cmdlets Set-Content tem agora um novo parâmetro - NoNewline, que omite uma nova linha após a saída.
- O cmdlet New-Guid aproveita a classe Guid do .NET Framework para gerar um GUID, útil quando estiver escrevendo scripts ou recursos de DSC.
- Uma vez que as informações de versão do ficheiro podem ser enganosos, particularmente depois de um ficheiro for corrigido, novas propriedades de script de FileVersionRaw e ProductVersionRaw estão disponíveis para objetos FileInfo. Por exemplo, pode executar o seguinte comando para apresentar os valores dessas propriedades para powershell.exe, onde o $pid contém o ID de processo para uma sessão de execução do Windows PowerShell:  ```Get-Process -Id $pid -FileVersionInfo | Format-List *version* -Force```
- Novos cmdlets Enter PSHostProcess e Exit PSHostProcess permitem depurar scripts do Windows PowerShell em processos separados do processo atual que está a executar na consola do Windows PowerShell. Execute o Enter-PSHostProcess para introduzir ou anexar a um ID de processo específico e, em seguida, execute Get-Runspace para devolver os espaços de execução dentro do processo do Active Directory. Execute Exit-PSHostProcess para anular a exposição do processo, quando tiver concluído o script no processo de depuração.
- Foi adicionado um novo cmdlet de depurador de espera para o [Utility](https://technet.microsoft.com/library/hh849958.aspx) módulo. Pode executar o depurador de espera para parar um script no depurador antes de executar a seguinte instrução no script.
- O depurador de fluxo de trabalho do Windows PowerShell suporta agora a conclusão do comando ou separador, e pode depurar funções de fluxo de trabalho aninhado. Agora pode premir **Ctrl + Break** para introduzir o depurador num script em execução em sessões locais e remotos e num script de fluxo de trabalho.
- Foi adicionado um cmdlet de depuração-Job para o [Microsoft.PowerShell.Core](https://technet.microsoft.com/library/hh849695.aspx) módulo para depurar scripts de tarefa em execução para o fluxo de trabalho do Windows PowerShell, em segundo plano e tarefas em execução em sessões remotas.
- Foi adicionado um novo Estado, AtBreakpoint, para tarefas do Windows PowerShell. O estado de AtBreakpoint aplica-se quando uma tarefa está a executar um script que inclui o conjunto de pontos de interrupção, e o script atingir um ponto de interrupção. Quando uma tarefa está parada num ponto de interrupção de depuração, deverá depurá a tarefa executando o cmdlet de tarefa de depuração.
- Windows PowerShell 5.0 implementa o suporte para várias versões de um mesmo módulo do Windows PowerShell na mesma pasta em $PSModulePath. Uma propriedade de RequiredVersion foi adicionada à classe ModuleSpecification para ajudar a que obtém a versão pretendida de um módulo; Esta propriedade é mutuamente exclusiva com a propriedade ModuleVersion. RequiredVersion é agora suportado como parte do valor do parâmetro de Get-Module, FullyQualifiedName Import-Module e Remove-Module cmdlets.
- Agora pode executar a validação de versão do módulo ao executar o cmdlet Test-ModuleManifest.
- Resultados do cmdlet Get-Command apresentam agora uma coluna de versão; foi adicionada uma nova propriedade de versão para a classe CommandInfo. Get-Command apresenta os comandos de várias versões do módulo do mesmo. A propriedade de versão também faz parte de classes derivadas de CmdletInfo: CmdletInfo e ApplicationInfo.
- Get-Command tem um novo parâmetro, - ShowCommandInfo, que retorna informações ShowCommand como PSObjects. Essa é uma funcionalidade especialmente útil para quando o comando Show é executado no Windows PowerShell ISE ao utilizar a comunicação remota do Windows PowerShell. O parâmetro - ShowCommandInfo substitui a função de Get-SerializedCommand existente no módulo Utility, mas o script Get-SerializedCommand ainda está disponível para oferecer suporte a scripts de nível inferior.
- Um novo cmdlet Get-ItemPropertyValue permite-lhe obter o valor de uma propriedade sem usar a notação de ponto. Por exemplo, em versões mais antigas do Windows PowerShell, pode executar o seguinte comando para obter o valor da propriedade da chave do registo de PowerShellEngine Base do aplicativo: **(Get-ItemProperty-caminho HKLM:\\SOFTWARE\\Microsoft\\PowerShell\\3\\PowerShellEngine-nome ApplicationBase como). ApplicationBase como**. A partir do Windows PowerShell 5.0, pode executar **Get ItemPropertyValue-caminho HKLM:\\SOFTWARE\\Microsoft\\PowerShell\\3\\PowerShellEngine-ApplicationBase como do nome** .
- Agora, a consola do Windows PowerShell utiliza sintaxe de cores, assim como no ISE do Windows PowerShell.
- Um novo módulo NetworkSwitch contém cmdlets que permitem-lhe aplicar o comutador, LAN virtual (VLAN) e básica configuração de porta do comutador de rede de camada 2 a comutadores de rede com logótipo de certificação do Windows Server 2012 R2.
- Foi adicionado o parâmetro FullyQualifiedName para cmdlets Import-Module e Remove-Module, para suportar a armazenar várias versões de um módulo único.
- Save-Help, Update-Help, Import-PSSession, Export-PSSession e Get-Command tem um novo parâmetro, FullyQualifiedModule, do tipo ModuleSpecification. Adicione este parâmetro para especificar um módulo pelo nome totalmente qualificado.
- O valor de **$PSVersionTable.PSVersion** foi atualizada para 5.0.
- WMF 5.0 (PowerShell 5.0) inclui a **Pester** módulo.  Pester é uma unidade de estrutura de testes para o PowerShell. Ele fornece alguns simples de usar as palavras-chave que lhe permite criar testes para seus scripts.

### <a name="new-features-in-windows-powershell-desired-state-configuration"></a>Novos recursos do Windows PowerShell Desired State Configuration

- Aprimoramentos de linguagem do Windows PowerShell permitem-lhe definir os recursos do Windows PowerShell Desired State Configuration (DSC) através da utilização de classes. Import-DscResource agora é uma verdadeira palavra-chave dynamic; Windows PowerShell analisa o módulo de raiz do módulo especificado, pesquisa de classes que contêm o atributo DscResource. Agora, pode utilizar classes para definir os recursos de DSC, no qual não é necessária um ficheiro MOF nem uma subpasta DSCResource na pasta do módulo. Um arquivo de módulo do Windows PowerShell pode conter várias classes de recursos de DSC.
- Foi adicionado um novo parâmetro, ThrottleLimit, para os seguintes cmdlets no módulo PSDesiredStateConfiguration. Adicione o parâmetro de ThrottleLimit para especificar o número de computadores de destino ou dispositivos nos quais pretende que o comando para trabalhar ao mesmo tempo.
  - Get-DscConfiguration
  - Get-DscConfigurationStatus
  - Get-DscLocalConfigurationManager
  - Restore-DscConfiguration
  - Test-DscConfiguration
  - Compare-DscConfiguration
  - Publish-DscConfiguration
  - Set-DscLocalConfigurationManager
  - Start-DscConfiguration
  - Update-DscConfiguration
- Com centralizado DSC relatório de erros, informações de erro avançadas não são apenas registadas no caso de log, mas podem ser enviadas para um local central para análise posterior. Pode usar esse local central para armazenar os erros de configuração de DSC que aconteceram para qualquer servidor no seu ambiente. Depois do servidor de relatórios é definido no meta-configuração, todos os erros são enviados para o servidor de relatório e, em seguida, armazenados numa base de dados. Pode configurar esta funcionalidade, independentemente de estar ou não um nó de destino está configurado para solicitar configurações a partir de um servidor de solicitação.
- Melhorias ao ISE do Windows PowerShell facilitam a criação de recursos de DSC. Pode agora fazer o seguinte.
  - Listar todos os recursos de DSC dentro de um **configuration** ou **nó** bloco ao introduzir **Ctrl + espaço** numa linha em branco dentro do bloco de.
  - Conclusão automática das propriedades de recursos a **enumeração** tipo.
  - Conclusão automática no **DependsOn** propriedade de recursos de DSC, com base em outras instâncias de recurso na configuração.
  - Conclusão do separador melhorada de valores de propriedade de recurso.
- Um utilizador pode agora executar um recurso num conjunto especificado de credenciais ao adicionar o **PSDscRunAsCredential** de atributo a um bloco de nó. Por exemplo, PSDscRunAsCredential = Get-Credential Contoso\\DscUser. Essa funcionalidade é útil para a criação de configurações que executam o Windows Installer e programas de instalação do executáveis, acessar o ramo do registo de por utilizador ou executam outras tarefas fora do contexto de utilizador atual.
- foi adicionado suporte de (baseados em x86) de 32 bits para o **configuração** palavra-chave.
- Windows PowerShell inclui agora suporte para ajuda personalizada para configurações de DSC, definidas pela adição de \[CmdletBinding()] para a função de configuração gerada.
- Um novo **dsclocalconfigurationmanager para** atributo designa um bloco de configuração como uma meta-configuração, que é utilizada para configurar o Gestor de configuração de Local de DSC. Este atributo restringe uma configuração para que contém apenas os itens que configurar o Gestor de configuração de Local de DSC. Durante o processamento, esta configuração gera um \*. ficheiro de meta.mof que, ao executar o cmdlet Set-dsclocalconfigurationmanager para, em seguida, é enviado para os nós de destino apropriado.
- Configurações parciais agora são permitidas no Windows PowerShell 5.0. Pode entregar documentos de configuração para um nó em fragmentos. Para um nó receber vários fragmentos de um documento de configuração, Gestor de configuração de Local do nó deve primeiro configurar para especificar os fragmentos esperados
- Sincronização de computador entre as novidades no DSC no Windows PowerShell 5.0. Ao utilizar o WaitFor incorporada\* recursos (**WaitForAll**, **WaitForAny**, e **WaitForSome**), pode agora especificar dependências entre computadores durante a configuração é executado, sem orquestrações externas. Estes recursos fornecem a sincronização de nó para nó através de ligações de CIM através do protocolo WS-Man. Uma configuração pode aguardar por Estado de recurso específico de outro computador alterar.
- Apenas suficiente administração (JEA), um novo recurso de segurança de delegação, tira partido do DSC e espaços de execução do PowerShell de Windows restrita para ajudar as empresas a proteger contra perda de dados ou o comprometimento por funcionários, seja intencional ou não intencional. Para obter mais informações sobre JEA, incluindo onde pode transferir o recurso de xJEA DSC, veja [administração Just Enough, passo a passo](https://blogs.technet.com/b/privatecloud/archive/2014/05/14/just-enough-administration-step-by-step.aspx).
- Foram adicionados os seguintes novos cmdlets para o módulo de PSDesiredStateConfiguration.
  - Um novo cmdlet Get-DscConfigurationStatus obtém informações de alto nível sobre o estado de configuração a partir de um nó de destino. Pode obter o estado da última ou de todas as configurações.
  - Um novo cmdlet Compare-dscconfiguration para compara uma configuração especificada com o estado real de um ou mais nós de destino.
  - Um novo cmdlet Publish-dscconfiguration para copia um ficheiro MOF de configuração para um nó de destino, mas não se aplica a configuração. A configuração é aplicada durante o próximo passo de consistência, ou ao executar o cmdlet Update-dscconfiguration para.
  - Um novo cmdlet Test-dscconfiguration para permite-lhe verificar se uma configuração resultante corresponde da configuração pretendida, retornar True se a configuração de coincidir com a configuração pretendida, ou FALSO se a configuração real não corresponde a pretendido configuração.
  - Um novo cmdlet Update-dscconfiguration para força uma configuração para serem processados. Se o Gestor de configuração Local estiver no modo de solicitação, o cmdlet obtém a configuração do servidor de solicitação antes de aplicá-lo.

### <a name="new-features-in-windows-powershell-ise"></a>Novos recursos do Windows PowerShell ISE

- Agora pode editar scripts remotos do Windows PowerShell e arquivos numa cópia local do Windows PowerShell ISE, ao executar Enter-PSSession para iniciar uma sessão remota no computador que está armazenando os arquivos de que pretende editar e, em seguida, executar **PSEdit \<caminho e nome de ficheiro no computador remoto\>**. Esta funcionalidade facilita a edição ficheiros do Windows PowerShell que são armazenados na opção de instalação Server Core do Windows Server, onde não é possível executar o Windows PowerShell ISE.
- O cmdlet Start-Transcript é agora suportado no ISE do Windows PowerShell.
- Agora pode depurar scripts remotos no ISE do Windows PowerShell.
- Um novo comando de menu, **interromper todos os** (Ctrl + N), divide no depurador para scripts locais e remotamente em execução.

### <a name="new-features-in-windows-powershell-web-services-management-odata-iis-extension"></a>Novos recursos do Windows PowerShell Web Services (extensão de IIS de OData de gestão)

- A partir do Windows PowerShell 5.0, pode gerar um conjunto de cmdlets do Windows PowerShell com base na funcionalidade exposta por um determinado ponto de final de OData, executando o cmdlet Export-ODataEndpointProxy, encontrado no novo [ Microsoft.PowerShell.OdataUtils](https://technet.microsoft.com/library/dn818507(v=wps.640).aspx) módulo.

### <a name="notable-bug-fixes-in-windows-powershell-50"></a>Correções de erros importantes no Windows PowerShell 5.0

- Windows PowerShell 5.0 inclui uma nova implementação de COM, que oferece melhorias de desempenho significativas quando estiver a trabalhar com objetos COM. Para uma demonstração em vídeo do efeito, consulte [Com_Perf_Improvements](https://1drv.ms/1qu3UPZ).
- Foram efetuadas melhorias de desempenho significativas para a conclusão de separador primeiro numa sessão do Windows PowerShell, reduzindo o tempo de conclusão de separador por aproximadamente 500 ms.

## <a name="new-features-in-windows-powershell-40"></a>Novos recursos do Windows PowerShell 4.0

Windows PowerShell 4.0 é compatível. Cmdlets, fornecedores, módulos, snap-ins, scripts, funções e perfis que foram concebidos para o Windows PowerShell 3.0 e o Windows PowerShell 2.0 funcionam no Windows PowerShell 4.0 sem alterações.

Windows PowerShell 4.0 está instalado por padrão no Windows 8.1 e Windows Server 2012 R2. Para instalar o Windows PowerShell 4.0 no Windows 7 com SP1 ou Windows Server 2008 R2, transfira e instale [Windows Management Framework 4.0](https://www.microsoft.com/download/details.aspx?id=40855). Certifique-se de que leia os detalhes de download e todos os requisitos de sistema, de cumprir antes de instalar o Windows Management Framework 4.0.

- [Novos recursos do Windows PowerShell](#new-features-in-windows-powershell-1)
- [Novos recursos no Windows PowerShell Integrated Scripting Environment (ISE)](#new-features-in-windows-powershell-integrated-scripting-environment-ise)
- [Novos recursos do fluxo de trabalho do Windows PowerShell](#new-features-in-windows-powershell-workflow)
- [Novos recursos nos serviços de Web do Windows PowerShell](#new-features-in-windows-powershell-web-services)
- [Novos recursos do Windows PowerShell Web Access](#new-features-in-windows-powershell-web-access)
- [Correções de erros importantes no Windows PowerShell 4.0](#notable-bug-fixes-in-windows-powershell-40)

Windows PowerShell 4.0 inclui as seguintes novas funcionalidades.

### <a name="a-namenew-features-in-windows-powershell-1-new-features-in-windows-powershell"></a><a name="new-features-in-windows-powershell-1" />Novos recursos do Windows PowerShell

- **Windows PowerShell Desired State Configuration** (DSC) é um novo sistema de gerenciamento no Windows PowerShell 4.0, que permite a implementação e gestão de dados de configuração de serviços de software e o ambiente em que estes serviços são executados. Para obter mais informações sobre o DSC, veja [introdução ao Windows PowerShell Desired State Configuration](https://technet.microsoft.com/library/c134aa32-b085-4656-9a89-955d8ff768d0).
- **Save-Help** agora, vamos guardar ajuda para módulos que são instaladas em computadores remotos. Pode utilizar Save-Help para transferir o módulo ajuda a partir de um cliente ligado à Internet (em que nem todos os módulos para o qual pretende obter ajuda são necessariamente instalados) e, em seguida, copie a ajuda guardada para uma pasta remota partilhada ou um computador remoto que não tem a Internet acesso.
- O depurador do Windows PowerShell foi aprimorado para permitir a depuração dos fluxos de trabalho do Windows PowerShell, bem como scripts que são executadas em computadores remotos. Fluxos de trabalho do Windows PowerShell podem agora ser depurados no nível de script a partir da linha de comandos do Windows PowerShell ou o ISE do Windows PowerShell. Scripts do Windows PowerShell, incluindo fluxos de trabalho de script, podem agora ser depuradas através de sessões remotas. Sessões de depuração remoto é preservado ao longo de sessões remotas do Windows PowerShell que são desligados e, em seguida, mais tarde, ligação restabelecidas.
- R **RunNow** parâmetro para **Register-ScheduledJob** e **Set-ScheduledJob** elimina a necessidade de definir uma data de início de imediato e a hora para tarefas utilizando o **Acionador** parâmetro.
- **Invoke-RestMethod** e **Invoke-WebRequest** agora permitem que defina todos os cabeçalhos ao utilizar o parâmetro de cabeçalhos. Embora este parâmetro sempre tenha existido anteriormente, era um dos vários parâmetros para os cmdlets da web que resultaram em erros ou exceções.
- **Get-Module** tem um novo parâmetro **FullyQualifiedName**, do tipo **ModuleSpecification\[]**. O **FullyQualifiedName** parâmetro de Get-Module agora permite-lhe especificar um módulo com o nome do módulo, versão e, opcionalmente, respetivo GUID.
- É a predefinição da política de execução no Windows Server 2012 R2 **RemoteSigned**. No Windows 8.1, não há nenhuma alteração de configuração em default.
- Invocação de método utilizando nomes de método dinâmico a partir do Windows PowerShell 4.0, é suportada. Pode utilizar uma variável para armazenar um nome de método e, em seguida, invoque o método dinamicamente ao chamar a variável.
- Tarefas de fluxo de trabalho assíncrono já não são eliminadas quando o período de tempo limite que é especificado pela **PSElapsedTimeoutSec** parâmetro comum de fluxo de trabalho tiver sido decorrido.
- Um novo parâmetro **RepeatIndefinitely**, foi adicionada para o **New-JobTrigger** e **Set-JobTrigger** cmdlets. Isso elimina a necessidade de especificar um **TimeSpan.MaxValue** valor para o **RepetitionDuration** parâmetro para executar uma tarefa agendada repetidamente durante um período indefinido.
- R **Passthru** parâmetro foi adicionado para o **Enable-JobTrigger** e **Disable-JobTrigger** cmdlets. O parâmetro Passthru apresenta todos os objetos que são criados ou modificados pelo seu comando.
- Os nomes de parâmetro para especificar um grupo de trabalho do **Add-Computer** e **Remove-Computer** cmdlets agora são consistentes. Ambos os cmdlets agora utilizar o parâmetro **WorkgroupName**.
- Um novo parâmetro comum, **PipelineVariable**, foi adicionado. PipelineVariable permite-lhe guardar os resultados de um comando de pipe (ou parte de um comando de pipe) como uma variável que pode ser transmitida o resto do pipeline.
- Coleção de filtrar através de uma sintaxe de método é agora suportada. Isso significa que agora pode filtrar uma coleção de objetos, utilizando uma sintaxe simplificada, semelhante de Where() ou Where-Object, formatados como uma chamada de método. Segue-se um exemplo: (Get-Process).where({$_.Name -match 'powershell'})
- O **Get-Process** cmdlet tem um novo parâmetro, **IncludeUserName**.
- Um novo cmdlet **Get-FileHash**, que devolve um valor de hash de ficheiro em um dos vários formatos para um ficheiro especificado, foi adicionado.
- No Windows PowerShell 4.0, se um módulo utiliza a **DefaultCommandPrefix** chave em seu manifesto, ou se o utilizador importa um módulo com o **prefixo** parâmetro, o **ExportedCommands**propriedade do módulo mostra os comandos no módulo com o prefixo. Quando executa os comandos, utilizando a sintaxe qualificado do módulo, ModuleName\\CommandName, os nomes de comando tem de incluir o prefixo.
- O valor de **$PSVersionTable.PSVersion** foi atualizada para 4.0.
- **WHERE()** operador comportamento foi alterado. `Collection.Where('property -match name')` abertos ao recebimento de uma expressão de cadeia de caracteres no formato `"Property -CompareOperator Value"` já não é suportada. No entanto, o **Where()** operador aceita expressões de cadeia de caracteres no formato de um scriptblock; isso ainda é suportado.

### <a name="new-features-in-windows-powershell-integrated-scripting-environment-ise"></a>Novos recursos no Windows PowerShell Integrated Scripting Environment (ISE)

- ISE do Windows PowerShell suporta a depuração de fluxo de trabalho do Windows PowerShell e a depuração remota de script.
- Foi adicionado suporte ao IntelliSense para fornecedores de Windows PowerShell Desired State Configuration e as configurações.

### <a name="new-features-in-windows-powershell-workflow"></a>Novos recursos do fluxo de trabalho do Windows PowerShell

- Foi adicionado suporte para uma nova **PipelineVariable** parâmetro comum no contexto de pipelines iterativas, como os utilizados pelo System Center Orchestrator; ou seja, pipelines que são executados comandos simplesmente à esquerda para a direita, em oposição a intercaladas a execução com a transmissão em fluxo.
- Enlace de parâmetro foi aprimorado significativamente para trabalhar fora de cenários de conclusão de separador, tal como com os comandos que não existem no espaço de execução atual.
- Foi adicionado suporte para atividades de contentor personalizado para o fluxo de trabalho do Windows PowerShell. Se um parâmetro de atividade é dos tipos **atividade**, **atividade\[]** (ou é uma coleção genérica de atividades) e o utilizador tiver fornecido um bloco de script como um argumento, em seguida, o Windows PowerShell Fluxo de trabalho converte o bloco de scripts em XAML, tal como acontece com a compilação de script-para-fluxo de trabalho normal do Windows PowerShell.
- Após uma pane, o fluxo de trabalho do Windows PowerShell volta automaticamente para os nós geridos.
- É agora possível limitar **Foreach-Parallel** instruções de atividade, utilizando o **ThrottleLimit** propriedade.
- O **ErrorAction** parâmetro comum tem um novo valor válido, **suspender**, que é exclusivamente para fluxos de trabalho.
- Um ponto de extremidade do fluxo de trabalho agora fecha automaticamente se existirem não existem sessões ativas, não existem tarefas em curso e não existirem tarefas pendentes. Esta funcionalidade conserve a recursos no computador que está a agir como servidor de fluxo de trabalho, quando as condições de fecho automático tiverem sido cumpridas.

### <a name="new-features-in-windows-powershell-web-services"></a>Novos recursos nos serviços de Web do Windows PowerShell

- Quando ocorre um erro no Windows PowerShell Web Services (PSWS, também denominado OData IIS extensão de gestão), enquanto um cmdlet está em execução, as mensagens são devolvidas ao chamador de erro mais detalhada. Além disso, os códigos de erro siga [diretrizes de código de erro do Windows Azure REST API](https://msdn.microsoft.com/library/windowsazure/dd179357.aspx).
- Um ponto de extremidade pode agora definir a versão de API, bem como impor a utilização de uma versão de API específica. Sempre que ocorre a correspondência de versão entre cliente e servidor, são apresentados erros para o cliente e o servidor.
- Gestão do esquema de expedição foi simplificado ao gerar automaticamente os valores para quaisquer campos em falta no esquema. Geração ocorre, como um ponto de partida útil, mesmo que o esquema de expedição não existe.
- Tipo de processar em PSWS foi melhorado para suportar os tipos que utilizem um construtor diferente do que o construtor padrão, por se comportando de forma semelhante da **PSTypeConverter** no Windows PowerShell. Isto permite-lhe utilizar tipos complexos com PSWS.
- Agora, PSWS permite expandir uma instância associada ao executar uma consulta. Para obter conteúdo binário maior (como imagens, vídeos ou áudio), o custo de transferência é significativo e é melhor transferir dados binários sem codificação. PSWS utiliza fluxos de recursos com o nome para a transferência sem codificação. A sequência de recursos com o nome é uma propriedade de uma entidade do **Edm.Stream** tipo. Cada sequência de recursos com o nome tem um URI separado para obter ou ATUALIZAR operações.
- Ações de OData agora fornecem um mecanismo para invocar não CRUD (Create, Read, Update e Delete) métodos num recurso. Pode invocar uma ação Enviar um pedido de HTTP POST para o URI que é definido para a ação. Os parâmetros para a ação são definidos no corpo da solicitação POST.
- Para ser consistente com diretrizes do Windows Azure, todos os URLs devem ser simplificados. Uma alteração incluída no **chave como segmento** permite únicas chaves sejam representados como segmentos. Tenha em atenção de que referências que utilizam vários valores de chave exigem separados por vírgulas de valores na notação aninhamentos, como antes.
- Antes desta versão do PSWS, o só a maneira de executar a criação, atualização ou eliminação de operações foi invocar o Post, Put ou eliminar nos recursos de nível superior. Novos nesta versão do PSWS, operações de recursos contidos permitem aos utilizadores obter os mesmos resultados ao atingir o mesmo recurso menos diretamente, a aproximar-se como se fossem contidos estes recursos.

### <a name="new-features-in-windows-powershell-web-access"></a>Novos recursos do Windows PowerShell Web Access

- Pode desligar do e voltar a ligar às sessões existentes na consola do Windows PowerShell Web Access e baseado na web. R **guardar** botão na consola baseada na web permite-lhe desligar a partir de uma sessão sem eliminá-lo e voltar a ligar à sessão de outra vez.
- Parâmetros predefinidos podem ser exibidos na página de início de sessão. Para apresentar os parâmetros predefinidos, configure valores para todas as definições apresentadas no **definições de ligação opcionais** área da página início de sessão num ficheiro denominado **Web. config**. Pode utilizar o **Web. config** ficheiro para configurar todas as definições de ligação opcionais, exceto um conjunto de segundo ou alternativo de credenciais.
- No Windows Server 2012 R2, pode gerir remotamente as regras de autorização para o Windows PowerShell Web Access. O **Add-PswaAuthorizationRule** e **Test-PswaAuthorizationRule** cmdlets agora incluem um parâmetro Credential que permite aos administradores gerir regras de autorização de um computador remoto ou num Sessão do Windows PowerShell Web Access.
- Agora pode ter várias sessões do Windows PowerShell Web Access numa sessão de browser único através de um novo separador do browser para cada sessão. Já não terá de abrir uma nova sessão de browser para ligar a uma nova sessão na consola do Windows PowerShell baseada na web.

### <a name="notable-bug-fixes-in-windows-powershell-40"></a>Correções de erros importantes no Windows PowerShell 4.0

- **Get-Counter** agora pode retornar a contadores que contêm um apóstrofe em francês edições do Windows.
- Agora, pode ver o **GetType** método em objetos de serialização anulados.
- **#Requires** instruções agora permitir que os utilizadores necessitam de direitos de acesso de administrador, se necessário.
- O **Import-Csv** cmdlet ignora agora linhas em branco.
- Um problema em que o ISE do Windows PowerShell utiliza muita memória quando estiver a executar uma **Invoke-WebRequest** comando foi corrigido.
- **Get-Module** agora apresenta versões do módulo num **versão** coluna.
- Remove-Item - Recurse agora remove itens da subpastas, conforme o esperado.
- R **nome de utilizador** foi adicionada a propriedade **Get-Process** objetos de saída.
- O **Invoke-RestMethod** agora, o cmdlet retorna todos os resultados disponíveis.
- **Adicionar-Member** agora produz efeitos no hashtables, mesmo que as tabelas de hash ainda não tenham sido acedidas.
- **Select-Object - expanda** já não está a falhar ou gera uma exceção se o valor da propriedade é nulo ou estar vazio.
- **Get-Process** agora pode ser usado num pipeline com outros comandos que obtenha o **ComputerName** propriedade de objetos.
- **ConvertTo-Json** e **ConvertFrom-Json** agora pode aceitar termos entre aspas duplas e suas mensagens de erro são agora localizáveis.
- **Get-Job** agora devolve qualquer concluir as tarefas agendadas, mesmo em novas sessões.
- Problemas com montar e desmontar VHDs utilizando o **sistema de ficheiros** fornecedor no Windows PowerShell 4.0 ter sido corrigidos. Windows PowerShell agora é capaz de detetar novas unidades quando estão montadas na mesma sessão.
- Já não terá de carregar explicitamente **ScheduledJob** ou **fluxo de trabalho** módulos para trabalhar com seus tipos de tarefa.
- Foram efetuadas melhorias de desempenho para o processo de importação de fluxos de trabalho que definem fluxos de trabalho aninhados; Este processo agora é mais rápido.

## <a name="new-features-in-windows-powershell-30"></a>Novos recursos do Windows PowerShell 3.0

Windows PowerShell 3.0 inclui as seguintes novas funcionalidades.

- [O fluxo de trabalho do Windows PowerShell](#windows-powershell-workflow)
- [Windows PowerShell Web Access](#windows-powershell-web-access)
- [Novos recursos do Windows PowerShell ISE](#new-windows-powershell-ise-features)
- [Suporte para Microsoft .NET Framework 4.0](#support-for-microsoft-net-framework-4)
- [Suporte para o ambiente de pré-instalação do Windows](#support-for-windows-preinstallation-environment)
- [Sessões desligado](#disconnected-sessions)
- [Conectividade de sessão robusta](#robust-session-connectivity)
- [Sistema de ajuda atualizável](#updatable-help-system)
- [Avançado de Ajuda Online](#enhanced-online-help)
- [Integração de CIM](#cim-integration)
- [Ficheiros de configuração de sessão](#session-configuration-files)
- [Tarefas agendadas e a integração do agendador de tarefas](#scheduled-jobs-and-task-scheduler-integration)
- [Aprimoramentos de linguagem do PowerShell do Windows](#windows-powershell-language-enhancements)
- [Novos Cmdlets de núcleo](#new-core-cmdlets)
- [Melhorias para existente principais Cmdlets e fornecedores](#improvements-to-existing-core-cmdlets-and-providers)
- [Importação do módulo remoto e a deteção](#remote-module-import-and-discovery)
- [Conclusão de tabulação aprimorada](#enhanced-tab-completion)
- [Carregamento automático de módulo](#module-auto-loading)
- [Melhorias na experiência de módulo](#module-experience-improvements)
- [Deteção de comando simplificada](#simplified-command-discovery)
- [A melhoria do registo, o diagnóstico e o suporte de política de grupo](#improved-logging-diagnostics-and-group-policy-support)
- [Formatação e melhorias de saída](#formatting-and-output-improvements)
- [Experiência de anfitrião da consola melhorada](#enhanced-console-host-experience)
- [Novo Cmdlet e alojamento de APIs](#new-cmdlet-and-hosting-apis)
- [Melhorias de desempenho](#performance-improvements)
- [RunAs e suporte de anfitriões partilhado](#runas-and-shared-host-support)
- [Melhorias de manipulação de caráter especial](#special-character-handling-improvements)

### <a name="windows-powershell-workflow"></a>O fluxo de trabalho do Windows PowerShell

O fluxo de trabalho do Windows PowerShell traz o poder do Windows Workflow Foundation para Windows PowerShell. Pode escrever fluxos de trabalho em XAML ou no idioma do Windows PowerShell e executá-los tal como faria a executar um cmdlet. O [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) cmdlet obtém os comandos de fluxo de trabalho e o [Get-Help](https://technet.microsoft.com/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) cmdlet obtém ajuda para fluxos de trabalho.

Fluxos de trabalho são seqüências de atividades de gestão multicomputer que são de longa execução, repetíveis, frequentes, ponto pode ser paralelizada, passível de interrupção, suspendable e reinicializável. Fluxos de trabalho podem ser retomados a partir de uma interrupção intencional ou acidental, como uma falha de rede, um reinício do Windows ou uma falha de energia.

Fluxos de trabalho também são portáteis; eles podem ser exportados como ou importados a partir dos ficheiros XAML. Pode escrever as configurações de sessão personalizadas que permitem que o fluxo de trabalho ou atividades num fluxo de trabalho para ser executado pelos usuários delegados ou subordinados.

Seguem-se os benefícios do fluxo de trabalho do Windows PowerShell

- Automatização de tarefas de longa execução sequenciadas.
- **Monitorização remota de tarefas de longa execução**. Estado e o progresso das atividades estão visíveis em qualquer altura.
- **Gestão multicomputer.** Executar simultaneamente as tarefas como fluxos de trabalho em centenas de nós geridos. O fluxo de trabalho do Windows PowerShell inclui uma biblioteca incorporada dos parâmetros comuns de gestão, como **PSComputerName**, que ativar cenários de gestão de vários computadores.
- **Execução de tarefa única de processos complexos.** Pode combinar scripts relacionados que implementam um cenário ponto-a-ponto completo num único fluxo de trabalho.
- **Persistência.** : um fluxo de trabalho é guardado (ou apontado de verificação) em pontos específicos definidos pelo respetivo autor, para que possa retomar o fluxo de trabalho desde a última tarefa persistente (ou ponto de verificação), em vez de reiniciar o fluxo de trabalho desde o início.
- **Robustez.** Recuperação de falha automatizada. Fluxos de trabalho sobrevivem a reinícios planeados e não planeados. Pode suspender a execução de fluxo de trabalho e, em seguida, retomar o fluxo de trabalho desde o último ponto de persistência. Os autores de fluxo de trabalho podem designar atividades específicas para ser executado novamente em caso de falha num ou mais nós geridos.
- **Capacidade de desligar, ligar novamente e executados em sessões desligados.** Os utilizadores podem ligar e desligar do servidor de fluxo de trabalho, mas o fluxo de trabalho seja executada continuamente. Faça logoff no computador cliente ou reiniciar o computador cliente e monitorizar a execução de fluxo de trabalho a partir de outro computador sem interromper o fluxo de trabalho.
- **Agendamento.** Tarefas de fluxo de trabalho podem ser agendadas como qualquer cmdlet do Windows PowerShell ou o script.
- **Fluxo de trabalho e a limitação de conexão.** Execução de fluxo de trabalho e ligações para nós podem ser otimizadas, que permite cenários de elevada disponibilidade e escalabilidade.

### <a name="windows-powershell-web-access"></a>Windows PowerShell Web Access

Windows PowerShell Web Access é uma funcionalidade do Windows Server 2012 que permite aos utilizadores executar comandos do Windows PowerShell e scripts num console baseado na web. Dispositivos que utilizam a consola baseada na web não necessitam de Windows PowerShell, o software de gestão remota ou as instalações de plug-in do navegador. Tudo o que é necessário é um gateway de acesso do Windows PowerShell Web configurado corretamente e um browser de dispositivo do cliente que suporte a JavaScript e aceite cookies.

Para obter mais informações, consulte [implantar o Windows PowerShell Web Access](https://go.microsoft.com/fwlink/p/?LinkID=221050).

### <a name="new-windows-powershell-ise-features"></a>Novos recursos do Windows PowerShell ISE

Para Windows PowerShell 3.0, Windows PowerShell Integrated Scripting Environment (ISE) tem muitos recursos novos, incluindo IntelliSense, a janela de comando Show, um painel de consola unificada, trechos de código, a correspondência de chaves, expandir-fechar secções, o salvamento automático, itens recentes lista, cópia avançada, cópia de bloco e suporte completo para escrever fluxos de trabalho de script de Windows PowerShell. Para obter mais informações, consulte [about_Windows_PowerShell_ISE [v3]](https://technet.microsoft.com/library/dfa54d47-60c6-4fff-8197-c747e8d411bb).

### <a name="support-for-microsoft-net-framework-4"></a>Suporte para Microsoft .NET Framework 4

Windows PowerShell baseia-se contra o 4.0 de tempo de execução de linguagem comum. Cmdlet, script e autores de fluxo de trabalho podem utilizar as novas classes de Microsoft .NET Framework 4 no Windows PowerShell, com recursos que incluem a compatibilidade de aplicativos e a implementação, a Managed Extensibility Framework, computação paralela, rede, do Windows Communication Foundation e o Windows Workflow Foundation.

### <a name="support-for-windows-preinstallation-environment"></a>Suporte para o ambiente de pré-instalação do Windows

Windows PowerShell 3.0 é um componente opcional do ambiente de pré-instalação do Windows (Windows PE) 4.0 para o Windows 8. Windows PE é um sistema operativo mínimo que inicia um computador sem sistema operativo e prepara-o para a instalação do Windows. Windows PE pode ser utilizado para a partição e formatar os discos rígidos, copie as imagens de disco para um computador e iniciar a configuração do Windows a partir de um compartilhamento de rede. Windows PowerShell 3.0 pode ser utilizado no Windows PE para gerir a implementação, diagnóstico e cenários de recuperação.

### <a name="disconnected-sessions"></a>Sessões desligado

A partir do Windows PowerShell 3.0, persistentes-gerido sessões ("PSSessions") que criou utilizando o cmdlet New-PSSession são guardadas no computador remoto. Já não são dependentes da sessão em que foram criados.

Pode agora desligar a partir de uma sessão sem interromper os comandos que estão em execução na sessão. Pode fechar a sessão e encerrar o computador. Mais tarde, pode voltar a ligar à sessão de uma sessão diferente no mesmo ou num computador diferente.

O **nomedocomputador** parâmetro do [Get-PSSession](https://technet.microsoft.com/library/b2b10531-d0df-4746-b877-e75c09955cb6) cmdlet agora obtém todas as sessões do utilizador que se ligam ao computador, mesmo que eram inicializados numa sessão diferente num computador diferente. Pode ligar-se para as sessões, obter os resultados dos comandos, iniciar novos comandos e, em seguida, encerre a sessão.

Foram adicionados novos cmdlets para suportar a funcionalidade de sessões de desligado, incluindo [Disconnect-PSSession](https://technet.microsoft.com/library/f8f95111-612f-4cba-9098-77904b0473d8), [Connect-PSSession](https://technet.microsoft.com/library/b803dd29-f208-4079-80d4-db04d778f060), e foram adicionadas Receive-PSSession e novos parâmetros para os cmdlets que gerem PSSessions, tais como o **InDisconnectedSession** parâmetro do [Invoke-Command](https://technet.microsoft.com/library/906b4b41-7da8-4330-9363-e7164e5e6970) cmdlet.

A funcionalidade de sessões desligado é suportada apenas quando os computadores em ambos ("cliente") de origem e termina ("server") da ligação de terminação executem o Windows PowerShell 3.0.

### <a name="robust-session-connectivity"></a>Conectividade de sessão robusta

Windows PowerShell 3.0 Deteta perdas inesperadas de conectividade entre o cliente e servidor e tenta restabelecer a conectividade e continuar a execução automaticamente. Se não é possível restabelecer a ligação de cliente-servidor no tempo atribuído, o utilizador é notificado e a sessão é desligada. Durante a tentativa de restabelecer a ligação, o Windows PowerShell fornece comentários contínuos para o usuário.

Se a sessão desligada foi iniciada utilizando o InvokeCommand, o Windows PowerShell cria uma tarefa para a sessão desligada para que seja mais fácil voltar a ligar e retomar a execução.

Esses recursos fornecem uma experiência de comunicação remota mais confiável e recuperáveis e permitir que os usuários realizem tarefas de longa execução que exigem sessões robustos, tais como fluxos de trabalho.

### <a name="updatable-help-system"></a>Sistema de ajuda atualizável

Agora pode baixar os arquivos de ajuda atualizados para os cmdlets nos seus módulos. O [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) cmdlet identifica os ficheiros de ajuda mais recentes, transfere-os partir da Internet, a Desempacote-los, valida e instala-os no diretório específico ao idioma correto para o módulo.

Para utilizar os ficheiros de ajuda atualizada, basta escrever `Get-Help`. Não é necessário reiniciar o Windows ou Windows PowerShell. Para atualizar a ajuda para módulos no diretório $pshome, inicie o Windows PowerShell com a opção "Executar como administrador".

Para suportar utilizadores que não têm acesso à Internet e os utilizadores por trás de firewalls, a nova [Save-Help](https://technet.microsoft.com/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa) cmdlet transfere ficheiros de ajuda para um diretório de sistema de ficheiros, como uma partilha de ficheiros. Os utilizadores, em seguida, podem utilizar o [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) cmdlet para obter os ficheiros de ajuda atualizada da partilha de ficheiros.

Pode utilizar o [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) cmdlet para atualizar a ajuda de ficheiros para todos os ou da interface do Usuário de suporte de módulos específicos em todas as culturas. Pode até mesmo colocar uma [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) comando no seu perfil do Windows PowerShell. Por predefinição, Windows PowerShell transfere os ficheiros de ajuda para um módulo não mais do que uma vez por dia.

Módulos do Windows 8 e Windows Server 2012 não incluir arquivos de ajuda. Para transferir os ficheiros de ajuda mais recentes, escreva `Update-Help`. Para obter mais informações, escreva `Get-Help` (sem parâmetros) ou veja [about_Updatable_Help](https://technet.microsoft.com/library/10bba75c-f4ac-4ca1-bbf3-8f34dd521ffe).

Quando os arquivos da ajuda de um cmdlet não estão instalados no computador, o [Get-Help](https://technet.microsoft.com/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) cmdlet apresenta agora ajuda gerado automaticamente. A ajuda de gerado automaticamente inclui a sintaxe de comando e instruções para utilizar o [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) cmdlet para transferir os ficheiros de ajuda.

Qualquer autor de módulos pode suportar a ajuda Atualizável de mensagens em fila para o módulo. Pode incluir arquivos de ajuda no módulo e utilizar a ajuda Atualizável de mensagens em fila para atualizá-las ou omitir os arquivos da ajuda e utilizar a ajuda Atualizável de mensagens em fila para instalá-los. Para obter mais informações sobre o apoio ajuda Atualizável, consulte [apoio ajuda Atualizável](https://go.microsoft.com/FWLink/?LinkID=242129) no MSDN.

### <a name="enhanced-online-help"></a>Avançado de Ajuda Online

Ajuda online do Windows PowerShell é um recurso valioso para todos os utilizadores, mas é especialmente importante para os utilizadores que não suportam ou não é possível instalar arquivos de ajuda atualizada.

Para obter ajuda online para qualquer cmdlet do Windows PowerShell, escreva:

```
Get-Help <cmdlet-name> -Online
```

Windows PowerShell é aberta a versão online do tópico de ajuda no seu browser de Internet predefinido.

O **Get-Help-Online** funcionalidade no Windows PowerShell 3.0 está agora ainda mais poderosa pois funciona até mesmo quando os arquivos de ajuda para o cmdlet não estão instalados no computador. O **Get-Help-Online** funcionalidade obtém o URI para o tópico de ajuda online da propriedade HelpUri de cmdlets e funções avançadas.

```
PS C:\>(Get-Command Get-ScheduledJob).HelpUri
http://go.microsoft.com/fwlink/?LinkID=223923
```

A partir do Windows PowerShell 3.0, os autores de C# cmdlets pode preencher o **HelpUri** propriedade através da criação de um **HelpUri** atributo na classe cmdlet. Os autores de funções avançadas que podem definir uma **HelpUri** propriedade no **CmdletBinding** atributo. O valor do **HelpUri** propriedade tem de começar com "http" ou "https".

Também pode incluir uma **HelpUri** valor na primeira ligação relacionada de um arquivo de ajuda do cmdlet baseado em XML ou o. Diretiva de ligação de ajuda baseada no comentário numa função.

Para obter mais informações sobre o suporte de ajuda online, consulte [apoio Ajuda Online](/powershell/developer/module/supporting-online-help) do Microsoft Docs.

### <a name="cim-integration"></a>Integração de CIM

Windows PowerShell 3.0 inclui suporte para o modelo CIM (Common Information), que fornece definições comuns de informações de gestão para sistemas, redes, aplicativos e serviços, permitindo-lhes a troca de informações de gestão entre sistemas heterogêneos. Suporte para CIM no Windows PowerShell 3.0, incluindo a capacidade de criar com base nas classes CIM novas ou existentes, comandos de cmdlets do Windows PowerShell com base na definição de cmdlet arquivos XML, suporte para CIM .NET Framework. API, os cmdlets de gestão de CIM e provedores de WMI 2.0.

### <a name="session-configuration-files"></a>Ficheiros de configuração de sessão

A partir do Windows PowerShell 3.0, pode criar uma configuração de sessão personalizada utilizando um ficheiro. O ficheiro de configuração de novo sessão permite-lhe determinar o ambiente de sessões que utilizam a configuração de sessão, incluindo quais módulos, scripts, e os arquivos de formato são carregados em sessões, cmdlets e idioma elementos os utilizadores que podem utilizar, quais módulos e scripts podem executar e quais variáveis podem ver.

Pode criar uma sessão em que os utilizadores só podem executar os cmdlets num módulo específico ou uma sessão em que os utilizadores têm linguagem completa, o acesso a todos os módulos e o acesso a scripts que executem tarefas avançadas.

Nas versões anteriores do Windows PowerShell, o controle nesse nível estava disponível apenas para aqueles que poderia escrever um C# programa ou um script de inicialização complexa. Agora, qualquer membro do grupo Administradores no computador pode personalizar uma configuração de sessão utilizando um ficheiro de configuração.

Para criar um ficheiro de configuração de sessão, utilize o [New-PSSessionConfigurationFile](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866) cmdlet. Para aplicar o ficheiro de configuração de sessão a uma configuração de sessão, utilize o [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) ou [conjunto-PSSessionConfiguration](https://technet.microsoft.com/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) cmdlets.

Para obter mais informações, consulte [about_Session_Configuration_Files](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configuration_files?view=powershell-5.0) e [New-PSSessionConfigurationFile](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866).

### <a name="scheduled-jobs-and-task-scheduler-integration"></a>Tarefas agendadas e a integração do agendador de tarefas

Agora pode agendar tarefas do Windows PowerShell em segundo plano e geri-los no Windows PowerShell e no agendador de tarefas.

Tarefas do PowerShell de Windows agendada são uma mistura útil de tarefas do Windows PowerShell em segundo plano e tarefas do agendador de tarefas.

Assim como tarefas do Windows PowerShell em segundo plano, as tarefas agendadas são executados assincronicamente em segundo plano. Instâncias de tarefas agendadas que tem concluído podem ser geridas, utilizando os cmdlets de tarefa, tal como [tarefa de início](https://technet.microsoft.com/library/2bc04935-0deb-4ec0-b856-d7290cca6442) e [Get-Job](https://technet.microsoft.com/library/1352c534-7193-46ca-9ab1-0c5219a661ad).

Como tarefas do agendador de tarefas, pode executar as tarefas agendadas, com base numa agenda recorrente ou uma única vez, ou em resposta a uma ação ou um evento. Pode ver e gerir tarefas agendadas no agendador de tarefas, ativar e desativá-las conforme necessário, executá-las ou utilizá-los como modelos e definir as condições sob as quais as tarefas serem iniciadas.

Além disso, as tarefas agendadas são fornecidos com um conjunto personalizado de cmdlets para a respetiva gestão. Os cmdlets permitem-lhe criar, editar, gerir, desativar e volte a ativar as tarefas agendadas, criar acionadores de tarefa agendada e definir as opções de tarefa agendada.

Para obter mais informações sobre as tarefas agendadas, consulte [about_Scheduled_Jobs](https://technet.microsoft.com/library/3b546629-703c-4939-b44f-52dd567bce92).

### <a name="windows-powershell-language-enhancements"></a>Aprimoramentos de linguagem do PowerShell do Windows

Windows PowerShell 3.0 inclui muitos recursos que são projetados para facilitar a sua linguagem, mais simples e mais fáceis de usar e para evitar erros comuns. Os melhoramentos incluem propriedades de enumeração, contagem e comprimento de propriedade em objetos escalares, novos operadores de redirecionamento, o modificador do âmbito $Using, formatação de script automático, variável e flexível de PSItem, atributos de variáveis, atributo simplificada argumentos, nomes de comandos numérico, o operador de análise de parada, splatting do matriz melhorada, novos operadores bit, dicionários ordenados, PSCustomObject conversão e aprimorada ajuda baseada no comentário.

### <a name="new-core-cmdlets"></a>Novos Cmdlets de núcleo

Novos cmdlets foram adicionados à instalação do Windows PowerShell Core, incluindo cmdlets para gerir as tarefas agendadas, sessões de desligado, integração de CIM e o sistema de ajuda Atualizável.

|||
|-|-|
|Add-JobTrigger|New-JobTrigger|
|Connect-PSSession|New-PSSessionConfigurationFile|
|ConvertFrom-Json|New-PSTransportOption|
|ConvertTo-Json|New-PSWorkflowExecutionOption|
|Disable-JobTrigger|New-PSWorkflowSession|
|Disable-ScheduledJob|New-ScheduledJobOption|
|Disconnect-PSSession|New-WinEvent|
|Enable-JobTrigger|Receive-PSSession|
|Enable-ScheduledJob|Register-CimIndicationEvent|
|Get-CimAssociatedInstance|Register-ScheduledJob|
|Get-CimClass|Remove-CimInstance|
|Get-CimInstance|Remove-CimSession|
|Get-CimSession|Remove-TypeData|
|Get-ControlPanelItem|Rename-Computer|
|Get-IseSnippet|Resume-Job|
|Get-JobTrigger|Save-Help|
|Get-ScheduledJob|Set-CimInstance|
|Get-ScheduledJobOption|Set-JobTrigger|
|Get-TypeData|Set-ScheduledJob|
|Import-IseSnippet|Set-ScheduledJobOption|
|Invoke-AsWorkflow|Comando show|
|Invoke-CimMethod|Show-ControlPanelItem|
|Invoke-RestMethod|Suspend-Job|
|Invoke-WebRequest|Test-PSSessionConfigurationFile|
|New-CimInstance|Ficheiro de desbloqueio|
|New-CimSession|Unregister-ScheduledJob|
|New-CimSessionOption|Update-Help|
|New-IseSnippet||

### <a name="improvements-to-existing-core-cmdlets-and-providers"></a>Melhorias para existente principais Cmdlets e fornecedores

Windows PowerShell 3.0 inclui novos recursos para cmdlets existentes, incluindo sintaxe simplificada e novos parâmetros para os seguintes cmdlets: Cmdlets de computador, os cmdlets CSV, Get-ChildItem, Get-Command, Get-Content, histórico de Get-objeto de medida, cmdlets de segurança, Select-Object, o Select-String, o caminho de divisão, o processo de início, Tee-Object, ligação de teste, Add-Member e cmdlets do WMI.

Os fornecedores de Windows PowerShell foram também melhoraram significativamente, incluindo suporte de fornecedor de certificados para o gerenciamento de certificados de Secure Socket Layer (SSL) para hospedagem na web, suporte para credenciais, unidades de rede persistente e fluxos de dados alternativo em unidades de sistema de ficheiros.

### <a name="remote-module-import-and-discovery"></a>Importação do módulo remoto e a deteção

Windows PowerShell 3.0 estende a deteção de módulo, importar e capacidades de comunicação remota implícita em computadores remotos. Os cmdlets do módulo obter módulos em computadores remotos e importe os módulos no computador local ou remoto ao utilizar a comunicação remota do Windows PowerShell. Novo suporte de sessão CIM permite-lhe utilizar o CIM e o WMI para gerir computadores não-Windows através da importação de comandos no computador local que são executadas implicitamente no computador remoto.

Para obter mais informações, consulte os tópicos de ajuda para o [Get-Module](https://technet.microsoft.com/library/2cccd4c4-9a21-4c77-b691-984ee57242e1) e [Import-Module](https://technet.microsoft.com/library/af616c24-e122-4098-930e-1e3ea2080ade) cmdlets.

### <a name="enhanced-tab-completion"></a>Conclusão de tabulação aprimorada

Conclusão de tabulação na consola do Windows PowerShell agora conclui os nomes dos cmdlets, parâmetros, valores de parâmetros, enumerações, .NET Frameworks tipos, COM objetos, diretórios e muito mais. A funcionalidade de conclusão de separador foi completamente reescrita com base num novo analisador e a árvore de sintaxe abstrata para suportar mais cenários, incluindo árvores de análise dentro da memória e de conclusão de tabulação midline.

### <a name="module-auto-loading"></a>Carregamento automático de módulo

O [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) cmdlet agora obtém todos os cmdlets e funções de todos os módulos instalados no computador, mesmo que o módulo não é importado para a sessão atual.

Quando receber o cmdlet que necessita, pode utilizá-la imediatamente sem importar qualquer módulo. Módulos do Windows PowerShell agora são importados automaticamente quando utiliza qualquer cmdlet no módulo. Já não terá de procurar o módulo e importá-lo para utilizar os seus cmdlets.

Importação automática dos módulos é acionado com o cmdlet num comando, em execução **Get-Command** de um cmdlet sem carateres universais, ou de execução [Get-Help](https://technet.microsoft.com/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) para um cmdlet sem carateres universais.

Pode ativar, desativar e configurar a importação automática de módulos, utilizando o **$PSModuleAutoLoadingPreference** variável de preferência.

Para obter mais informações, consulte [about_Modules](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_modules?view=powershell-5.0), [about_Preference_Variables [v4]](https://technet.microsoft.com/library/31344314-be29-4286-b039-afa5460cbe8b)e os tópicos de ajuda para o [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) e [Import-Module](https://technet.microsoft.com/library/af616c24-e122-4098-930e-1e3ea2080ade) cmdlets.

### <a name="module-experience-improvements"></a>Melhorias na experiência de módulo

Windows PowerShell 3.0 traz o suporte de funcionalidades avançadas para módulos, incluindo as seguintes novas funcionalidades.

1. Registo de módulo de módulos individuais (LogPipelineExecutionDetails) e a nova definição de política de grupo "Ativar no módulo de registo"
2. Expandido objetos de módulo que expõem os valores do manifesto do módulo
3. Novos **ExportedCommands** aninhada de propriedade de módulos, incluindo módulos, que combina os comandos de todos os tipos
4. Deteção melhorada de módulos disponíveis (não importados), incluindo a permitir que o **caminho** e **ListAvailable** parâmetros no mesmo comando
5. Novos **DefaultCommandPrefix** chave nos manifestos de módulo que evita conflitos de nome sem alterar o código do módulo.
6. Melhorada a requisitos de módulo, incluindo os módulos necessários totalmente qualificado com versão e GUID e importação automática de módulos necessários
7. Operação de mais calmos e simplificada do [New-ModuleManifest](https://technet.microsoft.com/library/512adced-f42f-4e88-ba7c-834fc9e5d047) cmdlet.
8. Novos **módulo** parâmetro #Requires
9. Melhorada [Import-Module](https://technet.microsoft.com/library/af616c24-e122-4098-930e-1e3ea2080ade) cmdlet com ambos **MinimumVersion** e **RequiredVersion** parâmetros.

### <a name="simplified-command-discovery"></a>Deteção de comando simplificada

Já não terá de importar todos os módulos para descobrir os comandos disponíveis para a sua sessão. No Windows PowerShell 3.0, o [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) cmdlet obtém todos os comandos de todos os módulos instalados. E, se utilizar um comando, o módulo que exporta o comando é importado automaticamente para a sua sessão.

A nova [comando Show](https://technet.microsoft.com/library/65bba50b-91a8-49d5-80a2-a30fc684ba41) cmdlet foi desenvolvido especialmente para iniciantes. Pode procurar comandos numa janela. Pode ver todos os comandos ou filtrar por módulo, importar um módulo ao clicar num botão, utilize as caixas de texto e listas suspensas para construir um comando válido e, em seguida, copie ou execute o comando sem sair da janela.

### <a name="improved-logging-diagnostics-and-group-policy-support"></a>A melhoria do registo, o diagnóstico e o suporte de política de grupo

Windows PowerShell 3.0 melhora o log e rastreamento de suporte para comandos e módulos com suporte para rastreamento de eventos nos registos do Windows (ETW), um editáveis **LogPipelineExecutionDetails** propriedade de módulos e o "ativar no módulo Grupo de registo"definição de política. Agora pode obter valores de parâmetros de detalhes do registo ao apresentar as propriedades de registo.

### <a name="formatting-and-output-improvements"></a>Formatação e melhorias de saída

Formatação de novos e de saída melhorias melhorar a eficiência de todos os utilizadores do Windows PowerShell. Os melhoramentos incluem o redirecionamento de saída para todos os fluxos, um cmdlet de tipo de atualização aprimorado que adiciona a tipos dinamicamente sem ficheiros Format.ps1xml, moldagem do texto na saída, padrão de formatação de propriedades de objetos personalizados, o **PSCustomObject** tipo, melhorado para objetos WMI e objetos heterogêneos e suporte para detetar a sobrecarga de métodos de formatação.

### <a name="enhanced-console-host-experience"></a>Experiência de anfitrião da consola melhorada

O programa de host de console do Windows PowerShell tem novas funcionalidades no Windows PowerShell 3.0, incluindo apartamento de thread único por predefinição. A nova opção "Executar com PowerShell" no Explorador de ficheiros permite-lhe executar scripts numa sessão sem restrições, simplesmente clicando com o. Nova lógica de inicialização do host de console é iniciado mais rápido do Windows PowerShell e novas fontes permitem-lhe personalizar a experiência de janela de consola familiar.

Para obter mais informações, consulte [about_Run_With_PowerShell](https://technet.microsoft.com/library/c9d9ca5f-eff9-4409-be9d-e43b5b4087eb).

### <a name="new-cmdlet-and-hosting-apis"></a>Novo Cmdlet e alojamento de APIs

A nova API de Cmdlet e API de hospedagem incluem a árvore de sintaxe de avançadas pública APIs (AST) e APIs para paginação de pipeline, pipelines aninhados, conclusão de tabulação de conjuntos de espaço de execução, Windows RT, o atributo de cmdlet obsoleto e propriedades de verbo e substantivo do objeto FunctionInfo.

### <a name="performance-improvements"></a>Melhorias de desempenho

Melhorias de desempenho significativas no Windows PowerShell são provenientes do novo analisador de idioma, que está incorporado no dinâmica tempo de execução do dlr (Dynamic Language) no .NET Framework 4., juntamente com a compilação de script de tempo de execução, melhorias de confiabilidade do mecanismo e as alterações para o algoritmo do [Get-ChildItem](https://technet.microsoft.com/library/75cf79bb-4db6-4a67-8c36-3d20754e2190) que melhorar seu desempenho, especialmente quando procurar rede partilha.

### <a name="runas-and-shared-host-support"></a>RunAs e suporte de anfitriões partilhado

Windows PowerShell 3.0 inclui suporte para funcionalidades de RunAs e de anfitriões partilhado.

O *RunAs* funcionalidade, concebida para o fluxo de trabalho do Windows PowerShell, permite que os utilizadores de uma configuração de sessão a criar sessões que são executados com a permissão de uma conta de utilizador partilhadas. Isto permite que os usuários com menos privilégios executar comandos específicos e scripts com permissões de administrador e reduz a necessidade de inclusão de usuários menos sênior do grupo Administradores.

O **SharedHost** funcionalidade permite que vários utilizadores em vários computadores para se ligar a uma sessão de fluxo de trabalho em simultâneo e monitorizar o progresso de um fluxo de trabalho. Os utilizadores podem iniciar um fluxo de trabalho num computador e, em seguida, ligar-se para a sessão de fluxo de trabalho em outro computador sem a desligar a sessão do computador original. Os utilizadores tem de ter as mesmas permissões e estar a utilizar a mesma configuração de sessão. Para obter mais informações, consulte "Em execução um Windows PowerShell Workflow" Introdução ao fluxo de trabalho do Windows PowerShell.

### <a name="special-character-handling-improvements"></a>Melhorias de manipulação de caráter especial

Para melhorar a capacidade do Windows PowerShell 3.0 para interpretar e processa corretamente caracteres especiais, o **LiteralPath** parâmetro, que lida com carateres especiais em caminhos, é válido em quase todos os cmdlets que tenham um  **Caminho** parâmetro, incluindo a nova [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) e [Save-Help](https://technet.microsoft.com/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa) cmdlets. O analisador também inclui uma lógica especial para aperfeiçoar o tratamento do caractere acento grave (\`) e colchetes em nomes de ficheiros e caminhos.

## <a name="see-also"></a>Veja Também

- [about_Windows_PowerShell_5.0](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_powershell_5.0?view=powershell-5.0)
- [Windows PowerShell](https://go.microsoft.com/fwlink/?LinkID=107116)
