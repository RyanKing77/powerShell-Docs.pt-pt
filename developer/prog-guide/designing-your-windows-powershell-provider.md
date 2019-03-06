---
title: Estruturar o seu fornecedor do Windows PowerShell | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide], designing
ms.assetid: 11d20319-cc40-4227-b810-4af33372b182
caps.latest.revision: 10
ms.openlocfilehash: 711a85e9b2eade7b9095d7560f53610e709e380a
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429946"
---
# <a name="designing-your-windows-powershell-provider"></a>Designing Your Windows PowerShell Provider (Criar o seu Fornecedor do Windows PowerShell)

Se o produto ou a configuração expõe um conjunto de dados armazenados, por exemplo, uma base de dados que o utilizador vai querer navegue ou procure, deve implementar um fornecedor de Windows PowerShell. Além disso, se o seu produto fornece um contêiner, mesmo que não é um contentor de vários níveis, faz sentido para implementar um fornecedor de Windows PowerShell. Por exemplo, pode querer implementar um fornecedor de contentor do Windows PowerShell, se o verbo do cmdlet copiar, mover, mudar o nome novo ou remover faz sentido como uma operação nos seus dados de produto ou de configuração.

## <a name="windows-powershell-paths-identify-your-provider"></a>Caminhos do Windows PowerShell identificar o seu fornecedor

O tempo de execução do Windows PowerShell utiliza os caminhos do Windows PowerShell para aceder ao fornecedor de Windows PowerShell apropriado. Quando um cmdlet Especifica um destes caminhos, o tempo de execução saiba qual o fornecedor a utilizar para aceder ao arquivo de dados associados. Estes caminhos incluem caminhos qualificado de unidade, caminhos qualificado de fornecedor, caminhos de fornecedor direct e caminhos internas do fornecedor. Cada fornecedor de Windows PowerShell tem de suportar um ou mais desses caminhos.

Para obter mais informações sobre os caminhos do Windows PowerShell, veja como o Windows PowerShell funciona.

### <a name="defining-a-drive-qualified-path"></a>Definindo um caminho qualificado de unidade

Para permitir ao utilizador aceder aos dados localizados numa unidade física, o seu fornecedor de Windows PowerShell tem de suportar um caminho qualificado de unidade. Este caminho que começa com o nome de unidade, seguido de dois pontos (:), por exemplo, mydrive:\abc\bar.

### <a name="defining-a-provider-qualified-path"></a>Definindo um caminho qualificado do fornecedor

Para permitir que o tempo de execução do Windows PowerShell inicializar e uninitialize o fornecedor, o seu fornecedor de Windows PowerShell tem de suportar um caminho qualificado do fornecedor. Por exemplo, sistema de ficheiros::\\\uncshare\abc\bar é o caminho qualificado do fornecedor para o fornecedor do sistema de ficheiros fornecido pelo Windows PowerShell.

### <a name="defining-a-provider-direct-path"></a>Definindo um caminho direto de fornecedor

Para permitir o acesso remoto para o seu fornecedor de Windows PowerShell, deve oferecer suporte a um caminho de fornecedor direct para passar diretamente para o fornecedor de Windows PowerShell para a localização atual. Por exemplo, pode utilizar o fornecedor de Windows PowerShell de Registro \\\server\regkeypath como um caminho direto de fornecedor.

### <a name="defining-a-provider-internal-path"></a>Definindo um caminho de fornecedor-interno

Para permitir que o cmdlet do fornecedor para aceder aos dados através de interfaces de programação de aplicações (APIs) não - Windows PowerShell, o seu fornecedor de Windows PowerShell deve suportar um caminho internas do fornecedor. Este caminho é indicado depois do "::" no caminho qualificado do fornecedor. Por exemplo, o caminho do fornecedor interno para o fornecedor de Windows PowerShell do sistema de ficheiros é \\\uncshare\abc\bar.

## <a name="changing-stored-data"></a>A alteração de dados armazenados

