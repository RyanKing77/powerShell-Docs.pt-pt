---
title: Como criar um Shell do Console | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Make-Shell [PowerShell Programmer's Guide]
ms.assetid: 6c24dd44-a8ec-421d-ac86-90912e1a8cc6
caps.latest.revision: 5
ms.openlocfilehash: 7166881bd1403ea8c81ec2928321f6b93e3ac58d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081591"
---
# <a name="how-to-create-a-console-shell"></a>How to Create a Console Shell (Como Criar uma Shell da Consola)

Windows PowerShell fornece uma ferramenta de Make-Shell, também referida como o "marca-kit", que é utilizado para criar um shell de consola que não é extensível. Shells criados com essa nova ferramenta não podem ser expandidas posteriormente por meio de um snap-in do Windows PowerShell.

## <a name="syntax"></a>Sintaxe

Segue-se a sintaxe usada para executar Make-Shell a partir de dentro de um arquivo de marca.

```
make-shell
  -out n.exe
  -namespace ns
  [ -lib libdirectory1[,libdirectory2,..] ]
  [ -reference ca1.dll[,ca2.dll,...] ]
  [ -formatdata fd1.format.ps1xml[,fd2.format.ps1xml,...] ]
  [ -typedata td1.type.ps1xml[,td2.type.ps1xml,...] ]
  [ -source c1.cs [,c2.cs,...] ]
  [ -authorizationmanager authorizationManagerType ]
  [ -win32icon i.ico ]
  [ -initscript p.ps1 ]
  [ -builtinscript s1.ps1[,s2.ps1,...] ]
  [ -resource resourcefile.txt ]
  [ -cscflags cscFlags ]
  [ -? | -help ]
```

## <a name="parameters"></a>Parâmetros

Eis uma breve descrição dos parâmetros de Make-Shell.

> [!CAUTION]
> Caminhos UNC para assemblies não são suportados pelo Make-Shell.

|Parâmetro|Descrição|
|---------------|-----------------|
|-out n.exe|Obrigatório. O nome do shell para produzir. O caminho é especificado como parte deste parâmetro.<br /><br /> Make-shell serão acrescentadas ".exe" a este valor se não for especificado. **Atenção:**  Não crie um ficheiro de saída com o mesmo nome que o ficheiro. dll referenciada. Se tentar isso, a ferramenta de Make-Shell cria um arquivo. cs com o mesmo nome, o que irá substituir o ficheiro. CS que tem o seu código-fonte cmdlet.|
|-namespace ns|Obrigatório. O espaço de nomes a utilizar para a derivada [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) classe que o kit de marca gera e compila.|
|-lib libdirectory1 [, libdirectory2,...]|Os diretórios que serão pesquisados assemblies do .NET, incluindo os assemblies do Windows PowerShell, assemblies especificados pelo `reference` parâmetro, assemblagens referenciadas indiretamente pelo outro assembly e os assemblies de system .NET.|
|-reference ca1.dll[,ca2.dll,...]|Uma lista separada por vírgulas dos assemblies para incluir no shell. Esses assemblies inclui todos os cmdlet e os assemblies de fornecedor, bem como assemblies de recursos que devem ser carregados. Se este parâmetro não for especificado, em seguida, um shell é produzido que contém apenas os principais cmdlets e fornecedores fornecidos pelo Windows PowerShell.<br /><br /> Os assemblies podem ser especificados usando o caminho completo, caso contrário, serão procurados para utilizar o caminho especificado pelo `lib` parâmetro.|
|-formatdata fd1.format.ps1xml[,fd2.format.ps1xml,...]|Uma lista separada por vírgulas de dados de formato para incluir no shell. Se este parâmetro não for especificado, em seguida, um shell é produzido que contém os dados do formato fornecidos pelo Windows PowerShell.|
|-typedata td1.type.ps1xml[,td2.type.ps1xml,...]|Uma lista separada por vírgulas de dados de tipo para incluir no shell. Se este parâmetro não for especificado, em seguida, um shell é produzido que contém apenas os dados de tipo fornecidos pelo Windows PowerShell.|
|-source c1.cs [,c2.cs,...]|O nome de um ficheiro, fornecido pelo desenvolvedor do shell, que contém qualquer código de origem necessário para criar o shell.<br /><br /> O arquivo de código de origem pode conter nenhum do seguinte código de origem:<br /><br /> -A implementação do Gestor de autorização que substitui o Gerenciador de autorização de predefinição. (Isso poderia também ser fornecido compilado num assembly.)<br />-Declarações de atributo informativa assemblagem: como AssemblyCompanyAttribute, AssemblyCopyrightAttribute, AssemblyFileVersionAttribute, AssemblyInformationalVersionAttribute, AssemblyProductAttribute, e AssemblyTrademarkAttribute.|
|-authorizationmanager authorizationManagerType|O tipo que contém a implementação do Gestor de autorização. Isso pode ser definido no código-fonte ou compilado num assembly (especificado pelo `reference` parâmetro). Se este parâmetro não for especificado, é utilizado o Gestor de segurança padrão. O valor deve ser o nome de tipo completo, incluindo espaços de nomes.|
|-win32icon i.ico|O ícone para o ficheiro de .exe para o shell. Se não for especificado, o shell tem o ícone que o compilador c# inclui (se houver).|
|-initscript p.ps1|O perfil de inicialização para o shell. O ficheiro está incluído "como-é"; sem verificação de validade é feito pelo Make-Shell.|
|-builtinscript s1.ps1[,s2.ps1,...]|Uma lista de scripts incorporadas para o shell. Estes scripts são detetados antes de scripts no caminho, e seu conteúdo não pode ser alterado depois do shell é criado.<br /><br /> Os ficheiros estão incluídos "como-é"; sem verificação de validade é feito pelo Make-Shell.|
|-resourcefile.txt de recursos|O ficheiro. txt que contém recursos de ajuda e faixa para o shell. O primeiro recurso é o nome ShellHelp e contém o texto apresentado se o shell é invocado com o `help` parâmetro. O segundo recurso com o nome ShellBanner e contém o texto e as informações de copyright apresentado quando o shell é iniciado no modo interativo.<br /><br /> Se este parâmetro não for fornecido, ou estes recursos não estão presentes, em seguida, uma faixa de Ajuda genérica e são utilizados.|
|-cscflags cscFlags|Sinalizadores que devem ser passados para o C# compilador (csc.exe). Estes são transmitidos através de inalterado. Se este parâmetro incluir espaços, devem ser rodeado de aspas duplas.|
|-?<br /><br /> -Ajuda|Apresenta a mensagem de direitos autorais e opções de linha de comandos da Shell de marca.|
|-verbose|Mostra informações detalhadas, enquanto o shell está a ser criado.|

## <a name="see-also"></a>Veja Também

[Guia do programador do Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)