---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 3d74217621d00dfd68cad1c45d187a9c2ffb9980
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054379"
---
# <a name="known-issues-and-limitations"></a>Limitações e Problemas Conhecidos

## <a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a>Atalhos do PowerShell são perdidos quando utilizado pela primeira vez

**Resolução:** Execute uma das seguintes ações:

1. Clique com o botão direito do rato no atalho do PowerShell. Selecione "Windows PowerShell" para iniciar num modo não elevados.
2. Clique com o botão direito do rato no atalho do PowerShell. Clique com o botão direito do rato em "Windows PowerShell" e selecione "Executar como administrador" iniciar num modo elevado.

Depois de ter realizado qualquer uma das ações acima, os atalhos do PowerShell irão funcionar. Estas ações precisam ser executadas apenas uma vez.

## <a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a>Erros de relatório de módulos do PowerShell e recursos de DSC sobre ExecutionPolicy no Windows 7

No Windows 7, a utilização de módulos do PowerShell e recursos de DSC pode resultar em erros comunicados sobre ExecutionPolicy.

**Resolução:** Defina o ExecutionPolicy para RemoteSigned, executando o seguinte comando numa sessão do PowerShell elevada (executar como administrador):

```powershell
Set-ExecutionPolicy RemoteSigned
```

## <a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a>Ligar a um ponto de extremidade Exchange antigo remoto faz com que uma falha

Redireciona o antigo ponto de extremidade do Exchange para um novo ponto final. Há um bug na lógica de redirecionamento que resulte numa pane.

**Resolução:** Ligue-se diretamente para o novo ponto final.

## <a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a>Funcionalidade de registo de inventário de software está parada erroneamente após a instalação de WMF 5.0 no Windows Server 2012 R2

Ao instalar o WMF 5.0 no Windows Server 2012 R2 que já está a executar o SIL, a funcionalidade registo de inventário de Software incorretamente é interrompida após a instalação.

**Resolução:** Execute o cmdlet Start-SilLogging uma vez após a instalação de WMF, como o processo de instalação incorretamente irá parar a funcionalidade registo de inventário de Software.

## <a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a>`Get-ChildItem` não funciona se - LiteralPath e - Recurse são utilizados em conjunto

Se um nome de diretório contém um caráter de carateres universais inválido, em seguida, `Get-ChildItem` não produzirá os resultados esperados quando – LiteralPath tanto - Recurse são utilizados em conjunto.

**Resolução:** Solução não ideal, mas atual é implementar a recursão no script, em vez de contar com o cmdlet.

## <a name="sysprep-fails-after-wmf-50-installation"></a>Falha de Sysprep após a instalação de WMF 5.0

Existem duas soluções alternativas para este problema, dependendo da versão do Windows Server que está a executar.

**Resolução:**

- Para sistemas que executam **Windows Server 2008 R2**
  1. Abra PowerShell como administrador
  2. Execute o seguinte comando

     ```powershell
     Set-SilLogging –TargetUri https://BlankTarget –CertificateThumbprint 0123456789
     ```

  3. Execute o comando e ignorar o erro, como eles são esperados.

     ```powershell
     Publish-SilData
     ```

  4. Eliminar os ficheiros no diretório de \Windows\System32\Logfiles\SIL\

     ```powershell
     Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
     ```

  5. Instale todas as atualizações Windows importante disponíveis e iniciar a operação de Sysyprep normalmente.

- Para sistemas que executam **Windows Server 2012**
  1. Depois de instalar o WMF 5.0 no servidor para ser Sysprep d', inicie sessão como administrador.
  2. Copiar Generize.xml do diretório \Windows\System32\Sysprep\ActionFiles\ para uma localização fora do diretório do Windows, C:\ Por exemplo.
  3. Abra a sua cópia Generalize.xml com o bloco de notas.
  4. Localizar e remover o texto a seguir, uma instância de cada tem de ser eliminado (estará próximo do final do documento).

     ```xml
     <sysprepOrder order="0x3200"></sysprepOrder>
     <sysprepOrder order="0x3300"></sysprepOrder>
     ```

  5. Guardar a cópia editada de Generalize.xml e feche o ficheiro.
  6. Abra uma linha de comandos como administrador
  7. Execute o seguinte comando para obter a propriedade do ficheiro Generalize.xml na pasta system32:

     ```powershell
     Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

  8. Execute o seguinte comando para definir as permissões adequadas no ficheiro:

     ```powershell
     Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
     ```

     - Responda Sim no prompt de confirmação.
     - Tenha em atenção que `<AdministratorUserName>` deve ser substituído pelo nome de usuário que seja administrador no computador. Por exemplo, "Administrador".

  9. Copie o ficheiro editado e guardado ao longo para o diretório de Sysprep utilizando o seguinte comando:

     ```powershell
     xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

     - Responder Yes para substituir (Observe que se não houver nenhuma linha de comandos para substituir, volte a verificar o caminho que introduziu).
     - Assume a que sua cópia editada do Generalize.xml foi copiada para C:\.

  10. Generalize.xml está agora atualizada com a solução alternativa. Execute o Sysprep com a opção de generalize ativada.