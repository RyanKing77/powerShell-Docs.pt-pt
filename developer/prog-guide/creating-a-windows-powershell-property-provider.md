---
title: Criar um fornecedor de propriedade do PowerShell do Windows | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- property providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], property provider
ms.assetid: a6adca44-b94b-4103-9970-a9b414355e60
caps.latest.revision: 5
ms.openlocfilehash: 6ec0752a9ae06c5c2cdd1a1851caeeff52d8eb74
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081840"
---
# <a name="creating-a-windows-powershell-property-provider"></a>Creating a Windows PowerShell Property Provider (Criar um Fornecedor de Propriedades do Windows PowerShell)

Este tópico descreve como criar um fornecedor que permite ao usuário manipular as propriedades de itens num arquivo de dados. Como conseqüência, este tipo de fornecedor é referido como um fornecedor de propriedade do Windows PowerShell. Por exemplo, o fornecedor de registo fornecido por valores de chave do registo de identificadores do Windows PowerShell como propriedades do item de chave de registo. Este tipo de fornecedor tem de adicionar o [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interface para a implementação da classe .NET.

> [!NOTE]
> Windows PowerShell fornece um arquivo de modelo que pode usar para desenvolver um fornecedor de Windows PowerShell. O arquivo de TemplateProvider.cs está disponível no Microsoft Windows Software Development Kit para Windows Vista e .NET Framework 3.0 Runtime Components. Para obter instruções de transferência, consulte [como instalar o Windows PowerShell e transferir o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> O modelo transferido está disponível na  **\<exemplos do PowerShell >** diretório. Deve fazer uma cópia deste ficheiro e utilize a cópia para criar um novo fornecedor de Windows PowerShell, a remoção de qualquer funcionalidade que não é necessário.
>
> Para obter mais informações sobre outras implementações de provedores do Windows PowerShell, consulte [conceber Windows PowerShell Fornecedor_de_e](./designing-your-windows-powershell-provider.md).

> [!CAUTION]
> Os métodos do seu fornecedor de propriedade devem escrever todos os objetos com o [System.Management.Automation.Provider.Cmdletprovider.Writepropertyobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WritePropertyObject) método.

A lista seguinte contém as secções neste tópico. Se não estiver familiarizado com a escrita de um fornecedor de propriedade do Windows PowerShell, ler estas informações na ordem em que ele é exibido. No entanto, se estiver familiarizado com a escrita de um fornecedor de propriedade do Windows PowerShell, aceda diretamente às informações de que precisa.

- [Definir o fornecedor do Windows PowerShell](#Defining-the-Windows-PowerShell-provider)

- [Definir funcionalidade de Base](#Defining-Base-Functionality)

- [A obter propriedades](#Retrieving-Properties)

- [Os parâmetros dinâmicos para a anexar o `Get-ItemProperty` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-ItemProperty-Cmdlet)

- [Propriedades da definição](#Setting-Properties)

- [Os parâmetros dinâmicos para a anexar o `Set-ItemProperty` Cmdlet](#Attaching-Dynamic-Parameters-for-the-Set-ItemProperty-Cmdlet)

- [Limpar uma propriedade](#Clearing-Properties)

- [Os parâmetros dinâmicos para a anexar o `Clear-ItemProperty` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Clear-ItemProperty-Cmdlet)

- [Criando o provedor do Windows PowerShell](#Building-the-Windows-PowerShell-provider)

## <a name="defining-the-windows-powershell-provider"></a>Definir o fornecedor de Windows PowerShell

Um fornecedor de propriedade tem de criar uma classe do .NET que suporte o [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interface. Segue-se a declaração da classe padrão do ficheiro TemplateProvider.cs fornecido pelo Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration](Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration)]  -->

## <a name="defining-base-functionality"></a>Definir funcionalidade de Base

O [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interface pode ser anexada a qualquer uma das classes base do provedor, com exceção do [ System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe. Adicione a funcionalidade básica que sejam necessários para a classe base que está a utilizar. Para obter mais informações sobre base classes, consulte [conceber Windows PowerShell Fornecedor_de_e](./designing-your-windows-powershell-provider.md).

## <a name="retrieving-properties"></a>A obter propriedades

Para obter as propriedades, o fornecedor tem de implementar o [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) método para oferecer suporte a chamadas a partir do `Get-ItemProperty` cmdlet. Este método obtém as propriedades do item, localizado no caminho especificado internas do fornecedor (totalmente qualificado).

O `providerSpecificPickList` parâmetro indica quais propriedades para recuperar. Se este parâmetro é `null` ou vazio, o método deve recuperar todas as propriedades. Além disso, [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) escreve uma instância de um [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objeto que representa um matriz de propriedades das propriedades obtidas. O método deve retornar nada.

Recomenda-se que a implementação do [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) suporta a expansão de caráter universal de nomes de propriedade para cada elemento na lista de seleção. Para tal, utilize o [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) classe para efetuar a correspondência de padrão de caráter universal.

Eis a implementação padrão da [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) do arquivo TemplateProvider.cs fornecido pelo Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty)]  -->

#### <a name="things-to-remember-about-implementing-getproperty"></a>Coisas a serem lembrados sobre a implementação GetProperty

As seguintes condições podem aplicar-se na implementação [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty):

- Ao definir a classe do provedor, um fornecedor de propriedade do Windows PowerShell poderia declarar capacidades de fornecedor de ExpandWildcards, filtro, inclusão ou exclusão, da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeração. Nestes casos, a implementação do [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) método precisa para se certificar de que o caminho transmitido ao método cumpre os requisitos do especificado capacidades. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriedades.

- Por predefinição, substituições deste método não devem obter um leitor para objetos que estão ocultos do utilizador, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) estiver definida como `true`. Deve ser escrito um erro se o caminho representa um item que está oculto do usuário e [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) está definida como `false`.

## <a name="attaching-dynamic-parameters-to-the-get-itemproperty-cmdlet"></a>Anexar parâmetros dinâmicos para o Cmdlet Get-ItemProperty

O `Get-ItemProperty` cmdlet pode exigir parâmetros adicionais que são especificados dinamicamente no tempo de execução. Para fornecer estes parâmetros dinâmicos, o fornecedor de propriedade do Windows PowerShell tem de implementar o [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) método. O `path` parâmetro indica um caminho interno para o fornecedor totalmente qualificado, enquanto o `providerSpecificPickList` parâmetro especifica as propriedades de específica do fornecedor introduzidas na linha de comandos. Este parâmetro pode ser `null` ou vazia se as propriedades são direcionadas para o cmdlet. Neste caso, esse método retorna um objeto com propriedades e campos com análise atributos semelhantes a uma classe cmdlet ou uma [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O tempo de execução do Windows PowerShell usa o objeto devolvido para adicionar os parâmetros para o cmdlet.

Eis a implementação padrão da [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) do arquivo TemplateProvider.cs fornecido pelo Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters)]  -->

## <a name="setting-properties"></a>Propriedades da definição

Para definir as propriedades, o fornecedor de propriedade do Windows PowerShell tem de implementar o [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) método para oferecer suporte a chamadas a partir do `Set-ItemProperty` cmdlet. Esse método define um ou mais propriedades do item no caminho especificado e substitui as propriedades fornecidas conforme necessário. [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) também escreve uma instância de um [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objeto que representa uma matriz de propriedades de atualizada Propriedades.

Eis a implementação padrão da [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) do arquivo TemplateProvider.cs fornecido pelo Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty)]  -->

#### <a name="things-to-remember-about-implementing-set-itemproperty"></a>Coisas a serem lembrados sobre a implementação ItemProperty de conjunto

As seguintes condições podem aplicar-se para uma implementação do [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty):

- Ao definir a classe do provedor, um fornecedor de propriedade do Windows PowerShell poderia declarar capacidades de fornecedor de ExpandWildcards, filtro, inclusão ou exclusão, da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeração. Nestes casos, a implementação do [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) método tem de garantir que o caminho transmitido ao método cumpre os requisitos do especificado capacidades. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriedades.

- Por predefinição, substituições deste método não devem obter um leitor para objetos que estão ocultos do utilizador, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) estiver definida como `true`. Deve ser escrito um erro se o caminho representa um item que está oculto do usuário e [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) está definida como `false`.

- Sua implementação do [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) deve chamar o método [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e verifique se o valor de retorno antes de fazer alterações ao arquivo de dados. Este método é usado para confirmar a execução de uma operação quando é efetuada uma alteração de estado do sistema, por exemplo, mudar o nome de ficheiros. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) envia o nome do recurso a ser alterado para o utilizador, com o tempo de execução do Windows PowerShell e o tratamento de definições de linha de comandos ou variáveis de preferência na determinação o que deverá ser apresentado.

  Após a chamada para [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) devolve `true`, se podem ser feitas modificações de sistema potencialmente perigosas, o [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) método deve chamar o [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) método. Este método envia uma mensagem de confirmação ao utilizador para permitir que os comentários adicionais indicar que a operação deve ser contínuo.

## <a name="attaching-dynamic-parameters-for-the-set-itemproperty-cmdlet"></a>Anexar parâmetros dinâmicos para o Cmdlet Set-ItemProperty

O `Set-ItemProperty` cmdlet pode exigir parâmetros adicionais que são especificados dinamicamente no tempo de execução. Para fornecer estes parâmetros dinâmicos, o fornecedor de propriedade do Windows PowerShell tem de implementar o [System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) método. Esse método retorna um objeto com propriedades e campos com análise atributos semelhantes a uma classe cmdlet ou uma [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O `null` valor pode ser devolvido se não existem parâmetros dinâmicos devem ser adicionadas.

Eis a implementação padrão da [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) do arquivo TemplateProvider.cs fornecido pelo Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters)]  -->

## <a name="clearing-properties"></a>Propriedades de limpar

Para limpar as propriedades, o fornecedor de propriedade do Windows PowerShell tem de implementar o [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) método para oferecer suporte a chamadas a partir do `Clear-ItemProperty` cmdlet. Este método define as propriedades de um ou mais para o item, localizado no caminho especificado.

Eis a implementação padrão da [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) do arquivo TemplateProvider.cs fornecido pelo Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty](Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty)]  -->

#### <a name="thing-to-remember-about-implementing-clearproperty"></a>Ponto a ser lembrado sobre a implementação ClearProperty

As seguintes condições podem aplicar-se na implementação [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty):

- Ao definir a classe do provedor, um fornecedor de propriedade do Windows PowerShell poderia declarar capacidades de fornecedor de ExpandWildcards, filtro, inclusão ou exclusão, da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeração. Nestes casos, a implementação do [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) método precisa para se certificar de que o caminho transmitido ao método cumpre os requisitos do especificado capacidades. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriedades.

- Por predefinição, substituições deste método não devem obter um leitor para objetos que estão ocultos do utilizador, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) estiver definida como `true`. Deve ser escrito um erro se o caminho representa um item que está oculto do usuário e [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) está definida como `false`.

- Sua implementação do [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) deve chamar o método [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess ](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e verifique se o valor de retorno antes de fazer alterações ao arquivo de dados. Este método é usado para confirmar a execução de uma operação antes de uma alteração é feita para o estado do sistema, tais como limpar o conteúdo. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) envia o nome do recurso a ser alterados ao usuário, com o tempo de execução do Windows PowerShell tendo em conta as definições de linha de comandos ou variáveis de preferência em determinar o que deverá ser apresentado.

  Após a chamada para [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) devolve `true`, se podem ser feitas modificações de sistema potencialmente perigosas, o [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) método deve chamar o [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) método. Este método envia uma mensagem de confirmação ao utilizador para permitir que os comentários adicionais indicar que a operação potencialmente perigosa deve ser contínuo.

## <a name="attaching-dynamic-parameters-to-the-clear-itemproperty-cmdlet"></a>Anexar parâmetros dinâmicos para o Cmdlet Clear ItemProperty

O `Clear-ItemProperty` cmdlet pode exigir parâmetros adicionais que são especificados dinamicamente no tempo de execução. Para fornecer estes parâmetros dinâmicos, o fornecedor de propriedade do Windows PowerShell tem de implementar o [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) método. Esse método retorna um objeto com propriedades e campos com análise atributos semelhantes a uma classe cmdlet ou uma [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O `null` valor pode ser devolvido se não existem parâmetros dinâmicos devem ser adicionadas.

Eis a implementação padrão da [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) do arquivo TemplateProvider.cs fornecido pelo Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters)]  -->

## <a name="building-the-windows-powershell-provider"></a>Criando o provedor do Windows PowerShell

Ver [como registar os Cmdlets, fornecedores e alojar aplicações](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="see-also"></a>Veja Também

[Fornecedor de Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Fornecedor do design do Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Como registar os Cmdlets, fornecedores e alojar aplicações](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)