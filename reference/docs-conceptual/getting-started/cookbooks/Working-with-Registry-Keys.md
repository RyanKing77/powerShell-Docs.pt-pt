---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Trabalhar com Chaves do Registo
ms.assetid: 91bfaecd-8684-48b4-ad86-065dfe6dc90a
ms.openlocfilehash: a9d08f2f6b5803980dec45a4e266ad66879c8c8d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="working-with-registry-keys"></a>Trabalhar com Chaves do Registo

Uma vez que as chaves de registo são itens em unidades do Windows PowerShell, trabalhar com eles é muito semelhante para trabalhar com ficheiros e pastas. Uma diferença crítica é que todos os itens numa unidade do Windows PowerShell baseada no registo é um contentor, tal como uma pasta numa unidade de sistema de ficheiros. No entanto, as entradas de registo e os respetivos valores associados são propriedades dos itens, itens não distintos.

### <a name="listing-all-subkeys-of-a-registry-key"></a>Listar todas as subchaves da chave de registo

Pode mostrar todos os itens diretamente dentro de uma chave de registo utilizando **Get-ChildItem**. Adicionar o opcional **Force** parâmetro para apresentar ocultada ou itens de sistema. Por exemplo, este comando apresenta os itens diretamente na unidade do Windows PowerShell HKCU:, que corresponde ao ramo do registo em HKEY_CURRENT_USER:

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

Estes são visíveis em HKEY_CURRENT_USER no Editor de registo (Regedit.exe), as chaves de nível superior.

Também pode especificar este caminho de registo, especificando o nome do fornecedor de registo, seguido de "**::**". Nome completo do fornecedor de registo for **Microsoft.PowerShell.Core\\registo**, mas isto pode ser shortened para just **registo**. Qualquer um dos seguintes comandos irá listar o conteúdo diretamente em HKCU:

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

Estes comandos listam apenas os itens contidos diretamente, semelhante a utilização do Cmd.exe **DIR** comando ou **ls** na shell de UNIX. Mostrar itens que contêm, tem de especificar o **Recurse** parâmetro. Para listar todas as chaves de registo no HKCU, utilize o seguinte comando (esta operação pode demorar uma hora extremamente longa.):

```powershell
Get-ChildItem -Path hkcu:\ -Recurse
```

**Get-ChildItem** pode efetuar as capacidades de filtragem complexas através do respetivo **caminho**, **filtro**, **incluir**, e **excluir**parâmetros, mas esses parâmetros normalmente baseiam-se apenas no nome. Pode efetuar a filtragem complexas com base nas outras propriedades de itens utilizando o **Where-Object** cmdlet. O comando seguinte localiza todas as chaves dentro HKCU:\\Software que tenham mais do que uma subchave e também de ter exatamente quatro valores:

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

### <a name="copying-keys"></a>Copiar chaves

A copiar é feito com **Copy-Item**. O comando seguinte copia HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion e todas as suas propriedades para HKCU:\\, criar uma nova chave com o nome "CurrentVersion":

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

Se examinar esta nova chave no editor de registo ou utilizando **Get-ChildItem**, irá reparar que não dispõe de cópias das subchaves contidas na nova localização. Para copiar todo o conteúdo de um contentor, terá de especificar o **Recurse** parâmetro. Para tornar a recursiva de comando de cópia anterior, teria de utilizar este comando:

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

Pode continuar a utilizar outras ferramentas já tiver disponíveis para efetuar cópias de sistema de ficheiros. As ferramentas de edição de registo — incluindo reg.exe, regini.exe e regedit.exe—and objetos COM que suportam a edição de registo (por exemplo, a classe de StdRegProv WScript.Shell e do WMI) pode ser utilizada a partir do Windows PowerShell.

### <a name="creating-keys"></a>Criação de chaves

A criação de chaves novas no registo é mais simples do que criar um novo item no sistema de ficheiros. Uma vez que todas as chaves de registo são contentores, não tem de especificar o tipo de item Basta fornecer um caminho explícito, tais como:

```powershell
New-Item -Path hkcu:\software_DeleteMe
```

Também pode utilizar um caminho baseado em fornecedores para especificar uma chave:

```powershell
New-Item -Path Registry::HKCU_DeleteMe
```

### <a name="deleting-keys"></a>A eliminação de chaves

Eliminar itens é, essencialmente, igual para todos os fornecedores. Os seguintes comandos irão automaticamente remover itens:

```powershell
Remove-Item -Path hkcu:\Software_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

### <a name="removing-all-keys-under-a-specific-key"></a>Remover todas as chaves sob uma chave específica

Pode remover os itens que contêm utilizando **Remove-Item**, mas será solicitado para confirmar a remoção, se o item contém tudo o resto. Por exemplo, se vamos tentar eliminar o HKCU:\\CurrentVersion subchave criámos, vemos isto:

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Para eliminar os itens que contêm sem pedir confirmação, especifique o **-Recurse** parâmetro:

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

Se pretender remover todos os itens no HKCU:\\CurrentVersion mas não HKCU:\\CurrentVersion próprio, em vez disso, pode utilizar:

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```