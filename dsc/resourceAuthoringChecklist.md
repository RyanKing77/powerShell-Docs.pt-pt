---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, do powershell, a configuração, a configuração
title: Lista de verificação de criação de recursos
ms.openlocfilehash: 39f652b458702dc7e815ab4b2f965e6728fa1b51
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="resource-authoring-checklist"></a>Lista de verificação de criação de recursos
Esta lista de verificação se uma lista de melhores práticas quando criar um novo recurso do DSC.
## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a>Módulo de recursos contém ficheiros. psd1 e schema.mof para cada recurso
Certifique-se de que o recurso tem estrutura correta e contém todos os ficheiros necessários. Cada módulo de recurso deve conter um ficheiro. psd1 e todos os recursos de compostos não devem ter schema.mof ficheiro. Recursos que contém o esquema não serão listados por **Get-DscResource** e os utilizadores não poderão utilizar o intellisense ao escrever código contra os módulos no ISE.
A estrutura de diretórios para xRemoteFile recurso, o que faz parte do [módulo de recurso xPSDesiredStateConfiguration](https://github.com/PowerShell/xPSDesiredStateConfiguration), procura da seguinte forma:


```
xPSDesiredStateConfiguration
    DSCResources
        MSFT_xRemoteFile
            MSFT_xRemoteFile.psm1
            MSFT_xRemoteFile.schema.mof
    Examples
        xRemoteFile_DownloadFile.ps1
    ResourceDesignerScripts
        GenerateXRemoteFileSchema.ps1
    Tests
        ResourceDesignerTests.ps1
    xPSDesiredStateConfiguration.psd1
```

## <a name="resource-and-schema-are-correct"></a>Recursos e de esquema estão corretos # #
Verifique o esquema de recursos (*. schema.mof) ficheiros. Pode utilizar o [Designer de recursos de DSC](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) para ajudar a desenvolver e testar o esquema.
Certifique-se de que:
- Tipos de propriedade são corretos (por exemplo, não utilize cadeia para propriedades que aceitam valores numéricos, deve utilizar UInt32 ou outros tipos numéricos em vez disso)
- Atributos de propriedade estão corretamente especificados como: ([chave], [necessário], [escrever], [ler])
- Pelo menos um parâmetro no esquema tem de ser marcado como [chave]
- [ler] propriedade não coexistir juntamente com qualquer um dos: [necessário], [a chave], [escrever]
- Se forem especificadas várias qualificadores exceto [leitura], [a chave] tem precedência
- Se [escrever] e [necessário] especificado, em seguida, tem precedência [necessário]
- ValueMap especificado apropriado

Exemplo:
```
[Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
```

- Nome amigável for especificado e confirma para as convenções de nomenclatura de DSC

Exemplo: ```[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]```

- Cada campo tem uma descrição com significado. O repositório do PowerShell GitHub tem bons exemplos, tais como [o. schema.mof para xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)

Além disso, deve utilizar **teste xDscResource** e **teste xDscSchema** os cmdlets da [Designer de recursos de DSC](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) para verificar automaticamente o recurso e o esquema:
```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```
Por exemplo:
```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a>Recurso carrega sem erros ##
Verifique se o módulo de recurso pode ser carregado com êxito.
Isto pode ser conseguido manualmente, executando `Import-Module <resource_module> -force ` e confirmar que ocorreram sem erros ou ao escrever a automatização de teste. Em caso desta última opção, pode seguir esta estrutura no seu caso de teste:
```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw “Module was not imported correctly. Errors returned: $error”
}
```
## <a name="resource-is-idempotent-in-the-positive-case"></a>Recurso é idempotent no caso de positivo
Uma das características fundamentais de recursos de DSC está a ser idempotence. Significa que aplicar uma configuração de DSC que contém esse recurso várias vezes será sempre alcançar o mesmo resultado. Por exemplo, vamos criar uma configuração que contém o seguinte recurso do ficheiro:
```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```
Depois de aplicá-la pela primeira vez, deverá aparecer test.txt de ficheiro na pasta C:\test. No entanto, as execuções subsequentes da configuração da mesma não devem alterar o estado da máquina (por exemplo, não existem cópias do ficheiro test.txt devem ser criadas).
Para garantir a um recurso idempotent repetidamente pode chamar **conjunto TargetResource** quando testar o recurso diretamente ou chamar **início DscConfiguration** várias vezes ao fazer o teste de ponto a ponto. O resultado deve ser o mesmo após cada execução.


## <a name="test-user-modification-scenario"></a>Cenário de modificação de utilizador de teste ##
Ao alterar o estado da máquina e, em seguida, volte a executar DSC, pode verificar que **conjunto TargetResource** e **teste TargetResource** funcionar corretamente. Seguem-se passos que deve tomar:
1.  Começar a utilizar o recurso não no estado pretendido.
2.  Execute a configuração com o seu recurso
3.  Certifique-se **teste DscConfiguration** devolve True
4.  Modificar o item configurado para ser fora do estado pretendido
5.  Certifique-se **teste DscConfiguration** devolve false Eis um exemplo mais concreto através de recursos de registo:
1.  Começar a utilizar a chave de registo não no estado pretendido
2.  Executar **início DscConfiguration** com uma configuração para colocá-la no estado pretendido e certifique-se de passa.
3.  Executar **teste DscConfiguration** e certifique-se de que devolve true
4.  Modifique o valor da chave para que não esteja no estado pretendido
5.  Executar **teste DscConfiguration** e certifique-se de que devolve false
6.  Funcionalidade de GET-TargetResource foi verificada através de Get-DscConfiguration

Detalhes do estado atual do recurso deve ser devolvido por Get-TargetResource. Certifique-se para testá-lo por Get-DscConfiguration ao chamar depois de aplicar a configuração e a verificar que saída corretamente reflete o estado atual da máquina. É importante para testá-lo em separado, uma vez que os problemas nesta área deixa de aparecer quando chamar DscConfiguration de início.

## <a name="call-getsettest-targetresource-functions-directly"></a>Chamar **Get/conjunto/teste-TargetResource** funciona diretamente ##

Certifique-se de que testa o **Get/conjunto/teste-TargetResource** funções implementadas no seu recurso pelo diretamente ao chamá-los e verificar que estão a funcionar conforme esperado.

## <a name="verify-end-to-end-using-start-dscconfiguration"></a>Certifique-se através de ponto a ponto **DscConfiguration de início** ##

Testar **Get/conjunto/teste-TargetResource** funções chamando-los diretamente é importante, mas não todos os problemas serão detetados desta forma. Deve focar-se parte significativo dos testes no utilizando **início DscConfiguration** ou o servidor de solicitação. Na verdade, esta é a forma como os utilizadores utilizarão o recurso de, pelo que não underestimate significância deste tipo de testes.
Tipos possíveis problemas:
- Credenciais/sessão pode comportar-se de forma diferente porque o agente de DSC é executado como um serviço.  Lembre-se de que testar quaisquer funcionalidades aqui ponto a ponto.
- Erros de saída por **início DscConfiguration** poderão ser diferentes das apresentado ao chamar o **conjunto TargetResource** diretamente a funcionar.

## <a name="test-compatability-on-all-dsc-supported-platforms"></a>Teste de compatibilidade no DSC todas as plataformas suportadas ##
Recursos deverão funcionar em todas as plataformas de DSC suportada (Windows Server 2008 R2 e mais recentes). Instale o WMF mais recente (Windows Management Framework) no seu SO para obter a versão mais recente do DSC. Se o recurso não funciona em algumas destas plataformas por predefinição, uma mensagem de erro específica deve ser devolvida. Além disso, certifique-se de que o seu recurso verifica se os cmdlets que são chamar são presentes no computador específico. Windows Server 2012 adicionados um grande número de novos cmdlets que não estão disponíveis no Windows Server 2008 R2 o, mesmo com WMF instalado.

## <a name="verify-on-windows-client-if-applicable"></a>Certifique-se num cliente Windows (se aplicável) ##
Um intervalo de teste muito comum está a verificar o recurso apenas em versões de servidor do Windows. Muitos recursos também foram concebidos para funcionar no SKUs de cliente, para que o se o que acontece no seu caso, não se esqueça de testá-lo no bem essas plataformas.
## <a name="get-dscresource-lists-the-resource"></a>Get-DSCResource apresenta uma lista de recursos ##
Depois de implementar o módulo, chamar Get-DscResource deve listar o recurso dos restantes como resultado. Se não é possível localizar o recurso na lista, certifique-se de que o ficheiro schema.mof para esse recurso existe.
## <a name="resource-module-contains-examples"></a>Módulo de recursos contém exemplos ##
Criar exemplos de qualidade que irão ajudar os outros compreender como utilizá-la. Isto é crucial, especialmente, uma vez que muitos utilizadores tratar código de exemplo como documentação.
- Em primeiro lugar, deve determinar os exemplos que serão incluídos com o módulo – no mínimo, deve abranger os casos de utilização mais importantes para o seu recurso:
- Se o módulo contiver vários recursos que necessitam para funcionarem em conjunto para um cenário ponto-a-ponto, o exemplo básico do ponto-a-ponto ideal seria ter primeiro.
- Os exemplos iniciais devem ser muito simples – como começar com os recursos em pequenos segmentos geríveis (por exemplo, criar um novo VHD)
- Exemplos subsequentes devem tirar partido dessas exemplos (por exemplo, criar uma VM a partir de um VHD, remover a VM, modificar VM) e mostram a funcionalidade avançada (por exemplo, criar uma VM com memória dinâmica)
- Configurações de exemplo devem ser parametrizadas (todos os valores devem ser transmitidos para a configuração como parâmetros e não deverá haver nenhum valores codificado):
```powershell
configuration Sample_xRemoteFile_DownloadFile
{
    param
    (
        [string[]] $nodeName = 'localhost',

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $destinationPath,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $uri,

        [String] $userAgent,

        [Hashtable] $headers
    )

    Import-DscResource -Name MSFT_xRemoteFile -ModuleName xPSDesiredStateConfiguration

    Node $nodeName
    {
        xRemoteFile DownloadFile
        {
            DestinationPath = $destinationPath
            Uri = $uri
            UserAgent = $userAgent
            Headers = $headers
        }
    }
}
```
- É uma boa prática incluir (comentado out) exemplo de como chamar a configuração com os valores reais no final do script de exemplo.
Por exemplo, na configuração acima não se encontra necessariamente óbvios que é a melhor forma de o especificar UserAgent:

`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` Caso em que um comentário pode clarificar a execução da configuração pretendida:
```
<#
Sample use (parameter values need to be changed according to your scenario):

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
-userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
#>
```
- Para cada exemplo, escreva uma breve descrição que explica o que faz e o significado dos parâmetros.
- Certifique-se exemplos abrangem a maioria dos cenários importantes para o seu recurso e se não há nada em falta, certifique-se de que todos os executar e colocar a máquina no estado pretendido.

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a>Mensagens de erro são fáceis de compreender e ajudar utilizadores a resolver problemas ##
Mensagens de erro boa devem ser:
- Não existe: O problema maior com mensagens de erro é que não existem muitas vezes, por isso, certifique-se de que existem.
- Fácil de compreender: códigos de erros humanos legível, não obscura
- Preciso: Descrevem o que é exatamente o problema
- Constructive: Conselhos saber como corrigir o problema
- Um: Não blame utilizador ou marca-los sentir incorretos Certifique-se verificar erros em cenários de ponto a ponto (utilizando **início DscConfiguration**), porque diferem das devolvido ao executar diretamente as funções de recursos.

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a>Mensagens de registo são fáceis de compreender e informativo (incluindo-verbose,-debug e registos ETW) ##
Certifique-se de que os registos debitados pelo recurso são fáceis de compreender e forneça o valor ao utilizador. Recursos devem saída todas as informações que poderão ser úteis para o utilizador, mas mais registos nem sempre é melhor. Deve evitar redundância e exportar dados que não fornecer valor adicional – não se alguém passar por centenas de entradas de registo para encontrar aquilo procura. Obviamente, não existem registos não é uma solução aceitável para este problema seja.

Quando o testar, também deve analisar verboso e registos de depuração (executando **início DscConfiguration** com-verbose e – depurar comutadores adequadamente), bem como registos ETW. Para ver registos de DSC ETW, aceda ao Visualizador de eventos e abra a seguinte pasta: aplicações e serviços da Microsoft - Windows - configuração de estado pretendido.  Por predefinição existe irá ser canal operacional, mas certifique-se de ativar registos analíticos e de depuração canais antes de executar a configuração.
Para ativar registos analíticos/depuração canais, pode executar o script abaixo:
```powershell
$statusEnabled = $true
# Use "Analytic" to enable Analytic channel
$eventLogFullName = "Microsoft-Windows-Dsc/Debug"
$commandToExecute = "wevtutil set-log $eventLogFullName /e:$statusEnabled /q:$statusEnabled   "
$log = New-Object System.Diagnostics.Eventing.Reader.EventLogConfiguration $eventLogFullName
if($statusEnabled -eq $log.IsEnabled)
{
    Write-Host -Verbose "The channel event log is already enabled"
    return
}
Invoke-Expression $commandToExecute
```
## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a>Implementação de recursos não contém codificado caminhos ##
Certifique-se existem não existem caminhos codificado da implementação de recursos, particularmente se estes partem do princípio de idioma (en-us), ou quando existem variáveis do sistema que podem ser utilizadas.
Se o recurso necessário aceder aos caminhos específicos, utilize as variáveis de ambiente em vez de codificar o caminho, dado que pode divergir nas outras máquinas.

Exemplo:

Em vez de:
```
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
 ```
Pode escrever:
```
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)}
```
## <a name="resource-implementation-does-not-contain-user-information"></a>Implementação de recursos não contém informações de utilizador ##
Certificar-se de que não são nomes de e-mail, as informações da conta ou nomes de pessoas no código.
## <a name="resource-was-tested-with-validinvalid-credentials"></a>Recurso foi testado com credenciais válidas/inválido. ##
Se o seu recurso aceita uma credencial como parâmetro:
- Certifique-se o recurso funciona quando o sistema Local (ou a conta de computador para recursos remotos) não tem acesso.
- Certifique-se de que funciona a recursos com uma credencial especificada para obter, definir e teste
- Se o seu recurso acede partilhas, teste todos os variantes que tem de suportar, tais como:
  - Partilhas de padrão do windows.
  - Partilhas DFS.
  - Partilhas SAMBA (se pretende suportar Linux.)

## <a name="resource-does-not-require-interactive-input"></a>Recurso não necessita de entrada interativa ##
**Get/conjunto/teste-TargetResource** funções deve ser executadas automaticamente e não terá de aguardar para o utilizador de entrada em qualquer fase de execução (por exemplo, não deve utilizar **Get-Credential** dentro estas funções). Se necessitar de intervenção do utilizador, deve transmiti-lo para a configuração como parâmetro durante a fase de compilação.
## <a name="resource-functionality-was-thoroughly-tested"></a>Funcionalidade de recurso foi testada exaustivamente ##
Esta lista de verificação contém itens que são importantes para testar e/ou são frequentemente omitidos. Será bunch dos testes, principalmente funcionais aqueles que serão específicos para o recurso estiver a testar e não são aqui mencionados. Não se esqueça sobre casos de teste negativos.
## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a>Recomendado: módulo de recursos contém a pasta de testes com script de ResourceDesignerTests.ps1 ##
É uma boa prática para criar a pasta "testes" no interior do módulo de recurso, criar ficheiro de ResourceDesignerTests.ps1 e adicionar testes utilizando **teste xDscResource** e **teste xDscSchema** para todos os recursos em determinados módulo.
Desta forma pode validar rapidamente esquemas de todos os recursos dos módulos indicados e efetue uma sanity verificar antes de publicar.
Para xRemoteFile, ResourceTests.ps1 pode ter um aspeto tão simples como:
```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```
##<a name="best-practice-resource-folder-contains-resource-designer-script-for-generating-schema"></a>Recomendado: a pasta do recurso contém script estruturador do recurso para gerar o esquema # #
Cada recurso deve conter um script de estruturador do recurso que gera um esquema de mof do recurso. Este ficheiro deve ser colocado na <ResourceName>\ResourceDesignerScripts e será nomeado gerar<ResourceName>Schema.ps1 para o recurso de xRemoteFile este ficheiro deverá ser chamado GenerateXRemoteFileSchema.ps1 e conter:
```powershell
$DestinationPath = New-xDscResourceProperty -Name DestinationPath -Type String -Attribute Key -Description 'Path under which downloaded or copied file should be accessible after operation.'
$Uri = New-xDscResourceProperty -Name Uri -Type String -Attribute Required -Description 'Uri of a file which should be copied or downloaded. This parameter supports HTTP and HTTPS values.'
$Headers = New-xDscResourceProperty -Name Headers -Type Hashtable[] -Attribute Write -Description 'Headers of the web request.'
$UserAgent = New-xDscResourceProperty -Name UserAgent -Type String -Attribute Write -Description 'User agent for the web request.'
$Ensure = New-xDscResourceProperty -Name Ensure -Type String -Attribute Read -ValidateSet "Present", "Absent" -Description 'Says whether DestinationPath exists on the machine'
$Credential = New-xDscResourceProperty -Name Credential -Type PSCredential -Attribute Write -Description 'Specifies a user account that has permission to send the request.'
$CertificateThumbprint = New-xDscResourceProperty -Name CertificateThumbprint -Type String -Attribute Write -Description 'Digital public key certificate that is used to send the request.'

