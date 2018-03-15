---
description: 
ms.topic: article
ms.prod: powershell
keywords: PowerShell, o cmdlet
ms.date: 2016-12-12
title: Adicionar pswaauthorizationrule
ms.technology: powershell
schema: 2.0.0
ms.openlocfilehash: 71954fc115daee4c05662d11baa2bc6a0a417896
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/15/2018
---
# <a name="add-pswaauthorizationrule"></a>Add-PswaAuthorizationRule

## <a name="synopsis"></a>SYNOPSIS

Adiciona uma nova regra de autorização para o conjunto de regras de autorização de acesso de Web do Windows PowerShell®.

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

O **Add-PswaAuthorizationRule** cmdlet adiciona uma nova regra de autorização para o conjunto de regras de autorização de acesso de Web do Windows PowerShell®.

Tem de especificar os utilizadores, computadores e pontos finais do Windows PowerShell para esta regra. Pode especificar utilizadores e computadores, contas de utilizador individuais e nomes de computador ou ao especificar os grupos.

Para um computador que está associado a um domínio do Active Directory, o cmdlet utiliza o identificador de segurança (SID) do computador para criar a regra.
Isto permite-lhe utilizar um nome abreviado de um nome de domínio completamente qualificado (FQDN) ou um endereço IP para o **nome do computador** campo na página de início de sessão.

Para um computador que não está associado a um domínio do Active Directory, o cmdlet cria a regra ao utilizar o nome do computador fornecido pelo administrador. Ligar com êxito a esta máquina, o utilizador final tem de fornecer o nome do computador exatamente conforme aparece na regra.

Se existirem vários computadores com o mesmo nome na rede, pode resolver nome abreviado a mais do que um computador. Isto pode levar a ambiguidade quando estabelecer uma ligação. Por exemplo, se existe uma regra para o computador de grupo de trabalho com o nome "*servidor1*" e um novo computador com o nome *server1.contoso.com* está associado à rede, utilizando as regras de autorização de validação é concluída com êxito e Acesso Web Windows PowerShell tenta estabelecer uma ligação ao computador com o nome "*servidor1*". Não é garantido que a ligação é estabelecida com o computador de grupo de trabalho especificado; a tentativa de foi possível estabelecer o grupo de trabalho ou o computador de domínio com o nome "*servidor1*". Para reduzir a ambiguidade, é recomendado que utilize o FQDN para o computador de destino, sempre que possível criar uma regra de autorização.

As regras de autorização avaliar a credencial primária início de sessão dos utilizadores de acesso Web Windows PowerShell, não as credenciais alternativas (o segundo conjunto de credenciais encontrado no **definições de ligação opcionais** secção a início de sessão página). Para obter um exemplo disto, consulte o exemplo 6.

## <a name="parameters"></a>Parâmetros

### <a name="-computergroupnameltstringgt"></a>-ComputerGroupName&lt;String&gt;

Especifica o nome de um grupo de computador nos serviços de domínio do Active Directory (AD DS) ou grupos locais para o qual esta regra concede acesso.

|||  
|-|-|
| Aliases                              | nenhum                                 |
| Obrigatório?                            | VERDADEIRO                                 |
| Posição?                            | com o nome                                |
| Valor Predefinido                        | nenhum                                 |
| Aceitar Entrada de Pipeline?               | VERDADEIRO (ByPropertyName)                |
| Aceitar Carateres Universais?          | falso                                |

### <a name="-computernameltstringgt"></a>-ComputerName&lt;String&gt;

Especifica o nome do computador ao qual esta regra concede acesso.

|||  
|-|-|
| Aliases                              | nenhum                                 |
| Obrigatório?                            | VERDADEIRO                                 |
| Posição?                            | com o nome                                |
| Valor Predefinido                        | nenhum                                 |
| Aceitar Entrada de Pipeline?               | VERDADEIRO (ByPropertyName)                |
| Aceitar Carateres Universais?          | falso                                |

### <a name="-configurationnameltstringgt"></a>-ConfigurationName&lt;String&gt;

Especifica o nome da configuração de sessão do Windows PowerShell, também conhecido como espaço de execução, ao qual esta regra concede acesso.

|||  
|-|-|
| Aliases                              | nenhum                                 |
| Obrigatório?                            | VERDADEIRO                                 |
| Posição?                            | com o nome                                |
| Valor Predefinido                        | nenhum                                 |
| Aceitar Entrada de Pipeline?               | VERDADEIRO (ByPropertyName)                |
| Aceitar Carateres Universais?          | falso                                |

### <a name="-credentialltpscredentialgt"></a>-Credential&lt;PSCredential&gt;

