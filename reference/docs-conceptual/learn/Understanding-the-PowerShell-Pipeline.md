---
ms.date: 08/23/2018
keywords: PowerShell, o cmdlet
title: Compreender os pipelines do PowerShell
ms.openlocfilehash: 3033a4fe1a704fbbfa76e6d38662c8b22c3dbd9b
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030385"
---
# <a name="understanding-pipelines"></a>Noções básicas sobre pipelines

Pipelines atuam como uma série de segmentos ligados de pipe. Movendo o pipeline de itens passam por cada segmento. Para criar um pipeline do PowerShell, se conectar a comandos em conjunto com o operador pipe "|". O resultado de cada comando é utilizado como entrada para o próximo comando.

A notação utilizada para pipelines é similar a notação utilizada de outros shells. À primeira vista, talvez não seja aparente como os pipelines são diferentes no PowerShell. Apesar de ver o texto na tela, o PowerShell canaliza objetos, e não texto entre comandos.

## <a name="the-powershell-pipeline"></a>O pipeline do PowerShell

Os pipelines são indiscutivelmente o conceito mais valioso utilizado nas interfaces de linha de comandos. Quando usada corretamente, pipelines de reduzem o esforço de usar comandos complexos e tornam mais fácil ver o fluxo de trabalho para os comandos. Cada comando num pipeline (chamado de um elemento de pipeline) passa o respetivo resultado para o comando seguinte no pipeline, item a item. Comandos não é preciso lidar com mais de um item por vez. O resultado é o consumo de recursos reduzida e a capacidade para começar a obter o resultado imediatamente.

Por exemplo, se usar o `Out-Host` cmdlet para forçar uma apresentação de página por página de saída de outro comando, o aspeto de saída apenas como o texto normal exibido na tela, dividida em páginas:

```powershell
Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging
```

```Output
    Directory: C:\WINDOWS\system32

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        4/12/2018   2:15 AM                0409
d-----        5/13/2018  11:31 PM                1033
d-----        4/11/2018   4:38 PM                AdvancedInstallers
d-----        5/13/2018  11:13 PM                af-ZA
d-----        5/13/2018  11:13 PM                am-et
d-----        4/11/2018   4:38 PM                AppLocker
d-----        5/13/2018  11:31 PM                appmgmt
d-----        7/11/2018   2:05 AM                appraiser
d---s-        4/12/2018   2:20 AM                AppV
d-----        5/13/2018  11:10 PM                ar-SA
d-----        5/13/2018  11:13 PM                as-IN
d-----        8/14/2018   9:03 PM                az-Latn-AZ
d-----        5/13/2018  11:13 PM                be-BY
d-----        5/13/2018  11:10 PM                BestPractices
d-----        5/13/2018  11:10 PM                bg-BG
d-----        5/13/2018  11:13 PM                bn-BD
d-----        5/13/2018  11:13 PM                bn-IN
d-----        8/14/2018   9:03 PM                Boot
d-----        8/14/2018   9:03 PM                bs-Latn-BA
d-----        4/11/2018   4:38 PM                Bthprops
d-----        4/12/2018   2:19 AM                ca-ES
d-----        8/14/2018   9:03 PM                ca-ES-valencia
d-----        5/13/2018  10:46 PM                CatRoot
d-----        8/23/2018   5:07 PM                catroot2
<SPACE> next page; <CR> next line; Q quit
...
```

Paginação também reduz a utilização de CPU porque o processamento é transferida para o `Out-Host` cmdlet quando tem uma página concluída, pronta para apresentar. Os cmdlets que como prefixo no pipeline de interromper a execução até que a página seguinte da saída esteja disponível.

Pode ver como piping afeta a utilização de CPU e memória no Gerenciador de tarefas do Windows ao comparar os seguintes comandos:

- `Get-ChildItem C:\Windows -Recurse`
- `Get-ChildItem C:\Windows -Recurse | Out-Host -Paging`

> [!NOTE]
> O **paginação** parâmetro não é suportado por todos os anfitriões do PowerShell. Por exemplo, quando tenta utilizar o **paginação** parâmetro no ISE do PowerShell, verá o seguinte erro:
>
> ```Output
> out-lineoutput : The method or operation is not implemented.
> At line:1 char:1
> + Get-ChildItem C:\Windows -Recurse | Out-Host -Paging
> + ~~~~~~~~~~~~~~~~~~~~~~~~~~~
>     + CategoryInfo          : NotSpecified: (:) [out-lineoutput], NotImplementedException
>     + FullyQualifiedErrorId : System.NotImplementedException,Microsoft.PowerShell.Commands.OutLineOutputCommand
> ```

## <a name="objects-in-the-pipeline"></a>Objetos no pipeline

Quando executa um cmdlet no PowerShell, verá a saída de texto porque é necessário representar objetos como texto numa janela de consola. A saída de texto não pode exibir todas as propriedades do objeto a ser o resultado.

Por exemplo, considere o `Get-Location` cmdlet. Se executar `Get-Location` enquanto sua localização atual é a raiz da unidade C, verá a seguinte saída:

```
PS> Get-Location

Path
----
C:\
```

A saída de texto é um resumo das informações, não uma representação completa do objeto retornado por `Get-Location`. O cabeçalho na saída é adicionado pelo processo que formata os dados para exibição na tela.

Quando canalizar a saída para o `Get-Member` cmdlet obtém informações sobre o objeto devolvido pelo `Get-Location`.

```powershell
Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

`Get-Location` Devolve um **PathInfo** objeto que contém o caminho atual e outras informações.
