---
title: Criar um fornecedor de PowerShell do Windows básico | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- base provider [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], base provider
ms.assetid: 11eeea41-15c8-47ad-9016-0f4b72573305
caps.latest.revision: 7
ms.openlocfilehash: 19cc3817016d96e1412a5f3506e9d694ba55b48d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082078"
---
# <a name="creating-a-basic-windows-powershell-provider"></a>Creating a Basic Windows PowerShell Provider (Criar um Fornecedor Básico do Windows PowerShell)

Este tópico é o ponto de partida para aprender como criar um fornecedor de Windows PowerShell. O fornecedor básico descrito aqui fornece métodos para iniciar e parar o fornecedor e, apesar deste fornecedor não fornece um meio para aceder a um arquivo de dados ou para obter ou definir os dados no arquivo de dados, ela fornece a funcionalidade básica que sejam necessários para todos os fornecedores.

Como mencionado anteriormente, o fornecedor básico descrito aqui implementa métodos para iniciar e parar o fornecedor. O tempo de execução do Windows PowerShell chama esses métodos para inicializar e uninitialize o fornecedor.

> [!NOTE]
> Pode encontrar um exemplo deste fornecedor no ficheiro AccessDBSampleProvider01.cs fornecido pelo Windows PowerShell.

As secções neste tópico incluem o seguinte:

