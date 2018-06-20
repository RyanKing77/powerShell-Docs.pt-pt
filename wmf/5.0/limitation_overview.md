---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 4b006d2ac812abf1f281b6b4e382c2760f92a95c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186835"
---
# <a name="known-issues-and-limitations"></a>Limitações e Problemas Conhecidos

<a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a>Atalhos de PowerShell sejam interrompidos quando utilizado pela primeira vez
------------------------------------------------------------

**Resolução:** , efetue uma das seguintes ações:

1.  Clique com o botão direito do rato no atalho do PowerShell. Selecione "O Windows PowerShell" Iniciar no modo de não elevada.
2.  Clique com o botão direito do rato no atalho do PowerShell. Clique em "Windows PowerShell" e selecione "Executar como administrador de" iniciar um elevados.

Assim que tiver efetuado qualquer uma das ações acima, os atalhos de PowerShell irão funcionar. Estas ações tem de ser executada apenas uma vez.


<a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a>Módulos do PowerShell e recursos de DSC reporte erros acerca ExecutionPolicy no Windows 7
-------------------------------------------------------------------------------------
No Windows 7, a utilização de módulos do PowerShell e recursos de DSC poderá resultar em erros comunicados sobre ExecutionPolicy.

**Resolução:** como o ExecutionPolicy RemoteSigned executando o seguinte comando numa sessão do PowerShell elevada (executar como administrador):

```powershell
Set-ExecutionPolicy RemoteSigned
```

<a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a>Ligar a um ponto de final Exchange antigo remoto faz com que uma falha
------------------------------------------------------------

O ponto final do Exchange antigo redireciona para um novo ponto final. Há um erro na lógica de redirecionamento que resultados com falhas.

**Resolução:** ligar diretamente para o novo ponto final.


<a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a>A funcionalidade de registo de inventário de software está parada indica após a instalação do WMF 5.0 no Windows Server 2012 R2
-------------------------------------------------------------------------------------------------------------

Ao instalar o WMF 5.0 num Windows Server 2012 R2 que já está a executar o SIL, a funcionalidade registo de inventário de Software indica é interrompida após a instalação.

**Resolução:** executar o cmdlet Start-SilLogging uma vez após a instalação do WMF, como o processo de instalação erradamente irá parar a funcionalidade registo de inventário de Software.

<a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a>Get-ChildItem não funciona se - LiteralPath - Recurse são utilizados e em conjunto
--------------------------------------------------------------------------

Se um nome de diretório contém um caráter universal inválido, em seguida, Get-ChildItem irá não produzir resultados esperados quando - LiteralPath tanto - Recurse são utilizados em conjunto.

**Resolução:** não ideal, mas a atual solução é implementar recursão no script em vez de depender o cmdlet.


<a name="sysprep-fails-after-wmf-50-installation"></a>Falha de Sysprep após a instalação do WMF 5.0
----------------------------------------

Existem duas soluções para este problema, dependendo da versão do Windows Server estão em execução.

**Resolução:**
- Para sistemas com **Windows Server 2008 R2**
  1. Abra Powershell como administrador
  2. Execute o seguinte comando

  ```powershell
    Set-SilLogging –TargetUri https://BlankTarget –CertificateThumbprint 0123456789
  ```
  3. Execute o comando e ignorar o erro, como os são esperados.

  ```powershell
    Publish-SilData
   ```
  4. Elimine os ficheiros no diretório \windows\system32\logfiles\sil\.

  ```powershell
    Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
  ```
  5. Instale todas as atualizações do Windows importante disponíveis e iniciar a operação de Sysyprep normalmente.

- Para sistemas com **Windows Server 2012**
  1.    Depois de instalar o WMF 5.0 no servidor para ser Sysprep'd, inicie sessão como administrador.
  2.    Copie Generize.xml do diretório \Windows\System32\Sysprep\ActionFiles\ para uma localização fora do diretório do Windows, C:\ por exemplo.
  3.    Abra a sua cópia Generalize.xml com o bloco de notas.
  4.    Localizar e remova o seguinte texto, uma instância de cada tem de ser eliminado (estarão perto do final do documento).

    ```
    <sysprepOrder order="0x3200"></sysprepOrder>
    <sysprepOrder order="0x3300"></sysprepOrder>
    ```

  5.    Guardar a cópia editada de Generalize.xml e feche o ficheiro.
  6.    Abra uma linha de comandos como administrador
  7.    Execute o seguinte comando para assumir a propriedade do ficheiro Generalize.xml na pasta system32:

    ```
    Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
    ```

  8.    Execute o comando seguinte para definir as permissões adequadas no ficheiro:

    ```
    Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
    ```
      * Responder Sim na linha de confirmação.
      * Tenha em atenção que `<AdministratorUserName>` deve ser substituído pelo nome de utilizador que seja administrador no computador. Por exemplo, "Administrador".

  9.    Copie o ficheiro editado e guardado através de para o diretório de Sysprep utilizando o seguinte comando:

    ```
    xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
    ```
      * Responder Sim para substituir (tenha em atenção que se não houver nenhuma linha de comandos para substituir, volte a verificar o caminho que introduziu).
      * Assume a que sua cópia editada Generalize.xml foi copiada para C:\.

  10.   Generalize.xml agora é atualizado com a solução. Execute o Sysprep com a opção de generalize ativada.
