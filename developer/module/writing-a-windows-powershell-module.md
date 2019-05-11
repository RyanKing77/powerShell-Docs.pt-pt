---
title: Escrever um módulo do Windows PowerShell | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 0b7263ea19745e902fff04b993933e443d4d6333
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229339"
---
# <a name="writing-a-windows-powershell-module"></a>Writing a Windows PowerShell Module (Escrever um Módulo do Windows PowerShell)

Este documento foi escrito para os administradores, desenvolvedores de script e desenvolvedores de cmdlet que precisam para empacotar e distribuir seus cmdlets do Windows PowerShell. Ao utilizar módulos do Windows PowerShell, pode empacotar e distribuir as suas soluções do Windows PowerShell sem utilizar uma linguagem compilada.

Módulos do Windows PowerShell permitem que a partição, organizar e abstraem o código do Windows PowerShell em unidades independentes e reutilizáveis. Com estas unidades reutilizáveis, pode partilhar facilmente os seus módulos diretamente com outras pessoas. Se for um desenvolvedor de script, também pode reempacotar os módulos de terceiros para criar aplicativos personalizados baseados em script. Módulos, semelhantes aos módulos em outras linguagens de script como Perl e Python, ativar soluções de script prontos para produção que utilizam componentes reutilizáveis e redistribuíveis, com o benefício adicional de que lhe permite reempacotar e abstrair vários componentes a Crie soluções personalizadas.

Em sua forma mais básica, Windows PowerShell irá tratar qualquer código de script do Windows PowerShell válido guardado num ficheiro. psm1 como um módulo. PowerShell também automaticamente irão tratar qualquer assembly do cmdlet binários como um módulo. No entanto, também pode utilizar um módulo (ou mais especificamente, um manifesto de módulo) para agrupar uma solução inteira. Os seguintes cenários descrevem as utilizações típicas para módulos do Windows PowerShell.

### <a name="libraries"></a>Bibliotecas

Módulos podem ser utilizados para empacotar e distribuir bibliotecas coesos de funções que realizam tarefas comuns. Normalmente, os nomes dessas funções partilham um ou mais substantivos que refletem a tarefa comum que são utilizadas. Essas funções também podem ser semelhantes a classes do .NET Framework que podem ter público e membros privados. Por exemplo, uma biblioteca pode conter um conjunto de funções para as transferências de ficheiros. Neste caso, o substantivo que reflete a tarefa comum pode ser "arquivo".

### <a name="configuration"></a>Configuração

Módulos podem ser utilizados para personalizar o seu ambiente através da adição de cmdlets específicos, provedores, funções e variáveis.

### <a name="compiled-code-development-and-distribution"></a>Desenvolvimento de código compilado e distribuição

Os desenvolvedores do cmdlet e o fornecedor podem utilizar os módulos para testar e distribuir seus códigos compilados sem a necessidade de criar o snap-ins. Importar o assembly que contém o código compilado como um módulo (um módulo de binário) sem a necessidade de criar e registar o snap-ins.

## <a name="see-also"></a>Veja Também

[Noções básicas sobre um módulo do Windows PowerShell](./understanding-a-windows-powershell-module.md)

[Como escrever um módulo de Script do PowerShell](./how-to-write-a-powershell-script-module.md)

[Como escrever um módulo de PowerShell binário](./how-to-write-a-powershell-binary-module.md)

[Como escrever um manifesto de módulo do PowerShell](how-to-write-a-powershell-module-manifest.md)

[Modificar o caminho de instalação PSModulePath](./modifying-the-psmodulepath-installation-path.md)

[Importar um módulo do PowerShell](./importing-a-powershell-module.md)

[Instalar um módulo do PowerShell](./installing-a-powershell-module.md)
