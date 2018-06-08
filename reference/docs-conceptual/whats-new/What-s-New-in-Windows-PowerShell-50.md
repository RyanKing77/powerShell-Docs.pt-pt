---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Novidades no Windows PowerShell 5.0
ms.openlocfilehash: f5a27c0541e21b379f88b318cbe09a0344c1b372
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/07/2018
ms.locfileid: "34483190"
---
# <a name="whats-new-in-windows-powershell-50"></a>Novidades no Windows PowerShell 5.0
Windows PowerShell 5.0 inclui funcionalidades novas importantes que expandem a sua utilização, melhoram a usabilidade e permitem controlar e gerir ambientes baseados em Windows mais fácil e abrangente.

Windows PowerShell 5.0 é compatível com versões anteriores. Os cmdlets, fornecedores, módulos, snap-ins, scripts, funções e perfis que foram concebidos para o Windows PowerShell 4.0, o Windows PowerShell 3.0 e o Windows PowerShell 2.0, geralmente, funcionam no Windows PowerShell 5.0 sem alterações.

# <a name="installing-windows-powershell"></a>Instalar o Windows PowerShell
Windows PowerShell 5.0 é instalado por predefinição no Windows Server 2016 Technical Preview e Windows 10.

Para instalar o Windows PowerShell 5.0 no Windows Server 2012 R2, Windows 8.1 Enterprise ou Windows 8.1 Pro, transfira e instale [Windows Management Framework 5.0](http://aka.ms/wmf5download). Lembre-se de que lê os detalhes de transferência e cumprir todos os requisitos de sistema, antes de instalar o Windows Management Framework 5.0.

## <a name="in-this-topic"></a>Neste tópico

- [Atualizações do Windows PowerShell 4.0 DSC na KB 3000850](#windows-powershell-40-updates-in-november-2014-update-rollup-kb-3000850)
- [Novas funcionalidades do Windows PowerShell 5.0](#new-features-in-windows-powershell-50)
- [Novas funcionalidades do Windows PowerShell 4.0](#new-features-in-windows-powershell-40)
- [Novas funcionalidades no Windows PowerShell 3.0](#new-features-in-windows-powershell-30)

## <a name="windows-powershell-40-updates-in-november-2014-update-rollup-kb-3000850"></a>Coletânea de atualizações do Windows PowerShell 4.0 em Novembro de 2014 (KB 3000850)
Muitas atualizações e melhoramentos para Windows PowerShell pretendido Estado Configuration (DSC) no Windows PowerShell 4.0 estão disponíveis no [rollup de atualização de Novembro de 2014 para Windows RT 8.1, Windows 8.1 e Windows Server 2012 R2](https://support.microsoft.com/kb/3000850/) (KB 3000850 ). Pode determinar se KB 3000850 está instalado no seu sistema, executando `Get-Hotfix -Id KB3000850` no Windows PowerShell.

- Atualizações para os cmdlets existentes no [PSDesiredStateConfiguration](https://technet.microsoft.com/library/dn391651(v=wps.640).aspx) módulo

    -   [Get-DscResource](http://technet.microsoft.com/library/dn521625.aspx) é mais rápido (especialmente no ISE).

    -   [Início DscConfiguration](http://technet.microsoft.com/library/dn521623.aspx) tem um novo parâmetro, - UseExisting, que volta a última configuração aplicada.

    -   [Início DscConfiguration](http://technet.microsoft.com/library/dn521623.aspx) -Force foi corrigido.

    -   [Get-DscLocalConfigurationManager](http://technet.microsoft.com/library/dn407378.aspx) apresenta informações mais úteis sobre o estado do motor.

    -   [Teste DscConfiguration](http://technet.microsoft.com/library/dn407382.aspx) agora devolve o nome do computador, juntamente com VERDADEIRO ou FALSO.

    -   [Novo DscChecksum](http://technet.microsoft.com/library/dn521622.aspx) suporta agora caminhos UNC.

- Cmdlets novos no [PSDesiredStateConfiguration](http://technet.microsoft.com/library/dn391651(v=wps.640).aspx) módulo

    -   [Atualização DscConfiguration](http://technet.microsoft.com/library/mt143541(v=wps.630).aspx): executa uma verificação de servidor de solicitação a pedido.

    -   [Stop-DscConfiguration](http://technet.microsoft.com/library/mt143542(v=wps.630).aspx): deixa de uma configuração que já está em execução.

    -   [Remover DscConfigurationDocument](http://technet.microsoft.com/library/mt143544(v=wps.630).aspx): permite-lhe remover documentos de configuração em várias etapas (pendentes, anteriores ou atuais).

- Melhoramentos de idioma

    -   DependsOn suporta agora recursos compostos.

    -   DependsOn suporta agora números em nomes de instância de recurso.

    -   As expressões de nó que avaliar já não está vazia para gerem erros.

    -   Correção do erro que ocorre se uma expressão de nó for avaliada como vazio.

    -   Configurações de chamar configurações agora trabalham na consola do Windows PowerShell.

- Melhoramentos de modo de extração

    -   Modo de extração suporta agora a todos os ficheiros ZIP.

    -   **AllowModuleOverwrite** agora funciona corretamente.

- Melhoramentos de resiliência

    -   Novo **DebugMode** permite-lhe recarregar módulos de recursos.

    -   Se ocorrer uma falha de configuração, o ficheiro pending.mof não é eliminado.

    -   O Gestor de configuração Local (MMC) agora é mais resistente quando as definições de configuração meta tem de ficar danificadas.

- Melhorias de diagnóstico

    -   Um aviso é apresentado quando o MMC define o temporizador para diferentes definições que especificou.

    -   Ficheiros de registo de erros incluem agora a pilha de chamadas de recursos do Windows PowerShell.

- Melhoramentos de flexibilidade

    -   O recurso de LocalConfigurationManager tem uma nova propriedade **ActionAfterReboot**.

        -   ContinueConfiguration (valor predefinido): retoma automaticamente uma configuração depois de um nó de destino ser reiniciado.

        -   StopConfiguration: Não retomado automaticamente uma configuração depois de um nó for reiniciado.

    -   Uma execução de consistência agora pode ocorrer com mais frequência do que uma operação de SOLICITAÇÃO, ou vice-versa.

    -   Suporte de controlo de versões: DSC agora pode reconhecer um documento que foi gerado num cliente mais recente (incluído no [WMF 5.0](http://aka.ms/wmf5download)).

- Melhoramentos de prevenção de erro

    -   Versão do módulo é agora imposta antes de uma configuração é aplicada.

    -   **DebugPreference** agora está corretamente definida para o Get-, Set- ou chamadas TargetResource de teste.

- Melhoramentos de processamento de credenciais

    -   É utilizado um certificado agora, se ambas as **certificado** e **PSDscAllowPlainTextPassword** especificados.

    -   As credenciais são desencriptadas, mesmo para Get-TargetResource.

    -   Credenciais de configuração meta são encriptadas e desencriptadas.

    -   PSCredentials agora são desencriptados quando estão a ser um objeto incorporado.

- Melhoramentos de recursos incorporadas

    -   O recurso de pacote

        -   Já não instala o pacote incorreto (local a partir de origens de web ou).

        -   Agora suporta HTTPS.

    -   Não há suporte agora para HTTPS no [recursos do pacote](http://technet.microsoft.com/library/dn282132.aspx).

    -   [Recurso de arquivo](http://technet.microsoft.com/library/dn249917.aspx) agora suporta credenciais.

## <a name="new-features-in-windows-powershell-50"></a>Novas funcionalidades do Windows PowerShell 5.0

- [Novas funcionalidades no Windows PowerShell](#new-features-in-windows-powershell)
- [Novas funcionalidades na configuração de estado pretendido do Windows PowerShell](#new-features-in-windows-powershell-desired-state-configuration)
- [Novas funcionalidades no ISE do Windows PowerShell](#new-features-in-windows-powershell-ise)
- [Novas funcionalidades nos serviços Web do Windows PowerShell](#new-features-in-windows-powershell-web-services-management-odata-iis-extension)
- [Correções de erros relevantes no Windows PowerShell 5.0](#notable-bug-fixes-in-windows-powershell-50)

### <a name="new-features-in-windows-powershell"></a>Novas funcionalidades no Windows PowerShell

- A partir do Windows PowerShell 5.0, pode desenvolver utilizando as classes, utilizando a sintaxe formal e semântica que é semelhante às outras linguagens de programação orientado para objetos. **Classe**, **Enum**, e outras palavras-chave foram adicionados ao idioma do Windows PowerShell para suportar a funcionalidade de novo. Para obter mais informações sobre como trabalhar com as classes, consulte about_Classes.

- Windows PowerShell 5.0 introduz um fluxo de informações de novo, estruturados que pode utilizar para transmitir dados estruturados entre um script e respetivos os chamadores (ou ambiente de alojamento). Agora, pode utilizar o anfitrião de escrita para emitir saída no fluxo de informações. Fluxos de informações também funcionam para PowerShell.Streams, tarefas, tarefas agendadas e fluxos de trabalho. As seguintes funcionalidades de suportar o fluxo de informações.

    -   Um cmdlet de escrita informações novo que lhe permite especificar a forma como o Windows PowerShell processa dados de fluxo de informações de um comando. Escrita anfitrião é um wrapper para informações de escrita. Informações de escrita também são uma atividade de fluxo de trabalho suportadas.

    -   Dois parâmetros comuns novos, InformationVariable e InformationAction, permitem-lhe determinar a forma como os fluxos de informações de um comando são apresentados. Os valores válidos para InformationAction são SilentlyContinue, parar, continuar, Inquire, ignorar ou suspender, com SilentlyContinue a ser a predefinição. InformationVariable Especifica uma cadeia como o nome da variável a que pretende que os dados do anfitrião de escrita de um comando guardado.

    -   Uma nova variável de preferência, InformationPreference, especifica a sua preferência predefinida para os dados de fluxo de informações numa sessão do Windows PowerShell. O valor predefinido é SilentlyContinue.

    -   Dois novos parâmetros comuns, PSInformation e InformationAction, foram adicionados.

    -   Quando utiliza o comando Format-Table, colunas da tabela agora são formatadas automaticamente através da avaliação do primeiro 300ms dos dados que atravessa o fluxo.

- Em colaboração com [Microsoft Research](http://research.microsoft.com/), foi adicionado um novo cmdlet, ConvertFrom-cadeia. Cadeia ConvertFrom permite extrair e analisar os objetos estruturados do conteúdo de cadeias de texto. Para obter mais informações, consulte ConvertFrom-cadeia.

- Um novo cmdlet de converter a cadeia formata automaticamente com base no exemplo que fornecem um - parâmetro de exemplo de texto.

- Um novo módulo, Microsoft.PowerShell.Archive, inclui cmdlets que lhe permitem comprima os ficheiros e pastas para ficheiros de arquivo (também conhecido como ZIP), extraia os ficheiros de ficheiros ZIP existentes e atualizar ficheiros ZIP com versões mais recentes dos ficheiros comprimidos dentro delas.

- Um novo módulo, PackageManagement, permite-lhe detetar e instalar pacotes de software na Internet. O módulo de PackageManagement (anteriormente conhecida como OneGet) é um gestor ou multiplexer de gestores de pacote existente (também denominados fornecedores do pacote) uniformizar a gestão de pacotes do Windows com uma única interface do Windows PowerShell.

- Um novo módulo, PowerShellGet, permite-lhe localizar, instalar, publicar e atualizar módulos e recursos de DSC no [galeria do PowerShell](http://www.powershellgallery.com/), ou um repositório de módulo interno que pode configurar executando o cmdlet Register-PSRepository.

- Uma novo idioma palavra-chave, **Hidden**, foi adicionada para especificar se um membro (uma propriedade ou um método) não é apresentado por predefinição nos resultados de Get-membro (exceto se adicionar o parâmetro - Force). Propriedades ou métodos que foram marcadas como ocultos também não apresentada nos resultados de IntelliSense, a menos que estejam num contexto onde o membro deve estar visível; Por exemplo, o automática variável $Isto deve mostrar ocultos os membros quando o método de classe.

- Novo Item, Item de remover e Get-ChildItem foram melhoradas para suportar a criação e gestão [ligações simbólicas](http://en.wikipedia.org/wiki/Symbolic_link). O **- ItemType** parâmetro para o novo Item aceita um novo valor **SymbolicLink**. Agora, pode criar as ligações simbólicas numa única linha, executando o cmdlet New-Item.

- Get-ChildItem também tem um new - profundidade parâmetro, que utiliza com o parâmetro-Recurse para limitar a recursão. Por exemplo, Get-ChildItem-Recurse - 2 de profundidade devolve resultados pastas na pasta atual, todas as pastas de subordinados dentro da pasta atual e todas as pastas no subordinadas.

- Copy-Item agora permite copiar ficheiros ou pastas a partir de uma sessão do Windows PowerShell para outro, que significa que pode copiar ficheiros para sessões que estão ligadas a computadores remotos, (incluindo computadores que executem [Nano servidor](http://blogs.technet.com/b/windowsserver/archive/2015/04/08/microsoft-announces-nano-server-for-modern-apps-and-cloud.aspx), e não ter assim nenhuma outra interface). Para copiar ficheiros, especifique os IDs de PSSession como o valor dos parâmetros - FromSession e - ToSession novo e adicione - caminho e - destino para especificar o caminho de origem e destino, respetivamente. Por exemplo, Copy-Item-c do caminho\\omeuficheiro.txt - ToSession $s-destino d:\\destinationFolder.

- Windows PowerShell transcription foi melhorado para aplicar a todas as aplicações de alojamento (por exemplo, o Windows PowerShell ISE) para além do anfitrião da consola (**powershell.exe**). Opções de transcription (incluindo ativar um transcript globais do sistema) podem ser configuradas ao ativar o **ativar PowerShell Transcription** definição de política de grupo, localizada no administrativo componentes de modelos/Windows/Windows PowerShell.

- Uma nova funcionalidade de rastreio de script detalhado permite-lhe ativar análise de utilização de script do Windows PowerShell num sistema e detalhadas de controlo. Depois de ativar o rastreio de script detalhado, do Windows PowerShell regista todos os blocos de script para o registo de eventos de evento rastreio para o Windows (ETW), **Microsoft-Windows-PowerShell/Operational**.

- A partir do Windows PowerShell 5.0, novos cmdlets de serviços de criptografia de sintaxe de mensagens suporta a encriptação e desencriptação de conteúdo utilizando o formato de padrão da IEFT para proteger criptograficamente mensagens conforme documentado [RFC5652](http://tools.ietf.org/html/rfc5652). Os cmdlets Get-CmsMessage, proteger CmsMessage e Unprotect-CmsMessage foram adicionados para o [Microsoft.PowerShell.Security](http://technet.microsoft.com/library/hh849807.aspx) módulo.

- Cmdlets novos no [Utility](http://technet.microsoft.com/library/hh849958.aspx) módulo, espaço de execução de Get, espaço de execução de depuração, Get-RunspaceDebug, RunspaceDebug ativar e desativar-RunspaceDebug, permitem-lhe definir as opções de depuração no espaço de execução e de início e de fim depuração num espaço de execução. Para espaços de arbitrários execução de depuração "ou seja, espaços de execução que não sejam o espaço de execução predefinido para uma consola do Windows PowerShell ou a sessão do Windows PowerShell ISE'" do Windows PowerShell permite-lhe configurar pontos de interrupção num script e tiver adicionado a pontos de interrupção terminar o script de em execução até que pode anexar um depurador para depurar o script de espaço de execução. Suporte de depuração aninhado para espaços de execução arbitrários foi adicionado ao depurador de script do Windows PowerShell para espaços de execução.

- Foi adicionado um novo cmdlet do formato hexadecimal para a [Utility](http://technet.microsoft.com/library/hh849958.aspx) módulo. Formato hexadecimal permite-lhe ver os dados de texto ou binário em formato hexadecimal.

- Foram adicionados os cmdlets Get-área de transferência e Set-área de transferência para o [Utility](http://technet.microsoft.com/library/hh849958.aspx) módulo; facilitam a transferência de conteúdo e de uma sessão do Windows PowerShell. Os cmdlets de área de transferência suporta imagens, ficheiros de áudio, listas de ficheiro e texto.

- Foi adicionado um novo cmdlet, desmarque-RecycleBin, para o [Management](http://technet.microsoft.com/library/hh849827(v=wps.640).aspx) módulo; este cmdlet esvazia Bin a Reciclagem para uma unidade fixa, que inclui unidades externas. Por predefinição, lhe for pedido para confirmar um comando de limpar RecycleBin, porque a propriedade ConfirmImpact do cmdlet está definida como ConfirmImpact.High.

- Um novo cmdlet, New-TemporaryFile, permite-lhe criar um ficheiro temporário como parte do processamento de scripts. Por predefinição, o novo ficheiro temporário é criado no ```C:\Users\<user name>\AppData\Local\Temp```.

- O Out-File, adicionar conteúdo e conteúdo do conjunto de cmdlets agora tem um novo parâmetro - NoNewline, que omite uma nova linha depois do resultado.

- O cmdlet New-Guid aproveita a classe de .NET Framework Guid para gerar um GUID, útil quando estiver a escrever scripts ou recursos de DSC.

- Como informação de versão pode ser enganosa, particularmente depois de um ficheiro é aplicado, novas propriedades de script de FileVersionRaw e ProductVersionRaw estão disponíveis para FileInfo objetos. Por exemplo, pode executar o seguinte comando para apresentar os valores destas propriedades para o powershell.exe, onde o $pid contém o ID de processo para uma sessão de execução do Windows PowerShell:  ```Get-Process -Id $pid -FileVersionInfo | Format-List *version* -Force```

- Novos cmdlets Enter PSHostProcess e PSHostProcess de saída permitem a depurar scripts do Windows PowerShell em processos separados do processo atual que está a ser executado na consola do Windows PowerShell. Execute Enter-PSHostProcess para introduzir ou ligar a um ID de processo específico e, em seguida, execute Get-espaço de execução para devolver os Active Directory espaços de execução no processo. Execute PSHostProcess de saída para anular a exposição do processo de quando tiver terminado de depurar o script no processo.

- Foi adicionado um novo cmdlet de depurador de espera para a [Utility](http://technet.microsoft.com/library/hh849958.aspx) módulo. Pode executar o depurador de espera para parar um script no depurador antes de executar a seguinte instrução no script.

- O depurador de fluxo de trabalho do Windows PowerShell suporta agora a conclusão de separador ou comando, e pode depurar as funções de fluxo de trabalho aninhado. Agora pode premir **Ctrl + Break** para introduzir o depurador num script em execução, em sessões locais e remotas e um script de fluxo de trabalho.

- Foi adicionado um cmdlet de tarefa de depuração para o [Microsoft.PowerShell.Core](http://technet.microsoft.com/library/hh849695.aspx) módulo para depurar scripts de tarefas em execução para o fluxo de trabalho do Windows PowerShell, em segundo plano e tarefas em execução na sessões remotas.

- Foi adicionado um novo Estado, AtBreakpoint, para tarefas do Windows PowerShell. O estado de AtBreakpoint aplica-se quando uma tarefa está a executar um script que inclui o conjunto de pontos de interrupção e o script atingiu um ponto de interrupção. Quando uma tarefa está parada, um ponto de interrupção de depuração, tem de depuração a tarefa executando o cmdlet de depuração-Job.

- Windows PowerShell 5.0 implementa o suporte para várias versões de um módulo do Windows PowerShell único na mesma pasta no $PSModulePath. Uma propriedade de RequiredVersion foi adicionada à classe ModuleSpecification para ajudar a que obter a versão pretendida do módulo; Esta propriedade é mutuamente exclusiva com a propriedade ModuleVersion. RequiredVersion é agora suportado como parte do valor do parâmetro de nome totalmente qualificado do Get-Module, Import-Module e os cmdlets do módulo de remover.

- Agora pode efetuar a validação do módulo versão ao executar o cmdlet de teste ModuleManifest.

- Resultados do cmdlet Get-Command apresentam agora uma coluna de versão; foi adicionada uma nova propriedade de versão para a classe de CommandInfo. Get-Command mostra comandos de várias versões do mesmo módulo. A propriedade de versão também faz parte de classes derivadas de CmdletInfo: CmdletInfo e ApplicationInfo.

- Get-Command tenha um novo parâmetro, - ShowCommandInfo, que devolve informações ShowCommand como PSObjects. Isto é especialmente útil funcionalidade para quando Mostrar comando é executado no ISE do Windows PowerShell, utilizando a comunicação remota do Windows PowerShell. O parâmetro - ShowCommandInfo substitui a função de Get-SerializedCommand existente no módulo Utility, mas o script Get-SerializedCommand ainda está disponível para suportar a criação de scripts de nível inferior.

- Um novo cmdlet Get-ItemPropertyValue permite-lhe obter o valor de uma propriedade sem utilizar a notação de pontos. Por exemplo, em versões mais antigas do Windows PowerShell, pode executar o seguinte comando para obter o valor da propriedade da chave de registo PowerShellEngine Base da aplicação: **(Get-ItemProperty-caminho HKLM:\\SOFTWARE\\ Microsoft\\PowerShell\\3\\PowerShellEngine-nome ApplicationBase). ApplicationBase**. A partir do Windows PowerShell 5.0, pode executar **Get ItemPropertyValue-caminho HKLM:\\SOFTWARE\\Microsoft\\PowerShell\\3\\PowerShellEngine-nome ApplicationBase** .

- Agora, a consola do Windows PowerShell utiliza de cores da sintaxe, tal como em ISE do Windows PowerShell.

- Um novo módulo NetworkSwitch contém cmdlets que lhe permite aplicar comutador, LAN virtual (VLAN) e básica configuração de porta do comutador de rede de camada 2 para comutadores de rede de certificação de logótipo do Windows Server 2012 R2.

- O parâmetro de nome totalmente qualificado foi adicionado aos cmdlets do módulo de remover e Import-Module, para suportar a armazenar várias versões de um módulo único.

- Save-Help, Update-Help, importação-PSSession, exportação-PSSession e Get-Command têm um novo parâmetro, FullyQualifiedModule, do tipo ModuleSpecification. Adicione este parâmetro para especificar um módulo pelo respetivo nome completamente qualificado.

- O valor de **$PSVersionTable.PSVersion** foi atualizada para 5.0.

### <a name="new-features-in-windows-powershell-desired-state-configuration"></a>Novas funcionalidades na configuração de estado pretendido do Windows PowerShell

- Melhoramentos de idioma do Windows PowerShell permitem-lhe definir os recursos de configuração de estado pretendido do Windows PowerShell (DSC) utilizando as classes. DscResource de importação é agora uma verdadeira dinâmica palavra-chave; Windows PowerShell analisa o módulo especificado '™ módulo de raiz s, procurar classes que contém o atributo DscResource. Agora, pode utilizar classes para definir os recursos de DSC, em que nenhum é necessária um ficheiro MOF nem DSCResource subpasta da pasta do módulo. Um ficheiro de módulo do Windows PowerShell pode conter várias classes de recursos de DSC.

- Foi adicionado um novo parâmetro, ThrottleLimit, para os seguintes cmdlets no módulo PSDesiredStateConfiguration. Adicione o parâmetro de ThrottleLimit para especificar o número de computadores de destino ou dispositivos nos quais pretende que o comando para trabalhar em simultâneo.

    -   Get-DscConfiguration

    -   Get-DscConfigurationStatus

    -   Get-DscLocalConfigurationManager

    -   Restauro DscConfiguration

    -   Teste DscConfiguration

    -   Comparar DscConfiguration

    -   DscConfiguration publicar

    -   Conjunto DscLocalConfigurationManager

    -   Início DscConfiguration

    -   Atualização DscConfiguration

- Com centralizada DSC relatório de erros, informações de erro avançadas não são apenas registadas nos eventos de registo, mas podem ser enviadas para uma localização central de Analysis Services posteriores. Pode utilizar esta localização central para armazenar os erros de configuração de DSC ocorridas para qualquer servidor no respetivo ambiente. Depois do servidor de relatórios está definido na configuração de metadados, todos os erros são enviados para o servidor de relatórios e, em seguida, armazenados numa base de dados. Pode configurar esta funcionalidade, independentemente se pretende ou não um nó de destino está configurado para solicitar a configurações de um servidor de solicitação.

- Melhoramentos ao ISE do Windows PowerShell facilitam a criação de recursos de DSC. Agora, pode realizar a seguinte.

    -   Listar todos os recursos de DSC dentro de um **configuração** ou **nó** bloco introduzindo **Ctrl + espaço** numa linha em branco no bloco.

    -   A conclusão automática em Propriedades de recurso do **enumeração** tipo.

    -   A conclusão automática no **DependsOn** propriedade dos recursos de DSC, com base nas outras instâncias de recurso na configuração.

    -   Conclusão de separador melhorada dos valores de propriedade de recurso.

- Um utilizador pode agora executar um recurso de um conjunto especificado de credenciais ao adicionar o **PSDscRunAsCredential** atributo para um bloco de nó. Por exemplo, PSDscRunAsCredential = Get-Credential Contoso\\DscUser. Esta funcionalidade é útil para a criação de configurações que executam o Windows Installer e programas de instalação do executável, aceder ramo de registo por utilizador ou efetuar outras tarefas fora do contexto de utilizador atual.

- foi adicionado suporte (baseado em x86) de 32 bits para o **configuração** palavra-chave.

- O Windows PowerShell inclui agora suporte para obter ajuda personalizada para configurações de DSC, definidas adicionando \[CmdletBinding()] para a função de configuração gerado.

- Um novo **DscLocalConfigurationManager** atributo designa um bloco de configuração como uma meta-configuração, o que é utilizada para configurar o Gestor de configuração Local do DSC. Este atributo restringe uma configuração para que contém apenas os itens que configurem o Gestor de configuração Local do DSC. Durante o processamento, esta configuração gera um \*. ficheiro meta.mof que, executando o cmdlet Set-DscLocalConfigurationManager, em seguida, é enviado para os nós de destino adequada.

- Configurações parciais agora são permitidas no Windows PowerShell 5.0. Pode fornecer documentos de configuração para um nó de fragmentos. Para um nó receber vários fragmentos de um documento de configuração, o nó '™ s Local Configuration Manager deve primeiro configurar para especificar os fragmentos esperados

- A sincronização entre o computador é nova no DSC no Windows PowerShell 5.0. Utilizando o WaitFor incorporada\* recursos (**WaitForAll**, **WaitForAny**, e **WaitForSome**), pode agora especificar dependências em computadores durante a configuração é executado, sem orchestrations externos. Estes recursos fornecem sincronização de nó de nó, utilizando ligações CIM através do protocolo WS-Man. Uma configuração pode aguardar que outro computador '™ Estado do recurso específico s para alterar.

- Apenas suficiente administração (JEA), uma nova funcionalidade de segurança de delegação, tira partido do DSC e espaços de execução restrita do Windows PowerShell para ajudar as empresas seguras de perda de dados ou compromisso pelos funcionários, se intencional ou não intencional. Para obter mais informações sobre JEA, incluindo onde pode transferir o recurso de xJEA DSC, consulte [apenas suficiente administração, passo a passo](http://blogs.technet.com/b/privatecloud/archive/2014/05/14/just-enough-administration-step-by-step.aspx).

- Foram adicionados os seguintes novos cmdlets no módulo PSDesiredStateConfiguration.

    -   Um novo cmdlet Get-DscConfigurationStatus obtém informações de alto nível sobre o estado de configuração a partir de um nó de destino. Pode obter o estado do último ou de todas as configurações.

    -   Um novo cmdlet comparar DscConfiguration compara uma configuração especificada com o estado real de um ou mais nós de destino.

    -   Um novo cmdlet Publish-DscConfiguration copia um ficheiro MOF de configuração para um nó de destino, mas não se aplica a configuração. A configuração é aplicada durante a próxima passagem de consistência ou ao executar o cmdlet Update-DscConfiguration.

    -   Um novo cmdlet de teste DscConfiguration permite-lhe verificar que uma configuração resultante corresponde à configuração pretendida, devolvendo um verdadeiro se a configuração corresponder a configuração pretendida, ou FALSO se a configuração real não corresponde a pretendida configuração.

    -   Um novo cmdlet Update-DscConfiguration força uma configuração para ser processado. Se o Gestor de configuração Local está no modo de solicitação, o cmdlet obtém a configuração do servidor de solicitação antes de aplicá-la.

### <a name="new-features-in-windows-powershell-ise"></a>Novas funcionalidades no ISE do Windows PowerShell

- Agora pode editar remotos scripts do Windows PowerShell e ficheiros de uma cópia local do ISE do Windows PowerShell, executando Enter-PSSession para iniciar uma sessão remota no computador que '™ s armazenar os ficheiros que pretende editar e, em seguida, em execução **PSEdit <path and file name on the remote computer>**. Esta funcionalidade facilita a edição ficheiros do Windows PowerShell que são armazenados na opção de instalação Server Core do Windows Server, onde não é possível executar o ISE do Windows PowerShell.

- O cmdlet Start-Transcript é agora suportado no ISE do Windows PowerShell.

- Agora pode depurar scripts remotos no ISE do Windows PowerShell.

- Um comando de menu novo, **interromper todos os** (Ctrl + B), interrompe ao depurador para scripts locais e remotamente em execução.

### <a name="new-features-in-windows-powershell-web-services-management-odata-iis-extension"></a>Novas funcionalidades do Windows PowerShell Web Services (extensão IIS da gestão OData)

- A partir do Windows PowerShell 5.0, pode gerar um conjunto de cmdlets do Windows PowerShell com base na funcionalidade exposta por um determinado ponto de final de OData, executando o cmdlet Export-ODataEndpointProxy, foi encontrado na nova [ Microsoft.PowerShell.OdataUtils](http://technet.microsoft.com/library/dn818507(v=wps.640).aspx) módulo.

### <a name="notable-bug-fixes-in-windows-powershell-50"></a>Correções de erros relevantes no Windows PowerShell 5.0

- Windows PowerShell 5.0 inclui uma nova implementação COM, que oferece melhoramentos substanciais no desempenho quando estiver a trabalhar com objetos de COM. Para uma demonstração em vídeo o efeito, consulte [Com_Perf_Improvements](http://1drv.ms/1qu3UPZ).

- Foram introduzidas melhorias significativas de desempenho para a conclusão de separador primeiro numa sessão do Windows PowerShell, encurtar o tempo de conclusão de separador por quase 500 ms.

## <a name="new-features-in-windows-powershell-40"></a>Novas funcionalidades do Windows PowerShell 4.0
Windows PowerShell 4.0 é compatível com versões anteriores. Os cmdlets, fornecedores, módulos, snap-ins, scripts, funções e perfis que foram concebidos para o Windows PowerShell 3.0 e o Windows PowerShell 2.0 funcionam no Windows PowerShell 4.0 sem alterações.

Windows PowerShell 4.0 está instalado por predefinição no Windows 8.1 e Windows Server 2012 R2. Para instalar o Windows PowerShell 4.0 no Windows 7 com SP1 ou Windows Server 2008 R2, transfira e instale [Windows Management Framework 4.0](http://www.microsoft.com/download/details.aspx?id=40855). Lembre-se de que lê os detalhes de transferência e cumprir todos os requisitos de sistema, antes de instalar o Windows Management Framework 4.0.

- [Novas funcionalidades no Windows PowerShell](#new-features-in-windows-powershell-1)
- [Novas funcionalidades no Windows PowerShell Integrated Scripting Environment (ISE)](#new-features-in-windows-powershell-integrated-scripting-environment-ise)
- [Novas funcionalidades no fluxo de trabalho do Windows PowerShell](#new-features-in-windows-powershell-workflow)
- [Novas funcionalidades nos serviços Web do Windows PowerShell](#new-features-in-windows-powershell-web-services)
- [Novas funcionalidades no Windows PowerShell Web Access](#new-features-in-windows-powershell-web-access)
- [Correções de erros relevantes no Windows PowerShell 4.0](#notable-bug-fixes-in-windows-powershell-40)

Windows PowerShell 4.0 inclui as seguintes novas funcionalidades.

### <a name="new-features-in-windows-powershell"></a>Novas funcionalidades no Windows PowerShell

- **A configuração de estado pretendido do Windows PowerShell** (DSC) é um novo sistema de gestão no Windows PowerShell 4.0, que permite a implementação e gestão de dados de configuração de serviços de software e o ambiente em que estes serviços são executados. Para obter mais informações sobre o DSC, consulte [começar com a configuração de estado pretendido do Windows PowerShell](https://technet.microsoft.com/library/c134aa32-b085-4656-9a89-955d8ff768d0).

- **Save-Help** agora permite guardar ajuda para módulos que são instaladas em computadores remotos. Pode utilizar Save-Help para transferir o módulo ajuda a partir de um cliente ligado à Internet (em que nem todos os módulos para a qual pretende obter ajuda são necessariamente instalados) e, em seguida, copie a ajuda guardada para uma pasta partilhada remota ou um computador remoto que não tenha Internet acesso.

- O depurador do Windows PowerShell foi melhorado para permitir a depuração de fluxos de trabalho do Windows PowerShell, bem como os scripts que são executados em computadores remotos. Agora podem ser debugged fluxos de trabalho do Windows PowerShell ao nível do script de linha de comandos do Windows PowerShell ou ISE do Windows PowerShell. Scripts do Windows PowerShell, incluindo fluxos de trabalho de script, podem agora ser debugged através de sessões remotas. Sessões de depuração remotas são preservadas através de sessões de remotas do Windows PowerShell que são desligadas e, em seguida, mais tarde ligados de novo.

- A **RunNow** parâmetro **Register-ScheduledJob** e **Set-ScheduledJob** elimina a necessidade de definir uma data de início imediata e a hora para tarefas utilizando o **Acionador** parâmetro.

- **Invoke-RestMethod** e **Invoke-WebRequest** agora permitem-lhe definir todos os cabeçalhos utilizando o parâmetro de cabeçalhos. Embora este parâmetro sempre já existia, era um dos vários parâmetros para os cmdlets da web que resultaram numa exceções ou erros.

- **Get-Module** tem um parâmetro novo, **nome totalmente qualificado**, do tipo **ModuleSpecification\[]**. O **nome totalmente qualificado** parâmetro de Get-Module agora permite-lhe especificar um módulo com o nome do módulo, versão e, opcionalmente, respetivo GUID.

- A predefinição da política de execução no Windows Server 2012 R2 é **RemoteSigned**. No Windows 8.1, não há nenhuma alteração no predefinido definição.

- A invocação de métodos utilizando nomes de método dinâmico a partir do Windows PowerShell 4.0, é suportada. Pode utilizar uma variável para armazenar um nome de método e, em seguida, invocar dinamicamente o método ao chamar a variável.

- Tarefas de fluxo de trabalho assíncrono já não são eliminadas quando o período de tempo limite que é especificado pelo **PSElapsedTimeoutSec** parâmetro comum de fluxo de trabalho tiver decorrido.

- Um novo parâmetro **RepeatIndefinitely**, foi adicionada para o **New-JobTrigger** e **Set-JobTrigger** cmdlets. Isto elimina a necessária de especificar um **TimeSpan. MaxValue** valor para o **RepetitionDuration** parâmetro para executar uma tarefa agendada repetidamente durante um período indefinido.

- A **Passthru** parâmetro foi adicionado para o **Enable-JobTrigger** e **Disable-JobTrigger** cmdlets. O parâmetro Passthru mostra os objetos que são criados ou modificados pelo seu comando.

- Os nomes de parâmetro para especificar um grupo de trabalho no **Add-Computer** e **Remove-Computer** cmdlets agora são consistentes. Ambos os cmdlets agora utilizar o parâmetro **WorkgroupName**.

- Um novo parâmetro comum, **PipelineVariable**, foi adicionado. PipelineVariable permite-lhe guardar os resultados de um comando direcionado (ou parte de um comando piped) como uma variável que pode ser transmitida o resto do pipeline.

- Coleção de filtragem, utilizando uma sintaxe de método é agora suportada. Isto significa que agora, pode filtrar uma coleção de objetos utilizando sintaxe simplificada, semelhante de Where() ou Where-Object, a formatados como uma chamada de método. Segue-se um exemplo: (Get-Process) .where ({$_. Nome – corresponder 'powershell'})

- O **Get-Process** cmdlet tem um parâmetro novo, **IncludeUserName**.

- Um novo cmdlet **Get-FileHash**, que devolve um valor de hash de ficheiro dos formatos vários para um ficheiro especificado, foi adicionado.

- No Windows PowerShell 4.0, se utilizar um módulo o **DefaultCommandPrefix** principais no respetivo manifesto, ou se o utilizador importa um módulo com o **prefixo** parâmetro, a **ExportedCommands**propriedade do módulo mostra os comandos no módulo com o prefixo. Quando executa os comandos utilizando a sintaxe qualificado do módulo, ModuleName\\CommandName, os nomes de comando tem de incluir o prefixo.

- O valor de **$PSVersionTable.PSVersion** foi atualizada para 4.0.

- **WHERE()** foi alterado o comportamento de operador. `Collection.Where('property -match name')` aceitar uma expressão de cadeia no formato `"Property -CompareOperator Value"` já não é suportada. No entanto, o **Where()** operador aceita as expressões de cadeia no formato de um scriptblock; isto ainda é suportado.

### <a name="new-features-in-windows-powershell-integrated-scripting-environment-ise"></a>Novas funcionalidades no Windows PowerShell Integrated Scripting Environment (ISE)

- ISE do Windows PowerShell suporta a depuração de fluxo de trabalho do Windows PowerShell e a depuração de script remoto.

- Foi adicionado suporte IntelliSense para fornecedores de configuração de estado pretendido do Windows PowerShell e configurações.

### <a name="new-features-in-windows-powershell-workflow"></a>Novas funcionalidades no fluxo de trabalho do Windows PowerShell

- Foi adicionado suporte para um novo **PipelineVariable** parâmetro comum no contexto de pipelines iterativos, tais como as utilizadas pelo System Center Orchestrator; ou seja, pipelines que execute comandos simplesmente à esquerda para a direita, opposed para disseminado com utilizando a transmissão em fluxo.

- Enlace de parâmetro foi melhorado significativamente para trabalhar fora cenários de conclusão de separador, tal como com os comandos que não existe no espaço de execução atual.

- Foi adicionado suporte para as atividades de contentor personalizado para o fluxo de trabalho do Windows PowerShell. Se for um parâmetro de atividade dos tipos **atividade**, **atividade\[]**' "ou é uma coleção genérica de atividades" e o utilizador tiver fornecido um bloco de script como um argumento, em seguida, o Windows Fluxo de trabalho do PowerShell converte o bloco de script em XAML, tal como acontece com a compilação de scripts-para-fluxo de trabalho normal do Windows PowerShell.

- Após uma falha, o fluxo de trabalho do Windows PowerShell automaticamente volta a ligar a nós geridos.

- Agora pode limitar **Foreach-Parallel** declarações de atividade utilizando a **ThrottleLimit** propriedade.

- O **ErrorAction** parâmetro comum de tem um valor válido novo, **suspender**, que é exclusivamente para fluxos de trabalho.

- Um ponto final do fluxo de trabalho agora é fechada automaticamente se não existirem sem sessões ativas, não existem tarefas em curso e não existem tarefas pendentes. Esta funcionalidade conserva valiosos recursos no computador que está a agir como servidor de fluxo de trabalho, quando as condições de fecho automático tiverem sido cumpridas.

### <a name="new-features-in-windows-powershell-web-services"></a>Novas funcionalidades nos serviços Web do Windows PowerShell

- Quando ocorre um erro no Windows PowerShell Web Services (PSWS, também chamado Management OData extensão IIS), enquanto um cmdlet está em execução, as mensagens são devolvidas para o autor da chamada de erro mais detalhada. Além disso, siga os códigos de erro [diretrizes de código de erro de API de REST do Windows Azure](http://msdn.microsoft.com/library/windowsazure/dd179357.aspx).

- Um ponto final pode agora definir a versão de API, bem como impor a utilização de uma versão de API específica. Sempre que ocorre correspondência de versão entre cliente e servidor, são apresentados erros para o cliente e o servidor.

- Gestão do esquema de distribuição foi simplificado ao gerar automaticamente os valores para os campos em falta no esquema. Geração ocorre, como um ponto de partida útil, mesmo se o esquema de distribuição não existe.

- Tipo de processamento no PSWS foi melhorado para suportar os tipos que utilizam um construtor diferente que o construtor predefinido, por comportam de forma semelhante de **PSTypeConverter** no Windows PowerShell. Isto permite-lhe utilizar tipos complexos com PSWS.

- Agora, PSWS permite expandir uma instância associada ao executar uma consulta. Para obter conteúdo binário maior (por exemplo, imagens, áudio ou vídeos), o custo de transferência é significativo e é melhor transferir dados binários sem codificação. PSWS utiliza fluxos com nome de recurso para transferência sem codificação. A sequência de recursos com o nome é uma propriedade de uma entidade do **Edm.Stream** tipo. Cada sequência de recursos com o nome tem um URI separado para operações GET ou UPDATE.

- Ações de OData agora fornecem um mecanismo para invocar a métodos (criar, ler, atualizar e eliminar) não CRUD num recurso. Pode invocar uma ação, enviando um pedido POST de HTTP para o URI que está definido para a ação. Os parâmetros para a ação são definidos no corpo do pedido POST.

- Para estar consistente com as diretrizes do Windows Azure, devem ser simplificados todos os URLs. Uma alteração incluída no **chave como segmento** permite chaves único a ser representado como segmentos. Tenha em atenção que as referências que utilizam vários valores de chaves necessitam de valores separados por vírgulas na notação parenthetical, como anteriormente.

- Antes desta versão do PSWS, o só para efetuar a criação, atualização ou eliminação operações foi invocar Post, Put, ou eliminar um recurso de nível superior. Novos nesta versão do PSWS, operações de recursos contidos permitir que os utilizadores alcançar os resultados da mesmos ao atingir o mesmo recurso menos diretamente, a aproximar-se como se estes recursos foram contidos.

### <a name="new-features-in-windows-powershell-web-access"></a>Novas funcionalidades no Windows PowerShell Web Access

- Pode desligar do e voltar a ligar a sessões existentes na consola do acesso Web Windows PowerShell baseada na web. A **guardar** botão na consola baseada na web permite-lhe desligar a partir de uma sessão sem eliminar e voltar a ligar à sessão outra vez.

- Os parâmetros predefinidos podem ser apresentados na página de início de sessão. Para apresentar os parâmetros predefinidos, configurar os valores para todas as definições apresentadas no **definições de ligação opcionais** área da página de início de sessão num ficheiro denominado **Web. config**. Pode utilizar o **Web. config** ficheiros para configurar todas as definições de ligação opcionais, exceto um conjunto de segundo ou alternativo de credenciais.

- No Windows Server 2012 R2, pode gerir remotamente as regras de autorização de acesso Web Windows PowerShell. O **Add-PswaAuthorizationRule** e **Test-PswaAuthorizationRule** cmdlets incluem agora um parâmetro de credencial que permite aos administradores gerir regras de autorização de um computador remoto ou por um Sessão de acesso Web Windows PowerShell.

- Agora pode ter várias sessões de acesso Web Windows PowerShell numa sessão de browser único através de um novo separador do browser para cada sessão. Já não terá de abrir uma nova sessão de browser para ligar a uma nova sessão na consola do Windows PowerShell baseada na web.

### <a name="notable-bug-fixes-in-windows-powershell-40"></a>Correções de erros relevantes no Windows PowerShell 4.0

- **Get-Counter** agora podem devolver os contadores que contêm um caráter de apóstrofo em francês edições do Windows.

- Agora, pode ver o **GetType** método em objetos de serialização anulados.

- **#Requires** instruções permitem agora que os utilizadores necessitam de direitos de acesso de administrador, se necessário.

- O **importação de Csv** cmdlet agora ignora as linhas em branco.

- Um problema onde o ISE do Windows PowerShell utiliza demasiada memória quando estiver a executar um **Invoke-WebRequest** comando foi corrigido.

- **Get-Module** apresenta agora versões de módulo num **versão** coluna.

- Item de remove - Recurse agora remove itens subpastas conforme esperado.

- A **UserName** propriedade foi adicionada ao **Get-Process** objetos de saída.

- O **Invoke-RestMethod** cmdlet agora devolve todos os resultados disponíveis.

- **Membro adicionar** agora entra em vigor no tabelas hash, mesmo se a tabelas hash ainda não ter sido acedida.

- **Select-Object - expanda** ou falhar já não gera uma exceção se o valor da propriedade é nulo ou estar vazio.

- **Get-Process** pode agora ser utilizado num pipeline com outros comandos que obtenha o **ComputerName** propriedade dos objetos.

- **ConvertTo-Json** e **ConvertFrom Json** agora pode aceitar os termos dentro de aspas duplas e as mensagens de erro são agora localizável.

- **Get-Job** agora devolve qualquer concluir tarefas agendadas, mesmo em novas sessões.

- Problemas com montar e desmontagem VHDs utilizando o **FileSystem** corrigir fornecedor no Windows PowerShell 4.0. Agora é capaz de detetar unidades novas quando estão montados na mesma sessão do Windows PowerShell.

- Já não necessita de carregar explicitamente **ScheduledJob** ou **fluxo de trabalho** módulos para trabalhar com os respetivos tipos de tarefa.

- Foram efetuados melhoramentos de desempenho para o processo de importação de fluxos de trabalho que definem fluxos de trabalho aninhados; Este processo agora é mais rápido.

## <a name="new-features-in-windows-powershell-30"></a>Novas funcionalidades no Windows PowerShell 3.0
Windows PowerShell 3.0 inclui as seguintes novas funcionalidades.

- [O fluxo de trabalho do Windows PowerShell](#windows-powershell-workflow)
- [Acesso Web Windows PowerShell](#windows-powershell-web-access)
- [Novas funcionalidades do Windows PowerShell ISE](#new-windows-powershell-ise-features)
- [Suporte para o Microsoft .NET Framework 4.0](#support-for-microsoft-net-framework-4)
- [Suporte para o ambiente de pré-instalação do Windows](#support-for-windows-preinstallation-environment)
- [Sessões desligadas](#disconnected-sessions)
- [Conectividade de sessão robusta](#robust-session-connectivity)
- [Sistema de ajuda atualizável](#updatable-help-system)
- [Avançado de Ajuda Online](#enhanced-online-help)
- [Integração de CIM](#cim-integration)
- [Ficheiros de configuração de sessão](#session-configuration-files)
- [Tarefas agendadas e a integração do Programador de tarefas](#scheduled-jobs-and-task-scheduler-integration)
- [Melhoramentos do Windows PowerShell idioma](#windows-powershell-language-enhancements)
- [Novos Cmdlets de núcleo](#new-core-cmdlets)
- [Melhoramentos para os Cmdlets de núcleo existente e fornecedores](#improvements-to-existing-core-cmdlets-and-providers)
- [Importação do módulo remoto e a deteção](#remote-module-import-and-discovery)
- [Conclusão de separador Avançado](#enhanced-tab-completion)
- [Carregamento do módulo automático](#module-auto-loading)
- [Melhoramentos de experiência de módulo](#module-experience-improvements)
- [Deteção de comando simplificada](#simplified-command-discovery)
- [Registo melhorado, diagnóstico e suporte de política de grupo](#improved-logging-diagnostics-and-group-policy-support)
- [Formatação e melhoramentos de saída](#formatting-and-output-improvements)
- [Experiência de anfitrião da consola avançada](#enhanced-console-host-experience)
- [Novo Cmdlet e alojamento de APIs](#new-cmdlet-and-hosting-apis)
- [Melhorias de desempenho](#performance-improvements)
- [Suporte de anfitriões partilhado e RunAs](#runas-and-shared-host-support)
- [Melhoramentos de processamento de caráter especial](#special-character-handling-improvements)

### <a name="windows-powershell-workflow"></a>O fluxo de trabalho do Windows PowerShell
O fluxo de trabalho do Windows PowerShell oferece a capacidade da Windows Workflow Foundation para o Windows PowerShell. Pode escrever fluxos de trabalho em XAML ou no idioma do Windows PowerShell e executá-los tal como, deverá executar um cmdlet. O [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) cmdlet obtém workflw comandos e o [Get-Help](https://technet.microsoft.com/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) cmdlet obtém ajuda para fluxos de trabalho.

Fluxos de trabalho são sequências de atividades de gestão multicomputer que são de longa execução, repetíveis, frequentes, paralelizáveis, podem ser, suspendable e reiniciados. Fluxos de trabalho podem ser retomados a partir de uma interrupção acidental ou intencional, como uma falha de rede, um reinício do Windows ou uma falha de energia.

Fluxos de trabalho também são portátil; pode ser exportados como ou importados a partir de ficheiros XAML. Pode escrever configurações de sessão personalizadas que permitem que o fluxo de trabalho ou atividades num fluxo de trabalho a ser executada pelos utilizadores delegados ou subordinados.

Seguem-se as vantagens do fluxo de trabalho do Windows PowerShell

- Automatização de tarefas sequenciadas, execução longa.

- **Monitorização remota das tarefas de longa execução**. Estado e o progresso das atividades são visíveis em qualquer altura.

- **Gestão multicomputer.** Execute simultaneamente tarefas como fluxos de trabalho em centenas de nós geridos. O fluxo de trabalho do Windows PowerShell inclui uma biblioteca incorporada dos parâmetros comuns de gestão, tais como **PSComputerName**, que ativar cenários de gestão de vários computadores.

- **Execução da tarefa única de processos complexos.** Pode combinar scripts relacionados que implementam um cenário ponto-a-ponto completo num fluxo de trabalho único.

- **Persistência.** : um fluxo de trabalho é guardado (ou indicada de verificação) em pontos específicos definidos pelo respetivo autor, para que possa retomar o fluxo de trabalho desde a última tarefa persistente (ou ponto de verificação), em vez de reiniciar o fluxo de trabalho a partir do início.

- **Robustez.** Recuperação de falha automatizada. Fluxos de trabalho sobrevivem a reinícios planeados e imprevistos. Pode suspender a execução do fluxo de trabalho e, em seguida, retomar o fluxo de trabalho do último ponto de persistência. Os autores de fluxo de trabalho podem designar atividades específicas a ser executada novamente em caso de falha num ou mais nós geridos.

- **Capacidade para desligar, voltar a ligar e executar nas sessões desligadas.** Os utilizadores podem ligar e desligar do servidor de fluxo de trabalho, mas o fluxo de trabalho é executada continuamente. Pode terminar o computador cliente ou reinicie o computador cliente e monitorizar a execução de fluxo de trabalho a partir de outro computador sem interromper o fluxo de trabalho.

- **Durante o agendamento.** Tarefas de fluxo de trabalho podem ser agendadas como qualquer cmdlet do Windows PowerShell ou script.

- **Fluxo de trabalho e a limitação de ligação.** Ligações a nós e da execução do fluxo de trabalho podem ser limitadas, permitindo cenários de elevada disponibilidade e escalabilidade.

### <a name="windows-powershell-web-access"></a>Windows PowerShell Web Access
Acesso Web Windows PowerShell é uma funcionalidade do Windows Server 2012 que permite que os utilizadores executar comandos do Windows PowerShell e scripts numa consola baseada na web. Dispositivos que utilizam a consola baseada na web não requerem o Windows PowerShell, o software de gestão remota ou instalações de plug-in do browser. Tudo o que é necessário é um gateway de acesso Web Windows PowerShell corretamente configurados e um browser do dispositivo cliente que suporte JavaScript e aceite cookies.

Para obter mais informações, consulte [implementar o Windows PowerShell Web Access](http://go.microsoft.com/fwlink/p/?LinkID=221050).

### <a name="new-windows-powershell-ise-features"></a>Novas funcionalidades do Windows PowerShell ISE
Para o Windows PowerShell 3.0, o Windows PowerShell Integrated Scripting Environment (ISE) tem várias novas funcionalidades, incluindo o IntelliSense, a janela de comando de mostrar, um painel de consola unificada, fragmentos, chaveta correspondente, expanda-fechar secções, guardar automática, itens recentes lista, cópia avançada, cópia de bloco e suporte integral para escrever fluxos de trabalho de script de Windows PowerShell. Para obter mais informações, consulte [about_Windows_PowerShell_ISE [v3]](https://technet.microsoft.com/library/dfa54d47-60c6-4fff-8197-c747e8d411bb).

### <a name="support-for-microsoft-net-framework-4"></a>Suporte para o Microsoft .NET Framework 4
Windows PowerShell baseia-se contra o 4.0 de tempo de execução de idioma comum. Cmdlet, scripts e os autores de fluxo de trabalho podem utilizar as novas classes do Microsoft .NET Framework 4 no Windows PowerShell, com funcionalidades que incluem a compatibilidade aplicacional e implementação, geridos Framework de extensibilidade, computação paralela, funcionamento em rede do Windows Communication Foundation e o Windows Workflow Foundation.

### <a name="support-for-windows-preinstallation-environment"></a>Suporte para o ambiente de pré-instalação do Windows
Windows PowerShell 3.0 é um componente opcional de ambiente de pré-instalação do Windows (Windows PE) 4.0 para Windows 8. O Windows PE é um sistema operativo mínimo que inicia um computador que não tenha nenhum sistema operativo e prepara-o para a instalação do Windows. Windows PE podem ser utilizados para a partição e formatar os discos rígidos, copie as imagens do disco para um computador e iniciar o programa de configuração do Windows a partir de uma partilha de rede. Windows PowerShell 3.0 pode ser utilizado no Windows PE para gerir a implementação, diagnóstico e cenários de recuperação.

### <a name="disconnected-sessions"></a>Sessões desligadas
A partir do Windows PowerShell 3.0, persistentes gerida pelo utilizador sessões ("PSSessions") que criou utilizando o cmdlet New-PSSession são guardadas no computador remoto. Já não são dependentes na sessão que foram criados.

Pode agora desligar a partir de uma sessão sem perturbar os comandos que estão em execução na sessão. Pode fechar a sessão e encerrar o computador. Mais tarde, poderá restabelecer a ligação para a sessão a partir de uma sessão diferente no mesmo ou num computador diferente.

O **ComputerName** parâmetro o [Get-PSSession](https://technet.microsoft.com/library/b2b10531-d0df-4746-b877-e75c09955cb6) cmdlet agora obtém todas as sessões do utilizador que se ligam ao computador, mesmo que iniciaram numa sessão diferente num computador diferente. Pode ligar-se para as sessões, obtenha os resultados de comandos, iniciar novos comandos e, em seguida, desligue a sessão.

Foram adicionados novos cmdlets para suportar a funcionalidade de sessões de desligado, incluindo [Disconnect-PSSession](https://technet.microsoft.com/library/f8f95111-612f-4cba-9098-77904b0473d8), [Connect-PSSession](https://technet.microsoft.com/library/b803dd29-f208-4079-80d4-db04d778f060), e Receive-PSSession e novos parâmetros, foram adicionados para cmdlets que gerir PSSessions, tais como o **InDisconnectedSession** parâmetro o [Invoke-Command](https://technet.microsoft.com/library/906b4b41-7da8-4330-9363-e7164e5e6970) cmdlet.

A funcionalidade de sessões desligado só é suportada quando os computadores em ambos ("cliente") de origem e termina ("servidor") da ligação de terminação estão a executar Windows PowerShell 3.0.

### <a name="robust-session-connectivity"></a>Conectividade de sessão robusta
Windows PowerShell 3.0 Deteta perdas inesperadas de conectividade entre o cliente e o servidor e tenta restabelecer a conectividade e retomar a execução automaticamente. Se não é possível restabelecer a ligação de cliente-servidor dentro do tempo atribuído, o utilizador é notificado e a sessão é desligada. Durante a tentativa de restabelecer a ligação, o Windows PowerShell fornece comentários contínuos para o utilizador.

Se a sessão desligada foi iniciada utilizando a InvokeCommand, o Windows PowerShell cria uma tarefa para a sessão desligada tornar mais fácil restabelecer a ligação e retomar a execução.

Estas funcionalidades proporcionam uma experiência de gestão remota mais fiável e recuperáveis e permitir que os utilizadores efetuar tarefas de longa execução que necessitam de sessões robustas, tais como os fluxos de trabalho.

### <a name="updatable-help-system"></a>Sistema de ajuda atualizável
Agora pode transferir os ficheiros de ajuda atualizados para os cmdlets no seu módulos. O [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) cmdlet identifica os ficheiros de ajuda mais recentes, transfere-os partir da Internet, descompacta-los, valida-los e instala-as no diretório específicas do idioma correto para o módulo.

Para utilizar os ficheiros de ajuda atualizados, basta escrevê `Get-Help`. Não é necessário reiniciar o Windows ou o Windows PowerShell. Para atualizar a ajuda para módulos no diretório $pshome, inicie o Windows PowerShell com a opção "Executar como administrador".

Para suportar os utilizadores que não tem acesso à Internet e os utilizadores atrás de firewalls, a nova [Save-Help](https://technet.microsoft.com/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa) cmdlet transfere ficheiros de ajuda para um diretório de sistema de ficheiros, tais como uma partilha de ficheiros. Os utilizadores podem, em seguida, utilizar o [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) cmdlet para obter ficheiros de ajuda atualizados da partilha de ficheiros.

Pode utilizar o [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) módulos específicos em todas as suportados da IU ou ficheiros de cmdlet para atualizar a ajuda para todos os idiomas. Ainda pode colocar um [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) comando no seu perfil do Windows PowerShell. Por predefinição, do Windows PowerShell transfere os ficheiros de ajuda para um módulo não mais do que uma vez por dia.

Módulos do Windows 8 e Windows Server 2012 não incluem ficheiros de ajuda. Para transferir os ficheiros de ajuda mais recentes, escreva `Update-Help`. Para obter mais informações, escreva `Get-Help` (sem parâmetros) ou consulte [about_Updatable_Help](https://technet.microsoft.com/library/10bba75c-f4ac-4ca1-bbf3-8f34dd521ffe).

Quando os ficheiros de ajuda para um cmdlet não estão instalados no computador, o [Get-Help](https://technet.microsoft.com/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) cmdlet apresenta agora ajuda gerada automaticamente. A ajuda gerado automaticamente inclui a sintaxe de comando e instruções para utilizar o [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) cmdlet para transferir ficheiros de ajuda.

Autor qualquer módulo pode suportar a ajuda Atualizável de mensagens em fila para o respetivo módulo. Pode incluir ficheiros de ajuda no módulo e utilizar a ajuda Atualizável atualizá-las ou omita os ficheiros de ajuda e utilizar a ajuda Atualizável para instalá-los. Para obter mais informações sobre o apoio ajuda Atualizável, consulte [apoio ajuda Atualizável](http://go.microsoft.com/FWLink/?LinkID=242129) no MSDN.

### <a name="enhanced-online-help"></a>Avançado de Ajuda Online
Ajuda online do Windows PowerShell é um recurso importante para todos os utilizadores, mas é especialmente importante para os utilizadores que não compatíveis ou não é possível instalar os ficheiros de ajuda atualizados.

Para obter ajuda online para qualquer cmdlet Windows PowerShell, escreva:

```
Get-Help <cmdlet-name> -Online
```

Windows PowerShell abre-se a versão do tópico de ajuda online no seu browser predefinido.

O **Get-Help-Online** funcionalidade no Windows PowerShell 3.0 está agora ainda mais poderosa porque funciona, mesmo quando os ficheiros de ajuda para o cmdlet não estão instalados no computador. O **Get-Help-Online** funcionalidade obtém o URI para o tópico de ajuda online da propriedade HelpUri de cmdlets e funções avançadas.

```
PS C:\>(Get-Command Get-ScheduledJob).HelpUri
http://go.microsoft.com/fwlink/?LinkID=223923
```

A partir do Windows PowerShell 3.0, os autores de c# cmdlets podem preencher o **HelpUri** propriedade criando um **HelpUri** atributo na classe de cmdlet. Os autores de funções avançadas podem definir um **HelpUri** propriedade o **CmdletBinding** atributo. O valor da **HelpUri** propriedade tem de começar com "http" ou "https".

Também pode incluir um **HelpUri** valor na primeira ligação relacionada de um ficheiro de ajuda do cmdlet baseado em XML ou. Diretiva de ligação de ajuda baseada no comentário de uma função.

Para obter mais informações sobre o suporte de ajuda online, consulte [apoio Ajuda Online](http://go.microsoft.com/fwlink/?LinkId=242132) no MSDN.

### <a name="cim-integration"></a>Integração de CIM
Windows PowerShell 3.0 inclui suporte para o modelo CIM (Common Information), que fornece definições comuns de informações de gestão de sistemas, redes, aplicações e serviços, permitindo-lhes a troca de informações de gestão entre sistemas heterogéneos. Suporte para CIM no Windows PowerShell 3.0, incluindo a capacidade de cmdlets do Windows PowerShell com base nas classes CIM novas ou existentes, os comandos de autor com base na definição de cmdlet ficheiros XML, o suporte para CIM .NET Framework. API, os cmdlets de gestão do CIM e fornecedores WMI 2.0.

### <a name="session-configuration-files"></a>Ficheiros de configuração de sessão
A partir do Windows PowerShell 3.0, pode conceber uma configuração de sessão personalizada utilizando um ficheiro. O ficheiro de configuração de novo sessão permite-lhe determinar o ambiente de sessões que utilizam a configuração de sessão, incluindo quais os módulos, scripts e ficheiros de formato são carregados no sessões, cmdlets e de idioma elementos os utilizadores que podem utilizar, quais os módulos e scripts podem ser executados e que as variáveis podem ver.

Pode estruturar uma sessão em que os utilizadores só podem executar os cmdlets em de um módulo específico, ou uma sessão em que os utilizadores têm acesso para scripts que efetuar tarefas avançadas, acesso a todos os módulos e completo de linguagem.

Em versões anteriores do Windows PowerShell, o controlo deste nível estava disponível apenas a quem foi possível escrever um programa c# ou um script de arranque complexos. Agora, qualquer membro do grupo Administradores no computador pode personalizar uma configuração de sessão utilizando um ficheiro de configuração.

Para criar um ficheiro de configuração de sessão, utilize o [New-PSSessionConfigurationFile](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866) cmdlet. Para aplicar o ficheiro de configuração de sessão a uma configuração de sessão, utilize o [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) ou [Set-PSSessionConfiguration](https://technet.microsoft.com/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) cmdlets.

Para obter mais informações, consulte [about_Session_Configuration_Files](https://technet.microsoft.com/library/c7217447-1ebf-477b-a8ef-4dbe9a1473b8) e [New-PSSessionConfigurationFile](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866).

### <a name="scheduled-jobs-and-task-scheduler-integration"></a>Tarefas agendadas e a integração do Programador de tarefas
Agora pode agendar tarefas do Windows PowerShell em segundo plano e geri-los no Windows PowerShell e no programador de tarefas.

Tarefas agendadas do Windows PowerShell são uma híbrida útil de tarefas do Windows PowerShell em segundo plano e tarefas do Programador de tarefas.

Como as tarefas em segundo plano do Windows PowerShell, tarefas agendadas executam de forma assíncrona em segundo plano. Instâncias de tarefas agendadas que concluíram podem ser geridas utilizando os cmdlets de tarefa, tal como [Start-Job](https://technet.microsoft.com/library/2bc04935-0deb-4ec0-b856-d7290cca6442) e [Get-Job](https://technet.microsoft.com/library/1352c534-7193-46ca-9ab1-0c5219a661ad).

Como as tarefas do Programador de tarefas, pode executar tarefas agendadas com base numa agenda periódica ou única ou em resposta a uma ação ou o evento. Pode ver e gerir tarefas agendadas no programador de tarefas, ativar e desativá-las conforme necessário, executá-las ou utilizá-los como modelos e definir condições sob as quais as tarefas de início.

Além disso, as tarefas agendadas são fornecidos com um conjunto personalizado de cmdlets para a respetiva gestão. Os cmdlets permitem-lhe criar, editar, gerir, desativar e volte a ativar a tarefas agendadas, criar os acionadores de tarefa agendada e definir as opções de tarefa agendada.

Para obter mais informações sobre tarefas agendadas, consulte [about_Scheduled_Jobs](https://technet.microsoft.com/library/3b546629-703c-4939-b44f-52dd567bce92).

### <a name="windows-powershell-language-enhancements"></a>Melhoramentos do Windows PowerShell idioma
Windows PowerShell 3.0 inclui muitas funcionalidades que foram concebidas para tornar o respetivo idioma mais simples e mais fácil de utilizar e para evitar erros comuns. As melhorias incluem propriedades de enumeração, contagem e um comprimento de propriedade em objetos escalares, novo operadores de redirecionamento, o modificador do âmbito $Using, PSItem formatação de script automático de variável, flexível, atributos de variáveis, atributo simplificada argumentos, nomes de comando numérico, o operador de análise de parar, «splatting» de matriz melhorada, novo operadores de bits, dicionários ordenados, PSCustomObject conversão e ajuda baseada no comentário melhorada.

### <a name="new-core-cmdlets"></a>Novos Cmdlets de núcleo
Foram adicionados novos cmdlets para a instalação do núcleo do Windows PowerShell, incluindo cmdlets para gerir tarefas agendadas, sessões desligadas, integração de CIM e o sistema de ajuda Atualizável.

|||
|-|-|
|Adicionar-JobTrigger|Novo-JobTrigger|
|Connect-PSSession|Novo PSSessionConfigurationFile|
|ConvertFrom Json|New-PSTransportOption|
|ConvertTo-Json|Novo-PSWorkflowExecutionOption|
|Disable-JobTrigger|Novo PSWorkflowSession|
|Disable-ScheduledJob|Novo ScheduledJobOption|
|Desligar-PSSession|Novo-WinEvent.|
|Enable-JobTrigger|Receber-PSSession|
|Enable-ScheduledJob|Registar CimIndicationEvent|
|Get-CimAssociatedInstance|Register-ScheduledJob|
|Get-CimClass|Remover CimInstance|
|Get-CimInstance|Remove-CimSession|
|Get-CimSession|Remover TypeData|
|Get-ControlPanelItem|Mudança de nome de computador|
|Get-IseSnippet|Resume-Job|
|Get-JobTrigger|Save-Help|
|Get-ScheduledJob|Conjunto CimInstance|
|Get-ScheduledJobOption|Set-JobTrigger|
|Get-TypeData|Set-ScheduledJob|
|Importar IseSnippet|Conjunto ScheduledJobOption|
|AsWorkflow invocar|Mostrar comando|
|CimMethod invocar|Mostrar ControlPanelItem|
|RestMethod invocar|Suspend-Job|
|WebRequest invocar|Teste PSSessionConfigurationFile|
|Novo CimInstance|Ficheiro de desbloqueio|
|Novo-CimSession|Anular o registo-ScheduledJob|
|Novo CimSessionOption|Update-Help|
|Novo IseSnippet||

### <a name="improvements-to-existing-core-cmdlets-and-providers"></a>Melhoramentos para os Cmdlets de núcleo existente e fornecedores
Windows PowerShell 3.0 inclui novas funcionalidades para os cmdlets existentes, incluindo a sintaxe simplificada e novos parâmetros para os seguintes cmdlets: os cmdlets do computador, os cmdlets CSV, Get-ChildItem, Get-Command, Get-conteúdo, histórico de Get, objeto de medida de segurança cmdlets Select-Object, selecione-String, caminho de divisão, processo de início, Tee-Object, Test-Connection, adicionar membro e cmdlets do WMI.

Os fornecedores do Windows PowerShell foram também significativamente melhorados, incluindo o suporte de fornecedor de certificados para gerir certificados de Secure Socket Layer (SSL) para alojamento web, o suporte para credenciais, unidades de rede persistente e fluxos de dados alternativos no unidades de sistema de ficheiros.

### <a name="remote-module-import-and-discovery"></a>Importação do módulo remoto e a deteção
Windows PowerShell 3.0 expande a deteção de módulo, importar e capacidades de gestão remota implícita em computadores remotos. Os cmdlets do módulo obter módulos em computadores remotos e importe os módulos no computador local ou remoto ao utilizar a comunicação remota do Windows PowerShell. Novo suporte de sessão do CIM permite-lhe utilizar o CIM e o WMI para gerir computadores não-Windows através da importação de comandos no computador local que executam implicitamente no computador remoto.

Para obter mais informações, consulte os tópicos de ajuda para o [Get-Module](https://technet.microsoft.com/library/2cccd4c4-9a21-4c77-b691-984ee57242e1) e [Import-Module](https://technet.microsoft.com/library/af616c24-e122-4098-930e-1e3ea2080ade) cmdlets.

### <a name="enhanced-tab-completion"></a>Conclusão de separador Avançado
Conclusão de separador na consola do Windows PowerShell agora conclui os nomes dos cmdlets, parâmetros, os valores de parâmetros, enumerações, .NET Frameworks tipos, COM objetos, diretórios ocultos e muito mais. A funcionalidade de conclusão de separador foi completamente reescrita com base num novo parser e a árvore de sintaxe abstrato para suportar cenários mais, incluindo árvores de análise de memória e a conclusão de separador midline.

### <a name="module-auto-loading"></a>Carregamento do módulo automático
O [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) cmdlet agora obtém todos os cmdlets e funções de todos os módulos que estão instalados no computador, mesmo que o módulo não é importado para a sessão atual.

Quando obtiver o cmdlet que precisa, pode utilizá-lo imediatamente sem importar todos os módulos. Módulos do Windows PowerShell agora são importados automaticamente quando utiliza qualquer cmdlet no módulo. Já não terá de procurar o módulo e importá-lo para utilizar os cmdlets.

A importação automática de módulos é acionado utilizando o cmdlet num comando, em execução **Get-Command** para um cmdlet sem carateres universais ou em execução [Get-Help](https://technet.microsoft.com/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) para um cmdlet sem carateres universais.

Pode ativar, desativar e configurar a importação automática de módulos, utilizando o **$PSModuleAutoLoadingPreference** variável de preferência.

Para obter mais informações, consulte [about_Modules [v4]](https://technet.microsoft.com/library/94f57429-a539-4aee-bb0d-205cd7e801f9), [about_Preference_Variables [v4]](https://technet.microsoft.com/library/31344314-be29-4286-b039-afa5460cbe8b)e os tópicos de ajuda para o [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) e [Import-Module ](https://technet.microsoft.com/library/af616c24-e122-4098-930e-1e3ea2080ade) cmdlets.

### <a name="module-experience-improvements"></a>Melhoramentos de experiência de módulo
Windows PowerShell 3.0 oferece suporte de funcionalidades avançadas para módulos, incluindo as seguintes novas funcionalidades.

1. Registo de módulo de módulos individuais (LogPipelineExecutionDetails) e a nova definição de política de grupo "Ativar no módulo registo"

2. Expandido objetos de módulos que expõem os valores do manifesto do módulo

3. Novo **ExportedCommands** aninhada de propriedade de módulos, incluindo módulos, o que combina os comandos de todos os tipos

4. Deteção melhorada de módulos (anular importados) disponíveis, incluindo a permitir que o **caminho** e **ListAvailable** parâmetros no mesmo comando

5. Novo **DefaultCommandPrefix** chave em manifestos de módulo que evita o nome entra em conflito sem alterar o código do módulo.

6. Melhorado módulo os requisitos, incluindo completamente qualificado módulos necessários com versão e GUID e importar automático de módulos necessários

7. Operação quieter e simplificada do [New-ModuleManifest](https://technet.microsoft.com/library/512adced-f42f-4e88-ba7c-834fc9e5d047) cmdlet.

8. Novo **módulo** parâmetro #Requires

9. Melhorado [Import-Module](https://technet.microsoft.com/library/af616c24-e122-4098-930e-1e3ea2080ade) cmdlet com ambos **MinimumVersion** e **RequiredVersion** parâmetros.

### <a name="simplified-command-discovery"></a>Deteção de comando simplificada
Já não terá de importar todos os módulos para detetar os comandos disponíveis para a sua sessão. No Windows PowerShell 3.0, o [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) cmdlet obtém todos os comandos de todos os módulos instalados. Além disso, se utilizar um comando, o módulo que exporta o comando é importado automaticamente para a sua sessão.

A nova [Mostrar comando](https://technet.microsoft.com/library/65bba50b-91a8-49d5-80a2-a30fc684ba41) cmdlet foi concebido especialmente para principiantes. Pode procurar comandos numa janela. Pode ver todos os comandos ou pelo módulo de filtro, importar um módulo ao clicar num botão, utilize as caixas de texto e na lista pendente para construir um comando válido e, em seguida, copiar ou execute o comando sem nunca sair da janela.

### <a name="improved-logging-diagnostics-and-group-policy-support"></a>Registo melhorado, diagnóstico e suporte de política de grupo
Windows PowerShell 3.0 melhora o registo e rastreio suporte para os comandos e módulos com o suporte de rastreio de eventos em registos do Windows (ETW), um editáveis **LogPipelineExecutionDetails** propriedade de módulos e o "ativar no módulo Grupo de registo"definição de política. Agora pode obter os valores dos parâmetros de detalhes de registo ao apresentar as propriedades de registo.

### <a name="formatting-and-output-improvements"></a>Formatação e melhoramentos de saída
Formatação novo e de saída melhoramentos melhorar a eficiência de todos os utilizadores do Windows PowerShell. As melhorias incluem o redirecionamento de saída para todos os fluxos, um cmdlet de tipo de atualização avançado que adicione dinamicamente sem Format.ps1xml ficheiros, moldar o texto no resultado, os tipos predefinidos propriedades de formatação de objetos personalizados, o **PSCustomObject** tipo melhorado formatação para objetos WMI e objetos heterogéneos e suporte para detetar as sobrecargas do método.

### <a name="enhanced-console-host-experience"></a>Experiência de anfitrião da consola avançada
O programa de anfitrião do Windows PowerShell consola tem novas funcionalidades no Windows PowerShell 3.0, incluindo apartamento com thread único por predefinição. A nova opção "Executar com PowerShell" no Explorador de ficheiros permite-lhe executar scripts numa sessão sem restrições apenas clicando com o. Novo lógica de iniciação de anfitrião da consola é iniciada mais rápida do Windows PowerShell e novos tipos de letra permitem-lhe personalizar a experiência de janela de consola familiar.

Para obter mais informações, consulte [about_Run_With_PowerShell](https://technet.microsoft.com/library/c9d9ca5f-eff9-4409-be9d-e43b5b4087eb).

### <a name="new-cmdlet-and-hosting-apis"></a>Novo Cmdlet e alojamento de APIs
O novo Cmdlet API e que aloja a API incluem a árvore de sintaxe avançadas público (AST) APIs e APIs para paginação de pipeline, pipelines aninhadas, conclusão de separador de conjuntos de espaço de execução, Windows RT, o atributo de cmdlet obsoleto e verbo e substantivo propriedades do objeto FunctionInfo.

### <a name="performance-improvements"></a>Melhorias de desempenho
Melhorias de desempenho significativas no Windows PowerShell provenientes o analisador de idioma novo, o que está incorporado no dinâmica Runtime idioma (DLR) no .NET Framework 4., juntamente com a compilação de scripts de tempo de execução, melhoramentos do motor fiabilidade e alterações para o algoritmo do [Get-ChildItem](https://technet.microsoft.com/library/75cf79bb-4db6-4a67-8c36-3d20754e2190) que melhorar o desempenho dele, especialmente quando as partilhas de rede de procura.

### <a name="runas-and-shared-host-support"></a>Suporte de anfitriões partilhado e RunAs
Windows PowerShell 3.0 inclui suporte para funcionalidades RunAs e anfitriões partilhado.

O *RunAs* funcionalidade, concebida para o fluxo de trabalho do Windows PowerShell, permite que os utilizadores de uma configuração de sessão a criar sessões que são executados com a permissão de uma conta de utilizador partilhadas. Isto permite que os utilizadores com menos privilégios executar scripts e comandos específicos com permissões de administrador e reduz a necessidade de adicionar utilizadores menos sénior ao grupo de administradores.

O **SharedHost** funcionalidade permite que vários utilizadores em vários computadores para ligar a uma sessão de fluxo de trabalho em simultâneo e monitorizar o progresso de um fluxo de trabalho. Os utilizadores podem iniciar um fluxo de trabalho num computador e, em seguida, ligar à sessão do fluxo de trabalho noutro computador sem desligar a sessão do computador original. Os utilizadores têm de ter as mesmas permissões e utilizar a mesma configuração de sessão. Para obter mais informações, consulte "Em execução um Windows PowerShell Workflow" na introdução ao fluxo de trabalho do Windows PowerShell.

### <a name="special-character-handling-improvements"></a>Melhoramentos de processamento de caráter especial
Para melhorar a capacidade do Windows PowerShell 3.0 interpretar e processa corretamente caracteres especiais, o **LiteralPath** parâmetro, que processa os carateres especiais em caminhos, é válido em quase todos os cmdlets que tenham um  **Caminho** parâmetro, incluindo a nova [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) e [Save-Help](https://technet.microsoft.com/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa) cmdlets. O analisador também inclui uma lógica especial para melhorar o processamento do caráter backtick (\`) e parênteses Retos nos nomes de ficheiros e caminhos.

## <a name="see-also"></a>Consulte Também
- [about_Windows_PowerShell_5.0](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_powershell_5.0?view=powershell-5.0)
- [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116)