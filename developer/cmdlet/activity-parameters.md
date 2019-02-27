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
ms.openlocfilehash: 32e2b8acf33bc733c5e4cab94a721076ff46225d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849092"
---
# <a name="activity-parameters"></a>Parâmetros de Atividades

A tabela seguinte lista os nomes recomendados e a funcionalidade para parâmetros de atividades.

Acrescente o tipo de dados: SwitchParameter

Implemente este parâmetro para que o utilizador pode adicionar conteúdo ao final de um recurso quando o parâmetro for especificado.

Tipo de dados de CaseSensitive: SwitchParameter

Implemente este parâmetro para que o utilizador pode exigir a maiúsculas e minúsculas, quando o parâmetro for especificado.

Tipo de dados de comando: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar uma cadeia de caracteres de comando para executar.

Tipo de dados de CompatibleVersion: Objeto de ter

Implemente este parâmetro para que o utilizador pode especificar a semântica que o cmdlet tem de ser compatível com para compatibilidade com versões anteriores.

Comprima o tipo de dados: SwitchParameter

Implemente este parâmetro para que a compressão de dados é utilizada quando o parâmetro for especificado.

Comprima o tipo de dados: Palavra-chave

Implemente este parâmetro para que o utilizador pode especificar o algoritmo a utilizar para compressão de dados.

Tipo de dados contínuos: SwitchParameter

Implemente este parâmetro, de modo a que os dados são processados até que o usuário termina o cmdlet quando o parâmetro for especificado. Se o parâmetro não for especificado, o cmdlet processa uma quantidade predefinida de dados e, em seguida, termina a operação.

Crie tipo de dados: SwitchParameter

Implemente este parâmetro para indicar que um recurso é criado se ainda não existir quando é especificado o parâmetro.

Elimine tipo de dados: SwitchParameter

Implemente este parâmetro, de modo a que os recursos são eliminados quando o cmdlet concluiu sua operação quando o parâmetro for especificado.

Drenar o tipo de dados: SwitchParameter

Implemente este parâmetro para indicar que os itens de trabalho pendentes são processados antes do cmdlet processa novos dados, quando o parâmetro for especificado. Se o parâmetro não for especificado, os itens de trabalho são processados imediatamente.

Apagar o tipo de dados: Int32

Implemente este parâmetro para que o utilizador pode especificar o número de vezes que um recurso é apagado antes de ser eliminado.

Tipo de dados de nível de erro: Int32

Implemente este parâmetro para que o utilizador pode especificar o nível de erros ao relatório.

Exclua o tipo de dados: String[]

Implemente este parâmetro para que o usuário pode excluir algo de uma atividade. Para obter mais informações sobre como utilizar filtros de entrada, consulte [parâmetros de filtro de entrada](./input-filter-parameters.md).

Tipo de dados de filtro: Palavra-chave

Implemente este parâmetro para que o utilizador pode especificar um filtro que seleciona os recursos no qual executar a ação de cmdlet. Para obter mais informações sobre como utilizar filtros de entrada, consulte [parâmetros de filtro de entrada](./input-filter-parameters.md).

Siga o tipo de dados: SwitchParameter

Implemente este parâmetro, de modo a que o progresso é controlado quando o parâmetro for especificado.

Força o tipo de dados: SwitchParameter

Implemente este parâmetro para indicar que o usuário pode executar uma ação, mesmo que restrições são encontradas quando o parâmetro for especificado. O parâmetro não permite a segurança ser comprometido. Por exemplo, este parâmetro permite que um utilizador substituir um ficheiro só de leitura.

Inclua o tipo de dados: String[]

Implemente este parâmetro para que o utilizador pode incluir algo numa atividade. Para obter mais informações sobre como utilizar filtros de entrada, consulte [parâmetros de filtro de entrada](./input-filter-parameters.md).

Tipo de dados incrementais: SwitchParameter

Implemente este parâmetro para indicar que o processamento é efetuado incrementalmente quando o parâmetro for especificado. Por exemplo, este parâmetro permite que um utilizador efetuar cópias de segurança incrementais de que fazer backup de arquivos apenas desde a última cópia de segurança.

Tipo de dados de InputObject: Objeto

Implemente este parâmetro quando o cmdlet pega a entrada de outros cmdlets. Quando define um `InputObject` parâmetro, sempre especificar o `ValueFromPipeline` palavra-chave quando declara a **parâmetro** atributo. Para obter mais informações sobre como utilizar filtros de entrada, consulte [parâmetros de filtro de entrada](./input-filter-parameters.md).

