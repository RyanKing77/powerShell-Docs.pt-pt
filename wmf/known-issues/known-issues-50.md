---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Problemas conhecidos no WMF 5.0
ms.openlocfilehash: 91f556cb43ef971107f05c4041b725b1c7e4f1bd
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856358"
---
# <a name="known-issues-in-wmf-50"></a><span data-ttu-id="ced75-103">Problemas conhecidos no WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="ced75-103">Known Issues in WMF 5.0</span></span>

## <a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a><span data-ttu-id="ced75-104">Atalhos do PowerShell são perdidos quando utilizado pela primeira vez</span><span class="sxs-lookup"><span data-stu-id="ced75-104">PowerShell Shortcuts are broken when used for the first time</span></span>

<span data-ttu-id="ced75-105">**Resolução:** Execute uma das seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="ced75-105">**Resolution:** Perform one of the following actions:</span></span>

1. <span data-ttu-id="ced75-106">Clique com o botão direito do rato no atalho do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ced75-106">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="ced75-107">Selecione "Windows PowerShell" para iniciar num modo não elevados.</span><span class="sxs-lookup"><span data-stu-id="ced75-107">Select "Windows PowerShell" to launch in a non-elevated mode.</span></span>
2. <span data-ttu-id="ced75-108">Clique com o botão direito do rato no atalho do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ced75-108">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="ced75-109">Clique com o botão direito do rato em "Windows PowerShell" e selecione "Executar como administrador" iniciar num modo elevado.</span><span class="sxs-lookup"><span data-stu-id="ced75-109">Right click on "Windows PowerShell" and select "Run As Administrator" to launch in an elevated mode.</span></span>

<span data-ttu-id="ced75-110">Depois de ter realizado qualquer uma das ações acima, os atalhos do PowerShell irão funcionar.</span><span class="sxs-lookup"><span data-stu-id="ced75-110">Once you have performed either of the above actions, the PowerShell shortcuts will work.</span></span> <span data-ttu-id="ced75-111">Estas ações precisam ser executadas apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="ced75-111">These actions need to be performed only once.</span></span>

## <a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a><span data-ttu-id="ced75-112">Erros de relatório de módulos do PowerShell e recursos de DSC sobre ExecutionPolicy no Windows 7</span><span class="sxs-lookup"><span data-stu-id="ced75-112">PowerShell Modules and DSC Resources report errors about ExecutionPolicy on Windows 7</span></span>

<span data-ttu-id="ced75-113">No Windows 7, a utilização de módulos do PowerShell e recursos de DSC pode resultar em erros comunicados sobre ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="ced75-113">On Windows 7, using PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

<span data-ttu-id="ced75-114">**Resolução:** Definir o ExecutionPolicy **RemoteSigned** executando o seguinte comando numa sessão do PowerShell elevada (executar como administrador):</span><span class="sxs-lookup"><span data-stu-id="ced75-114">**Resolution:** Set the ExecutionPolicy to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

## <a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a><span data-ttu-id="ced75-115">Ligar a um ponto de extremidade Exchange antigo remoto faz com que uma falha</span><span class="sxs-lookup"><span data-stu-id="ced75-115">Connecting to an old remote Exchange endpoint causes a crash</span></span>

<span data-ttu-id="ced75-116">Redireciona o antigo ponto de extremidade do Exchange para um novo ponto final.</span><span class="sxs-lookup"><span data-stu-id="ced75-116">The old Exchange endpoint redirects to a new endpoint.</span></span> <span data-ttu-id="ced75-117">Há um bug na lógica de redirecionamento que resulte numa pane.</span><span class="sxs-lookup"><span data-stu-id="ced75-117">There is a bug in the redirection logic that results in a crash.</span></span>

<span data-ttu-id="ced75-118">**Resolução:** Ligue-se diretamente para o novo ponto final.</span><span class="sxs-lookup"><span data-stu-id="ced75-118">**Resolution:** Connect directly to the new endpoint.</span></span>

## <a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a><span data-ttu-id="ced75-119">Funcionalidade de registo de inventário de software está parada erroneamente após a instalação de WMF 5.0 no Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="ced75-119">Software Inventory Logging feature is erroneously stopped after WMF 5.0 installation on Windows Server 2012 R2</span></span>

