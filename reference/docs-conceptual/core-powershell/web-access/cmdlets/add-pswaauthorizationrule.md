---
ms.topic: reference
keywords: PowerShell, o cmdlet
ms.date: 12/12/2016
title: Add-PswaAuthorizationRule
schema: 2.0.0
ms.openlocfilehash: fe2b71dcfa870ba3f92484ae3fd3c45b3107a1bc
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45523084"
---
# <a name="add-pswaauthorizationrule"></a>Add-PswaAuthorizationRule

## <a name="synopsis"></a>SINOPSE

Adiciona uma nova regra de autorização para o conjunto de regras de autorização do Windows PowerShell Web Access.

## <a name="syntax"></a>Sintaxe

### <a name="usergroupnamecomputergroupname"></a>UserGroupNameComputerGroupName

```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a>UserGroupNameComputerName

```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a>UserNameComputerGroupName

```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a>UserNameComputerName

```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a>DESCRIÇÃO

O **Add-PswaAuthorizationRule** cmdlet adiciona uma nova regra de autorização para o conjunto de regras de autorização do Windows PowerShell(r) Web Access.

Tem de especificar os utilizadores, computadores e pontos de extremidade do Windows PowerShell para esta regra. Pode especificar utilizadores e computadores, contas de utilizador individuais e nomes de computador ou ao especificar grupos.

Para um computador que está associado a um domínio do Active Directory, o cmdlet utiliza o identificador de segurança (SID) do computador para criar a regra. Isto permite-lhe utilizar um nome abreviado, um nome de domínio completamente qualificado (FQDN) ou um endereço IP para o **nome do computador** campo na página de início de sessão.

Para um computador que não está associado a um domínio do Active Directory, o cmdlet cria a regra com o nome do computador fornecido pelo administrador. Para ligar com êxito a esta máquina, o utilizador final tem de fornecer o nome do computador exatamente como aparece na regra.

Se existirem vários computadores com o mesmo nome na rede, pode resolver nome abreviado para mais de um computador. Isto pode levar a ambigüidade durante o estabelecimento de uma ligação. Por exemplo, se existe uma regra para o computador de grupo de trabalho com o nome "*servidor1*" e um novo computador com o nome *server1.contoso.com* está associado à rede, usando as regras de autorização de validação é bem-sucedida e Windows PowerShell Web Access tenta estabelecer uma ligação para o computador com o nome "*servidor1*". Não é garantido que a ligação é estabelecida com o computador de grupo de trabalho especificado; a tentativa de foi possível estabelecer o grupo de trabalho ou o computador de domínio com o nome "*servidor1*". Para reduzir a ambiguidade, recomenda-se que utilize o FQDN para o computador de destino sempre que possível criar uma regra de autorização.

As regras de autorização avaliar a credencial primária início de sessão dos utilizadores do Windows PowerShell Web Access, não as credenciais alternativas (o segundo conjunto de credenciais encontrado no **definições de ligação opcionais** secção a página de entrada). Para obter um exemplo disto, consulte o exemplo 6.

## <a name="parameters"></a>Parâmetros

### <a name="-computergroupname-string"></a>-ComputerGroupName \<cadeia\>

Especifica o nome de um grupo de computadores em serviços de domínio do Active Directory (AD DS) ou grupos locais para a qual esta regra concede acesso.

|||
|-|-|
| Aliases                     | nenhum                  |
| Obrigatório?                   | VERDADEIRO                  |
| Posição?                   | com o nome                 |
| Valor Predefinido               | nenhum                  |
| Aceitar Entrada de Pipeline?      | TRUE (ByPropertyName) |
| Aceitar Carateres Universais? | falso                 |

### <a name="-computername-string"></a>-ComputerName \<cadeia\>

Especifica o nome do computador ao qual esta regra concede acesso.

|||
|-|-|
| Aliases                     | nenhum                  |
| Obrigatório?                   | VERDADEIRO                  |
| Posição?                   | com o nome                 |
| Valor Predefinido               | nenhum                  |
| Aceitar Entrada de Pipeline?      | TRUE (ByPropertyName) |
| Aceitar Carateres Universais? | falso                 |

