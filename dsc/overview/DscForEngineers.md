---
ms.date: 10/13/2017
keywords: DSC, powershell, configuração, a configuração
title: Descrição Geral do Desired State Configuration para Engenheiros
ms.openlocfilehash: 0e599c2218cd2df29dbd0529006be5e1ef17ce5f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405367"
---
# <a name="desired-state-configuration-overview-for-engineers"></a>Descrição Geral do Desired State Configuration para Engenheiros

Este documento destina-se para as equipas de programação e operações compreender os benefícios do PowerShell Desired State Configuration (DSC).
Para uma vista de nível superior do valor DSC fornece, veja [Desired State Configuration descrição geral para tomadores de decisões](decisionMaker.md)

## <a name="benefits-of-desired-state-configuration"></a>Benefícios do Desired State Configuration

DSC existe para:

- Diminuir a complexidade do processamento de scripts no Windows
- Aumentar a velocidade de iteração

O conceito de "implementação contínua" está se tornando mais importante.
Implementação contínua significa que a capacidade de implementar com frequência, potencialmente, muitas vezes por dia.
A finalidade destas implementações são não para corrigir algo, mas para obter algo publicados de forma rápida.
Obtendo novos recursos por meio do desenvolvimento em operação tão suave e de forma fiável do possível, reduza tempo / valor da nova lógica de negócios.

O movimento na direção de implica uma solução de implementação que utiliza um modelo de modelo "declarativa", em que um ambiente de estado final é declarado como texto e publicado um mecanismo de implementação de informática na cloud.
Essa técnica de implantação permite alterações rápidas, à escala, com resiliência contra ameaças de falha porque a qualquer momento a implementação pode ser repetida consistentemente para garantir um estado final.
A criação de ferramentas e serviços que oferecem suporte a esse estilo de operações por meio de automação é uma resposta a essas mudanças.

DSC é uma plataforma que fornece declarativa e a implantação de (repetível) de idempotentes, a configuração e a conformidade.
A plataforma de DSC permite-lhe garantir que os componentes do seu centro de dados tenham a configuração correta, o que evita erros e evita falhas de implementação de alto custo.
Ao tratar as configurações de DSC como parte do código do aplicativo, o DSC permite a implementação contínua.
A configuração de DSC deve ser atualizada como parte da aplicação, garantindo que o conhecimento necessário para implementar a aplicação é sempre atualizado e pronto a ser utilizado.

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a>"Eu tenho o PowerShell, por que razão necessito de Desired State Configuration?"

Objetivo de separado de configurações de DSC, ou "o que quero fazer", de execução, ou "como eu quero fazê-lo."
Isso significa que a lógica de execução está contida nos recursos.
Os utilizadores não têm de saber como implementar ou implantar um recurso quando um recurso de DSC para essa funcionalidade está disponível.
Isto permite ao utilizador para se concentrar a estrutura da implementação deles.

Por exemplo, scripts do PowerShell devem ter um aspeto semelhante a esta:
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
Este script é simples, simples e compreensível.
No entanto, se tentar colocar esse script em produção, será executado em vários problemas.
O que acontece se que o script for executado duas vezes numa linha?
O que acontece se Bob tinha anteriormente o acesso total à partilha?

Para compensar estes problemas, uma versão "real" o script ficará mais de perto para algo como:
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

Este script é mais complexo, com muita lógica e tratamento de erros.
O script é mais complexo porque já não são que diz o que deseja concluído, mas *como fazê-lo*.

DSC, pode dizer o que deseja concluído e a lógica subjacente é abstraída.

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

Este script está corretamente formatado e fácil de ler.
Os caminhos de lógica e o tratamento de erros ainda estão presentes no [recursos](../resources/resources.md) implementação, mas invisível para o autor do script.

## <a name="separating-environment-from-structure"></a>Separar o ambiente de estrutura

Um padrão comum em DevOps é ter vários ambientes para a implementação.
Por exemplo, pode ser um ambiente de "dev" usado para rapidamente código novo do protótipo.
O código do ambiente de "dev" vai para um ambiente de "teste", onde outras pessoas verificar a nova funcionalidade.
Por fim, o código entra "prod" ou o ambiente de produção do site em direto.

Configurações de DSC acomodar este pipeline de desenvolvimento-teste-prod através da utilização de [dados de configuração](../configurations/configData.md).
Isso ainda mais abstrai a diferença entre a estrutura da configuração a partir de nós que são geridos.
Por exemplo, pode definir uma configuração que requer um SQL server, um servidor IIS e um servidor de camada intermediária.
Independentemente do que nós recebem as diferentes partes desta configuração, esses três elementos sempre estará presentes.
Pode utilizar dados de configuração para apontar a todos os três elementos em direção à mesma máquina para um ambiente de desenvolvimento, separado horizontalmente os três elementos para três máquinas diferentes para um ambiente de teste e, finalmente, para todos os servidores de produção para o ambiente de produção.
Para implementar em diferentes ambientes, pode invocar **Start-dscconfiguration para** com os dados de configuração correto para o ambiente de destino.

## <a name="see-also"></a>Consulte Também

[Configurações](../configurations/configurations.md)

[Dados de configuração](../configurations/configData.md)

[Recursos](../resources/resources.md)
