---
description: Saiba mais sobre o histórico de versão para a extensão de configuração de estado pretendido (DSC) no Azure.
ms.date: 03/14/2018
ms.topic: conceptual
keywords: DSC, extensão do powershell do azure,
title: Histórico de versão da extensão DSC do Azure
author: DCtheGeek
ms.author: dacoulte
ms.openlocfilehash: a183137dde302811874bd5466c35bccebca5d128
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="azure-desired-state-configuration-extension-version-history"></a>Histórico de versão da extensão de configuração de estado da Desired do Azure

A extensão da VM do Azure pretendido Estado Configuration (DSC) é atualizada como-necessário para suportar melhoramentos e novas capacidades fornecidas pelo Azure, Windows Server e o Windows Management Framework (WMF) que inclui o Windows PowerShell.

Este artigo fornece informações sobre cada versão da extensão de VM de DSC do Azure, que ambientes que suporta, comentários e observações em novas funcionalidades ou as alterações.

## <a name="latest-versions"></a>Versões mais recentes

### <a name="version-275"></a>Versão 2.75

- **Data da versão:**
  - 5 de Março de 2018
- **Suporte de SO:**
  - Windows Server 2016
  - Windows Server 2012 R2
  - Windows Server 2012
  - Windows Server 2008 R2 SP1
  - Cliente Windows 8.1/7/10
  - Servidor Nano
- **Suporte do WMF:**
  - WMF 5.1
  - WMF 5.0 RTM
  - Atualização do WMF 4.0
  - WMF 4.0
- **Ambiente:**
  - Azure
