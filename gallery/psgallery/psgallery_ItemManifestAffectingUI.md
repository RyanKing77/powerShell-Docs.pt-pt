# <a name="item-manifest-values-that-impact-the-powershell-gallery-ui"></a>Valores de manifesto do item que afetam a IU de galeria do PowerShell

Este tópico fornece os publicadores com informações de resumo sobre como modificar o manifesto para as publicações de galeria do PowerShell para que as funcionalidades de PowerShellGet cmdlets e a IU de galeria do PowerShell serão afetadas. Este conteúdo está organizado por onde a alteração será apresentada, começando com a secção do System center, em seguida, a área de navegação à esquerda. Há uma secção de detalhes de etiquetas de abrangente, que identifica importante etiquetas, bem como algumas das mais frequentemente utilizadas etiquetas. Existem dois tópicos fornecem exemplos de manifesto: 

* Para módulos, consulte [manifesto de módulo de atualização](https://docs.microsoft.com/powershell/gallery/psget/module/psget_update-modulemanifest)
* Para scripts, consulte [criar ficheiro de Script com metadados](https://docs.microsoft.com/powershell/gallery/psget/script/psget_new-scriptfileinfo)

## <a name="powershell-gallery-feature-elements-controlled-by-the-manifest"></a>Elementos da galeria do PowerShell de funcionalidade controlados pelo manifesto

A tabela abaixo mostra os elementos da página de item de galeria do PowerShell da IU que são controlados pelo fabricante.
Cada item indica se pode ser controlado pelo manifesto de módulo ou script.

| Elemento de IU | Descrição | Módulo | Script | 
| --- | --- | --- | --- |
| **Título** | Este é o nome do item de que é publicado na Galeria  | Não | Não |
| **Versão** | A versão apresentada é a cadeia de versão nos metadados, e um pré-lançamento se for especificado. A parte da versão de um manifesto de módulo principal é o ModuleVersion. Para obter um script, é identificado como. VERSÃO. Se não for especificada uma cadeia de versão de pré-lançamento,-será anexado ao ModuleVersion de módulos, ou especificada como parte da. VERSÃO de scripts. Não há documentação para especificar as cadeias de pré-lançamento no [módulos](https://docs.microsoft.com/en-us/powershell/gallery/psget/module/prereleasemodule)e, em [scripts](https://docs.microsoft.com/en-us/powershell/gallery/psget/script/prereleasescript) | Sim | Sim |
| **Descrição** | Esta é a descrição no manifesto do módulo, e um manifesto do ficheiro de script é. DESCRIÇÃO | Sim | Sim |
| **Solicite a aceitação de licença** | Um módulo pode exigir que o utilizador aceitar uma licença, modificando o manifesto de módulo com RequireLicenseAcceptance = $true, fornecendo um LicenseURI e fornecer um ficheiro de license.txt na raiz da pasta do módulo. Estão disponíveis informações adicionais no [exigir a aceitação de licença](https://docs.microsoft.com/en-us/powershell/gallery/psgallery/psgallery_requires_license_acceptance) tópico. | Sim | Não |
| **Notas de versão** | Para módulos, esta informação é desenhada da secção ReleaseNotes, sob PSData\PrivateData. Manifestos de script, é o. Elemento RELEASENOTES. | Sim | Sim |
| **Proprietários** | Os proprietários são a lista de utilizadores na galeria do PowerShell que pode atualizar um item. A lista de proprietário não está incluída no manifesto de item. Documentação adicional descreve como [Gerir proprietários do item](https://docs.microsoft.com/en-us/powershell/gallery/psgallery/managing-item-owners). | Não | Não |
| **autor** | Isto está incluído no manifesto como o autor do módulo e no manifesto script como. AUTOR. O campo autor é frequentemente utilizado para especificar uma empresa ou organização associada a um item. | Sim | Sim |
| **Copyright** | Este é o campo de direitos de autor no manifesto do módulo, e. COPYRIGHT no manifesto script. | Sim | Sim |
| **FileList** | A lista de ficheiros é desenhada do pacote quando este for publicado na galeria do PowerShell. Não é controllable pelas informações de manifesto. Nota: existe é um ficheiro de .nuspec adicionais listado com cada item da galeria do PowerShell que não está presente depois de instalar o item num sistema. Este é o manifesto do pacote Nuget para o item e pode ser ignorada. | Não | Não |
| **Etiquetas** | Para módulos, as etiquetas estão incluídas em PSData\PrivateData. Para scripts, a secção é assinaladas como. ETIQUETAS. Tenha em atenção que as etiquetas não podem conter espaços, mesmo quando são aspas. As etiquetas têm requisitos adicionais e significados, que são descritos mais à frente neste tópico na seção Detalhes da etiqueta. | Sim | Sim |
| **Cmdlets** | Isto é fornecido no manifesto do módulo CmdletsToExport a utilizar. Tenha em atenção que a melhor prática é explicitamente lista os itens, em vez de utilizar o caráter universal "*", conforme que irá melhorar o desempenho do módulo de carga para os utilizadores. | Sim | Não |
| **Funções** | Isto é fornecido no manifesto do módulo FunctionsToExport a utilizar. Tenha em atenção que a melhor prática é explicitamente lista os itens, em vez de utilizar o caráter universal "*", conforme que irá melhorar o desempenho do módulo de carga para os utilizadores. | Sim | Não |
| **Recursos de DSC** | Para módulos que serão utilizados no PowerShell versão 5.0 e posterior, isto é fornecido no manifesto utilizando DscResourcesToExport. Se o módulo está a ser utilizado no PowerShell 4, o DSCResourcesToExport não deve ser utilizada como não é uma chave de manifesto suportada. (O DSC não estava disponível antes de PowerShell 4). | Sim | Não |
| **Fluxos de Trabalho** | Fluxos de trabalho são publicados para a galeria do PowerShell, como scripts e identificados como fluxos de trabalho (consulte [Connect-AzureVM](https://www.powershellgallery.com/packages/Connect-AzureVM/1.0/Content/Connect-AzureVM.ps1) para obter um exemplo) no código. Isto não for controlado pelo manifesto. | Não | Não |
| **Capacidades de função** | Esta será listada quando o módulo publicado na galeria do PowerShell contém um ou mais ficheiros de capacidade (.psrc) de função, que são utilizados pelo JEA. Consulte a documentação de JEA para obter mais detalhes sobre [capacidades de função](https://docs.microsoft.com/en-us/powershell/jea/role-capabilities). | Sim | Não |
| **Edições de PowerShell** | Isto é especificado no manifesto de módulo ou script. Para módulos concebidos para serem utilizados com o PowerShell 5.0 e abaixo, este são controlados utilizando etiquetas. Para ambiente de trabalho, utilize a tag PSEdition_Desktop e para o principal, utilizar a tag PSEdition_Core. Para módulos que serão utilizados apenas no PowerShell 5.1 e acima, há uma chave de CompatiblePSEditions no manifesto principal. Para obter detalhes adicionais, consulte a funcionalidade de edição de PS no [a documentação do PowerShell Get](https://docs.microsoft.com/en-us/powershell/gallery/psget/module/modulewithpseditionsupport). | Sim | Sim |
| **Dependências** | As dependências são os módulos na galeria do PowerShell que são declarados no módulo como RequiredModules ou no manifesto de script como #Requires – módulo (nome). | Sim | Sim |
| **Versão mínima do Powershell** | Isto pode ser especificado no manifesto módulo como PowerShellVersion | Sim | Não |
| **Histórico da versão** | O histórico da versão reflete as atualizações efetuadas a um módulo na galeria do PowerShell. Se uma versão de um item está oculta a utilizar a funcionalidade de eliminação, que será não ser apresentado no histórico de versão, exceto para os proprietários do item. | Não | Não |
| **Site do projeto** | O site de projeto é fornecido para módulos na secção Privatedata\PSData do manifesto do módulo especificando um ProjectURI. No manifesto de script, é controlada ao especificar. PROJECTURI. | Sim | Sim |
| **Licença** | É fornecida uma ligação de licença de módulos na secção Privatedata\PSData do manifesto do módulo especificando um LicenseURI. No manifesto de script, é controlada ao especificar. LICENSEURI. É importante ter em conta que se uma licença não é fornecida através de LicenseURI ou dentro de um módulo, em seguida, os termos de utilização para a galeria do PowerShell especificar os termos de utilização para o item. Consulte os termos de utilização para obter mais detalhes. | Sim | Sim |

## <a name="editing-item-details"></a>Editar detalhes do item

A página de item a editar de galeria do PowerShell permite alterar vários campos apresentados para um item, especificamente os publicadores:

* Título
* Descrição
* Resumo
* URL de ícone
* URL de página inicial do projeto
* Autores
* Copyright
* Etiquetas
* Notas de versão
* Necessita de licença

Esta abordagem não é, geralmente, recomendada, exceto quando for necessário para corrigir o que é apresentado para uma versão mais antiga de um módulo. Os utilizadores que adquirir o módulo irão ver que os metadados não corresponde ao conteúdo que é apresentado na galeria do PowerShell, gera as questões sobre o item. Frequentemente esta operação resultará compras vai para os proprietários do item para confirmar a alteração. É vivamente recomendado que qualquer altura que esta abordagem é utilizada, uma nova versão do item deve ser publicada com as alterações do mesmas. 

## <a name="tag-details"></a>Detalhes da etiqueta

As etiquetas são cadeias simples consumidores utilizado para localizar itens. As etiquetas são mais importantes quando são utilizados consistentemente entre o número de itens relacionados com o mesmo tópico. A utilização de várias versões do mesmo word (por exemplo da base de dados e bases de dados, ou teste e testar) fornece normalmente benefício pouco. As etiquetas são cadeias sensível de palavra única e não podem incluir espaços em branco. Se existir uma frase de acesso que se considerar que irão procurar utilizadores, adicione que a descrição do item e irá ser possível encontrá-lo nos resultados da pesquisa. Se estiver a tentar melhorar a legibilidade, utilize Pascal tem maiúsculas e minúsculas, hífen, um caráter de sublinhado ou período. Tenha cuidado sobre a criação de etiquetas invulgares, longas e complexas, como estes são frequentemente mal escritos. 

Existem etiquetas que são importantes a ter em atenção, como a galeria do PowerShell e PowerShellGet cmdlets tratá-los exclusivamente. PSEdition_Desktop PSEdition_Core são os exemplos específicos e descritas acima. 

Conforme indicado acima, as etiquetas fornecem o máximo valor quando são específicos e utilizados consistentemente entre o número de itens. Como um publicador tentar localizar as melhores etiquetas a utilizar, a abordagem mais fácil é procurar a galeria do PowerShell para as etiquetas que estiver a considerar. Idealmente, será devolvido de número de itens e as descrições de item irão alinhar com a utilização dessa palavra-chave. 

Para referência, aqui estão algumas etiquetas frequentemente utilizadas a partir de 14/12/2017. Em alguns casos, existem semelhante, mas talvez menos ideais das opções apresentadas junto a etiqueta.
É uma melhor prática para utilizar a Tag preferencial, como, que irá resultar num menor ruído e melhor resultados da pesquisa para consumidores. 


| **Etiqueta preferencial** | **Alternativas e notas** |
| --- | --- |
| **Azure** |  |
| **DSC** | DesiredStateConfiguration é desejável inferior, é demasiado longo |
| **ResourceManager** | É utilizada para descrever o grupo de processadores ARM e não deve ser utilizada para o Azure Resource Manager | **DSCResourceKit** |  |
| **SQL** |  |
| **AWS** |  |
| **DSCResource** |  |
| **Automatização** |  |
| **REST** |  |
| **ActiveDirectory** | AD não é atualmente utilizado por si só  |
| **SQLServer** |  |
| **DBA** |  |
| **Segurança** | Defesa é menos precisa |
| **base de dados** | Bases de dados (plural) é desejável inferior |
| **DevOps** |  |
| **Windows** |  |
| **Compilação** |  |
| **Implementação** | Implementar é utilizado um pouco menos frequentemente |
| **Na nuvem** |  |
| **GIT** |  |
| **Test** | Teste é inferior desejável |
| **VersionControl** | A versão é menos exatos, embora utilizados mais frequentemente  |
| **Logging** | Utilize preferencial de início de sessão como uma ação |
| **Registo** | Utilização preferencial de registo como uma coisa |
| **Backup** |  |
| **IaaS** |  |
| **Linux** |  |
| **IIS** |  |
| **AzureAutomation** |  |
| **Armazenamento** |  |
| **GitHub** |  |
| **Json** |  |
| **Exchange** |  |
| **Network** | Funcionamento em rede é semelhante, menos frequentemente utilizados |
| **SharePoint** |  |
| **Relatórios** | Relatórios é uma ação, o relatório é uma coisa |
| **Relatório** | Relatório é uma coisa |
| **WinRM** |  |
| **Monitorização** |  |
| **VSTS** |  |
| **Excel** |  |
| **Google** |  |
| **Color** |  |
| **DNS** |  |
| **Office365** | É preferível spelling saída Office. Office 365 é utilizado com menos frequência, embora mais curto | **Gitlab** |  |
| **Pester** |  |
| **AzureAD** |  |
| **HTML** |  |
| **Hyper-V** | Hyper-v é menos comuns, como uma etiqueta |
| **Configuração** |  |
| **ChatOps** |  |
| **PackageManagement** |  |
| **WMI** |  |
| **Firewall** |  |
| **Docker** |  |
| **Appveyor** |  |
| **AzureRm** | Utilizada principalmente para os módulos AzureRM |
| **Zip** |  |
| **MSI** |  |
| **Mac** |  |
| **PoshBot** |  |


