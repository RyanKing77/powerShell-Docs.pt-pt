---
ms.date: 2017-06-05
keywords: PowerShell, o cmdlet
title: Como utilizar perfis no ISE do Windows PowerShell
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
ms.openlocfilehash: f959aeb91eecc8056c91c56162ea9bff53537be9
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/08/2017
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a>Como utilizar perfis no ISE do Windows PowerShell
Este tópico explica como utilizar perfis no Windows PowerShell® Integrated Scripting Environment (ISE). Recomendamos que antes de executar as tarefas nesta secção, consulte o artigo [about_Profiles [v4]](https://technet.microsoft.com/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054(v=wps.630)), ou no painel de consola, tipo, `Get-Help about_Profiles` e prima **ENTER**.

Um perfil é um script de ISE do Windows PowerShell que é executado automaticamente quando iniciar uma nova sessão.  Pode criar um ou mais perfis do Windows PowerShell para o ISE do Windows PowerShell e utilizá-los para adicionar a configurar o ambiente do Windows PowerShell ou o ISE do Windows PowerShell, prepará-lo para utilização, com variáveis, aliases, funções e cor e o tipo de letra preferências que pretende que sejam disponíveis. Um perfil afeta cada sessão de ISE do Windows PowerShell que pode inicia.

> [!NOTE]
> A política de execução do Windows PowerShell determina se pode executar scripts e um perfil de carga. A política de execução da predefinição "Restrito," impedem que todos os scripts sejam executados, incluindo perfis. Se utilizar a política de "Restrito", não é possível carregar o perfil. Para obter mais informações sobre a política de execução, consulte [about_Execution_Policies [v4]](https://technet.microsoft.com/library/347708dc-1515-4d74-978b-8334603472e6(v=wps.630)).

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a>Selecionar um perfil para utilizar no ISE do Windows PowerShell
ISE do Windows PowerShell suporta perfis para o utilizador atual e todos os utilizadores. Também suporta os perfis do Windows PowerShell que se aplicam a todos os anfitriões.

O perfil que utiliza é determinado pelo como utilizar o Windows PowerShell e o ISE do Windows PowerShell.

- Se utilizar apenas ISE do Windows PowerShell para executar o Windows PowerShell, em seguida, guarde a todos os seus itens dos perfis de ISE específicas, tais como o perfil de CurrentUserCurrentHost para ISE do Windows PowerShell ou o perfil de AllUsersCurrentHost para ISE do Windows PowerShell.

- Se utilizar vários programas de anfitrião para executar o Windows PowerShell, guarde a funções, aliases, variáveis e os comandos num perfil que afeta todos os programas de anfitrião, como o CurrentUserAllHosts ou no perfil de AllUsersAllHosts e guardar funcionalidades específicas do ISE, como cor e o tipo de letra personalização no perfil de CurrentUserCurrentHost para perfil do ISE do Windows PowerShell ou o perfil de AllUsersCurrentHost para ISE do Windows PowerShell.

Seguem-se perfis que podem ser criados e utilizados no ISE do Windows PowerShell. Cada perfil é guardado para a sua própria caminho específico.

| Tipo de perfil | Caminho do perfil |
| --- | --- |
| **Utilizador atual, o ISE do PowerShell**| `$PROFILE.CurrentUserCurrentHost`, ou`$PROFILE` |
| **Todos os utilizadores, ISE do PowerShell**| `$PROFILE.AllUsersCurrentHost` |
| **Utilizador atual, todos os anfitriões**| `$PROFILE.CurrentUserAllHosts` |
| **Todos os utilizadores, todos os anfitriões** | `$PROFILE.AllUsersAllHosts` |

## <a name="to-create-a-new-profile"></a>Para criar um novo perfil
Para criar um nova "utilizador atual, ISE do Windows PowerShell" perfil, execute este comando:

```powershell
if (!(Test-Path -Path $PROFILE )) 
{ New-Item -Type File -Path $PROFILE -Force }
```

Para criar uma nova "Todos os utilizadores, ISE do Windows PowerShell" perfil, execute este comando:

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost)) 
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

Para criar um novo perfil "utilizador atual, todos os anfitriões", execute este comando:

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts)) 
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

Para criar um novo perfil "todos os utilizadores, todos os anfitriões", escreva:

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts)) 
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a>Para editar um perfil

1. Para abrir o perfil, execute o comando psedit com a variável que especifica o perfil que pretende editar. Por exemplo, para abrir o "utilizador atual, ISE do Windows PowerShell" perfil, escreva:`psEdit $PROFILE`

2. Adicione alguns itens para o seu perfil. Seguem-se alguns exemplos para ajudar a começar:

    -   Para alterar a cor de fundo predefinido do painel de consola para azul, no tipo de ficheiro de perfil: `$psISE.Options.OutputPaneBackground = 'blue'` . Para mais informações sobre a variável de $psISE, consulte [referência de modelo de objeto do Windows PowerShell ISE](The-ISE-Object-Model-Hierarchy.md).

    -   Para alterar o tamanho do tipo de letra para 20, no tipo de ficheiro de perfil:`$psISE.Options.FontSize =20`

3. Para guardar o ficheiro de perfil, no **ficheiro** menu, clique em **guardar**. Próxima vez que abrir o ISE do Windows PowerShell, as personalizações são aplicadas.

## <a name="see-also"></a>Consulte Também
- [about_Profiles [v4]](https://technet.microsoft.com/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054(v=wps.630))
- [Utilizar o ISE do Windows PowerShell](Using-the-Windows-PowerShell-ISE.md)

