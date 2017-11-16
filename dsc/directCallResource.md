---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: "Chamar os métodos de recursos de DSC diretamente"
ms.openlocfilehash: ab00e66d526eda244500a41e450c56b0151274ee
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="calling-dsc-resource-methods-directly"></a>Chamar os métodos de recursos de DSC diretamente

>Aplica-se a: O Windows PowerShell 5.0

Pode utilizar o [Invoke-DscResource](https://technet.microsoft.com/en-us/library/mt517869.aspx) cmdlet para chamar diretamente as funções ou métodos de um recurso de DSC (o **Get-TargetResource**, **conjunto TargetResource**e  **Test-TargetResource** funções de um recurso com base no MOF, ou o **obter**, **definir**, e **teste** métodos de um recurso com base na classe). Isto pode ser utilizado por terceiros, a que pretendem utilizar recursos de DSC ou como uma ferramenta útil enquanto programar recursos. 

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
- [A depuração de recursos de DSC](debugResource.md)

