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
ms.openlocfilehash: cc4877242a16a9caa99564aeaae985f85e38791e
ms.sourcegitcommit: ffcc1c55f5b3adc063353cb75f2a2183acc2234a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70737590"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a>How to Add Dynamic Parameters to a Provider Help Topic (Como Adicionar Parâmetros Dinâmicos ao Tópico de Ajuda de um Fornecedor)

Esta seção explica como preencher a seção de **parâmetros dinâmicos** de um tópico de ajuda do provedor.

*Parâmetros dinâmicos* são parâmetros de um cmdlet ou função que estão disponíveis somente em condições especificadas.

Os parâmetros dinâmicos documentados em um tópico de ajuda do provedor são os parâmetros dinâmicos que o provedor adiciona ao cmdlet ou função quando o cmdlet ou a função é usada na unidade do provedor.

Os parâmetros dinâmicos também podem ser documentados na ajuda do cmdlet personalizado para um provedor. Ao escrever a ajuda do provedor e a ajuda do cmdlet personalizado para um provedor, inclua a documentação do parâmetro dinâmico em ambos os documentos. Para obter mais informações sobre a ajuda de cmdlets personalizados, consulte [escrevendo a ajuda do cmdlet personalizado do Windows PowerShell para provedores](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).

Se um provedor não implementar nenhum parâmetro dinâmico, o tópico da ajuda do provedor conterá `DynamicParameters` um elemento vazio.

### <a name="to-add-dynamic-parameters"></a>Para adicionar parâmetros dinâmicos

1. No arquivo *AssemblyName*. dll-help. xml, dentro do `providerHelp` elemento, adicione um `DynamicParameters` elemento. O `DynamicParameters` elemento deve aparecer após o `Tasks` elemento e antes do `RelatedLinks` elemento.

   Por exemplo:

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

   Se o provedor não implementar nenhum parâmetro dinâmico, o `DynamicParameters` elemento poderá ficar vazio.

2. Dentro do `DynamicParameters` elemento, para cada parâmetro dinâmico, adicione um `DynamicParameter` elemento.

   Por exemplo:

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. Em cada `DynamicParameter` elemento, adicione um `Name` elemento `CmdletSupported` e.

   |Nome do Elemento|Descrição|
   |------------------|-----------------|
   |Nome|Especifica o nome do parâmetro.|
   |CmdletSupported|Especifica os cmdlets nos quais o parâmetro é válido. Digite uma lista separada por vírgulas de nomes de cmdlet.|

   Por exemplo, o XML a seguir documenta `Encoding` o parâmetro dinâmico que o provedor do sistema de arquivos do `Add-Content`Windows PowerShell `Set-Content` adiciona aos cmdlets, `Get-Content`,.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. Em cada `DynamicParameter` elemento, adicione um `Type` elemento. O `Type` elemento é um contêiner para o `Name` elemento que contém o tipo .net do valor do parâmetro dinâmico.

   Por exemplo, o XML a seguir mostra que o tipo .net do `Encoding` parâmetro dinâmico é a enumeração [Microsoft. PowerShell. Commands. FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) .

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

5. Adicione o `Description` elemento, que contém uma breve descrição do parâmetro dinâmico. Ao compor a descrição, use as diretrizes indicadas para todos os parâmetros de cmdlet em [como adicionar informações de parâmetro](./how-to-add-parameter-information.md).

   Por exemplo, o XML a seguir inclui a descrição do `Encoding` parâmetro dinâmico.

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

6. Adicione o `PossibleValues` elemento e seus elementos filho. Juntos, esses elementos descrevem os valores do parâmetro dinâmico. Esse elemento é projetado para valores enumerados. Se o parâmetro dinâmico não receber um valor, como é o caso com um parâmetro de opção, ou os valores não podem ser enumerados, adicione um elemento `PossibleValues` vazio.

   A tabela a seguir lista e descreve `PossibleValues` o elemento e seus elementos filho.

   |Nome do Elemento|Descrição|
   |------------------|-----------------|
   |PossibleValues|Este elemento é um contêiner. Seus elementos filho são descritos abaixo. Adicione um `PossibleValues` elemento a cada tópico da ajuda do provedor. O elemento pode estar vazio.|
   |Possível|Este elemento é um contêiner. Seus elementos filho são descritos abaixo. Adicione um `PossibleValue` elemento para cada valor do parâmetro dinâmico.|
   |Valor|Especifica o nome do valor.|
   |Descrição|Este elemento contém um `Para` elemento. O texto no `Para` elemento descreve o valor que é nomeado `Value` no elemento.|

   Por exemplo, o XML a seguir mostra `PossibleValue` um elemento `Encoding` do parâmetro dinâmico.

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

## <a name="example"></a>Exemplo

O exemplo a seguir mostra `DynamicParameters` o elemento `Encoding` do parâmetro dinâmico.

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