---
title: Apoio Ajuda Online | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: b76f45299d11dc10c8b16ed80f87c7f1fcc5ed65
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082146"
---
# <a name="supporting-online-help"></a>Apoio Ajuda Online

A partir do Windows PowerShell 3.0, existem duas formas para apoiar o `Get-Help` recurso Online para comandos do Windows PowerShell. Este tópico explica como implementar esta funcionalidade para tipos de comando diferentes.

## <a name="about-online-help"></a>Ajuda Online

Ajuda online sempre foi uma parte essencial do Windows PowerShell. Embora o `Get-Help` cmdlet apresenta os tópicos de ajuda no prompt de comando, o número de utilizadores que prefere a experiência de leitura de online, incluindo codificação por cores, hiperlinks e compartilhamento de idéias no conteúdo da Comunidade e os documentos com base no wiki. Mais importante é que, antes do advento do ajuda Atualizável, ajuda online fornecidos a versão mais recente dos ficheiros de ajuda.

Com o advento do ajuda Atualizável no Windows PowerShell 3.0, a ajuda online ainda desempenha um papel fundamental. Além da experiência de usuário flexível, a ajuda online fornece ajuda aos utilizadores que não suportam ou não é possível utilizar ajuda Atualizável para transferir os tópicos de ajuda.

## <a name="how-get-help--online-works"></a>Como Get-Help-Online funciona

Para ajudar os utilizadores a encontrar os tópicos de ajuda online para obter comandos, o `Get-Help` comando tem um parâmetro Online que abre a versão online de tópico de ajuda para um comando no browser de Internet predefinido do utilizador.

Por exemplo, o seguinte comando abre o tópico de ajuda online para o `Invoke-Command` cmdlet.

```powershell
Get-Help Invoke-Command -Online
```

Para implementar `Get-Help` -Online, o `Get-Help` cmdlet procura para um identificador URI (Uniform Resource) para o tópico de ajuda da versão online nas seguintes localizações.

- Na primeira ligação na seção Links relacionados do tópico de ajuda para o comando. O tópico de ajuda deve ser instalado no computador do usuário. Esta funcionalidade foi introduzida no Windows PowerShell 2.0.

- A propriedade HelpUri de todos os comandos. A propriedade HelpUri está acessível, mesmo quando o tópico de ajuda para o comando não está instalado no computador do usuário. Esta funcionalidade foi introduzida no Windows PowerShell 3.0.

  `Get-Help` procura um URI na primeira entrada na seção Links relacionados antes de obter o valor da propriedade HelpUri. Se o valor da propriedade está incorreto ou foi alterado, pode substitui-lo ao introduzir um valor diferente na primeira ligação relacionados. No entanto, na primeira ligação relacionados funciona apenas quando os tópicos de ajuda estão instalados no computador do usuário.

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a>Adicionar um URI na primeira ligação relacionada de um tópico de ajuda do comando

Pode suportar `Get-Help` -Online para qualquer comando através da adição de um URI válido para a primeira entrada na seção Links relacionados do tópico de ajuda baseados em XML para o comando. Esta opção é válida apenas em tópicos de ajuda baseados em XML e funciona apenas quando o tópico de ajuda está instalado no computador do usuário. Quando o tópico de ajuda está instalado e o URI é preenchido, este valor tem precedência sobre o **HelpUri** propriedade do comando. Para obter informações sobre tópicos de ajuda baseados em XML para comandos, consulte [Writing XML-Based tópicos de ajuda para comandos](../help/writing-xml-based-help-topics-for-commands.md).

Para suportar esta funcionalidade, o URI tem de aparecer no `maml:uri` elemento no primeiro `maml:relatedLinks/maml:navigationLink` elemento no `maml:relatedLinks` elemento.

O XML a seguir mostra o posicionamento correto do URI. A "versão Online:" texto no `maml:linkText` elemento é uma prática recomendada, mas não é necessário.

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>http://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a>Adicionar a propriedade HelpUri a um comando

Esta secção mostra como adicionar a propriedade HelpUri a comandos de diferentes tipos.

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a>Adicionar uma propriedade HelpUri a um Cmdlet

Para cmdlets escritos em C#, adicione uma **HelpUri** atributo à classe Cmdlet. O valor do atributo tem de ser um URI que começa com "http" ou "https".

O código seguinte mostra o atributo HelpUri a `Get-History` classe cmdlet.

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a>Adicionar uma propriedade HelpUri a uma função avançada

Para funções avançadas, adicione uma **HelpUri** propriedade para o **CmdletBinding** atributo. O valor da propriedade tem de ser um URI que começa com "http" ou "https".

O código seguinte mostra o atributo HelpUri da função New-calendário

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a>Adicionar um atributo HelpUri a um comando CIM

Para obter comandos CIM, adicione uma **HelpUri** atributo para o **CmdletMetadata** elemento no ficheiro CDXML. O valor do atributo tem de ser um URI que começa com "http" ou "https".

O código seguinte mostra o atributo HelpUri do comando de início-Debug CIM

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a>Adicionar um atributo HelpUri a um fluxo de trabalho

Para fluxos de trabalho que são escritos no idioma do Windows PowerShell, adicione um **. ExternalHelp** diretiva de comentário para o código de fluxo de trabalho. O valor da diretiva tem de ser um URI que começa com "http" ou "https".

> [!NOTE]
> A propriedade HelpUri não é suportada para fluxos de trabalho baseados em XAML no Windows PowerShell.

O código seguinte mostra o. Diretiva de ExternalHelp num arquivo de fluxo de trabalho.

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```