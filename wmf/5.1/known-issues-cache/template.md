---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.topic: conceptual
title: modelo de exemplo de um writeup conhecido de problema ou limitação
ms.openlocfilehash: 8c1004e16f78913174af2e519e451f6fd9f30ff7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055552"
---
 >Nota: fornecer um título descritivo proposto e uma breve descrição

## <a name="example-erroneous-executionpolicy-errors"></a>Exemplo: Erros de ExecutionPolicy errados
No Windows 7, a utilização de módulos do PowerShell e recursos de DSC pode resultar em erros comunicados sobre ExecutionPolicy.

### <a name="resolution"></a>Resolução

Para resolver, definir o **ExecutionPolicy** ao **RemoteSigned** executando o seguinte comando numa sessão do PowerShell elevada (executar como administrador):

```powershell
Set-ExecutionPolicy RemoteSigned
```
