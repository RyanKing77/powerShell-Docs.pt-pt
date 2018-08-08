---
title: Ciclo de Vida do Suporte do PowerShell Core
description: As políticas que regem suportam para o PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: 2e0ca1b9c133e6f316a40aff13365d0489059165
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587164"
---
# <a name="powershell-core-support-lifecycle"></a>Ciclo de Vida do Suporte do PowerShell Core

O PowerShell Core é um conjunto distinto de ferramentas e componentes que é entregue, instalado e configurado separadamente a partir do Windows PowerShell.
Por conseguinte, o PowerShell Core não está incluído nos contratos de licenciamento do Windows 7/8.1/10 ou Windows Server.

No entanto, o PowerShell Core é suportado por tradicionais contratos de suporte da Microsoft, incluindo [Premier][], [contratos Enterprise do Microsoft][enterprise-agreement]e [Microsoft Software Assurance][assurance].
Também pode pagar [o suporte assistido][] para o PowerShell Core através do preenchimento de um pedido de suporte para o seu problema.

Também oferecemos [suporte da Comunidade][] no GitHub onde pode enviar um problema, correção ou pedido de funcionalidade.
Em alternativa, pode encontrar a ajuda de outros membros da Comunidade sobre gerais [Microsoft Community][] ou o Microsoft [Comunidade tecnológica do PowerShell][].
Não oferecemos nenhuma garantia aí que o problema será resolvido ou resolvido em tempo hábil.
Se tiver um problema que requeira atenção imediata, deve usar o tradicional, opções de suporte pago.

## <a name="lifecycle-of-powershell-core"></a>Ciclo de vida do PowerShell Core

Está a adotar o PowerShell Core a [política de ciclo de vida moderno do Microsoft][modern].
Este ciclo de vida do suporte destina-se para manter os clientes atualizados com as versões mais recentes.

O ramo do 6.x de versão do PowerShell Core será atualizado aproximadamente uma vez a cada seis meses (por exemplo, 6.0, 6.1, 6.2, etc.)

> [!IMPORTANT]
> Tem de atualizar dentro de seis meses depois de cada nova versão secundária da versão para continuar a receber suporte.

Por exemplo, se o PowerShell Core 6.1 for lançado no dia 1 de Julho de 2018, esperada para atualizar para o PowerShell Core 6.1 até 1 de Janeiro de 2019 para manter o suporte.

![O ciclo de vida do PowerShell Core ramo][lifecycle-chart]

A política de ciclo de vida moderno também requer que Microsoft disponibilizar aos clientes aviso de 12 meses antes de interromper o suporte para um produto (ou seja, o PowerShell Core).

Por fim, podemos esperar o PowerShell Core irá adotar o "longo prazo de manutenção" abordagem em que é necessário apenas e manutenção de segurança de atualizações para manter o suporte numa filial/versão específica do 6.x.

## <a name="supported-platforms"></a>Plataformas suportadas

Consulte a tabela seguinte para ver qual plataforma a versão do PowerShell Core estiver a utilizar é oficialmente suportada.

Nossa Comunidade também contribuiu pacotes em algumas plataformas, mas não são suportadas oficialmente.
Esses pacotes são marcados como `Community` na tabela.

Plataformas listadas como `Experimental` não serem suportados oficialmente, mas estão disponíveis para a experimentação e comentários.