Especifica um **PSCredential** objeto para uma conta de utilizador que pretende utilizar para alterar as regras de autorização de acesso Web Windows PowerShell. Se não adicionar este parâmetro, o cmdlet utiliza a conta de utilizador atualmente com sessão iniciada. Para obter um **PSCredential** objeto, que é necessário para adicionar regras de autorização remotamente, execute o [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.

|||  
|-|-|
| Aliases                              | nenhum                                 |
| Obrigatório?                            | falso                                |
| Posição?                            | com o nome                                |
| Valor Predefinido                        | nenhum                                 |
| Aceitar Entrada de Pipeline?               | falso                                |
| Aceitar Carateres Universais?          | falso                                |

### <a name="-force"></a>-Force

Força o comando a executar sem pedir confirmação do utilizador. \
Além disso, este também solicita a confirmação ao introduzir um nome de computador simples ou curto (como um nome que não é um nome de domínio ou não está completamente qualificado). Confirmação solicitada por motivos de segurança, para que possa utilizar o nome simple para adicionar um computador apenas se o computador está num grupo de trabalho.

|||  
|-|-|
| Aliases                              | nenhum                                 |
| Obrigatório?                            | falso                                |
| Posição?                            | com o nome                                |
| Valor Predefinido                        | nenhum                                 |
| Aceitar Entrada de Pipeline?               | falso                                |
| Aceitar Carateres Universais?          | falso                                |

### <a name="-rulenameltstringgt"></a>-RuleName&lt;String&gt;

Especifica o nome amigável para esta regra.

|||  
|-|-|
| Aliases                              | nenhum                                 |
| Obrigatório?                            | falso                                |
| Posição?                            | com o nome                                |
| Valor Predefinido                        | nenhum                                 |
| Aceitar Entrada de Pipeline?               | VERDADEIRO (ByPropertyName)                |
| Aceitar Carateres Universais?          | falso                                |

### <a name="-usergroupnameltstringgt"></a>-UserGroupName&lt;String\[\]&gt;

Especifica o nome de um ou mais grupos de utilizador no AD DS ou grupos locais para o qual esta regra concede acesso.

|||  
|-|-|
| Aliases                              | nenhum                                 |
| Obrigatório?                            | VERDADEIRO                                 |
| Posição?                            | com o nome                                |
| Valor Predefinido                        | nenhum                                 |
| Aceitar Entrada de Pipeline?               | VERDADEIRO (ByPropertyName)                |
| Aceitar Carateres Universais?          | falso                                |

### <a name="-usernameltstringgt"></a>-UserName&lt;String\[\]&gt;

Especifica um ou mais utilizadores ao qual esta regra concede acesso. O nome de utilizador pode ser uma conta de utilizador local no computador gateway ou um utilizador no AD DS.
O formato é `domain\user` ou `computer\user`.

|||  
|-|-|
| Aliases                              | nenhum                                 |
| Obrigatório?                            | VERDADEIRO                                 |
| Posição?                            | 1                                    |
| Valor Predefinido                        | nenhum                                 |
| Aceitar Entrada de Pipeline?               | VERDADEIRO (ByValue, ByPropertyName)       |
| Aceitar Carateres Universais?          | falso                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Este cmdlet suporta os parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, e -OutVariable.
Para obter mais informações, consulte [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).

## <a name="inputs"></a>ENTRADAS

### <a name="string"></a>Cadeia

Este cmdlet aceita uma cadeia ou uma matriz de cadeias como entrada.

### <a name="string"></a>Cadeia\[\]

Este cmdlet aceita uma cadeia ou uma matriz de cadeias como entrada.

## <a name="outputs"></a>Saídas

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule

Este cmdlet devolve a um objeto de regra de autorização.

## <a name="examples"></a>EXEMPLOS

### <a name="example-1"></a>EXEMPLO 1

Neste exemplo concede acesso à configuração de sessão *PSWAEndpoint*, um restrito espaço de execução, no *srv2* para os utilizadores a *SMAdmins* grupo. \
**Tenha em atenção**: O nome do computador tem de ser um nome de domínio completamente qualificado (FQDN). Os administradores definem uma configuração de sessão restritas ou um espaço de execução, o que é um intervalo limitado de cmdlets e tarefas que os utilizadores finais podem ser executados. Definir um espaço de execução restrito pode impedir que os utilizadores acedam a outros computadores que são não num espaço de execução permitido do Windows PowerShell®, oferecendo assim uma ligação mais segura. Para obter mais informações sobre configurações de sessão, consulte [about_Session_Configurations](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) ou [instalar e utilizar o acesso Web Windows PowerShell](../install-and-use-windows-powershell-web-access.md).

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a>EXEMPLO 2

Neste exemplo concede acesso à configuração de sessão predefinida do Windows PowerShell, `Microsoft.PowerShell`, no *srv2* para utilizadores nos utilizadores com o nome contoso\\user1, contoso\\Utilizador2 e contoso\\user3. Este cmdlet cria três regras (1 por pessoa).

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a>EXEMPLO 3

Este exemplo ilustra como valores de nome de utilizador através do pipeline de entrada.

```
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a>EXEMPLO 4

Este exemplo ilustra a forma como todos os parâmetros tirar valores de pipeline ao nome da propriedade.

````PowerShell
$o = New-Object -TypeName PSObject | 
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru | 
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru | 
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a>EXEMPLO 5

Este exemplo adiciona uma regra para permitir ao utilizador local com o nome *PswaServer\\ChrisLocal* acesso ao servidor com o nome *srv1.contoso.com*.

Este exemplo ilustra um cenário em que o gateway está num grupo de trabalho e o computador de destino está num domínio. Se aplica a regra de autorização para utilizadores locais no gateway. O acesso Web Windows PowerShell-na página sessão, para autenticar com êxito, o utilizador tem de fornecer um segundo conjunto de credenciais no **definições de ligação opcionais** área. O servidor de gateway utiliza o conjunto de credenciais adicionais para autenticar o utilizador no computador de destino, um servidor com o nome *srv1.contoso.com*.

````
Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a>EXEMPLO 6

Este exemplo permite que todos os utilizadores acesso a todos os pontos finais em todos os computadores.
Isto essencialmente desativa a regras de autorização. \
**Tenha em atenção**: utilizar o `*` caráter universal não é recomendada para implementações de segurança confidenciais e deve apenas ser considerado para ambientes de teste ou utilizado em implementações em que pode ser flexibilizada segurança.

````PowerShell
Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a>Consulte Também

- [Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)
- [Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)
- [Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)
- [Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)
- [Add-Member](http://go.microsoft.com/fwlink/p/?LinkId=113280)
- [New-Object](http://go.microsoft.com/fwlink/p/?LinkId=113355)
- [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936)
