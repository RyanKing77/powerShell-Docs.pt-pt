---
ms.topic: reference
keywords: PowerShell, o cmdlet
ms.date: 12/12/2016
title: Remove-PswaAuthorizationRule
ms.openlocfilehash: 6a3720bb9b8df3e1c6bb9f4a6196c9868b85b67d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
---
# <a name="remove-pswaauthorizationrule"></a>Remove-PswaAuthorizationRule

## <a name="synopsis"></a>RESUMO

Remove uma regra de autorização especificada do Windows PowerShell® Web Access.

## <a name="syntax"></a>SINTAXE

### <a name="id"></a>Id
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a>Regra
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>DESCRIÇÃO

Remove uma regra de autorização especificada do acesso Web Windows PowerShell.

## <a name="parameters"></a>PARÂMETROS

### <a name="-force"></a>-Force

Executa o cmdlet sem pedir confirmação. Por predefinição, o cmdlet pede-lhe confirmação antes de continuar.

|||
|-|-|
| Aliases                              | nenhum                                 |
| Obrigatório?                            | falso                                |
| Posição?                            | com o nome                                |
| Valor Predefinido                        | nenhum                                 |
| Aceitar Entrada de Pipeline?               | falso                                |
| Aceitar Carateres Universais?          | falso                                |

### <a name="-id-ltint32gt"></a>-Id &lt;Int32\[\]&gt;

Especifica os identificadores (IDs) de uma ou mais regras para remover.

|||
|-|-|
| Aliases                              | nenhum                                 |
| Obrigatório?                            | VERDADEIRO                                 |
| Posição?                            | 2                                    |
| Valor Predefinido                        | nenhum                                 |
| Aceitar Entrada de Pipeline?               | VERDADEIRO (ByValue, ByPropertyName)       |
| Aceitar Carateres Universais?          | falso                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a>-Regras &lt;PswaAuthorizationRule\[\]&gt;

Especifica regras para remover.

|||
|-|-|
| Aliases                              | nenhum                                 |
| Obrigatório?                            | VERDADEIRO                                 |
| Posição?                            | 2                                    |
| Valor Predefinido                        | nenhum                                 |
| Aceitar Entrada de Pipeline?               | VERDADEIRO (ByValue)                       |
| Aceitar Carateres Universais?          | falso                                |

### <a name="-confirm"></a>-Confirm

Solicita a sua confirmação antes de executar o cmdlet.

|||
|-|-|
| Obrigatório?                            | falso                                |
| Posição?                            | com o nome                                |
| Valor Predefinido                        | falso                                |
| Aceitar Entrada de Pipeline?               | falso                                |
| Aceitar Carateres Universais?          | falso                                |

### <a name="-whatif"></a>-WhatIf

Apresenta o que aconteceria mediante a execução do cmdlet. O cmdlet não é executado.

|||
|-|-|
| Obrigatório?                            | falso                                |
| Posição?                            | com o nome                                |
| Valor Predefinido                        | falso                                |
| Aceitar Entrada de Pipeline?               | falso                                |
| Aceitar Carateres Universais?          | falso                                |

### <a name="ltcommonparametersgt"></a>&lt;Parâmetroscomuns&gt;

Este cmdlet suporta os parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, e -OutVariable.
Para obter mais informações, consulte [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>ENTRADAS

### <a name="int"></a>Int\[\]

Este cmdlet aceita uma matriz de números inteiros ou uma matriz de objetos de PswaAuthorizationRule.

### <a name="pswaauthorizationrule"></a>PswaAuthorizationRule\[\]

Este cmdlet aceita uma matriz de números inteiros ou uma matriz de objetos de PswaAuthorizationRule.

## <a name="outputs"></a>SAÍDAS

Este cmdlet não produz nenhuma saída.

## <a name="examples"></a>EXEMPLOS

### <a name="example-1"></a>EXEMPLO 1

Neste exemplo remove a regra de autorização com o ID de *2*.

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a>EXEMPLO 2 {.subHeading #example-2}

Neste exemplo remove todas as regras de autorização e é também necessária confirmação pelo utilizador.

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a>Tópicos relacionados

- [Adicionar-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)