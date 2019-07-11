---
description: Saiba mais sobre o histórico de versão para a extensão do Desired State Configuration (DSC) no Azure.
ms.date: 06/21/2018
keywords: dsc, powershell, azure, extension
title: Histórico de versões da extensão de DSC do Azure
ms.openlocfilehash: 6d821e53e9206d99425e8c83f6d90986c7c28b63
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734655"
---
# <a name="azure-desired-state-configuration-extension-version-history"></a>Histórico de versões de extensão do Azure Desired State Configuration

A extensão de VM do Azure Desired State Configuration (DSC) é atualizada conforme necessário para suportar aprimoramentos e novos recursos fornecidos pelo Azure, o Windows Server e o Windows Management Framework (WMF) que inclui o Windows PowerShell.

Este artigo fornecerá informações sobre cada versão da extensão de VM de DSC do Azure, quais ambientes ele suporta e comentários e comentários em novas funcionalidades ou as alterações.

## <a name="latest-version"></a>Versão mais recente

### <a name="version-276"></a>Versão 2.76

- **Data de lançamento:**
  - 9 de Maio de 2018 (Azure) | 21 de Junho de 2018 (o Azure na China, o Azure Government)
- **Suporte do sistema operacional:**
  - Windows Server 2016
  - Windows Server 2012 R2
  - Windows Server 2012
  - Windows Server 2008 R2 SP1
  - Cliente do Windows 7/8.1/10
  - Servidor Nano
- **Suporte WMF:**
  - WMF 5.1
  - WMF 5.0 RTM
  - Atualização do WMF 4.0
  - WMF 4.0
- **Ambiente:**
  - Azure
  - Azure China
  - Azure Government
