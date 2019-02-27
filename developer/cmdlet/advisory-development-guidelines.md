---
title: Diretrizes de consultoria de desenvolvimento | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 79c9bcbc-a2eb-4253-a4b8-65ba54ce8d01
caps.latest.revision: 9
ms.openlocfilehash: 97a2d3587f8f69edc92150474e94a620ff9a2f71
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845795"
---
# <a name="advisory-development-guidelines"></a>Advisory Development Guidelines (Diretrizes de Desenvolvimento Recomendadas)

Esta secção descreve as diretrizes que deve considerar para garantir boa experiências de desenvolvimento e de utilizador. Por vezes, podem ser aplicadas e, às vezes, talvez não.

## <a name="design-guidelines"></a>Diretrizes de design

- [Suporte a um parâmetro de InputObject (AD01)](./advisory-development-guidelines.md#AD01)

- [Suporta o parâmetro Force (AD02)](./advisory-development-guidelines.md#AD02)

- [Lidar com as credenciais através do Windows PowerShell (AD03)](./advisory-development-guidelines.md#AD03)

- [Suporta parâmetros de codificação (AD04)](./advisory-development-guidelines.md#AD04)

- [Cmdlets de teste deverá devolver um valor booleano (AD05)](./advisory-development-guidelines.md#AD05)

## <a name="code-guidelines"></a>Diretrizes de código

- [Siga as convenções de nomenclatura de classe Cmdlet (AC01)](./advisory-development-guidelines.md#AC01)

- [Se nenhuma entrada de Pipeline substituir o método BeginProcessing (AC02)](./advisory-development-guidelines.md#AC02)

- [Para processar pedidos de paragem substituem o método de StopProcessing (AC03)](./advisory-development-guidelines.md#AC03)

- [Implementar a Interface IDisposable (AC04)](./advisory-development-guidelines.md#AC04)

- [Usar tipos de parâmetro de amigável à serialização (AC05)](./advisory-development-guidelines.md#AC05)

- [Utilizar SecureString para dados confidenciais (AC06)](./advisory-development-guidelines.md#AC06)

## <a name="design-guidelines"></a>Diretrizes de design

As diretrizes seguintes devem ser consideradas ao criar cmdlets. Quando encontrar uma diretriz de Design que se aplica à sua situação, certifique-se de que examinar as diretrizes de código para obter diretrizes semelhantes.

### <a name="support-an-inputobject-parameter-ad01"></a>Suporte a um parâmetro de InputObject (AD01)

Como o Windows PowerShell funciona diretamente com objetos do Microsoft .NET Framework, um objeto do .NET Framework, muitas vezes, está disponível-se de que exatamente as correspondências de tipo o utilizador tem de executam uma determinada operação. `InputObject` é o nome padrão para um parâmetro que pega desse objecto como entrada. Por exemplo, o exemplo **Stop-Proc** cmdlet no [StopProc Tutorial](./stopproc-tutorial.md) define um `InputObject` parâmetro do tipo de processo que suporta a entrada do pipeline. O utilizador pode obter um conjunto de objetos de processo, manipulá-los para selecionar os objetos exatos para parar e, em seguida, passá-los para o **Stop-Proc** cmdlet diretamente.

### <a name="support-the-force-parameter-ad02"></a>Suporta o parâmetro Force (AD02)

Ocasionalmente, um cmdlet tem de proteger o usuário de executar uma operação pedida. Tal um cmdlet deve suportar um `Force` parâmetro para permitir ao utilizador substituir essa proteção, se o utilizador tem permissões para executar a operação.

Por exemplo, o [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item) cmdlet não remove normalmente um ficheiro só de leitura. No entanto, este cmdlet suporta um `Force` parâmetro para que um utilizador pode forçar a remoção de um ficheiro só de leitura. Se o utilizador já tem permissão para modificar o atributo só de leitura e o utilizador remove o ficheiro, utilize o `Force` parâmetro simplifica a operação. No entanto, se o utilizador não tem permissão para remover o arquivo, o `Force` parâmetro não tem qualquer efeito.

### <a name="handle-credentials-through-windows-powershell-ad03"></a>Lidar com as credenciais através do Windows PowerShell (AD03)

Um cmdlet deve definir um `Credential` parâmetro para representar as credenciais. Este parâmetro tem de ser do tipo [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) e tem de ser definido com uma declaração de atributo de credencial. Esse suporte solicita automaticamente ao utilizador para o nome de utilizador, a palavra-passe ou para ambos, quando uma credencial completa não é fornecida diretamente. Para obter mais informações sobre o atributo de credenciais, consulte [declaração de atributo de credencial](./credential-attribute-declaration.md).

### <a name="support-encoding-parameters-ad04"></a>Suporta parâmetros de codificação (AD04)

Se seu cmdlet lê ou escreve o texto de ou para um formato binário, por exemplo, escrever ou ler a partir de um ficheiro num sistema de ficheiros, seu cmdlet tem de ter o parâmetro de codificação que especifica como o texto está codificado no formato binário.

### <a name="test-cmdlets-should-return-a-boolean-ad05"></a>Cmdlets de teste deverá devolver um valor booleano (AD05)

Cmdlets que efetuam testes relativamente aos respetivos recursos deverá devolver um [Boolean](/dotnet/api/System.Boolean) escreva para o pipeline, para que podem ser utilizadas em expressões condicionais.

## <a name="code-guidelines"></a>Diretrizes de código

As diretrizes seguintes devem ser consideradas ao escrever o código de cmdlet. Quando encontrar uma diretriz que se aplica à sua situação, certifique-se de que examinar as diretrizes de Design para obter diretrizes semelhantes.

### <a name="follow-cmdlet-class-naming-conventions-ac01"></a>Siga as convenções de nomenclatura de classe Cmdlet (AC01)

Por seguintes convenções de nomenclatura padrão, tornar seus cmdlets mais detectáveis e ajudar o utilizador a que se compreender exatamente o que os cmdlets fazem. Esta prática é particularmente importante para outros desenvolvedores usando o Windows PowerShell como os cmdlets são tipos públicos.

#### <a name="define-a-cmdlet-in-the-correct-namespace"></a>Definir um Cmdlet no espaço de nomes correto

Normalmente define a classe para um cmdlet num espaço de nomes do .NET Framework que acrescenta ". Comandos"para o espaço de nomes que representa o produto no qual é executado o cmdlet. Por exemplo, os cmdlets que estão incluídas com o Windows PowerShell são definidos no `Microsoft.PowerShell.Commands` espaço de nomes.

#### <a name="name-the-cmdlet-class-to-match-the-cmdlet-name"></a>Nome da classe Cmdlet corresponder ao nome do Cmdlet

Ao atribuir nomes a classe do .NET Framework que implementa um cmdlet, nomeio a classe "*\<verbo >**\<substantivo >**\<comando >*", em que substitua o  *\<Verbo >* e  *\<substantivo >* marcadores de posição com o verbo e substantivo usado para o nome do cmdlet. Por exemplo, o [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet é implementado por uma classe chamada `GetProcessCommand`.

### <a name="if-no-pipeline-input-override-the-beginprocessing-method-ac02"></a>Se nenhuma entrada de Pipeline substituir o método BeginProcessing (AC02)

Se seu cmdlet não aceita entrada do pipeline, o processamento deve ser implementado no [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método. Utilização deste método permite que o Windows PowerShell manter a ordenação entre cmdlets. O primeiro cmdlet no pipeline sempre retorna seus objetos antes dos cmdlets restantes no pipeline de obter uma oportunidade de começar o seu processamento.

### <a name="to-handle-stop-requests-override-the-stopprocessing-method-ac03"></a>Para processar pedidos de paragem substituem o método de StopProcessing (AC03)

Substituir a [System.Management.Automation.Cmdlet.Stopprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) método para que seu cmdlet pode manipular o sinal de paragem. Alguns cmdlets demorar muito tempo para concluir o funcionamento deles, e permitem que um longo tempo passar entre chamadas para o tempo de execução do Windows PowerShell, por exemplo, quando o cmdlet bloqueia o thread em chamadas RPC de execução longa. Isto inclui cmdlets que fazem chamadas para o [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) método para o [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método e para outros comentários mecanismos que podem demorar muito tempo a concluir. Nesses casos, o utilizador poderá ter de enviar um sinal de paragem para estes cmdlets.

### <a name="implement-the-idisposable-interface-ac04"></a>Implementar a Interface IDisposable (AC04)

Se seu cmdlet tem objetos que não são descartados de (escrito para o pipeline) o [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método, seu cmdlet pode exigir a disposição do objeto adicionais. Por exemplo, se seu cmdlet abre um identificador de ficheiro no seu [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método e mantém o identificador aberto para utilização pelo [System.Management.Automation.Cmdlet.Processrecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método, esse identificador tem de ser fechado ao final do processamento.

O tempo de execução do Windows PowerShell não sempre chamar o [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método. Por exemplo, o [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) não poderia ser chamado o método se o cmdlet é cancelado midway durante sua operação ou se acabar o erro ocorre em qualquer parte do cmdlet. Por conseguinte, a classe do .NET Framework para um cmdlet que necessita de limpeza do objeto deve implementar o concluída [System.Idisposable](/dotnet/api/System.IDisposable) padrão de interface, incluindo o finalizador, para que o tempo de execução do Windows PowerShell possa chamar ambos o [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) e [System.Idisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) métodos no final do processamento.

### <a name="use-serialization-friendly-parameter-types-ac05"></a>Usar tipos de parâmetro de amigável à serialização (AC05)

Para suportar a executar o cmdlet em computadores remotos, utilize tipos que podem ser facilmente serializados no computador cliente e, em seguida, reativados no computador do servidor. Os tipos de siga são amigável à serialização.

Tipos primitivos:

- Byte, SByte, Decimal, Single, Double, Int16, Int32, Int64, Uint16, UInt32 e UInt64.

- Booleano, Guid, Byte [], período de tempo, DateTime, Uri e versão.

- Char, cadeia de caracteres, XmlDocument.

Tipos de rehydratable internos:

- PSPrimitiveDictionary

- SwitchParmeter

- PSListModifier

- PSCredential

- IPAddress, MailAddress

- CultureInfo

- X509Certificate2, X500DistinguishedName

- RegistrySecurity DirectorySecurity, FileSecurity,

Outros tipos de:

- SecureString

- Contentores (listas e dicionários do tipo acima)

### <a name="use-securestring-for-sensitive-data-ac06"></a>Utilizar SecureString para dados confidenciais (AC06)

Ao manipular dados confidenciais sempre utilizar o [SecureString](/dotnet/api/System.Security.SecureString) tipo de dados. Isso pode incluir a entrada do pipeline para parâmetros, bem como devolver dados confidenciais para o pipeline.

## <a name="see-also"></a>Consulte Também

[Diretrizes de desenvolvimento necessárias](./required-development-guidelines.md)

[Diretrizes de desenvolvimento altamente incentivadas](./strongly-encouraged-development-guidelines.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
