---
title: Ciclo de Vida do Suporte do PowerShell Core
description: As políticas que regem suportam para o PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: 178e5c43520f9a392ca219b9f785eb18b1ec5436
ms.sourcegitcommit: f268dce5b5e72be669be0c6634b8db11369bbae2
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/29/2019
ms.locfileid: "58623863"
---
# <a name="powershell-core-support-lifecycle"></a>Ciclo de Vida do Suporte do PowerShell Core

O PowerShell Core é um conjunto distinto de ferramentas e componentes que é entregue, instalado e configurado separadamente a partir do Windows PowerShell.
Então, o PowerShell Core não está incluído nos contratos de licenciamento do Windows 7/8.1/10 ou Windows Server.

No entanto, o PowerShell Core é suportado por tradicionais contratos de suporte da Microsoft, incluindo [Premier][], [contratos Enterprise do Microsoft][enterprise-agreement]e [Microsoft Software Assurance][assurance].
Também pode pagar [o suporte assistido][] para o PowerShell Core através do preenchimento de um pedido de suporte para o seu problema.

## <a name="community-support"></a>Suporte da Comunidade

Também oferecemos [suporte da Comunidade][] no GitHub onde pode enviar um problema, correção ou pedido de funcionalidade.
Além disso, pode encontrar a ajuda de outros membros da Comunidade sobre gerais [Microsoft Community][] ou o Microsoft [Comunidade tecnológica do PowerShell][].
Não oferecemos nenhuma garantia aí que a Comunidade irá abordar ou resolver o problema em tempo hábil.
Se tiver um problema que requeira atenção imediata, deve usar o tradicional, opções de suporte pago.

## <a name="lifecycle-of-powershell-core"></a>Ciclo de vida do PowerShell Core

Está a adotar o PowerShell Core a [política de ciclo de vida moderno do Microsoft][modern].
Este ciclo de vida do suporte destina-se para manter os clientes atualizados com as versões mais recentes.

O ramo do 6.x de versão do PowerShell Core será atualizado aproximadamente uma vez a cada seis meses (exemplos: 6.0, 6.1, 6.2, etc.)

> [!IMPORTANT]
> Tem de atualizar dentro de seis meses depois de cada nova versão secundária da versão para continuar a receber suporte.

Por exemplo, se o PowerShell Core 6.1 for lançado no dia 1 de Julho de 2018, esperada para atualizar para o PowerShell Core 6.1 até 1 de Janeiro de 2019 para manter o suporte.

> [!IMPORTANT]
> Tem de atualizar dentro de 30 dias após cada nova versão de patch de versão para continuar a receber suporte.

Por exemplo, se estiver a executar o PowerShell Core 6.1 e 6.1.3 foi lançado no dia 19 de Fevereiro de 2019, esperada para atualizar para o PowerShell Core 6.1.3 até 21 de Março de 2019, que é 30 dias após o lançamento para manter o suporte.
Se quaisquer correções são necessárias, as correções serão lançadas em nossa próxima atualização cumulativa.

![O ciclo de vida do PowerShell Core ramo][lifecycle-chart]

A política de ciclo de vida moderno também requer que Microsoft disponibilizar aos clientes aviso de 12 meses antes de interromper o suporte para um produto (ou seja, o PowerShell Core).

Por fim, podemos esperar o PowerShell Core irá adotar o "longo prazo de manutenção" abordagem.
Nesta abordagem de manutenção, vamos exigiria apenas de manutenção e atualizações de segurança para se manter em suporte numa filial/versão específica do 6.x.

## <a name="supported-platforms"></a>Plataformas suportadas

A tabela seguinte para ver qual plataforma a versão do PowerShell Core estiver a utilizar é oficialmente suportada.

Nossa Comunidade também contribuiu pacotes em algumas plataformas, mas não são suportadas oficialmente.
Esses pacotes são marcados como `Community` na tabela.

Plataformas listadas como `Experimental` não serem suportados oficialmente, mas estão disponíveis para a experimentação e comentários.

