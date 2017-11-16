---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "DSC, do powershell, a configuração, a configuração"
title: DSC de Linux nxFile recursos
ms.openlocfilehash: 14f1ae31a8409b8874d76a91b8b29595e30fbb46
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-for-linux-nxfile-resource"></a>DSC de Linux nxFile recursos

O **nxFile** recursos no PowerShell pretendido Estado Configuration (DSC) fornece um mecanismo para gerir ficheiros e diretórios num nó de Linux.

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
| DestinationPath| Especifica a localização onde pretende garantir o estado de um ficheiro ou diretório.| 
| SourcePath| Especifica o caminho a partir dos quais pretende copiar o recurso do ficheiro ou pasta. Este caminho pode ser um caminho local, ou um `http/https/ftp` URL. Remoto `http/https/ftp` URLs só são suportadas quando o valor da **tipo** propriedade é o ficheiro.| 
| Certifique-se| Determina se deve verificar se o ficheiro existe. Defina esta propriedade para "Presente" para garantir que o ficheiro existe. Defina-o para "Ausente", certifique-se de que o ficheiro não existe. O valor predefinido é "Presente".| 
| Tipo| Especifica se o recurso que está a ser configurado é um diretório ou um ficheiro. Defina esta propriedade para "diretório" para indicar que o recurso é um diretório. Defina-o para "do ficheiro" para indicar que o recurso é um ficheiro. O valor predefinido é "ficheiros"| 
| Conteúdos| Especifica o conteúdo de um ficheiro, como uma cadeia específica.| 
| Soma de verificação| Define o tipo a utilizar ao determinar se os dois ficheiros são as mesmas. Se **soma de verificação** não for especificado, apenas o nome de ficheiro ou diretório é utilizado para comparação. Os valores são: "ctime", "mtime" ou "md5".| 
| Recurse| Indica se subdiretórios estão incluídos. Defina esta propriedade como **$true** para indicar que pretende que o subdiretórios a incluir. A predefinição é **$false**. **Nota:** esta propriedade só é válido quando o **tipo** propriedade está definida para o diretório.| 
| Force| Determinadas operações de ficheiros (como substituir um ficheiro ou eliminar um diretório que não está vazio) resultará num erro. Utilizar o **Force** propriedade substitui esses erros. O valor predefinido é **$false**.| 
| Ligações| Especifica o comportamento pretendido para as ligações simbólicas. Definir esta propriedade para "seguir", siga as ligações simbólicas e atuar sobre o destino de ligações (por exemplo. Copie o ficheiro em vez da ligação). Definir esta propriedade para "Gerir" para atuar na ligação (por exemplo. Copie a ligação próprio). Defina esta propriedade para "Ignorar" para ignorar as ligações simbólicas.| 
| Grupo| O nome do **grupo** possuir o ficheiro ou diretório.| 
| Modo| Especifica as permissões pretendidas para o recurso, octal ou simbólica notação. (por exemplo, 777 ou rwxrwxrwx). Se utilizar a notação simbólica, não fornecem o primeiro caráter que indica o diretório ou ficheiro.| 
| dependsOn | Indica que a configuração de outro recurso tem de executar antes deste recurso é configurado. Por exemplo, se o **ID** do recurso de bloco de script de configuração que pretende executar primeiro é **ResourceName** e o respetivo tipo é **ResourceType**, a sintaxe para utilizar esta a propriedade é `DependsOn = "[ResourceType]ResourceName"`.| 

## <a name="additional-information"></a>Informações Adicionais


Linux e Windows utilizar carateres de quebra de linha diferente nos ficheiros de texto por predefinição e isto pode causar resultados inesperados quando configurar alguns ficheiros num computador com Linux __nxFile__. Existem várias formas de gerir o conteúdo de um ficheiro de Linux ao evitando problemas causados por carateres de quebra de linha inesperado:

Passo 1: Copiar o ficheiro de uma origem remota (http, https ou ftp): Crie um ficheiro no Linux com os conteúdos pretendidos e testar num servidor web ou de ftp acessível a principais irá configurar. Definir o __SourcePath__ propriedade no __nxFile__ recursos com o URL de web ou de ftp para o ficheiro.

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


Passo 2: Ler o conteúdo do ficheiro no script PowerShell com [Get-Content](https://technet.microsoft.com/en-us/library/hh849787.aspx) após a definição de __$OFS__ propriedade para utilizar o caráter de quebra de linha do Linux.


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


Passo 3: Utilize uma função do PowerShell para substituir as quebras de linha do Windows com carateres de quebra de linha do Linux.

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

O exemplo seguinte assegura que o diretório `/opt/mydir` existir, e se um ficheiro com conteúdo especificado existe este diretório.

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

