---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.topic: conceptual
title: modelo de exemplo de um writeup conhecido de problema ou limitação
ms.openlocfilehash: ed7ae3de392c8902917e5b98fd4fc9d5138ccaed
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688680"
---
>Nota: fornecer um título descritivo proposto e uma breve descrição

## <a name="example-erroneous-executionpolicy-errors"></a>Exemplo: Erros de ExecutionPolicy errados ##
No Windows 7, a utilização de módulos do PowerShell e recursos de DSC pode resultar em erros comunicados sobre ExecutionPolicy.

### <a name="resolution"></a>Resolução

Para resolver, definir o **ExecutionPolicy** ao **RemoteSigned** executando o seguinte comando numa sessão do PowerShell elevada (executar como administrador):

```powershell
Set-ExecutionPolicy RemoteSigned
```
