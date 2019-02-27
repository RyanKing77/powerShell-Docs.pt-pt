---
title: Como adicionar parâmetros dinâmicos para um tópico de ajuda do Provedor | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e20e5ad6-a6e6-4a63-9d42-1ac54214f748
caps.latest.revision: 5
ms.openlocfilehash: cc4877242a16a9caa99564aeaae985f85e38791e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849526"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="627d2-102">How to Add Dynamic Parameters to a Provider Help Topic (Como Adicionar Parâmetros Dinâmicos ao Tópico de Ajuda de um Fornecedor)</span><span class="sxs-lookup"><span data-stu-id="627d2-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="627d2-103">Esta secção explica como preencher os **parâmetros DINÂMICOS** seção um tópico de ajuda do fornecedor.</span><span class="sxs-lookup"><span data-stu-id="627d2-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="627d2-104">*Os parâmetros dinâmicos* são parâmetros de um cmdlet ou ser especificada de função que estão disponíveis apenas em condições.</span><span class="sxs-lookup"><span data-stu-id="627d2-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="627d2-105">Os parâmetros dinâmicos que estão documentados num tópico de ajuda do provedor são os parâmetros dinâmicos que o fornecedor adiciona a função ou o cmdlet quando a função ou o cmdlet é utilizada na unidade de fornecedor.</span><span class="sxs-lookup"><span data-stu-id="627d2-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="627d2-106">Os parâmetros dinâmicos também podem ser documentados na ajuda do cmdlet personalizado para um fornecedor.</span><span class="sxs-lookup"><span data-stu-id="627d2-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="627d2-107">Ao escrever a ajuda do provedor e ajuda de cmdlets personalizados para um fornecedor, incluem a documentação de parâmetro dinâmico em ambos os documentos.</span><span class="sxs-lookup"><span data-stu-id="627d2-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span> <span data-ttu-id="627d2-108">Para obter mais informações sobre a ajuda do cmdlet personalizado, consulte [escrita Windows PowerShell personalizado ajuda do Cmdlet para fornecedores](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span><span class="sxs-lookup"><span data-stu-id="627d2-108">For more information about custom cmdlet help, see [Writing Windows PowerShell Custom Cmdlet Help for Providers](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span></span>

<span data-ttu-id="627d2-109">Se um fornecedor não implementa qualquer parâmetros dinâmicos, o tópico de ajuda do provedor contém vazio `DynamicParameters` elemento.</span><span class="sxs-lookup"><span data-stu-id="627d2-109">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="627d2-110">Para adicionar parâmetros dinâmicos</span><span class="sxs-lookup"><span data-stu-id="627d2-110">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="627d2-111">Na *AssemblyName*help.xml. dll do ficheiro, dentro da `providerHelp` elemento, adicionar um `DynamicParameters` elemento.</span><span class="sxs-lookup"><span data-stu-id="627d2-111">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="627d2-112">O `DynamicParameters` elemento deve aparecer após o `Tasks` elemento e antes do `RelatedLinks` elemento.</span><span class="sxs-lookup"><span data-stu-id="627d2-112">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="627d2-113">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="627d2-113">For example:</span></span>

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

   <span data-ttu-id="627d2-114">Se o fornecedor não implementa qualquer parâmetros dinâmicos, o `DynamicParameters` elemento pode estar vazio.</span><span class="sxs-lookup"><span data-stu-id="627d2-114">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