|                                                   | 6.0         | 6.1         |
|---------------------------------------------------|:-----------:|:-----------:|
| Windows 7, 8.1 e 10                            | Suportada   | Suportada   |
| Windows Server 2008 R2, 2012 R2, 2016             | Suportada   | Suportada   |
| [Canal Semianual do Windows Server][semi-annual] | Suportada   | Suportada   |
| Ubuntu 14.04 e 16.04                           | Suportada   | Suportada   |
| Ubuntu 18.04                                      |             | Suportada   |
| Ubuntu 18.10 (por meio do ajuste pacote)                   |             | Comunidade   |
| Debian 8,7 + e 9                                | Suportada   | Suportada   |
| CentOS 7                                          | Suportada   | Suportada   |
| Red Hat Enterprise Linux 7                        | Suportada   | Suportada   |
| OpenSUSE 42.3                                     | Suportada   | Suportada   |
| Fedora 27                                         | Suportada   | Suportada   |
| Fedora 28                                         |             | Suportada   |
| macOS 10.12 +                                      | Suportada   | Suportada   |
| Arch                                              | Comunidade   | Comunidade   |
| Raspbian                                          | Experimentais| Comunidade   |
| Kali                                              | Comunidade   | Comunidade   |
| AppImage (funciona em várias plataformas Linux)     | Comunidade   | Comunidade   |
| [Ajustar o pacote](https://snapcraft.io/powershell)   | Consulte a nota    | Consulte a nota    |

> [!NOTE]
> Ajuste pacotes estarão experimentais durante um período.  Depois, estamos a certeza de que Snap não introduz novos problemas de suporte, o suporte seguirão a distribuição que está a executar o pacote.

## <a name="platform-which-are-out-of-support"></a>Plataforma que estão fora de suporte

Quando uma versão de plataforma atinge o fim-de-vida conforme definido pelo proprietário de plataforma, o PowerShell Core também deixará de fornecer suporte para essa versão de plataforma. Já lançadas pacotes permanecerá disponíveis para clientes que precisam de acesso, mas suporte formal e atualizações de qualquer tipo já não serão fornecidas.

Por conseguinte, o suporte para as seguintes versões foi terminada pelos proprietários de distribuição e não são suportadas.

| SO       | Versão | Fim de vida                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| Fedora   | 24      | [Agosto de 2017](https://fedoramagazine.org/fedora-24-eol/)                                    |
| Fedora   | 25      | [Dezembro de 2017](https://fedoramagazine.org/fedora-25-end-life/)                             |
| Fedora   | 26      | [Maio de 2018](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| OpenSUSE | 42.1    | [Maio de 2017](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| OpenSUSE | 42.2    | [Janeiro de 2018](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| Ubuntu   | 16.10   | [Julho de 2017](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| Ubuntu   | 17.04   | [Janeiro de 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| Ubuntu   | 17.10   | [Julho de 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |

## <a name="notes-on-licensing"></a>Notas de licenciamento

O PowerShell Core é lançado sob o [licença MIT][].
Sob esta licença e, na ausência de um contrato de suporte pago, os utilizadores estão limitados a [suporte da Comunidade][].
Com o suporte da Comunidade, Microsoft não garante de capacidade de resposta ou correções.

## <a name="windows-powershell-module"></a>Módulo do Windows PowerShell

Suporte para o PowerShell Core não se estende para outros módulos de produto, a menos que esses módulos do PowerShell Core tem suporte explícito.
Por exemplo, utilizando o `ActiveDirectory` módulo que é fornecido como parte do Windows Server é um cenário não suportado.

No entanto, os módulos que não suportam explicitamente o PowerShell Core podem ser compatíveis em alguns casos.
Ao instalar o [ `WindowsPSModulePath` ][] módulo, pode acrescentar o Windows PowerShell `PSModulePath` para o PowerShell Core `PSModulePath`.

Primeiro, instale o `WindowsPSModulePath` módulo a partir da galeria do PowerShell:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

Depois de instalar este módulo, execute o `Add-WindowsPSModulePath` cmdlet para adicionar o Windows PowerShell `PSModulePath` para o PowerShell Core:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[suporte da Comunidade]: https://github.com/powershell/powershell/issues
[Microsoft Community]: https://answers.microsoft.com/
[Comunidade tecnológica do PowerShell]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[o suporte assistido]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[Licença MIT]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
['WindowsPSModulePath']: https://www.powershellgallery.com/packages/WindowsPSModulePath/
