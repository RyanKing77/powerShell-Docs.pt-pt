---
title: Criar um fornecedor de Item de PowerShell do Windows | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- item providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], item provider
ms.assetid: a5a304ce-fc99-4a5b-a779-de7d85e031fe
caps.latest.revision: 6
ms.openlocfilehash: f2c9e10f0dc392399cf062500b7f28b3d1c07f6e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081874"
---
# <a name="creating-a-windows-powershell-item-provider"></a>Creating a Windows PowerShell Item Provider (Criar um Fornecedor de Itens do Windows PowerShell)

Este tópico descreve como criar um fornecedor de Windows PowerShell que pode manipular os dados num arquivo de dados. Neste tópico, os elementos de dados no arquivo são referidos para como "itens" dos dados armazenar. Como conseqüência, um provedor que pode manipular os dados no arquivo é referido como um fornecedor de item do Windows PowerShell.

> [!NOTE]
> Pode transferir o C# ficheiro de origem (AccessDBSampleProvider03.cs) para este fornecedor com o Microsoft Windows Software Development Kit para Windows Vista e o .NET Framework 3.0 Runtime Components. Para obter instruções de transferência, consulte [como instalar o Windows PowerShell e transferir o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Os arquivos de fonte transferido estão disponíveis no  **\<exemplos do PowerShell >** diretório.
>
> Para obter mais informações sobre outras implementações de provedores do Windows PowerShell, consulte [conceber Windows PowerShell Fornecedor_de_e](./designing-your-windows-powershell-provider.md).

O fornecedor de item do Windows PowerShell descrito neste tópico obtém os itens de dados de um banco de dados do Access. Neste caso, "itens" é uma tabela na base de dados de acesso ou uma linha numa tabela.

A lista seguinte contém as secções neste tópico. Se não estiver familiarizado com a escrita de um fornecedor de item do Windows PowerShell, leia estas secções pela ordem em que aparecem. No entanto, se estiver familiarizado com a escrita de um fornecedor de item do Windows PowerShell, aceda diretamente às informações de que precisa:

