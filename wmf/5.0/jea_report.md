---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
ms.openlocfilehash: f3c218fc668e35fa50047459d8031d77cdf985a2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="reporting-on-jea"></a>No JEA de relatórios
Para gerar relatórios sobre o estado da configuração JEA, pode utilizar:
1.  **Get-PSSessionConfiguration** devolver uma lista de todos os registado pontos finais num computador especificado.
2.  **Get-PSSessionCapability** para elaborar relatórios sobre as capacidades de qualquer utilizador especificado tem um ponto final específico.

Eis um exemplo de **Get-PSSessionCapability**:
```powershell
Get-PSSessionCapability -ConfigurationName Maintenance -Username "CONTOSO\JohnDoe"

CommandType     Name                                               Version    Source           
-----------     ----                                               -------    ------           
Alias           clear -> Clear-Host                                                            
Alias           cls -> Clear-Host                                                              
Alias           exsn -> Exit-PSSession                                                         
Alias           gcm -> Get-Command                                                             
Alias           measure -> Measure-Object                                                      
Alias           select -> Select-Object                                                        
Function        Clear-Host                                                                     
Function        Exit-PSSession                                                                 
Function        Get-Command                                                                    
Function        Get-FormatData                                                                 
Function        Get-Help                                                                       
Function        Get-UserInfo                                                                   
Function        Measure-Object                                                                 
Function        Out-Default                                                                    
Function        Select-Object                                                                  
Cmdlet          Restart-Service                                    3.0.0.0 Microsof...


```

Para elaborar relatórios sobre o _ações_ utilizadores demorou durante uma sessão JEA, pode:
1. Ativar as transcrições "over-a-por cima ombro ficará" para esse ponto final JEA e consulte o diretório de transcript para um registo das ações de cada utilizador completo
2. Ativar o registo de módulo do PowerShell e Inspecione os registos de eventos do PowerShell.

