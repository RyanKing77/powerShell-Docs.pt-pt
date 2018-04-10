---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: cmdlet do powershell do galeria, psget
title: Unregister-PSRepository
ms.openlocfilehash: 7847e223ae7edd9ec2417d104e5e8130f92a59cf
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="unregister-psrepository"></a>Unregister-PSRepository

Anula o registo de um repositório.

## <a name="description"></a>Descrição

O cmdlet Unregister-PSRepository anula o registo de um repositório para o utilizador atual.
- Anulação do registo e re-registo do repositório PSGallery é permitido para uma empresa e desligado cenários.
- Os utilizadores podem voltar a registar o PSGallery executando simplesmente `Register-PSRepository -Default`
- Uma vez que PSGallery é a predefinição publicar repositório nos cmdlets do módulo de publicar e publicar Script, será emitido um erro se PSGallery não está disponível na lista de repositório registado.

## <a name="cmdlet-syntax"></a>Sintaxe de cmdlet

```powershell
Get-Command -Name Unregister-PSRepository -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a>Referência de ajuda online do cmdlet

[Unregister-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517130)

## <a name="example-commands"></a>Comandos de exemplo

```powershell
Unregister-PSRepository -Name "MyPrivateGallery"

Get-PSRepository exp | Unregister-PSRepository
```

### <a name="unregistration-and-re-registration-of-the-psgallery-repository-is-allowed-for-an-enterprise-and-disconnected-scenarios"></a>Anulação do registo e re-registo do repositório PSGallery é permitido para uma empresa e desligado cenários.
```powershell

# Unregister PSGallery repository
Unregister-PSRepository PSGallery

# Publish-Module throws an error when PSGallery is not a registered repository
Publish-Module -Name MyModule
publish-module : Unable to find repository 'PSGallery'. Use Get-PSRepository to see all available repositories. Try again after specifying a valid repository name. You can use 'Register-PSRepository -Default' to register the PSGallery repository.
At line:1 char:1
+ publish-module -name mymodule
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (PSGallery:String) [Publish-Module], ArgumentException
    + FullyQualifiedErrorId : PSGalleryNotFound,Publish-Module

# Re-register PSGallery repository
Register-PSRepository -Default
```