Ao substituir os métodos que modificam o armazenamento de dados subjacente, sempre chamar o [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) método com a versão mais recente do item alterado por que método. A infraestrutura de fornecedor determina se o objeto do item tem de ser transmitidos para o pipeline, por exemplo, quando o usuário Especifica o parâmetro - PassThru. Se a obter o item mais atualizado é uma operação dispendiosa (em termos de desempenho), pode testar a propriedade Context.PassThru para determinar se, na verdade, precisa escrever o item resultante.

## <a name="choose-a-base-class-for-your-provider"></a>Escolha uma classe Base para o seu fornecedor

Windows PowerShell fornece um número de classes base que pode utilizar para implementar o seu próprio fornecedor de Windows PowerShell. Ao criar um fornecedor, escolha a classe base, descrita nesta secção, o que é mais adequada aos seus requisitos.

Cada classe de base de fornecedor de Windows PowerShell disponibiliza um conjunto de cmdlets. Esta secção descreve os cmdlets, mas ele não descreve os parâmetros.

Utilizar o estado da sessão, o tempo de execução do Windows PowerShell disponibiliza vários cmdlets de localização para alguns fornecedores de Windows PowerShell, como o `Get-Location`, `Set-Location`, `Pop-Location`, e `Push-Location` cmdlets. Pode utilizar o `Get-Help` cmdlet para obter informações sobre estes cmdlets de localização.

### <a name="cmdletprovider-base-class"></a>Classe CmdletProvider Base

