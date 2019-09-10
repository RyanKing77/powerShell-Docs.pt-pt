---
title: Suporte à ajuda online | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: 5c5707d1c533e0498c6794b60f4499e530e25813
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848088"
---
# <a name="supporting-online-help"></a>Apoio Ajuda Online

A partir do Windows PowerShell 3,0, há duas maneiras de dar suporte `Get-Help` ao recurso online para comandos do Windows PowerShell. Este tópico explica como implementar esse recurso para diferentes tipos de comando.

## <a name="about-online-help"></a>Sobre a ajuda online

A ajuda online sempre foi uma parte vital do Windows PowerShell. Embora o `Get-Help` cmdlet exiba tópicos de ajuda no prompt de comando, muitos usuários preferem a experiência de leitura online, incluindo codificação por cores, hiperlinks e compartilhamento de ideias em conteúdo da Comunidade e documentos baseados em wiki. O mais importante é que, antes do advento da ajuda atualizável, a ajuda online forneceu a versão mais atualizada dos arquivos de ajuda.

Com o advento da ajuda atualizável no Windows PowerShell 3,0, a ajuda online ainda exerce uma função vital. Além da experiência do usuário flexível, a ajuda online fornece ajuda aos usuários que não ou que não podem usar a ajuda atualizável para baixar tópicos da ajuda.

## <a name="how-get-help--online-works"></a>Como o Get-Help-online funciona

Para ajudar os usuários a encontrar os tópicos da ajuda online para `Get-Help` comandos, o comando tem um parâmetro online que abre a versão online do tópico da ajuda para um comando no navegador de Internet padrão do usuário.

Por exemplo, o comando a seguir abre o tópico da ajuda online `Invoke-Command` para o cmdlet.

```powershell
Get-Help Invoke-Command -Online
```

Para implementar `Get-Help` -online, o `Get-Help` cmdlet procura um Uniform Resource Identifier (URI) para o tópico de ajuda da versão online nos locais a seguir.

- O primeiro link na seção links relacionados do tópico da ajuda para o comando. O tópico da ajuda deve ser instalado no computador do usuário. Esse recurso foi introduzido no Windows PowerShell 2,0.

- A propriedade HelpUri de qualquer comando. A propriedade HelpUri é acessível mesmo quando o tópico da ajuda do comando não está instalado no computador do usuário. Esse recurso foi introduzido no Windows PowerShell 3,0.

  `Get-Help`procura um URI na primeira entrada da seção links relacionados antes de obter o valor da propriedade HelpUri. Se o valor da propriedade estiver incorreto ou alterado, você poderá substituí-lo inserindo um valor diferente no primeiro link relacionado. No entanto, o primeiro link relacionado funciona somente quando os tópicos da ajuda são instalados no computador do usuário.

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a>Adicionando um URI ao primeiro link relacionado de um tópico de ajuda de comando

Você pode oferecer `Get-Help` suporte-online para qualquer comando, adicionando um URI válido à primeira entrada na seção links relacionados do tópico da ajuda baseada em XML para o comando. Essa opção só é válida em tópicos de ajuda baseados em XML e funciona somente quando o tópico da ajuda está instalado no computador do usuário. Quando o tópico da ajuda é instalado e o URI é populado, esse valor tem precedência sobre a propriedade **HelpUri** do comando.

Para dar suporte a esse recurso, o URI deve aparecer `maml:uri` no elemento sob o `maml:relatedLinks/maml:navigationLink` primeiro elemento no `maml:relatedLinks` elemento.

O XML a seguir mostra o posicionamento correto do URI. O texto "versão online:" no `maml:linkText` elemento é uma prática recomendada, mas não é necessário.

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

## <a name="adding-the-helpuri-property-to-a-command"></a>Adicionando a propriedade HelpUri a um comando

Esta seção mostra como adicionar a propriedade HelpUri a comandos de tipos diferentes.

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a>Adicionando uma propriedade HelpUri a um cmdlet

Para os cmdlets escritos C#em, adicione um atributo **HelpUri** à classe cmdlet. O valor do atributo deve ser um URI que comece com "http" ou "https".

O código a seguir mostra o atributo HelpUri da `Get-History` classe cmdlet.

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a>Adicionando uma propriedade HelpUri a uma função avançada

Para funções avançadas, adicione uma propriedade **HelpUri** ao atributo **CmdletBinding** . O valor da propriedade deve ser um URI que comece com "http" ou "https".

O código a seguir mostra o atributo HelpUri da função New-Calendar

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a>Adicionando um atributo HelpUri a um comando CIM

Para comandos CIM, adicione um atributo **HelpUri** ao elemento **CMDLETMETADATA** no arquivo CDXML. O valor do atributo deve ser um URI que comece com "http" ou "https".

O código a seguir mostra o atributo HelpUri do comando Start-Debug CIM

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a>Adicionando um atributo HelpUri a um fluxo de trabalho

Para fluxos de trabalho que são gravados na linguagem do Windows PowerShell, adicione um **. ExternalHelp** a diretiva de comentário para o código do fluxo de trabalho. O valor da diretiva deve ser um URI que comece com "http" ou "https".

> [!NOTE]
> A propriedade HelpUri não tem suporte para fluxos de trabalho baseados em XAML no Windows PowerShell.

O código a seguir mostra o. Diretiva ExternalHelp em um arquivo de fluxo de trabalho.

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```