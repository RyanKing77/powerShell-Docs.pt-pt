---
title: Estender objetos de resultado | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a252e0ec-d456-42d7-bd49-d6b8bc57f388
caps.latest.revision: 11
ms.openlocfilehash: 9c9d50c880f843e21621e5735c800e3afb48b2ad
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850961"
---
# <a name="extending-output-objects"></a>Extending Output Objects (Expandir Objetos de Resultado)

Pode estender os objetos do .NET Framework que são devolvidos por cmdlets, funções e scripts utilizando tipos de ficheiros (.ps1xml). Arquivos de tipos são ficheiros baseados em XML que lhe permite adicionar propriedades e métodos para objetos existentes. Por exemplo, o Windows PowerShell fornece o arquivo Types.ps1xml, adiciona elementos para vários objetos existentes do .NET Framework. O ficheiro de Types.ps1xml está localizado no diretório de instalação do Windows PowerShell (`$pshome`). Pode criar seu próprio arquivo de tipos de ampliar ainda mais esses objetos ou expandir a outros objetos. Quando expande um objeto ao utilizar um ficheiro de tipos, qualquer instância do objeto é estendida com os novos elementos.

## <a name="extending-the-systemarray-object"></a>Estendendo o objeto Array

O exemplo seguinte mostra como o Windows PowerShell estende a [System. Array](/dotnet/api/System.Array) objeto no arquivo Types.ps1xml. Por predefinição, [System. Array](/dotnet/api/System.Array) objetos têm uma `Length` propriedade que lista o número de objetos na matriz. No entanto, uma vez que o comprimento"nome" não descreve claramente a propriedade, o Windows PowerShell adiciona a `Count` propriedade de alias, que apresenta o mesmo valor que o `Length` propriedade. O XML a seguir adiciona o `Count` propriedade para o [Array](/dotnet/api/System.Array) tipo.

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>Length</ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>

```

Para ver esta nova propriedade de alias, utilize um [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) comando em qualquer matriz, como mostrado no exemplo a seguir.

```powershell
Get-Member -InputObject (1,2,3,4)
```

O comando devolve os seguintes resultados.
```output
Name           MemberType    Definition
----           ----------    ----------
Count          AliasProperty Count = Length
Address        Method        System.Object& Address(Int32 )
Clone          Method        System.Object Clone()
CopyTo         Method        System.Void CopyTo(Array array, Int32 index):
Equals         Method        System.Boolean Equals(Object obj)
Get            Method        System.Object Get(Int32 )
...
Length         Property      System.Int32 Length {get;}
```
Pode utilizar o `Count` propriedade ou o `Length` propriedade para determinar o número de objetos é numa matriz. Por exemplo:

```powershell
PS> (1, 2, 3, 4).Count
```

```output
4
```

```powershell
PS> (1, 2, 3, 4).Length
```

```output
4
```

## <a name="custom-types-files"></a>Ficheiros de tipos personalizados

Para criar um arquivo de tipos personalizados, comece por copiar um ficheiro existente de tipos. O novo ficheiro pode ter qualquer nome, mas tem de ter uma extensão de nome de ficheiro .ps1xml. Quando copiar o arquivo, pode colocar o novo ficheiro em qualquer diretório que esteja acessível para o Windows PowerShell, mas é útil colocar os arquivos no diretório de instalação do Windows PowerShell (`$pshome`) ou num subdiretório do diretório de instalação.

Para adicionar seus próprios tipos expandidos para o ficheiro, adicione um elemento de tipos para cada objeto que pretende expandir. Os tópicos seguintes fornecem exemplos.

- Para obter mais informações sobre como adicionar propriedades e os conjuntos de propriedades, consulte [Propriedades estendidas](./extending-properties-for-objects.md)

- Para obter mais informações sobre a adição de métodos, consulte [expandido métodos](./defining-default-methods-for-objects.md).

- Para obter mais informações sobre como adicionar conjuntos de membro, consulte [expandido define o membro](./defining-default-member-sets-for-objects.md).

Depois de definir seus próprios tipos expandidos, utilize um dos seguintes métodos para disponibilizar a seus objetos expandidos:

- Para disponibilizar o ficheiro de tipos expandida para a sessão atual, utilize o [TypeData atualização](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet para adicionar o novo ficheiro. Se pretender que os seus tipos de têm precedência sobre os tipos que são definidos em outros tipos de ficheiros (incluindo o arquivo Types.ps1xml), utilize o `PrependData` parâmetro do [atualização TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet.
- Para disponibilizar o ficheiro de tipos expandida para todas as futuras sessões, adicione o ficheiro de tipos a um módulo, exportar a sessão atual ou adicione a [TypeData atualização](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) comando ao seu perfil do Windows PowerShell.

## <a name="signing-types-files"></a>Assinatura de tipos de ficheiros

Ficheiros de tipos devem ser assinados digitalmente para impedir a adulteração, porque o XML pode incluir os blocos de script. Para obter mais informações sobre a adição de assinaturas digitais, consulte [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)

## <a name="see-also"></a>Consulte Também

[Definir propriedades predefinidas para objetos](./extending-properties-for-objects.md)

[Definindo os métodos de padrão para objetos](./defining-default-methods-for-objects.md)

[Definir conjuntos de membro predefinido de objetos](./defining-default-member-sets-for-objects.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
