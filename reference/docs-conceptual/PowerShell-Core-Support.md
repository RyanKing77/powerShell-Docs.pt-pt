# <a name="powershell-core-support-lifecycle"></a>Ciclo de vida de suporte de núcleos de PowerShell

Núcleo do PowerShell é um conjunto diferente de ferramentas e componentes que é enviada, instalado e configurado separadamente a partir do Windows PowerShell.
Por conseguinte, o PowerShell Core não está incluído nos contratos de licenciamento do Windows 7/8.1/10 ou Windows Server.

No entanto, o PowerShell Core é suportado em tradicionais contratos de suporte da Microsoft, incluindo [Premier][], [contratos do Microsoft Enterprise][enterprise-agreement]e [Microsoft Software Assurance][assurance].
Também pode paga [assistido suporte][] para PowerShell Core através da apresentação de um pedido de suporte para o seu problema.

Podemos também oferecem [suporte da Comunidade][] no GitHub, onde pode ficheiro um problema, erros ou pedido de funcionalidade.
Em alternativa, pode encontrar ajuda dos outros membros da Comunidade a gerais [Microsoft Community][] ou o Microsoft [PowerShell técnico Comunidade][].
Que não oferecemos nenhuma garantia de existir se o problema será resolvido ou resolvido de forma atempada.
Se tiver um problema que necessite de atenção imediata, deve utilizar tradicional, paga as opções de suporte.

## <a name="lifecycle-of-powershell-core"></a>Ciclo de vida de núcleos de PowerShell

Núcleos de PowerShell está a adotar o [política de ciclo de vida moderna Microsoft][modern].
Este ciclo de vida do suporte destina-se para manter clientes atualizados com as versões mais recentes.

O ramo de 6. x da versão do PowerShell Core será atualizado, aproximadamente, uma vez a cada seis meses (por exemplo, 6.0, 6.1, 6.2, etc.)

> [!IMPORTANT]
> Tem de atualizar dentro de seis meses após cada versão secundária nova versão para continuar a receber suporte.

Por exemplo, se PowerShell Core 6.1 é libertada, 1 de Julho de 2018, seria esperado para atualizar para o PowerShell Core 6.1 1 de Janeiro de 2019 para manter o suporte.

![Ciclo de vida do PowerShell Core sucursal][lifecycle-chart]

A política de ciclo de vida moderna também requer que Microsoft dar clientes aviso de 12 meses antes discontinuing suporte para um produto (ou seja, o PowerShell Core).

Eventualmente, esperamos PowerShell Core irá adotar a "longo prazo manutenção" abordagem onde é necessário apenas e atualização de segurança de atualizações para se manter no suporte de uma sucursal/versão específica do 6. x.

## <a name="supported-platforms"></a>Plataformas suportadas

PowerShell Core oficialmente é suportada nas seguintes plataformas:

* Windows 7, 8.1 e 10
* Windows Server 2008 R2, 2012 R2, 2016
* [Canal de ponto e anual do Windows Server][semi-annual]
* Ubuntu 14.04, 16.04 e 17.04
* Debian 8.7 + e 9
* CentOS 7
* Red Hat Enterprise Linux 7
* OpenSUSE 42.2
* Fedora 25, 26
* macOS 10.12 +

A nossa Comunidade também tem contribuíram pacotes para as seguintes plataformas, mas não estão oficialmente suppported:

* Arquitetura de Linux
* Kali Linux
* AppImage (funciona em várias plataformas Linux)

## <a name="notes-on-licensing"></a>Notas sobre o licenciamento

PowerShell Core for lançada sob o [licença MIT][].
Com esta licença e, na ausência de um contrato de suporte pago, os utilizadores estão limitados a [suporte da Comunidade][].
Com o suporte da Comunidade, Microsoft torna sem garantias de capacidade de resposta ou as correções.

## <a name="windows-powershell-module"></a>Módulo do Windows PowerShell

Suporte para o PowerShell Core se estendem aos outros módulos de produto, a menos que esses módulos explicitamente suportam PowerShell Core.
Por exemplo, utilizando o `ActiveDirectory` módulo que é fornecido como parte do Windows Server é um cenário não suportado.

No entanto, os módulos que não suportam explicitamente PowerShell Core podem ser compatíveis em alguns casos.
Ao instalar o [`WindowsPSModulePath`][] módulo, pode acrescentar o Windows PowerShell `PSModulePath` para o PowerShell Core `PSModulePath`.

Em primeiro lugar, instalar o `WindowsPSModulePath` módulo a partir da galeria do PowerShell:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin 
Install-Module WindowsPSModulePath -Force
```

Depois de instalar este módulo, execute o `Add-WindowsPSModulePath` cmdlet para adicionar o Windows PowerShell `PSModulePath` para núcleo de PowerShell:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[suporte da Comunidade]: https://github.com/powershell/powershell/issues
[Microsoft Community]: https://answers.microsoft.com/
[PowerShell técnico Comunidade]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[assistido suporte]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[licença MIT]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
['WindowsPSModulePath']: https://www.powershellgallery.com/packages/WindowsPSModulePath/
