---
ms.topic: reference
keywords: PowerShell, o cmdlet
ms.date: 12/12/2016
title: Desinstalar-PswaWebApplication
ms.openlocfilehash: b2a3e4d584fd04ee49e1e6408dba39fd8bc555dc
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221923"
---
# <a name="uninstall-pswawebapplication"></a>Desinstalar-PswaWebApplication

## <a name="synopsis"></a>RESUMO

Desinstala a aplicação de web Windows PowerShell®.

## <a name="syntax"></a>SINTAXE

### <a name="default"></a>Predefinido
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>DESCRIÇÃO

O **Uninstall-PswaWebApplication** cmdlet desinstala a aplicação web do Windows PowerShell e remove o Web site do IIS. O cmdlet não desinstala IIS nem outras funcionalidades instaladas porque estavam necessárias para o Windows PowerShell executar.

## <a name="parameters"></a>PARÂMETROS

### <a name="-deletetestcertificate"></a>-DeleteTestCertificate

Indica que os certificados de teste criado o **instalar\_PswaWebApplication** cmdlet (com o **UseTestCertificate** parâmetro) é eliminado.
Apenas o certificado de teste com o mesmo nome que criados pelo **Install-PswaWebApplication** cmdlet é removido.

|||
|-|-|
| Aliases                              | nenhum                                 |
| Obrigatório?                            | falso                                |
| Posição?                            | com o nome                                |
| Valor Predefinido                        | VERDADEIRO                                 |
| Aceitar Entrada de Pipeline?               | falso                                |
| Aceitar Carateres Universais?          | falso                                |

### <a name="-webapplicationname-ltstringgt"></a>-WebApplicationName &lt;cadeia&gt;

Especifica o nome da aplicação web para desinstalar.

|||
|-|-|
| Aliases                              | nenhum                                 |
| Obrigatório?                            | falso                                |
| Posição?                            | 1                                    |
| Valor Predefinido                        | pswa                                 |
| Aceitar Entrada de Pipeline?               | falso                                |
| Aceitar Carateres Universais?          | falso                                |

### <a name="-websitename-ltstringgt"></a>-WebSiteName &lt;cadeia&gt;

Especifica o nome do web site onde a aplicação web está instalada.

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

### <a name="ltcommonparametersgt"></a>&lt;Parâmetroscomuns&gt;

Este cmdlet suporta os parâmetros comuns: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, e -OutVariable.
Para obter mais informações, consulte [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>ENTRADAS

Este cmdlet não aceita nenhuma entrada.

## <a name="outputs"></a>SAÍDAS

Este cmdlet não devolve nenhum resultado.

## <a name="examples"></a>EXEMPLOS

### <a name="example-1"></a>EXEMPLO 1

Este comando desinstala a aplicação de Web do Windows PowerShell.
Pode utilizar este cmdlet para desinstalar a aplicação de Web do Windows PowerShell, se tiver instalado, utilizando os valores predefinidos.

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a>EXEMPLO 2

Este comando desinstala a aplicação de Web do Windows PowerShell e elimina o certificado de teste associado à aplicação.
Pode utilizar este cmdlet para desinstalar a aplicação de Web do Windows PowerShell, se instalou utilizando os valores predefinidos e criar um certificado de teste.

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a>EXEMPLO 3 {#example-3 .subHeading}

Este comando desinstala a aplicação do Windows PowerShell Web quando um Web site personalizado e aplicação foram especificadas durante a instalação.
O comando remove o Web site com o nome *MySite* e a aplicação com o nome *TestApplication* e especifica que os certificados de teste associados à aplicação também são eliminados.

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

## <a name="related-topics"></a>Tópicos relacionados

- [Adicionar-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)