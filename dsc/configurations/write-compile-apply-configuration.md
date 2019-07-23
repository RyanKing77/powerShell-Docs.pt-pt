---
ms.date: 12/12/2018
keywords: DSC, PowerShell, configuração, serviço, instalação
title: Escrever, Compilar e Aplicar uma Configuração
ms.openlocfilehash: 8bcd55518b0409b9a4b02ca95f027a0a77eb5300
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372172"
---
> Aplica-se a: Windows PowerShell 4,0, Windows PowerShell 5,0

# <a name="write-compile-and-apply-a-configuration"></a>Escrever, Compilar e Aplicar uma Configuração

Este exercício explica como criar e aplicar uma configuração de DSC (configuração de estado desejado) do início ao fim.
No exemplo a seguir, você aprenderá a escrever e aplicar uma configuração muito simples. A configuração garantirá que um arquivo "HelloWorld. txt" exista no computador local. Se você excluir o arquivo, o DSC o recriará na próxima vez em que for atualizado.

Para obter uma visão geral do que é o DSC e como ele funciona, consulte [visão geral da configuração de estado desejado para desenvolvedores](../overview/overview.md).

## <a name="requirements"></a>Requisitos

Para executar este exemplo, você precisará de um computador executando o PowerShell 4,0 ou posterior.

## <a name="write-the-configuration"></a>Gravar a configuração

Uma [configuração](configurations.md) DSC é uma função especial do PowerShell que define como você deseja configurar um ou mais computadores de destino (nós).

No ISE do PowerShell ou em outro editor do PowerShell, digite o seguinte:

```powershell
Configuration HelloWorld {

    # Import the module that contains the File resource.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets to compile MOF files for, when this configuration is executed.
    Node 'localhost' {

        # The File resource can ensure the state of files, or copy them from a source to a destination with persistent updates.
        File HelloWorld {
            DestinationPath = "C:\Temp\HelloWorld.txt"
            Ensure = "Present"
            Contents   = "Hello World from DSC!"
        }
    }
}
```

> ! Importante em cenários mais avançados em que vários módulos precisam ser importados para que você possa trabalhar com muitos recursos de DSC na mesma configuração, certifique-se de colocar cada módulo em `Import-DscResource`uma linha separada usando.
> Isso é mais fácil de manter no controle do código-fonte e é necessário ao trabalhar com a DSC na configuração de estado do Azure.
>
> ```powershell
>  Configuration HelloWorld {
>
>   # Import the module that contains the File resource.
>   Import-DscResource -ModuleName PsDesiredStateConfiguration
>   Import-DscResource -ModuleName xWebAdministration
>
> ```

Salve o arquivo como "HelloWorld. ps1".

Definir uma configuração é como definir uma função. O bloco de **nó** especifica o nó de destino a ser configurado, nesse `localhost`caso.

A configuração chama um [recursos](../resources/resources.md), o `File` recurso. Os recursos fazem o trabalho de garantir que o nó de destino esteja no estado definido pela configuração.

## <a name="compile-the-configuration"></a>Compilar a configuração

Para que uma configuração DSC seja aplicada a um nó, ela deve primeiro ser compilada em um arquivo MOF.
A execução da configuração, como uma função, irá compilar um arquivo ". mof" para cada nó definido pelo `Node` bloco.
Para executar a configuração, você precisa criar o *ponto de origem* do script "HelloWorld. ps1" no escopo atual.
Para obter mais informações, consulte [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).

<!-- markdownlint-disable MD038 -->
*Dot Source* seu script "HelloWorld. ps1" digitando o caminho onde você o armazenou, após o `. ` (ponto, espaço). Em seguida, você pode executar sua configuração chamando-a como uma função.
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\HelloWorld.ps1
HelloWorld
```

Isso gera a seguinte saída:

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a>Aplicar a configuração

Agora que você tem o MOF compilado, é possível aplicar a configuração ao nó de destino (nesse caso, o computador local) chamando o cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .

O `Start-DscConfiguration` cmdlet informa o [Configuration Manager local (LCM)](../managing-nodes/metaConfig.md), o mecanismo do DSC, para aplicar a configuração.
O LCM faz o trabalho de chamar os recursos de DSC para aplicar a configuração.

Use o código abaixo para executar o `Start-DSCConfiguration` cmdlet. Especifique o caminho do diretório em que o "localhost. mof" está armazenado `-Path` no parâmetro. O `Start-DSCConfiguration` cmdlet examina o diretório especificado para todos os arquivos\<"computername\>. mof". O `Start-DSCConfiguration` cmdlet tenta aplicar cada arquivo ". mof" encontrado ao ComputerName especificado pelo nome de arquivo ("localhost", "Server01", "DC-02", etc.).

> [!NOTE]
> Se o `-Wait` parâmetro não for especificado, `Start-DSCConfiguration` o criará um trabalho em segundo plano para executar a operação. A especificação `-Verbose` do parâmetro permite que você assista à saída **detalhada** da operação. `-Wait`e `-Verbose` são ambos parâmetros opcionais.

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a>Testar a configuração

Depois que `Start-DSCConfiguration` o cmdlet for concluído, você deverá ver um arquivo "HelloWorld. txt" no local especificado. Você pode verificar o conteúdo com o cmdlet [Get-Content](/powershell/module/microsoft.powershell.management/get-content) .

Você também pode *testar* o status atual usando [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).

A saída deverá ser "true" se o nó estiver em conformidade no momento com a configuração aplicada.

```powershell
Test-DSCConfiguration
```

```output
True
```

```powershell
Get-Content -Path C:\Temp\HelloWorld.txt
```

```output
Hello World from DSC!
```

## <a name="re-applying-the-configuration"></a>Reaplicando a configuração

Para ver sua configuração ser aplicada novamente, você pode remover o arquivo de texto criado pela sua configuração. Use o `Start-DSCConfiguration` cmdlet com o `-UseExisting` parâmetro. O `-UseExisting` parâmetro`Start-DSCConfiguration` instrui a aplicar novamente o arquivo "Current. mof", que representa a configuração aplicada com êxito mais recentemente.

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a>Passos Seguintes

- Saiba mais sobre as configurações de DSC em [configurações de DSC](configurations.md).
- Veja quais recursos de DSC estão disponíveis e como criar recursos personalizados de DSC em [recursos de DSC](../resources/resources.md).
- Localize as configurações e os recursos de DSC no [Galeria do PowerShell](https://www.powershellgallery.com/).
