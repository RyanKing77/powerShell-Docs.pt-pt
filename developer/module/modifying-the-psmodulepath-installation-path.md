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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082214"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>Modifying the PSModulePath Installation Path (Modificar o Caminho de Instalação PSModulePath)

O `PSModulePath` variável de ambiente armazena os caminhos para os locais dos módulos que estão instalados no disco. Windows PowerShell utiliza esta variável para localizar os módulos quando o utilizador não especifica o caminho completo para um módulo. Os caminhos nesta variável serão pesquisados na ordem em que aparecem.

Quando o Windows PowerShell é iniciado, `PSModulePath` é criada como uma variável de ambiente de sistema com o seguinte valor predefinido: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.

## <a name="to-view-the-psmodulepath-variable"></a>Para ver a variável PSModulePath

Para ver os caminhos especificados no `PSModulePath` variável, escreva o seguinte comando:

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>Para adicionar localizações à variável PSModulePath

Para adicionar caminhos para esta variável, utilize um dos seguintes métodos:

- Para adicionar um valor temporário que está disponível apenas para a sessão atual, execute o seguinte comando na linha de comandos:

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- Para adicionar um valor persistente que está disponível sempre que abrir uma sessão, adicione o seguinte comando para um perfil do Windows PowerShell:

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  Para obter mais informações sobre os perfis, consulte [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) na biblioteca do Microsoft TechNet.

- Para adicionar uma variável persistente para o registo, crie uma nova variável de ambiente de usuário chamada `PSModulePath` usando o Editor de variáveis de ambiente no **propriedades do sistema** caixa de diálogo.

- Para adicionar uma variável persistente usando um script, utilize o **SetEnvironmentVariable** método na classe de ambiente. Por exemplo, o script seguinte adiciona "C:\Program Files\Fabrikam\Module caminho para o valor da variável de ambiente PSModulePath para o computador. Para adicionar o caminho para a variável de ambiente de PSModulePath do utilizador, defina o destino como "Utilizador".

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a>Para remover o PSModulePath a localizações

Pode remover caminhos da variável usando métodos semelhantes: por exemplo, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` removerá o **c:\ModulePath** caminho da sessão atual.

## <a name="see-also"></a>Veja Também

[Escrever um módulo do Windows PowerShell](./writing-a-windows-powershell-module.md)
