---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.topic: conceptual
title: modelo de exemplo de uma escrita do problema ou limitação conhecida
ms.openlocfilehash: 453d4e40b906ebcab7314f04e138ded271338846
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221940"
---
>Nota: forneça um título descritivo proposto e uma breve descrição

## <a name="example-erroneous-executionpolicy-errors"></a>Exemplo: Erros de ExecutionPolicy errada ##
No Windows 7, a utilização de módulos do PowerShell e recursos de DSC poderá resultar em erros comunicados sobre ExecutionPolicy.

### <a name="resolution"></a>Resolução

Para resolver, defina o **ExecutionPolicy** para **RemoteSigned** executando o seguinte comando numa sessão do PowerShell elevada (executar como administrador):

```powershell
Set-ExecutionPolicy RemoteSigned
```
