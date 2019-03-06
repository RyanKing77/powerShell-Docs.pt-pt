---
title: Criar um fornecedor de conteúdo do PowerShell do Windows | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- content providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], content provider
ms.assetid: 3da88ff9-c4c7-4ace-aa24-0a29c8cfa060
caps.latest.revision: 6
ms.openlocfilehash: 5e35d2fdfa4c6bd70c1b69ca1f357ee8d8ebcdc4
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429980"
---
# <a name="creating-a-windows-powershell-content-provider"></a>Creating a Windows PowerShell Content Provider (Criar um Fornecedor de Conteúdos do Windows PowerShell)

Este tópico descreve como criar um fornecedor de Windows PowerShell que permite ao usuário manipular o conteúdo dos itens de um arquivo de dados. Como conseqüência, um provedor que pode manipular o conteúdo de itens é referido como um fornecedor de conteúdos do Windows PowerShell.

> [!NOTE]
> Pode transferir o C# ficheiro de origem (AccessDBSampleProvider06.cs) para este fornecedor com o Microsoft Windows Software Development Kit para Windows Vista e o .NET Framework 3.0 Runtime Components. Para obter instruções de transferência, consulte [como instalar o Windows PowerShell e transferir o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Os arquivos de fonte transferido estão disponíveis no  **\<exemplos do PowerShell >** diretório.
>
> Para obter mais informações sobre outras implementações de provedores do Windows PowerShell, consulte [conceber Windows PowerShell Fornecedor_de_e](./designing-your-windows-powershell-provider.md).

A lista seguinte contém as secções neste tópico. Se não estiver familiarizado com a escrita de um fornecedor de conteúdos do Windows PowerShell, leia estas secções pela ordem em que aparecem. No entanto, se estiver familiarizado com a escrita de um fornecedor de conteúdos do Windows PowerShell, aceda diretamente às informações de que precisa.

