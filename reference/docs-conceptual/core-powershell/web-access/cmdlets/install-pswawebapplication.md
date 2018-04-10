---
description: ''
ms.topic: article
ms.prod: powershell
keywords: PowerShell, o cmdlet
ms.date: 12/12/2016
title: instalar pswawebapplication
ms.technology: powershell
ms.openlocfilehash: c7f7768a41b6784d8c29afa1fccf0b855160b777
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="install-pswawebapplication"></a>Install-PswaWebApplication

## <a name="synopsis"></a>SYNOPSIS

Configura a aplicação web do Windows PowerShell® Web Access no IIS.

## <a name="syntax"></a>SYNTAX

### <a name="default"></a>Predefinido
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>DESCRIÇÃO

O **Install-PswaWebApplication** cmdlet configura aplicação web de acesso Web Windows PowerShell. Este cmdlet instala a aplicação web, associa-o com um web site e, opcionalmente, cria um teste SSL certificado, utilizando o **useTestCertificate** parâmetro. Segurança de administradores de web de motivos não devem utilizar um certificado de teste para ambientes de produção.

## <a name="parameters"></a>PARÂMETROS

### <a name="-usetestcertificate"></a>-UseTestCertificate

Especifica que é criado um certificado de teste. Se este parâmetro estiver definido como VERDADEIRO, então este cmdlet cria um certificado de teste e configura a aplicação web de acesso Web Windows PowerShell para utilizar o certificado para pedidos HTTPS. Se este parâmetro estiver definido como FALSO, não é criado nenhum certificado ou o enlace. Defina este valor como FALSO se outro certificado é utilizado para acesso Web Windows PowerShell.

|||
|-|-|
| Aliases                              | nenhum                                 |
| Obrigatório?                            | falso                                |
| Posição?                            | com o nome                                |
| Valor Predefinido                        | VERDADEIRO                                 |
| Aceitar Entrada de Pipeline?               | falso                                |
| Aceitar Carateres Universais?          | falso                                |

### <a name="-webapplicationnameltstringgt"></a>-WebApplicationName&lt;String&gt;

Especifica o nome da sua aplicação web. Isto é apresentado como a última parte do URL de acesso Web do Windows PowerShell.

|||
|-|-|
| Aliases                              | nenhum                                 |
| Obrigatório?                            | falso                                |
| Posição?                            | 1                                    |
| Valor Predefinido                        | pswa                                 |
| Aceitar Entrada de Pipeline?               | falso                                |
| Aceitar Carateres Universais?          | falso                                |

### <a name="-websitenameltstringgt"></a>-WebSiteName&lt;String&gt;

Especifica o nome do site do servidor Web (IIS) em que pretende instalar esta aplicação web do acesso Web Windows PowerShell.

|||
|-|-|
| Aliases                              | nenhum                                 |
| Obrigatório?                            | falso                                |
| Posição?                            | com o nome                                |
| Valor Predefinido                        | Web Site predefinido                     |
| Aceitar Entrada de Pipeline?               | falso                                |
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

Apresenta o que aconteceria mediante a execução do cmdlet.
O cmdlet não é executado.

|||
|-|-|
| Obrigatório?                            | falso                                |
| Posição?                            | com o nome                                |
| Valor Predefinido                        | falso                                |
| Aceitar Entrada de Pipeline?               | falso                                |
| Aceitar Carateres Universais?          | falso                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Este cmdlet suporta os parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, e -OutVariable.
Para obter mais informações, consulte [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>ENTRADAS

Este cmdlet não aceita nenhuma entrada.

## <a name="outputs"></a>SAÍDAS

Este cmdlet não produz nenhuma saída.

## <a name="examples"></a>EXEMPLOS

### <a name="example-1"></a>EXEMPLO 1

Este exemplo instala a aplicação de web PSWA utilizando os valores predefinidos para o **WebApplicationName** (*pswa*) e **WebSiteName** (*Default Web Site* ) parâmetros.

```
Install-PswaWebApplication
```

### <a name="example-2"></a>EXEMPLO 2

Este exemplo instala a aplicação de web PSWA com um certificado de teste e utilizando os valores predefinidos para o **WebApplicationName** e **WebSiteName** parâmetros.

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a>Tópicos relacionados

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)