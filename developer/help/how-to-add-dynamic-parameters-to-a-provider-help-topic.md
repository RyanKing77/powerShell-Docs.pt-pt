---
title: Como adicionar parâmetros dinâmicos a um tópico de ajuda do provedor | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e20e5ad6-a6e6-4a63-9d42-1ac54214f748
caps.latest.revision: 5
ms.openlocfilehash: 59839e9b8b6f2a56f2f1a9c755f2f1a85deb34aa
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848108"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="51ed7-102">How to Add Dynamic Parameters to a Provider Help Topic (Como Adicionar Parâmetros Dinâmicos ao Tópico de Ajuda de um Fornecedor)</span><span class="sxs-lookup"><span data-stu-id="51ed7-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="51ed7-103">Esta seção explica como preencher a seção de **parâmetros dinâmicos** de um tópico de ajuda do provedor.</span><span class="sxs-lookup"><span data-stu-id="51ed7-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="51ed7-104">*Parâmetros dinâmicos* são parâmetros de um cmdlet ou função que estão disponíveis somente em condições especificadas.</span><span class="sxs-lookup"><span data-stu-id="51ed7-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="51ed7-105">Os parâmetros dinâmicos documentados em um tópico de ajuda do provedor são os parâmetros dinâmicos que o provedor adiciona ao cmdlet ou função quando o cmdlet ou a função é usada na unidade do provedor.</span><span class="sxs-lookup"><span data-stu-id="51ed7-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="51ed7-106">Os parâmetros dinâmicos também podem ser documentados na ajuda do cmdlet personalizado para um provedor.</span><span class="sxs-lookup"><span data-stu-id="51ed7-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="51ed7-107">Ao escrever a ajuda do provedor e a ajuda do cmdlet personalizado para um provedor, inclua a documentação do parâmetro dinâmico em ambos os documentos.</span><span class="sxs-lookup"><span data-stu-id="51ed7-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span>

<span data-ttu-id="51ed7-108">Se um provedor não implementar nenhum parâmetro dinâmico, o tópico da ajuda do provedor conterá `DynamicParameters` um elemento vazio.</span><span class="sxs-lookup"><span data-stu-id="51ed7-108">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="51ed7-109">Para adicionar parâmetros dinâmicos</span><span class="sxs-lookup"><span data-stu-id="51ed7-109">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="51ed7-110">No arquivo *AssemblyName*. dll-help. xml, dentro do `providerHelp` elemento, adicione um `DynamicParameters` elemento.</span><span class="sxs-lookup"><span data-stu-id="51ed7-110">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="51ed7-111">O `DynamicParameters` elemento deve aparecer após o `Tasks` elemento e antes do `RelatedLinks` elemento.</span><span class="sxs-lookup"><span data-stu-id="51ed7-111">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="51ed7-112">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="51ed7-112">For example:</span></span>

    ```xml
    <providerHelp>
        <Tasks>
        </Tasks>
        <DynamicParameters>
        </DynamicParameters>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

   <span data-ttu-id="51ed7-113">Se o provedor não implementar nenhum parâmetro dinâmico, o `DynamicParameters` elemento poderá ficar vazio.</span><span class="sxs-lookup"><span data-stu-id="51ed7-113">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

2. <span data-ttu-id="51ed7-114">Dentro do `DynamicParameters` elemento, para cada parâmetro dinâmico, adicione um `DynamicParameter` elemento.</span><span class="sxs-lookup"><span data-stu-id="51ed7-114">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="51ed7-115">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="51ed7-115">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. <span data-ttu-id="51ed7-116">Em cada `DynamicParameter` elemento, adicione um `Name` elemento `CmdletSupported` e.</span><span class="sxs-lookup"><span data-stu-id="51ed7-116">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   |<span data-ttu-id="51ed7-117">Nome do Elemento</span><span class="sxs-lookup"><span data-stu-id="51ed7-117">Element Name</span></span>|<span data-ttu-id="51ed7-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="51ed7-118">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="51ed7-119">Nome</span><span class="sxs-lookup"><span data-stu-id="51ed7-119">Name</span></span>|<span data-ttu-id="51ed7-120">Especifica o nome do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="51ed7-120">Specifies the parameter name.</span></span>|
   |<span data-ttu-id="51ed7-121">CmdletSupported</span><span class="sxs-lookup"><span data-stu-id="51ed7-121">CmdletSupported</span></span>|<span data-ttu-id="51ed7-122">Especifica os cmdlets nos quais o parâmetro é válido.</span><span class="sxs-lookup"><span data-stu-id="51ed7-122">Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="51ed7-123">Digite uma lista separada por vírgulas de nomes de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="51ed7-123">Type a comma-separated list of cmdlet names.</span></span>|

   <span data-ttu-id="51ed7-124">Por exemplo, o XML a seguir documenta `Encoding` o parâmetro dinâmico que o provedor do sistema de arquivos do `Add-Content`Windows PowerShell `Set-Content` adiciona aos cmdlets, `Get-Content`,.</span><span class="sxs-lookup"><span data-stu-id="51ed7-124">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. <span data-ttu-id="51ed7-125">Em cada `DynamicParameter` elemento, adicione um `Type` elemento.</span><span class="sxs-lookup"><span data-stu-id="51ed7-125">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="51ed7-126">O `Type` elemento é um contêiner para o `Name` elemento que contém o tipo .net do valor do parâmetro dinâmico.</span><span class="sxs-lookup"><span data-stu-id="51ed7-126">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="51ed7-127">Por exemplo, o XML a seguir mostra que o tipo .net do `Encoding` parâmetro dinâmico é a enumeração [Microsoft. PowerShell. Commands. FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) .</span><span class="sxs-lookup"><span data-stu-id="51ed7-127">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
    ...
    </DynamicParameters>
    ```

