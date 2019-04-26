---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Chamar os métodos de recursos de DSC diretamente
ms.openlocfilehash: cf237f638593706e5959e2bcc0d851b0e55baf0e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079630"
---
# <a name="calling-dsc-resource-methods-directly"></a>Chamar os métodos de recursos de DSC diretamente

>Aplica-se a: Windows PowerShell 5.0

Pode utilizar o [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) cmdlet para chamar diretamente as funções ou métodos de um recurso de DSC (a **Get-TargetResource**, **Set-TargetResource**e  **Test-TargetResource** funções de um recurso baseado em MOF, ou o **Obtenha**, **definir**, e **teste** métodos de um recurso baseado em classes).
Isto pode ser utilizado por terceiros, a que pretende utilizar recursos de DSC, ou como uma ferramenta útil durante o desenvolvimento de recursos.

Este cmdlet é normalmente utilizado em combinação com uma propriedade de metaconfiguration `refreshMode = 'Disabled'`, mas pode ser utilizado, não importa o que **refreshMode** está definido como.

Ao chamar o **Invoke-DscResource** cmdlet, especifique qual método ou função a ser chamada utilizando o **método** parâmetro. Especificar as propriedades do recurso, passando uma tabela de hash como o valor do **propriedade** parâmetro.

Seguem-se exemplos de chamadas diretas de métodos de recursos:

## <a name="ensure-a-file-is-present"></a>Certifique-se de que um ficheiro está presente

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a>Testar a que um ficheiro está presente

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

>**Nota:** Não é suportada a chamadas diretas de métodos de recursos compostos. Em vez disso, chame os métodos dos recursos subjacentes que compõem o recurso composto.

## <a name="see-also"></a>Veja Também
- [Escrever um recurso personalizado do DSC com o MOF](../resources/authoringResourceMOF.md)
- [Escrever um recurso personalizado do DSC com classes do PowerShell](../resources/authoringResourceClass.md)
- [Depurar os recursos de DSC](../troubleshooting/debugResource.md)