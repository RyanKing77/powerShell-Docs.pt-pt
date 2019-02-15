---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Guia de introdução - criar um Web site com o DSC
ms.openlocfilehash: d98607939ccd3cc5e660936d8c0a6d54fce7d65f
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56265489"
---
> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="quickstart---create-a-website-with-dsc"></a>Guia de introdução - criar um Web site com o DSC

Neste exercício explica criar e aplicar uma configuração de configuração de estado pretendido (DSC) do início ao fim.
O exemplo utilizaremos garante que tem um servidor a `Web-Server` ativada a funcionalidade (IIS) e de que o conteúdo para um site de "Olá mundo" simples está presente no `inetpub\wwwroot` diretório de que o servidor.

Para obter uma descrição geral de Novidades DSC e como funciona, consulte [Desired Configuration descrição geral do Estado para os decisores](../overview/decisionMaker.md).

## <a name="requirements"></a>Requisitos

Para executar este exemplo, terá de um computador a executar o Windows Server 2012 ou posterior e o PowerShell 4.0 ou posterior.

## <a name="write-and-place-the-indexhtm-file"></a>Escrever e coloque o ficheiro index.htm

Em primeiro lugar, vamos criar o ficheiro HTML que iremos utilizar como o conteúdo do Web site.

Na sua pasta de raiz, crie uma pasta denominada `test`.

Num editor de texto, escreva o seguinte texto:

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

Guarde-o como `index.htm` no `test` pasta que criou anteriormente.

## <a name="write-the-configuration"></a>A configuração de escrita

A [configuração DSC](../configurations/configurations.md) é uma função de PowerShell especial que define a forma como pretende configurar um ou mais computadores de destino (nós).

No ISE do PowerShell, escreva o seguinte:

```powershell
Configuration WebsiteTest {

    # Import the module that contains the resources we're using.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets this configuration will be applied to.
    Node 'localhost' {

        # The first resource block ensures that the Web-Server (IIS) feature is enabled.
        WindowsFeature WebServer {
            Ensure = "Present"
            Name   = "Web-Server"
        }

        # The second resource block ensures that the website content copied to the website root folder.
        File WebsiteContent {
            Ensure = 'Present'
            SourcePath = 'c:\test\index.htm'
            DestinationPath = 'c:\inetpub\wwwroot'
        }
    }
}
```

Guarde o ficheiro como `WebsiteTest.ps1`.

Pode ver que se parece com uma função do PowerShell, com a adição da palavra-chave **configuração** utilizado antes do nome da função.

O **nó** bloco Especifica o nó de destino ser configurada, neste caso `localhost`.

A configuração chama dois [recursos](../resources/resources.md), **WindowsFeature** e **ficheiro**.
Recursos efetuar o trabalho de se certificar de que o nó de destino está no estado definido na configuração.

## <a name="compile-the-configuration"></a>A configuração de compilação

Para uma configuração de DSC a ser aplicado a um nó, deve primeiro ser compilado para um ficheiro MOF.
Para tal, execute a configuração, como uma função.
Na consola do PowerShell, navegue para a mesma pasta onde guardou a configuração e execute os seguintes comandos para compilar a configuração num ficheiro MOF:

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

Isto gera o seguinte resultado:

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

A primeira linha faz com que a função de configuração disponíveis na consola.
A segunda linha executa a configuração.
O resultado é que uma nova pasta designada `WebsiteTest` é criado como uma subpasta da pasta atual.
O `WebsiteTest` pasta contém um ficheiro denominado `localhost.mof`.
É este ficheiro que, em seguida, pode ser aplicado ao nó de destino.

## <a name="apply-the-configuration"></a>Aplicar a configuração

Agora que tem o MOF compilado, pode aplicar a configuração para o nó de destino (neste caso, o computador local) ao chamar o [início DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.

O `Start-DscConfiguration` cmdlet informa o [Gestor de configuração Local (MMC)](../managing-nodes/metaConfig.md), que é o motor do DSC, para aplicar a configuração.
O MMC efetua o trabalho de chamar os recursos de DSC para aplicar a configuração.

Na consola do PowerShell, navegue para a mesma pasta onde guardou a configuração e execute o seguinte comando:

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a>Testar a configuração

Pode chamar o [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) cmdlet para ver se a configuração foi concluída com êxito.

Pode também testar os resultados diretamente, neste caso, navegando até `http://localhost/` num web browser.
Deverá ver a página de "Olá mundo" HTML que criou como o primeiro passo neste exemplo.

## <a name="next-steps"></a>Próximos passos

- Saber mais sobre as configurações de DSC na [configurações de DSC](../configurations/configurations.md).
- Consulte os recursos de DSC estão disponíveis e como criar recursos de DSC personalizados em [recursos de DSC](../resources/resources.md).
- Localizar recursos e configurações de DSC o [galeria do PowerShell](https://www.powershellgallery.com/).
