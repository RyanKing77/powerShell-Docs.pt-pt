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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066690"
---
# <a name="creating-custom-controls"></a>Creating Custom Controls (Criar Controlos Personalizados)

Controles personalizados são os componentes mais flexíveis de um ficheiro de formatação. Ao contrário da tabela, lista e ampla vistas que definem uma estrutura formal de dados, como uma tabela de dados, o controles personalizados permitem-lhe definir como peça individual de dados é exibida. Pode definir um conjunto comum de controles personalizados que estão disponíveis para todas as vistas do arquivo formatação, pode definir a controles personalizados que estão disponíveis para uma vista específica ou pode definir um conjunto de controles que estão disponíveis para um grupo de objetos.

## <a name="custom-control-example"></a>Exemplo de controle personalizado

O exemplo seguinte mostra um controle personalizado que é definido no ficheiro Certificates.Format.ps1xml. Esse controle personalizado é utilizado para separar os [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) objetos apresentados numa vista de tabela.

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

## <a name="see-also"></a>Veja Também

[Escrever um ficheiro de formatação de PowerShell](./writing-a-powershell-formatting-file.md)
