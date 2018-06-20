---
ms.date: 06/12/2017
keywords: DSC, do powershell, a configuração, a configuração
title: Configuração do Estado de início rápido de pretendida
ms.openlocfilehash: eb7572f39f7a2710c82f132f42c3502b15c48d0f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219050"
---
> Aplica-se a: O Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="desired-state-configuration-quick-start"></a>Configuração do Estado de início rápido de pretendida

Neste exercício explica criar e aplicar uma configuração de configuração de estado pretendido (DSC) do início ao fim.
O exemplo utilizaremos garante que tem um servidor a `Web-Server` ativada a funcionalidade (IIS) e de que o conteúdo para um site de "Olá mundo" simples está presente no `intepub\wwwroot` diretório de que o servidor.

Para obter uma descrição geral de Novidades DSC e como funciona, consulte [Desired Configuration descrição geral do Estado para os decisores](decisionMaker.md).

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

A [configuração DSC](configurations.md) é uma função de PowerShell especial que define a forma como pretende configurar um ou mais computadores de destino (nós).

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

A configuração chama dois [recursos](resources.md), [WindowsFeature](windowsFeatureResource.md) e [ficheiro](fileResource.md).
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

Agora que tem o MOF compilado, pode aplicar a configuração para o nó de destino (neste caso, o computador local) ao chamar o [início DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration) cmdlet.

O `Start-DscConfiguration` cmdlet informa o [Gestor de configuração Local (MMC)](metaConfig.md), que é o motor do DSC, para aplicar a configuração.
O MMC efetua o trabalho de chamar os recursos de DSC para aplicar a configuração.

Na consola do PowerShell, navegue para a mesma pasta onde guardou a configuração e execute o seguinte comando:

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a>Testar a configuração

Pode chamar o [Get-DscConfigurationStatus](/reference/5.1/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet para ver se a configuração foi concluída com êxito.

Pode também testar os resultados diretamente, neste caso, navegando até `http://localhost/` num web browser.
Deverá ver a página de "Olá mundo" HTML que criou como o primeiro passo neste exemplo.

## <a name="next-steps"></a>Próximos passos

- Saber mais sobre as configurações de DSC na [configurações de DSC](configurations.md).
- Consulte os recursos de DSC estão disponíveis e como criar recursos de DSC personalizados em [recursos de DSC](resources.md).
- Localizar recursos e configurações de DSC o [galeria do PowerShell](https://www.powershellgallery.com/).