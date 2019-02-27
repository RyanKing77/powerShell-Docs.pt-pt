---
title: Modificar o caminho de instalação PSModulePath | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846509"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="14f4d-102">Modifying the PSModulePath Installation Path (Modificar o Caminho de Instalação PSModulePath)</span><span class="sxs-lookup"><span data-stu-id="14f4d-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="14f4d-103">O `PSModulePath` variável de ambiente armazena os caminhos para os locais dos módulos que estão instalados no disco.</span><span class="sxs-lookup"><span data-stu-id="14f4d-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="14f4d-104">Windows PowerShell utiliza esta variável para localizar os módulos quando o utilizador não especifica o caminho completo para um módulo.</span><span class="sxs-lookup"><span data-stu-id="14f4d-104">Windows PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="14f4d-105">Os caminhos nesta variável serão pesquisados na ordem em que aparecem.</span><span class="sxs-lookup"><span data-stu-id="14f4d-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="14f4d-106">Quando o Windows PowerShell é iniciado, `PSModulePath` é criada como uma variável de ambiente de sistema com o seguinte valor predefinido: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="14f4d-106">When Windows PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="14f4d-107">Para ver a variável PSModulePath</span><span class="sxs-lookup"><span data-stu-id="14f4d-107">To view the PSModulePath variable</span></span>

<span data-ttu-id="14f4d-108">Para ver os caminhos especificados no `PSModulePath` variável, escreva o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="14f4d-108">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="14f4d-109">Para adicionar localizações à variável PSModulePath</span><span class="sxs-lookup"><span data-stu-id="14f4d-109">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="14f4d-110">Para adicionar caminhos para esta variável, utilize um dos seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="14f4d-110">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="14f4d-111">Para adicionar um valor temporário que está disponível apenas para a sessão atual, execute o seguinte comando na linha de comandos:</span><span class="sxs-lookup"><span data-stu-id="14f4d-111">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- <span data-ttu-id="14f4d-112">Para adicionar um valor persistente que está disponível sempre que abrir uma sessão, adicione o seguinte comando para um perfil do Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="14f4d-112">To add a persistent value that is available whenever a session is opened, add the following command to a Windows PowerShell profile:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  <span data-ttu-id="14f4d-113">Para obter mais informações sobre os perfis, consulte [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) na biblioteca do Microsoft TechNet.</span><span class="sxs-lookup"><span data-stu-id="14f4d-113">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) in the Microsoft TechNet library.</span></span>

- <span data-ttu-id="14f4d-114">Para adicionar uma variável persistente para o registo, crie uma nova variável de ambiente de usuário chamada `PSModulePath` usando o Editor de variáveis de ambiente no **propriedades do sistema** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="14f4d-114">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="14f4d-115">Para adicionar uma variável persistente usando um script, utilize o **SetEnvironmentVariable** método na classe de ambiente.</span><span class="sxs-lookup"><span data-stu-id="14f4d-115">To add a persistent variable by using a script, use the **SetEnvironmentVariable** method on the Environment class.</span></span> <span data-ttu-id="14f4d-116">Por exemplo, o script seguinte adiciona "C:\Program Files\Fabrikam\Module caminho para o valor da variável de ambiente PSModulePath para o computador.</span><span class="sxs-lookup"><span data-stu-id="14f4d-116">For example, the following script adds the "C:\Program Files\Fabrikam\Module path to the value of the PSModulePath environment variable for the computer.</span></span> <span data-ttu-id="14f4d-117">Para adicionar o caminho para a variável de ambiente de PSModulePath do utilizador, defina o destino como "Utilizador".</span><span class="sxs-lookup"><span data-stu-id="14f4d-117">To add the path to the user PSModulePath environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="14f4d-118">Para remover o PSModulePath a localizações</span><span class="sxs-lookup"><span data-stu-id="14f4d-118">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="14f4d-119">Pode remover caminhos da variável usando métodos semelhantes: por exemplo, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` removerá o **c:\ModulePath** caminho da sessão atual.</span><span class="sxs-lookup"><span data-stu-id="14f4d-119">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="14f4d-120">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="14f4d-120">See Also</span></span>

[<span data-ttu-id="14f4d-121">Escrever um módulo do Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="14f4d-121">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
