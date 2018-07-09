---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 4eb2f0bac4f2169a9a06d80cb4fa214a09cdfa86
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892989"
---
# <a name="known-issues-and-limitations"></a><span data-ttu-id="27574-102">Limitações e Problemas Conhecidos</span><span class="sxs-lookup"><span data-stu-id="27574-102">Known Issues and Limitations</span></span>

## <a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a><span data-ttu-id="27574-103">Atalhos do PowerShell são perdidos quando utilizado pela primeira vez</span><span class="sxs-lookup"><span data-stu-id="27574-103">PowerShell Shortcuts are broken when used for the first time</span></span>

<span data-ttu-id="27574-104">**Resolução:** execute uma das seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="27574-104">**Resolution:** Perform one of the following actions:</span></span>

1. <span data-ttu-id="27574-105">Clique com o botão direito do rato no atalho do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="27574-105">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="27574-106">Selecione "Windows PowerShell" para iniciar num modo não elevados.</span><span class="sxs-lookup"><span data-stu-id="27574-106">Select “Windows PowerShell” to launch in a non-elevated mode.</span></span>
2. <span data-ttu-id="27574-107">Clique com o botão direito do rato no atalho do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="27574-107">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="27574-108">Clique com o botão direito do rato em "Windows PowerShell" e selecione "Executar como administrador" iniciar num modo elevado.</span><span class="sxs-lookup"><span data-stu-id="27574-108">Right click on “Windows PowerShell” and select “Run As Administrator” to launch in an elevated mode.</span></span>

<span data-ttu-id="27574-109">Depois de ter realizado qualquer uma das ações acima, os atalhos do PowerShell irão funcionar.</span><span class="sxs-lookup"><span data-stu-id="27574-109">Once you have performed either of the above actions, the PowerShell shortcuts will work.</span></span> <span data-ttu-id="27574-110">Estas ações precisam ser executadas apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="27574-110">These actions need to be performed only once.</span></span>

## <a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a><span data-ttu-id="27574-111">Erros de relatório de módulos do PowerShell e recursos de DSC sobre ExecutionPolicy no Windows 7</span><span class="sxs-lookup"><span data-stu-id="27574-111">PowerShell Modules and DSC Resources report errors about ExecutionPolicy on Windows 7</span></span>

<span data-ttu-id="27574-112">No Windows 7, a utilização de módulos do PowerShell e recursos de DSC pode resultar em erros comunicados sobre ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="27574-112">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

<span data-ttu-id="27574-113">**Resolução:** definido o ExecutionPolicy para RemoteSigned, executando o seguinte comando numa sessão do PowerShell elevada (executar como administrador):</span><span class="sxs-lookup"><span data-stu-id="27574-113">**Resolution:** Set the ExecutionPolicy to RemoteSigned by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

## <a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a><span data-ttu-id="27574-114">Ligar a um ponto de extremidade Exchange antigo remoto faz com que uma falha</span><span class="sxs-lookup"><span data-stu-id="27574-114">Connecting to an old remote Exchange endpoint causes a crash</span></span>

<span data-ttu-id="27574-115">Redireciona o antigo ponto de extremidade do Exchange para um novo ponto final.</span><span class="sxs-lookup"><span data-stu-id="27574-115">The old Exchange endpoint redirects to a new endpoint.</span></span> <span data-ttu-id="27574-116">Há um bug na lógica de redirecionamento que resulte numa pane.</span><span class="sxs-lookup"><span data-stu-id="27574-116">There is a bug in the redirection logic that results in a crash.</span></span>

<span data-ttu-id="27574-117">**Resolução:** ligar diretamente para o novo ponto final.</span><span class="sxs-lookup"><span data-stu-id="27574-117">**Resolution:** Connect directly to the new endpoint.</span></span>

## <a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a><span data-ttu-id="27574-118">Funcionalidade de registo de inventário de software está parada erroneamente após a instalação de WMF 5.0 no Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="27574-118">Software Inventory Logging feature is erroneously stopped after WMF 5.0 installation on Windows Server 2012 R2</span></span>

<span data-ttu-id="27574-119">Ao instalar o WMF 5.0 no Windows Server 2012 R2 que já está a executar o SIL, a funcionalidade registo de inventário de Software incorretamente é interrompida após a instalação.</span><span class="sxs-lookup"><span data-stu-id="27574-119">When installing WMF 5.0 on a Windows Server 2012 R2 that is already running SIL, the Software Inventory Logging feature is erroneously stopped after installation.</span></span>

