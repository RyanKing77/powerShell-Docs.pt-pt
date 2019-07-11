---
title: Descrição geral de fornecedor do PowerShell do Windows | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82244fbd-07b9-47f3-805c-3fb90ebbf58a
caps.latest.revision: 13
ms.openlocfilehash: 81f6c8cd75ccea9e711cd8f6d6daa6cca5a499a0
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734861"
---
# <a name="windows-powershell-provider-overview"></a>Windows PowerShell Provider Overview (Fornecedor do Windows PowerShell: Descrição Geral)

Um fornecedor de Windows PowerShell permite que qualquer arquivo de dados para serem expostas como um sistema de ficheiros, como se fosse uma unidade montada. Por exemplo, o fornecedor de registo incorporado permite-lhe navegar no Registro, como navegaria o `c` unidade do seu computador. Um provedor também pode substituir a `Item` cmdlets (por exemplo, `Get-Item`, `Set-Item`, etc.), de modo que os dados no seu arquivo de dados podem ser tratados como arquivos e diretórios são processados quando navegar de um sistema de ficheiros. Para obter mais informações sobre fornecedores e unidades e os provedores internos no Windows PowerShell, consulte [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).

## <a name="providers-and-drives"></a>Fornecedores e unidades

Um fornecedor define a lógica que serve para acessar, navegar e editar um arquivo de dados, enquanto uma unidade Especifica um ponto de entrada específico para um arquivo de dados (ou uma parte de um arquivo de dados) que é do tipo definido pelo provedor. Por exemplo, o fornecedor de registo permite-lhe aceder hives e as chaves num registo e as unidades HKLM e HKCU especifique os hives correspondente no registo. O HKLM e HKCU as unidades ambas utilizam o fornecedor de registo.

Quando escreve um fornecedor, pode especificar unidades-unidades padrão que são criados automaticamente quando o fornecedor está disponível. Também define um método para criar novas unidades que usar esse provedor.

## <a name="type-of-providers"></a>Tipo de fornecedores

Existem vários tipos de fornecedores, cada uma delas fornece um nível diferente de funcionalidade. Um provedor é implementado como uma classe que deriva de um dos descendentes do [System.Management.Automation.SessionStateCategory](/dotnet/api/system.management.automation.sessionstatecategory?view=pscore-6.2.0) **CmdletProvider** classe. Para obter informações sobre os diferentes tipos de fornecedores, consulte [tipos de fornecedor](./provider-types.md).

## <a name="provider-cmdlets"></a>Provider cmdlets (Cmdlets de fornecedores)

Os provedores podem implementar métodos que correspondem aos cmdlets, criando comportamentos personalizados no caso dos cmdlets quando usado numa unidade para esse provedor. Dependendo do tipo de fornecedor, os diferentes conjuntos de cmdlets estão disponíveis. Para obter uma lista completa dos cmdlets disponíveis para a personalização em fornecedores, consulte [cmdlets do fornecedor de](./provider-cmdlets.md).

## <a name="provider-paths"></a>Caminhos de fornecedor

Os utilizadores navegam unidades de fornecedor, como de sistemas de ficheiros. Por este motivo, esperam que a sintaxe de caminhos para corresponder aos caminhos usados na navegação do sistema de ficheiros. Quando um utilizador executa um cmdlet de fornecedor, eles especificam um caminho para o item a ser acessado. O caminho especificado pode ser interpretado de várias formas. Um provedor deve suportar uma ou mais dos seguintes tipos de caminho.

### <a name="drive-qualified-paths"></a>Caminhos de unidade qualificado

