---
title: Criar um fornecedor de navegação do Windows PowerShell | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- navigation providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], navigation provider
ms.assetid: 8bd3224d-ca6f-4640-9464-cb4d9f4e13b1
caps.latest.revision: 5
ms.openlocfilehash: 40454f880b57d5b3a8a8ded21c8c97aebba027fe
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055075"
---
# <a name="creating-a-windows-powershell-navigation-provider"></a>Creating a Windows PowerShell Navigation Provider (Criar um Fornecedor de Navegação do Windows PowerShell)

Este tópico descreve como criar um provedor de navegação do Windows PowerShell que pode navegar no arquivo de dados. Este tipo de fornecedor suporta comandos de recursiva, contêineres aninhados e caminhos relativos.

> [!NOTE]
> Pode transferir o C# ficheiro de origem (AccessDBSampleProvider05.cs) para este fornecedor com o Microsoft Windows Software Development Kit para Windows Vista e o .NET Framework 3.0 Runtime Components. Para obter instruções de transferência, consulte [como instalar o Windows PowerShell e transferir o SDK do Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Os arquivos de fonte transferido estão disponíveis no  **\<exemplos do PowerShell >** diretório.
>
> Para obter mais informações sobre outras implementações de provedores do Windows PowerShell, consulte [conceber Windows PowerShell Fornecedor_de_e](./designing-your-windows-powershell-provider.md).

O fornecedor descrito aqui permite o um banco de dados do Access o identificador do usuário como uma unidade, para que o utilizador pode navegar para as tabelas de dados na base de dados. Ao criar seu próprio provedor de navegação, pode implementar os métodos que podem fazer caminhos qualificado de unidade necessários para a navegação, normalizar caminhos relativos, mova os itens de arquivo de dados, bem como métodos que obtém nomes de subordinado, obtém o caminho principal de um item e de teste para identificar se um item é um contentor.

> [!CAUTION]
> Lembre-se de que esse design supõe que uma base de dados que tem um campo com o ID de nome e de que o tipo do campo é LongInteger.

A lista seguinte inclui as secções neste tópico. Se não estiver familiarizado com a escrita de um fornecedor de navegação do Windows PowerShell, ler estas informações na ordem em que ele é exibido. No entanto, se estiver familiarizado com a escrita de um fornecedor de navegação do Windows PowerShell, aceda diretamente às informações de que precisa.