O [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe define um provedor básico do Windows PowerShell. Esta classe suporta a declaração de fornecedor e fornece um número de propriedades e métodos que estão disponíveis para todos os fornecedores de Windows PowerShell. A classe é invocada pelo `Get-PSProvider` cmdlet para listar todos os fornecedores disponíveis para uma sessão. A implementação deste cmdlet é fornecida pelo Estado da sessão.

> [!NOTE]
> Fornecedores de Windows PowerShell estão disponíveis para todos os âmbitos de idioma do Windows PowerShell.

### <a name="drivecmdletprovider-base-class"></a>Classe DriveCmdletProvider Base

O [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe define um fornecedor de unidade do Windows PowerShell oferece suporte a operações para adicionar novas unidades, remover unidades existentes e a inicialização de unidades padrão. Por exemplo, o fornecedor do sistema de ficheiros fornecido pelo Windows PowerShell inicializa unidades para todos os volumes montados, tais como unidades de disco rígido e unidades de dispositivo de CD/DVD.

Essa classe deriva de [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe base. A tabela seguinte lista os cmdlets expostos pela classe. Para além dos indicados, o `Get-PSDrive` cmdlet (exposto por Estado de sessão) é um cmdlet relacionado que é utilizado para obter unidades disponíveis.

|Cmdlet|Definição|
|------------|----------------|
|`New-PSDrive`|Cria uma nova unidade para a sessão e transmite informações da unidade.|
|`Remove-PSDrive`|Remove uma unidade a partir da sessão.|

### <a name="itemcmdletprovider-base-class"></a>Classe ItemCmdletProvider Base

O [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe define um provedor de item do Windows PowerShell que executa operações nos itens individuais de arquivo de dados e não assume qualquer contêiner ou recursos de navegação. Essa classe deriva de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe base. A tabela seguinte lista os cmdlets expostos pela classe.

|Cmdlet|Definição|
|------------|----------------|
|`Clear-Item`|Limpa o conteúdo atual dos itens na localização especificada e substitui-o com o valor de "clear" especificado pelo fornecedor. Este cmdlet não passa um objeto de saída através do pipeline, a menos que seu `PassThru` parâmetro for especificado.|
|`Get-Item`|Obtém os itens a partir da localização especificada e transmite os objetos resultantes.|
|`Invoke-Item`|Invoca a ação predefinida para o item no caminho especificado.|
|`Set-Item`|Define um item na localização especificada com o valor indicado. Este cmdlet não passa um objeto de saída através do pipeline, a menos que seu `PassThru` parâmetro for especificado.|
|`Resolve-Path`|Resolve os carateres universais para um caminho do Windows PowerShell e informações de caminho de fluxos.|
|`Test-Path`|Testa o caminho especificado e devolve `true` se existir e `false` caso contrário. Este cmdlet é implementado para suportar o `IsContainer` parâmetro para o [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) método.|

### <a name="containercmdletprovider-base-class"></a>Classe ContainerCmdletProvider Base

O [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe define um provedor de contentor do Windows PowerShell que expõe um contentor, para itens de armazenamento de dados, para o usuário. Lembre-se de que um fornecedor de contentor do Windows PowerShell pode ser usado apenas quando existe um contentor (não existem contentores aninhadas) com os itens no mesmo. Se existirem contêineres aninhados, em seguida, deve implementar um fornecedor de navegação do Windows PowerShell.

Essa classe deriva de [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe base. A tabela seguinte define os cmdlets implementados por essa classe.

|Cmdlet|Definição|
|------------|----------------|
|`Copy-Item`|Itens de cópias de uma localização para outra. Este cmdlet não passa um objeto de saída através do pipeline, a menos que seu `PassThru` parâmetro for especificado.|
|`Get-Childitem`|Obtém os itens subordinados na localização especificada e transmite-os como objetos.|
|`New-Item`|Cria novos itens na localização especificada e transmite o objeto resultante.|
|`Remove-Item`|Remove itens da localização especificada.|
|`Rename-Item`|Muda o nome de um item na localização especificada. Este cmdlet não passa um objeto de saída através do pipeline, a menos que seu `PassThru` parâmetro for especificado.|

### <a name="navigationcmdletprovider-base-class"></a>Classe NavigationCmdletProvider Base

O [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe define um provedor de navegação do Windows PowerShell que executa operações para itens que utilizam mais de um contêiner. Essa classe deriva de [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe base. A tabela seguinte lista os cmdlets expostos pela classe.

|Cmdlet|Definição|
|------------|----------------|
|Caminho de combinação|Combina dois caminhos num caminho único, com um delimitador de específica do fornecedor entre caminhos. Este cmdlet transmite as cadeias de caracteres.|
|`Move-Item`|Move itens para a localização especificada. Este cmdlet não passa um objeto de saída através do pipeline, a menos que seu `PassThru` parâmetro for especificado.|

Um cmdlet relacionado é o cmdlet básico do caminho de análise fornecido pelo Windows PowerShell. Este cmdlet pode ser utilizado para analisar um caminho do Windows PowerShell para suportar o `Parent` parâmetro. Ele transmite em fluxo a cadeia do caminho principal.

## <a name="select-provider-interfaces-to-support"></a>Selecione as Interfaces de fornecedor de suporte

Além de derivar de uma das classes bases do Windows PowerShell, o seu fornecedor de Windows PowerShell pode suportar outras funcionalidades, derivando de um ou mais das seguintes interfaces de fornecedor. Esta secção define essas interfaces e os cmdlets suportados por cada uma. Ele descreve os parâmetros para os cmdlets de interface com suporte. Informações de parâmetro de cmdlet estão disponíveis online com o `Get-Command` e `Get-Help` cmdlets.

### <a name="icontentcmdletprovider"></a>IContentCmdletProvider

O [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface define um fornecedor de conteúdos que executa operações no conteúdo de um item de dados. A tabela seguinte lista os cmdlets expostos por esta interface.

|Cmdlet|Definição|
|------------|----------------|
|`Add-Content`|Acrescenta os comprimentos do valor indicado para o conteúdo do item especificado. Este cmdlet não passa um objeto de saída através do pipeline, a menos que seu `PassThru` parâmetro for especificado.|
|`Clear-Content`|Define o conteúdo do item especificado para o valor "clear". Este cmdlet não passa um objeto de saída através do pipeline, a menos que seu `PassThru` parâmetro for especificado.|
|`Get-Content`|Obtém o conteúdo dos itens especificados e transmite os objetos resultantes.|
|`Set-Content`|Substitui o conteúdo existente para os itens especificados. Este cmdlet não passa um objeto de saída através do pipeline, a menos que seu `PassThru` parâmetro for especificado.|

### <a name="ipropertycmdletprovider"></a>IPropertyCmdletProvider

O [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interface define um fornecedor de Windows PowerShell de propriedade que executa operações nas propriedades de itens no arquivo de dados. A tabela seguinte lista os cmdlets expostos por esta interface.

> [!NOTE]
> O `Path` parâmetro sobre estes cmdlets indica um caminho para um item em vez de identificação de uma propriedade.

|Cmdlet|Definição|
|------------|----------------|
|`Clear-ItemProperty`|Define as propriedades dos itens especificados para o valor "clear". Este cmdlet não passa um objeto de saída através do pipeline, a menos que seu `PassThru` parâmetro for especificado.|
|`Get-ItemProperty`|Obtém as propriedades dos itens especificados e transmite os objetos resultantes.|
|`Set-ItemProperty`|Define as propriedades dos itens especificados com os valores indicados. Este cmdlet não passa um objeto de saída através do pipeline, a menos que seu `PassThru` parâmetro for especificado.|

### <a name="idynamicpropertycmdletprovider"></a>IDynamicPropertyCmdletProvider

O [System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) interface, derivada [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider), define um fornecedor de que especifica os parâmetros dinâmicos para seus cmdlets suportados. Este tipo de fornecedor lida com operações para o qual as propriedades podem ser definidas no tempo de execução, por exemplo, uma nova operação de propriedade. Essas operações não são possíveis nos itens a ter definido estaticamente propriedades. A tabela seguinte lista os cmdlets expostos por esta interface.

|Cmdlet|Definição|
|------------|----------------|
|`Copy-ItemProperty`|Copia uma propriedade do item especificado para outro item. Este cmdlet não passa um objeto de saída através do pipeline, a menos que seu `PassThru` parâmetro for especificado.|
|`Move-ItemProperty`|Move uma propriedade do item especificado para o outro item. Este cmdlet não passa um objeto de saída através do pipeline, a menos que seu `PassThru` parâmetro for especificado.|
|`New-ItemProperty`|Cria uma propriedade nos itens especificados e transmite os objetos resultantes.|
|`Remove-ItemProperty`|Remove uma propriedade para os itens especificados.|
|`Rename-ItemProperty`|Muda o nome de uma propriedade dos itens especificados. Este cmdlet não passa um objeto de saída através do pipeline, a menos que seu `PassThru` parâmetro for especificado.|

### <a name="isecuritydescriptorcmdletprovider"></a>ISecurityDescriptorCmdletProvider

O [System.Management.Automation.Provider.Isecuritydescriptorcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ISecurityDescriptorCmdletProvider) interface adiciona funcionalidade de descritor de segurança para um fornecedor. Essa interface permite ao utilizador obter e definir informações de descritor de segurança de um item no arquivo de dados. A tabela seguinte lista os cmdlets expostos por esta interface.

|Cmdlet|Definição|
|------------|----------------|
|`Get-Acl`|Obtém as informações contidas numa lista de controlo de acesso (ACL), que é parte de um descritor de segurança utilizado para proteger os recursos do sistema operativo, por exemplo, um arquivo ou um objeto.|
|`Set-Acl`|Define as informações de uma ACL. É na forma de uma instância do [System.Security.Accesscontrol.Objectsecurity](/dotnet/api/System.Security.AccessControl.ObjectSecurity) sobre o item (NS) designado para o caminho especificado. Este cmdlet pode definir as informações sobre arquivos, chaves e subchaves no Registro ou qualquer outro item do fornecedor, se o fornecedor de Windows PowerShell suporta a definição de informações de segurança.|

## <a name="see-also"></a>Veja Também

[Criar provedores do Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Como funciona o Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[SDK do Windows PowerShell](../windows-powershell-reference.md)