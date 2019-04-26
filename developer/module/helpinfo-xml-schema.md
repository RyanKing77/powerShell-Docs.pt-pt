---
title: Esquema HelpInfo XML | Documentos da Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74dcb396-c295-4457-b84c-4432bdaa8df3
caps.latest.revision: 7
ms.openlocfilehash: 0f965f4ee1ef92a6a538b52b4348c04366cabf66
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082469"
---
# <a name="helpinfo-xml-schema"></a>HelpInfo XML Schema (Esquema XML HelpInfo)

Este tópico contém o esquema XML para arquivos de informações de ajuda Atualizável, comumente conhecido como "Arquivos de HelpInfo XML".

## <a name="helpinfo-xml-schema"></a>HelpInfo XML Schema (Esquema XML HelpInfo)

Arquivos HelpInfo XML baseiam-se o esquema XML abaixo.

```xml
<?xml version="1.0" encoding="utf-8"?>
<schema targetNamespace="http://schemas.microsoft.com/powershell/help/2010/05" xmlns="http://www.w3.org/2001/XMLSchema">
  <element name="HelpInfo">
    <complexType>
      <sequence>
        <element name="HelpContentURI" type="anyURI" minOccurs="1" maxOccurs="1" />
        <element name="SupportedUICultures" minOccurs="1" maxOccurs="1">
          <complexType>
            <sequence>
              <element name="UICulture" minOccurs="1" maxOccurs="unbounded">
                <complexType>
                  <sequence>
                    <element name="UICultureName" type="language" minOccurs="1" maxOccurs="1" />
                    <element name="UICultureVersion" type="string" minOccurs="1" maxOccurs="1" />
                  </sequence>
                </complexType>
              </element>
            </sequence>
          </complexType>
        </element>
      </sequence>
    </complexType>
  </element>
</schema>
```

## <a name="helpinfo-xml-elements"></a>Elementos HelpInfo XML

O ficheiro XML de HelpInfo inclui os seguintes elementos.

HelpContentURI contém o URI da localização da ajuda do ficheiros CAB para o módulo. O URI tem de começar com "http" ou "https". O URI deve especificar uma localização de Internet, mas não tem de incluir o nome do ficheiro CAB. O **HelpContentURI** valor pode ser igual ou diferente do **HelpInfoURI** valor.

SupportedUICultures representa os arquivos de ajuda do módulo em todas as culturas de interface do Usuário. Contém **UICulture** elementos, sendo que cada um representa um conjunto de arquivos de ajuda para o módulo numa cultura da interface do Usuário especificado.

UICulture representa um conjunto de arquivos de ajuda para o módulo numa cultura da interface do Usuário especificado. Adicionar uma **UICulture** elemento para cada cultura da interface do Usuário em que são escritos os arquivos da ajuda.

UICultureName contém o código de idioma para a cultura da interface do Usuário em que são escritos os arquivos da ajuda.

UICultureVersion contém um número de versão 4-part num "N1. N2. N3. N4 "formato que representa a versão do ficheiro de ajuda CAB na cultura da interface do Usuário. Incrementar este número de versão sempre que carregar a ajuda de novos ficheiros CAB na cultura da interface do Usuário que é especificado por **UICultureName**. Para obter mais informações sobre este valor, consulte "Versão Class (sistema)" no MSDN.