- [Definir a classe de fornecedor de conteúdo do PowerShell do Windows](#Define-the-Windows-PowerShell-Content-Provider-Class)

- [Definir funcionalidade de Base](#Define-Functionality-of-Base-Class)

- [Implementar um leitor de conteúdos](#Implementing-a-Content-Reader)

- [Implementando um gravador de conteúdo](#Implementing-a-Content-Writer)

- [A obter o leitor de conteúdos](#Retrieving-the-Content-Reader)

- [Os parâmetros dinâmicos para a anexar o `Get-Content` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-Content-Cmdlet)

- [A obter o escritor do conteúdo](#Retrieving-the-Content-Writer)

- [Anexar parâmetros dinâmicos para a Add_Content e `Set-Content` Cmdlets](#Attaching-Dynamic-Parameters-to-the-Add-Content-and-Set-Content-Cmdlets)

- [Limpar conteúdo](#Clearing-Content)

- [Os parâmetros dinâmicos para a anexar o `Clear-Content` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Clear-Content-Cmdlet)

- [Exemplo de código](#Code-Sample)

- [Definir tipos de objeto e formatação]()

- [Criando o provedor do Windows PowerShell](#Building-the-Windows-PowerShell-Provider)

- [Teste o fornecedor de Windows PowerShell](#Testing-the-Windows-PowerShell-Provider)

## <a name="define-the-windows-powershell-content-provider-class"></a>Definir a classe de fornecedor de conteúdo do PowerShell do Windows

Um fornecedor de conteúdos do Windows PowerShell tem de criar uma classe do .NET que suporte o [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface. Esta é a definição de classe para o fornecedor de item descrita nesta secção.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L32-L33 "AccessDBProviderSample06.cs")]

Tenha em atenção que, desta definição, de classe a [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atributo inclui dois parâmetros. O primeiro parâmetro especifica um nome amigável para o fornecedor que é utilizado pelo Windows PowerShell. O segundo parâmetro especifica os recursos específicos do Windows PowerShell que o fornecedor expõe o tempo de execução do Windows PowerShell durante o processamento do comando. Para este fornecedor, não há nenhum adicionadas capacidades específicas do Windows PowerShell.

## <a name="define-functionality-of-base-class"></a>Definir funcionalidade da classe Base

Conforme descrito em [Design Windows PowerShell Fornecedor_de_e](./designing-your-windows-powershell-provider.md), o [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe deriva de outras classes que fornecido funcionalidade de outro fornecedor. Um fornecedor de conteúdos do Windows PowerShell, portanto, normalmente define todas as funcionalidades fornecidas por essas classes.

Para obter mais informações sobre como implementar a funcionalidade para adicionar informações de inicialização de específico da sessão e para liberar os recursos que são utilizados pelo fornecedor, consulte [criar um fornecedor de PowerShell básica do Windows](./creating-a-basic-windows-powershell-provider.md). No entanto, a maioria dos fornecedores, incluindo o fornecedor descrito aqui, podem utilizar a implementação padrão dessa funcionalidade fornecida pelo Windows PowerShell.

Para acessar o arquivo de dados, o fornecedor tem de implementar os métodos do [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe base. Para obter mais informações sobre a implementação desses métodos, consulte [criar um fornecedor de unidade do Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

Para manipular os itens de um armazenamento de dados, como obter, configuração e itens de limpeza, o fornecedor tem de implementar os métodos fornecidos pela [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe base. Para obter mais informações sobre a implementação desses métodos, consulte [criar um fornecedor de Item do Windows PowerShell](./creating-a-windows-powershell-item-provider.md).

Para trabalhar em arquivos de dados de camada multi, o fornecedor tem de implementar os métodos fornecidos pela [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe base. Para obter mais informações sobre a implementação desses métodos, consulte [criar um fornecedor de contentor do Windows PowerShell](./creating-a-windows-powershell-container-provider.md).

Para suportar os comandos de recursiva, contêineres aninhados e caminhos relativos, o fornecedor tem de implementar o [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe base. Além disso, este fornecedor de conteúdos do Windows PowerShell pode anexa [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface para o [ System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe base e, por conseguinte, tem de implementar os métodos fornecidos pela classe. Para obter mais informações, consulte a implementação desses métodos, consulte [implementar um fornecedor de PowerShell do Windows de navegação](./creating-a-windows-powershell-navigation-provider.md).

## <a name="implementing-a-content-reader"></a>Implementar um leitor de conteúdos

Para ler conteúdo a partir de um item, um fornecedor tem implementa uma classe de leitor de conteúdos que deriva [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader). O leitor de conteúdos para este fornecedor permite o acesso a conteúdo de uma linha numa tabela de dados. A classe do leitor de conteúdo define um **leitura** método que obtém os dados da linha indicada e devolve uma lista que representa esses dados, uma **Seek** método que move o leitor de conteúdos, um  **Fechar** método que fecha o leitor de conteúdos, e um **Dispose** método.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2115-L2241 "AccessDBProviderSample06.cs")]

## <a name="implementing-a-content-writer"></a>Implementando um gravador de conteúdo

Para escrever conteúdo para um item, um fornecedor tem de implementar o conteúdo de um classe de escritor deriva [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter). A classe de conteúdo de escritor define um **escrever** método que grava o conteúdo da linha especificada, uma **Seek** método que move o escritor do conteúdo, uma **fechar** método que fecha o gravador de conteúdo e um **Dispose** método.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2250-L2394 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-reader"></a>A obter o leitor de conteúdos

Para obter o conteúdo de um item, o fornecedor tem de implementar o [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) para suportar o `Get-Content` cmdlet. Esse método retorna o leitor de conteúdos para o item, localizado no caminho especificado. O objeto do leitor, em seguida, pode ser aberto para ler o conteúdo.

Eis a implementação do [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) para este método para este fornecedor.

```csharp
public IContentReader GetContentReader(string path)
{
    string tableName;
    int rowNumber;

    PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

    if (type == PathType.Invalid)
    {
        ThrowTerminatingInvalidPathException(path);
    }
    else if (type == PathType.Row)
    {
        throw new InvalidOperationException("contents can be obtained only for tables");
    }

    return new AccessDBContentReader(path, this);
} // GetContentReader
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1829-L1846 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentreader"></a>Coisas a serem lembrados sobre a implementação GetContentReader

As seguintes condições podem aplicar-se para uma implementação do [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader):

- Ao definir a classe do provedor, um fornecedor de conteúdos do Windows PowerShell poderia declarar capacidades de fornecedor de ExpandWildcards, filtro, inclusão ou exclusão, da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)enumeração. Nestes casos, a implementação do [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) método tem de garantir que o caminho transmitido ao método cumpre os requisitos do especificado capacidades. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriedades.

- Por predefinição, substituições deste método não devem obter um leitor para objetos que estão ocultos do utilizador, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) estiver definida como `true`. Deve ser escrito um erro se o caminho representa um item que está oculto do usuário e [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) está definida como `false`.

## <a name="attaching-dynamic-parameters-to-the-get-content-cmdlet"></a>Anexar parâmetros dinâmicos para o Cmdlet Get-Content

O `Get-Content` cmdlet pode exigir parâmetros adicionais que são especificados dinamicamente no tempo de execução. Para fornecer estes parâmetros dinâmicos, o fornecedor de conteúdos do Windows PowerShell tem de implementar o [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) método. Esse método obtém parâmetros dinâmicos para o item no caminho indicado e retorna um objeto com propriedades e campos com análise atributos semelhantes a uma classe cmdlet ou uma [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O tempo de execução do Windows PowerShell usa o objeto devolvido para adicionar os parâmetros para o cmdlet.

Este fornecedor de contentor do Windows PowerShell não implementa esse método. No entanto, o código a seguir é a implementação do padrão desse método.

```csharp
public object GetContentReaderDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1853-L1856 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-writer"></a>A obter o escritor do conteúdo

Para escrever conteúdo para um item, o fornecedor tem de implementar o [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) para suportar a `Set-Content` e `Add-Content` cmdlets. Esse método retorna o escritor do conteúdo para o item, localizado no caminho especificado.

Eis a implementação do [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) desse método.

```csharp
public IContentWriter GetContentWriter(string path)
{
    string tableName;
    int rowNumber;

    PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

    if (type == PathType.Invalid)
    {
        ThrowTerminatingInvalidPathException(path);
    }
    else if (type == PathType.Row)
    {
        throw new InvalidOperationException("contents can be added only to tables");
    }

    return new AccessDBContentWriter(path, this);
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1863-L1880 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentwriter"></a>Coisas a serem lembrados sobre a implementação GetContentWriter

As seguintes condições podem aplicar-se na implementação [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter):

- Ao definir a classe do provedor, um fornecedor de conteúdos do Windows PowerShell poderia declarar capacidades de fornecedor de ExpandWildcards, filtro, inclusão ou exclusão, da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)enumeração. Nestes casos, a implementação do [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) método tem de garantir que o caminho transmitido ao método cumpre os requisitos do especificado capacidades. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriedades.

- Por predefinição, substituições deste método não devem obter um gravador para objetos que estão ocultos do utilizador, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) estiver definida como `true`. Deve ser escrito um erro se o caminho representa um item que está oculto do usuário e [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) está definida como `false`.

## <a name="attaching-dynamic-parameters-to-the-add-content-and-set-content-cmdlets"></a>Anexar parâmetros dinâmicos para os Cmdlets de conteúdo de adicionar e conteúdo do conjunto

O `Add-Content` e `Set-Content` cmdlets exijam adicionais parâmetros dinâmicos que são adicionados um tempo de execução. Para fornecer estes parâmetros dinâmicos, o fornecedor de conteúdos do Windows PowerShell tem de implementar o [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) método para lidar com esses parâmetros. Esse método obtém parâmetros dinâmicos para o item no caminho indicado e retorna um objeto com propriedades e campos com análise atributos semelhantes a uma classe cmdlet ou uma [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O tempo de execução do Windows PowerShell usa o objeto devolvido para adicionar os parâmetros para os cmdlets.

Este fornecedor de contentor do Windows PowerShell não implementa esse método. No entanto, o código a seguir é a implementação do padrão desse método.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1887-L1890 "AccessDBProviderSample06.cs")]

## <a name="clearing-content"></a>Limpar conteúdo

Implementa o fornecedor de conteúdos a [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) método support o `Clear-Content` cmdlet. Este método Remove o conteúdo do item no caminho especificado, mas mantém o item do utilizador intactos.

Eis a implementação do [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) método para este fornecedor.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1775-L1812 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-clearcontent"></a>Coisas a serem lembrados sobre a implementação ClearContent

As seguintes condições podem aplicar-se para uma implementação do [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent):

- Ao definir a classe do provedor, um fornecedor de conteúdos do Windows PowerShell poderia declarar capacidades de fornecedor de ExpandWildcards, filtro, inclusão ou exclusão, da [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)enumeração. Nestes casos, a implementação do [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) método tem de garantir que o caminho transmitido ao método cumpre os requisitos do especificado capacidades. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) e [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriedades.

- Por predefinição, substituições deste método não devem limpar o conteúdo de objetos que estão ocultos do utilizador, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) estiver definida como `true`. Deve ser escrito um erro se o caminho representa um item que está oculto do usuário e [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) está definida como `false`.

- Sua implementação do [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) deve chamar o método [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess* ](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e verifique se o valor de retorno antes de fazer alterações ao arquivo de dados. Este método é usado para confirmar a execução de uma operação quando é efetuada uma alteração para o armazenamento de dados, como limpar o conteúdo. O [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) método envia o nome do recurso a ser alterados ao usuário, com o tempo de execução do Windows PowerShell tratamento de definições de linha de comandos ou preferência variáveis de determinar o que deverá ser apresentado.

  Após a chamada para [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) devolve `true`, o [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent* ](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) método deve chamar o [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) método. Este método envia uma mensagem ao utilizador para permitir que os comentários verificar se a operação deve ser contínuo. A chamada para [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) permite que uma verificação adicional para as modificações de sistema potencialmente perigosas.

## <a name="attaching-dynamic-parameters-to-the-clear-content-cmdlet"></a>Anexar parâmetros dinâmicos para o Cmdlet de Clear-conteúdo

O `Clear-Content` cmdlet pode exigir adicionais parâmetros dinâmicos que são adicionados em tempo de execução. Para fornecer estes parâmetros dinâmicos, o fornecedor de conteúdos do Windows PowerShell tem de implementar o [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) método para lidar com esses parâmetros. Este método obtém os parâmetros para o item no caminho indicado. Esse método obtém parâmetros dinâmicos para o item no caminho indicado e retorna um objeto com propriedades e campos com análise atributos semelhantes a uma classe cmdlet ou uma [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. O tempo de execução do Windows PowerShell usa o objeto devolvido para adicionar os parâmetros para o cmdlet.

Este fornecedor de contentor do Windows PowerShell não implementa esse método. No entanto, o código a seguir é a implementação do padrão desse método.

```csharp
public object ClearContentDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1819-L1822 "AccessDBProviderSample06.cs")]

## <a name="code-sample"></a>Exemplo de código

Para o código de exemplo completo, consulte [exemplo de código AccessDbProviderSample06](./accessdbprovidersample06-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definir tipos de objeto e formatação

Ao escrever um fornecedor, poderá ser necessário adicionar membros a objetos existentes ou definir novos objetos. Quando isso for feito, tem de criar um ficheiro de tipos que pode utilizar o Windows PowerShell para identificar os membros do objeto e um ficheiro de formato que define como o objeto é apresentado. Para obter mais informações, consulte [estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Criando o provedor do Windows PowerShell

Ver [como registar os Cmdlets, fornecedores e alojar aplicações](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Teste o fornecedor do Windows PowerShell

Quando o seu fornecedor de Windows PowerShell foi registado com o Windows PowerShell, pode testá-lo ao executar os cmdlets suportados na linha de comandos. Por exemplo, teste o fornecedor de conteúdos de exemplo.

Utilize o `Get-Content` cmdlet para obter o conteúdo do item especificado na tabela de base de dados no caminho especificado pelo `Path` parâmetro. O `ReadCount` parâmetro especifica o número de itens para o leitor de conteúdo definido ler (predefinição 1). Com a seguinte entrada do comando, o cmdlet obtém as duas linhas (itens) da tabela e apresenta o seu conteúdo. Observe que o resultado de exemplo seguinte utiliza uma base de dados do Access fictício.

```powershell
Get-Content -Path mydb:\Customers -ReadCount 2
```

```output
ID        : 1
FirstName : Eric
LastName  : Gruber
Email     : ericgruber@fabrikam.com
Title     : President
Company   : Fabrikam
WorkPhone : (425) 555-0100
Address   : 4567 Main Street
City      : Buffalo
State     : NY
Zip       : 98052
Country   : USA
ID        : 2
FirstName : Eva
LastName  : Corets
Email     : evacorets@cohowinery.com
Title     : Sales Representative
Company   : Coho Winery
WorkPhone : (360) 555-0100
Address   : 8910 Main Street
City      : Cabmerlot
State     : WA
Zip       : 98089
Country   : USA
```

## <a name="see-also"></a>Veja Também

[Criar fornecedores de Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Fornecedor do design do Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Implementar um fornecedor de navegação Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md)

[Como registar os Cmdlets, fornecedores e alojar aplicações](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[SDK do Windows PowerShell](../windows-powershell-reference.md)

[Guia do programador do Windows PowerShell](./windows-powershell-programmer-s-guide.md)