- **Observações:** Esta versão utiliza DSC, incluído no Windows Server 2016; para outros sistemas operacionais Windows, ele instala o [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (instalação de WMF requer um reinício). Para o servidor Nano, a função de DSC está instalada na VM.
- **Novas funcionalidades:**
  - Melhoria no metadados de extensão de subestado e outras pequenas correções de erros.

## <a name="supported-versions"></a>Versões suportadas

> [!WARNING]
> As versões 2.4 por meio de 2,13 utilizam o WMF 5.0 pré-visualização pública cujos certificados de assinatura expiraram em Agosto de 2016.  Para obter mais informações sobre este problema, consulte [mensagem de blogue](https://blogs.msdn.microsoft.com/powershell/2016/05/24/azure-dsc-extension-versions-2-4-up-to-2-13-will-retire-in-august/).

### <a name="version-275"></a>Versão 2.75

- **Data de lançamento:** 5 de março de 2018
- **Suporte do sistema operacional:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows Client 7/8.1/10, Nano Server
- **Suporte WMF:** WMF 5.1, WMF 5.0 RTM, o WMF 4.0 Update, o WMF 4.0
- **Ambiente:** Azure
- **Observações:** Esta versão utiliza DSC, incluído no Windows Server 2016; para outros sistemas operacionais Windows, ele instala o [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (instalação de WMF requer um reinício). Para o servidor Nano, a função de DSC está instalada na VM.
- **Novas funcionalidades:**
  - Após a mudança recente do GitHub para o TLS 1.2, não é possível carregar uma VM para DSC de automatização do Azure através de modelos de BRICOLAGEM Resource Manager. disponíveis no Azure Marketplace ou utilizar a extensão de DSC para obter qualquer configuração alojada no GitHub. Verá um erro semelhante ao seguinte ao implementar a extensão:

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

  - A nova versão de extensão, TLS 1.2 agora é imposta. Ao implementar a extensão, se já teve o AutoUpgradeMinorVersion = true no modelo do Resource Manager, em seguida, a extensão irá obter autoupgraded para 2.75. Para obter atualizações manuais, especifique `TypeHandlerVersion = 2.75` no modelo do Resource Manager.

### <a name="version-270---272"></a>Versão à 2.70 2.72

- **Data de lançamento:** 13 de Novembro de 2017
- **Suporte do sistema operacional:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows Client 7/8.1/10, Nano Server
- **Suporte WMF:** WMF 5.1, WMF 5.0 RTM, o WMF 4.0 Update, o WMF 4.0
- **Ambiente:** Azure
- **Observações:** Esta versão utiliza DSC, incluído no Windows Server 2016; para outros sistemas operacionais Windows, ele instala o [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (instalação de WMF requer um reinício). Para o servidor Nano, a função de DSC está instalada na VM.
- **Novas funcionalidades:**
  - Correções e aprimoramentos que simplifica a utilização da automatização do Azure de DSC através do portal da interface do Usuário, bem como o modelo do Resource Manager de bugs.  Para obter mais informações, consulte [Script de configuração predefinido](/azure/virtual-machines/extensions/dsc-overview) na documentação de extensão de DSC.

### <a name="version-226"></a>Versão 2.26

- **Data de lançamento:** 9 de Junho de 2017
- **Suporte do sistema operacional:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows Client 7/8.1/10, Nano Server
- **Suporte WMF:** WMF 5.1, WMF 5.0 RTM, o WMF 4.0 Update, o WMF 4.0
- **Ambiente:** Azure
- **Observações:** Esta versão utiliza DSC, incluído no Windows Server 2016; para outros sistemas operacionais Windows, ele instala o [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (instalação de WMF requer um reinício). Para o servidor Nano, a função de DSC está instalada na VM.
- **Novas funcionalidades:**
  - Melhorias de telemetria.

### <a name="version-225"></a>Versão 2.25

- **Data de lançamento:** 2 de Junho de 2017
- **Suporte do sistema operacional:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Windows Client 7/8.1/10, Nano Server
- **Suporte WMF:** WMF 5.1, WMF 5.0 RTM, o WMF 4.0 Update, o WMF 4.0
- **Ambiente:** Azure
- **Observações:** Esta versão utiliza DSC, incluído no Windows Server 2016; para outros sistemas operacionais Windows, ele instala o [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (instalação de WMF requer um reinício). Para o servidor Nano, a função de DSC está instalada na VM.
- **Novas funcionalidades:**
  - Foram adicionadas várias correções de erros e outras pequenas melhorias.

### <a name="version-224"></a>Versão duplo 2.24

- **Data de lançamento:** 13 de Abril de 2017
- **Suporte do sistema operacional:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Nano Server
- **Suporte WMF:** WMF 5.1, WMF 5.0 RTM, o WMF 4.0 Update, o WMF 4.0
- **Ambiente:** Azure
- **Observações:** Esta versão utiliza DSC, incluído no Windows Server 2016; para outros sistemas operacionais Windows, ele instala o [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (instalação de WMF requer um reinício). Para o servidor Nano, a função de DSC está instalada na VM.
- **Novas funcionalidades:**
  - Expõe o UUID da VM e o ID do agente DSC como metadados de extensão. Outras pequenas melhorias foram adicionadas.

### <a name="version-223"></a>Versão 2.23

- **Data de lançamento:** 15 de Março de 2017
- **Suporte do sistema operacional:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Nano Server
- **Suporte WMF:** WMF 5.1, WMF 5.0 RTM, o WMF 4.0 Update, o WMF 4.0
- **Ambiente:** Azure
- **Observações:** Esta versão utiliza DSC, incluído no Windows Server 2016; para outros sistemas operacionais Windows, ele instala o [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (instalação de WMF requer um reinício). Para o servidor Nano, a função de DSC está instalada na VM.
- **Novas funcionalidades:**
  - Muitas correções de erros e outros aprimoramentos foram adicionadas.

### <a name="version-222"></a>Versão 2.22

- **Data de lançamento:** 8 de Fevereiro de 2017
- **Suporte do sistema operacional:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Nano Server
- **Suporte WMF:** WMF 5.1, WMF 5.0 RTM, o WMF 4.0 Update, o WMF 4.0
- **Ambiente:** Azure
- **Observações:** Esta versão utiliza DSC, incluído no Windows Server 2016; para outros sistemas operacionais Windows, ele instala o [Windows Management Framework 5.1](https://blogs.msdn.microsoft.com/powershell/2016/12/06/wmf-5-1-releasing-january-2017/) (instalação de WMF requer um reinício). Para o servidor Nano, a função de DSC está instalada na VM.
- **Novas funcionalidades:**
  - A extensão DSC tem agora suporte para o WMF 5.1.
  - Pequenas, que outros aprimoramentos foram adicionados.

### <a name="version-221"></a>Versão 2.21

- **Data de lançamento:** 2 de Dezembro de 2016
- **Suporte do sistema operacional:** Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1, Nano Server
- **Suporte WMF:** WMF 5.1 atualizar pré-visualização, WMF 5.0 RTM, o WMF 4.0, o WMF 4.0
- **Ambiente:** Azure
- **Observações:** Esta versão utiliza DSC, incluído no Windows Server 2016; para outros sistemas operacionais Windows, ele instala o [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (instalação de WMF requer um reinício). Para o servidor Nano, a função de DSC está instalada na VM.
- **Novas funcionalidades:**
  - A extensão DSC está agora disponível no servidor Nano. Esta versão contém, principalmente, as alterações de código para executar a extensão no servidor Nano.
  - Pequenas, que outros aprimoramentos foram adicionados.

### <a name="version-220"></a>Versão 2.20

- **Data de lançamento:** 2 de Agosto de 2016
- **Suporte do sistema operacional:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **Suporte WMF:** WMF 5.1 atualizar pré-visualização, WMF 5.0 RTM, o WMF 4.0, o WMF 4.0
- **Ambiente:** Azure
- **Observações:** Esta versão utiliza DSC, incluído no Windows Server 2016 Technical Preview; para outros sistemas operacionais Windows, ele instala o [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (instalação de WMF requer um reinício).
- **Novas funcionalidades:**
  - O suporte para o WMF 5.1 de pré-visualização. Quando publicada pela primeira vez, esta versão era uma atualização opcional e tinha que especifique Wmfversion = ' 5.1PP' em modelos do Resource Manager para instalar a pré-visualização do WMF 5.1. Wmfversion = "latest" ainda instala os [WMF 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/). Para obter mais informações sobre a pré-visualização do WMF 5.1, consulte [este blog](https://blogs.msdn.microsoft.com/powershell/2016/07/16/announcing-windows-management-framework-wmf-5-1-preview/).
  - Menor outras correções e melhorias foram adicionadas.

### <a name="version--219"></a>Versão 2.19

- **Data de lançamento:** 3 de Junho de 2016
- **Suporte do sistema operacional:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **Suporte WMF:** O WMF 5.0 RTM, o WMF 4.0 Update, o WMF 4.0
- **Ambiente:** Azure, Azure China, Azure Government
- **Observações:** Esta versão utiliza DSC, incluído no Windows Server 2016 Technical Preview; para outros sistemas operacionais Windows, ele instala o [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (instalação de WMF requer um reinício).
- **Novas funcionalidades:**
  - A extensão DSC está agora incluído para o Azure China. Esta versão contém, principalmente, correções para executar a extensão no Azure China.

### <a name="version-218"></a>Versão 2.18

- **Data de lançamento:** 3 de Junho de 2016
- **Suporte do sistema operacional:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **Suporte WMF:** O WMF 5.0 RTM, o WMF 4.0 Update, o WMF 4.0
- **Ambiente:** Azure
- **Observações:** Esta versão utiliza DSC, incluído no Windows Server 2016 Technical Preview; para outros sistemas operacionais Windows, ele instala o [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (instalação de WMF requer um reinício).
- **Novas funcionalidades:**
  - Certifique-se de telemetria sem bloqueio quando ocorre um erro durante a transferência de correção de telemetria (problema conhecido do DNS do Azure) ou durante a instalação.
  - Corrigi o problema intermitente onde extensão interrompe o processamento de configuração após um reinício. Isso estava causando a extensão do DSC para permanecer no estado de "transição".
  - Menor outras correções e melhorias foram adicionadas.

### <a name="version-217"></a>Versão 2.17

- **Data de lançamento:** 26 de Abril de 2016
- **Suporte do sistema operacional:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **Suporte WMF:** O WMF 5.0 RTM, o WMF 4.0 Update, o WMF 4.0
- **Ambiente:** Azure
- **Observações:** Esta versão utiliza DSC, incluído no Windows Server 2016 Technical Preview; para outros sistemas operacionais Windows, ele instala o [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (instalação de WMF requer um reinício).
- **Novas funcionalidades:**
  - O suporte para o WMF 4.0 Update. Para obter mais informações sobre a atualização do WMF 4.0, consulte [este blog](https://blogs.msdn.microsoft.com/powershell/2016/01/19/windows-management-framework-wmf-4-0-update-now-available-for-windows-server-2012-windows-server-2008-r2-sp1-and-windows-7-sp1/).
  - Instale a lógica de repetição sobre os erros que ocorrem durante a instalação da extensão DSC ou ao aplicar uma configuração de DSC publicar a extensão. Como parte dessa alteração, a extensão voltará a tentar a instalação, se uma instalação anterior falhou ou aplicá novamente uma configuração de DSC que tinha anteriormente falhado, para um máximo três vezes até atingir o estado de conclusão (erros/com êxito) ou se um pedido novo. Se a extensão falhar devido a entrada de utilizador/definições de utilizador inválido, não repita. Neste caso, a extensão tem de ser invocado de novo com um novo pedido e corrija as definições do utilizador. Nota: A extensão DSC está dependente do agente de VM do Azure para as repetições. O agente VM do Azure invoca a extensão com o último pedido com falha, até atingir um Estado de sucesso ou erro.

### <a name="version-216"></a>Versão 2.16

- **Data de lançamento:** 21 de Abril de 2016
- **Suporte do sistema operacional:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **Suporte WMF:** WMF 5.0 RTM, WMF 4.0
- **Ambiente:** Azure
- **Observações:** Esta versão utiliza DSC, incluído no Windows Server 2016 Technical Preview; para outros sistemas operacionais Windows, ele instala o [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (instalação de WMF requer um reinício).
- **Novas funcionalidades:**
  - Melhoria no processamento de erros e outras pequenas correções de erros.
  - Nova propriedade nas definições de extensão de DSC. ForcePullAndApply no AdvancedOptions é adicionado ao ativar a extensão DSC aplicá configurações de DSC quando o modo de atualização é Pull (em oposição ao modo de Push predefinido). Para obter mais informações, consulte [este blog](https://blogs.msdn.microsoft.com/powershell/2016/02/26/arm-dsc-extension-settings/) para obter mais informações sobre as definições de extensão de DSC.

### <a name="version-215"></a>Versão 2.15

- **Data de lançamento:** 14 de Março de 2016
- **Suporte do sistema operacional:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **Suporte WMF:** WMF 5.0 RTM, WMF 4.0
- **Ambiente:** Azure
- **Observações:** Esta versão utiliza DSC, incluído no Windows Server 2016 Technical Preview; para outros sistemas operacionais Windows, ele instala o [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (instalação de WMF requer um reinício).
- **Novas funcionalidades:**
  - Na versão de extensão 2.14, as alterações para instalar a versão RTM do WMF foram incluídas. Durante a atualização da versão de extensão 2.13.2.0 para 2.14.0.0, poderá reparar que alguns cmdlets de DSC falhar ou a configuração falha com um erro – 'Não encontrada a instância com devido a valores de propriedade'. Para obter mais informações, consulte a [notas de versão do DSC](https://msdn.microsoft.com/en-us/powershell/wmf/limitation_dsc). As soluções alternativas para esses problemas tenham sido adicionadas na versão 2,15.
  - Infelizmente, se já tiver instalado a versão 2.14 e se deparar com um dos dois problemas acima, terá de executar estes passos manualmente.  Numa sessão do PowerShell elevada:
    - `Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof`
    - `mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof`

### <a name="version-214"></a>Versão 2.14

- **Data de lançamento:** 25 de Fevereiro de 2016
- **Suporte do sistema operacional:** Windows Server 2016 Technical Preview, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 SP1
- **Suporte WMF:** WMF 5.0 RTM, WMF 4.0
- **Ambiente:** Azure
- **Observações:** Esta versão utiliza DSC, incluído no Windows Server 2016 Technical Preview; para outros sistemas operacionais Windows, ele instala o [Windows Management Framework 5.0 RTM](https://blogs.msdn.microsoft.com/powershell/2015/12/16/windows-management-framework-wmf-5-0-rtm-is-now-available/) (instalação de WMF requer um reinício).
- **Novas funcionalidades:**
  - Utiliza o RTM do WMF.
  - Permite a recolha de dados para melhorar a qualidade da extensão do DSC. Para obter mais informações, consulte [o blogue](https://blogs.msdn.microsoft.com/powershell/2016/02/02/azure-dsc-extension-data-collection-2/).
  - Fornece um formato de definições atualizadas para a extensão num modelo do Resource Manager. Para obter mais informações, consulte [o blogue](https://blogs.msdn.microsoft.com/powershell/2016/02/26/arm-dsc-extension-settings/).
  - Correções de erros e outras melhorias.

## <a name="next-steps"></a>Passos Seguintes

- Para obter mais informações sobre o DSC de PowerShell, vá para o [Centro de documentação do PowerShell](../overview/overview.md).
- Examine os [modelo do Resource Manager para a extensão DSC](/azure/virtual-machines/extensions/dsc-template).
- Para mais funcionalidades que pode gerir utilizando o PowerShell DSC e para mais recursos de DSC, procurar as [galeria do PowerShell](https://www.powershellgallery.com/packages?q=DscResource&x=0&y=0).
- Para obter detalhes sobre passando parâmetros confidenciais em configurações, consulte [gerir credenciais com segurança com o processador de extensão DSC](/azure/virtual-machines/extensions/dsc-credentials).
