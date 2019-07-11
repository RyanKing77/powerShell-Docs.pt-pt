---
title: Referência do Windows PowerShell | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows PowerShell SDK
ms.assetid: cbba4879-bcac-484a-9906-4bbe2cd1eb33
caps.latest.revision: 11
ms.openlocfilehash: 48b2b2b9ab2a39cf185ed54bcfa99d46562e13b6
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733747"
---
# <a name="windows-powershell-reference"></a>Windows PowerShell Reference (Referências do Windows PowerShell)

Windows PowerShell é um ambiente de conectados ao .NET Framework do Microsoft concebido para automação administrativa. Windows PowerShell fornece uma nova abordagem para a criação de comandos, composição de soluções e a criação gráfica de usuário ferramentas de gestão baseado na interface.

Windows PowerShell permite que um administrador de sistema para a execução de comandos para automatizar a administração de recursos do sistema diretamente ou através de scripts.

## <a name="developer-audience"></a>Público de desenvolvedores

O Software Development Kit (SDK) do Windows PowerShell foi escrito para desenvolvedores de comando que exigem informações de referência sobre as APIs fornecidas pelo Windows PowerShell. Os desenvolvedores de comando utilizam o Windows PowerShell para criar os comandos e fornecedores que estendem as tarefas que podem ser executadas pelo Windows PowerShell.

## <a name="windows-powershell-resources"></a>Recursos do Windows PowerShell

Além do SDK do Windows PowerShell, os seguintes recursos fornecem mais informações.

[Introdução ao Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell) fornece uma introdução ao Windows PowerShell: o idioma, os cmdlets, os fornecedores e o uso de objetos.

[Escrever um módulo do Windows PowerShell](./module/writing-a-windows-powershell-module.md) fornece informações e exemplos para os administradores, desenvolvedores de script e desenvolvedores de cmdlet que precisam para empacotar e distribuir as suas soluções do Windows PowerShell com módulos do Windows PowerShell.

[Escrever um Cmdlet do Windows PowerShell](./cmdlet/writing-a-windows-powershell-cmdlet.md) fornece informações e exemplos de código para gerentes de programa que estão a conceber cmdlets e para os desenvolvedores que estão a implementar o código de cmdlet.

[Blog da Equipe do Windows PowerShell](https://blogs.msdn.microsoft.com/PowerShell/) o melhor recurso para aprender e colaborar com outros utilizadores do Windows PowerShell. Leia o blog da Equipe do Windows PowerShell e, em seguida, associe o Fórum de utilizador do Windows PowerShell (microsoft.public.windows.powershell). Utilize o Windows Live Search para localizar outros blogs do Windows PowerShell e recursos. Em seguida, ao desenvolver seu conhecimento, livremente contribua com suas idéias.

[Browser de módulos do PowerShell](/powershell/module/) fornece as versões mais recentes dos tópicos de ajuda da linha de comandos.

## <a name="class-libraries"></a>Bibliotecas de classes

[System.Management.Automation](/dotnet/api/System.Management.Automation) este espaço de nomes é o espaço de nomes de raiz para o Windows PowerShell. Ela contém as classes, enumerações e interfaces necessárias para implementar cmdlets personalizados. Em particular, o [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe é a classe base da qual cmdlet todas as classes tem de ser derivadas. Para obter mais informações sobre os cmdlets, consulte.

[System.Management.Automation.Provider](/dotnet/api/System.Management.Automation.Provider) este espaço de nomes contém as classes, enumerações e interfaces necessárias para implementar um fornecedor de Windows PowerShell. Em particular, o [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe é a classe base a partir do qual PowerShell Windows todas as classes de fornecedor tem de ser derivados.

[Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) este espaço de nomes contém as classes para os cmdlets e provedores implementados pelo Windows PowerShell. Da mesma forma, é recomendado que crie uma *oseunome*. Espaço de nomes de comandos no caso dos cmdlets que implementar.

[System.Management.Automation.Host](/dotnet/api/System.Management.Automation.Host) este espaço de nomes contém as classes, enumerações e interfaces que o cmdlet usa para definir a interação entre o utilizador e o Windows PowerShell.

[System.Management.Automation.Internal](/dotnet/api/System.Management.Automation.Internal) este espaço de nomes contém as classes de bases utilizadas por outras classes de espaço de nomes. Por exemplo, o [System.Management.Automation.Internal.Cmdletmetadataattribute](/dotnet/api/System.Management.Automation.Internal.CmdletMetadataAttribute) classe é a classe base para o [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) classe.

[System.Management.Automation.Runspaces](/dotnet/api/System.Management.Automation.Runspaces) este espaço de nomes contém as classes, enumerações e interfaces utilizadas para criar um espaço de execução do Windows PowerShell. Neste contexto, o espaço de execução do Windows PowerShell é o contexto em que um ou mais pipelines de Windows PowerShell invocar cmdlets. Ou seja, os cmdlets funcionam dentro do contexto de um espaço de execução do Windows PowerShell. Para obter mais informações aboutWindows espaços de execução do PowerShell, consulte [espaços de execução do Windows PowerShell](https://msdn.microsoft.com/en-us/a1582cfe-f06d-4aff-adc6-71f49a860ce9).