5. <span data-ttu-id="51ed7-128">Adicione o `Description` elemento, que contém uma breve descrição do parâmetro dinâmico.</span><span class="sxs-lookup"><span data-stu-id="51ed7-128">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="51ed7-129">Ao compor a descrição, use as diretrizes indicadas para todos os parâmetros de cmdlet em [como adicionar informações de parâmetro](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="51ed7-129">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="51ed7-130">Por exemplo, o XML a seguir inclui a descrição do `Encoding` parâmetro dinâmico.</span><span class="sxs-lookup"><span data-stu-id="51ed7-130">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
            <Description> Specifies the encoding of the output file that contains the content. </Description>
    ...
    </DynamicParameters>
    ```

6. <span data-ttu-id="51ed7-131">Adicione o `PossibleValues` elemento e seus elementos filho.</span><span class="sxs-lookup"><span data-stu-id="51ed7-131">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="51ed7-132">Juntos, esses elementos descrevem os valores do parâmetro dinâmico.</span><span class="sxs-lookup"><span data-stu-id="51ed7-132">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="51ed7-133">Esse elemento é projetado para valores enumerados.</span><span class="sxs-lookup"><span data-stu-id="51ed7-133">This element is designed for enumerated values.</span></span> <span data-ttu-id="51ed7-134">Se o parâmetro dinâmico não receber um valor, como é o caso com um parâmetro de opção, ou os valores não podem ser enumerados, adicione um elemento `PossibleValues` vazio.</span><span class="sxs-lookup"><span data-stu-id="51ed7-134">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="51ed7-135">A tabela a seguir lista e descreve `PossibleValues` o elemento e seus elementos filho.</span><span class="sxs-lookup"><span data-stu-id="51ed7-135">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   |<span data-ttu-id="51ed7-136">Nome do Elemento</span><span class="sxs-lookup"><span data-stu-id="51ed7-136">Element Name</span></span>|<span data-ttu-id="51ed7-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="51ed7-137">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="51ed7-138">PossibleValues</span><span class="sxs-lookup"><span data-stu-id="51ed7-138">PossibleValues</span></span>|<span data-ttu-id="51ed7-139">Este elemento é um contêiner.</span><span class="sxs-lookup"><span data-stu-id="51ed7-139">This element is a container.</span></span> <span data-ttu-id="51ed7-140">Seus elementos filho são descritos abaixo.</span><span class="sxs-lookup"><span data-stu-id="51ed7-140">Its child elements are described below.</span></span> <span data-ttu-id="51ed7-141">Adicione um `PossibleValues` elemento a cada tópico da ajuda do provedor.</span><span class="sxs-lookup"><span data-stu-id="51ed7-141">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="51ed7-142">O elemento pode estar vazio.</span><span class="sxs-lookup"><span data-stu-id="51ed7-142">The element can be empty.</span></span>|
   |<span data-ttu-id="51ed7-143">Possível</span><span class="sxs-lookup"><span data-stu-id="51ed7-143">PossibleValue</span></span>|<span data-ttu-id="51ed7-144">Este elemento é um contêiner.</span><span class="sxs-lookup"><span data-stu-id="51ed7-144">This element is a container.</span></span> <span data-ttu-id="51ed7-145">Seus elementos filho são descritos abaixo.</span><span class="sxs-lookup"><span data-stu-id="51ed7-145">Its child elements are described below.</span></span> <span data-ttu-id="51ed7-146">Adicione um `PossibleValue` elemento para cada valor do parâmetro dinâmico.</span><span class="sxs-lookup"><span data-stu-id="51ed7-146">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>|
   |<span data-ttu-id="51ed7-147">Valor</span><span class="sxs-lookup"><span data-stu-id="51ed7-147">Value</span></span>|<span data-ttu-id="51ed7-148">Especifica o nome do valor.</span><span class="sxs-lookup"><span data-stu-id="51ed7-148">Specifies the value name.</span></span>|
   |<span data-ttu-id="51ed7-149">Descrição</span><span class="sxs-lookup"><span data-stu-id="51ed7-149">Description</span></span>|<span data-ttu-id="51ed7-150">Este elemento contém um `Para` elemento.</span><span class="sxs-lookup"><span data-stu-id="51ed7-150">This element contains a `Para` element.</span></span> <span data-ttu-id="51ed7-151">O texto no `Para` elemento descreve o valor que é nomeado `Value` no elemento.</span><span class="sxs-lookup"><span data-stu-id="51ed7-151">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>|

   <span data-ttu-id="51ed7-152">Por exemplo, o XML a seguir mostra `PossibleValue` um elemento `Encoding` do parâmetro dinâmico.</span><span class="sxs-lookup"><span data-stu-id="51ed7-152">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
    ...
            <Description> Specifies the encoding of the output file that contains the content. </Description>
            <PossibleValues>
                <PossibleValue>
                    <Value> ASCII </Value>
                    <Description>
                        <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                    </Description>
                </PossibleValue>
    ...
            </PossibleValues>
    </DynamicParameters>
    ```

## <a name="example"></a><span data-ttu-id="51ed7-153">Exemplo</span><span class="sxs-lookup"><span data-stu-id="51ed7-153">Example</span></span>

<span data-ttu-id="51ed7-154">O exemplo a seguir mostra `DynamicParameters` o elemento `Encoding` do parâmetro dinâmico.</span><span class="sxs-lookup"><span data-stu-id="51ed7-154">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

```xml
<DynamicParameters/>
    <DynamicParameter>
        <Name> Encoding </Name>
        <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
        <Type>
            <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
        <Type>
        <Description> Specifies the encoding of the output file that contains the content. </Description>
        <PossibleValues>
            <PossibleValue>
                <Value> ASCII </Value>
                <Description>
                    <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                </Description>
            </PossibleValue>
            <PossibleValue>
                <Value> Unicode </Value>
                <Description>
                    <para> Encodes in UTF-16 format using the little-endian byte order. </para>
                </Description>
            </PossibleValue>
        </PossibleValues>
</DynamicParameters>
```