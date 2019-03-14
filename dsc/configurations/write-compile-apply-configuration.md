---
ms.date: 12/12/2018
keywords: DSC, powershell, configuração, serviço, configuração
title: Escrever, Compilar e Aplicar uma Configuração
ms.openlocfilehash: c884af9d92ac375457d6eb75d815ae9a9159e273
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795424"
---
> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="write-compile-and-apply-a-configuration"></a>Escrever, Compilar e Aplicar uma Configuração

Neste exercício explica-criar e aplicar uma configuração do Desired State Configuration (DSC) do início ao fim.
No exemplo a seguir, aprenderá como escrever e aplicar uma configuração muito simples. A configuração irá garantir que existe um ficheiro de "HelloWorld.txt" no seu computador local. Se eliminar o ficheiro, DSC recriará o da próxima vez que ele atualiza.

Para uma descrição geral do que DSC é e como ele funciona, consulte [Desired State Configuration descrição geral para programadores](../overview/overview.md).

## <a name="requirements"></a>Requisitos

Para executar este exemplo, irá precisar de um computador a executar o PowerShell 4.0 ou posterior.

## <a name="write-the-configuration"></a>Escreva a configuração

Um DSC [configuração](configurations.md) é uma função especial do PowerShell que define a forma como pretende configurar uma ou mais computadores de destino (nós).

No ISE do PowerShell ou outro editor de PowerShell, escreva o seguinte:

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

Guarde o ficheiro como "HelloWorld.ps1".

Definir uma configuração é como definir uma função. O **nó** bloco Especifica o nó de destino a ser configurado, neste caso `localhost`.

A configuração chama uma [recursos](../resources/resources.md), o `File` recursos. Recursos de fazem o trabalho de garantir que o nó de destino está no estado definido pela configuração.

## <a name="compile-the-configuration"></a>Compilar a configuração

Para uma configuração de DSC a ser aplicado a um nó, deve primeiro ser compilado num arquivo MOF.
Executar a configuração, como uma função, irá compilar um arquivo de ". MOF" para cada nó definido pelo `Node` bloco.
Para executar a configuração, precisa *origem ponto* seu script de "HelloWorld.ps1" no âmbito atual.
Para obter mais informações, consulte [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).

<!-- markdownlint-disable MD038 -->
*Origem de dot* seu script de "HelloWorld.ps1" ao escrever no caminho onde armazenou, depois do `. ` (ponto, espaço). Pode, em seguida, execute a configuração ao chamá-la como uma função.
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\WebsiteTest.ps1
HelloWolrd
```

Isso gera o seguinte resultado:

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a>Aplicar a configuração

Agora que tem o MOF compilado, pode aplicar a configuração para o nó de destino (no caso, o computador local) ao chamar o [Start-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.

O `Start-DscConfiguration` cmdlet informa o [Gestor de configuração Local (LCM)](../managing-nodes/metaConfig.md), o motor de DSC, para aplicar a configuração.
O LCM faz o trabalho de chamar os recursos de DSC para aplicar a configuração.

Utilize o código abaixo para executar o `Start-DSCConfiguration` cmdlet. Especifique o caminho do diretório onde sua "localhost.mof" são armazenados para o `-Path` parâmetro. O `Start-DSCConfiguration` cmdlet examina o diretório especificado para qualquer "\<computername\>. MOF" ficheiros. O `Start-DSCConfiguration` cmdlet tenta aplicam-se cada arquivo de ". MOF" encontrar a computername especificado pelo nome de ficheiro ("localhost", "servidor01", "controlador de domínio-02", etc.).

> [!NOTE]
> Se o `-Wait` parâmetro não for especificado, `Start-DSCConfiguration` cria uma tarefa em segundo plano para executar a operação. Especificar a `-Verbose` parâmetro permite-lhe ver o **verboso** saída da operação. `-Wait`, e `-Verbose` são ambos os parâmetros opcionais.

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a>Testar a configuração

Uma vez o `Start-DSCConfiguration` cmdlet estiver concluído, deverá ver um ficheiro de "HelloWorld.txt" na localização que especificou. Pode verificar o conteúdo com o [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.

Também pode *testar* o estado atual com [Test-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).

O resultado deve ser "Verdadeiro" se o nó está atualmente em conformidade com a configuração aplicada.

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

## <a name="re-applying-the-configuration"></a>Voltar a aplicar a configuração

Para ver a configuração são aplicadas novamente, pode remover o arquivo de texto criado pela sua configuração. A utilização a `Start-DSCConfiguration` cmdlet com o `-UseExisting` parâmetro. O `-UseExisting` instrui o parâmetro `Start-DSCConfiguration` se inscrever novamente o ficheiro de "current.mof", que representa o último com êxito aplicada a configuração.

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a>Próximos passos

- Saiba mais sobre as configurações de DSC em [configurações de DSC](configurations.md).
- Veja quais recursos de DSC estão disponíveis e como criar recursos de DSC personalizados em [recursos de DSC](../resources/resources.md).
- Localizar as configurações de DSC e os recursos a [galeria do PowerShell](https://www.powershellgallery.com/).
