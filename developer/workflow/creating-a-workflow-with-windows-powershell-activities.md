---
title: Criar um fluxo de trabalho com o Windows PowerShell atividades | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 65d04c526ef7aa112da82adb924c0789731f3850
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845039"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a>Creating a Workflow with Windows PowerShell Activities (Criar um Fluxo de Trabalho com Atividades do Windows PowerShell)

Pode criar um fluxo de trabalho do Windows PowerShell ao selecionar a atividades do Visual Studio Toolbox e ao arrastá-los para a janela do estruturador de fluxo de trabalho. Para obter informações sobre como adicionar atividades do Windows PowerShell para o Visual Studio Toolbox, consulte [adição de atividades do Windows PowerShell para o Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).

Os procedimentos seguintes descrevem como criar um fluxo de trabalho que verifica o estado do domínio de um grupo de computadores especificadas pelo utilizador, associa-a um domínio, se já não estão associados e, em seguida, verifica o estado novamente.

### <a name="setting-up-the-project"></a>Definindo o projeto

1. Siga o procedimento descrito [adição de atividades do Windows PowerShell para o Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) para criar um projeto de fluxo de trabalho e adicionar as atividades a [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) e [ Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) assemblies à caixa de ferramentas.

2. Adicione System.Management.Automation, Microsoft.PowerShell.Activities, gestão de sistemas, Microsoft.PowerShell.Management.Activities e Microsoft.PowerShell.Commands.Management como para o projeto como assemblies de referência.

### <a name="adding-activities-to-the-workflow"></a>Adicionar atividades ao fluxo de trabalho

1. Adicionar uma **sequência** atividade ao fluxo de trabalho.

2. Criar um argumento com o nome `ComputerName` com um tipo de argumento do `String[]`. Este argumento representa os nomes dos computadores para verificar e Junte-se.

3. Criar um argumento com o nome `DomainCred` typu [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential). Este argumento representa as credenciais de domínio de uma conta de domínio que está autorizado para associar um computador ao domínio.

4. Criar um argumento com o nome `MachineCred` typu [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential). Este argumento representa as credenciais de administrador nos computadores para verificar e Junte-se.

5. Adicionar uma **ParallelForEach** atividade dentro do **sequência** atividade. Introduza `comp` e `ComputerName` em caixas de texto para que o loop faz a iteração pelos elementos do `ComputerName` matriz.

6. Adicionar uma **sequência** atividade ao corpo dos **ParallelForEach** atividade. Definir o **DisplayName** propriedade da sequência para `JoinDomain`.

7. Adicionar uma **GetWmiObject** atividade para o **JoinDomain** sequência.

8. Editar as propriedades do **GetWmiObject** atividade da seguinte forma.

   |Propriedade|Valor|
   |--------------|-----------|
   |**Classe**|"Win32_ComputerSystem"|
   |**PSComputerName**|{comp}|
   |**PSCredential**|MachineCred|

9. Adicionar uma **AddComputer** atividade para o **JoinDomain** sequência após o **GetWmiObject** atividade.

10. Editar as propriedades do **AddComputer** atividade da seguinte forma.

    |Propriedade|Valor|
    |--------------|-----------|
    |**ComputerName**|{comp}|
    |**DomainCredential**|DomainCred|

11. Adicionar uma **RestartComputer** atividade para o **JoinDomain** sequência após o **AddComputer** atividade.

12. Editar as propriedades do **RestartComputer** atividade da seguinte forma.

    |Propriedade|Valor|
    |--------------|-----------|
    |**ComputerName**|{comp}|
    |**Credencial**|MachineCred|
    |**para**|Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell|
    |**Force**|True|
    |Aguarde|True|
    |PSComputerName|{""}|

13. Adicionar uma **GetWmiObject** atividade para o **JoinDomain** sequência após o **RestartComputer** atividade. Editar as respetivas propriedades para ser o mesmo que a anterior **GetWmiObject** atividade.

    Quando tiver concluído os procedimentos, a janela de design de fluxo de trabalho deve ser assim:

    ![JoinDomain XAML no designer de fluxo de trabalho](../media/joindomainworkflow.png)
    ![JoinDomain XAML no designer de fluxo de trabalho](../media/joindomainworkflow.png "JoinDomainWorkflow")