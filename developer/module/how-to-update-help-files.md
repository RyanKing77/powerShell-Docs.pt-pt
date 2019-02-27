---
title: Como atualizar os arquivos de ajuda | Documentos da Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495869a6-080e-4401-9ddc-16edd2f86857
caps.latest.revision: 6
ms.openlocfilehash: 2c1fbd70aab1f65f33ea206b7ab1e2bd3dfd8c7a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846481"
---
# <a name="how-to-update-help-files"></a>How to Update Help Files (Como Atualizar Ficheiros de Ajuda)

Este tópico explica como atualizar os arquivos de ajuda para um módulo que oferece suporte a ajuda Atualizável.

## <a name="updating-help-files"></a>A atualizar os arquivos de ajuda

Existem muitas razões para atualizar os arquivos de ajuda, como corrigir erros, esclarecendo um conceito, responder uma pergunta de perguntas mais frequentes, adicionando novos ficheiros ou adicionar novos e melhores exemplos.

Para atualizar um arquivo de ajuda:

1. Altere os arquivos.

2. Traduza os ficheiros em outras culturas de interface do Usuário.

3. Recolha todos os arquivos de ajuda (nova, alterados e inalterados) para o módulo de cada cultura da interface do Usuário.

4. Valide os ficheiros no esquema de XML.

5. Recompile os arquivos CAB para cada cultura da interface do Usuário.

6. No ficheiro XML de HelpInfo, incremente os números de versão do ficheiro CAB para cada cultura da interface do Usuário.

7. Carregar os novos ficheiros CAB para o local especificado pelo valor de **HelpContentUri** elemento no arquivo XML de HelpInfo. Substitua os arquivos CAB mais antigos por novos ficheiros CAB.

8. Carregar o ficheiro XML de HelpInfo atualizado para a localização especificada pelos **HelpInfoUri** chave no manifesto do módulo. Substitua o ficheiro de HelpInfo XML mais antigo com o novo ficheiro.