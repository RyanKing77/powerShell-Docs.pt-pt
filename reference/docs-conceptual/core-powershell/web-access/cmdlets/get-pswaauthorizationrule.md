---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, o cmdlet
ms.date: 2016-12-12
title: obter pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: eb9f42ab4d9cec111e03a096b2f00740e97ee1b7
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/08/2017
---
# <a name="get-pswaauthorizationrule"></a>Get-PswaAuthorizationRule

## <a name="synopsis"></a>RESUMO

Devolve um conjunto de regras de autorização de acesso de Web do Windows PowerShell®.

## <a name="syntax"></a>Sintaxe

### <a name="id"></a>ID
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

### <a name="name"></a>Nome
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a>DESCRIÇÃO

O **Get-PswaAuthorizationRule** cmdlet devolve um conjunto de regras de autorização de acesso de Web do Windows PowerShell®.
Se nem o **Id** parâmetro nem o **RuleName** parâmetro for especificado, em seguida, este cmdlet apresenta uma lista de todas as regras. O **Id** parâmetro pode ser utilizado para filtrar os resultados.

## <a name="parameters"></a>PARÂMETROS

### <a name="-idltint32gt"></a>-Id&lt;Int32\[\]&gt;

Especifica os identificadores (IDs), as regras que deve receber este cmdlet. Se não existem IDs forem especificados, este cmdlet devolve todas as regras de autorização.

|||  
|-|-|
| Aliases                              | nenhum                                 |
| Obrigatório?                            | falso                                |
| Posição?                            | 2                                    |
| Valor Predefinido                        | nenhum                                 |
| Aceitar Entrada de Pipeline?               | VERDADEIRO (ByValue, ByPropertyName)       |
| Aceitar Carateres Universais?          | falso                                |

### <a name="-rulenameltstringgt"></a>-RuleName&lt;cadeia\[\]&gt;

Especifica os nomes das regras de autorização para obter. Este parâmetro devolve quaisquer regras que correspondem exatamente os nomes de regra de cadeias nesta matriz.

|||  
|-|-|
| Aliases                              | nenhum                                 |
| Obrigatório?                            | VERDADEIRO                                 |
| Posição?                            | 2                                    |
| Valor Predefinido                        | nenhum                                 |
| Aceitar Entrada de Pipeline?               | VERDADEIRO (ByValue, ByPropertyName)       |
| Aceitar Carateres Universais?          | falso                                |

### <a name="ltcommonparametersgt"></a>&lt;Parâmetroscomuns&gt;

Este cmdlet suporta os parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, e -OutVariable.
Para obter mais informações, consulte [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>ENTRADAS

### <a name="int"></a>Int\[\]

Este cmdlet aceita uma matriz de números inteiros ou uma matriz de valores de cadeia como entrada.

### <a name="string"></a>Cadeia\[\]

Este cmdlet aceita uma matriz de números inteiros ou uma matriz de valores de cadeia como entrada.

## <a name="outputs"></a>SAÍDAS

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

Este cmdlet produz um objeto de PswaAuthorizationRule como saída.


## <a name="examples"></a>EXEMPLOS

### <a name="example-1"></a>EXEMPLO 1

Neste exemplo obtém todas as regras.

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a>EXEMPLO 2

Neste exemplo obtém uma regra com um ID de *2*.

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a>EXEMPLO 3 {#example-3 .subHeading}

Este exemplo ilustra como o cmdlet aceita um valor do pipeline.
Um id de regra e um nome de regra são transmitidos este cmdlet.

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

## <a name="related-topics"></a>Tópicos relacionados

- [Adicionar-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Teste-PswaAuthorizationRule](test-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