<span data-ttu-id="ced75-120">Ao instalar o WMF 5.0 no Windows Server 2012 R2 que já está a executar o SIL, a funcionalidade registo de inventário de Software incorretamente é interrompida após a instalação.</span><span class="sxs-lookup"><span data-stu-id="ced75-120">When installing WMF 5.0 on a Windows Server 2012 R2 that is already running SIL, the Software Inventory Logging feature is erroneously stopped after installation.</span></span>

<span data-ttu-id="ced75-121">**Resolução:** Execute o `Start-SilLogging` cmdlet, uma vez após a instalação de WMF, como o processo de instalação incorretamente irá parar a funcionalidade registo de inventário de Software.</span><span class="sxs-lookup"><span data-stu-id="ced75-121">**Resolution:** Run the `Start-SilLogging` cmdlet once after the WMF installation, as the installation process will errantly stop the Software Inventory Logging feature.</span></span>

## <a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a><span data-ttu-id="ced75-122">`Get-ChildItem` não funciona se - LiteralPath e - Recurse são utilizados em conjunto</span><span class="sxs-lookup"><span data-stu-id="ced75-122">`Get-ChildItem` does not work if -LiteralPath and -Recurse are used together</span></span>

<span data-ttu-id="ced75-123">Se um nome de diretório contém um caráter de carateres universais inválido, em seguida, `Get-ChildItem` não produzirá os resultados esperados quando – LiteralPath tanto - Recurse são utilizados em conjunto.</span><span class="sxs-lookup"><span data-stu-id="ced75-123">If a directory name contains an invalid wildcard character, then `Get-ChildItem` will not produce expected results when both -LiteralPath and -Recurse are used together.</span></span>

<span data-ttu-id="ced75-124">**Resolução:** Solução não ideal, mas atual é implementar a recursão no script, em vez de contar com o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ced75-124">**Resolution:** Not ideal, but current workaround is to implement recursion in the script rather than rely on the cmdlet.</span></span>

## <a name="sysprep-fails-after-wmf-50-installation"></a><span data-ttu-id="ced75-125">Falha de Sysprep após a instalação de WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="ced75-125">Sysprep fails after WMF 5.0 installation</span></span>

<span data-ttu-id="ced75-126">Existem duas soluções alternativas para este problema, dependendo da versão do Windows Server que está a executar.</span><span class="sxs-lookup"><span data-stu-id="ced75-126">There are two workarounds for this issue depending on the version of Windows Server you are running.</span></span>

<span data-ttu-id="ced75-127">**Resolução:**</span><span class="sxs-lookup"><span data-stu-id="ced75-127">**Resolution:**</span></span>

- <span data-ttu-id="ced75-128">Para sistemas que executam **Windows Server 2008 R2**</span><span class="sxs-lookup"><span data-stu-id="ced75-128">For systems running **Windows Server 2008 R2**</span></span>
  1. <span data-ttu-id="ced75-129">Abra PowerShell como administrador</span><span class="sxs-lookup"><span data-stu-id="ced75-129">Open PowerShell as an administrator</span></span>
  2. <span data-ttu-id="ced75-130">Execute o seguinte comando</span><span class="sxs-lookup"><span data-stu-id="ced75-130">Run the following command</span></span>

     ```powershell
     Set-SilLogging -TargetUri https://BlankTarget -CertificateThumbprint 0123456789
     ```

  3. <span data-ttu-id="ced75-131">Execute o comando e ignorar o erro, como eles são esperados.</span><span class="sxs-lookup"><span data-stu-id="ced75-131">Run the command and ignore the error, as they are expected.</span></span>

     ```powershell
     Publish-SilData
     ```

  4. <span data-ttu-id="ced75-132">Eliminar os ficheiros no diretório de \Windows\System32\Logfiles\SIL\\</span><span class="sxs-lookup"><span data-stu-id="ced75-132">Delete the files in  \Windows\System32\Logfiles\SIL\ directory</span></span>

     ```powershell
     Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
     ```

  5. <span data-ttu-id="ced75-133">Instale todas as atualizações Windows importante disponíveis e iniciar a operação de Sysyprep normalmente.</span><span class="sxs-lookup"><span data-stu-id="ced75-133">Install all available important Windows Updates, and begin Sysyprep operation normally.</span></span>

