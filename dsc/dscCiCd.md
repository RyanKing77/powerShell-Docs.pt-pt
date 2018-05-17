---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Criar um pipeline de integração contínua e a implementação contínua com DSC
ms.openlocfilehash: ce0f2ed79f5f96a1c38e0beaf32529aba7538963
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a>Criar um pipeline de integração contínua e a implementação contínua com DSC

Este exemplo demonstra como criar um pipeline de implementação contínua/integração contínua (CI/CD) utilizando o PowerShell, DSC, Pester e Visual Studio Team Foundation Server (TFS).

Depois do pipeline é criado e configurado, pode utilizá-la completamente implementar, configurar e testar um servidor DNS e associados registos de anfitrião.
Este processo simula a primeira parte de um pipeline que seria utilizada num ambiente de desenvolvimento.

Um pipeline de CI/CD automatizado ajuda-o a atualização de software mais rápido e mais fiável, garantir que todo o código é testado e de que é uma compilação atual do seu código disponível em todas as vezes.

## <a name="prerequisites"></a>Pré-requisitos

Para utilizar este exemplo, deve estar familiarizado com o seguinte:

- Conceitos do CD de CI. É possível localizar uma referência de boa [o modelo de Pipeline de versão](http://aka.ms/thereleasepipelinemodelpdf).
- [Git](https://git-scm.com/) controlo de origem
- O [Pester](https://github.com/pester/Pester) testar framework
- [Do Team Foundation Server](https://www.visualstudio.com/tfs/)

## <a name="what-you-will-need"></a>O que precisa

Para compilar e executar este exemplo, terá um ambiente com vários computadores e/ou máquinas virtuais.

### <a name="client"></a>Cliente

Este é o computador onde irá fazer todo o trabalho configurar e executar o exemplo.

O computador cliente tem de ser um computador Windows com o seguinte instalado:
- [Git](https://git-scm.com/)
- um repositório de local git clonado a partir do https://github.com/PowerShell/Demo_CI
- editor de texto, tal como [Visual Studio Code](https://code.visualstudio.com/)

### <a name="tfssrv1"></a>TFSSrv1

O computador que aloja o servidor TFS onde vai definir a compilação e versão.
Este computador tem de ter [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) instalado.

### <a name="buildagent"></a>BuildAgent

O computador que executa o Windows criar agente que cria o projeto.
Este computador tem de ter um Windows criar o agente instalado e em execução.
Consulte [implementar um agente no Windows](https://www.visualstudio.com/en-us/docs/build/actions/agents/v2-windows) para obter instruções sobre como instalar e executar o Windows criar agente.

Também tem de instalar ambas as `xDnsServer` e `xNetworking` módulos de DSC neste computador.

### <a name="testagent1"></a>TestAgent1

Este é o computador que está configurado como um servidor DNS na configuração de DSC neste exemplo.
O computador tem de estar em execução [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).

### <a name="testagent2"></a>TestAgent2

Este é o computador que aloja o site que este exemplo configura.
O computador tem de estar em execução [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).

## <a name="add-the-code-to-tfs"></a>Adicione o código para o TFS

Iremos começar ao criar um repositório de Git no TFS e importar o código do seu repositório local no computador cliente.
Se já não clonar o repositório de Demo_CI para o seu computador cliente, fazê-lo agora, por isso, executando o seguinte comando do git:

`git clone https://github.com/PowerShell/Demo_CI`

1. No computador cliente, navegue para o servidor TFS num web browser.
1. No TFS, [criar um novo projeto de equipa](https://www.visualstudio.com/en-us/docs/setup-admin/create-team-project) denominado Demo_CI.

    Certifique-se de que **controlo de versão** está definido como **Git**.
1. No computador cliente, adicione um remoto para o repositório que acabou de criar no TFS com o seguinte comando:

    `git remote add tfs <YourTFSRepoURL>`

    Onde `<YourTFSRepoURL>` é o URL do clone para o repositório do TFS que criou no passo anterior.

    Se não souber onde encontrar este URL, consulte [clonar um repositório de Git existente](https://www.visualstudio.com/en-us/docs/git/tutorial/clone).
1. Emitir o código do seu repositório local para o seu repositório TFS com o seguinte comando:

    `git push tfs --all`
1. O repositório TFS será preenchido com o código de Demo_CI.

>**Nota:** este exemplo utiliza o código de `ci-cd-example` ramo do repositório de Git.
>Lembre-se de que especifique este ramo como o ramo predefinido no seu projeto do TFS e para os acionadores de CI/CD que cria.

## <a name="understanding-the-code"></a>Noções sobre o código

Antes de iremos criar pipelines de compilação e implementação, vamos ver alguns do código para compreender o que está a suceder.
No computador cliente, abra o editor de texto favorito e navegue para a raiz do repositório de Demo_CI Git.

### <a name="the-dsc-configuration"></a>A configuração DSC

Abra o ficheiro `DNSServer.ps1` (de raiz do repositório Demo_CI local, `./InfraDNS/Configs/DNSServer.ps1`).

Este ficheiro contém a configuração de DSC que configura o servidor DNS. Segue-se na íntegra:

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

Isto localiza quaisquer nós que foram definidos como tendo uma função de `DNSServer` no [dados de configuração](configData.md), que é criado pelo `DevEnv.ps1` script.

É importante utilizar dados de configuração para definir nós ao efetuar CI porque as informações do nó, provavelmente, serão alterado entre ambientes e utilização de dados de configuração permite-lhe facilmente efetuar alterações às informações do nó, sem alterar o código de configuração.

No primeiro bloco de recursos, a configuração chama o [WindowsFeature](windowsFeatureResource.md) para se certificar de que a funcionalidade DNS está ativada.
Os blocos de recursos que se seguem recursos chamada a partir de [xDnsServer](https://github.com/PowerShell/xDnsServer) módulo para configurar a zona primária e registos DNS.

Tenha em atenção que as duas `xDnsRecord` blocos são moldados numa `foreach` ciclos iterar através de matrizes de dados de configuração.
Novamente, os dados de configuração são criados pelo `DevEnv.ps1` script, que vamos ver seguinte.

### <a name="configuration-data"></a>Dados de configuração

O `DevEnv.ps1` ficheiro (de raiz do repositório Demo_CI local, `./InfraDNS/DevEnv.ps1`) Especifica os dados de configuração específicas do ambiente de uma tabela hash e, em seguida, transmite essa tabela hash para uma chamada para o `New-DscConfigurationDataDocument` função, o que está definida na `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).

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

O `New-DscConfigurationDataDocument` função (definido no `\Assets\DscPipelineTools\DscPipelineTools.psm1`) através de programação cria um documento de dados de configuração a partir da tabela hash (dados do nó) e a matriz (dados do nó não) que são transmitidos como o `RawEnvData` e `OtherEnvData` parâmetros.

No nosso caso, apenas o `RawEnvData` parâmetro é utilizado.

### <a name="the-psake-build-script"></a>O script de compilação psake

O [psake](https://github.com/psake/psake) compilar o script definido no `Build.ps1` (de raiz do repositório Demo_CI, `./InfraDNS/Build.ps1`) define as tarefas que façam parte de compilação.
Também define as tarefas que cada tarefa depende.
Quando foi invocado, o script de psake garante que a tarefa especificada (ou a tarefa com o nome `Default` se não for especificado nenhum) é executado e que também executam todas as dependências (isto é recursiva, para que as dependências de dependências de executam, e assim sucessivamente).

Neste exemplo, o `Default` tarefas está definida como:

```powershell
Task Default -depends UnitTests
```

O `Default` tarefa não tem qualquer implementação próprio, mas tem uma dependência `CompileConfigs` tarefas.
A cadeia de dependências de tarefas resultante assegura que todas as tarefas no script de compilação são executadas.

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

Quando criamos a definição de compilação para o nosso exemplo no TFS, iremos irá fornecer o nosso ficheiro de script psake como o `fileName` parâmetro para este script.

O script de compilação define as seguintes tarefas:

#### <a name="generateenvironmentfiles"></a>GenerateEnvironmentFiles

Executa `DevEnv.ps1`, que gera o ficheiro de dados de configuração.

#### <a name="installmodules"></a>InstallModules

Instala os módulos necessários na configuração da `DNSServer.ps1`.

#### <a name="scriptanalysis"></a>ScriptAnalysis

As chamadas a [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).

#### <a name="unittests"></a>UnitTests

Executa o [Pester](https://github.com/pester/Pester/wiki) testes de unidade.

#### <a name="compileconfigs"></a>CompileConfigs

Compila a configuração (`DNSServer.ps1`) para um ficheiro MOF, utilizando os dados de configuração gerados pelo `GenerateEnvironmentFiles` tarefas.

#### <a name="clean"></a>Limpar

Cria as pastas utilizadas para o exemplo e remove quaisquer resultados de teste, ficheiros de dados de configuração e módulos da execução anterior.

### <a name="the-psake-deploy-script"></a>O psake implementar script

O [psake](https://github.com/psake/psake) script de implementação foi definido no `Deploy.ps1` (de raiz do repositório Demo_CI, `./InfraDNS/Deploy.ps1`) define as tarefas que implemente e execute a configuração.

`Deploy.ps1` Define as seguintes tarefas:

#### <a name="deploymodules"></a>DeployModules

Inicia uma sessão do PowerShell no `TestAgent1` e instala os módulos que contém os recursos de DSC necessários para a configuração.

#### <a name="deployconfigs"></a>DeployConfigs

As chamadas a [início DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration.md) cmdlet para executar a configuração `TestAgent1`.

#### <a name="integrationtests"></a>IntegrationTests

Executa o [Pester](https://github.com/pester/Pester/wiki) testes de integração.

#### <a name="acceptancetests"></a>AcceptanceTests

Executa o [Pester](https://github.com/pester/Pester/wiki) testes de aceitação.

#### <a name="clean"></a>Limpar

Remove quaisquer módulos instalados no executa anterior e assegura que a pasta de resultado do teste existe.

### <a name="test-scripts"></a>Testar scripts

Testes de aceitação, integração e a unidade são definidos em scripts no `Tests` pasta (de raiz do repositório Demo_CI, `./InfraDNS/Tests`), cada em ficheiros com o nome `DNSServer.tests.ps1` no seus respetivas pastas.

O teste de scripts utilize [Pester](https://github.com/pester/Pester/wiki) e [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) sintaxe.

#### <a name="unit-tests"></a>Testes de unidade

A unidade testes configurações de teste do DSC si próprios para se certificar de que irão fazer as configurações que é esperado quando são executadas.
A unidade testar o script utiliza [Pester](https://github.com/pester/Pester/wiki).

#### <a name="integration-tests"></a>Testes de integração

Os testes de integração testar a configuração do sistema para se certificar de que, quando integrado com outros componentes, o sistema está configurado como esperado. Estes testes executam no nó de destino depois pois foi configurado com DSC.
O script de teste de integração utiliza uma combinação de [Pester](https://github.com/pester/Pester/wiki) e [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) sintaxe.

#### <a name="acceptance-tests"></a>Testes de aceitação

Testes de aceitação testar o sistema para se certificar de que esta se comporta conforme esperado.
Por exemplo, testes para garantir que uma página web devolve as informações corretas quando consultado.
Estes testes executam remotamente a partir do nó de destino para testar cenários no mundo real.
O script de teste de integração utiliza uma combinação de [Pester](https://github.com/pester/Pester/wiki) e [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) sintaxe.

## <a name="define-the-build"></a>Definir a compilação

Agora que tiver carregado o nosso código para o TFS e consultou o que faz, definamos o nosso compilação.

Aqui, iremos abranger apenas os passos de compilação que irá adicionar a compilação. Para obter instruções sobre como criar uma definição de compilação no TFS, consulte [criar e uma definição de compilação de fila](https://www.visualstudio.com/en-us/docs/build/define/create).

Criar uma nova definição de compilação (selecionar o **vazio** modelo) com o nome "InfraDNS".
Adicione que os seguintes passos para a definição de compilação:

- Script do PowerShell
- Publicar os resultados do teste
- Copiar ficheiros
- Publicar artefactos

Depois de adicionar estas criar passos, edite as propriedades de cada passo da seguinte forma:

### <a name="powershell-script"></a>Script do PowerShell

1. Definir o **tipo** propriedade `File Path`.
1. Definir o **caminho do Script** propriedade `initiate.ps1`.
1. Adicionar `-fileName build` para o **argumentos** propriedade.

Este passo de compilação é executado o `initiate.ps1` ficheiro, que chama o script de compilação psake.

### <a name="publish-test-results"></a>Publicar os resultados do teste

1. Definir **testar o formato de resultado** para `NUnit`
1. Definir **resultados do teste de ficheiros** para `InfraDNS/Tests/Results/*.xml`
1. Definir **testar título execução** para `Unit`.
1. Certifique-se **opções de controlo** **ativado** e **são sempre executadas** tem ambos os selecionado.

Este passo de compilação executa os testes de unidade no script Pester iremos consultou anteriormente e armazena os resultados no `InfraDNS/Tests/Results/*.xml` pasta.

### <a name="copy-files"></a>Copiar ficheiros

1. Adicionar cada um dos seguintes linhas ao **conteúdo**:

    ```
    initiate.ps1
    **\deploy.ps1
    **\Acceptance\**
    **\Integration\**
    ```

1. Definir **TargetFolder** para `$(Build.ArtifactStagingDirectory)\`

Este passo copia a compilação e teste de scripts para o diretório de testes para que o possa ser publicada como criar artefactos pelo passo seguinte.

### <a name="publish-artifact"></a>Publicar artefactos

1. Definir **caminho publicar** para `$(Build.ArtifactStagingDirectory)\`
1. Definir **artefactos nome** para `Deploy`
1. Definir **artefactos tipo** para `Server`
1. Selecione `Enabled` no **controlo opções**

## <a name="enable-continuous-integration"></a>Ativar a integração contínua

Agora iremos definir um acionador que faz com que o projeto para qualquer tempo de compilação uma alteração é verificada para o `ci-cd-example` ramo do repositório de git.

1. No TFS, clique em de **compilar & versão** separador
1. Selecione o `DNS Infra` Criar definição e clique em **editar**
1. Clique em de **Acionadores** separador
1. Selecione **integração contínua (CI)** e selecione `refs/heads/ci-cd-example` na lista pendente sucursal
1. Clique em **guardar** e, em seguida, **OK**

Agora qualquer alteração nos acionadores de repositório de git do TFS uma compilação automatizada.

## <a name="create-the-release-definition"></a>Criar a definição da versão

Vamos criar uma definição de versão, para que o projeto é implementado no ambiente de desenvolvimento com cada dar entrada no código.

Para tal, adicione uma nova definição de versão associada a `InfraDNS` Criar definição que criou anteriormente.
Lembre-se de que selecione **a implementação contínua** para que uma nova versão será acionada sempre que uma nova compilação for concluída.
([Como: trabalhar com definições de versão](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions)) e configurá-lo da seguinte forma:

Adicione os seguintes passos para a definição da versão:

- Script do PowerShell
- Publicar os resultados do teste
- Publicar os resultados do teste

Edite os passos da seguinte forma:

### <a name="powershell-script"></a>Script do PowerShell

1. Definir o **caminho do Script** campo para `$(Build.DefinitionName)\Deploy\initiate.ps1"`
1. Definir o **argumentos** campo para `-fileName Deploy`

### <a name="first-publish-test-results"></a>Publicar primeiro os resultados do teste

1. Selecione `NUnit` para o **formato de resultado do teste** campo
1. Definir o **ficheiros de resultado do teste** campo para `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`
1. Definir o **testar título execução** para `Integration`
1. Em **opções de controlo**, verifique **são sempre executadas**

### <a name="second-publish-test-results"></a>Segundo publicar os resultados do teste

1. Selecione `NUnit` para o **formato de resultado do teste** campo
1. Definir o **ficheiros de resultado do teste** campo para `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`
1. Definir o **testar título execução** para `Acceptance`
1. Em **opções de controlo**, verifique **são sempre executadas**

## <a name="verify-your-results"></a>Verificar os resultados

Agora, sempre que enviar a alterações `ci-cd-example` ramo para o TFS, uma nova compilação será iniciado.
Se a compilação for concluída com êxito, é acionada uma nova implementação.

Pode verificar o resultado da implementação ao abrir um browser no computador cliente e navegar até `www.contoso.com`.

## <a name="next-steps"></a>Próximos passos

Este exemplo configura o servidor DNS `TestAgent1` para que o URL `www.contoso.com` é resolvido para `TestAgent2`, mas não implementa efetivamente um Web site.
A estrutura para fazê-lo é fornecida no repositório sob o `WebApp` pasta.
Pode utilizar os stubs fornecidos para criar psake scripts, Pester testes e configurações de DSC para implementar a sua própria Web site.