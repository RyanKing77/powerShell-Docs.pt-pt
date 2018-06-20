---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Chamar os métodos de recursos de DSC diretamente
ms.openlocfilehash: 3ec3a3a8da615f45f3fdd28b1c1e46e312507ed5
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189623"
---
# <a name="calling-dsc-resource-methods-directly"></a>Chamar os métodos de recursos de DSC diretamente

>Aplica-se a: O Windows PowerShell 5.0

Pode utilizar o [Invoke-DscResource](https://technet.microsoft.com/library/mt517869.aspx) cmdlet para chamar diretamente as funções ou métodos de um recurso de DSC (o **Get-TargetResource**, **conjunto TargetResource**e  **Test-TargetResource** funções de um recurso com base no MOF, ou o **obter**, **definir**, e **teste** métodos de um recurso com base na classe).
Isto pode ser utilizado por terceiros, a que pretendem utilizar recursos de DSC ou como uma ferramenta útil enquanto programar recursos.

Este cmdlet é normalmente utilizado em combinação com uma propriedade de configuração meta `refreshMode = 'Disabled'`, mas podem ser utilizado, independentemente da que **refreshMode** está definido como.

Quando chamar o **Invoke-DscResource** cmdlet, especifique o método ou a função para chamar utilizando o **método** parâmetro. Especificar as propriedades do recurso transferindo uma tabela hash, como o valor de **propriedade** parâmetro.

Seguem-se exemplos de chamar directamente os métodos de recursos:

## <a name="ensure-a-file-is-present"></a>Certifique-se de que um ficheiro está presente

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a>Testar se um ficheiro está presente

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a>Obter o conteúdo do ficheiro

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

>**Nota:** diretamente chamar os métodos de composto de recurso não é suportado. Em vez disso, chame os métodos dos recursos subjacentes que compõem o recurso composto.

## <a name="see-also"></a>Consulte Também
- [Escrever um recurso personalizado de DSC com MOF](authoringResourceMOF.md)
- [Escrever um recurso personalizado de DSC com classes de PowerShell](authoringResourceClass.md)
- [Depurar os recursos de DSC](debugResource.md)