---
description: ''
ms.topic: article
ms.prod: powershell
keywords: PowerShell, o cmdlet
ms.date: 12/12/2016
title: teste pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: ed6d56b2f3c4ee4ac410cdaadda312bffe506ee9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="test-pswaauthorizationrule"></a>Test-PswaAuthorizationRule

## <a name="synopsis"></a>SYNOPSIS

Verifica se existe uma regra para um utilizador especificado, o computador ou o ponto final.

## <a name="syntax"></a>SYNTAX

### <a name="computername"></a>ComputerName
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a>ConnectionUri
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a>DESCRIÇÃO

O **Test-PswaAuthorizationRule** cmdlet verifica se existe uma regra para um utilizador especificado, o computador ou o ponto final.
Este cmdlet também pode ser utilizado para testar as regras de autorização, para validar que um pedido de acesso de utilizador, computador ou ponto final específico está autorizado.
Por predefinição, este cmdlet avalia todas as regras no ficheiro de autorização.
No entanto, pode especificar um subconjunto de regras para testar.

Pode utilizar este cmdlet para ajudar a resolver problemas de falhas de autenticação.

Os parâmetros para este cmdlet correspondem aos campos da página de início de sessão o acesso Web do Windows PowerShell®.

## <a name="parameters"></a>PARÂMETROS

### <a name="-computername-ltstringgt"></a>-ComputerName &lt;cadeia&gt;

Especifica o nome do computador para testar.

|||
|-|-|
| Aliases                              | nenhum                                 |
| Obrigatório?                            | VERDADEIRO                                 |
| Posição?                            | 2                                    |
| Valor Predefinido                        | nenhum                                 |
| Aceitar Entrada de Pipeline?               | falso                                |
| Aceitar Carateres Universais?          | falso                                |

### <a name="-configurationname-ltstringgt"></a>-ConfigurationName &lt;cadeia&gt;

Especifica o nome da configuração de sessão do Windows PowerShell, também conhecido como o ponto final ou o espaço de execução, para testar.

|||
|-|-|
| Aliases                              | nenhum                                 |
| Obrigatório?                            | falso                                |
| Posição?                            | 3                                    |
| Valor Predefinido                        | nenhum                                 |
| Aceitar Entrada de Pipeline?               | falso                                |
| Aceitar Carateres Universais?          | falso                                |

### <a name="-connectionuri-lturigt"></a>-ConnectionUri &lt;Uri&gt;

Especifica a ligação de URI para testar.

|||
|-|-|
| Aliases                              | nenhum                                 |
| Obrigatório?                            | VERDADEIRO                                 |
| Posição?                            | 2                                    |
| Valor Predefinido                        | nenhum                                 |
| Aceitar Entrada de Pipeline?               | falso                                |
| Aceitar Carateres Universais?          | falso                                |

### <a name="-credential-ltpscredentialgt"></a>-Credential &lt;PSCredential&gt;

Especifica um **PSCredential** objeto para uma conta de utilizador que pretende utilizar para testar as regras de autorização de acesso Web Windows PowerShell. Se não adicionar este parâmetro, o cmdlet utiliza a conta de utilizador atualmente com sessão iniciada. Para obter um **PSCredential** objeto, que é necessário para testar as regras de autorização remotamente, execute o [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.

|||
|-|-|
| Aliases                              | nenhum                                 |
| Obrigatório?                            | falso                                |
| Posição?                            | com o nome                                |
| Valor Predefinido                        | nenhum                                 |
| Aceitar Entrada de Pipeline?               | falso                                |
| Aceitar Carateres Universais?          | falso                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a>-Regras &lt;PswaAuthorizationRule\[\]&gt;

Especifica um subconjunto de regras para testar. Se este parâmetro não for especificado, este cmdlet testes relativamente a todas as regras de autorização.

|||
|-|-|
| Aliases                              | nenhum                                 |
| Obrigatório?                            | falso                                |
| Posição?                            | com o nome                                |
| Valor Predefinido                        | nenhum                                 |
| Aceitar Entrada de Pipeline?               | VERDADEIRO (ByValue)                       |
| Aceitar Carateres Universais?          | falso                                |

### <a name="-username-ltstringgt"></a>-UserName &lt;cadeia&gt;

Especifica o nome do utilizador para testar.

|||
|-|-|
| Aliases                              | nenhum                                 |
| Obrigatório?                            | VERDADEIRO                                 |
| Posição?                            | 1                                    |
| Valor Predefinido                        | nenhum                                 |
| Aceitar Entrada de Pipeline?               | falso                                |
| Aceitar Carateres Universais?          | falso                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Este cmdlet suporta os parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, e -OutVariable.
Para obter mais informações, consulte [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>ENTRADAS

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

Este cmdlet aceita uma matriz de objetos de PswaAuthorizationRule como entrada.

## <a name="outputs"></a>SAÍDAS

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

Este cmdlet produz uma matriz de objetos de PswaAuthorizationRule como saída.

## <a name="examples"></a>EXEMPLOS

### <a name="example-1"></a>EXEMPLO 1

Neste exemplo testa todas as regras de autorização para apresentar todas as regras que permitem ao utilizador *contoso\\mhanson* para ligar ao computador *srv2* e utilize uma sessão do Windows PowerShell configuração com o nome *testar*.

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a>EXEMPLO 2

Este testes de exemplo todas as regras de autorização para verificar as regras de autorização aplicam ao utilizador *contoso\\mhanson*.

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a>Tópicos relacionados

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)