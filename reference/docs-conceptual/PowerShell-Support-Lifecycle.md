---
title: Ciclo de Vida do Suporte do PowerShell Core
description: Políticas que regem o suporte para o PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: 60999ed54ca3be15232ffee3ab0c49cb94873a8f
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986740"
---
# <a name="powershell-core-support-lifecycle"></a>Ciclo de Vida do Suporte do PowerShell Core

O PowerShell Core é um conjunto distinto de ferramentas e componentes que são fornecidos, instalados e configurados separadamente do Windows PowerShell. Portanto, o PowerShell Core não está incluído nos contratos de licenciamento do Windows 7/8.1/10 ou do Windows Server.

No entanto, o PowerShell Core tem suporte em contratos de suporte tradicionais da Microsoft, incluindo [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement]e [Microsoft Software Assurance][assurance].
Você também pode pagar pelo [suporte assistido][] do PowerShell Core ao arquivar uma solicitação de suporte para seu problema.

## <a name="community-support"></a>Suporte da Comunidade

Também oferecemos [suporte da Comunidade][] no GitHub, onde você pode arquivar um problema, bug ou solicitação de recurso.
Além disso, você pode encontrar ajuda de outros membros da Comunidade na comunidade geral da [Comunidade da Microsoft][] ou na [Comunidade de tecnologia do PowerShell][]do Microsoft PowerShell. Não oferecemos nenhuma garantia de que a Comunidade irá abordar ou resolver seu problema em tempo hábil. Se você tiver um problema que exija atenção imediata, deverá usar as opções de suporte tradicionais e pagas.

## <a name="lifecycle-of-powershell-core"></a>Ciclo de vida do PowerShell Core

O PowerShell Core está adotando a [política de ciclo de vida moderno da Microsoft][modern]. Esse ciclo de vida de suporte destina-se a manter os clientes atualizados com as versões mais recentes.

A ramificação da versão 6. x do PowerShell Core será atualizada aproximadamente uma vez a cada seis meses (exemplos: 6,0, 6,1, 6,2, etc.)

> [!IMPORTANT]
> Você deve atualizar dentro de seis meses após cada nova versão secundária para continuar recebendo suporte.

Por exemplo, se o PowerShell Core 6,1 for lançado em 1º de julho de 2018, você deverá atualizar para o PowerShell Core 6,1 até 1º de janeiro de 2019 para manter o suporte.

> [!IMPORTANT]
> Você deve atualizar dentro de 30 dias após a liberação de cada nova versão de patch para continuar recebendo suporte.

Por exemplo, se você estiver executando o PowerShell Core 6,1 e o 6.1.3 foi lançado em 19 de fevereiro de 2019, espera-se que você atualize para o PowerShell Core 6.1.3 até 21 de março de 2019, que é 30 dias após o lançamento para manter o suporte. Se forem encontradas correções para serem necessárias, as correções serão lançadas em nossa próxima atualização cumulativa.

A política moderna de ciclo de vida também exige que a Microsoft forneça aos clientes 12 meses de aviso antes de interromper o suporte para um produto (ou seja, PowerShell Core).

Eventualmente, esperamos que o PowerShell Core Adote a abordagem de manutenção em longo prazo. Nessa abordagem de manutenção, exigimos que apenas atualizações de serviço e de segurança permaneçam em suporte em um Branch/versão específica do 6. x.

## <a name="supported-platforms"></a>Plataformas suportadas

Para confirmar se a plataforma e a versão do PowerShell Core são oficialmente suportadas, consulte a tabela a seguir.

Nossa comunidade também contribuiu com pacotes para algumas plataformas, mas elas não têm suporte oficial. Esses pacotes são marcados como `Community` na tabela.

As plataformas listadas como `Experimental` não são oficialmente suportadas, mas estão disponíveis para experimentação e comentários.