<span data-ttu-id="27574-120">**Resolução:** executar o cmdlet Start-SilLogging uma vez após a instalação de WMF, como o processo de instalação incorretamente irá parar a funcionalidade registo de inventário de Software.</span><span class="sxs-lookup"><span data-stu-id="27574-120">**Resolution:** Run the Start-SilLogging cmdlet once after the WMF installation, as the installation process will errantly stop the Software Inventory Logging feature.</span></span>

## <a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a><span data-ttu-id="27574-121">`Get-ChildItem` não funciona se - LiteralPath e - Recurse são utilizados em conjunto</span><span class="sxs-lookup"><span data-stu-id="27574-121">`Get-ChildItem` does not work if -LiteralPath and -Recurse are used together</span></span>

<span data-ttu-id="27574-122">Se um nome de diretório contém um caráter de carateres universais inválido, em seguida, `Get-ChildItem` não produzirá os resultados esperados quando – LiteralPath tanto - Recurse são utilizados em conjunto.</span><span class="sxs-lookup"><span data-stu-id="27574-122">If a directory name contains an invalid wildcard character, then `Get-ChildItem` will not produce expected results when both -LiteralPath and -Recurse are used together.</span></span>

<span data-ttu-id="27574-123">**Resolução:** solução não ideal, mas atual é implementar a recursão no script, em vez de contar com o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="27574-123">**Resolution:** Not ideal, but current workaround is to implement recursion in the script rather than rely on the cmdlet.</span></span>

## <a name="sysprep-fails-after-wmf-50-installation"></a><span data-ttu-id="27574-124">Falha de Sysprep após a instalação de WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="27574-124">Sysprep fails after WMF 5.0 installation</span></span>

<span data-ttu-id="27574-125">Existem duas soluções alternativas para este problema, dependendo da versão do Windows Server que está a executar.</span><span class="sxs-lookup"><span data-stu-id="27574-125">There are two workarounds for this issue depending on the version of Windows Server you are running.</span></span>

<span data-ttu-id="27574-126">**Resolução:**</span><span class="sxs-lookup"><span data-stu-id="27574-126">**Resolution:**</span></span>

- <span data-ttu-id="27574-127">Para sistemas que executam **Windows Server 2008 R2**</span><span class="sxs-lookup"><span data-stu-id="27574-127">For systems running **Windows Server 2008 R2**</span></span>
  1. <span data-ttu-id="27574-128">Abra Powershell como administrador</span><span class="sxs-lookup"><span data-stu-id="27574-128">Open Powershell as an administrator</span></span>
  2. <span data-ttu-id="27574-129">Execute o seguinte comando</span><span class="sxs-lookup"><span data-stu-id="27574-129">Run the following command</span></span>

     ```powershell
     Set-SilLogging –TargetUri https://BlankTarget –CertificateThumbprint 0123456789
     ```

  3. <span data-ttu-id="27574-130">Execute o comando e ignorar o erro, como eles são esperados.</span><span class="sxs-lookup"><span data-stu-id="27574-130">Run the command and ignore the error, as they are expected.</span></span>

     ```powershell
     Publish-SilData
     ```

  4. <span data-ttu-id="27574-131">Eliminar os ficheiros no diretório de \Windows\System32\Logfiles\SIL\\</span><span class="sxs-lookup"><span data-stu-id="27574-131">Delete the files in  \Windows\System32\Logfiles\SIL\ directory</span></span>

     ```powershell
     Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
     ```

  5. <span data-ttu-id="27574-132">Instale todas as atualizações Windows importante disponíveis e iniciar a operação de Sysyprep normalmente.</span><span class="sxs-lookup"><span data-stu-id="27574-132">Install all available important Windows Updates, and begin Sysyprep operation normally.</span></span>

