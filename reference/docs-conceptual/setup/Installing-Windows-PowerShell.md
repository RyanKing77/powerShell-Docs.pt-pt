---
ms.date: 2017-08-09
keywords: "PowerShell, cmdlet, transferir, instalar, a configuração, o windows 10, windows 8.1, windows 8.0, windows 7"
title: Instalar o Windows PowerShell
ms.openlocfilehash: 781bf50b6ac649e72bcdbb708555275fb7422d94
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/29/2017
---
# <a name="installing-windows-powershell"></a><span data-ttu-id="af84e-103">Instalar o Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="af84e-103">Installing Windows PowerShell</span></span>

<span data-ttu-id="af84e-104">PowerShell é instalado por predefinição em todos os Windows, começando com o Windows 7 SP1 e Windows Server 2008 R2 SP1.</span><span class="sxs-lookup"><span data-stu-id="af84e-104">PowerShell comes installed by default in every Windows, starting with Windows 7 SP1 and Windows Server 2008 R2 SP1.</span></span>

<span data-ttu-id="af84e-105">Utilizadores do Linux, macOS e Windows que pretenderem instalar **PowerShell 6** (beta), nos respetivos computadores, tem de:</span><span class="sxs-lookup"><span data-stu-id="af84e-105">Linux, macOS, and Windows users that would like to install **PowerShell 6** (beta), in their machines, need to:</span></span>

