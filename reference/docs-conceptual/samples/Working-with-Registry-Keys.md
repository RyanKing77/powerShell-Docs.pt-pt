---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Trabalhar com Chaves do Registo
ms.assetid: 91bfaecd-8684-48b4-ad86-065dfe6dc90a
ms.openlocfilehash: a9d08f2f6b5803980dec45a4e266ad66879c8c8d
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405581"
---
# <a name="working-with-registry-keys"></a>Trabalhar com Chaves do Registo

Como as chaves de registo são itens em unidades do Windows PowerShell, trabalhar com eles é muito semelhante a trabalhar com ficheiros e pastas. Uma diferença fundamental é que todos os itens numa unidade do Windows PowerShell baseada no registo são um contentor, tal como uma pasta numa unidade de sistema de ficheiros. No entanto, as entradas do Registro e seus valores associados são propriedades dos itens, itens não distintos.

### <a name="listing-all-subkeys-of-a-registry-key"></a>A listagem de todas as subchaves da chave de registo

Pode mostrar todos os itens diretamente dentro de uma chave do Registro usando **Get-ChildItem**. Adicionar o opcional **força** parâmetro para apresentar ocultada ou itens de sistema. Por exemplo, este comando apresenta os itens diretamente na unidade do Windows PowerShell HKCU:, que corresponde do ramo de registo HKEY_CURRENT_USER:

```
PS> Get-ChildItem -Path hkcu:\

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

SKC  VC Name                           Property
---  -- ----                           --------
  2   0 AppEvents                      {}
  7  33 Console                        {ColorTable00, ColorTable01, ColorTab...
 25   1 Control Panel                  {Opened}
  0   5 Environment                    {APR_ICONV_PATH, INCLUDE, LIB, TEMP...}
  1   7 Identities                     {Last Username, Last User ...
  4   0 Keyboard Layout                {}
...
```

Estas são as chaves de nível superior visíveis em HKEY_CURRENT_USER no Editor de registo (Regedit.exe).

Também pode especificar este caminho de registo, especificando o nome do fornecedor de registo, seguido por "**::**". O nome completo do fornecedor de registo é **Microsoft.PowerShell.Core\\Registro**, mas isso pode ser baixou para just **registo**. Qualquer um dos seguintes comandos irá listar o conteúdo diretamente em HKCU:

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

Estes comandos listam apenas os itens contidos diretamente, bem similar ao uso do Cmd.exe **DIR** comando ou **ls** numa shell de UNIX. Para mostrar os itens contidos, tem de especificar o **Recurse** parâmetro. Para listar todas as chaves de Registro em HKCU, utilize o seguinte comando (esta operação pode demorar muito tempo.):

```powershell
Get-ChildItem -Path hkcu:\ -Recurse
```

**Get-ChildItem** pode efetuar as capacidades de filtragem complexas por meio de seu **caminho**, **filtro**, **Include**, e **excluir**parâmetros, mas esses parâmetros são, normalmente, com base apenas no nome. Pode efetuar uma filtragem complexa com base no outras propriedades de itens com o **Where-Object** cmdlet. O comando seguinte localiza todas as chaves em HKCU:\\Software que não mais do que uma subchave e também de ter exatamente quatro valores:

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

### <a name="copying-keys"></a>Copiar chaves

A copiar é feita com **Copy-Item**. O seguinte comando copia HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion e todas as respetivas propriedades para HKCU:\\, criar uma nova chave denominada "CurrentVersion":

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

Se examinar esta chave de novo no editor do Registro ou usando **Get-ChildItem**, irá reparar que não tem cópias das subchaves contidas na nova localização. Para poder copiar o conteúdo inteiro de um contentor, tem de especificar o **Recurse** parâmetro. Para tornar a recursiva de comando de cópia anterior, usaria este comando:

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

Pode continuar a utilizar outras ferramentas que já tem disponível para efetuar cópias de sistema de ficheiros. Qualquer registo de ferramentas de edição — incluindo reg.exe regini.exe e regedit.exe—and objetos COM que o suporte à edição de registo (por exemplo, a classe StdRegProv de Wscript. shell e do WMI) pode ser usado no Windows PowerShell.

### <a name="creating-keys"></a>Criação de chaves

A criação de novas chaves no Registro é mais simples do que criar um novo item num sistema de ficheiros. Uma vez que todas as chaves de registo são contentores, não é necessário especificar o tipo de item; simplesmente fornecer um caminho explícito, tais como:

```powershell
New-Item -Path hkcu:\software_DeleteMe
```

Também pode utilizar um caminho baseado em provedor para especificar uma chave:

```powershell
New-Item -Path Registry::HKCU_DeleteMe
```

### <a name="deleting-keys"></a>A eliminar chaves

A eliminar itens é essencialmente o mesmo para todos os fornecedores. Os seguintes comandos irão automaticamente remover itens:

```powershell
Remove-Item -Path hkcu:\Software_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

### <a name="removing-all-keys-under-a-specific-key"></a>Remover todas as chaves numa chave específica

Pode remover itens contidos através de **Remove-Item**, mas será solicitado a confirmar a remoção, se o item contiver qualquer outra coisa. Por exemplo, se tentar eliminar o HKCU:\\CurrentVersion subchave que criámos, vemos isso:

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Para eliminar os itens contidos sem pedir confirmação, especifique a **-Recurse** parâmetro:

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

Se quisesse remover todos os itens dentro do HKCU:\\CurrentVersion mas não HKCU:\\CurrentVersion em si, em vez disso, poderia usar:

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```