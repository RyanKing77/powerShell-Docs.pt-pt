---
ms.date: 06/12/2017
keywords: DSC, powershell, configuração, a configuração
title: DSC para Linux nxFile recursos
ms.openlocfilehash: 80969ba2ea6247fcd616a301d951403a840c851d
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048822"
---
# <a name="dsc-for-linux-nxfile-resource"></a>DSC para Linux nxFile recursos

O **nxFile** recursos no PowerShell Desired State Configuration (DSC) fornece um mecanismo para gerir ficheiros e diretórios num nó de Linux.

## <a name="syntax"></a>Sintaxe

```
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Ensure = <string> { Absent | Present }  ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Propriedades

|  Propriedade |  Descrição |
|---|---|
| DestinationPath| Especifica a localização onde pretende garantir que o estado para um ficheiro ou diretório.|
| SourcePath| Especifica o caminho a partir da qual pretende copiar o recurso de ficheiro ou pasta. Este caminho pode ser um caminho local, ou um `http/https/ftp` URL. Remoto `http/https/ftp` URLs só são suportados quando o valor do **tipo** propriedade é o ficheiro.|
| Certifique-se| Determina se deve verificar se o ficheiro existe. Defina esta propriedade para "Presente" para garantir que o ficheiro existe. Defini-lo como "Ausente", certifique-se de que o ficheiro não existe. O valor predefinido é "Presente".|
| Tipo| Especifica se o recurso a ser configurado é um diretório ou um ficheiro. Defina esta propriedade para o "diretório" para indicar que o recurso é um diretório. Defina-o para "file" para indicar que o recurso é um ficheiro. O valor predefinido é "file"|
| Conteúdos| Especifica o conteúdo de um arquivo, como uma determinada cadeia de caracteres.|
| Soma de verificação| Define o tipo a utilizar ao determinar se dois arquivos são os mesmos. Se **soma de verificação** não for especificada, apenas o nome de ficheiro ou diretório é utilizado para comparação. Os valores são: "ctime", "mtime", ou "md5".|
| Recurse| Indica se são incluídos os subdiretórios. Defina esta propriedade como **$true** para indicar que pretende que o subdiretórios a serem incluídos. A predefinição é **$false**. **Nota:** Esta propriedade só é válido quando o **tipo** propriedade está definida como o diretório.|
| Force| Determinadas operações de arquivo (como substituir um ficheiro ou eliminar um diretório que não está vazio) irão resultar num erro. Utilizar o **força** propriedade substitui esses erros. O valor predefinido é **$false**.|
| Ligações| Especifica o comportamento desejado para links simbólicos. Defina esta propriedade de "seguir" seguir links simbólicos e tomar decisões sobre o destino de ligações (por exemplo. Copie o ficheiro em vez da ligação). Defina esta propriedade para "Gerir" para tomar decisões sobre a ligação (por exemplo. Copie a ligação em si). Defina esta propriedade para "Ignorar" Ignorar links simbólicos.|
| Grupo| O nome da **grupo** para o proprietário do ficheiro ou diretório.|
| Modo| Especifica as permissões pretendidas para o recurso na notação octal ou simbólica. (por exemplo, 777 ou rwxrwxrwx). Se utilizar a notação simbólica, não fornecem o primeiro caráter que indica o arquivo ou diretório.|
| DependsOn | Indica que a configuração de outro recurso deve ser executado antes deste recurso está configurado. Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e seu tipo é **ResourceType**, a sintaxe para usar isso a propriedade é `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="additional-information"></a>Informações Adicionais


Linux e Windows utilizam carateres de quebra de linha de diferentes em arquivos de texto por padrão, e isso pode causar resultados inesperados quando configurar alguns ficheiros num computador Linux com __nxFile__. Existem várias formas de gerir o conteúdo de um ficheiro do Linux, evitando problemas causados por carateres de quebra de linha inesperado:

Passo 1: Copie o ficheiro a partir de uma origem remota (http, https ou ftp): Crie um ficheiro no Linux com o conteúdo pretendido e testá-los num servidor de ftp ou web acessível o nó (s) que irá configurar. Definir o __SourcePath__ propriedade na __nxFile__ recursos com o URL de web ou de ftp para o ficheiro.

```
Import-DSCResource -Module nx
Node $Node
{
nxFile resolvConf
{
    SourcePath = "http://10.185.85.11/conf/resolv.conf"
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"

}

}
```


Passo 2: Ler o conteúdo do ficheiro do script do PowerShell com [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) após a definição a __$OFS__ propriedade para utilizar o caractere de quebra de linha de Linux.


```
Import-DSCResource -Module nx
Node $Node
{
$OFS = "`n"
$Contents = Get-Content C:\temp\resolv.conf

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"
    Contents = "$Contents"
}

}
```


Passo 3: Utilize uma função do PowerShell para substituir Windows quebras de linha com carateres de quebra de linha de Linux.

```
Function LinuxString($inputStr){
    $outputStr = $inputStr.Replace("`r`n","`n")
    $ouputStr += "`n"
    Return $outputStr
}

Import-DSCResource -Module nx
Node $Node
{

$Contents = @'
search contoso.com
domain contoso.com
nameserver 10.185.85.11
'@

$Contents = LinuxString $Contents

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"
    Contents = $Contents

}
}
```

## <a name="example"></a>Exemplo

O exemplo seguinte, garante que o diretório `/opt/mydir` existe, e se um ficheiro com conteúdo especificado existe neste diretório.

```
Import-DSCResource -Module nx

Node $node {
nxFile DirectoryExample
{
   Ensure = "Present"
   DestinationPath = "/opt/mydir"
   Type = "Directory"
}

nxFile FileExample
{
    Ensure = "Present"
    Destinationpath = "/opt/mydir/myfile"
    Contents=@"
#!/bin/bash`necho "hello world"`n
"@
    Mode = “755”
    DependsOn = "[nxFile]DirectoryExample"
}
}
```