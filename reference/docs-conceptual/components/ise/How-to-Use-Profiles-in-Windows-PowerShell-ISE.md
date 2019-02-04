---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Como Utilizar Perfis no ISE do Windows PowerShell
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
ms.openlocfilehash: b319aa089c2a4a7008acd9850f15342dac70aee2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684466"
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a>Como Utilizar Perfis no ISE do Windows PowerShell

Este tópico explica como utilizar perfis no Windows PowerShell® Integrated Scripting Environment (ISE). Recomendamos que antes de executar as tarefas nesta secção, reveja [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), ou no painel da consola, tipo, `Get-Help about_Profiles` e prima **ENTER**.

Um perfil é um script do ISE do Windows PowerShell que é executada automaticamente quando iniciar uma sessão de novo.  Pode criar um ou mais perfis do Windows PowerShell para o ISE do Windows PowerShell e utilizá-los para adicionar a configurar o ambiente do Windows PowerShell ou o Windows PowerShell ISE, preparando-o para a sua utilização, com variáveis, aliases, funções e a cor e tipo de letra preferências que quer estão disponíveis. Um perfil afeta todas as sessões de ISE do Windows PowerShell que começar.

> [!NOTE]
> A política de execução do Windows PowerShell determina se pode executar scripts e um perfil de carga. A diretiva de execução padrão "Restritas", impede que todos os scripts sejam executados, incluindo perfis. Se utilizar a política de "Restrito", não é possível carregar o perfil. Para obter mais informações sobre a política de execução, consulte [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a>Selecionar um perfil para utilizar no ISE do Windows PowerShell

ISE do Windows PowerShell suporta perfis para o utilizador atual e todos os utilizadores. Também suporta os perfis do Windows PowerShell que se aplicam a todos os anfitriões.

O perfil que utiliza é determinado pelo como usar o Windows PowerShell e Windows PowerShell ISE.

- Se utilizar apenas o Windows PowerShell ISE para executar o Windows PowerShell, em seguida, guarde a todos os seus itens em um dos perfis de ISE específicos, como o perfil de CurrentUserCurrentHost para ISE do Windows PowerShell ou o perfil de AllUsersCurrentHost para Windows PowerShell ISE.

- Se utilizar vários programas de anfitrião para executar o Windows PowerShell, salvar seus aliases, funções, variáveis e comandos num perfil que afeta todos os programas de anfitrião, como o CurrentUserAllHosts ou o perfil de AllUsersAllHosts e guardar os recursos específicos do ISE, como cor e tipo de letra personalização no perfil de CurrentUserCurrentHost para o perfil do ISE do Windows PowerShell ou o perfil de AllUsersCurrentHost para Windows PowerShell ISE.

Seguem-se os perfis podem ser criados e utilizados no ISE do Windows PowerShell. Cada perfil é salvo em seu próprio caminho específico.

| Tipo de perfil | Caminho do perfil |
| --- | --- |
| **Utilizador atual, o ISE do PowerShell**| `$PROFILE.CurrentUserCurrentHost`, ou `$PROFILE` |
| **Todos os utilizadores, o ISE do PowerShell**| `$PROFILE.AllUsersCurrentHost` |
| **Utilizador atual, todos os anfitriões**| `$PROFILE.CurrentUserAllHosts` |
| **Todos os utilizadores, todos os anfitriões** | `$PROFILE.AllUsersAllHosts` |

## <a name="to-create-a-new-profile"></a>Para criar um novo perfil

Para criar um novo "utilizador atual, a ISE do Windows PowerShell" perfil, execute este comando:

```powershell
if (!(Test-Path -Path $PROFILE ))
{ New-Item -Type File -Path $PROFILE -Force }
```

Para criar um novo "Todos os utilizadores, a ISE do Windows PowerShell" perfil, execute este comando:

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost))
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

Para criar um novo perfil "utilizador atual, todos os anfitriões", execute este comando:

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts))
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

Para criar um novo perfil de "todos os utilizadores, todos os anfitriões", escreva:

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts))
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a>Para editar um perfil

1. Para abrir o perfil, execute o comando psedit com a variável que especifica o perfil que pretende editar. Por exemplo, para abrir o "utilizador atual, a ISE do Windows PowerShell" de perfil, escreva: `psEdit $PROFILE`

2. Adicione alguns itens ao seu perfil. Seguem-se alguns exemplos para começar:

   - Para alterar a cor de fundo padrão do painel de consola para azul, no tipo de ficheiro de perfil: `$psISE.Options.OutputPaneBackground = 'blue'` . Para obter mais informações sobre a variável $psISE, consulte [referência do modelo de objeto ISE do Windows PowerShell](object-model/The-ISE-Object-Model-Hierarchy.md).

   - Para alterar o tamanho da fonte para 20, no tipo de ficheiro de perfil: `$psISE.Options.FontSize =20`

3. Para guardar o ficheiro de perfil, diante a **arquivo** menu, clique em **guardar**. Próxima vez que abrir o ISE do Windows PowerShell, as personalizações são aplicadas.

## <a name="see-also"></a>Veja Também

- [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)
- [Introdução ao ISE do Windows PowerShell](Introducing-the-Windows-PowerShell-ISE.md)