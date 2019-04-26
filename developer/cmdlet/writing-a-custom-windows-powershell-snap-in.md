---
title: Escrever um Snap-in do PowerShell do Windows personalizados | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], custom PSSnapin example
- cmdlets [PowerShell SDK], specified in snap-ins
ms.assetid: 55c8b5cb-8ee2-4080-afc4-3f09c9f20128
caps.latest.revision: 6
ms.openlocfilehash: 4d50ef4dcd75d5c0ba802fbcfe2d7d1d7c954707
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067030"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a>Writing a Custom Windows PowerShell Snap-in (Escrever um Snap-in Personalizado do Windows PowerShell)

Este exemplo mostra como escrever um snap-in do Windows PowerShell que registra cmdlets específicos.

Com esse tipo de snap-in, especifique quais cmdlets, fornecedores, tipos ou formatos para se registar. Para obter mais informações sobre como escrever um snap-in que registra todos os cmdlets e provedores num assembly, consulte [escrever um Snap-in do PowerShell Windows](./writing-a-windows-powershell-snap-in.md).

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a>Para escrever um Snap-in do PowerShell do Windows, que registra cmdlets específicos.

1. Adicione o atributo RunInstallerAttribute.

2. Criar uma classe pública que deriva de [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classe.

   Neste exemplo, o nome da classe é "CustomPSSnapinTest".

3. Adicione uma propriedade pública para o nome do snap-in (obrigatório). Quando atribuir nomes snap-ins, não use nenhum dos seguintes carateres: #. , ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ? @ ` *

   Neste exemplo, o nome do snap-in é "CustomPSSnapInTest".

4. Adicione uma propriedade pública para o fornecedor do snap-in (obrigatório).

   Neste exemplo, o fornecedor é "Microsoft".

5. Adicione uma propriedade pública para o recurso do fornecedor do snap-in (opcional).

   Neste exemplo, o recurso de fornecedor é "CustomPSSnapInTest, Microsoft".

6. Adicione uma propriedade pública para a descrição do snap-in (obrigatório).

   Neste exemplo, a descrição é: "Este é um personalizado Windows PowerShell snap-in que inclui os cmdlets de teste CustomSnapinTest e teste-HelloWorld".

7. Adicione uma propriedade pública para o recurso de descrição do snap-in (opcional).

   Neste exemplo, o recurso de fornecedor é "CustomPSSnapInTest, este é um personalizado Windows PowerShell snap-in que inclui os cmdlets de teste-HelloWorld e CustomSnapinTest de teste".

8. Especifique os cmdlets que pertencem ao personalizado snap-in (opcional) com o [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) classe. As informações adicionadas aqui incluem o nome do cmdlet, seu tipo de .NET e o nome de ficheiro de ajuda do cmdlet (o formato do nome de ficheiro de ajuda do cmdlet deve ser name.dll help.xml).

   Este exemplo adiciona os cmdlets de teste-HelloWorld e TestCustomSnapinTest.

9. Especifica os provedores que pertencem ao personalizado snap-in (opcional).

   Neste exemplo não especifique quaisquer fornecedores.

10. Especifica os tipos que pertencem ao personalizado snap-in (opcional).

    Neste exemplo não especifica todos os tipos.

11. Especifique os formatos que pertencem ao personalizado snap-in (opcional).

    Neste exemplo não especifique quaisquer formatos.

## <a name="example"></a>Exemplo

Este exemplo mostra como escrever um snap-in personalizado Windows PowerShell que pode ser utilizado para registar os cmdlets de teste CustomSnapinTest e teste-HelloWorld. Lembre-se de que neste exemplo, o assembly completo pode conter outros cmdlets e fornecedores que não poderiam ser registados por este snap-in.

```csharp
[RunInstaller(true)]
public class CustomPSSnapinTest : CustomPSSnapIn
{
  /// <summary>
  /// Creates an instance of CustomPSSnapInTest class.
  /// </summary>
  public CustomPSSnapinTest()
          : base()
  {
  }

  /// <summary>
  /// Specify the name of the custom PowerShell snap-in.
  /// </summary>
  public override string Name
  {
    get
    {
      return "CustomPSSnapInTest";
    }
  }

  /// <summary>
  /// Specify the vendor for the custom PowerShell snap-in.
  /// </summary>
  public override string Vendor
  {
    get
    {
      return "Microsoft";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the vendor.
  /// Use the format: resourceBaseName,resourceName.
  /// </summary>
  public override string VendorResource
  {
    get
    {
        return "CustomPSSnapInTest,Microsoft";
    }
  }

  /// <summary>
  /// Specify a description of the custom PowerShell snap-in.
  /// </summary>
  public override string Description
  {
    get
    {
      return "This is a custom PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets.";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the description.
  /// Use the format: resourceBaseName,Description.
  /// </summary>
  public override string DescriptionResource
  {
    get
    {
        return "CustomPSSnapInTest,This is a custom PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets.";
    }
  }

  /// <summary>
  /// Specify the cmdlets that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<CmdletConfigurationEntry> _cmdlets;
  public override Collection<CmdletConfigurationEntry> Cmdlets
  {
    get
    {
      if (_cmdlets == null)
      {
        _cmdlets = new Collection<CmdletConfigurationEntry>();
        _cmdlets.Add(new CmdletConfigurationEntry("test-customsnapintest", typeof(TestCustomSnapinTest), "TestCmdletHelp.dll-help.xml"));
        _cmdlets.Add(new CmdletConfigurationEntry("test-helloworld", typeof(TestHelloWorld), "HelloWorldHelp.dll-help.xml"));
      }

      return _cmdlets;
    }
  }

  /// <summary>
  /// Specify the providers that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<ProviderConfigurationEntry> _providers;
  public override Collection<ProviderConfigurationEntry> Providers
  {
    get
    {
      if (_providers == null)
      {
        _providers = new Collection<ProviderConfigurationEntry>();
      }

      return _providers;
    }
  }

  /// <summary>
  /// Specify the types that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<TypeConfigurationEntry> _types;
  public override Collection<TypeConfigurationEntry> Types
  {
    get
    {
      if (_types == null)
      {
        _types = new Collection<TypeConfigurationEntry>();
      }

      return _types;
    }
  }

  /// <summary>
  /// Specify the formats that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<FormatConfigurationEntry> _formats;
  public override Collection<FormatConfigurationEntry> Formats
  {
    get
    {
      if (_formats == null)
      {
        _formats = new Collection<FormatConfigurationEntry>();
      }

      return _formats;
    }
  }
}
```

Para obter mais informações sobre como registar o snap-ins, consulte [como registrar Cmdlets, fornecedores e alojar aplicações](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) no [Guia do programador do Windows PowerShell](../prog-guide/windows-powershell-programmer-s-guide.md).

## <a name="see-also"></a>Veja Também

[Como registar os Cmdlets, fornecedores e alojar aplicações](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Shell do Windows PowerShell SDK](../windows-powershell-reference.md)