| Plataforma                                          | 6.1         | 6.2         |
|---------------------------------------------------|:-----------:|:-----------:|
| Windows 7, 8,1 e 10                            | Suportado   | Suportado   |
| Windows Server 2008 R2, 2012 R2, 2016             | Suportado   | Suportado   |
| [Canal semestral do Windows Server][semi-annual] | Suportado   | Suportado   |
| Ubuntu 16, 4 e 18, 4                            | Suportado   | Suportado   |
| Ubuntu 18,10 (via pacote de snap)                   | Comunidade   | Comunidade   |
| Ubuntu 19, 4 (via pacote de snap)                   | Comunidade   | Comunidade   |
| Debian 9                                          | Suportado   | Suportado   |
| CentOS 7                                          | Suportado   | Suportado   |
| Red Hat Enterprise Linux 7                        | Suportado   | Suportado   |
| openSUSE 42,3                                     | Suportado   | Suportado   |
| Fedora 28                                         | Suportado   | Suportado   |
| macOS 10.12 +                                      | Suportado   | Suportado   |
| Arquea                                              | Comunidade   | Comunidade   |
| Raspbian                                          | Comunidade   | Comunidade   |
| Kali                                              | Comunidade   | Comunidade   |
| AppImage (funciona em várias plataformas Linux)      | Comunidade   | Comunidade   |
| [Ajustar pacote](https://snapcraft.io/powershell)   | Consulte a observação    | Consulte a observação    |

> [!NOTE]
> Pacotes snap têm suporte da mesma forma que a distribuição em que você está executando o pacote.

## <a name="powershell-releases-end-of-life"></a>Fim da vida útil dos lançamentos do PowerShell

Com base no [ciclo de vida do PowerShell Core](#lifecycle-of-powershell-core), a tabela a seguir lista as datas em que não haverá mais suporte para várias versões.

| Versão | Fim da vida útil                   |
|---------|-------------------------------|
| 6.0     | 13 de fevereiro de 2019             |
| 6.1     | 28 de setembro de 2019            |
| 6.2     | 6 meses após 7 versões     |

## <a name="unsupported-platforms"></a>Plataformas sem suporte

Quando uma versão de plataforma atinge o fim da vida útil conforme definido pelo proprietário da plataforma, o PowerShell Core também cessará para oferecer suporte a essa versão da plataforma. Os pacotes lançados anteriormente permanecerão disponíveis para clientes que precisam de acesso, mas suporte formal e atualizações de qualquer tipo não serão mais fornecidos.

Portanto, os proprietários de distribuição terminaram o suporte para as seguintes versões e não têm suporte.

| Plataforma | Versão | Fim da vida útil                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| Fedora   | 24      | [Agosto de 2017](https://fedoramagazine.org/fedora-24-eol/)                                    |
| Fedora   | 25      | [Dezembro de 2017](https://fedoramagazine.org/fedora-25-end-life/)                             |
| Fedora   | 26      | [Maio de 2018](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| openSUSE | 42.1    | [Maio de 2017](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| openSUSE | 42,2    | [Janeiro de 2018](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| Ubuntu   | 16,10   | [Julho de 2017](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| Ubuntu   | 17, 4   | [Janeiro de 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| Ubuntu   | 17,10   | [Julho de 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| Debian   | 8       | [Junho de 2018](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| Fedora   | 27      | [Novembro de 2018](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| Ubuntu   | 14.04   | [Abril de 2019](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a>Observações sobre o licenciamento

O PowerShell Core é lançado sob a [licença MIT][]. Sob essa licença e sem um contrato de suporte pago, os usuários são limitados ao [suporte da Comunidade][]. Com o suporte da Comunidade, a Microsoft não oferece nenhuma garantia de capacidade de resposta ou correções.

## <a name="windows-powershell-module"></a>Módulo do Windows PowerShell

O suporte para PowerShell Core não inclui módulos de produto, a menos que esses módulos ofereçam suporte explícito ao PowerShell Core. Por exemplo, o uso `ActiveDirectory` do módulo que é fornecido como parte do Windows Server é um cenário sem suporte.

No entanto, os módulos que não oferecem suporte explícito ao PowerShell Core podem ser compatíveis em alguns casos. Ao instalar o [`WindowsPSModulePath`][] módulo, você pode adicionar o Windows PowerShell `PSModulePath` ao seu núcleo `PSModulePath`do PowerShell.

Primeiro, instale o `WindowsPSModulePath` módulo do Galeria do PowerShell:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

Depois de instalar este módulo, execute `Add-WindowsPSModulePath` o cmdlet para adicionar o Windows `PSModulePath` PowerShell ao PowerShell Core:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="experimental-features"></a>Recursos experimentais

Os [recursos experimentais][] são limitados ao [suporte da Comunidade](#community-support).

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[suporte da Comunidade]: https://github.com/powershell/powershell/issues
[Comunidade da Microsoft]: https://answers.microsoft.com/
[Comunidade de tecnologia do PowerShell]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[suporte assistido]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[Licença MIT]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
['WindowsPSModulePath']: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[Recursos experimentais]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
