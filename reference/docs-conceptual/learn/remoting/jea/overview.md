---
ms.date: 07/10/2019
keywords: Jea, PowerShell, segurança
title: Visão geral da administração apenas suficiente
ms.openlocfilehash: 4b74e5be9558810748a8844a325c8213e1b3ebc9
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017861"
---
# <a name="just-enough-administration"></a><span data-ttu-id="87fbf-103">Administração Apenas Suficiente</span><span class="sxs-lookup"><span data-stu-id="87fbf-103">Just Enough Administration</span></span>

<span data-ttu-id="87fbf-104">A JEA (administração suficiente) é uma tecnologia de segurança que permite a administração delegada para qualquer coisa gerenciada pelo PowerShell.</span><span class="sxs-lookup"><span data-stu-id="87fbf-104">Just Enough Administration (JEA) is a security technology that enables delegated administration for anything managed by PowerShell.</span></span> <span data-ttu-id="87fbf-105">Com o JEA, você pode:</span><span class="sxs-lookup"><span data-stu-id="87fbf-105">With JEA, you can:</span></span>

- <span data-ttu-id="87fbf-106">**Reduza o número de administradores em seus computadores** usando contas virtuais ou contas de serviço gerenciadas por grupo para executar ações privilegiadas em nome de usuários regulares.</span><span class="sxs-lookup"><span data-stu-id="87fbf-106">**Reduce the number of administrators on your machines** using virtual accounts or group-managed service accounts to perform privileged actions on behalf of regular users.</span></span>
- <span data-ttu-id="87fbf-107">**Limite o que os usuários podem fazer** especificando quais cmdlets, funções e comandos externos eles podem executar.</span><span class="sxs-lookup"><span data-stu-id="87fbf-107">**Limit what users can do** by specifying which cmdlets, functions, and external commands they can run.</span></span>
- <span data-ttu-id="87fbf-108">**Entenda melhor o que os usuários estão fazendo** com transcrições e logs que mostram exatamente quais comandos um usuário executou durante sua sessão.</span><span class="sxs-lookup"><span data-stu-id="87fbf-108">**Better understand what your users are doing** with transcripts and logs that show you exactly which commands a user executed during their session.</span></span>

<span data-ttu-id="87fbf-109">**Por que o JEA é importante?**</span><span class="sxs-lookup"><span data-stu-id="87fbf-109">**Why is JEA important?**</span></span>