|                                                   | 6.1         | 6.2         |
|---------------------------------------------------|:-----------:|:-----------:|
| Windows 7, 8.1 e 10                            | Suportado   | Suportado   |
| Windows Server 2008 R2, 2012 R2, 2016             | Suportado   | Suportado   |
| [Canal Semianual do Windows Server][semi-annual] | Suportado   | Suportado   |
| Ubuntu 16.04 e 18.04                            | Suportado   | Suportado   |
| Ubuntu 18.10 (por meio do ajuste pacote)                   | Comunidade   | Comunidade   |
| Debian 9                                          | Suportado   | Suportado   |
| CentOS 7                                          | Suportado   | Suportado   |
| Red Hat Enterprise Linux 7                        | Suportado   | Suportado   |
| openSUSE 42.3                                     | Suportado   | Suportado   |
| Fedora 28                                         | Suportado   | Suportado   |
| macOS 10.12+                                      | Suportado   | Suportado   |
| Arch                                              | Comunidade   | Comunidade   |
| Raspbian                                          | Comunidade   | Comunidade   |
| Kali                                              | Comunidade   | Comunidade   |
| AppImage (funciona em várias plataformas Linux)     | Comunidade   | Comunidade   |
| [Ajustar o pacote](https://snapcraft.io/powershell)   | Consulte a nota    | Consulte a nota    |

> [!NOTE]
> Ajustar os pacotes são suportados o mesmo que a distribuição estiver a executar o pacote no.

## <a name="powershell-release-end-of-life"></a>PowerShell versão final de vida

Com base na [ciclo de vida do PowerShell Core](#lifecycle-of-powershell-core), a tabela seguinte lista as datas de lançamento vários quando já não será suportado.

| Versão | Fim de vida                   |
|---------|-------------------------------|
| 6.0     | 13 de Fevereiro de 2019             |
| 6.1     | 28 de Setembro de 2019            |
| 6.2     | versões de seis meses a 6.3   |

## <a name="platforms-which-are-out-of-support"></a>Plataformas, que estão fora de suporte

Quando uma versão de plataforma atinge o final da vida, conforme definido pelo proprietário de plataforma, o PowerShell Core também deixará de suportar essa versão de plataforma.
Já lançadas pacotes permanecerá disponíveis para clientes que precisam de acesso, mas suporte formal e atualizações de qualquer tipo já não serão fornecidas.

Então, os proprietários de distribuição terminou o suporte para as seguintes versões e não são suportados.

| SO       | Versão | Fim de vida                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| Fedora   | 24      | [Agosto de 2017](https://fedoramagazine.org/fedora-24-eol/)                                    |
| Fedora   | 25      | [Dezembro de 2017](https://fedoramagazine.org/fedora-25-end-life/)                             |
| Fedora   | 26      | [Maio de 2018](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| openSUSE | 42.1    | [Maio de 2017](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| openSUSE | 42.2    | [Janeiro de 2018](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| Ubuntu   | 16.10   | [Julho de 2017](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| Ubuntu   | 17.04   | [Janeiro de 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| Ubuntu   | 17.10   | [Julho de 2018](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| Debian   | 8       | [Junho de 2018](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| Fedora   | 27      | [Novembro de 2018](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| Ubuntu   | 14.04   | [Abril de 2019](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a>Notas de licenciamento

O PowerShell Core é lançado sob o [licença MIT][].
Sob esta licença e sem um contrato de suporte pago, os utilizadores estão limitados a [suporte da Comunidade][].
Com o suporte da Comunidade, Microsoft não garante de capacidade de resposta ou correções.

## <a name="windows-powershell-module"></a>Módulo do Windows PowerShell

Suporte para o PowerShell Core não inclui módulos do produto, a menos que esses módulos do PowerShell Core tem suporte explícito.
Por exemplo, utilizando o `ActiveDirectory` módulo que é fornecido como parte do Windows Server é um cenário não suportado.

No entanto, os módulos que não suportam explicitamente o PowerShell Core podem ser compatíveis em alguns casos.
Ao instalar o [ `WindowsPSModulePath` ][] módulo, pode adicionar o Windows PowerShell `PSModulePath` para o PowerShell Core `PSModulePath`.

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

## <a name="experimental-features"></a>Funcionalidades experimentais

[Funcionalidades experimentais][] estão limitados a [suporte da Comunidade](#community-support).

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[Suporte da Comunidade]: https://github.com/powershell/powershell/issues
[Microsoft Community]: https://answers.microsoft.com/
[Comunidade tecnológica do PowerShell]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[o suporte assistido]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[Licença MIT]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[Funcionalidades experimentais]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