Um caminho qualificado de unidade é uma combinação do nome do item, o contentor e os subcontentores no qual o item está localizado e a unidade do Windows PowerShell através do qual o item ser acedido. (As unidades são definidas pelo provedor que é usado para acessar o arquivo de dados. Este caminho que começa com o nome de unidade, seguido de dois pontos (:). Por exemplo: `get-childitem C:`

### <a name="provider-qualified-paths"></a>Caminhos de fornecedor qualificado

Para permitir que o mecanismo do Windows PowerShell inicializar e uninitialize seu fornecedor, o fornecedor tem de suportar um caminho qualificado do fornecedor. Por exemplo, o utilizador pode inicializar e uninitialize o fornecedor do sistema de ficheiros, pois ele define o seguinte caminho qualificado do fornecedor: `FileSystem::\\uncshare\abc\bar`.

### <a name="provider-direct-paths"></a>Caminhos de fornecedor direct

Para permitir o acesso remoto para o seu fornecedor de Windows PowerShell, deve oferecer suporte a um caminho de fornecedor direct para passar diretamente para o fornecedor de Windows PowerShell para a localização atual. Por exemplo, pode utilizar o fornecedor de Windows PowerShell de Registro `\\server\regkeypath` como um caminho direto de fornecedor.

### <a name="provider-internal-paths"></a>Caminhos de fornecedor-interno

Para permitir que o cmdlet do fornecedor para aceder aos dados através de interfaces de programação de aplicações (APIs) não - Windows PowerShell, o seu fornecedor de Windows PowerShell deve suportar um caminho internas do fornecedor. Este caminho é indicado depois do "::" no caminho qualificado do fornecedor. Por exemplo, o caminho do fornecedor interno para o fornecedor de Windows PowerShell do sistema de ficheiros é `\\uncshare\abc\bar`.

## <a name="overriding-cmdlet-parameters"></a>Substituição de parâmetros do cmdlet

O comportamento de alguns cmdlets específicos do fornecedor pode ser substituído por um fornecedor. Para obter uma lista de parâmetros que pode ser substituído e como substitui-los na sua classe de fornecedor, consulte [parâmetros de cmdlet do fornecedor](./provider-cmdlet-parameters.md)

## <a name="dynamic-parameters"></a>Parâmetros dinâmicos

Fornecedores de podem definir parâmetros dinâmicos que são adicionados a um cmdlet de fornecedor quando o usuário Especifica um determinado valor para um dos parâmetros estáticos do cmdlet. Um provedor faz isso implementando um ou mais métodos de parâmetro dinâmico. Para obter uma lista de parâmetros de cmdlet que pode ser utilizado para adicionar o parâmetro dinâmico e os métodos utilizados para implementá-los, consulte [parâmetros dinâmicos do fornecedor cmdlet](./provider-cmdlet-dynamic-parameters.md).

## <a name="provider-capabilities"></a>Capacidades de fornecedor

O [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeração define uma série de recursos que podem oferecer suporte a provedores. Estes incluem a capacidade de carateres universais de utilização, filtrar itens e as transações de suporte. Para especificar as capacidades de um fornecedor, adicione uma lista de valores do [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeração, juntamente com uma lógica `OR` operação, como o [ System.Management.Automation.Provider.Cmdletproviderattribute.Providercapabilities*](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities) propriedade (o segundo parâmetro do atributo) da [System.Management.Automation.Provider.Cmdletproviderattribute ](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atributo para sua classe de fornecedor. Por exemplo, o atributo seguinte especifica que o fornecedor suporta o [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities?view=pscore-6.2.0) **ShouldProcess** e [ System.Management.Automation.Provider.ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities?view=pscore-6.2.0) **transações** capacidades.

```csharp
[CmdletProvider(RegistryProvider.ProviderName, ProviderCapabilities.ShouldProcess | ProviderCapabilities.Transactions)]

```

## <a name="provider-cmdlet-help"></a>Ajuda do cmdlet de fornecedor

Ao escrever um fornecedor, pode implementar a sua própria ajuda para os cmdlets de fornecedor com suporte. Isto inclui um único tópico de ajuda para cada cmdlet de fornecedor ou em várias versões de um tópico de ajuda para casos em que o cmdlet de fornecedor funciona de forma diferente, consoante a utilização de parâmetros dinâmicos. Para suportar a ajuda do provedor específico do cmdlet, o fornecedor tem de implementar o [System.Management.Automation.Provider.Icmdletprovidersupportshelp](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp) interface.

As chamadas de motor do Windows PowerShell a [System.Management.Automation.Provider.Icmdletprovidersupportshelp.Gethelpmaml*](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp.GetHelpMaml) método para exibir o tópico de ajuda para os cmdlets do fornecedor. O mecanismo fornece o nome do cmdlet que o utilizador especificado durante a execução do `Get-Help` cmdlet e o caminho atual do utilizador. O caminho atual é necessário se o fornecedor de implementar versões diferentes do mesmo cmdlet de fornecedor para unidades diferentes. O método deve retornar uma cadeia que contém o XML para a ajuda do cmdlet.

O conteúdo para o ficheiro de ajuda é escrito usando PSMAML XML. Este é o mesmo esquema XML, que é utilizado para escrever o conteúdo de ajuda para cmdlets autónomo. Adicionar o conteúdo para a sua ajuda para o ficheiro de ajuda para o seu fornecedor de cmdlet personalizado sob o `CmdletHelpPaths` elemento. A exemplo a seguir mostra o `command` elemento para um cmdlet de fornecedor único e ele mostra como especificar o nome do cmdlet fornecedor que o fornecedor. suporta a

```xml
<CmdletHelpPaths>
  <command:command>
    <command:details>
      <command:name>ProviderCmdletName</command:name>
      <command:verb>Verb</command:verb>
      <command:noun>Noun</command:noun>
    <command:details>
  </command:command>
<CmdletHelpPath>
```

## <a name="see-also"></a>Veja Também

[Funcionalidade de fornecedor do PowerShell do Windows](./provider-types.md)

[Cmdlets do fornecedor](./provider-cmdlets.md)

[Escrever um fornecedor do Windows PowerShell](./writing-a-windows-powershell-provider.md)