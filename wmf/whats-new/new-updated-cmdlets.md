---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Cmdlets novos e atualizados
ms.openlocfilehash: 9ec31c89c0bc4b111b40e2d4725fa0782a573204
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856246"
---
# <a name="new-and-updated-cmdlets"></a>Cmdlets novos e atualizados

Adicionámos novos e atualizados cmdlets existentes com base nos comentários da Comunidade.

## <a name="archive-cmdlets"></a>Archive cmdlets

Dois novos cmdlets `Compress-Archive` e `Expand-Archive`, vou comprimir e expanda arquivos ZIP.

Para obter mais informações, consulte a [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/) documentação do módulo.

## <a name="catalog-cmdlets"></a>Cmdlets Catalog

Foram adicionados dois novos cmdlets no módulo Microsoft.PowerShell.Security.

- [New-FileCatalog](/powershell/module/microsoft.powershell.security/New-FileCatalog)
- [Test-FileCatalog](/powershell/module/microsoft.powershell.security/Test-FileCatalog)

Estes gerarem e validar os arquivos de catálogo do Windows.

## <a name="clipboard-cmdlets"></a>Cmdlets de área de transferência

`Get-Clipboard` e `Set-Clipboard` facilitar a transferência de conteúdo de e para uma sessão do Windows PowerShell. Os cmdlets de área de transferência suporta imagens, arquivos de áudio, listas de ficheiro e texto.

Para mais informações, consulte:

- [Get-Clipboard](/powershell/module/Microsoft.PowerShell.Management/Get-Clipboard)
- [Área de transferência de conjunto](/powershell/module/Microsoft.PowerShell.Management/Set-Clipboard)

## <a name="cryptographic-message-syntax-cms-cmdlets"></a>Cmdlets de sintaxe de mensagem (CMS) criptográfico