- <span data-ttu-id="ced75-134">Para sistemas que executam **Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="ced75-134">For systems running **Windows Server 2012**</span></span>
  1. <span data-ttu-id="ced75-135">Depois de instalar o WMF 5.0 no servidor para ser Sysprep d', inicie sessão como administrador.</span><span class="sxs-lookup"><span data-stu-id="ced75-135">After installing WMF 5.0 on the server to be Sysprep'd, login as administrator.</span></span>
  2. <span data-ttu-id="ced75-136">Copie Generize.xml do diretório `\Windows\System32\Sysprep\ActionFiles\` para uma localização fora do diretório do Windows, `C:\` por exemplo.</span><span class="sxs-lookup"><span data-stu-id="ced75-136">Copy Generize.xml from directory `\Windows\System32\Sysprep\ActionFiles\` to a location outside of the Windows directory, `C:\` for example.</span></span>
  3. <span data-ttu-id="ced75-137">Abra a sua cópia Generalize.xml com o bloco de notas.</span><span class="sxs-lookup"><span data-stu-id="ced75-137">Open your Generalize.xml copy with notepad.</span></span>
  4. <span data-ttu-id="ced75-138">Localizar e remover o texto a seguir, uma instância de cada tem de ser eliminado (estará próximo do final do documento).</span><span class="sxs-lookup"><span data-stu-id="ced75-138">Find and remove the following text, one instance of each needs to be deleted (they will be near the end of the document).</span></span>

     ```xml
     <sysprepOrder order="0x3200"></sysprepOrder>
     <sysprepOrder order="0x3300"></sysprepOrder>
     ```

  5. <span data-ttu-id="ced75-139">Guardar a cópia editada de Generalize.xml e feche o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="ced75-139">Save the edited copy of Generalize.xml and close the file.</span></span>
  6. <span data-ttu-id="ced75-140">Abra uma linha de comandos como administrador</span><span class="sxs-lookup"><span data-stu-id="ced75-140">Open a command prompt as administrator</span></span>
  7. <span data-ttu-id="ced75-141">Execute o seguinte comando para obter a propriedade do ficheiro Generalize.xml na pasta system32:</span><span class="sxs-lookup"><span data-stu-id="ced75-141">Run the following command to take ownership of the Generalize.xml file in system32 folder:</span></span>

     ```powershell
     Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

  8. <span data-ttu-id="ced75-142">Execute o seguinte comando para definir as permissões adequadas no ficheiro:</span><span class="sxs-lookup"><span data-stu-id="ced75-142">Run the following command to set appropriate permission on the file:</span></span>

     ```powershell
     Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
     ```

     - <span data-ttu-id="ced75-143">Responda Sim no prompt de confirmação.</span><span class="sxs-lookup"><span data-stu-id="ced75-143">Answer Yes at the prompt for confirmation.</span></span>
     - <span data-ttu-id="ced75-144">Tenha em atenção que `<AdministratorUserName>` deve ser substituído pelo nome de usuário que seja administrador no computador.</span><span class="sxs-lookup"><span data-stu-id="ced75-144">Note that `<AdministratorUserName>` should be replaced by the username who is administrator on the machine.</span></span> <span data-ttu-id="ced75-145">Por exemplo, "Administrador".</span><span class="sxs-lookup"><span data-stu-id="ced75-145">For example, "Administrator".</span></span>

  9. <span data-ttu-id="ced75-146">Copie o ficheiro editado e guardado ao longo para o diretório de Sysprep utilizando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="ced75-146">Copy the file you edited and saved over to the Sysprep directory using the following command:</span></span>

     ```powershell
     xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

     - <span data-ttu-id="ced75-147">Responder Yes para substituir (Observe que se não houver nenhuma linha de comandos para substituir, volte a verificar o caminho que introduziu).</span><span class="sxs-lookup"><span data-stu-id="ced75-147">Answer Yes to overwrite (note that if there is no prompt to overwrite, double check the path entered).</span></span>
     - <span data-ttu-id="ced75-148">Assume a que sua cópia editada do Generalize.xml foi copiada para C:\.</span><span class="sxs-lookup"><span data-stu-id="ced75-148">Assumes your edited copy of Generalize.xml was copied to C:\ .</span></span>

  10. <span data-ttu-id="ced75-149">Generalize.xml está agora atualizada com a solução alternativa.</span><span class="sxs-lookup"><span data-stu-id="ced75-149">Generalize.xml is now updated with the workaround.</span></span> <span data-ttu-id="ced75-150">Execute o Sysprep com a opção de generalize ativada.</span><span class="sxs-lookup"><span data-stu-id="ced75-150">Please run Sysprep with the generalize option enabled.</span></span>