- [Definir a classe de fornecedor do PowerShell do Windows](#Defining-the-Windows-PowerShell-Provider-Class)

- [Definir informações de estado de específica do fornecedor](#Defining-Provider-Specific-State-Information)

- [A inicializar o fornecedor](#Initializing-the-Provider)

- [Iniciar parâmetros dinâmicos](#Start-Dynamic-Parameters)

- [Uninitializing o fornecedor](#Uninitializing-the-Provider)

- [Exemplo de código](#Code-Sample)

- [Teste o fornecedor do Windows PowerShell](#Testing-the-Windows-PowerShell-Provider)

## <a name="defining-the-windows-powershell-provider-class"></a>Definir a classe de fornecedor do PowerShell do Windows

A primeira etapa na criação de um fornecedor de Windows PowerShell é definir sua classe do .NET. Este fornecedor básica define uma classe chamada `AccessDBProvider` que deriva do [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe base.

É recomendável que coloque suas classes de fornecedor numa `Providers` espaço de nomes do seu espaço de nomes de API, por exemplo, xxx. PowerShell.Providers. Esse provedor usa o `Microsoft.Samples.PowerShell.Provider` espaço de nomes, em que executar todas as amostras de fornecedor de Windows PowerShell.

> [!NOTE]
> A classe de um fornecedor de Windows PowerShell tem de ser marcada explicitamente como pública. Classes não marcadas como pública serão predefinido para interno e não serão encontrados pelo tempo de execução do Windows PowerShell.

Segue-se a definição de classe deste provedor básico:

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L23-L24 "AccessDBProviderSample01.cs")]

Logo antes da definição de classe, deve declarar o [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atributo, com a sintaxe [CmdletProvider()].

Pode definir palavras-chave de atributo ainda mais declarar a classe, se necessário. Tenha em atenção que o [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atributo declarado aqui inclui dois parâmetros. O primeiro parâmetro de atributo especifica o nome amigável do padrão para o fornecedor, que o usuário pode modificar mais tarde. O segundo parâmetro especifica os recursos definidos pelo Windows PowerShell que o fornecedor expõe o tempo de execução do Windows PowerShell durante o processamento do comando. Os valores possíveis para as funcionalidades de fornecedor são definidos pelos [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeração. Porque se trata de um fornecedor de base, ele oferece suporte sem recursos.

> [!NOTE]
> O nome completamente qualificado do fornecedor de Windows PowerShell inclui o nome do assembly e outros atributos determinados pelo Windows PowerShell no registo do fornecedor.

## <a name="defining-provider-specific-state-information"></a>Definir informações de estado de específica do fornecedor

O [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe base e todas as classes derivadas são consideradas sem monitoração de estado porque o tempo de execução do Windows PowerShell cria instâncias do fornecedor apenas conforme necessário. Por conseguinte, se o seu fornecedor de precisar controlo total e a manutenção de estado para específica do fornecedor de dados, devem derivar uma classe a partir da [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) classe. Sua classe derivada deve definir os membros necessários para manter o estado, para que os dados específicos de fornecedor podem ser acedidos quando o tempo de execução do Windows PowerShell chama o [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) método para inicializar o fornecedor.

Um fornecedor de Windows PowerShell também pode manter o estado da ligação com base em. Para obter mais informações sobre como manter o estado da ligação, veja [criar um fornecedor de unidade do PowerShell](./creating-a-windows-powershell-drive-provider.md).

## <a name="initializing-the-provider"></a>A inicializar o fornecedor

Para inicializar o fornecedor, as chamadas de tempo de execução do Windows PowerShell a [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) método quando o Windows PowerShell é iniciado. Na maior parte, o seu fornecedor pode utilizar a implementação padrão deste método, que simplesmente retorna o [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) objeto que descreve o seu fornecedor. No entanto, no caso em que pretende adicionar informações adicionais de inicialização, deve implementar sua própria [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) método que retorna uma versão modificada do [ System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) objeto que é passado para o seu fornecedor. Em geral, esse método deve retornar fornecido [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) objeto passado para ele ou um modificados [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) de objeto que contém outras informações de inicialização.

Este fornecedor básica não substitui este método. No entanto, o código seguinte mostra a implementação padrão deste método:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStart](Msh_samplesaccessdbprov01#accessdbprov01ProviderStart)]  -->

O fornecedor pode manter o estado de informações específicas do fornecedor, conforme descrito em [Defining específicas do fornecedor de dados de estado](#Defining-Provider-Specific-State-Information). Neste caso, sua implementação tem de substituir a [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) método para retornar uma instância da classe derivada.

## <a name="start-dynamic-parameters"></a>Iniciar parâmetros dinâmicos

Sua implementação do fornecedor do [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) método pode requerer a parâmetros adicionais. Neste caso, o fornecedor deve substituir a [System.Management.Automation.Provider.Cmdletprovider.Startdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters) método e retornar um objeto com propriedades e campos com análise atributos semelhante a um classe cmdlet ou uma [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto.

Este fornecedor básica não substitui este método. No entanto, o código seguinte mostra a implementação padrão deste método:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters](Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters)]  -->

## <a name="uninitializing-the-provider"></a>Uninitializing o fornecedor

Para libertar recursos que utiliza o fornecedor de Windows PowerShell, o fornecedor deve implementar sua própria [System.Management.Automation.Provider.Cmdletprovider.Stop*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop) método. Este método é chamado pelo tempo de execução do Windows PowerShell para uninitialize o fornecedor de fechamento de uma sessão.

Este fornecedor básica não substitui este método. No entanto, o código seguinte mostra a implementação padrão deste método:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStop](Msh_samplesaccessdbprov01#accessdbprov01ProviderStop)]  -->

## <a name="code-sample"></a>Exemplo de código

Para o código de exemplo completo, consulte [exemplo de código AccessDbProviderSample01](./accessdbprovidersample01-code-sample.md).

## <a name="testing-the-windows-powershell-provider"></a>Teste o fornecedor do Windows PowerShell

Assim que o seu fornecedor de Windows PowerShell foi registado com o Windows PowerShell, pode testá-lo ao executar os cmdlets suportados na linha de comandos. Para este fornecedor básica, execute o novo shell e utilize o `Get-PSProvider` cmdlet para obter a lista de fornecedores e certifique-se de que o fornecedor de AccessDb está presente.

```powershell
Get-PSProvider
```

É apresentado o seguinte resultado:

```output
Name                 Capabilities                  Drives
----                 ------------                  ------
AccessDb             None                          {}
Alias                ShouldProcess                 {Alias}
Environment          ShouldProcess                 {Env}
FileSystem           Filter, ShouldProcess         {C, Z}
Function             ShouldProcess                 {function}
Registry             ShouldProcess                 {HKLM, HKCU}
```

## <a name="see-also"></a>Veja Também

[Criar provedores do Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Estruturar o seu fornecedor do Windows PowerShell](./designing-your-windows-powershell-provider.md)