New-xDscResource -Name MSFT_xRemoteFile -Property @($DestinationPath, $Uri, $Headers, $UserAgent, $Ensure, $Credential, $CertificateThumbprint) -ModuleName xPSDesiredStateConfiguration2 -FriendlyName xRemoteFile
```
## <a name="best-practice-resource-supports--whatif"></a>Recomendado: recurso suporta - whatif ##
Se o recurso está a efetuar operações "perigosos", é recomendável implementar - whatif funcionalidade. Depois de terminar, certifique-se de que a saída de whatif descreve corretamente operações que aconteceria se o comando foi executado sem whatif comutador.
Além disso, certifique-se de que não é executado operações (são efetuadas sem alterações para o estado do nó) quando o comutador – whatif está presente.
Por exemplo, vamos supor que iremos estiver a testar o recurso do ficheiro. Segue-se configuração simple que cria o ficheiro "test.txt" com conteúdo "teste":
```powershell
configuration config
{
    node localhost
    {
        File file
        {
            Contents="test"
            DestinationPath="C:\test\test.txt"
        }
    }
}
config
```
Se podemos compilar e, em seguida, executar a configuração com o parâmetro – whatif, o resultado é informar-nos exatamente que acontece quando é executada a configuração. A configuração do próprio no entanto não foi executada (o ficheiro de test.txt não foi criado).
```powershell
Start-DscConfiguration -path .\config -ComputerName localhost -wait -verbose -whatif
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer CHARLESX1 with user sid
S-1-5-21-397955417-626881126-188441444-5179871.
What if: [X]: LCM:  [ Start  Set      ]
What if: [X]: LCM:  [ Start  Resource ]  [[File]file]
What if: [X]: LCM:  [ Start  Test     ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]: LCM:  [ End    Test     ]  [[File]file]  in 0.0270 seconds.
What if: [X]: LCM:  [ Start  Set      ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]:                            [C:\test\test.txt] Creating and writing contents and setting attributes.
What if: [X]: LCM:  [ End    Set      ]  [[File]file]  in 0.0180 seconds.
What if: [X]: LCM:  [ End    Resource ]  [[File]file]
What if: [X]: LCM:  [ End    Set      ]
VERBOSE: [X]: LCM:  [ End    Set      ]    in  0.1050 seconds.
VERBOSE: Operation 'Invoke CimMethod' complete.
```

Esta lista não é exaustiva, mas abrange a muitas questões importantes que podem ser encontrados ao conceber, desenvolver e testar a recursos de DSC.