2. <span data-ttu-id="627d2-115">Dentro de `DynamicParameters` elemento, para cada parâmetro dinâmico, adicionar um `DynamicParameter` elemento.</span><span class="sxs-lookup"><span data-stu-id="627d2-115">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="627d2-116">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="627d2-116">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. <span data-ttu-id="627d2-117">Em cada `DynamicParameter` elemento, adicione um `Name` e `CmdletSupported` elemento.</span><span class="sxs-lookup"><span data-stu-id="627d2-117">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   |<span data-ttu-id="627d2-118">Nome do Elemento</span><span class="sxs-lookup"><span data-stu-id="627d2-118">Element Name</span></span>|<span data-ttu-id="627d2-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="627d2-119">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="627d2-120">Nome</span><span class="sxs-lookup"><span data-stu-id="627d2-120">Name</span></span>|<span data-ttu-id="627d2-121">Especifica o nome do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="627d2-121">Specifies the parameter name.</span></span>|
   |<span data-ttu-id="627d2-122">CmdletSupported</span><span class="sxs-lookup"><span data-stu-id="627d2-122">CmdletSupported</span></span>|<span data-ttu-id="627d2-123">Especifica os cmdlets em que o parâmetro é válido.</span><span class="sxs-lookup"><span data-stu-id="627d2-123">Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="627d2-124">Escreva uma lista separada por vírgulas de nomes de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="627d2-124">Type a comma-separated list of cmdlet names.</span></span>|

   <span data-ttu-id="627d2-125">Por exemplo, os seguintes documentos XML a `Encoding` parâmetro dinâmico, que o fornecedor do sistema de ficheiros do Windows PowerShell adiciona para o `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="627d2-125">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. <span data-ttu-id="627d2-126">Em cada `DynamicParameter` elemento, adicione um `Type` elemento.</span><span class="sxs-lookup"><span data-stu-id="627d2-126">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="627d2-127">O `Type` elemento é um contentor para o `Name` elemento que contém o tipo de .NET do valor do parâmetro dinâmico.</span><span class="sxs-lookup"><span data-stu-id="627d2-127">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="627d2-128">Por exemplo, o XML a seguir mostra que o tipo de .NET do `Encoding` parâmetro dinâmico é o [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeração.</span><span class="sxs-lookup"><span data-stu-id="627d2-128">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

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

5. <span data-ttu-id="627d2-129">Adicionar o `Description` elemento, que contém uma breve descrição do parâmetro dinâmico.</span><span class="sxs-lookup"><span data-stu-id="627d2-129">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="627d2-130">Ao redigir a descrição, utilize as diretrizes prescritas para todos os parâmetros de cmdlet em [como adicionar informações de parâmetro](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="627d2-130">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="627d2-131">Por exemplo, o XML a seguir inclui a descrição do `Encoding` parâmetro dinâmico.</span><span class="sxs-lookup"><span data-stu-id="627d2-131">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

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

6. <span data-ttu-id="627d2-132">Adicionar o `PossibleValues` elemento e os respetivos elementos subordinados.</span><span class="sxs-lookup"><span data-stu-id="627d2-132">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="627d2-133">Juntos, esses elementos descrevem os valores do parâmetro dinâmico.</span><span class="sxs-lookup"><span data-stu-id="627d2-133">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="627d2-134">Este elemento foi concebido para valores enumerados.</span><span class="sxs-lookup"><span data-stu-id="627d2-134">This element is designed for enumerated values.</span></span> <span data-ttu-id="627d2-135">Se o parâmetro dinâmico não tem um valor, tal como é o caso de um parâmetro ou os valores não não possível enumerar, adicionar vazio `PossibleValues` elemento.</span><span class="sxs-lookup"><span data-stu-id="627d2-135">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="627d2-136">A tabela seguinte lista e descreve o `PossibleValues` elemento e os respetivos elementos subordinados.</span><span class="sxs-lookup"><span data-stu-id="627d2-136">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   |<span data-ttu-id="627d2-137">Nome do Elemento</span><span class="sxs-lookup"><span data-stu-id="627d2-137">Element Name</span></span>|<span data-ttu-id="627d2-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="627d2-138">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="627d2-139">PossibleValues</span><span class="sxs-lookup"><span data-stu-id="627d2-139">PossibleValues</span></span>|<span data-ttu-id="627d2-140">Este elemento é um contentor.</span><span class="sxs-lookup"><span data-stu-id="627d2-140">This element is a container.</span></span> <span data-ttu-id="627d2-141">Elementos filho são descritos abaixo.</span><span class="sxs-lookup"><span data-stu-id="627d2-141">Its child elements are described below.</span></span> <span data-ttu-id="627d2-142">Adicionar um `PossibleValues` elemento cada tópico de ajuda do fornecedor.</span><span class="sxs-lookup"><span data-stu-id="627d2-142">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="627d2-143">O elemento pode estar vazio.</span><span class="sxs-lookup"><span data-stu-id="627d2-143">The element can be empty.</span></span>|
   |<span data-ttu-id="627d2-144">PossibleValue</span><span class="sxs-lookup"><span data-stu-id="627d2-144">PossibleValue</span></span>|<span data-ttu-id="627d2-145">Este elemento é um contentor.</span><span class="sxs-lookup"><span data-stu-id="627d2-145">This element is a container.</span></span> <span data-ttu-id="627d2-146">Elementos filho são descritos abaixo.</span><span class="sxs-lookup"><span data-stu-id="627d2-146">Its child elements are described below.</span></span> <span data-ttu-id="627d2-147">Adicionar um `PossibleValue` elemento para cada valor do parâmetro dinâmico.</span><span class="sxs-lookup"><span data-stu-id="627d2-147">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>|
   |<span data-ttu-id="627d2-148">Valor</span><span class="sxs-lookup"><span data-stu-id="627d2-148">Value</span></span>|<span data-ttu-id="627d2-149">Especifica o nome do valor.</span><span class="sxs-lookup"><span data-stu-id="627d2-149">Specifies the value name.</span></span>|
   |<span data-ttu-id="627d2-150">Descrição</span><span class="sxs-lookup"><span data-stu-id="627d2-150">Description</span></span>|<span data-ttu-id="627d2-151">Esse elemento contém um `Para` elemento.</span><span class="sxs-lookup"><span data-stu-id="627d2-151">This element contains a `Para` element.</span></span> <span data-ttu-id="627d2-152">O texto a `Para` elemento descreve o valor com o nome no `Value` elemento.</span><span class="sxs-lookup"><span data-stu-id="627d2-152">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>|

   <span data-ttu-id="627d2-153">Por exemplo, o XML a seguir mostra um `PossibleValue` elemento do `Encoding` parâmetro dinâmico.</span><span class="sxs-lookup"><span data-stu-id="627d2-153">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="627d2-154">Exemplo</span><span class="sxs-lookup"><span data-stu-id="627d2-154">Example</span></span>

<span data-ttu-id="627d2-155">A exemplo a seguir mostra a `DynamicParameters` elemento do `Encoding` parâmetro dinâmico.</span><span class="sxs-lookup"><span data-stu-id="627d2-155">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

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