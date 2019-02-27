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
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a>How to Add Dynamic Parameters to a Provider Help Topic (Como Adicionar Parâmetros Dinâmicos ao Tópico de Ajuda de um Fornecedor)

Esta secção explica como preencher os **parâmetros DINÂMICOS** seção um tópico de ajuda do fornecedor.

*Os parâmetros dinâmicos* são parâmetros de um cmdlet ou ser especificada de função que estão disponíveis apenas em condições.

Os parâmetros dinâmicos que estão documentados num tópico de ajuda do provedor são os parâmetros dinâmicos que o fornecedor adiciona a função ou o cmdlet quando a função ou o cmdlet é utilizada na unidade de fornecedor.

Os parâmetros dinâmicos também podem ser documentados na ajuda do cmdlet personalizado para um fornecedor. Ao escrever a ajuda do provedor e ajuda de cmdlets personalizados para um fornecedor, incluem a documentação de parâmetro dinâmico em ambos os documentos. Para obter mais informações sobre a ajuda do cmdlet personalizado, consulte [escrita Windows PowerShell personalizado ajuda do Cmdlet para fornecedores](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).

Se um fornecedor não implementa qualquer parâmetros dinâmicos, o tópico de ajuda do provedor contém vazio `DynamicParameters` elemento.

### <a name="to-add-dynamic-parameters"></a>Para adicionar parâmetros dinâmicos

1. Na *AssemblyName*help.xml. dll do ficheiro, dentro da `providerHelp` elemento, adicionar um `DynamicParameters` elemento. O `DynamicParameters` elemento deve aparecer após o `Tasks` elemento e antes do `RelatedLinks` elemento.

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

   Se o fornecedor não implementa qualquer parâmetros dinâmicos, o `DynamicParameters` elemento pode estar vazio.

2. Dentro de `DynamicParameters` elemento, para cada parâmetro dinâmico, adicionar um `DynamicParameter` elemento.

   Por exemplo:

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. Em cada `DynamicParameter` elemento, adicione um `Name` e `CmdletSupported` elemento.

   |Nome do Elemento|Descrição|
   |------------------|-----------------|
   |Nome|Especifica o nome do parâmetro.|
   |CmdletSupported|Especifica os cmdlets em que o parâmetro é válido. Escreva uma lista separada por vírgulas de nomes de cmdlet.|

   Por exemplo, os seguintes documentos XML a `Encoding` parâmetro dinâmico, que o fornecedor do sistema de ficheiros do Windows PowerShell adiciona para o `Add-Content`, `Get-Content`, `Set-Content` cmdlets.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. Em cada `DynamicParameter` elemento, adicione um `Type` elemento. O `Type` elemento é um contentor para o `Name` elemento que contém o tipo de .NET do valor do parâmetro dinâmico.

   Por exemplo, o XML a seguir mostra que o tipo de .NET do `Encoding` parâmetro dinâmico é o [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeração.

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

5. Adicionar o `Description` elemento, que contém uma breve descrição do parâmetro dinâmico. Ao redigir a descrição, utilize as diretrizes prescritas para todos os parâmetros de cmdlet em [como adicionar informações de parâmetro](./how-to-add-parameter-information.md).

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

6. Adicionar o `PossibleValues` elemento e os respetivos elementos subordinados. Juntos, esses elementos descrevem os valores do parâmetro dinâmico. Este elemento foi concebido para valores enumerados. Se o parâmetro dinâmico não tem um valor, tal como é o caso de um parâmetro ou os valores não não possível enumerar, adicionar vazio `PossibleValues` elemento.

   A tabela seguinte lista e descreve o `PossibleValues` elemento e os respetivos elementos subordinados.

   |Nome do Elemento|Descrição|
   |------------------|-----------------|
   |PossibleValues|Este elemento é um contentor. Elementos filho são descritos abaixo. Adicionar um `PossibleValues` elemento cada tópico de ajuda do fornecedor. O elemento pode estar vazio.|
   |PossibleValue|Este elemento é um contentor. Elementos filho são descritos abaixo. Adicionar um `PossibleValue` elemento para cada valor do parâmetro dinâmico.|
   |Valor|Especifica o nome do valor.|
   |Descrição|Esse elemento contém um `Para` elemento. O texto a `Para` elemento descreve o valor com o nome no `Value` elemento.|

   Por exemplo, o XML a seguir mostra um `PossibleValue` elemento do `Encoding` parâmetro dinâmico.

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

A exemplo a seguir mostra a `DynamicParameters` elemento do `Encoding` parâmetro dinâmico.

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