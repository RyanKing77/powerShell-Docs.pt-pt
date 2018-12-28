---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: Início rápido - criar um Web site com o DSC
ms.openlocfilehash: c62e2d8af46bf74c4dd13069ddff6cc39763a209
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404677"
---
> Aplica-se a: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="quickstart---create-a-website-with-dsc"></a>Início rápido - criar um Web site com o DSC

Neste exercício explica-criar e aplicar uma configuração do Desired State Configuration (DSC) do início ao fim.
O exemplo, usaremos garante que tem um servidor do `Web-Server` (IIS) funcionalidade ativada e que o conteúdo para um site de "Hello World" simples está presente no `intepub\wwwroot` diretório desse servidor.

Para uma descrição geral do que DSC é e como ele funciona, consulte [Desired State Configuration descrição geral para os tomadores de decisão](../overview/decisionMaker.md).

## <a name="requirements"></a>Requisitos

Para executar este exemplo, irá precisar de um computador a executar o Windows Server 2012 ou posterior e o PowerShell 4.0 ou posterior.

## <a name="write-and-place-the-indexhtm-file"></a>Escrever e colocar o arquivo htm

Em primeiro lugar, vamos criar o arquivo HTML que iremos utilizar como o conteúdo do Web site.

Na sua pasta de raiz, crie uma pasta denominada `test`.

Num editor de texto, escreva o seguinte texto:

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

Guardar como `index.htm` no `test` pasta que criou anteriormente.

## <a name="write-the-configuration"></a>Escreva a configuração

R [configuração do DSC](../configurations/configurations.md) é uma função especial do PowerShell que define a forma como pretende configurar uma ou mais computadores de destino (nós).

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

Pode ver que ele se parece com uma função de PowerShell, com a adição da palavra-chave **configuração** utilizado antes do nome da função.

O **nó** bloco Especifica o nó de destino a ser configurado, neste caso `localhost`.

A configuração chama dois [recursos](../resources/resources.md), **WindowsFeature** e **ficheiro**.
Recursos de fazem o trabalho de garantir que o nó de destino está no estado definido pela configuração.

## <a name="compile-the-configuration"></a>Compilar a configuração

Para uma configuração de DSC a ser aplicado a um nó, deve primeiro ser compilado num arquivo MOF.
Para tal, execute a configuração como uma função.
Na consola do PowerShell, navegue para a mesma pasta onde guardou a configuração e execute os seguintes comandos para compilar a configuração para um ficheiro MOF:

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

Isso gera o seguinte resultado:

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

A primeira linha faz a função de configuração disponíveis na consola.
A segunda linha executa a configuração.
O resultado é que uma nova pasta, com o nome `WebsiteTest` é criado como uma subpasta da pasta atual.
O `WebsiteTest` pasta contém um ficheiro denominado `localhost.mof`.
É esse arquivo que, em seguida, pode ser aplicado ao nó de destino.

## <a name="apply-the-configuration"></a>Aplicar a configuração

Agora que tem o MOF compilado, pode aplicar a configuração para o nó de destino (no caso, o computador local) ao chamar o [Start-dscconfiguration para](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.

O `Start-DscConfiguration` cmdlet informa o [Gestor de configuração Local (LCM)](../managing-nodes/metaConfig.md), que é o motor de DSC, para aplicar a configuração.
O LCM faz o trabalho de chamar os recursos de DSC para aplicar a configuração.

Na consola do PowerShell, navegue para a mesma pasta onde guardou a configuração e execute o seguinte comando:

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a>Testar a configuração

Pode chamar o [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) cmdlet para ver se a configuração foi bem-sucedida.

Também pode testar os resultados diretamente, neste caso, navegando até `http://localhost/` num navegador da web.
Deverá ver a página de "Hello World" HTML que criou como a primeira etapa neste exemplo.

## <a name="next-steps"></a>Próximos passos

- Saiba mais sobre as configurações de DSC em [configurações de DSC](../configurations/configurations.md).
- Veja quais recursos de DSC estão disponíveis e como criar recursos de DSC personalizados em [recursos de DSC](../resources/resources.md).
- Localizar as configurações de DSC e os recursos a [galeria do PowerShell](https://www.powershellgallery.com/).
