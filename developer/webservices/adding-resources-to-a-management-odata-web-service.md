---
title: A adição de recursos para um serviço da Web de OData gestão | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e620bf6d-76be-47b0-a7a8-f43418f30c60
caps.latest.revision: 6
ms.openlocfilehash: b81a32b867795ae51c3f5308c2f82c31ed2747fa
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848469"
---
# <a name="adding-resources-to-a-management-odata-web-service"></a>Adding Resources to a Management OData Web Service (Adicionar Recursos a um Serviço Web OData de Gestão)

Este exemplo demonstra como adicionar um recurso a um serviço de web de OData de gestão existente usando o Designer de esquema do Management OData. O [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) exemplo cria um serviço web que expõe os recursos de processo e servidor. Neste exemplo, adicionará um recurso de Máquina Virtual (VM) para o serviço web.

## <a name="prerequisites"></a>Pré-requisitos

Este tópico pressupõe que transferiu e instalou o [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) exemplo conforme descrito na [criar um serviço da Web do Windows PowerShell](./creating-a-management-odata-web-service.md), e que tenham transferido e instalado o [Designer de esquema de OData da gestão](https://marketplace.visualstudio.com/items?itemName=jlisc0.ManagementODataSchemaDesigner). Este tópico também pressupõe que tem o módulo de Hyper-V do Windows PowerShell instalado no computador onde configura o ponto final Odata de gestão.

## <a name="adding-vm-as-a-resource-to-the-web-service"></a>Adicionar VM como um recurso para o serviço Web

O primeiro passo é importar o esquema de ponto de final de OData de gestão existente para o designer de esquema. O procedimento seguinte descreve como fazer isso.

#### <a name="importing-an-existing-schema-into-the-schema-designer"></a>Importar um esquema existente para o designer de esquema

1. Abra o Designer de esquema de OData de gestão.

2. Partir do **arquivo** menu, selecione **ficheiro** ; **Novo** ; **Ficheiro**. O **novo ficheiro** é apresentada a caixa de diálogo.

3. Clique em **modelo de gestão de OData**e, em seguida, clique em **aberto**.

4. Com o botão direito na janela principal e clique em **arquivo do esquema** ; **Importação**. O **aberto** é apresentada a caixa de diálogo.

5. Navegue para a pasta onde configura o serviço da web de OData de gestão para o [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) exemplo. Se utilizou o script do Windows PowerShell fornecido com esse exemplo para configurar o ponto final sem modificar o script, essa pasta está **C:\inetpub\wwwroot\Modata**. Selecione Schema.mof e clique em **aberto**.

   Neste momento, abra os arquivos Schema.mof e Schema num editor de texto e tenha em atenção que contêm mapeamentos para os recursos de processo e pelo serviço. Utiliza o ficheiro de Schema.mof [Distributed Management Task Force](https://www.dmtf.org/) standard (DTMF) MOF (Managed Object). O arquivo Schema utiliza um esquema XML que está descrito em [esquema de mapeamento de recursos](./resource-mapping-schema.md).

   O procedimento seguinte descreve como importar os cmdlets de Hyper-V para o modelo de esquema.

#### <a name="importing-cmdlets-into-the-schema"></a>Importar os cmdlets para o esquema

1. Com o botão direito numa área em branco da janela do estruturador de esquema e clique em **Cmdlets de importação**. O **Assistente de importação de Cmdlet** é apresentada a caixa de diálogo.

2. Certifique-se **computador Local** está selecionada e clique em **próxima**.

3. Certifique-se de que os módulos do PowerShell de Windows instalado está selecionado e selecione o Hyper-V na lista pendente. Clique em **seguinte**. Clique em **Seguinte**.

4. Na **substantivo do Cmdlet** lista, selecione **VM**. Clique em **Seguinte**

5. Neste exemplo, ligamos apenas os Get e Delete comandos com cmdlets. Limpar o **criar** e **UPDATE** caixas de seleção e certifique-se a **obter** e **eliminar** caixas de verificação são verificadas. Certifique-se de que o `Get-VM` cmdlet está selecionado para **Obtenha**e o `Remove-VM` cmdlet está selecionado para **eliminar**.

6. Como os metadados para os cmdlets VM não especificam um tipo de saída, será necessário executar o cmdlet para especificar o tipo de saída. Selecione **tipo de saída forneça** e clique em **execute o cmdlet**. O **execute o Cmdlet** é apresentada a caixa de diálogo. Clique em **Executar**. O **tipo de CLR** caixa é preenchida com o `VirtualMachine` tipo. Clique em **OK**, em seguida, clique em **próxima**.

7. Por predefinição, todas as propriedades do objeto VirtualMachine estão selecionadas. Pode limpar quaisquer propriedades que não pretende como parte dos dados retornados ao pedir este recurso do serviço web. Clique em **Seguinte**.

8. Tem de selecionar pelo menos uma propriedade a ser utilizado como uma chave. Selecione **Name** na lista e clique em **próxima**.

9. A próxima janela permite-lhe mapear as propriedades do recurso OData de gestão para as propriedades dos cmdlets subjacentes. O Assistente de propriedades com nomes idênticos é mapeado por padrão. Por exemplo, o `ComputerName` propriedade do recurso é mapeada para o `ComputerName` propriedade dos cmdlets.  Isto permite-lhe especificar o `ComputerName` propriedade numa solicitação ao serviço da web e tem o valor que especificar ser passada para o `Get-VM` cmdlet. `Id` e `Name` também são mapeadas por predefinição.

   10. Clique em **próxima**, em seguida, clique em **concluir**.

       O recurso da VM é agora apresentado na janela do estruturador de esquema. Pode examinar as propriedades e operações associadas o recursos. Em seguida, irá exportar os ficheiros de esquema atualizado para o diretório virtual para o serviço web.

#### <a name="exporting-schema-files-from-the-schema-designer"></a>Exportar ficheiros de esquema do designer de esquema

1. Com o botão direito numa área em branco da janela do estruturador de esquema e clique em **arquivo do esquema** ; **Exportar**. O **guardar como** é apresentada a caixa de diálogo.

2. Navegue para o mesmo diretório de onde o ficheiro MOF que importou. Nomeie o arquivo, o mesmo que o ficheiro MOF original (Schema.mof por padrão) e clique em **guardar**. Confirme que pretende substituir o ficheiro existente.

   Embora não for explicitamente declarado no **guardar como** caixa de diálogo, isto substitui os ficheiros de Schema.mof tanto Schema.

## <a name="next-steps"></a>Próximos Passos

Antes de acessar o novo recurso da VM do serviço web OData da gestão, tem de atualizar o ficheiro de RbacConfiguration.xml para permitir o acesso para o módulo de Hyper-V do Windows PowerShell, tal como descrito no [autorização baseada em funções de configuração](./configuring-role-based-authorization.md), e também terá de reiniciar o serviço web.