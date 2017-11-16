---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, o powershell, o programa de configuração"
title: "modelo de exemplo de uma escrita do problema ou limitação conhecida"
ms.openlocfilehash: b93393b2c84e76a301e6406d1388e82e95a2959c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/12/2017
---
>Nota: forneça um título descritivo proposto e uma breve descrição

## <a name="example-erroneous-executionpolicy-errors"></a>Exemplo: Erros de ExecutionPolicy errada ##
No Windows 7, a utilização de módulos do PowerShell e recursos de DSC poderá resultar em erros comunicados sobre ExecutionPolicy.

### <a name="resolution"></a>Resolução

Para resolver, defina o **ExecutionPolicy** para **RemoteSigned** executando o seguinte comando numa sessão do PowerShell elevada (executar como administrador):

```powershell
Set-ExecutionPolicy RemoteSigned
```

