---
title: Criação de controles personalizados | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3baa406-cd33-4420-be5a-07ef09d93480
caps.latest.revision: 8
ms.openlocfilehash: 3504ab1d974c55e9279172d0e851961474ccb926
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844850"
---
# <a name="creating-custom-controls"></a><span data-ttu-id="ee25e-102">Creating Custom Controls (Criar Controlos Personalizados)</span><span class="sxs-lookup"><span data-stu-id="ee25e-102">Creating Custom Controls</span></span>

<span data-ttu-id="ee25e-103">Controles personalizados são os componentes mais flexíveis de um ficheiro de formatação.</span><span class="sxs-lookup"><span data-stu-id="ee25e-103">Custom controls are the most flexible components of a formatting file.</span></span> <span data-ttu-id="ee25e-104">Ao contrário da tabela, lista e ampla vistas que definem uma estrutura formal de dados, como uma tabela de dados, o controles personalizados permitem-lhe definir como peça individual de dados é exibida.</span><span class="sxs-lookup"><span data-stu-id="ee25e-104">Unlike table, list, and wide views that define a formal structure of data, such as a table of data, custom controls allow you to define how an individual piece of data is displayed.</span></span> <span data-ttu-id="ee25e-105">Pode definir um conjunto comum de controles personalizados que estão disponíveis para todas as vistas do arquivo formatação, pode definir a controles personalizados que estão disponíveis para uma vista específica ou pode definir um conjunto de controles que estão disponíveis para um grupo de objetos.</span><span class="sxs-lookup"><span data-stu-id="ee25e-105">You can define a common set of custom controls that are available to all the views of the formatting file, you can define custom controls that are available to a specific view, or you can define a set of controls that are available to a group of objects.</span></span>

## <a name="custom-control-example"></a><span data-ttu-id="ee25e-106">Exemplo de controle personalizado</span><span class="sxs-lookup"><span data-stu-id="ee25e-106">Custom Control Example</span></span>

<span data-ttu-id="ee25e-107">O exemplo seguinte mostra um controle personalizado que é definido no ficheiro Certificates.Format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="ee25e-107">The following example shows a custom control that is defined in the Certificates.Format.ps1xml file.</span></span> <span data-ttu-id="ee25e-108">Esse controle personalizado é utilizado para separar os [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) objetos apresentados numa vista de tabela.</span><span class="sxs-lookup"><span data-stu-id="ee25e-108">This custom control is used to separate the [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) objects displayed in a table view.</span></span>

```xml
<Controls>
  <Control>
    <Name>SignatureTypes-GroupingFormat</Name>
    <CustomControl>
      <CustomEntries>
        <CustomEntry>
          <CustomItem>
            <Frame>
              <LeftIndent>4</LeftIndent>
              <CustomItem>
                <Text AssemblyName="System.Management.Automation" BaseName="FileSystemProviderStrings"
                  ResourceId="DirectoryDisplayGrouping"/>
                <ExpressionBinding>
                  <ScriptBlock>split-path $_.Path</ScriptBlock>
                </ExpressionBinding>
                <NewLine/>
              </CustomItem>
            </Frame>
          </CustomItem>
        </CustomEntry>
      </CustomEntries>
    </CustomControl>
  </Control>
</Controls>

```

## <a name="see-also"></a><span data-ttu-id="ee25e-109">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="ee25e-109">See Also</span></span>

[<span data-ttu-id="ee25e-110">Escrever um ficheiro de formatação de PowerShell</span><span class="sxs-lookup"><span data-stu-id="ee25e-110">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