- **Observações:** nesta versão utiliza DSC incluído no Windows Server 2016; para outros SO Windows anteriores, instala o [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (instalar WMF requer um reinício). Para o servidor de nano for apresentado, a função de DSC está instalada na VM.
- **Novas funcionalidades:**
  - Após a mudança recente do GitHub para TLS 1.2, não é possível carregar uma VM para o DSC de automatização do Azure utilizando o Gestor de recursos DIY modelos disponíveis no Azure Marketplace ou utilizar a extensão de DSC para obter a configuração de alojada no GitHub. Verá um erro semelhante ao seguinte durante a implementação de extensão:

    ```json
    {
        "code": "DeploymentFailed",
        "message": "At least one resource deployment operation failed. Please list deployment operations for details. Please see https://aka.ms/arm-debug for usage details.",
        "details": [{
            "code": "Conflict",
            "message": "{
                \"status\": \"Failed\",
                \"error\": {
                    \"code\": \"ResourceDeploymentFailure\",
                    \"message\": \"The resource operation completed with terminal provisioning state 'Failed'.\",
                    \"details\": [ {
                        \"code\": \"VMExtensionProvisioningError\",
                        \"message\": \"VM has reported a failure when processing extension 'Microsoft.Powershell.DSC'.
                        Error message: \\\"The DSC Extension failed to execute: Error downloading
                        https://github.com/Azure/azure-quickstart-templates/raw/master/dsc-extension-azure-automation-pullserver/UpdateLCMforAAPull.zip
                        after 29 attempts: The request was aborted: Could not create SSL/TLS secure channel..\\nMore information about the failure can
                        be found in the logs located under 'C:\\\\WindowsAzure\\\\Logs\\\\Plugins\\\\Microsoft.Powershell.DSC\\\\2.74.0.0' on the VM.\\\".\"
                    } ]
                }
            }"
        }]
    }
    ```

  - A nova versão da extensão, TLS 1.2 agora é imposta. Ao implementar a extensão se já tiver o AutoUpgradeMinorVersion = true no modelo do Resource Manager, em seguida, a extensão obterá autoupgraded para 2.75. Para obter atualizações manuais, especifique `TypeHandlerVersion = 2.75` no seu modelo do Resource Manager.

### <a name="version-219"></a>Versão 2.19

- **Data da versão:**
  - 3 de Junho de 2016
- **Suporte de SO:**
  - Windows Server 2016 Technical Preview
  - Windows Server 2012 R2
  - Windows Server 2012
  - Windows Server 2008 R2 SP1
- **Suporte do WMF:**
  - WMF 5.0 RTM
  - Atualização do WMF 4.0
  - WMF 4.0
- **Ambiente:**
  - Azure
  - Azure China
  - Azure Government
- **Observações:** nesta versão utiliza DSC incluído no Windows Server 2016 Technical Preview; para outros sos, instala o [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (instalar WMF requer um reinício).
- **Novas funcionalidades:**
  - A extensão de DSC agora está na integrada para o Azure China. Esta versão contém principalmente correções para executar a extensão no Azure China.

## <a name="supported-versions"></a>Versões suportadas

> [!WARNING]
> Versões 2.4 através de 2.13 utilizam WMF 5.0 pré-visualização pública cujos certificados de assinatura expiraram dentro de Agosto de 2016.  Para obter mais informações sobre este problema, consulte [blogue](https://blogs.msdn.microsoft.com/powershell/2016/05/24/azure-dsc-extension-versions-2-4-up-to-2-13-will-retire-in-august/).

### <a name="version-270---272"></a>Versão 2.70 2.72

- **Data da versão:** 13 de Novembro de 2017
- **Suporte de SO:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows cliente 7/8.1/10, Nano servidor
- **Suporte do WMF:** WMF 5.1, WMF 5.0 RTM, atualização do WMF 4.0, WMF 4.0
- **Ambiente:** Azure
- **Observações:** nesta versão utiliza DSC incluído no Windows Server 2016; para outros SO Windows anteriores, instala o [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (instalar WMF requer um reinício). Para o servidor de nano for apresentado, a função de DSC está instalada na VM.
- **Novas funcionalidades:**
  - Erros correções & melhoramentos que simplifica a utilização da automatização do Azure de DSC através da IU do portal, bem como o modelo do Resource Manager.  Para obter mais informações, consulte [Script de configuração predefinido](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/extensions-dsc-overview#default-configuration-script) na documentação de extensão de DSC.

### <a name="version-226"></a>Versão 2.26

- **Data da versão:** 9 de Junho de 2017
- **Suporte de SO:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows cliente 7/8.1/10, Nano servidor
- **Suporte do WMF:** WMF 5.1, WMF 5.0 RTM, atualização do WMF 4.0, WMF 4.0
- **Ambiente:** Azure
- **Observações:** nesta versão utiliza DSC incluído no Windows Server 2016; para outros SO Windows anteriores, instala o [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (instalar WMF requer um reinício). Para o servidor de nano for apresentado, a função de DSC está instalada na VM.
- **Novas funcionalidades:**
  - Melhoramentos de telemetria.

### <a name="version-225"></a>Versão 2.25

- **Data da versão:** 2 de Junho de 2017
- **Suporte de SO:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows cliente 7/8.1/10, Nano servidor
- **Suporte do WMF:** WMF 5.1, WMF 5.0 RTM, atualização do WMF 4.0, WMF 4.0
- **Ambiente:** Azure
- **Observações:** nesta versão utiliza DSC incluído no Windows Server 2016; para outros SO Windows anteriores, instala o [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (instalar WMF requer um reinício). Para o servidor de nano for apresentado, a função de DSC está instalada na VM.
- **Novas funcionalidades:**
  - Foram adicionadas várias correções de erros e outras melhorias secundárias.

### <a name="version-224"></a>Versão duplo 2.24

- **Data da versão:** 13 de Abril de 2017
- **Suporte de SO:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Nano servidor
- **Suporte do WMF:** WMF 5.1, WMF 5.0 RTM, atualização do WMF 4.0, WMF 4.0
- **Ambiente:** Azure
- **Observações:** nesta versão utiliza DSC incluído no Windows Server 2016; para outros SO Windows anteriores, instala o [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (instalar WMF requer um reinício). Para o servidor de nano for apresentado, a função de DSC está instalada na VM.
- **Novas funcionalidades:**
  - Expõe UUID de VM & ID de agente do DSC como metadados de extensão. Foram adicionadas outras melhorias secundárias.

### <a name="version-223"></a>Versão 2.23

- **Data da versão:** 15 de Março de 2017
- **Suporte de SO:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Nano servidor
- **Suporte do WMF:** WMF 5.1, WMF 5.0 RTM, atualização do WMF 4.0, WMF 4.0
- **Ambiente:** Azure
- **Observações:** nesta versão utiliza DSC incluído no Windows Server 2016; para outros SO Windows anteriores, instala o [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (instalar WMF requer um reinício). Para o servidor de nano for apresentado, a função de DSC está instalada na VM.
- **Novas funcionalidades:**
  - Muitos correções de erros e outras melhorias foram adicionados.

### <a name="version-222"></a>Versão 2.22

- **Data da versão:** 8 de Fevereiro de 2017
- **Suporte de SO:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Nano servidor
- **Suporte do WMF:** WMF 5.1, WMF 5.0 RTM, atualização do WMF 4.0, WMF 4.0
- **Ambiente:** Azure
- **Observações:** nesta versão utiliza DSC incluído no Windows Server 2016; para outros SO Windows anteriores, instala o [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (instalar WMF requer um reinício). Para o servidor de nano for apresentado, a função de DSC está instalada na VM.
- **Novas funcionalidades:**
  - A extensão de DSC tem agora suporte para o WMF 5.1.
  - Outras melhorias foram adicionadas secundárias.

### <a name="version-221"></a>Versão 2.21

- **Data da versão:** 2 de Dezembro de 2016
- **Suporte de SO:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Nano servidor
- **Suporte do WMF:** pré-visualização do WMF 5.1, WMF 5.0 RTM, atualização do WMF 4.0, WMF 4.0
- **Ambiente:** Azure
- **Observações:** nesta versão utiliza DSC incluído no Windows Server 2016; para outros SO Windows anteriores, instala o [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (instalar WMF requer um reinício). Para o servidor de nano for apresentado, a função de DSC está instalada na VM.
- **Novas funcionalidades:**
  - A extensão de DSC está agora disponível no servidor de nano for apresentado. Esta versão contém principalmente alterações de código para executar a extensão no servidor de nano for apresentado.
  - Outras melhorias foram adicionadas secundárias.

### <a name="version-220"></a>Versão 2.20

- **Data da versão:** 2 de Agosto de 2016
- **Suporte de SO:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **Suporte do WMF:** pré-visualização do WMF 5.1, WMF 5.0 RTM, atualização do WMF 4.0, WMF 4.0
- **Ambiente:** Azure
- **Observações:** nesta versão utiliza DSC incluído no Windows Server 2016 Technical Preview; para outros SO Windows anteriores, instala o [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (instalar WMF requer um reinício).
- **Novas funcionalidades:**
  - Suporte para WMF 5.1 pré-visualização. Quando publicada pela primeira vez, esta versão foi uma atualização opcional e tiver de especificar Wmfversion = ' 5.1PP' em modelos do Resource Manager para instalar a pré-visualização do WMF 5.1. Wmfversion = 'mais recente' ainda instala o [WMF 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/). Para obter mais informações sobre a pré-visualização do WMF 5.1, consulte [este blogue]( https://blogs.msdn.microsoft.com/powershell/2016/07/16/announcing-windows-management-framework-wmf-5-1-preview/).
  - Secundária outras correções e foram adicionados melhoramentos.

### <a name="version--219"></a>Versão 2.19

- **Data da versão:** 3 de Junho de 2016
- **Suporte de SO:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **Suporte do WMF:** WMF 5.0 RTM, atualização do WMF 4.0, WMF 4.0
- **Ambiente:** Government do Azure do Azure, Azure China,
- **Observações:** nesta versão utiliza DSC incluído no Windows Server 2016 Technical Preview; para outros SO Windows anteriores, instala o [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (instalar WMF requer um reinício).
- **Novas funcionalidades:**
  - A extensão de DSC agora é integrado para o Azure China. Esta versão contém principalmente correções para executar a extensão no Azure China.

### <a name="version-218"></a>Versão 2.18

- **Data da versão:** 3 de Junho de 2016
- **Suporte de SO:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **Suporte do WMF:** WMF 5.0 RTM, atualização do WMF 4.0, WMF 4.0
- **Ambiente:** Azure
- **Observações:** nesta versão utiliza DSC incluído no Windows Server 2016 Technical Preview; para outros SO Windows anteriores, instala o [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (instalar WMF requer um reinício).
- **Novas funcionalidades:**
  - Certifique-telemetria não-bloquear quando ocorre um erro durante a transferência da correção de telemetria (problema de DNS do Azure conhecido) ou durante a instalação.
  - Corrija o problema intermitente faça onde extensão interrompe o processamento da configuração após um reinício. Isto foi fazendo com que a extensão de DSC permanecer no estado de "transição".
  - Secundária outras correções e foram adicionados melhoramentos.

### <a name="version-217"></a>Versão 2.17

- **Data da versão:** 26 de Abril de 2016
- **Suporte de SO:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **Suporte do WMF:** WMF 5.0 RTM, atualização do WMF 4.0, WMF 4.0
- **Ambiente:** Azure
- **Observações:** nesta versão utiliza DSC incluído no Windows Server 2016 Technical Preview; para outros SO Windows anteriores, instala o [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (instalar WMF requer um reinício).
- **Novas funcionalidades:**
  - Suporte para o WMF 4.0 Update. Para obter mais informações sobre a atualização do WMF 4.0, consulte [este blogue](https://blogs.msdn.microsoft.com/powershell/2016/01/19/windows-management-framework-wmf-4-0-update-now-available-for-windows-server-2012-windows-server-2008-r2-sp1-and-windows-7-sp1/).
  - Instale a lógica de repetição sobre os erros que ocorrem durante a instalação da extensão DSC ou ao aplicar uma configuração de DSC publicar a extensão. Como parte desta alteração, a extensão terá de repetir a instalação se a falha de uma instalação anterior ou enact novamente uma configuração de DSC que tinha falhado anteriormente, para um máximo três horas até atingir o estado de conclusão (erros/com êxito) ou se for proveniente de um novo pedido. Se a extensão falhar devido a entrada de utilizador/definições de utilizador inválido, não repita. Neste caso, a extensão tem de ser invocados novamente com um novo pedido e corrija as definições do utilizador. Nota: A extensão de DSC está dependente do agente da VM do Azure para as repetições. O agente VM do Azure invoca a extensão com o último pedido falhado até atingir um Estado de êxito ou erro.

### <a name="version-216"></a>Versão 2.16

- **Data da versão:** 21 de Abril de 2016
- **Suporte de SO:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **Suporte do WMF:** WMF 5.0 RTM, WMF 4.0
- **Ambiente:** Azure
- **Observações:** nesta versão utiliza DSC incluído no Windows Server 2016 Technical Preview; para outros SO Windows anteriores, instala o [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (instalar WMF requer um reinício).
- **Novas funcionalidades:**
  - Melhoria no processamento de erros e outras pequenas correções de erros.
  - Nova propriedade nas definições da extensão de DSC. ForcePullAndApply no AdvancedOptions é adicionada ao ativar a extensão de DSC enact configurações de DSC quando o modo de atualização é solicitação (em vez do modo predefinido de Push). Para obter mais informações, consulte [este blogue](https://blogs.msdn.microsoft.com/powershell/2016/02/26/arm-dsc-extension-settings/) para obter mais informações sobre as definições de extensão de DSC.

### <a name="version-215"></a>Versão 2.15

- **Data da versão:** 14 de Março de 2016
- **Suporte de SO:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **Suporte do WMF:** WMF 5.0 RTM, WMF 4.0
- **Ambiente:** Azure
- **Observações:** nesta versão utiliza DSC incluído no Windows Server 2016 Technical Preview; para outros SO Windows anteriores, instala o [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (instalar WMF requer um reinício).
- **Novas funcionalidades:**
  - Na versão de extensão 2.14, as alterações para instalar o WMF RTM estavam incluídas. Durante a atualização da versão da extensão 2.13.2.0 para 2.14.0.0, poderá reparar que alguns cmdlets do DSC falhar ou a configuração falha com um erro – 'Não encontrada a instância com fornecido valores de propriedade'. Para obter mais informações, consulte o [notas de versão do DSC](https://msdn.microsoft.com/en-us/powershell/wmf/limitation_dsc). Foram adicionadas as soluções para estes problemas na versão 2.15.
  - Infelizmente, se já instalou a versão 2.14 e em execução dos problemas de dois acima, terá de executar estes passos manualmente.  Numa sessão do PowerShell elevada:
    - `Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof`
    - `mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof`

### <a name="version-214"></a>Versão 2.14

- **Data da versão:** 25 de Fevereiro de 2016
- **Suporte de SO:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **Suporte do WMF:** WMF 5.0 RTM, WMF 4.0
- **Ambiente:** Azure
- **Observações:** nesta versão utiliza DSC incluído no Windows Server 2016 Technical Preview; para outros SO Windows anteriores, instala o [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (instalar WMF requer um reinício).
- **Novas funcionalidades:**
  - Utiliza o WMF RTM.
  - Permite a recolha de dados para melhorar a qualidade da extensão DSC. Para obter mais informações, consulte [o blogue](https://blogs.msdn.microsoft.com/powershell/2016/02/02/azure-dsc-extension-data-collection-2/).
  - Fornece um formato de definições atualizadas para a extensão de um modelo do Resource Manager. Para obter mais informações, consulte [o blogue](https://blogs.msdn.microsoft.com/powershell/2016/02/26/arm-dsc-extension-settings/).
  - Correções de erros e outros melhoramentos.

## <a name="next-steps"></a>Próximos passos

- Para obter mais informações sobre o PowerShell DSC, vá para o [Centro de documentação do PowerShell](overview.md).
- Examine o [modelo do Resource Manager para a extensão de DSC](/azure/virtual-machines/windows/extensions-dsc-template).
- Para obter mais funcionalidades que pode gerir utilizando o PowerShell DSC e mais recursos de DSC, procure o [galeria do PowerShell](https://www.powershellgallery.com/packages?q=DscResource&x=0&y=0).
- Para obter detalhes sobre a transmitir parâmetros confidenciais para as configurações, consulte [gerir credenciais de forma segura com o processador de extensão de DSC](/azure/virtual-machines/windows/extensions-dsc-credentials).