- [Definir uma classe de fornecedor de navegação de PS](#Define-the-Windows-PowerShell-provider)

- [Definir funcionalidade de Base](#Defining-Base-Functionality)

- [Criar um caminho de PS](#Creating-a-Windows-PowerShell-Path)

- [A obter o caminho principal](#Retrieving-the-Parent-Path)

- [A obter o nome do caminho de subordinados](#Retrieve-the-Child-Path-Name)

- [Determinar se um Item é um contentor](#Determining-if-an-Item-is-a-Container)

- [Mover um Item](#Moving-an-Item)

- [Os parâmetros dinâmicos para a anexar o `Move-Item` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Move-Item-Cmdlet)

- [Normalizar um caminho relativo](#Normalizing-a-Relative-Path)

- [Exemplo de código](#Code-Sample)

- [Definir tipos de objeto e formatação](#Defining-Object-Types-and-Formatting)

- [Criando o provedor do Windows PowerShell](#Building-the-Windows-PowerShell-provider)

- [Teste o fornecedor do Windows PowerShell](#Testing-the-Windows-PowerShell-provider)

## <a name="define-the-windows-powershell-provider"></a>Definir o fornecedor de Windows PowerShell

Um provedor de navegação do Windows PowerShell tem de criar uma classe do .NET que deriva de [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe base. Esta é a definição de classe para o fornecedor de navegação descrita nesta secção.

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L31-L32 "AccessDBProviderSample05.cs")]

Observe que, neste fornecedor, o [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atributo inclui dois parâmetros. O primeiro parâmetro especifica um nome amigável para o fornecedor que é utilizado pelo Windows PowerShell. O segundo parâmetro especifica os recursos específicos do Windows PowerShell que o fornecedor expõe o tempo de execução do Windows PowerShell durante o processamento do comando. Para este fornecedor, não há nenhum capacidades específicas do Windows PowerShell que são adicionadas.

## <a name="defining-base-functionality"></a>Definir funcionalidade de Base

Conforme descrito em [Design de seu fornecedor de PS](./designing-your-windows-powershell-provider.md), o [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe base derivada de outras classes que fornecidos fornecedor diferente funcionalidade. Um provedor de navegação do Windows PowerShell, por conseguinte, tem de definir todas as funcionalidades fornecidas por essas classes.

Para implementar a funcionalidade para adicionar informações de inicialização de específico da sessão e para liberar os recursos que são utilizados pelo fornecedor, veja [criar um fornecedor de PS básica](./creating-a-basic-windows-powershell-provider.md). No entanto, a maioria dos provedores de (incluindo o fornecedor descrito aqui) pode utilizar a implementação padrão desta funcionalidade fornecida pelo Windows PowerShell.

Para obter acesso ao arquivo de dados por meio de uma unidade do Windows PowerShell, tem de implementar os métodos do [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe base. Para obter mais informações sobre a implementação desses métodos, consulte [criar um fornecedor de unidade do Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

Para manipular os itens de um armazenamento de dados, como obter, configuração e itens de limpeza, o fornecedor tem de implementar os métodos fornecidos pela [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe base. Para obter mais informações sobre a implementação desses métodos, consulte [criar um fornecedor de Item do Windows PowerShell](./creating-a-windows-powershell-item-provider.md).

Para obter os itens subordinados ou seus nomes, de arquivo de dados, bem como métodos que criam, copiam, mudar o nome e remover itens, deve implementar os métodos fornecidos pelo [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)classe base. Para obter mais informações sobre a implementação desses métodos, consulte [criar um fornecedor de contentor do Windows PowerShell](./creating-a-windows-powershell-container-provider.md).

## <a name="creating-a-windows-powershell-path"></a>Criar um caminho do Windows PowerShell

Fornecedor de navegação do Windows PowerShell usar um caminho interno para o fornecedor do Windows PowerShell para navegar os itens de arquivo de dados. Para criar um caminho de fornecedor interno o fornecedor tem de implementar o [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) chama o método para suporta do cmdlet Combine-Path. Este método combina um caminho pai e filho num caminho de fornecedor interno, com um separador de caminho específica do fornecedor entre os caminhos principais e subordinados.

A implementação padrão usa caminhos com "/" ou "\\"como separador de caminho, normaliza o separador de caminho para"\\", combina as partes do caminho principal e subordinada com o separador entre eles e, em seguida, retorna uma cadeia que contém o caminhos combinados.

Este fornecedor de navegação não implementa esse método. No entanto, o código a seguir é a implementação padrão do [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermakepath](Msh_samplestestcmdlets#testprovidermakepath)]  -->

#### <a name="things-to-remember-about-implementing-makepath"></a>Coisas a serem lembrados sobre a implementação MakePath

As seguintes condições podem aplicar-se na implementação [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):

- Sua implementação do [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) método não deve validar o caminho como um caminho totalmente qualificado legal no espaço de nomes do fornecedor. Lembre-se de que cada parâmetro só pode representar uma parte de um caminho e as partes combinadas não podem gerar um caminho totalmente qualificado. Por exemplo, o [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) método para o fornecedor do sistema de ficheiros pode receber "windows\system32" no `parent` parâmetro e "abc.dll" o `child` parâmetro. O método é associado esses valores com o "\\" separador e devolve "windows\system32\abc.dll", que não é um caminho de sistema de ficheiro completamente qualificado.

  > [!IMPORTANT]
  > As partes do caminho fornecidas na chamada para [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) pode conter carateres não permitidos no espaço de nomes do fornecedor. Estes carateres é muito provável que são utilizados para expansão de caráter universal e a implementação desse método não deve removê-los.

## <a name="retrieving-the-parent-path"></a>A obter o caminho principal

Provedores de navegação do Windows PowerShell implementam a [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) método para recuperar a parte do principal do indicado total ou parcial caminho de específica do fornecedor. O método Remove a parte-filho do caminho e retorna a principal parte do caminho. O `root` parâmetro especifica o caminho totalmente qualificado para a raiz de uma unidade. Este parâmetro pode ser nulo nem estar vazio se uma unidade montada não está a ser utilizado para a operação de obtenção. Se for especificada uma raiz, o método deve retornar um caminho para um contentor na mesma árvore de como a raiz.

O exemplo de provedor de navegação não substitui este método, mas usa a implementação padrão. Ela aceita caminhos que utilizam ambos "/" e "\\" como separadores de caminho. Ele primeiro normaliza o caminho para ter apenas "\\" separadores, em seguida, divide o caminho principal desativado no último "\\" e retorna o caminho principal.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetparentpath](Msh_samplestestcmdlets#testprovidergetparentpath)]  -->

#### <a name="to-remember-about-implementing-getparentpath"></a>Lembrar-se sobre a implementação GetParentPath

Sua implementação do [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) método deve dividir o caminho lexicalmente no separador de caminho para o espaço de nomes do fornecedor. Por exemplo, o fornecedor do sistema de ficheiros utiliza este método para procurar o último "\\" e retorna tudo para a esquerda do separador.

## <a name="retrieve-the-child-path-name"></a>Obter o nome do caminho de subordinados

Sua implementa de fornecedor de navegação da [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) método para recuperar o nome (elemento da folha) do filho do item localizado em todo o indicados ou caminho de específica do fornecedor parcial.

O exemplo de provedor de navegação não substitui este método. A implementação padrão é mostrada abaixo. Ela aceita caminhos que utilizam ambos "/" e "\\" como separadores de caminho. -Lo primeiro normaliza o caminho para ter apenas "\\" separadores, em seguida, divide o caminho principal desativado no último "\\" e devolve o nome do filho parte do caminho.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildname](Msh_samplestestcmdlets#testprovidergetchildname)]  -->

#### <a name="things-to-remember-about-implementing-getchildname"></a>Coisas a serem lembrados sobre a implementação GetChildName

Sua implementação do [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) método deve dividir o caminho lexicalmente no separador de caminho. Se o caminho fornecido não contém nenhuma separadores de caminho, o método deve retornar o caminho sem modificações.

> [!IMPORTANT]
> O caminho fornecido na chamada para esse método pode conter carateres que são ilegais no espaço de nomes do fornecedor. Esses caracteres são mais prováveis utilizado para expansão de carateres universais ou correspondência de expressões regulares, e a implementação desse método não deve removê-los.

## <a name="determining-if-an-item-is-a-container"></a>Determinar se um Item é um contentor

O fornecedor de navegação que pode implementar o [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) método para determinar se o caminho especificado indica um contentor. Devolve VERDADEIRO se o caminho representa um contentor e false caso contrário. O utilizador tem este método para poder utilizar o `Test-Path` cmdlet para o caminho fornecido.

O código seguinte mostra os [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) implementação no nosso exemplo de provedor de navegação. O método verifica que o caminho especificado está correto e se a tabela existe e devolve verdadeira se o caminho indica um contentor.

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L847-L872 "AccessDBProviderSample05.cs")]

#### <a name="things-to-remember-about-implementing-isitemcontainer"></a>Coisas a serem lembrados sobre a implementação IsItemContainer

Seu fornecedor de navegação de classe do .NET pode declarar capacidades de fornecedor de ExpandWildcards, filtro, inclusão ou exclusão, do [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeração. Neste caso, a implementação do [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) tem de garantir que o caminho transmitido cumpre os requisitos. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) propriedade.

## <a name="moving-an-item"></a>Mover um Item

Support do `Move-Item` seu provedor de navegação de cmdlet, implementa o [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) método. Esse método passa o item especificado pelos `path` parâmetro para o contentor no caminho fornecido no `destination` parâmetro.

O exemplo de provedor de navegação não substitui a [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) método. Segue-se a implementação padrão.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitem](Msh_samplestestcmdlets#testprovidermoveitem)]  -->

#### <a name="things-to-remember-about-implementing-moveitem"></a>Coisas a serem lembrados sobre a implementação MoveItem

Seu fornecedor de navegação de classe do .NET pode declarar capacidades de fornecedor de ExpandWildcards, filtro, inclusão ou exclusão, do [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeração. Neste caso, a implementação do [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) tem de garantir que o caminho transmitido cumpre os requisitos. Para fazer isso, o método deve acessar a propriedade apropriada, por exemplo, o **CmdletProvider.Exclude** propriedade.

Por predefinição, substituições deste método não deverá mover objetos ao longo de objetos existentes, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) estiver definida como `true`. Por exemplo, o fornecedor do sistema de ficheiros não copiará c:\temp\abc.txt ao longo de um ficheiro de c:\bar.txt existente, a menos que o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) estiver definida como `true`. Se o caminho especificado na `destination` parâmetro existe e é um contentor, o [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriedade não é necessária. Neste caso, [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) deve mover o item indicado pela `path` parâmetro para o contentor indicado pelo `destination` parâmetro como um filho.

Sua implementação do [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) deve chamar o método [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e verifique o valor de retorno antes de fazer alterações ao arquivo de dados. Este método é usado para confirmar a execução de uma operação quando é efetuada uma alteração de estado do sistema, por exemplo, a eliminar ficheiros. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) envia o nome do recurso a ser alterados ao usuário, com o tempo de execução do Windows PowerShell tendo em conta as definições de linha de comandos ou variáveis de preferência em determinar o que deverá ser apresentado ao utilizador.

Após a chamada para [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) devolve `true`, o [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) método deve chamar o [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) método. Este método envia uma mensagem ao utilizador para permitir que os seus comentários para dizer se deve ser contínuo a operação. O fornecedor deve chamar [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) como uma verificação adicional para as modificações de sistema potencialmente perigosas.

## <a name="attaching-dynamic-parameters-to-the-move-item-cmdlet"></a>Anexar parâmetros dinâmicos para o Cmdlet Move-Item

Por vezes, o `Move-Item` cmdlet requer parâmetros adicionais que são fornecidos dinamicamente no tempo de execução. Para fornecer estes parâmetros dinâmicos, o fornecedor de navegação tem de implementar o [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) método para obter os valores de parâmetro necessário do item no caminho indicado e devolver um objeto com propriedades e campos com análise atributos semelhante a uma classe cmdlet ou uma [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto.

Este fornecedor de navegação não implementa esse método. No entanto, o código a seguir é a implementação padrão da [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters](Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters)]  -->

## <a name="normalizing-a-relative-path"></a>Normalizar um caminho relativo

Sua implementa de fornecedor de navegação da [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) método normalizar o caminho totalmente qualificado indicado no `path` parâmetro como sendo relativo ao caminho especificado pelo `basePath` parâmetro. O método retorna uma representação de cadeia de caracteres do caminho normalizado. Ele escreve um erro se o `path` parâmetro especifica um caminho não existe.

O exemplo de provedor de navegação não substitui este método. Segue-se a implementação padrão.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernormalizepath](Msh_samplestestcmdlets#testprovidernormalizepath)]  -->

#### <a name="things-to-remember-about-implementing-normalizerelativepath"></a>Coisas a serem lembrados sobre a implementação NormalizeRelativePath

A implementação do [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) deve analisar o `path` parâmetro, mas não tem de utilizar a análise puramente sintática. Incentivamos o design corresponde a este método para utilizar o caminho para procurar as informações de caminho no arquivo de dados e criar um caminho que as maiúsculas e minúsculas e padronizados a sintaxe do caminho.

## <a name="code-sample"></a>Exemplo de código

Para o código de exemplo completo, consulte [exemplo de código AccessDbProviderSample05](./accessdbprovidersample05-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definir tipos de objeto e formatação

É possível que um fornecedor adicionar membros a objetos existentes ou definir novos objetos. Para obter mais informações, consulte[estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Criando o provedor do Windows PowerShell

Para obter mais informações, consulte [como registrar Cmdlets, fornecedores e alojar aplicações](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Teste o fornecedor de Windows PowerShell

Quando o seu fornecedor de Windows PowerShell foi registado com o Windows PowerShell, pode testá-lo ao executar os cmdlets suportados na linha de comando, incluindo cmdlets disponibilizados pela derivação. Neste exemplo testará o provedor de navegação de exemplo.

1. Execute o seu novo shell e utilize o `Set-Location` cmdlet para definir o caminho para indicar o banco de dados do Access.

   ```powershell
   Set-Location mydb:
   ```

2. Agora, execute o `Get-Childitem` cmdlet para obter uma lista dos itens da base de dados, que são as tabelas de base de dados disponíveis. Para cada tabela, este cmdlet obtém também o número de linhas de tabela.

   ```powershell
   Get-ChildItem | Format-Table rowcount,name -AutoSize
   ```

   ```output
   RowCount   Name
   --------   ----
        180   MSysAccessObjects
          0   MSysACEs
          1   MSysCmdbars
          0   MSysIMEXColumns
          0   MSysIMEXSpecs
          0   MSysObjects
          0   MSysQueries
          7   MSysRelationships
          8   Categories
         91   Customers
          9   Employees
       2155   Order Details
        830   Orders
         77   Products
          3   Shippers
         29   Suppliers
   ```

3. Utilize o `Set-Location` cmdlet novamente para definir o local da tabela de dados de funcionários.

   ```powershell
   Set-Location Employees
   ```

4. Agora, vamos utilizar o `Get-Location` cmdlet para obter o caminho para a tabela de funcionários.

   ```powershell
   Get-Location
   ```

   ```output
   Path
   ----
   mydb:\Employees
   ```

5. Agora utilizar o `Get-Childitem` cmdlet enviado por pipe para o `Format-Table` cmdlet. Este conjunto de cmdlets recupera os itens para a tabela de dados de funcionários, que são as linhas de tabela. São formatados como especificado pelo `Format-Table` cmdlet.

   ```powershell
   Get-ChildItem | Format-Table rownumber,psiscontainer,data -AutoSize
   ```

   ```output
   RowNumber   PSIsContainer   Data
   ---------   --------------   ----
   0           False            System.Data.DataRow
   1           False            System.Data.DataRow
   2           False            System.Data.DataRow
   3           False            System.Data.DataRow
   4           False            System.Data.DataRow
   5           False            System.Data.DataRow
   6           False            System.Data.DataRow
   7           False            System.Data.DataRow
   8           False            System.Data.DataRow
   ```

6. Agora, pode executar o `Get-Item` cmdlet para obter os itens para 0 de linha da tabela de dados de funcionários.

   ```powershell
   Get-Item 0
   ```

   ```output
   PSPath        : AccessDB::C:\PS\Northwind.mdb\Employees\0
   PSParentPath  : AccessDB::C:\PS\Northwind.mdb\Employees
   PSChildName   : 0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data           : System.Data.DataRow
   RowNumber      : 0
   ```

7. Utilize o `Get-Item` cmdlet novamente para obter os dados de funcionários para os itens na linha 0.

   ```powershell
   (Get-Item 0).data
   ```

   ```output
   EmployeeID      : 1
   LastName        : Davis
   FirstName       : Sara
   Title           : Sales Representative
   TitleOfCourtesy : Ms.
   BirthDate       : 12/8/1968 12:00:00 AM
   HireDate        : 5/1/1992 12:00:00 AM
   Address         : 4567 Main Street
                     Apt. 2A
   City            : Buffalo
   Region          : NY
   PostalCode      : 98052
   Country         : USA
   HomePhone       : (206) 555-9857
   Extension       : 5467
   Photo           : EmpID1.bmp
   Notes           : Education includes a BA in psychology from
                     Colorado State University. She also completed "The
                     Art of the Cold Call."  Nancy is a member of
                     Toastmasters International.
   ReportsTo       : 2
   ```

## <a name="see-also"></a>Veja Também

[Criar fornecedores de Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Fornecedor do design do Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Estendendo tipos de objeto e formatação](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Implementar um fornecedor de contentor Windows PowerShell](./creating-a-windows-powershell-container-provider.md)

[Como registar os Cmdlets, fornecedores e alojar aplicações](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Guia do programador do Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)