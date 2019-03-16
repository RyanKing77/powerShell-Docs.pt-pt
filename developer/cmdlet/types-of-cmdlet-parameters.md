---
title: Tipos de parâmetros de Cmdlet | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: f5781c0c03aca41d01a44598a9a8c00d6d21d2fd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059580"
---
# <a name="types-of-cmdlet-parameters"></a>Types of Cmdlet Parameters (Tipos de Parâmetros de Cmdlets)

Este tópico descreve os diferentes tipos de parâmetros que pode declarar nos cmdlets. Parâmetros do cmdlet podem ser posicional, com nome, obrigatória, opcional ou parâmetros.

## <a name="positional-and-named-parameters"></a>Parâmetros posicionais e com nome

Todos os parâmetros de cmdlet são parâmetros nomeados ou posicionais. Um parâmetro nomeado exige que digite o nome do parâmetro e o argumento ao chamar o cmdlet. Um parâmetro posicional requer apenas que digite os argumentos por ordem relativa. O sistema mapeia, em seguida, o primeiro argumento sem nome para o primeiro parâmetro posicional. O sistema mapeia o segundo argumento sem nome para o segundo parâmetro sem nome e assim por diante. Por predefinição, todos os parâmetros de cmdlet são nomeados parâmetros.

Para definir um parâmetro nomeado, omita o `Position` palavra-chave no **parâmetro** atributo declaração, conforme mostrado na seguinte declaração de parâmetro.

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Para definir um parâmetro posicional, adicione o `Position` palavra-chave no parâmetro declaração de atributo e, em seguida, especifique uma posição. No exemplo a seguir, o `UserName` parâmetro está declarado como um parâmetro posicional com posição 0. Isso significa que o primeiro argumento da chamada será vinculado automaticamente para este parâmetro.

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

> [!NOTE]
> Design de cmdlet boas recomenda que os parâmetros utilizados por mais ser declarada como parâmetros posicionais, para que o utilizador não tem de introduzir o nome do parâmetro, quando o cmdlet é executado.

Parâmetros nomeados e posicionais aceitam argumentos únicos ou vários argumentos separados por vírgulas. São permitidos vários argumentos apenas se o parâmetro aceita uma coleção, como uma matriz de cadeias de caracteres. Pode misturar os parâmetros posicionais e com nome no mesmo cmdlet. Neste caso, o sistema recupera os argumentos nomeados primeiro e, em seguida, tenta mapear o restante sem nome argumentos para os parâmetros posicionais.

Os comandos seguintes mostram as diferentes formas em que pode especificar único e vários argumentos para os parâmetros do `Get-Command` cmdlet. Tenha em atenção que nos dois últimos exemplos **-name** não precisa de ser especificado porque o `Name` parâmetro é definido como um parâmetro posicional.

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a>Parâmetros obrigatórios e opcionais

Também pode definir parâmetros do cmdlet como parâmetros obrigatórios ou opcionais. (Deve ser especificado um parâmetro obrigatório antes do tempo de execução do Windows PowerShell invoca o cmdlet.)  Por predefinição, os parâmetros são definidos como opcionais.

Para definir um parâmetro obrigatório, adicione a `Mandatory` palavra-chave no parâmetro declaração de atributo e defini-lo como `true`, conforme mostrado na seguinte declaração de parâmetro.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Para definir um parâmetro opcional, omita o `Mandatory` palavra-chave no **parâmetro** atributo declaração, conforme mostrado na seguinte declaração de parâmetro.

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a>Parâmetros de comutador

Windows PowerShell fornece uma [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) tipo que permite-lhe definir um parâmetro cujo valor é automaticamente definido como `false` se o parâmetro não for especificado, quando o cmdlet é chamado. Sempre que possível, use parâmetros em vez dos parâmetros booleanos.

Considere o exemplo a seguir. Por predefinição, vários cmdlets do Windows PowerShell não passar um objeto de saída pelo pipeline. No entanto, estes cmdlets têm um `PassThru` mudar o parâmetro que substitui o comportamento predefinido. Se o `PassThru` parâmetro for especificado, quando estes cmdlets são chamados, o cmdlet retorna um objeto de saída no pipeline.

Se é necessário o parâmetro tenha um valor padrão de `true` quando o parâmetro não for especificado na chamada, considere revertendo o sentido do parâmetro. Para obter exemplo, em vez de definir o atributo de parâmetro para um valor booleano `true`, declare a propriedade como o [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) escreva e, em seguida, defina o valor predefinido do parâmetro como `false`.

Para definir um parâmetro de mudança, declarar a propriedade como o [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) escreve, conforme mostrado no exemplo a seguir.

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

Para tornar o cmdlet agir sobre o parâmetro quando é especificado, utilize a seguinte estrutura dentro da entrada de métodos de processamento.

```csharp
protected override void ProcessRecord()
{
  WriteObject("Switch parameter test: " + userName + ".");
  if(goodbye)
  {
    WriteObject(" Goodbye!");
  }
} // End ProcessRecord
```

## <a name="see-also"></a>Veja Também

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
