---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Criar um pipeline de integração contínua e implementação contínua com o DSC
ms.openlocfilehash: 012057a32ccf85b0d15e76a332cadda4b226180a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076480"
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a>Criar um pipeline de integração contínua e implementação contínua com o DSC

Este exemplo demonstra como criar um pipeline de implementação contínua/integração contínua (CI/CD) com o PowerShell, DSC, Pester e Visual Studio Team Foundation Server (TFS).

Após o pipeline é criado e configurado, pode utilizá-lo totalmente implementar, configurar e testar um servidor DNS e registos de anfitrião de associados.
Este processo simula a primeira parte de um pipeline que vai ser utilizada num ambiente de desenvolvimento.

Um pipeline CI/CD automático ajuda-o a atualização de software mais rapidamente e de forma mais fiável, garantindo que todo o código é testado e de que uma compilação atual do seu código está disponível, o tempo todo.

## <a name="prerequisites"></a>Pré-requisitos

Para utilizar este exemplo, deve estar familiarizado com o seguinte:

- Conceitos do CD de CI. Uma boa referência pode ser encontrada em [o modelo de Pipeline de lançamento](http://aka.ms/thereleasepipelinemodelpdf).
- [Git](https://git-scm.com/) controlo de origem
- O [Pester](https://github.com/pester/Pester) estrutura de testes
- [Team Foundation Server](https://www.visualstudio.com/tfs/)

## <a name="what-you-will-need"></a>O que irá precisar

Para criar e executar este exemplo, terá um ambiente com vários computadores e/ou máquinas virtuais.

### <a name="client"></a>Cliente

Este é o computador onde irá realizar todo o trabalho de configurar e executar o exemplo.

O computador cliente tem de ser um computador Windows com o seguinte instalado:

- [Git](https://git-scm.com/)
- clonar a partir de um repositório de local git https://github.com/PowerShell/Demo_CI
- editor de texto, como [Visual Studio Code](https://code.visualstudio.com/)

### <a name="tfssrv1"></a>TFSSrv1

O computador que aloja o servidor do TFS nos quais definirá sua compilação e versão.
Este computador tem de ter [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) instalado.

### <a name="buildagent"></a>BuildAgent

O computador que executa o Windows o agente que cria o projeto de compilação.
Este computador tem de ter um agente instalado e em execução de compilação de Windows.
Ver [implementar um agente no Windows](/azure/devops/pipelines/agents/v2-windows) para obter instruções sobre como instalar e executar um Windows de agente de compilação.

Também tem de instalar ambas as `xDnsServer` e `xNetworking` módulos de DSC neste computador.

### <a name="testagent1"></a>TestAgent1

Este é o computador que está configurado como um servidor DNS na configuração de DSC neste exemplo.
O computador tem de estar em execução [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).

### <a name="testagent2"></a>TestAgent2

Este é o computador que aloja o site, que este exemplo configura.
O computador tem de estar em execução [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).

## <a name="add-the-code-to-tfs"></a>Adicione o código para o TFS

Irá começamos pela criação de um repositório de Git no TFS e importar o código do seu repositório local no computador cliente.
Se já não clonar o repositório de Demo_CI até o computador cliente, portanto, agora fazer ao executar o seguinte comando do git:

`git clone https://github.com/PowerShell/Demo_CI`

1. No computador cliente, navegue para o servidor do TFS num navegador da web.
1. No TFS, [criar um novo projeto de equipe](/azure/devops/organizations/projects/create-project) Demo_CI com o nome.

   Certifique-se de que **controle de versão** está definida como **Git**.
1. No computador cliente, adicione um remoto para o repositório que acabou de criar no TFS com o seguinte comando:

   `git remote add tfs <YourTFSRepoURL>`

   Onde `<YourTFSRepoURL>` é o URL do clone para o repositório do TFS que criou no passo anterior.

   Se não sabe onde encontrar este URL, veja [clonar um repositório de Git existente](/azure/devops/repos/git/clone).
1. Envie o código do seu repositório local para o seu repositório TFS com o seguinte comando:

   `git push tfs --all`
1. O repositório do TFS será preenchido com o código de Demo_CI.

> [!NOTE]
> Este exemplo utiliza o código no `ci-cd-example` ramo do repositório Git.
> Certifique-se de que especificar este ramo como o ramo predefinido no seu projeto do TFS e para criar os acionadores de CI/CD.

## <a name="understanding-the-code"></a>Compreender o código

Antes de criarmos os pipelines de compilação e implementação, vamos examinar alguns códigos para compreender o que está acontecendo.
No computador cliente, abra o seu editor de texto favorito e navegue para a raiz do repositório Demo_CI Git.

### <a name="the-dsc-configuration"></a>A configuração de DSC

Abra o ficheiro `DNSServer.ps1` (partir da raiz do repositório local Demo_CI, `./InfraDNS/Configs/DNSServer.ps1`).

Este ficheiro contém a configuração de DSC que configura o servidor DNS. Este é integralmente:

```powershell
configuration DNSServer
{
    Import-DscResource -module 'xDnsServer','xNetworking', 'PSDesiredStateConfiguration'

    Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
    {
        WindowsFeature DNS
        {
            Ensure  = 'Present'
            Name    = 'DNS'
        }

        xDnsServerPrimaryZone $Node.zone
        {
            Ensure    = 'Present'
            Name      = $Node.Zone
            DependsOn = '[WindowsFeature]DNS'
        }

        foreach ($ARec in $Node.ARecords.keys) {
            xDnsRecord $ARec
            {
                Ensure    = 'Present'
                Name      = $ARec
                Zone      = $Node.Zone
                Type      = 'ARecord'
                Target    = $Node.ARecords[$ARec]
                DependsOn = '[WindowsFeature]DNS'
            }
        }

        foreach ($CName in $Node.CNameRecords.keys) {
            xDnsRecord $CName
            {
                Ensure    = 'Present'
                Name      = $CName
                Zone      = $Node.Zone
                Type      = 'CName'
                Target    = $Node.CNameRecords[$CName]
                DependsOn = '[WindowsFeature]DNS'
            }
        }
    }
}
```

Tenha em atenção o `Node` instrução:

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

Isso encontra quaisquer nós que foram definidos como tendo uma função de `DNSServer` no [dados de configuração](../configurations/configData.md), que é criado pelo `DevEnv.ps1` script.

Pode ler mais sobre o `Where` método na [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)

Usando dados de configuração para definir nós é importante fazer CI porque as informações do nó vão provavelmente mudar entre ambientes e usar dados de configuração permite que facilmente fazer alterações às informações do nó, sem alterar o código de configuração.

No primeiro bloco de recursos, a configuração chama o **WindowsFeature** para se certificar de que a funcionalidade DNS está ativada.
Os blocos de recursos que se seguem os recursos de chamada a partir da [xDnsServer](https://github.com/PowerShell/xDnsServer) módulo para configurar a zona primária e registos DNS.

Tenha em atenção que os dois `xDnsRecord` blocos são encapsulados em `foreach` loops iterar por meio de matrizes nos dados de configuração.
Novamente, os dados de configuração são criados pelo `DevEnv.ps1` script, que veremos seguinte.

### <a name="configuration-data"></a>Dados de configuração

O `DevEnv.ps1` ficheiro (partir da raiz do repositório local Demo_CI, `./InfraDNS/DevEnv.ps1`) Especifica os dados de configuração específicos do ambiente numa tabela de hash e, em seguida, passa essa tabela de hash a uma chamada para o `New-DscConfigurationDataDocument` função, o que é definida no `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).

O `DevEnv.ps1` ficheiro:

```powershell
param(
    [parameter(Mandatory=$true)]
    [string]
    $OutputPath
)

Import-Module $PSScriptRoot\..\Assets\DscPipelineTools\DscPipelineTools.psd1 -Force

# Define Unit Test Environment
$DevEnvironment = @{
    Name                        = 'DevEnv';
    Roles = @(
        @{  Role                = 'DNSServer';
            VMName              = 'TestAgent1';
            Zone                = 'Contoso.com';
            ARecords            = @{'TFSSrv1'= '10.0.0.10';'Client'='10.0.0.15';'BuildAgent'='10.0.0.30';'TestAgent1'='10.0.0.40';'TestAgent2'='10.0.0.50'};
            CNameRecords        = @{'DNS' = 'TestAgent1.contoso.com'};
        }
    )
}

Return New-DscConfigurationDataDocument -RawEnvData $DevEnvironment -OutputPath $OutputPath
```

O `New-DscConfigurationDataDocument` função (definidos na `\Assets\DscPipelineTools\DscPipelineTools.psm1`) por meio de programação cria um documento de dados de configuração a partir da tabela hash (dados do nó) e a matriz (não-nó de dados) que são transmitidas como o `RawEnvData` e `OtherEnvData` parâmetros.

No nosso caso, apenas o `RawEnvData` parâmetro é utilizado.

### <a name="the-psake-build-script"></a>O script de compilação psake

O [psake](https://github.com/psake/psake) criar script definido no `Build.ps1` (da raiz do repositório Demo_CI, `./InfraDNS/Build.ps1`) define as tarefas que fazem parte da compilação.
Define as tarefas que cada tarefa depende.
Quando invocado, o script de psake garante que a tarefa especificada (ou a tarefa com o nome `Default` se não for especificado nenhum) é executado e que também execute todas as dependências (isto é recursiva, para que as dependências das dependências executam, e assim por diante).

Neste exemplo, o `Default` tarefa é definida como:

```powershell
Task Default -depends UnitTests
```

O `Default` tarefa não tem nenhuma implementação propriamente dita, mas tem uma dependência no `CompileConfigs` tarefas.
A cadeia resultante de dependências de tarefas garante que todas as tarefas no script de compilação são executadas.

Neste exemplo, o script de psake é invocado por uma chamada para `Invoke-PSake` no `Initiate.ps1` ficheiro (localizado na raiz do repositório Demo_CI):

```powershell
param(
    [parameter()]
    [ValidateSet('Build','Deploy')]
    [string]
    $fileName
)

#$Error.Clear()

Invoke-PSake $PSScriptRoot\InfraDNS\$fileName.ps1

<#if($Error.count)
{
    Throw "$fileName script failed. Check logs for failure details."
}
#>
```

Quando criamos a definição de compilação para o nosso exemplo no TFS, irá fornecer o nosso arquivo de script psake como o `fileName` parâmetro para este script.

O script de compilação define as seguintes tarefas:

#### <a name="generateenvironmentfiles"></a>GenerateEnvironmentFiles

Execuções `DevEnv.ps1`, que gera o arquivo de dados de configuração.

#### <a name="installmodules"></a>InstallModules

Instala os módulos necessários pela configuração `DNSServer.ps1`.

#### <a name="scriptanalysis"></a>ScriptAnalysis

Chamadas a [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).

#### <a name="unittests"></a>UnitTests

Executa o [Pester](https://github.com/pester/Pester/wiki) testes de unidade.

#### <a name="compileconfigs"></a>CompileConfigs

Compila a configuração (`DNSServer.ps1`) para um ficheiro MOF, com os dados de configuração gerados pelo `GenerateEnvironmentFiles` tarefas.

#### <a name="clean"></a>Limpar

Cria as pastas utilizadas para o exemplo e remove quaisquer resultados do teste, arquivos de dados de configuração e módulos de execuções anteriores.

### <a name="the-psake-deploy-script"></a>O psake implementar script

O [psake](https://github.com/psake/psake) script de implementação definida na `Deploy.ps1` (da raiz do repositório Demo_CI, `./InfraDNS/Deploy.ps1`) define as tarefas que implemente e execute a configuração.

`Deploy.ps1` Define as seguintes tarefas:

#### <a name="deploymodules"></a>DeployModules

Inicia uma sessão do PowerShell no `TestAgent1` e instala os módulos que contém os recursos de DSC necessários para a configuração.

#### <a name="deployconfigs"></a>DeployConfigs

Chamadas a [Start-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet para executar a configuração no `TestAgent1`.

#### <a name="integrationtests"></a>IntegrationTests

Executa o [Pester](https://github.com/pester/Pester/wiki) testes de integração.

#### <a name="acceptancetests"></a>AcceptanceTests

Executa o [Pester](https://github.com/pester/Pester/wiki) testes de aceitação.

#### <a name="clean"></a>Limpar

Remove quaisquer módulos instalados no execuções anteriores e garante que a pasta de resultado de teste existe.

### <a name="test-scripts"></a>Scripts de teste

Testes de unidade, integração e aceitação são definidos nos scripts na `Tests` pasta (da raiz do repositório Demo_CI, `./InfraDNS/Tests`), cada nos arquivos chamados `DNSServer.tests.ps1` em suas respectivas pastas.

O teste de uso de scripts [Pester](https://github.com/pester/Pester/wiki) e [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) sintaxe.

#### <a name="unit-tests"></a>Testes de unidade

Os testes de unidade configurações de teste a DSC para garantir que as configurações fará o que é esperado quando executados.
O teste de unidade script usa [Pester](https://github.com/pester/Pester/wiki).

#### <a name="integration-tests"></a>Testes de integração

Os testes de integração de teste a configuração do sistema para garantir que, quando integrada com outros componentes, o sistema está configurado conforme esperado. Esses testes são executados no nó de destino após ter sido configurada com DSC.
O script de teste de integração utiliza uma mistura de [Pester](https://github.com/pester/Pester/wiki) e [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) sintaxe.

#### <a name="acceptance-tests"></a>Testes de aceitação

Testes de aceitação testar o sistema para garantir que funciona conforme o esperado.
Por exemplo, testes para garantir que uma página da web devolve as informações corretas quando consultado.
Esses testes executados remotamente partir do nó de destino para testar cenários do mundo real.
O script de teste de integração utiliza uma mistura de [Pester](https://github.com/pester/Pester/wiki) e [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) sintaxe.

## <a name="define-the-build"></a>Definir a compilação

Agora que já carregou o nosso código para o TFS e viu o que ele faz, vamos definir nossa compilação.

Aqui, vamos abordar apenas os passos de compilação que adicionará à compilação. Para obter instruções sobre como criar uma definição de compilação no TFS, consulte [criar e uma definição de compilação de fila](/azure/devops/pipelines/get-started-designer).

Criar uma nova definição de compilação (selecione o **vazio** modelo) com o nome "InfraDNS".
Adicione que os seguintes passos para a definição de compilação:

- Script do PowerShell
- Publicar os resultados do teste
- Copiar ficheiros
- Publicar artefactos

Depois de adicionar estes passos de criar, editar as propriedades de cada passo da seguinte forma:

### <a name="powershell-script"></a>Script do PowerShell

1. Definir o **tipo** propriedade `File Path`.
1. Definir o **caminho do Script** propriedade `initiate.ps1`.
1. Adicione `-fileName build` para o **argumentos** propriedade.

Este passo de compilação é executado o `initiate.ps1` arquivo, que chama o script de compilação psake.

### <a name="publish-test-results"></a>Publicar os resultados do teste

1. Definir **formato de resultado de teste** para `NUnit`
1. Definir **arquivos de resultados do teste** para `InfraDNS/Tests/Results/*.xml`
1. Definir **Title de execução de teste** para `Unit`.
1. Certifique-se **opções de controlo** **ativado** e **sempre executar** são ambos os selecionado.

Este passo de compilação executa os testes de unidade no script Pester vimos anteriormente e armazena os resultados no `InfraDNS/Tests/Results/*.xml` pasta.

### <a name="copy-files"></a>Copiar ficheiros

1. Adicionar cada uma das seguintes linhas ao **conteúdo**:

   ```
   initiate.ps1
   **\deploy.ps1
   **\Acceptance\**
   **\Integration\**
   ```

1. Definir **TargetFolder** para `$(Build.ArtifactStagingDirectory)\`

Este passo copia a compilação e teste os scripts para o diretório de transição até o pode ser publicado como artefactos de compilação, o passo seguinte.

### <a name="publish-artifact"></a>Publicar artefactos

1. Definir **caminho para publicar** para `$(Build.ArtifactStagingDirectory)\`
1. Definir **nome do artefacto** para `Deploy`
1. Definir **tipo de Artefato** para `Server`
1. Selecione `Enabled` em **controlar opções**

## <a name="enable-continuous-integration"></a>Ativar a integração contínua

Agora, iremos configurar um acionador que faz com que o projeto criar sempre que uma alteração é check-in a `ci-cd-example` ramo do repositório git.

1. No TFS, clique nas **compilação e versão** separador
1. Selecione o `DNS Infra` definição de compilação e clique em **editar**
1. Clique nas **Acionadores** separador
1. Selecione **integração contínua (CI)** e selecione `refs/heads/ci-cd-example` na lista pendente ramificação
1. Clique em **salvar** e, em seguida, **OK**

Agora qualquer alteração nos acionadores de repositório de git do TFS uma compilação automatizada.

## <a name="create-the-release-definition"></a>Criar a definição de versão

Vamos criar uma definição de versão, para que o projeto é implementado no ambiente de desenvolvimento com cada check-in de código.

Para fazer isso, adicione uma nova definição de versão associada a `InfraDNS` Criar definição que criou anteriormente.
Verifique se seleciona **implementação contínua** para que uma nova versão será acionada sempre que uma nova compilação é concluída.
([Quais são os pipelines de versão? ](/azure/devops/pipelines/release/what-is-release-management)) e configurá-lo da seguinte forma:

Adicione os seguintes passos para a definição de versão:

- Script do PowerShell
- Publicar os resultados do teste
- Publicar os resultados do teste

Edite os passos da seguinte forma:

### <a name="powershell-script"></a>Script do PowerShell

1. Definir o **caminho do Script** campo para `$(Build.DefinitionName)\Deploy\initiate.ps1"`
1. Definir o **argumentos** campo para `-fileName Deploy`

### <a name="first-publish-test-results"></a>Em primeiro lugar, publicar os resultados do teste

1. Selecione `NUnit` para o **formato de resultado de teste** campo
1. Definir o **ficheiros do resultado de teste** campo para `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`
1. Definir o **Title de execução de teste** para `Integration`
1. Sob **opções de controlo**, verifique **sempre executar**

### <a name="second-publish-test-results"></a>Em segundo lugar, publicar os resultados do teste

1. Selecione `NUnit` para o **formato de resultado de teste** campo
1. Definir o **ficheiros do resultado de teste** campo para `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`
1. Definir o **Title de execução de teste** para `Acceptance`
1. Sob **opções de controlo**, verifique **sempre executar**

## <a name="verify-your-results"></a>Verificar os resultados

Agora, sempre que emitir alterações `ci-cd-example` ramo para o TFS, uma nova compilação será iniciado.
Se a compilação for concluída com êxito, uma nova implementação é acionada.

Pode verificar o resultado da implementação ao abrir um browser no computador cliente e navegar para `www.contoso.com`.

## <a name="next-steps"></a>Próximos passos

Este exemplo configura o servidor DNS `TestAgent1` , para que o URL `www.contoso.com` é resolvida para `TestAgent2`, mas não implementa, na verdade, um Web site.
O esqueleto para fazer isso é fornecido no repositório sob o `WebApp` pasta.
Pode usar os stubs fornecidos para criar configurações de DSC, Pester testes e psake scripts para implementar o seu próprio Web site.
