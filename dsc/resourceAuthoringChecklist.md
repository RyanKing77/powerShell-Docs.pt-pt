---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Lista de verificação de criação de recursos
ms.openlocfilehash: 91942a174bc6f38fa77c1925dc3c690ecf2ab34b
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893560"
---
# <a name="resource-authoring-checklist"></a>Lista de verificação de criação de recursos

Esta lista de verificação é uma lista de melhores práticas durante a criação de um novo recurso de DSC.

## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a>Módulo de recursos contém o ficheiro. psd1 e schema.mof para todos os recursos

Verifique se o seu recurso tem a estrutura correta e contém todos os ficheiros necessários. Cada módulo de recurso deve conter um ficheiro. psd1 e todos os recursos compostos não devem ter schema.mof ficheiro. Recursos que contém o esquema não serão listados por `Get-DscResource` e os utilizadores não poderão usar o intellisense ao escrever código contra esses módulos no ISE.
A estrutura de diretórios para o recurso de xRemoteFile, que faz parte do [módulo do recurso de xPSDesiredStateConfiguration](https://github.com/PowerShell/xPSDesiredStateConfiguration), seria semelhante ao seguinte:

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

## <a name="resource-and-schema-are-correct"></a>Esquema e de recursos estão corretos

Verifique se o esquema de recursos (*. schema.mof) ficheiros. Pode utilizar o [Designer de recursos de DSC](https://www.powershellgallery.com/packages/xDSCResourceDesigner) para ajudar a desenvolver e testar o seu esquema.
Certifique-se de que:

- Tipos de propriedade estão corretos (por exemplo, não utilizar cadeia de caracteres para propriedades que aceitam os valores numéricos, deve usar UInt32 ou outros tipos numéricos em vez disso)
- Atributos da propriedade estão corretamente especificados como: ([chave], [necessário], [escrever], [ler])
- Pelo menos um parâmetro no esquema tem de ser marcado como [chave]
- [ler] propriedade não coexistir juntamente com qualquer um dos: [necessário], [a chave], [escrever]
- Se vários qualificadores forem especificados, exceto [leitura], [a chave] tem precedência
- Se [escrever] e [necessário] são especificados, em seguida, tem precedência de [necessário]
- ValueMap é especificada quando apropriado exemplo:

  ```
  [Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
  ```

- Nome amigável é especificado e confirma as convenções de nomenclatura de DSC

  Exemplo: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`

- Cada campo tem descrição relevante. O repositório do GitHub do PowerShell possui bons exemplos, como [o. schema.mof para xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)

Além disso, deve usar **teste xDscResource** e **teste xDscSchema** cmdlets da [Designer de recursos de DSC](https://www.powershellgallery.com/packages/xDSCResourceDesigner) para verificar automaticamente o recurso e o esquema:

```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```

Por exemplo:

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a>Recurso for carregada sem erros

Verifique se o módulo de recurso pode ser carregado com êxito.
Isso pode ser conseguido manualmente, executando `Import-Module <resource_module> -force` e confirmar que nenhum erro ocorreu, ou ao escrever automação de teste. Em caso da última opção, pode seguir esta estrutura no seu caso de teste:

```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw “Module was not imported correctly. Errors returned: $error”
}
```

## <a name="resource-is-idempotent-in-the-positive-case"></a>Recurso é idempotent no caso positivo

Uma das características fundamentais de recursos de DSC está a ser idempotence. Isso significa que a aplicação de uma configuração de DSC contendo esse recurso várias vezes será sempre alcançar o mesmo resultado. Por exemplo, se criarmos uma configuração que contém o seguinte recurso do ficheiro:

```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```

Depois de aplicá-lo pela primeira vez, o ficheiro txt deve aparecer na `C:\test` pasta. No entanto, as execuções posteriores da configuração do mesmo não devem alterar o estado da máquina (por exemplo, não existem cópias do `test.txt` ficheiro deve ser criado).
Para garantir que um recurso é idempotente pode chamar repetidamente `Set-TargetResource` quando o recurso de teste diretamente ou chamar `Start-DscConfiguration` várias vezes fazendo quando o teste de ponto a ponto. O resultado deve ser o mesmo após cada execução.

## <a name="test-user-modification-scenario"></a>Cenário de modificação de utilizador de teste

Ao alterar o estado da máquina e, em seguida, volte a executar a DSC, pode verificar que `Set-TargetResource` e `Test-TargetResource` funcionar corretamente. Eis os passos que deve tomar:

1. Comece com o recurso não no estado pretendido.
2. Configuração de execução com o seu recurso
3. Certifique-se de `Test-DscConfiguration` retorna True
4. Modificar o item configurado para ser sair do estado pretendido
5. Certifique-se de `Test-DscConfiguration` retorna FALSO

Eis um exemplo mais concreto usando o recurso de Registro:

1. Começar com a chave de registo não no estado pretendido
2. Executar `Start-DscConfiguration` com uma configuração para colocá-la no estado pretendido e verifique se ele passa.
3. Executar `Test-DscConfiguration` e certifique-se de que ela retorna verdadeiro
4. Modifique o valor da chave, para que não esteja no estado pretendido
5. Executar `Test-DscConfiguration` e certifique-se de que ele retornará false
6. `Get-TargetResource` funcionalidade foi verificada através de `Get-DscConfiguration`

`Get-TargetResource` deverá devolver os detalhes do estado atual do recurso. Certifique-se de testá-lo chamando `Get-DscConfiguration` depois de aplicar a configuração e verificar que saída corretamente reflete o estado atual da máquina. É importante testá-lo em separado, uma vez que todos os problemas nessa área não será apresentado ao chamar `Start-DscConfiguration`.

## <a name="call-getsettest-targetresource-functions-directly"></a>Chamar **Get/Set/teste-TargetResource** diretamente de funções

Certifique-se de que teste o **Get/Set/teste-TargetResource** funções implementadas no seu recurso chamando-las diretamente e verificar que estão a funcionar conforme esperado.

## <a name="verify-end-to-end-using-start-dscconfiguration"></a>Certifique-se de que ponto a ponto com **início-dscconfiguration para**

Testes **Get/Set/teste-TargetResource** funções ao chamá-los diretamente é importante, mas nem todos os problemas serão detetados dessa maneira. Deve focar-se uma parte significativa de teste sobre como utilizar `Start-DscConfiguration` ou o servidor de solicitação. Na verdade, isso é como os usuários usarão o recurso, portanto, não subestime a importância desse tipo de testes.
Possíveis tipos de problemas:

- Credenciais/sessão pode ter um comportamento diferente porque o agente DSC é executado como um serviço.  Certifique-se de que quaisquer funcionalidades aqui de teste ponta a ponta.
- Erros de saída por `Start-DscConfiguration` podem ser diferentes dos apresentados ao chamar o `Set-TargetResource` função diretamente.

## <a name="test-compatability-on-all-dsc-supported-platforms"></a>Teste de compatibilidade no DSC todas as plataformas suportadas

Recurso deverá funcionar em todas as plataformas suportada do DSC (Windows Server 2008 R2 e versões mais recentes). Instale o WMF mais recente (Windows Management Framework) no seu SO para obter a versão mais recente do DSC. Se o recurso não funciona em algumas dessas plataformas por design, uma mensagem de erro específico deve ser devolvida. Além disso, certifique-se de que o seu recurso verifica se está a chamar de cmdlets estão presentes na máquina específica. Windows Server 2012 adicionados um grande número de novos cmdlets que não estão disponíveis no Windows Server 2008 R2, mesmo com WMF instalado.

## <a name="verify-on-windows-client-if-applicable"></a>Certifique-se no cliente do Windows (se aplicável)

Um intervalo de teste muito comum é a verificar o recurso apenas em versões de servidor do Windows. Muitos recursos também foram concebidos para funcionar em SKUs de cliente, portanto, se isso for verdade no seu caso, não se esqueça de testá-lo nessas plataformas também.

## <a name="get-dscresource-lists-the-resource"></a>O recurso apresenta uma lista de GET-DSCResource

Depois de implementar o módulo, chamar `Get-DscResource` deve listar assim o seu recurso, entre outros. Se não encontrar o recurso na lista, certifique-se esse arquivo schema.mof esse recurso de existência.

## <a name="resource-module-contains-examples"></a>Módulo de recursos contém exemplos

Criar exemplos de qualidade que irão ajudar os outros entenderem como usá-lo. Isso é crucial, especialmente, uma vez que muitos usuários tratam o código de exemplo como documentação.

- Em primeiro lugar, deve determinar os exemplos que serão incluídos com o módulo – no mínimo, deve abranger os casos de utilização mais importantes para o seu recurso:
- Se o seu módulo contém vários recursos que precisam para trabalharem em conjunto para um cenário ponto-a-ponto, o exemplo básico do ponto-a-ponto ideal seria ter primeiro.
- Os exemplos iniciais devem ser muito simples – como começar com os seus recursos em pequenas partes gerenciáveis (por exemplo, criar um novo VHD)
- Exemplos de subsequentes devem compilar nesses exemplos (por exemplo, criar uma VM a partir de um VHD, remover a VM, VM de modificação) e mostrar funcionalidades avançadas (por exemplo, criar uma VM com a memória dinâmica)
- As configurações de exemplo devem ser parametrizadas (todos os valores devem ser passados para a configuração como parâmetros e não deve haver nenhum valores embutidos em código):

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

- É uma boa prática para incluir (comentado horizontalmente) de exemplo de como chamar a configuração com os valores reais no final do script de exemplo.
  Por exemplo, na configuração acima não é necessariamente óbvio que é a melhor maneira de especificar UserAgent:

  `UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` Caso em que um comentário pode esclarecer a execução pretendida da configuração:

  ```powershell
  <#
  Sample use (parameter values need to be changed according to your scenario):

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
  -userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
  #>
  ```

- Para cada exemplo, escreva uma descrição breve que explica o que ele faz e o significado dos parâmetros.
- Certifique-se exemplos abrangem a maioria dos cenários importantes para o seu recurso e se não há nada em falta, certifique-se de que todos são executados e colocar a máquina do estado pretendido.

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a>Mensagens de erro são fáceis de compreender e ajudar os utilizadores a resolver problemas

Boas mensagens de erro devem ser:

- : O maior problema com mensagens de erro é que, muitas vezes, não existem, por isso, certifique-se de que eles estão lá.
- Fácil de compreender: códigos de erro de leitura e não obscuro humano
- Preciso: Descrever o que é exatamente o problema
- Construtivos: Conselhos como corrigir o problema
- Educado: Não o culparia usuário ou torná-los se aflija

Certifique-se de verificar a erros em cenários de ponto a ponto (usando `Start-DscConfiguration`), porque eles podem ser diferentes das devolvido ao executar as funções de recurso diretamente.

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a>Mensagens de registo são fáceis de compreender e informativos (incluindo – verboso, – depuração e os registos ETW)

Certifique-se de que registos produzidos pelo recurso são fáceis de compreender e fornecer valor ao utilizador. Recursos devem produzir todas as informações que poderão ser úteis para os utilizadores, mas os registos mais nem sempre é melhor. Deve evitar redundância e saída de dados que não agregam valor adicional ao – não faça alguém passar por centenas de entradas de registo para encontrar aquilo procura. É claro, não existem registos não é uma solução aceitável para este problema seja.

Ao testar, também deve analisar verboso e registos de depuração (executando `Start-DscConfiguration` com `–Verbose` e `–Debug` muda adequadamente), bem como os registos ETW. Para ver os registos DSC ETW, vá para o Visualizador de eventos e abra a seguinte pasta: aplicações e serviços da Microsoft - Windows - Desired State Configuration.  Por predefinição lá irá ser canal operacional, mas certifique-se de ativar a análise e depurar canais antes de executar a configuração.
Para ativar canais analíticos/depuração, pode executar o script abaixo:

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

## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a>Implementação de recursos não contém caminhos codificados

Certifique-se não há nenhum caminho codificado na implementação de recursos, especialmente se partem do princípio de idioma (en-us), ou quando existem variáveis de sistema que podem ser utilizadas.
Se precisar do recurso aceder aos caminhos específicos, utilize as variáveis de ambiente em vez de codificar o caminho, porque ele poderá ser diferente em outras máquinas.

Exemplo:

Em vez de:

```powershell
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
```

Pode escrever:

```powershell
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)}
```

## <a name="resource-implementation-does-not-contain-user-information"></a>Implementação de recursos não contém informações de utilizador

Certifique-se de que não são nomes de e-mail, as informações da conta ou nomes de pessoas no código.

## <a name="resource-was-tested-with-validinvalid-credentials"></a>Recurso foi testado com credenciais válidas/inválido

Se o seu recurso usa uma credencial como parâmetro:

- Verifique se o recurso funciona quando o sistema Local (ou a conta de computador para recursos remotos) não tem acesso.
- Certifique-se de que a funciona de recursos com uma credencial especificada para obter, definir e teste
- Se o recurso aceder a partilhas, teste todas as variantes que tem de suportar, tais como:
  - Partilhas de padrão do windows.
  - Partilhas DFS.
  - Partilhas do SAMBA (se quiser suporte Linux.)

## <a name="resource-does-not-require-interactive-input"></a>Recurso não necessita de entrada interativa

**Get/Set/teste-TargetResource** funções deve ser executadas automaticamente e não terá de aguardar para a entrada do utilizador em qualquer fase de execução (por exemplo, não deve usar `Get-Credential` dentro dessas funções). Se precisar de fornecer a entrada do usuário, deve passá-lo para a configuração como parâmetro durante a fase de compilação.

## <a name="resource-functionality-was-thoroughly-tested"></a>Funcionalidade de recursos foi totalmente testada

Esta lista de verificação contém itens que são importantes a serem testados e/ou muitas vezes seja perdidas. Haverá vários testes, principalmente aqueles funcionais que serão específicos para o recurso estiver a testar e não são mencionadas aqui. Não se esqueça de sobre casos de teste negativos.

## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a>Melhor prática: módulo de recursos contém a pasta de testes com ResourceDesignerTests.ps1 script

É uma boa prática para criar a pasta "testes" no módulo de recursos, crie `ResourceDesignerTests.ps1` de ficheiros e adicionar testes usando **teste xDscResource** e **teste xDscSchema** para todos os recursos em determinados módulo.
Dessa forma pode validar rapidamente esquemas de todos os recursos dos módulos de determinado e fazer uma sanidade verificar antes de publicar.
Para xRemoteFile, `ResourceTests.ps1` pode ter um aspeto tão simples como:

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="best-practice-resource-folder-contains-resource-designer-script-for-generating-schema"></a>Melhor prática: pasta de recurso contém o script do estruturador de recurso para gerar esquema

Cada recurso deve conter um script de designer de recursos que gera um esquema de mof do recurso. Este ficheiro deve ser colocado na `<ResourceName>\ResourceDesignerScripts` e ter o nome gerar `<ResourceName>Schema.ps1` para o recurso de xRemoteFile este ficheiro seria chamado `GenerateXRemoteFileSchema.ps1` e conter:

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

## <a name="best-practice-resource-supports--whatif"></a>Melhor prática: - WhatIf oferece suporte a recursos

Se o recurso está a efetuar operações de "perigosas", é uma boa prática para implementar `-WhatIf` funcionalidade. Depois de terminar, certifique-se de que `-WhatIf` saída corretamente descreve as operações que acontecem se o comando foi executado sem `-WhatIf` mudar.
Além disso, certifique-se de que as operações não é executado (não para o estado do nó são feitas alterações) quando `–WhatIf` comutador está presente.
Por exemplo, vamos supor que está a testar o recurso de ficheiros. Segue-se configuração simples que cria o ficheiro `test.txt` com conteúdo "teste":

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

Se vamos compilar e, em seguida, executar a configuração com o `-WhatIf` comutador, a saída é a indicar exatamente o que aconteceria quando executamos a configuração. A configuração do próprio no entanto não foi executada (`test.txt` ficheiro não foi criado).

```powershell
Start-DscConfiguration -Path .\config -ComputerName localhost -Wait -Verbose -WhatIf
```

```output
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

Esta lista não é exaustiva, mas abrange vários problemas importantes que podem ser encontrados durante a criação, desenvolvimento e teste de recursos de DSC.