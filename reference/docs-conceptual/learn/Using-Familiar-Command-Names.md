---
ms.date: 08/27/2018
keywords: PowerShell, o cmdlet
title: Utilizar Nomes de Comandos Familiares
ms.assetid: 021e2424-c64e-4fa5-aa98-aa6405758d5d
ms.openlocfilehash: b61d647d882d4b2f7ea423a48319e3c104ce96c7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058000"
---
# <a name="using-familiar-command-names"></a>Utilizar nomes de comandos familiares

PowerShell suporta aliases para fazer referência aos comandos por nomes alternativos. Aliasing permite aos utilizadores com experiência de outros shells a utilizar nomes de comando comuns que já conhecem para operações semelhantes no PowerShell.

Aliasing associa um novo nome de outro comando. Por exemplo, o PowerShell tem uma função interna chamada `Clear-Host` que limpa a janela de saída. Pode digitar um a `cls` ou `clear` alias num prompt de comando. PowerShell interpreta estes aliases e executa o `Clear-Host` função.

Esta funcionalidade ajuda os utilizadores para aprender o PowerShell. Primeira, a maioria **cmd.exe** e usuários do Unix têm um grande repertório de comandos que já conhece os utilizadores por nome. Os equivalentes de PowerShell talvez não produzam resultados idênticos. No entanto, os resultados são fechar suficiente que os utilizadores podem fazer o trabalho sem saber o nome do comando do PowerShell. "Dedo memória" é outra das principais fontes de frustração quando um novo shell de comando de aprendizado. Se tiver utilizado **cmd.exe** durante anos, forma reflexiva pode digitar o `cls` comando para limpar o ecrã. Sem o alias para `Clear-Host`, recebe uma mensagem de erro e não saberá o que fazer para limpar a saída.

A lista seguinte mostra algumas do comum **cmd.exe** e comandos de Unix, que podem ser usados no PowerShell:

|||||
|-|-|-|-|
|cat|dir|Montagem|rm|
|cd|echo|mover|rmdir|
|chdir|Apagar|popd|Modo de suspensão|
|Limpar|h|ps|Ordenação|
|cls|Histórico|pushd|Tee|
|cópia|kill|pwd|tipo|
|del|lp|r|Escrita|
|diff|ls|ren||

O `Get-Alias` cmdlet mostra-lhe o nome real do comando do PowerShell nativo, associado com um alias.

```powershell
PS> Get-Alias cls
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Alias           cls -> Clear-Host
```

## <a name="interpreting-standard-aliases"></a>Interpretar os aliases padrão

Os aliases que descrevemos anteriormente foram projetados para nome de compatibilidade com outros shells de comando.
A maioria dos aliases incorporados no PowerShell foram concebidos para fins de brevidade. Nomes mais curtos são mais fáceis de tipo, mas são difíceis de ler se não sabe o que dizem respeito a.

Aliases de PowerShell tentam comprometer entre clareza e questões de brevidade. PowerShell utiliza um conjunto padrão de aliases para comum substantivos e verbos.

Abreviações de exemplo:

| Substantivo ou verbo | Abreviatura |
|--------------|--------------|
| Obter          | g            |
| Definir          | s            |
| Item         | posso            |
| Localização     | l            |
| Comando      | cm           |
| Alias        | al           |

Estes aliases são compreensíveis quando sabe os nomes abreviados.

| Nome do cmdlet    | Alias |
|----------------|-------|
| `Get-Item`     | gi    |
| `Set-Item`     | si    |
| `Get-Location` | gl    |
| `Set-Location` | sl    |
| `Get-Command`  | gcm   |
| `Get-Alias`    | gal   |

Quando estiver familiarizado com o aliasing de PowerShell, é fácil supor que o **sal** alias refere-se ao `Set-Alias`.

## <a name="creating-new-aliases"></a>Criação de novos aliases

Pode criar seu próprio aliases usando o `Set-Alias` cmdlet. Por exemplo, as seguintes declarações de criar os aliases de padrão de cmdlet discutidos anteriormente:

```powershell
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

Internamente, o PowerShell utiliza comandos semelhantes durante o arranque, mas estes aliases não são alteráveis.
Se tentar executar um desses comandos, obterá um erro explicando o que o alias não pode ser modificado. Por exemplo:

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```
