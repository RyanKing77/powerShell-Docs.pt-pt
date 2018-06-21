---
ms.date: 10/13/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Descrição Geral do Desired State Configuration para Engenheiros
ms.openlocfilehash: 30ce8bbb8bd3ea69dbf8ca509ecf523eb8fd915f
ms.sourcegitcommit: bad40d59598ae5597051fa381986316a2d9bf6c8
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/20/2018
ms.locfileid: "36271080"
---
# <a name="desired-state-configuration-overview-for-engineers"></a>Descrição Geral do Desired State Configuration para Engenheiros

Este documento destina-se a equipas de programador as operações de e compreender as vantagens do PowerShell pretendido Estado Configuration (DSC).
Para obter uma vista de nível superior do valor DSC fornece, consulte [Desired Configuration descrição geral do Estado para os decisores](decisionMaker.md)

## <a name="benefits-of-desired-state-configuration"></a>Vantagens da configuração do estado pretendido

Não existe DSC para:

- Reduzir a complexidade do processamento de scripts do Windows
- Aumentar a velocidade da iteração

O conceito de "implementação contínua" se está a tornar mais importante.
A implementação contínua significa que a capacidade de implementar com frequência, potencialmente, muitas vezes por dia.
O objetivo estas implementações são não para corrigir algo mas obter algo publicados rapidamente.
Por obter novas funcionalidades através de programação numa operação como facilmente e fiável quanto possível, reduzir o tempo ao valor de lógica de negócio novas.

A mudança para implica uma solução de implementação que utiliza um modelo de modelo "declarativa", em que um ambiente de estado de fim é declarado como texto e publicado um motor de implementação de computação na nuvem.
Esta técnica de implementação permite rápida alteração, escala, com resiliência contra ameaças de falha porque em qualquer altura a implementação pode ser repetida consistentemente para garantir um estado final.
A criação de ferramentas e serviços que suportam este estilo das operações através da automatização é uma resposta a estas alterações.

DSC é uma plataforma que fornece declarativa e implementação (repetíveis) idempotent, configuração e conformidade.
A plataforma de DSC permite-lhe garantir que os componentes do seu centro de dados têm a configuração correta, o que evita a erros e impede a falhas de implementação dispendiosos.
Por encará-los configurações de DSC como parte do código da aplicação, DSC permite a implementação contínua.
A configuração de DSC deve ser atualizada como parte da aplicação, garantindo o conhecimento necessário para implementar a aplicação é sempre atualizados e pronto a ser utilizado.

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a>"Preciso de PowerShell, por que motivo precisa a configuração de estado pretendido?"

Objetivo separado de configurações de DSC ou "o que pretender fazer", da execução, ou "como pretender fazê-lo."
Isto significa que a lógica de execução é contida os recursos.
Os utilizadores não é necessário saber como implementar ou implementar uma funcionalidade quando está disponível um recurso de DSC para essa funcionalidade.
Isto permite ao utilizador para se focarem na estrutura da implementação deles.

Por exemplo, scripts do PowerShell devem ter o seguinte aspeto:
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
Este script é simples, comprehensible e fácil.
No entanto, se tentar colocar nesse script em produção, será executado em vários problemas.
O que acontece se que o script é executado duas vezes numa linha?
O que acontece se Bernardo tinha anteriormente acesso total à partilha?

Para compensar estes problemas, uma versão do script "real" procurará próximo de algo semelhante ao seguinte:
```powershell
# But actually creating a share in an idempotent way would be

$shareExists = $false
$smbShare = Get-SmbShare -Name $Name -ErrorAction SilentlyContinue
if($smbShare -ne $null)
{
    Write-Verbose -Message "Share with name $Name exists"
    $shareExists = $true
}

if ($shareExists -eq $false)
{
    Write-Verbose "Creating share $Name to ensure it is Present"
    New-SmbShare @psboundparameters
}
else
{
    # Need to call either Set-SmbShare or *ShareAccess cmdlets
    if ($psboundparameters.ContainsKey("ChangeAccess"))
    {
       #...etc, etc, etc
    }
}
```

Este script é mais complexo, com muitos de lógica e processamento de erros.
O script for mais complexo porque já não são indicar que o que pretende efectuada, mas *como fazê-lo*.

DSC permite-lhe dizer o que pretende efectuada e a lógica subjacente é abstracted ausente.

```powershell
# A configuration is a special kind of PowerShell function
Configuration Sample_Share
{
   Import-DscResource -Module xSmbShare
   # Nodes are the endpoint we wish to configure
   # A Configuration block can have zero or more Node blocks
   Node $NodeName
   {
      # Next, specify one or more resource blocks
      # Resources are simply PowerShell modules that
      # implement the logic of "how" to execute a task
      xSmbShare MySMBShare
      {
          Ensure      = "Present"
          Name        = "MyShare"
          Path        = "C:\Demo\Temp"
          ReadAccess  = "Bob"
          FullAccess  = "Alice"
          Description = "This is an updated description for this share"
      }
   }
}
#Run the function to compile the configuration
Sample_Share
#Pass the configuration to the nodes we defined and configure them
Start-DscConfiguration Sample_Share
```

Este script está corretamente formatado e simples para leitura.
Os caminhos lógicos e processamento de erros são continuam presentes no [recursos](resources.md) implementação, mas invisíveis ao autor do script.

## <a name="separating-environment-from-structure"></a>Separação de ambiente de estrutura

Um padrão comum no DevOps consiste em vários ambientes para implementação.
Por exemplo, poderá ser um ambiente de "dev" utilizado para rapidamente criar protótipos novo código.
O código do ambiente de "dev" entra no ambiente de "teste", em que outras pessoas Certifique-se a nova funcionalidade.
Por fim, o código entra "prod" ou o ambiente de produção do site em direto.

Configurações de DSC acomodar este pipeline de teste-dev-prod através da utilização de [dados de configuração](configData.md).
Isto deduz ainda mais a diferença entre a estrutura da configuração de nós geridos.
Por exemplo, pode definir uma configuração que requer um SQL server, um servidor IIS e um servidor de camada média.
Independentemente da que nós recebem as diferentes partes desta configuração, essas três elementos sempre estará presentes.
Pode utilizar dados de configuração para apontar três todos os elementos para a mesma máquina para um ambiente de desenvolvimento, separado saída três elementos para três máquinas diferentes para um ambiente de teste e, finalmente, para todos os servidores de produção para o ambiente de prod.
Para implementar os ambientes diferentes, pode invocar **início DscConfiguration** com os dados de configuração correto para o ambiente de destino.

## <a name="see-also"></a>Consulte Também

[Configurações](configurations.md)

[Dados de configuração](configData.md)

[Recursos](resources.md)