Os cmdlets de sintaxe de mensagem criptográfica suportam a encriptação e desencriptação de conteúdo utilizando o formato de padrão IETF para proteger criptograficamente mensagens conforme documentado [RFC5652](https://tools.ietf.org/html/rfc5652).

A encriptação de CMS padrão implementa a criptografia de chave pública, em que a chave utilizada para encriptar o conteúdo (a *chave pública*) e a chave utilizada para desencriptar o conteúdo (a *chave privada*) estão separados.

A chave pública pode ser partilhada amplamente e não dados confidenciais. Só pode ser desencriptado qualquer conteúdo encriptado com a chave pública com a chave privada. Para obter mais informações, consulte [criptografia de chave pública](https://en.wikipedia.org/wiki/Public-key_cryptography).

Para mais informações, consulte:

- [Get-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Get-CmsMessage.md)
- [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage.md)
- [Unprotect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/rotect-CmsMessage.md)

Certificados necessitem de um identificador exclusivo de utilização de chave (EKU), como 'Assinatura de código' ou 'Encriptados Mail', para identificá-los como certificados de encriptação de dados no PowerShell. Para ver os certificados de encriptação de documentos no fornecedor de certificado, pode utilizar o **DocumentEncryptionCert** parâmetro dinâmico de `Get-ChildItem`:

```powershell
Get-ChildItem Cert:\CurrentUser -DocumentEncryptionCert -Recurse
```

## <a name="extract-and-parse-structured-objects-from-string-content"></a>Extrair e analisar objetos estruturados do conteúdo de cadeia de caracteres

### <a name="convertfrom-string"></a>ConvertFrom-String

O novo `ConvertFrom-String` cmdlet oferece suporte a dois modos:

- Basic delimitados por análise
- Gerado automaticamente baseadas no exemplo de análise

Análise delimitados, por predefinição, divide a entrada em espaço em branco e atribui os nomes das propriedades aos grupos resultantes.

O **UpdateTemplate** parâmetro guarda os resultados do algoritmo de aprendizado num comentário no ficheiro de modelo. Isso torna o aprendizado processar (a fase mais lenta) um custo único. Executar `ConvertFrom-String` com um modelo que contém o algoritmo de aprendizagem codificada agora é quase instantânea.

Para obter mais informações, consulte [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).

### <a name="convert-string"></a>Convert-String

`Convert-String` permite-lhe fornecer antes e depois de exemplos de como pretende que o texto deve parecer. O cmdlet formata automaticamente o seu texto.

Para obter mais informações, consulte [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).

## <a name="updates-to-fileinfo-object"></a>Atualizações do objeto FileInfo

Informações de versão do ficheiro podem ser equivocado, especialmente em casos em que o ficheiro foi corrigido. WMF 5.0 adiciona novos **FileVersionRaw** e **ProductVersionRaw** propriedades do script **FileInfo** objetos.
Aqui estão as propriedades, tal como apresentado para powershell.exe (partindo do princípio de $pid é o ID do processo do PowerShell):

```powershell
Get-Process -Id $pid -FileVersionInfo | Format-List *version*
```

```Output
FileVersionRaw    : 10.0.17763.1
ProductVersionRaw : 10.0.17763.1
FileVersion       : 10.0.17763.1 (WinBuild.160101.0800)
ProductVersion    : 10.0.17763.1
```

## <a name="format-hex"></a>Format-Hex

`Format-Hex` permite-lhe ver o texto ou dados binários em formato hexadecimal.

Para obter mais informações, consulte [formato hexadecimal](/powershell/module/microsoft.powershell.utility/format-hex).

## <a name="get-childitem-has--depth-parameter"></a>Tem de GET-ChildItem - parâmetro de profundidade

`Get-ChildItem` tem agora uma **profundidade** parâmetro para utilização com **Recurse** para limitar a recursão:

## <a name="modules-support-for-declaring-version-ranges-1-etc"></a>Suporte de módulos para a declaração de intervalos de versão (1. *, etc.)

Agora pode combinar **MinimumVersion** e **MaximumVersion** para importar o módulo dentro do intervalo específico. Os parâmetros também suportam carateres universais.

```powershell
Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*
```

```Output
VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```

## <a name="new-guid"></a>New-Guid

Há muitos cenários em que youneed para identificador exclusivo. O `New-GUID` cmdlet fornece uma forma simple de criar um novo GUID.

```powershell
New-Guid
```

```Output
Guid
----
e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
```

## <a name="nonewline-parameter"></a>Parâmetro NoNewLine

`Out-File`, `Add-Content`, e `Set-Content` agora tem uma nova **NoNewline** comutador que omite uma nova linha após a saída. Por exemplo:

```powershell
"This is " | Out-File -FilePath Example.txt -NoNewline
"a single " | Add-Content -Path Example.txt -NoNewline
"sentence." | Add-Content -Path Example.txt -NoNewline
Get-Content .\Example.txt

```Output
This is a single sentence.
```

Sem **NoNewline** especificado, cada fragmento seria numa linha separada:

```powershell
"This is " | Out-File -FilePath Example.txt
"a single " | Add-Content -Path Example.txt
"sentence." | Add-Content -Path Example.txt
Get-Content .\Example.txt
```

```Output
This is
a single
sentence.
```

## <a name="interact-with-symbolic-links-using-improved-item-cmdlets"></a>Interagir com ligações simbólicas através dos cmdlets de Item melhorados

O cmdlet de Item e alguns cmdlets relacionados foram estendidos para oferecer suporte a links simbólicos.

### <a name="symbolic-link-files"></a>Arquivos de link simbólico

Neste exemplo, vamos criar um novo ficheiro de ligação simbólica designado MySymLinkFile.txt em C:\Temp que liga à $pshome\profile.ps1. Todos os três exemplos produzem o mesmo resultado.

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="symbolic-link-directories"></a>Diretórios de link simbólico

Neste exemplo, vamos criar um novo diretório de ligação simbólica MySymLinkDir em C:\Temp, que contém ligações para a pasta de $pshome com o nome. Todos os três exemplos produzem o mesmo resultado.

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkDir -Value $pshome
```

### <a name="hard-links"></a>Ligações fixas

As mesmo combinações de **caminho** e **nome** permitido conforme descrito acima.

```powershell
New-Item -ItemType HardLink -Path C:\Temp -Name MyHardLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="directory-junctions"></a>Junções de diretório

As mesmo combinações de **caminho** e **nome** permitido conforme descrito acima.

```powershell
New-Item -ItemType Junction -Path C:\Temp\MyJunctionDir -Value $pshome
```

### <a name="get-childitem"></a>Get-ChildItem

`Get-ChildItem` apresenta agora um "l" na **modo** propriedade para indicar um link simbólico ficheiro ou diretório.

```powershell
Get-ChildItem C:\Temp | sort LastWriteTime -Descending

Directory: C:\Temp

Mode       LastWriteTime Length Name
----       ------------- ------ ----
-a---- 6/13/2014 3:00 PM     16 File.txt
d----- 6/13/2014 3:00 PM        Directory
-a---l 6/13/2014 3:21 PM      0 MySymLinkFile.txt
d----l 6/13/2014 3:22 PM        MySymLinkDir
-a---l 6/13/2014 3:23 PM  23304 MyHardLinkFile.txt
d----l 6/13/2014 3:24 PM        MyJunctionDir
```

### <a name="remove-item"></a>Remove-Item

Remover links simbólicos funciona como qualquer outro tipo de item a remover.

```powershell
Remove-Item C:\Temp\MySymLinkFile.txt
Remove-Item C:\Temp\MySymLinkDir
```

Utilize o **força** parâmetro para remover os ficheiros no diretório de destino e a ligação simbólica.

```powershell
Remove-Item C:\Temp\MySymLinkDir -Force
```

## <a name="new-temporaryfile"></a>New-TemporaryFile

Por vezes, nos seus scripts, tem de criar um arquivo temporário. Agora pode fazer isso com o `New-TemporaryFile` cmdlet:

```powershell
$tempFile = New-TemporaryFile
$tempFile.FullName
```

```Output
C:\Users\user1\AppData\Local\Temp\tmp375.tmp
```

## <a name="network-switch-management-with-powershell"></a>Gestão de Comutador de Rede com o PowerShell

Os cmdlets de comutador de rede, introduzidos no WMF 5.0, permitem-lhe aplicar o comutador, LAN virtual (VLAN) e básica configuração de porta do comutador de rede de camada 2 a comutadores de rede com logótipo de certificação do Windows Server 2012 R2. Utilizando estes cmdlets pode efetuar:

- Global mudar a configuração, tais como:
  - Nome de anfitrião do conjunto
  - Faixa de comutador de conjunto
  - Manter a configuração
  - Ativar ou desativar funcionalidade

- Configuração de VLAN:
  - Criar ou remover VLAN
  - Ativar ou desativar a VLAN
  - Enumerar VLAN
  - Nome amigável do conjunto a uma VLAN

- Configuração da porta de camada 2:
  - Enumerar portas
  - Ativar ou desativar as portas
  - Modos de porta do conjunto e propriedades
  - Adicionar ou associar a VLAN de ramal ou acesso na porta

Para obter mais informações, consulte a [NetworkSwitchManager](/powershell/module/networkswitchmanager/) documentação.

## <a name="generate-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a>Gerar os cmdlets do PowerShell com base num ponto de final de OData com ODataUtils

O módulo de ODataUtils permite a geração de cmdlets do PowerShell a partir de pontos de extremidade REST que dão suporte a OData. O módulo de Microsoft.PowerShell.ODataUtils inclui as seguintes funcionalidades:

- Canal de informações adicionais do ponto de extremidade do lado do servidor para o lado do cliente.
- Suporte de paginação do lado do cliente
- Filtragem do lado do servidor utilizando o - parâmetro selecione
- Suporte para cabeçalhos de solicitação da web

Os cmdlets do proxy gerados pela `Export-ODataEndPointProxy` cmdlet fornecem informações adicionais do ponto de final de OData do lado do servidor sobre o **informações** stream.

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
```

No exemplo a seguir, estamos a obter o produto superior e capturar a saída no `$infoStream` variável.

Ao especificar **IncludeTotalResponseCount** parâmetro, podemos obter a contagem total de todos os **produto** registos disponíveis no servidor.

```powershell
Import-Module $generatedProxyModuleDir -Force
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
$additionalInfo['odata.count']
```

Pode obter os registos do servidor em lotes com o suporte de paginação do lado do cliente. Isto é útil quando tem de obter uma grande quantidade de dados do servidor através da rede.

```powershell
$skipCount = 0
$batchSize = 3
while($skipCount -le $additionalInfo['odata.count'])
{
  Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
  $skipCount += $batchSize
}
```

Os cmdlets do proxy gerado suportam o **selecione** parâmetro que é utilizado como um filtro para receber apenas as propriedades de registo que o cliente precisa. A filtragem ocorre no servidor, o que reduz a quantidade de dados que são transferidos através da rede.

```powershell
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

O `Export-ODataEndpointProxy` cmdlet e os cmdlets do proxy gerados por ele, suportam agora o **cabeçalhos** parâmetro. O cabeçalho pode ser utilizado para obter informações adicionais esperadas pelo ponto de final de OData do channel.

No exemplo a seguir, uma tabela de hash que contém uma chave de subscrição é fornecida para o **cabeçalhos** parâmetro. Este é um exemplo típico para serviços que esperam uma chave de subscrição para a autenticação.

```powershell
Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