- [Definir a classe de fornecedor do Windows PowerShell Item](#Defining-the-Windows-PowerShell-Item-Provider-Class)

- [Definir funcionalidade de Base](#Defining-Base-Functionality)

- [A verificação de validade de caminho](#Checking-for-Path-Validity)

- [Determinar se existe um Item](#Determining-if-an-Item-Exists)

- [Os parâmetros dinâmicos para a anexar o `Test-Path` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Test-Path-Cmdlet)

- [Um Item a obter](#Retrieving-an-Item)

- [Os parâmetros dinâmicos para a anexar o `Get-Item` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-Item-Cmdlet)

- [A definição de um Item](#Setting-an-Item)

- [Os parâmetros dinâmicos para a anexar o `Set-Item` Cmdlet](#Retrieving-Dynamic-Parameters-for-SetItem)

- [Desmarcar um Item](#Clearing-an-Item)

- [Anexar parâmetros dinâmicos para o Cmdlet Clear-Item](#Retrieve-Dynamic-Parameters-for-ClearItem)

- [Executar uma ação padrão de um Item](#Performing-a-Default-Action-for-an-Item)

- [A obter os parâmetros dinâmicos para InvokeDefaultAction](#Retrieve-Dynamic-Parameters-for-InvokeDefaultAction)

- [Implementar Classes e métodos auxiliares](#Implementing-Helper-Methods-and-Classes)

- [Exemplo de código](#Code-Sample)

- [Definir tipos de objeto e formatação](#Defining-Object-Types-and-Formatting)

- [Criando o provedor do Windows PowerShell](#Building-the-Windows-PowerShell-provider)

- [Teste o fornecedor do Windows PowerShell](#Testing-the-Windows-PowerShell-provider)

## <a name="defining-the-windows-powershell-item-provider-class"></a>Definir a classe de fornecedor do Windows PowerShell Item

Um provedor de item do Windows PowerShell tem de definir uma classe do .NET que deriva de [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe base. Segue-se a definição de classe para o fornecedor de item descrita nesta secção.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L34-L36 "AccessDBProviderSample03.cs")]

Tenha em atenção que, desta definição, de classe a [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atributo inclui dois parâmetros. O primeiro parâmetro especifica um nome amigável para o fornecedor que é utilizado pelo Windows PowerShell. O segundo parâmetro especifica os recursos específicos do Windows PowerShell que o fornecedor expõe o tempo de execução do Windows PowerShell durante o processamento do comando. Para este fornecedor, não há nenhum adicionadas capacidades específicas do Windows PowerShell.

## <a name="defining-base-functionality"></a>Definir funcionalidade de Base

Conforme descrito em [Design Windows PowerShell Fornecedor_de_e](./designing-your-windows-powershell-provider.md), o [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe deriva de outras classes que fornecidos diferentes funcionalidade de fornecedor. Um provedor de item do Windows PowerShell, por conseguinte, tem de definir todas as funcionalidades fornecidas por essas classes.

Para obter mais informações sobre como implementar a funcionalidade para adicionar informações de inicialização de específico da sessão e para liberar os recursos utilizados pelo fornecedor, consulte [criar um fornecedor de PowerShell básica do Windows](./creating-a-basic-windows-powershell-provider.md). No entanto, a maioria dos fornecedores, incluindo o fornecedor descrito aqui, podem utilizar a implementação padrão dessa funcionalidade fornecida pelo Windows PowerShell.

Antes do fornecedor de item do Windows PowerShell pode manipular os itens na loja, tem de implementar os métodos do [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe para aceder ao arquivo de dados base. Para obter mais informações sobre a implementação dessa classe, consulte [criar um fornecedor de unidade do Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

## <a name="checking-for-path-validity"></a>A verificação de validade de caminho

Quando está à procura de um item de dados, o tempo de execução do Windows PowerShell furnishes um caminho do Windows PowerShell para o fornecedor, conforme definido na secção "Conceitos de se PSPath" [como o Windows PowerShell funciona](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58). Um fornecedor de item do Windows PowerShell tem de verificar a validade sintática e semântica de qualquer caminho passado para ele, implementando o [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) método. Este método devolve `true` se o caminho é válido, e `false` caso contrário. Estar ciente de que a implementação desse método não deve verificar a existência do item no caminho, mas apenas que o caminho é sintaticamente e semanticamente correto.

Eis a implementação do [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) método para este fornecedor. Observe que essa implementação chama um método de programa auxiliar de NormalizePath para converter todos os separadores no caminho para uma uniforme.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L274-L298 "AccessDBProviderSample03.cs")]

## <a name="determining-if-an-item-exists"></a>Determinar se existe um Item

Depois de verificar o caminho, o tempo de execução do Windows PowerShell tem de determinar se existe um item de dados em que o caminho. Para suportar este tipo de consulta, o fornecedor de item do Windows PowerShell implementa a [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) método. Este método devolve `true` um item for encontrado no caminho especificado e `false` (predefinida) caso contrário.

Eis a implementação do [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) método para este fornecedor. Observe que esse método chama os métodos de programa auxiliar PathIsDrive ChunkPath e GetTable e utiliza um fornecedor definido DatabaseTableInfo objeto.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L229-L267 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-itemexists"></a>Coisas a serem lembrados sobre a implementação ItemExists

As seguintes condições podem aplicar-se na implementação [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists):

- Ao definir a classe do provedor, um provedor de item do Windows PowerShell poderia declarar capacidades de fornecedor de ExpandWildcards, filtro, inclusão ou exclusão, da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)enumeração. Nestes casos, a implementação do [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) método tem de garantir que o caminho transmitido ao método cumpre os requisitos de recursos especificados. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriedades.

- A implementação desse método deve lidar com qualquer outra forma de acesso para o item que pode tornar o item visível ao utilizador. Por exemplo, se um utilizador tem acesso de escrita para um ficheiro através do fornecedor do sistema de ficheiros (fornecido pelo Windows PowerShell), mas não acesso de leitura, o ficheiro ainda existe e [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) retorna `true`. A implementação pode requerer a verificação de um item de principal para ver se o item subordinado pode ser enumerado.

## <a name="attaching-dynamic-parameters-to-the-test-path-cmdlet"></a>Anexar parâmetros dinâmicos para o Cmdlet Test-Path

Por vezes, o `Test-Path` cmdlet que chama [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) requer parâmetros adicionais que são especificados dinamicamente no tempo de execução. Para fornecer estes parâmetros dinâmicos do PowerShell de Windows item fornecedor tem de implementar o [System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) método. Esse método obtém os parâmetros dinâmicos para o item no caminho indicado e retorna um objeto com propriedades e campos com análise atributos semelhantes a uma classe cmdlet ou uma [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O tempo de execução do Windows PowerShell usa o objeto devolvido para adicionar os parâmetros para o `Test-Path` cmdlet.

Este fornecedor de item do Windows PowerShell não implementa esse método. No entanto, o código a seguir é a implementação do padrão desse método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovideritemexistdynamicparameters](Msh_samplestestcmdlets#testprovideritemexistdynamicparameters)]  -->

## <a name="retrieving-an-item"></a>Um Item a obter

Para obter um item, o fornecedor de item do Windows PowerShell tem de substituir [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) método para oferecer suporte a chamadas a partir do `Get-Item` cmdlet. Este método escreve o item com o [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) método.

Eis a implementação do [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) método para este fornecedor. Tenha em atenção que este método utiliza os métodos de programa auxiliar GetTable e GetRow para recuperar itens que estão a tabelas do banco de dados de acesso ou linhas numa tabela de dados.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L132-L163 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-getitem"></a>Coisas a serem lembrados sobre a implementação GetItem

As seguintes condições podem aplicar-se para uma implementação do [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem):

- Ao definir a classe do provedor, um provedor de item do Windows PowerShell poderia declarar capacidades de fornecedor de ExpandWildcards, filtro, inclusão ou exclusão, da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)enumeração. Nestes casos, a implementação do [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) tem de garantir que o caminho transmitido ao método atende a esses requisitos. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriedades.

- Por predefinição, substituições deste método não devem obter objetos que geralmente estão ocultos do utilizador, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) estiver definida como `true`. Por exemplo, o [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) método para as verificações de fornecedor do sistema de ficheiros a [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriedade antes de ele tenta chamar [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) para oculto ou ficheiros de sistema.

## <a name="attaching-dynamic-parameters-to-the-get-item-cmdlet"></a>Anexar parâmetros dinâmicos para o Cmdlet Get-Item

Por vezes, o `Get-Item` cmdlet requer parâmetros adicionais que são especificados dinamicamente no tempo de execução. Para fornecer estes parâmetros dinâmicos do PowerShell de Windows item fornecedor tem de implementar o [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) método. Esse método obtém os parâmetros dinâmicos para o item no caminho indicado e retorna um objeto com propriedades e campos com análise atributos semelhantes a uma classe cmdlet ou uma [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O tempo de execução do Windows PowerShell usa o objeto devolvido para adicionar os parâmetros para o `Get-Item` cmdlet.

Este fornecedor não implementa esse método. No entanto, o código a seguir é a implementação do padrão desse método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetitemdynamicparameters](Msh_samplestestcmdlets#testprovidergetitemdynamicparameters)]  -->

## <a name="setting-an-item"></a>A definição de um Item

Para definir um item, o fornecedor de item do Windows PowerShell tem de substituir a [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) método para oferecer suporte a chamadas a partir do `Set-Item` cmdlet. Este método define o valor do item no caminho especificado.

Este fornecedor não fornece uma substituição para o [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) método. No entanto, segue-se a implementação do padrão desse método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitem](Msh_samplestestcmdlets#testprovidersetitem)]  -->

#### <a name="things-to-remember-about-implementing-setitem"></a>Coisas a serem lembrados sobre a implementação SetItem

As seguintes condições podem aplicar-se na implementação [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem):

- Ao definir a classe do provedor, um provedor de item do Windows PowerShell poderia declarar capacidades de fornecedor de ExpandWildcards, filtro, inclusão ou exclusão, da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)enumeração. Nestes casos, a implementação do [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) tem de garantir que o caminho transmitido ao método atende a esses requisitos. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriedades.

- Por predefinição, substituições desse método devem não defina ou gravar os objetos que estão ocultos do utilizador, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) estiver definida como `true`. Um erro deve ser enviado para o [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) método se o caminho representa um item oculto e [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) está definido como `false`.

- Sua implementação do [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) deve chamar o método [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)e verifique se o valor de retorno antes de fazer alterações ao arquivo de dados. Este método é usado para confirmar a execução de uma operação quando é efetuada uma alteração ao arquivo de dados, por exemplo, a eliminar ficheiros. O [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) método envia o nome do recurso a ser alterados ao usuário, com o tempo de execução do Windows PowerShell tendo em conta todas as definições de linha de comandos ou variáveis de preferência de determinar o que deverá ser apresentado.

  Após a chamada para [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) devolve `true`, o [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)método deve chamar o [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) método. Este método envia uma mensagem ao utilizador para permitir que os comentários verificar se a operação deve ser contínuo. A chamada para [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) permite que uma verificação adicional para as modificações de sistema potencialmente perigosas.

## <a name="retrieving-dynamic-parameters-for-setitem"></a>A obter os parâmetros dinâmicos para SetItem

Por vezes, o `Set-Item` cmdlet requer parâmetros adicionais que são especificados dinamicamente no tempo de execução. Para fornecer estes parâmetros dinâmicos do PowerShell de Windows item fornecedor tem de implementar o [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) método. Esse método obtém os parâmetros dinâmicos para o item no caminho indicado e retorna um objeto com propriedades e campos com análise atributos semelhantes a uma classe cmdlet ou uma [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O tempo de execução do Windows PowerShell usa o objeto devolvido para adicionar os parâmetros para o `Set-Item` cmdlet.

Este fornecedor não implementa esse método. No entanto, o código a seguir é a implementação do padrão desse método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitemdynamicparameters](Msh_samplestestcmdlets#testprovidersetitemdynamicparameters)]  -->

## <a name="clearing-an-item"></a>Desmarcar um Item

Para limpar um item, o fornecedor de item do Windows PowerShell implementa o [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) método para oferecer suporte a chamadas a partir do `Clear-Item` cmdlet. Este método apaga o item de dados no caminho especificado.

Este fornecedor não implementa esse método. No entanto, o código a seguir é a implementação do padrão desse método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitem](Msh_samplestestcmdlets#testproviderclearitem)]  -->

#### <a name="things-to-remember-about-implementing-clearitem"></a>Coisas a serem lembrados sobre a implementação ClearItem

As seguintes condições podem aplicar-se para uma implementação do [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem):

- Ao definir a classe do provedor, um provedor de item do Windows PowerShell poderia declarar capacidades de fornecedor de ExpandWildcards, filtro, inclusão ou exclusão, da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)enumeração. Nestes casos, a implementação do [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) tem de garantir que o caminho transmitido ao método atende a esses requisitos. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriedades.

- Por predefinição, substituições desse método devem não defina ou gravar os objetos que estão ocultos do utilizador, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) estiver definida como `true`. Um erro deve ser enviado para o [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) método se o caminho representa um item que está oculto do usuário e [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) está definido como `false`.

- Sua implementação do [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) deve chamar o método [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)e verifique se o valor de retorno antes de fazer alterações ao arquivo de dados. Este método é usado para confirmar a execução de uma operação quando é efetuada uma alteração ao arquivo de dados, por exemplo, a eliminar ficheiros. O [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) método envia o nome do recurso a ser alterado para o usuário, com o tempo de execução do Windows PowerShell e lidar com as definições da linha de comandos ou preferência variáveis de determinar o que deverá ser apresentado.

  Após a chamada para [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) devolve `true`, o [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)método deve chamar o [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) método. Este método envia uma mensagem ao utilizador para permitir que os comentários verificar se a operação deve ser contínuo. A chamada para [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) permite que uma verificação adicional para as modificações de sistema potencialmente perigosas.

## <a name="retrieve-dynamic-parameters-for-clearitem"></a>Obter os parâmetros dinâmicos para ClearItem

Por vezes, o `Clear-Item` cmdlet requer parâmetros adicionais que são especificados dinamicamente no tempo de execução. Para fornecer estes parâmetros dinâmicos do PowerShell de Windows item fornecedor tem de implementar o [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) método. Esse método obtém os parâmetros dinâmicos para o item no caminho indicado e retorna um objeto com propriedades e campos com análise atributos semelhantes a uma classe cmdlet ou uma [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O tempo de execução do Windows PowerShell usa o objeto devolvido para adicionar os parâmetros para o `Clear-Item` cmdlet.

Este fornecedor de item não implementa esse método. No entanto, o código a seguir é a implementação do padrão desse método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitemdynamicparameters](Msh_samplestestcmdlets#testproviderclearitemdynamicparameters)]  -->

## <a name="performing-a-default-action-for-an-item"></a>Executar uma ação padrão de um Item

Um fornecedor de item do Windows PowerShell pode implementar o [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) método para oferecer suporte a chamadas do `Invoke-Item` cmdlet, que permite ao fornecedor para Execute uma ação padrão para o item no caminho especificado. Por exemplo, o fornecedor do sistema de ficheiros poderá utilizar este método para chamar ShellExecute para um item específico.

Este fornecedor não implementa esse método. No entanto, o código a seguir é a implementação do padrão desse método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultaction](Msh_samplestestcmdlets#testproviderinvokedefaultaction)]  -->

#### <a name="things-to-remember-about-implementing-invokedefaultaction"></a>Coisas a serem lembrados sobre a implementação InvokeDefaultAction

As seguintes condições podem aplicar-se para uma implementação do [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction):

- Ao definir a classe do provedor, um provedor de item do Windows PowerShell poderia declarar capacidades de fornecedor de ExpandWildcards, filtro, inclusão ou exclusão, da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)enumeração. Nestes casos, a implementação do [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) tem de garantir que o caminho transmitido ao método atende a esses requisitos. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriedades.

- Por predefinição, substituições desse método devem não defina ou gravar objetos ocultados do utilizador, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) estiver definida como `true`. Um erro deve ser enviado para o [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) método se o caminho representa um item que está oculto do usuário e [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) está definido como `false`.

## <a name="retrieve-dynamic-parameters-for-invokedefaultaction"></a>Obter os parâmetros dinâmicos para InvokeDefaultAction

Por vezes, o `Invoke-Item` cmdlet requer parâmetros adicionais que são especificados dinamicamente no tempo de execução. Para fornecer estes parâmetros dinâmicos do PowerShell de Windows item fornecedor tem de implementar o [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) método. Esse método obtém os parâmetros dinâmicos para o item no caminho indicado e retorna um objeto com propriedades e campos com análise atributos semelhantes a uma classe cmdlet ou uma [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O tempo de execução do Windows PowerShell usa o objeto devolvido para adicionar os parâmetros dinâmicos para a `Invoke-Item` cmdlet.

Este fornecedor de item não implementa esse método. No entanto, o código a seguir é a implementação do padrão desse método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters](Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters)]  -->

## <a name="implementing-helper-methods-and-classes"></a>Implementar Classes e métodos auxiliares

Este fornecedor de item implementa vários métodos auxiliares e métodos definidos pelo Windows PowerShell de substituição de classes que são utilizadas pelo público. O código para essas classes e métodos auxiliares são mostrados na [exemplo de código](#Code-Sample) secção.

### <a name="normalizepath-method"></a>Método NormalizePath

Este fornecedor de item implementa um método de programa auxiliar de NormalizePath para garantir que o caminho tem um formato consistente. O formato especificado utiliza uma barra invertida (\\) como um separador.

### <a name="pathisdrive-method"></a>Método PathIsDrive

Este fornecedor de item implementa um método de programa auxiliar de PathIsDrive para determinar se o caminho especificado é, na verdade, o nome da unidade.

### <a name="chunkpath-method"></a>Método ChunkPath

Este fornecedor de item implementa um método de programa auxiliar de ChunkPath divide o caminho especificado para que o fornecedor pode identificar os respetivos elementos individuais. Ele retorna que uma matriz é composto pelos elementos de caminho.

### <a name="gettable-method"></a>Método getTable

Este fornecedor de item implementa o método auxiliar GetTables que retorna um objeto de DatabaseTableInfo que representa informações sobre a tabela especificada na chamada.

### <a name="getrow-method"></a>Método GetRow

O [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) método deste fornecedor de item chama o método de programa auxiliar de GetRows. Esse método auxiliar obtém um objeto de DatabaseRowInfo que representa informações sobre a linha especificada na tabela.

### <a name="databasetableinfo-class"></a>Classe de DatabaseTableInfo

Este fornecedor de item define uma classe de DatabaseTableInfo que representa uma coleção de informações numa tabela de dados na base de dados. Esta classe é semelhante para o [System.IO.Directoryinfo](/dotnet/api/System.IO.DirectoryInfo) classe.

O provedor de item de exemplo define um método de DatabaseTableInfo.GetTables que retorna uma coleção de objetos de informações de tabela definindo as tabelas na base de dados. Esse método inclui um bloco try/catch para garantir que qualquer erro de base de dados aparece como uma linha com entradas de zero.

### <a name="databaserowinfo-class"></a>Classe de DatabaseRowInfo

Este fornecedor de item define a classe de programa auxiliar de DatabaseRowInfo que representa uma linha numa tabela do banco de dados. Esta classe é semelhante para o [FILEINFO](/dotnet/api/System.IO.FileInfo) classe.

O provedor de exemplo define um método de DatabaseRowInfo.GetRows para retornar uma coleção de objetos de informações da linha da tabela especificada. Esse método inclui um bloco try/catch para interceptar exceções. Todos os erros irão resultar em nenhuma informação de linha.

## <a name="code-sample"></a>Exemplo de código

Para o código de exemplo completo, consulte [exemplo de código AccessDbProviderSample03](./accessdbprovidersample03-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definir tipos de objeto e formatação

Ao escrever um fornecedor, poderá ser necessário adicionar membros a objetos existentes ou definir novos objetos. Quando terminar, crie um ficheiro de tipos que pode utilizar o Windows PowerShell para identificar os membros do objeto e um ficheiro de formato que define como o objeto é apresentado. Para obter mais informações sobre, consulte [estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Criando o provedor do Windows PowerShell

Ver [como registar os Cmdlets, fornecedores e alojar aplicações](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Teste o fornecedor de Windows PowerShell

Quando este fornecedor de item do Windows PowerShell é registrado com o Windows PowerShell, pode apenas testar o básico e funcionalidade do fornecedor de unidade. Para testar a manipulação de itens, também deve implementar a funcionalidade de contentor descrita [implementando um provedor de PowerShell do contentor Windows](./creating-a-windows-powershell-container-provider.md).

## <a name="see-also"></a>Veja Também

[SDK do Windows PowerShell](../windows-powershell-reference.md)

[Guia do programador do Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Criar provedores do Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Estruturar o fornecedor do Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Como funciona o Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Criar um fornecedor de contentor Windows PowerShell](./creating-a-windows-powershell-container-provider.md)

[Criar um fornecedor de unidade o Windows PowerShell](./creating-a-windows-powershell-drive-provider.md)

[Como registar os Cmdlets, fornecedores e alojar aplicações](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)