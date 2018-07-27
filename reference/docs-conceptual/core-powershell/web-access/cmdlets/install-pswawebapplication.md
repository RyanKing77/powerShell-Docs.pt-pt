---
ms.topic: reference
keywords: PowerShell, o cmdlet
ms.date: 12/12/2016
title: Install-PswaWebApplication
ms.openlocfilehash: 29e074b75eeb387640831229c63142e6dd5e991a
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268304"
---
# <a name="install-pswawebapplication"></a>Install-PswaWebApplication

## <a name="synopsis"></a>SINOPSE

Configura o aplicativo web do Windows PowerShell Web Access no IIS.

## <a name="syntax"></a>SINTAXE

### <a name="default"></a>Predefinido
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>DESCRIÇÃO

O **Install-PswaWebApplication** cmdlet configura o aplicativo de web do Windows PowerShell Web Access.
Este cmdlet instala a aplicação web, associa-à um web site e, opcionalmente, cria um teste SSL certificado com o **useTestCertificate** parâmetro. Segurança de administradores da web motivos não devem utilizar um certificado de teste para ambientes de produção.

## <a name="parameters"></a>PARÂMETROS

### <a name="-usetestcertificate"></a>-UseTestCertificate

Especifica que um certificado de teste é criado. Se este parâmetro estiver definido como true, em seguida, este cmdlet cria um certificado de teste e configura o aplicativo web do Windows PowerShell Web Access para utilizar o certificado para pedidos HTTPS. Se este parâmetro estiver definido como false, não é criada nenhum certificado ou a ligação. Defina este valor como FALSO se outro certificado é utilizado para o Windows PowerShell Web Access.

|||
|-|-|
| Aliases                              | nenhum                                 |
| Obrigatório?                            | falso                                |
| Posição?                            | com o nome                                |
| Valor Predefinido                        | VERDADEIRO                                 |
| Aceitar Entrada de Pipeline?               | falso                                |
| Aceitar Carateres Universais?          | falso                                |

### <a name="-webapplicationname"></a>-WebApplicationName

Especifica o nome da sua aplicação web. É apresentado como a última parte do URL do Windows PowerShell Web Access.

|||
|-|-|
| Aliases                              | nenhum                                 |
| Obrigatório?                            | falso                                |
| Posição?                            | 1                                    |
| Valor Predefinido                        | pswa                                 |
| Aceitar Entrada de Pipeline?               | falso                                |
| Aceitar Carateres Universais?          | falso                                |

### <a name="-websitename"></a>-WebSiteName

Especifica o nome do site do servidor Web (IIS) em que pretende instalar esta aplicação web do Windows PowerShell Web Access.

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

Este cmdlet suporta os parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, e -OutVariable. Para obter mais informações, consulte [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>ENTRADAS

Este cmdlet não precisa de entrada.

## <a name="outputs"></a>SAÍDAS

Este cmdlet não produz nenhuma saída.

## <a name="examples"></a>EXEMPLOS

### <a name="example-1"></a>EXEMPLO 1

Este exemplo instala a aplicação de web PSWA utilizando os valores predefinidos para o **WebApplicationName** (*pswa*) e **WebSiteName** (*Web Site predefinido* ) parâmetros.

```
Install-PswaWebApplication
```

### <a name="example-2"></a>EXEMPLO 2

Este exemplo instala o aplicativo da web PSWA com um certificado de teste e utilizar os valores predefinidos para o **WebApplicationName** e **WebSiteName** parâmetros.

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a>Tópicos relacionados

- [Adicionar-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)