### <a name="-configurationname-string"></a>-ConfigurationName \<cadeia\>

Especifica o nome da configuração de sessão do Windows PowerShell, também conhecido como espaço de execução, ao qual esta regra concede acesso.

|||
|-|-|
| Aliases                     | nenhum                  |
| Obrigatório?                   | VERDADEIRO                  |
| Posição?                   | com o nome                 |
| Valor Predefinido               | nenhum                  |
| Aceitar Entrada de Pipeline?      | TRUE (ByPropertyName) |
| Aceitar Carateres Universais? | falso                 |

### <a name="-credential--pscredential"></a>-Credential \<PSCredential\>

Especifica um **PSCredential** objeto para uma conta de utilizador que pretende utilizar para alterar as regras de autorização do Windows PowerShell Web Access. Se não adicionar este parâmetro, o cmdlet utiliza a conta de utilizador com sessão atualmente iniciada. Para obter um **PSCredential** objeto, que é necessário para adicionar regras de autorização remotamente, execute o [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.

|||
|-|-|
| Aliases                     | nenhum  |
| Obrigatório?                   | falso |
| Posição?                   | com o nome |
| Valor Predefinido               | nenhum  |
| Aceitar Entrada de Pipeline?      | falso |
| Aceitar Carateres Universais? | falso |

### <a name="-force"></a>-Force

Força o comando a ser executado sem solicitar a confirmação do utilizador. Além disso, ele também solicita a confirmação ao introduzir um nome de computador simples ou curto (como um nome que não é um nome de domínio ou não é totalmente qualificado). Confirmação é solicitada por motivos de segurança, para que possa utilizar o nome simple para adicionar um computador apenas se o computador está num grupo de trabalho.

|||
|-|-|
| Aliases                              | nenhum                                 |
| Obrigatório?                            | falso                                |
| Posição?                            | com o nome                                |
| Valor Predefinido                        | nenhum                                 |
| Aceitar Entrada de Pipeline?               | falso                                |
| Aceitar Carateres Universais?          | falso                                |

### <a name="-rulename-string"></a>-RuleName \<cadeia\>

Especifica o nome amigável para esta regra.

|||
|-|-|
| Aliases                              | nenhum                                 |
| Obrigatório?                            | falso                                |
| Posição?                            | com o nome                                |
| Valor Predefinido                        | nenhum                                 |
| Aceitar Entrada de Pipeline?               | TRUE (ByPropertyName)                |
| Aceitar Carateres Universais?          | falso                                |

### <a name="-usergroupname-string"></a>-UserGroupName \<cadeia\[\]\>

Especifica o nome de um ou mais grupos de utilizadores no AD DS ou grupos locais para a qual esta regra concede acesso.

|||
|-|-|
| Aliases                              | nenhum                                 |
| Obrigatório?                            | VERDADEIRO                                 |
| Posição?                            | com o nome                                |
| Valor Predefinido                        | nenhum                                 |
| Aceitar Entrada de Pipeline?               | TRUE (ByPropertyName)                |
| Aceitar Carateres Universais?          | falso                                |

### <a name="-username-string"></a>-UserName \<cadeia\[\]\>

Especifica um ou mais utilizadores ao qual esta regra concede acesso. O nome de utilizador pode ser uma conta de utilizador local no computador gateway ou um utilizador no AD DS. O formato é `domain\user` ou `computer\user`.

|||
|-|-|
| Aliases                              | nenhum                                 |
| Obrigatório?                            | VERDADEIRO                                 |
| Posição?                            | 1                                    |
| Valor Predefinido                        | nenhum                                 |
| Aceitar Entrada de Pipeline?               | TRUE (ByValue, ByPropertyName)       |
| Aceitar Carateres Universais?          | falso                                |

###  <a name="commonparameters"></a>\<CommonParameters\>

Este cmdlet suporta os parâmetros comuns:

-Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, e -OutVariable.
Para obter mais informações, consulte [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).

## <a name="inputs"></a>ENTRADAS

### <a name="string"></a>Cadeia

Este cmdlet aceita uma cadeia de caracteres ou uma matriz de cadeias de caracteres como entrada.

### <a name="string"></a>Cadeia de caracteres\[\]

Este cmdlet aceita uma cadeia de caracteres ou uma matriz de cadeias de caracteres como entrada.

## <a name="outputs"></a>Saídas

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule

Este cmdlet devolve a um objeto de regra de autorização.

## <a name="examples"></a>EXEMPLOS

### <a name="example-1"></a>EXEMPLO 1

Neste exemplo concede acesso à configuração de sessão _PSWAEndpoint_, um restritas espaço de execução, na _srv2_ para utilizadores no _SMAdmins_ grupo.

> [!NOTE]
> O nome do computador tem de ser um nome de domínio completamente qualificado (FQDN). Os administradores de definir uma configuração de sessão restritas ou espaço de execução, o que é um intervalo limitado de cmdlets e tarefas que os utilizadores finais podem ser executadas. Definir um espaço de execução restrito pode impedir que os utilizadores acedam a outros computadores que não estiver num espaço de execução permitido do Windows PowerShell(r), portanto, oferecendo uma conexão mais segura. Para obter mais informações sobre configurações de sessão, consulte [about_Session_Configurations](/powershell/module/microsoft.powershell.core/about/about_session_configurations) ou [instalar e utilizar o acesso Web Windows PowerShell](../install-and-use-windows-powershell-web-access.md).

```powershell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a>EXEMPLO 2

Neste exemplo concede acesso para a configuração de sessão do Windows PowerShell padrão `Microsoft.PowerShell`, no *srv2* aos utilizadores dos utilizadores com o nome `contoso\user1`, `contoso\user2`, e `contoso\user3`. Este cmdlet cria três regras (1 por pessoa).

```powershell
Add-PswaAuthorizationRule -UserName contoso\user1, contoso\user2, contoso\user3 -ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a>EXEMPLO 3

Este exemplo ilustra como valores de nome de utilizador através do pipeline de entrada.

```powershell
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule -ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a>EXEMPLO 4

Este exemplo ilustra como todos os parâmetros tirar valores do pipeline por nome de propriedade.

````powershell
$o = New-Object -TypeName PSObject |
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru |
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru |
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" -PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a>EXEMPLO 5

Este exemplo adiciona uma regra para permitir que o usuário local chamado `PswaServer\ChrisLocal` acesso ao servidor com o nome **srv1.contoso.com**.

Este exemplo ilustra um cenário onde o gateway está num grupo de trabalho e o computador de destino está num domínio. Se aplica a regra de autorização para os utilizadores locais no gateway. Na página do Windows PowerShell Web Access início de sessão, para autenticar com êxito, o utilizador tem de fornecer um segundo conjunto de credenciais no **definições de ligação opcionais** área. O servidor de gateway utiliza o conjunto de credenciais adicional para autenticar o utilizador no computador de destino, um servidor com o nome *srv1.contoso.com*.

````powershell
Add-PswaAuthorizationRule -UserName PswaServer\ChrisLocal -ComputerName srv1.contoso.com -ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a>EXEMPLO 6

Este exemplo permite todos os utilizadores o acesso a todos os pontos finais em todos os computadores. Essencialmente, isso se desligar as regras de autorização.

> [!NOTE]
> Utilizar o `*` caráter universal não é recomendada para implementações de protegida e deve apenas ser considerado para ambientes de teste ou utilizado em implementações em que pode ser Relaxada segurança.

````powershell
Add-PswaAuthorizationRule -UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a>Consulte Também

[Get-PswaAuthorizationRule](https://technet.microsoft.com/library/jj592891(v=wps.630).aspx)

[Remove-PswaAuthorizationRule](https://technet.microsoft.com/library/jj592893(v=wps.630).aspx)

[Test-PswaAuthorizationRule](https://technet.microsoft.com/library/jj592892(v=wps.630).aspx)

[Install-PswaWebApplication](https://technet.microsoft.com/library/jj592894(v=wps.630).aspx)

[Adicionar membros](http://go.microsoft.com/fwlink/p/?LinkId=113280)

[New-Object](http://go.microsoft.com/fwlink/p/?LinkId=113355)

[Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936)