1. <span data-ttu-id="af84e-106">Obter o PowerShell para o SO e versão específica do [GitHub](https://github.com/powershell/powershell#get-powershell)</span><span class="sxs-lookup"><span data-stu-id="af84e-106">Get PowerShell for the specific OS and version, from [GitHub](https://github.com/powershell/powershell#get-powershell)</span></span>
1. <span data-ttu-id="af84e-107">Siga as instruções de instalação</span><span class="sxs-lookup"><span data-stu-id="af84e-107">Follow the installation instructions</span></span>
  - [<span data-ttu-id="af84e-108">Linux</span><span class="sxs-lookup"><span data-stu-id="af84e-108">Linux</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md)
  - [<span data-ttu-id="af84e-109">macOS</span><span class="sxs-lookup"><span data-stu-id="af84e-109">macOS</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#macos-1012)
  - [<span data-ttu-id="af84e-110">Windows</span><span class="sxs-lookup"><span data-stu-id="af84e-110">Windows</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/windows.md#msi)

<span data-ttu-id="af84e-111">PowerShell 6 também está disponível para Docker; consulte [instalação Docker](https://github.com/PowerShell/PowerShell/tree/master/docker) instruções.</span><span class="sxs-lookup"><span data-stu-id="af84e-111">PowerShell 6 is also available for Docker; see [Docker installation](https://github.com/PowerShell/PowerShell/tree/master/docker) instructions.</span></span>

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a><span data-ttu-id="af84e-112">Localizar o PowerShell no Windows 10, 8.1, 8.0 e 7</span><span class="sxs-lookup"><span data-stu-id="af84e-112">Finding PowerShell in Windows 10, 8.1, 8.0, and 7</span></span>

<span data-ttu-id="af84e-113">Por vezes, localizar PowerShell consola ou ISE (ambiente de Scripting integrado) no Windows pode ser difícil, como localização de move de uma versão do Windows para o seguinte.</span><span class="sxs-lookup"><span data-stu-id="af84e-113">Sometimes locating PowerShell console or ISE (Integrated Scripting Environment) in Windows can be difficult, as it's location moves from one version of Windows to the next.</span></span>

<span data-ttu-id="af84e-114">As tabelas seguintes deverão ajudar a encontrar PowerShell na sua versão do Windows.</span><span class="sxs-lookup"><span data-stu-id="af84e-114">The following tables should help you find PowerShell in your Windows version.</span></span>
<span data-ttu-id="af84e-115">Todas as versões listadas aqui tem a versão original, à lançadas com não existem atualizações.</span><span class="sxs-lookup"><span data-stu-id="af84e-115">All versions listed here are the original version, as released, with no updates.</span></span>

### <a name="for-console"></a><span data-ttu-id="af84e-116">Para a consola</span><span class="sxs-lookup"><span data-stu-id="af84e-116">For Console</span></span>

<span data-ttu-id="af84e-117">Versão</span><span class="sxs-lookup"><span data-stu-id="af84e-117">Version</span></span> | <span data-ttu-id="af84e-118">Localização</span><span class="sxs-lookup"><span data-stu-id="af84e-118">Location</span></span>
-- | --
<span data-ttu-id="af84e-119">10 do Windows</span><span class="sxs-lookup"><span data-stu-id="af84e-119">Windows 10</span></span> | <span data-ttu-id="af84e-120">Clique em ícone do Windows canto inferior esquerdo, comece a escrever o PowerShell</span><span class="sxs-lookup"><span data-stu-id="af84e-120">Click left lower corner Windows icon, start typing PowerShell</span></span>
<span data-ttu-id="af84e-121">Windows 8.1, 8.0</span><span class="sxs-lookup"><span data-stu-id="af84e-121">Windows 8.1, 8.0</span></span> | <span data-ttu-id="af84e-122">No ecrã Iniciar, comece a escrever o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="af84e-122">On the start screen, start typing PowerShell.</span></span><br/><span data-ttu-id="af84e-123">Se, no ambiente de trabalho, clique em ícone do Windows canto inferior esquerdo, comece a escrever o PowerShell</span><span class="sxs-lookup"><span data-stu-id="af84e-123">If on desktop, click left lower corner Windows icon, start typing PowerShell</span></span>
<span data-ttu-id="af84e-124">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="af84e-124">Windows 7 SP1</span></span> | <span data-ttu-id="af84e-125">Clique em esquerdo inferior canto ícone do Windows, no início de caixa de pesquisa escrevendo o PowerShell</span><span class="sxs-lookup"><span data-stu-id="af84e-125">Click left lower corner Windows icon, on the search box start typing PowerShell</span></span>

### <a name="for-ise"></a><span data-ttu-id="af84e-126">Para ISE</span><span class="sxs-lookup"><span data-stu-id="af84e-126">For ISE</span></span>

<span data-ttu-id="af84e-127">Versão</span><span class="sxs-lookup"><span data-stu-id="af84e-127">Version</span></span> | <span data-ttu-id="af84e-128">Localização</span><span class="sxs-lookup"><span data-stu-id="af84e-128">Location</span></span>
-- | --
<span data-ttu-id="af84e-129">10 do Windows</span><span class="sxs-lookup"><span data-stu-id="af84e-129">Windows 10</span></span> | <span data-ttu-id="af84e-130">Clique em ícone do Windows canto inferior esquerdo, comece a escrever ISE</span><span class="sxs-lookup"><span data-stu-id="af84e-130">Click left lower corner Windows icon, start typing ISE</span></span>
<span data-ttu-id="af84e-131">Windows 8.1, 8.0</span><span class="sxs-lookup"><span data-stu-id="af84e-131">Windows 8.1, 8.0</span></span> | <span data-ttu-id="af84e-132">No ecrã Iniciar, escreva **ISE do PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="af84e-132">On the start screen, type **PowerShell ISE**.</span></span><br/><span data-ttu-id="af84e-133">Se no ambiente de trabalho, clique em deixado ícone do Windows canto inferior, escreva **ISE do PowerShell**</span><span class="sxs-lookup"><span data-stu-id="af84e-133">If on desktop, click left lower corner Windows icon, type **PowerShell ISE**</span></span>
<span data-ttu-id="af84e-134">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="af84e-134">Windows 7 SP1</span></span> | <span data-ttu-id="af84e-135">Clique em esquerdo inferior canto ícone do Windows, no início de caixa de pesquisa escrevendo o PowerShell</span><span class="sxs-lookup"><span data-stu-id="af84e-135">Click left lower corner Windows icon, on the search box start typing PowerShell</span></span>

## <a name="finding-powershell-in-windows-server-versions"></a><span data-ttu-id="af84e-136">Localizar PowerShell em versões do Windows Server</span><span class="sxs-lookup"><span data-stu-id="af84e-136">Finding PowerShell in Windows Server versions</span></span>

<span data-ttu-id="af84e-137">A partir do Windows Server 2008 R2, sistema operativo Windows pode ser instalado sem a interface de utilizador gráfica (GUI).</span><span class="sxs-lookup"><span data-stu-id="af84e-137">Starting with Windows Server 2008 R2, Windows operating system can be installed without the graphical user interface (GUI).</span></span>
<span data-ttu-id="af84e-138">Edições do Windows Server sem GUI são denominadas **Core** edições e edições com a GUI são denominados **ambiente de trabalho**.</span><span class="sxs-lookup"><span data-stu-id="af84e-138">Editions of Windows Server without GUI are named **Core** editions, and editions with the GUI are named **Desktop**.</span></span>

### <a name="windows-server-core-editions"></a><span data-ttu-id="af84e-139">Edições do Windows Server Core</span><span class="sxs-lookup"><span data-stu-id="af84e-139">Windows Server Core editions</span></span>

<span data-ttu-id="af84e-140">Em todas as edições Core, quando iniciar sessão para o servidor de obter uma janela de linha de comandos do Windows.</span><span class="sxs-lookup"><span data-stu-id="af84e-140">In all Core editions, when you log to the server you get a Windows command prompt window.</span></span>

<span data-ttu-id="af84e-141">Tipo `powershell` e prima **ENTER** para iniciar o PowerShell dentro da sessão de linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="af84e-141">Type `powershell` and press **ENTER** to start PowerShell inside the command prompt session.</span></span> <span data-ttu-id="af84e-142">Tipo `exit` para terminar a sessão do PowerShell e regressar à linha de comandos.</span><span class="sxs-lookup"><span data-stu-id="af84e-142">Type `exit` to terminate the PowerShell session and return to command prompt.</span></span>

### <a name="windows-server-desktop-editions"></a><span data-ttu-id="af84e-143">Edições de ambiente de trabalho do Windows Server</span><span class="sxs-lookup"><span data-stu-id="af84e-143">Windows Server Desktop editions</span></span>

<span data-ttu-id="af84e-144">Todas as edições de ambiente de trabalho, clique no ícone de Windows canto inferior esquerdo, comece a escrever o PowerShell.</span><span class="sxs-lookup"><span data-stu-id="af84e-144">In all desktop editions, click the left lower corner Windows icon, start typing PowerShell.</span></span>
<span data-ttu-id="af84e-145">Obter a consola e opções de ISE.</span><span class="sxs-lookup"><span data-stu-id="af84e-145">You get both console and ISE options.</span></span>

<span data-ttu-id="af84e-146">A única exceção à regra acima é o ISE do Windows Server 2008 R2 SP1; Neste caso, clique no ícone de Windows canto inferior esquerdo, escreva o ISE do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="af84e-146">The only exception to the above rule is the ISE in Windows Server 2008 R2 SP1; in this case, click the left lower corner Windows icon, type PowerShell ISE.</span></span>

## <a name="how-to-check-the-version-of-powershell"></a><span data-ttu-id="af84e-147">Como verificar a versão do PowerShell</span><span class="sxs-lookup"><span data-stu-id="af84e-147">How to check the version of PowerShell</span></span>

<span data-ttu-id="af84e-148">Para localizar a versão do PowerShell que instalou o, inicie uma consola do PowerShell (ou o ISE) e o tipo `$PSVersionTable` e prima **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="af84e-148">To find which version of PowerShell you have installed, start a PowerShell console (or the ISE) and type `$PSVersionTable` and press **ENTER**.</span></span>

## <a name="upgrading-existing-windows-powershell"></a><span data-ttu-id="af84e-149">Atualizar existentes do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="af84e-149">Upgrading existing Windows PowerShell</span></span>

<span data-ttu-id="af84e-150">O pacote de instalação para o PowerShell ficar no interior de um programa de instalação do WMF.</span><span class="sxs-lookup"><span data-stu-id="af84e-150">The installation package for PowerShell comes inside a WMF installer.</span></span>
<span data-ttu-id="af84e-151">A versão do programa de instalação do WMF corresponde à versão do PowerShell; Não há nenhum instalador autónomo do Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="af84e-151">The version of the WMF installer matches the version of PowerShell; there's no stand alone installer for Windows PowerShell.</span></span>

<span data-ttu-id="af84e-152">Se precisar de atualizar a versão existente do PowerShell, no Windows, utilize a seguinte tabela para localizar o instalador para a versão do PowerShell que pretende atualizar para.</span><span class="sxs-lookup"><span data-stu-id="af84e-152">If you need to update your existing version of PowerShell, in Windows, use the following table to locate the installer for the version of PowerShell you want to update to.</span></span>

<span data-ttu-id="af84e-153">Windows</span><span class="sxs-lookup"><span data-stu-id="af84e-153">Windows</span></span> | <span data-ttu-id="af84e-154">PS 3.0</span><span class="sxs-lookup"><span data-stu-id="af84e-154">PS 3.0</span></span> | <span data-ttu-id="af84e-155">PS 4.0</span><span class="sxs-lookup"><span data-stu-id="af84e-155">PS 4.0</span></span> | <span data-ttu-id="af84e-156">PS 5.0</span><span class="sxs-lookup"><span data-stu-id="af84e-156">PS 5.0</span></span> | <span data-ttu-id="af84e-157">PS 5.1</span><span class="sxs-lookup"><span data-stu-id="af84e-157">PS 5.1</span></span> |
--|--|--|--|--|
<span data-ttu-id="af84e-158">Windows 10 (consulte Note1)</span><span class="sxs-lookup"><span data-stu-id="af84e-158">Windows 10 (see Note1)</span></span><br/><span data-ttu-id="af84e-159">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="af84e-159">Windows Server 2016</span></span> | - | - | - | <span data-ttu-id="af84e-160">instalado</span><span class="sxs-lookup"><span data-stu-id="af84e-160">installed</span></span>
<span data-ttu-id="af84e-161">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="af84e-161">Windows 8.1</span></span><br/><span data-ttu-id="af84e-162">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="af84e-162">Windows Server 2012 R2</span></span> | - | <span data-ttu-id="af84e-163">instalado</span><span class="sxs-lookup"><span data-stu-id="af84e-163">installed</span></span> | [<span data-ttu-id="af84e-164">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="af84e-164">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="af84e-165">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="af84e-165">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
<span data-ttu-id="af84e-166">Windows 8</span><span class="sxs-lookup"><span data-stu-id="af84e-166">Windows 8</span></span><br/><span data-ttu-id="af84e-167">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="af84e-167">Windows Server 2012</span></span> | <span data-ttu-id="af84e-168">instalado</span><span class="sxs-lookup"><span data-stu-id="af84e-168">installed</span></span> | [<span data-ttu-id="af84e-169">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="af84e-169">WMF 4.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [<span data-ttu-id="af84e-170">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="af84e-170">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="af84e-171">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="af84e-171">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
<span data-ttu-id="af84e-172">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="af84e-172">Windows 7 SP1</span></span><br/><span data-ttu-id="af84e-173">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="af84e-173">Windows Server 2008 R2 SP1</span></span> | [<span data-ttu-id="af84e-174">WMF 3.0</span><span class="sxs-lookup"><span data-stu-id="af84e-174">WMF 3.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [<span data-ttu-id="af84e-175">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="af84e-175">WMF 4.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [<span data-ttu-id="af84e-176">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="af84e-176">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="af84e-177">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="af84e-177">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)

> <span data-ttu-id="af84e-178">**Tenha em atenção 1**:</span><span class="sxs-lookup"><span data-stu-id="af84e-178">**Note 1**:</span></span>
  >>
  >> <span data-ttu-id="af84e-179">A edição inicial do Windows 10, com as atualizações automáticas ativada, PowerShell obtém atualizado da versão 5.0 para 5.1.</span><span class="sxs-lookup"><span data-stu-id="af84e-179">On the initial release of Windows 10, with automatic updates enabled, PowerShell gets updated from version 5.0 to 5.1.</span></span>
  >>
  >> <span data-ttu-id="af84e-180">Se a versão original do Windows 10 não for atualizada através de atualizações do Windows, a versão do PowerShell é 5.0.</span><span class="sxs-lookup"><span data-stu-id="af84e-180">If the original version of Windows 10 is not updated through Windows Updates, the version of PowerShell is 5.0.</span></span>

## <a name="need-azure-powershell"></a><span data-ttu-id="af84e-181">Precisa do Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="af84e-181">Need Azure PowerShell</span></span>

<span data-ttu-id="af84e-182">Se estiver à procura de **Azure PowerShell**, poderá começar pela [descrição geral do Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure).</span><span class="sxs-lookup"><span data-stu-id="af84e-182">If you're looking for **Azure PowerShell**, you could start with [Overview of Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure).</span></span>

<span data-ttu-id="af84e-183">Caso contrário, o que poderá ser necessário é [instalar e configurar o Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure/install-azurerm-ps)</span><span class="sxs-lookup"><span data-stu-id="af84e-183">Otherwise, what you might need is [Install and configure Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure/install-azurerm-ps)</span></span>

## <a name="see-also"></a><span data-ttu-id="af84e-184">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="af84e-184">See Also</span></span>

- [<span data-ttu-id="af84e-185">Requisitos de sistema do PowerShell do Windows</span><span class="sxs-lookup"><span data-stu-id="af84e-185">Windows PowerShell System Requirements</span></span>](Windows-PowerShell-System-Requirements.md)
- [<span data-ttu-id="af84e-186">A partir do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="af84e-186">Starting Windows PowerShell</span></span>](Starting-Windows-PowerShell.md)