<span data-ttu-id="87fbf-110">Contas altamente privilegiadas usadas para administrar seus servidores apresentam um sério risco de segurança.</span><span class="sxs-lookup"><span data-stu-id="87fbf-110">Highly privileged accounts used to administer your servers pose a serious security risk.</span></span> <span data-ttu-id="87fbf-111">Caso um invasor comprometa uma dessas contas, ele poderia iniciar [ataques laterais](https://aka.ms/pth) em toda a sua organização.</span><span class="sxs-lookup"><span data-stu-id="87fbf-111">Should an attacker compromise one of these accounts, they could launch [lateral attacks](https://aka.ms/pth) across your organization.</span></span> <span data-ttu-id="87fbf-112">Cada conta comprometida dá a um invasor acesso a ainda mais contas e recursos e os coloca um passo mais próximo de roubar os segredos da empresa, lançar um ataque de negação de serviço e muito mais.</span><span class="sxs-lookup"><span data-stu-id="87fbf-112">Each compromised account gives an attacker access to even more accounts and resources, and puts them one step closer to stealing company secrets, launching a denial-of-service attack, and more.</span></span>

<span data-ttu-id="87fbf-113">Nem sempre é fácil remover privilégios administrativos.</span><span class="sxs-lookup"><span data-stu-id="87fbf-113">It's not always easy to remove administrative privileges, either.</span></span> <span data-ttu-id="87fbf-114">Considere o cenário comum em que a função DNS está instalada no mesmo computador que o controlador de Domínio do Active Directory.</span><span class="sxs-lookup"><span data-stu-id="87fbf-114">Consider the common scenario where the DNS role is installed on the same machine as your Active Directory Domain Controller.</span></span> <span data-ttu-id="87fbf-115">Os administradores de DNS exigem privilégios de administrador local para corrigir problemas com o servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="87fbf-115">Your DNS administrators require local administrator privileges to fix issues with the DNS server.</span></span> <span data-ttu-id="87fbf-116">Mas, para fazer isso, você deve torná-los membros do grupo de segurança **Administradores de domínio** altamente privilegiados.</span><span class="sxs-lookup"><span data-stu-id="87fbf-116">But to do so, you must make them members of the highly privileged **Domain Admins** security group.</span></span> <span data-ttu-id="87fbf-117">Essa abordagem efetivamente fornece aos administradores de DNS o controle sobre todo o domínio e o acesso a todos os recursos nesse computador.</span><span class="sxs-lookup"><span data-stu-id="87fbf-117">This approach effectively gives DNS Administrators control over your whole domain and access to all resources on that machine.</span></span>

<span data-ttu-id="87fbf-118">JEA resolve esse problema por meio do princípio de **privilégios mínimos**.</span><span class="sxs-lookup"><span data-stu-id="87fbf-118">JEA addresses this problem through the principle of **Least Privilege**.</span></span> <span data-ttu-id="87fbf-119">Com o JEA, você pode configurar um ponto de extremidade de gerenciamento para administradores de DNS que concede acesso apenas aos comandos do PowerShell que eles precisam para realizar seu trabalho.</span><span class="sxs-lookup"><span data-stu-id="87fbf-119">With JEA, you can configure a management endpoint for DNS administrators that gives them access only to the PowerShell commands they need to get their job done.</span></span> <span data-ttu-id="87fbf-120">Isso significa que você pode fornecer o acesso apropriado para reparar um cache DNS inviabilizada ou reiniciar o servidor DNS sem conceder a eles direitos de Active Directory, ou procurar o sistema de arquivos, ou executar scripts potencialmente perigosos.</span><span class="sxs-lookup"><span data-stu-id="87fbf-120">This means you can provide the appropriate access to repair a poisoned DNS cache or restart the DNS server without unintentionally giving them rights to Active Directory, or to browse the file system, or run potentially dangerous scripts.</span></span> <span data-ttu-id="87fbf-121">Melhor ainda, quando a sessão JEA é configurada para usar contas virtuais com privilégios temporários, os administradores de DNS podem se conectar ao servidor usando credenciais **não administrativas** e ainda executar comandos que normalmente exigem privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="87fbf-121">Better yet, when the JEA session is configured to use temporary privileged virtual accounts, your DNS administrators can connect to the server using **non-admin** credentials and still run commands that typically require admin privileges.</span></span> <span data-ttu-id="87fbf-122">O JEA permite que você remova usuários de funções de administrador de domínio/local com privilégios elevados e controle cuidadosamente o que eles podem fazer em cada computador.</span><span class="sxs-lookup"><span data-stu-id="87fbf-122">JEA enables you to remove users from widely privileged local/domain administrator roles and carefully control what they can do on each machine.</span></span>

## <a name="next-steps"></a><span data-ttu-id="87fbf-123">Passos Seguintes</span><span class="sxs-lookup"><span data-stu-id="87fbf-123">Next steps</span></span>

<span data-ttu-id="87fbf-124">Para saber mais sobre os requisitos para usar o JEA, consulte o artigo [pré-requisitos](prerequisites.md) .</span><span class="sxs-lookup"><span data-stu-id="87fbf-124">To learn more about the requirements to use JEA, see the [Prerequisites](prerequisites.md) article.</span></span>

## <a name="samples-and-dsc-resource"></a><span data-ttu-id="87fbf-125">Exemplos e recurso de DSC</span><span class="sxs-lookup"><span data-stu-id="87fbf-125">Samples and DSC resource</span></span>

<span data-ttu-id="87fbf-126">As configurações de JEA de exemplo e o recurso de DSC JEA podem ser encontrados no [repositório GitHub do Jea](https://github.com/PowerShell/JEA).</span><span class="sxs-lookup"><span data-stu-id="87fbf-126">Sample JEA configurations and the JEA DSC resource can be found in the [JEA GitHub repository](https://github.com/PowerShell/JEA).</span></span>