Insira o tipo de dados: SwitchParameter

Implemente este parâmetro para que o cmdlet insere um item quando o parâmetro for especificado.

Tipo de dados interativos: SwitchParameter

Implemente este parâmetro para que o cmdlet interativamente funciona com o utilizador de quando o parâmetro for especificado.

Tipo de dados de intervalo: HashTable

Implemente este parâmetro para que o utilizador pode especificar uma tabela de hash de palavras-chave que contém os valores. O exemplo seguinte mostra os valores de exemplo para o `Interval` parâmetro: `-interval @{ResumeScan=15; Retry=3}`.

Tipo de dados de registo: SwitchParameter

Implemente esta auditoria de parâmetro as ações do cmdlet, quando o parâmetro for especificado.

Tipo de dados de NoClobber: SwitchParameter

Implemente este parâmetro para que o recurso não será substituído quando o parâmetro for especificado. Este parâmetro aplica-se geralmente aos cmdlets de criar novos objetos para que eles podem ser impedidos de substituição de objetos existentes com o mesmo nome.

Notificar o tipo de dados: SwitchParameter

Implemente este parâmetro para que o utilizador será notificado que a atividade foi concluída quando o parâmetro for especificado.

Tipo de dados de NotifyAddress: Endereço de E-mail

Implementar este parâmetro para que o utilizador pode especificar o endereço de e-mail a utilizar para enviar uma notificação quando o `Notify` parâmetro for especificado.

Substitua o tipo de dados: SwitchParameter

Implemente este parâmetro para que o cmdlet substitui qualquer dado existente quando o parâmetro for especificado.

Tipo de dados de linha de comandos: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar uma linha de comandos para o cmdlet.

Tipo de dados silencioso: SwitchParameter

Implemente este parâmetro para que o cmdlet suprime os comentários dos utilizadores durante suas ações quando é especificado o parâmetro.

Recurse o tipo de dados: SwitchParameter

Implemente este parâmetro para que o cmdlet recursivamente executa suas ações nos recursos quando o parâmetro for especificado.

Repare o tipo de dados: SwitchParameter

Implemente este parâmetro para que o cmdlet irá tentar corrigir algo a partir de um estado danificado quando o parâmetro for especificado.

Tipo de dados de RepairString: Cadeia (de carateres)

Implementar este parâmetro para que o utilizador pode especificar uma cadeia de caracteres a utilizar quando o `Repair` parâmetro for especificado.

Repita o tipo de dados: Int32

Implemente este parâmetro para que o utilizador pode especificar o número de vezes que o cmdlet irá tentar uma ação.

Selecione o tipo de dados: Matriz de palavra-chave

Implemente este parâmetro para que o utilizador pode especificar uma matriz de tipos de itens.

Tipo de dados do Stream: SwitchParameter

Implemente este parâmetro para que o utilizador pode transmitir vários objetos de resultado através do pipeline, quando o parâmetro for especificado.

Tipo de dados Strict: SwitchParameter

Implemente este parâmetro para que todos os erros são tratados como erros de terminação quando o parâmetro for especificado.

Tipo de dados de TempLocation: Cadeia (de carateres)

Implemente este parâmetro para que o utilizador pode especificar a localização de dados temporárias que são utilizados durante a operação do cmdlet.

Tipo de dados de tempo limite: Int32

Implemente este parâmetro para que o utilizador pode especificar o intervalo de tempo limite (em milissegundos).

Truncar o tipo de dados: SwitchParameter

Implemente este parâmetro para que o cmdlet irá truncar suas ações quando é especificado o parâmetro. Se o parâmetro não for especificado, o cmdlet executa outra ação.

Verifique se o tipo de dados: SwitchParameter

Implemente este parâmetro para que o cmdlet irá testar para determinar se uma ação tenha ocorrido quando o parâmetro for especificado.

Aguarde o tipo de dados: SwitchParameter

Implemente este parâmetro para que o cmdlet irá aguardar pela intervenção do utilizador antes de continuar quando o parâmetro for especificado.

Tipo de dados de tempo de espera: Int32

Implementar este parâmetro para que o utilizador pode especificar a duração (em segundos) que o cmdlet irá esperar para o utilizador de entrada quando a `Wait` parâmetro for especificado.

## <a name="see-also"></a>Consulte Também

[Parâmetros do cmdlet](./cmdlet-parameters.md)

[Escrever um Cmdlet do Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[SDK do Windows PowerShell](../windows-powershell-reference.md)
