---
title: Parâmetros de atividades | Documentos da Microsoft
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e4e0cf6-19e0-44b8-8b40-d6f6075276cf
caps.latest.revision: 5
ms.openlocfilehash: 489d8bcdabe904d6a3d2bc6cdb9d7e23d09cbef2
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251222"
---
# <a name="activity-parameters"></a>Parâmetros de Atividades

A tabela seguinte lista os nomes recomendados e a funcionalidade para parâmetros de atividades.

|Parâmetro|Funcionalidade|
|---|---|
|**Acrescentar**<br>Tipo de dados: SwitchParameter|Implemente este parâmetro para que o utilizador pode adicionar conteúdo ao final de um recurso quando o parâmetro for especificado.|
|**CaseSensitive**<br>Tipo de dados: SwitchParameter|Implemente este parâmetro para que o utilizador pode exigir a maiúsculas e minúsculas, quando o parâmetro for especificado.|
|**Comando**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar uma cadeia de caracteres de comando para executar.|
|**CompatibleVersion**<br>Tipo de dados: Objeto de ter|Implemente este parâmetro para que o utilizador pode especificar a semântica que o cmdlet tem de ser compatível com para compatibilidade com versões anteriores.|
|**comprimir**<br>Tipo de dados: SwitchParameter|Implemente este parâmetro para que a compressão de dados é utilizada quando o parâmetro for especificado.|
|**comprimir**<br>Tipo de dados: Palavra-chave|Implemente este parâmetro para que o utilizador pode especificar o algoritmo a utilizar para compressão de dados.|
|**Contínua**<br>Tipo de dados: SwitchParameter|Implemente este parâmetro, de modo a que os dados são processados até que o usuário termina o cmdlet quando o parâmetro for especificado. Se o parâmetro não for especificado, o cmdlet processa uma quantidade predefinida de dados e, em seguida, termina a operação.|
|**Criar**<br>Tipo de dados: SwitchParameter|Implemente este parâmetro para indicar que um recurso é criado se ainda não existir quando é especificado o parâmetro.|
|**Eliminar**<br>Tipo de dados: SwitchParameter|Implemente este parâmetro, de modo a que os recursos são eliminados quando o cmdlet concluiu sua operação quando o parâmetro for especificado.|
|**Drenar**<br>Tipo de dados: SwitchParameter|Implemente este parâmetro para indicar que os itens de trabalho pendentes são processados antes do cmdlet processa novos dados, quando o parâmetro for especificado. Se o parâmetro não for especificado, os itens de trabalho são processados imediatamente.|
|**Erase**<br>Tipo de dados: Int32|Implemente este parâmetro para que o utilizador pode especificar o número de vezes que um recurso é apagado antes de ser eliminado.|
|**ErrorLevel**<br>Tipo de dados: Int32|Implemente este parâmetro para que o utilizador pode especificar o nível de erros ao relatório.|
|**Excluir**<br>Tipo de dados: String[]|Implemente este parâmetro para que o usuário pode excluir algo de uma atividade. Para obter mais informações sobre como utilizar filtros de entrada, consulte [parâmetros de filtro de entrada](input-filter-parameters.md).|
|**Filtro**<br>Tipo de dados: Palavra-chave|Implemente este parâmetro para que o utilizador pode especificar um filtro que seleciona os recursos no qual executar a ação de cmdlet. Para obter mais informações sobre como utilizar filtros de entrada, consulte [parâmetros de filtro de entrada](./input-filter-parameters.md).|
|**Siga**<br>Tipo de dados: SwitchParameter|Implemente este parâmetro, de modo a que o progresso é controlado quando o parâmetro for especificado.|
|**Force**<br>Tipo de dados: SwitchParameter|Implemente este parâmetro para indicar que o usuário pode executar uma ação, mesmo que restrições são encontradas quando o parâmetro for especificado. O parâmetro não permite a segurança ser comprometido. Por exemplo, este parâmetro permite que um utilizador substituir um ficheiro só de leitura.|
|**Incluir**<br>Tipo de dados: String[]|Implemente este parâmetro para que o utilizador pode incluir algo numa atividade. Para obter mais informações sobre como utilizar filtros de entrada, consulte [parâmetros de filtro de entrada](input-filter-parameters.md).|
|**Incremental**<br>Tipo de dados: SwitchParameter|Implemente este parâmetro para indicar que o processamento é efetuado incrementalmente quando o parâmetro for especificado. Por exemplo, este parâmetro permite que um utilizador efetuar cópias de segurança incrementais de que fazer backup de arquivos apenas desde a última cópia de segurança.|
|**InputObject**<br>Tipo de dados: Objeto|Implemente este parâmetro quando o cmdlet pega a entrada de outros cmdlets. Quando define um **InputObject** parâmetro, sempre especificar a **ValueFromPipeline** palavra-chave quando declara o **parâmetro** atributo. Para obter mais informações sobre como utilizar filtros de entrada, consulte [parâmetros de filtro de entrada](./input-filter-parameters.md).|
|**Inserir**<br>Tipo de dados: SwitchParameter|Implemente este parâmetro para que o cmdlet insere um item quando o parâmetro for especificado.|
|**Interativo**<br>Tipo de dados: SwitchParameter|Implemente este parâmetro para que o cmdlet interativamente funciona com o utilizador de quando o parâmetro for especificado.|
|**intervalo**<br>Tipo de dados: HashTable|Implemente este parâmetro para que o utilizador pode especificar uma tabela de hash de palavras-chave que contém os valores. O exemplo seguinte mostra os valores de exemplo para o **intervalo** parâmetro: `-interval @{ResumeScan=15; Retry=3}`.|
|**registo**<br>Tipo de dados: SwitchParameter|Implemente esta auditoria de parâmetro as ações do cmdlet, quando o parâmetro for especificado.|
|**NoClobber**<br>Tipo de dados: SwitchParameter|Implemente este parâmetro para que o recurso não será substituído quando o parâmetro for especificado. Este parâmetro aplica-se geralmente aos cmdlets de criar novos objetos para que eles podem ser impedidos de substituição de objetos existentes com o mesmo nome.|
|**Notificar**<br>Tipo de dados: SwitchParameter|Implemente este parâmetro para que o utilizador será notificado que a atividade foi concluída quando o parâmetro for especificado.|
|**NotifyAddress**<br>Tipo de dados: Endereço de correio eletrónico|Implementar este parâmetro para que o utilizador pode especificar o endereço de e-mail a utilizar para enviar uma notificação quando os **notificar** parâmetro for especificado.|
|**Substituir**<br>Tipo de dados: SwitchParameter|Implemente este parâmetro para que o cmdlet substitui qualquer dado existente quando o parâmetro for especificado.|
|**Pedido de confirmação**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar uma linha de comandos para o cmdlet.|
|**silencioso**<br>Tipo de dados: SwitchParameter|Implemente este parâmetro para que o cmdlet suprime os comentários dos utilizadores durante suas ações quando é especificado o parâmetro.|
|**Recurse**<br>Tipo de dados: SwitchParameter|Implemente este parâmetro para que o cmdlet recursivamente executa suas ações nos recursos quando o parâmetro for especificado.|
|**Repair**<br>Tipo de dados: SwitchParameter|Implemente este parâmetro para que o cmdlet irá tentar corrigir algo a partir de um estado danificado quando o parâmetro for especificado.|
|**RepairString**<br>Tipo de dados: Cadeia (de carateres)|Implementar este parâmetro para que o utilizador pode especificar uma cadeia de caracteres a utilizar quando o **reparação** parâmetro for especificado.|
|**Tente novamente**<br>Tipo de dados: Int32|Implemente este parâmetro para que o utilizador pode especificar o número de vezes que o cmdlet irá tentar uma ação.|
|**Select**<br>Tipo de dados: Matriz de palavra-chave|Implemente este parâmetro para que o utilizador pode especificar uma matriz de tipos de itens.|
|**Stream**<br>Tipo de dados: SwitchParameter|Implemente este parâmetro para que o utilizador pode transmitir vários objetos de resultado através do pipeline, quando o parâmetro for especificado.|
|**Strict**<br>Tipo de dados: SwitchParameter|Implemente este parâmetro para que todos os erros são tratados como erros de terminação quando o parâmetro for especificado.|
|**TempLocation**<br>Tipo de dados: Cadeia (de carateres)|Implemente este parâmetro para que o utilizador pode especificar a localização de dados temporárias que são utilizados durante a operação do cmdlet.|
|**Tempo limite**<br>Tipo de dados: Int32|Implemente este parâmetro para que o utilizador pode especificar o intervalo de tempo limite (em milissegundos).|
|**Truncar**<br>Tipo de dados: SwitchParameter|Implemente este parâmetro para que o cmdlet irá truncar suas ações quando é especificado o parâmetro. Se o parâmetro não for especificado, o cmdlet executa outra ação.|
|**Certifique-se**<br>Tipo de dados: SwitchParameter|Implemente este parâmetro para que o cmdlet irá testar para determinar se uma ação tenha ocorrido quando o parâmetro for especificado.|
|**Wait**<br>Tipo de dados: SwitchParameter|Implemente este parâmetro para que o cmdlet irá aguardar pela intervenção do utilizador antes de continuar quando o parâmetro for especificado.
|**WaitTime**<br>Tipo de dados: Int32|Implementar este parâmetro para que o utilizador pode especificar a duração (em segundos) que o cmdlet irá esperar para o utilizador de entrada quando os **aguarde** parâmetro for especificado.|

## <a name="see-also"></a>Veja Também

[Parâmetros do cmdlet](./cmdlet-parameters.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