- <span data-ttu-id="27574-133">Para sistemas que executam **Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="27574-133">For systems running **Windows Server 2012**</span></span>
  1. <span data-ttu-id="27574-134">Depois de instalar o WMF 5.0 no servidor para ser Sysprep d', inicie sessão como administrador.</span><span class="sxs-lookup"><span data-stu-id="27574-134">After installing WMF 5.0 on the server to be Sysprep’d, login as administrator.</span></span>
  2. <span data-ttu-id="27574-135">Copie Generize.xml do diretório \Windows\System32\Sysprep\ActionFiles\ para uma localização fora do diretório do Windows, C:\ por exemplo.</span><span class="sxs-lookup"><span data-stu-id="27574-135">Copy Generize.xml from directory \Windows\System32\Sysprep\ActionFiles\ to a location outside of the Windows directory, C:\ for example.</span></span>
  3. <span data-ttu-id="27574-136">Abra a sua cópia Generalize.xml com o bloco de notas.</span><span class="sxs-lookup"><span data-stu-id="27574-136">Open your Generalize.xml copy with notepad.</span></span>
  4. <span data-ttu-id="27574-137">Localizar e remover o texto a seguir, uma instância de cada tem de ser eliminado (estará próximo do final do documento).</span><span class="sxs-lookup"><span data-stu-id="27574-137">Find and remove the following text, one instance of each needs to be deleted (they will be near the end of the document).</span></span>

     ```xml
     <sysprepOrder order="0x3200"></sysprepOrder>
     <sysprepOrder order="0x3300"></sysprepOrder>
     ```

  5. <span data-ttu-id="27574-138">Guardar a cópia editada de Generalize.xml e feche o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="27574-138">Save the edited copy of Generalize.xml and close the file.</span></span>
  6. <span data-ttu-id="27574-139">Abra uma linha de comandos como administrador</span><span class="sxs-lookup"><span data-stu-id="27574-139">Open a command prompt as administrator</span></span>
  7. <span data-ttu-id="27574-140">Execute o seguinte comando para obter a propriedade do ficheiro Generalize.xml na pasta system32:</span><span class="sxs-lookup"><span data-stu-id="27574-140">Run the following command to take ownership of the Generalize.xml file in system32 folder:</span></span>

     ```powershell
     Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

  8. <span data-ttu-id="27574-141">Execute o seguinte comando para definir as permissões adequadas no ficheiro:</span><span class="sxs-lookup"><span data-stu-id="27574-141">Run the following command to set appropriate permission on the file:</span></span>

     ```powershell
     Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
     ```

     - <span data-ttu-id="27574-142">Responda Sim no prompt de confirmação.</span><span class="sxs-lookup"><span data-stu-id="27574-142">Answer Yes at the prompt for confirmation.</span></span>
     - <span data-ttu-id="27574-143">Tenha em atenção que `<AdministratorUserName>` deve ser substituído pelo nome de usuário que seja administrador no computador.</span><span class="sxs-lookup"><span data-stu-id="27574-143">Note that `<AdministratorUserName>` should be replaced by the username who is administrator on the machine.</span></span> <span data-ttu-id="27574-144">Por exemplo, "Administrador".</span><span class="sxs-lookup"><span data-stu-id="27574-144">For example, "Administrator".</span></span>

  9. <span data-ttu-id="27574-145">Copie o ficheiro editado e guardado ao longo para o diretório de Sysprep utilizando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="27574-145">Copy the file you edited and saved over to the Sysprep directory using the following command:</span></span>

     ```powershell
     xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

     - <span data-ttu-id="27574-146">Responder Yes para substituir (Observe que se não houver nenhuma linha de comandos para substituir, volte a verificar o caminho que introduziu).</span><span class="sxs-lookup"><span data-stu-id="27574-146">Answer Yes to overwrite (note that if there is no prompt to overwrite, double check the path entered).</span></span>
     - <span data-ttu-id="27574-147">Assume a que sua cópia editada do Generalize.xml foi copiada para C:\.</span><span class="sxs-lookup"><span data-stu-id="27574-147">Assumes your edited copy of Generalize.xml was copied to C:\ .</span></span>

  10. <span data-ttu-id="27574-148">Generalize.xml está agora atualizada com a solução alternativa.</span><span class="sxs-lookup"><span data-stu-id="27574-148">Generalize.xml is now updated with the workaround.</span></span> <span data-ttu-id="27574-149">Execute o Sysprep com a opção de generalize ativada.</span><span class="sxs-lookup"><span data-stu-id="27574-149">Please run Sysprep with the generalize option enabled.</span></span>