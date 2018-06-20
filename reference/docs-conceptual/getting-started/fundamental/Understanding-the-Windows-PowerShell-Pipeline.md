---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Noções sobre o Pipeline do Windows PowerShell
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
ms.openlocfilehash: c3f1d17432cf3a77c0f5ecae137a4233a28a19d7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951074"
---
# <a name="understanding-the-windows-powershell-pipeline"></a>Noções sobre o Pipeline do Windows PowerShell
Piping em praticamente qualquer lugar funciona no Windows PowerShell. Apesar de ver o texto no ecrã, o Windows PowerShell pipe não texto entre comandos. Em vez disso, este encaminha objetos.

A notação utilizada para pipelines é semelhante à utilizada na outros shells, por isso, à primeira vista, pode não ser aparente que do Windows PowerShell apresenta um novo. Por exemplo, se utilizar o **out-anfitrião** cmdlet para forçar uma apresentação da página pela página de saída do comando de outro, a procura de saída apenas como o texto normal apresentado no ecrã, dividido dos páginas:

```
PS> Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\system32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2005-10-22  11:04 PM        315 $winnt$.inf
-a---        2004-08-04   8:00 AM      68608 access.cpl
-a---        2004-08-04   8:00 AM      64512 acctres.dll
-a---        2004-08-04   8:00 AM     183808 accwiz.exe
-a---        2004-08-04   8:00 AM      61952 acelpdec.ax
-a---        2004-08-04   8:00 AM     129536 acledit.dll
-a---        2004-08-04   8:00 AM     114688 aclui.dll
-a---        2004-08-04   8:00 AM     194048 activeds.dll
-a---        2004-08-04   8:00 AM     111104 activeds.tlb
-a---        2004-08-04   8:00 AM       4096 actmovie.exe
-a---        2004-08-04   8:00 AM     101888 actxprxy.dll
-a---        2003-02-21   6:50 PM     143150 admgmt.msc
-a---        2006-01-25   3:35 PM      53760 admparse.dll
<SPACE> next page; <CR> next line; Q quit
...
```

O Out-Host-comando de paginação é um elemento de pipeline útil sempre que ter demorado resultado que pretende apresentar lentamente. É especialmente útil se a operação é muito intensivas em CPU. Porque o processamento é transferido para o Out-anfitrião cmdlet quando tem uma página concluída, pronta para apresentar, os cmdlets que precedê-lo no pipeline de parar a operação até a página seguinte do resultado está disponível. Pode ver esta se utilizar o Gestor de tarefas do Windows para monitorizar a utilização da CPU e memória do Windows PowerShell.

Execute o seguinte comando: **Get-ChildItem c\\Windows-Recurse**. Comparar a utilização da CPU e memória a este comando: **Get-ChildItem c\\Windows-Recurse | Out-alojar-paginação**. O que vê no ecrã é o texto, mas isto acontece porque é necessário representar objetos como texto numa janela de consola. Isto é apenas uma representação que é realmente a acontecer no interior do Windows PowerShell. Por exemplo, considere o cmdlet Get-localização. Se escrever **Get-Location** enquanto a sua localização atual é a raiz da unidade C, verá a seguinte saída:

```
PS> Get-Location

Path
----
C:\
```

Se o Windows PowerShell encaminhados texto, emitir um comando, tal como **Get-Location | Out-anfitrião**, seria passam do **Get-Location** para **out-anfitrião** um conjunto de carateres na ordem são apresentadas onscreen. Por outras palavras, se pretendesse ignorar as informações de cabeçalho, **out-anfitrião** receberia primeiro o caráter '**C'**, em seguida, o caráter '**:'**, em seguida, o caráter ' **\\'**. O **out-anfitrião** cmdlet não foi possível determinar o que significa que a associar a saída de carateres, a **Get-Location** cmdlet.

Em vez de utilizar o texto para permitir que os comandos num pipeline comunicar, o Windows PowerShell utiliza objetos. De ponto de vista de um utilizador, objetos de pacote informações relacionadas com um formulário que torna mais fácil manipular informações como uma unidade e extrair itens específicos que precisa.

O **Get-Location** comando não devolve o texto que contém o caminho atual. Devolve um pacote de informações chamados um **PathInfo** objeto que contém o caminho atual, juntamente com outras informações. O **out-anfitrião** cmdlet, em seguida, envia esta **PathInfo** objeto para o ecrã e o Windows PowerShell decide que as informações a apresentar e como apresentá-lo com base nas suas regras de formatação.

Na verdade, as informações de cabeçalho de saída pelo **Get-Location** cmdlet é adicionado apenas no final do processo, como parte do processo de formatação os dados para apresentar onscreen. O que vê onscreen são um resumo de informações e não uma representação do objeto de saída completa.

Uma vez que poderá obter mais informações resultado de um Windows PowerShell comando que é o que veem apresentados na janela da consola, como pode obter os elementos não visível? Como visualizar os dados adicionais E e se pretende ver os dados num formato diferente do Windows PowerShell um normalmente utiliza?

O resto deste capítulo descreve como pode detetar a estrutura dos objetos específicos do Windows PowerShell, selecionar itens específicos e formatação-los para apresentar mais fácil e como enviar estas informações para localizações de saída alternativo, tal como ficheiros e impressoras.