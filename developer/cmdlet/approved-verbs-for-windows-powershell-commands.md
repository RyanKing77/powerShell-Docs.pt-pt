---
title: Aprovado verbos para comandos do PowerShell | Documentos da Microsoft
ms.custom: ''
ms.date: 09/07/2018
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- action names [PowerShell SDK]
- verb names [PowerShell SDK]
- cmdlets [PowerShell SDK], verb names
ms.assetid: 2d4e58a9-05bc-437c-86b9-d8d55cba7d48
caps.latest.revision: 36
ms.openlocfilehash: 4475b3f5e15826efbe8bab867011985cd7e2e1ae
ms.sourcegitcommit: 17ce42f97e13e8b3286779dc3f583474b0357023
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/18/2019
ms.locfileid: "59293355"
---
# <a name="approved-verbs-for-powershell-commands"></a>Verbos aprovados para comandos do PowerShell

PowerShell usa um par de verbo-substantivo para os nomes dos cmdlets e suas classes derivadas de Microsoft .NET Framework.
Por exemplo, o `Get-Command` cmdlet fornecido pelo PowerShell é utilizado para obter todos os comandos que estão registados no PowerShell.
A parte de verbo do nome identifica a ação que executa o cmdlet.
A parte do substantivo do nome identifica a entidade na qual a ação é executada.

> [!NOTE]
> PowerShell utiliza o termo *verbo* para descrever uma palavra que implica uma ação, mesmo que essa palavra não é um verbo padrão no idioma inglês.
> Por exemplo, o termo *New* é um nome válido de verbo PowerShell porque ela implica uma ação, embora não seja um verbo no idioma inglês.

## <a name="verb-naming-rules"></a>Regras de nomenclatura de verbo

A lista seguinte fornece orientações a considerar ao escolher o verbo para um nome do cmdlet:

* Quando especifica o verbo, recomendamos que utilize um dos verbos predefinidos para nomes fornecidos pelo PowerShell (aliases para esses verbos predefinidos estão incluídos nas tabelas a seguir).
  Quando utiliza um verbos predefinidos, garante a consistência entre os cmdlets que criar, os cmdlets que são fornecidos pelo PowerShell e os cmdlets que foram criados por outras pessoas.

* Utilize os verbos predefinidos para descrever o escopo geral da ação e utilizar os parâmetros para refinar ainda mais a ação do cmdlet.

* Para impor a consistência em todos os cmdlets, não utilize sinônimo de um verbo aprovado.

* Utilize apenas o formulário de cada verbo que está listado neste tópico.
  Por exemplo, utilize "Get", mas não utilize "Introdução" ou "Obtém".

* Utilizar Pascal casing para verbos.
  No Pascal casing, a letra inicial de cada palavra está em maiúsculas, como "ForEach".

* Não utilize os seguintes verbos reservados ou aliases.
  Esses verbos são utilizados pelo idioma do PowerShell, ou pelos cmdlets de casos especiais fornecidos pelo PowerShell.
  - ForEach (foreach)
  - Formato (f)
  - Grupo (gp)
  - Sort (sr)
  - Tee (te)
  - Onde (q)

## <a name="similar-verbs-for-different-actions"></a>Verbos semelhante para ações diferentes

Os seguintes verbos semelhante representam ações diferentes.

### <a name="new-vs-set"></a>Novo vs. Definir
O `New` verbo é usado para criar um novo recurso.
O `Set` verbo é usado para modificar um recurso existente, o recurso a criar, opcionalmente, se não existir, tais como o `Set-Variable` cmdlet.

### <a name="find-vs-search"></a>Encontre vs. Pesquisa
O `Find` verbo é usado para procurar um objeto.
O `Search` verbo é usado para criar uma referência a um recurso num contentor.

### <a name="get-vs-read"></a>Obtenha vs. Leitura
O `Get` verbo é usado para recuperar um recurso, tal como um ficheiro.
O `Read` verbo é usado para obter informações a partir de uma origem, tal como um ficheiro.

### <a name="invoke-vs-start"></a>Invoca vs. Iniciar
O `Invoke` verbo é usado para realizar uma operação que geralmente é uma operação síncrona, como a execução de um comando.
O `Start` verbo é usado para iniciar uma operação que é, geralmente, uma operação assíncrona, como iniciar um processo.

### <a name="ping-vs-test"></a>Ping vs. Teste
Utilize o `Test` verbo.

## <a name="common-verbs"></a>Common Verbs

PowerShell utiliza a [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon) classe de enumeração para definir ações genéricas que podem aplicar a quase qualquer cmdlet.
A tabela seguinte lista a maioria dos verbos definidos.

|Verbo (alias)|Ação|Comentários|
|--------------------|------------|--------------|
|[Adicionar](/dotnet/api/System.Management.Automation.VerbsCommon.Add) (a)|Adiciona um recurso para um contentor ou anexa um item para outro item. Por exemplo, o `Add-Content` cmdlet adiciona conteúdo a um ficheiro. Esse verbo é emparelhado com `Remove`.|Para esta ação, não utilize verbos como anexar, anexar, Concatenate ou inserir.|
|[Limpar](/dotnet/api/System.Management.Automation.VerbsCommon.Clear) (cl)|Remove todos os recursos de um contentor, mas não elimina o contentor. Por exemplo, o `Clear-Content` cmdlet Remove o conteúdo de um ficheiro, mas não elimina o ficheiro.|Para esta ação, não utilize verbos como Flush, apagar, versão, desmarcar, Unset ou Nullify.|
|[Fechar](/dotnet/api/System.Management.Automation.VerbsCommon.Close) (cs)|Altera o estado de um recurso para torná-la inacessível, indisponível ou não utilizável. Esse verbo é emparelhado com o `Open.`||
|[Cópia](/dotnet/api/System.Management.Automation.VerbsCommon.Copy) (cp)|Copia um recurso para outro nome ou para outro contêiner. Por exemplo, o `Copy-Item` cmdlet que é utilizada para aceder a dados armazenados copia um item de uma localização no arquivo de dados para outra localização.|Para esta ação, não utilize verbos como duplicado, Clone, replicar ou sincronização.|
|[Enter](/dotnet/api/System.Management.Automation.VerbsCommon.Enter) (et)|Especifica uma ação que permita ao usuário mover para um recurso. Por exemplo, o `Enter-PSSession` cmdlet coloca o usuário numa sessão interativa. Esse verbo é emparelhado com `Exit`.|Para esta ação, não utilize verbos, tais como o Push ou em.|
|[Saída](/dotnet/api/System.Management.Automation.VerbsCommon.Exit) (ex)|Define o ambiente atual ou o contexto para o contexto mais recentemente utilizado. Por exemplo, o `Exit-PSSession` cmdlet coloca o utilizador na sessão que foi utilizada para iniciar a sessão interativa. Esse verbo é emparelhado com `Enter`.|Para esta ação, não utilize verbos como Pop ou para fora.|
|[Encontrar](/dotnet/api/System.Management.Automation.VerbsCommon.Find) (fd)|Procura um objeto num contentor que é desconhecido, implícita, opcional ou especificado.||
|[Formato](/dotnet/api/System.Management.Automation.VerbsCommon.Format) (f)|Organiza os objetos num formulário especificado ou o layout.||
|[Obter](/dotnet/api/System.Management.Automation.VerbsCommon.Get) (g)|Especifica uma ação que obtém um recurso. Esse verbo é emparelhado com `Set`.|Para esta ação, não utilize verbos como leitura, aberto, Cat, tipo, Dir, obter, despejo, aquisição, Examine, localizar ou pesquisa.|
|[Ocultar](/dotnet/api/System.Management.Automation.VerbsCommon.Hide) (h)|Faz com que um recurso, indetetáveis. Por exemplo, um cmdlet cujo nome inclui o verbo de ocultar pode ocultar um serviço de um utilizador. Esse verbo é emparelhado com `Show`.|Para esta ação, não utilize um verbo, como o bloco.|
|[Junte-se a](/dotnet/api/System.Management.Automation.VerbsCommon.Join) (j)|Combina recursos num recurso. Por exemplo, o `Join-Path` cmdlet combina um caminho com um dos seus caminhos de subordinados para criar um caminho único. Esse verbo é emparelhado com `Split`.|Para esta ação, não utilize verbos como combinação, Unite, ligar ou associar.|
|[Bloqueio](/dotnet/api/System.Management.Automation.VerbsCommon.Lock) (lk)|Protege um recurso. Esse verbo é emparelhado com `Unlock`.|Para esta ação, não utilize verbos como restringir ou seguro.|
|[Move](/dotnet/api/System.Management.Automation.VerbsCommon.Move) (m)|Move um recurso de um único local para outro. Por exemplo, o `Move-Item` cmdlet move um item de uma localização no arquivo de dados para outra localização.|Para esta ação, não utilize verbos, como a transferência, o nome ou para migrar.|
|[Novo](/dotnet/api/System.Management.Automation.VerbsCommon.New) (n)|Cria um recurso. (A `Set` verbo também pode ser utilizado quando criar um recurso que inclui dados, como o `Set-Variable` cmdlet.)|Para esta ação, não utilize verbos como Create, gerar, compilação, certifique ou Allocate.|
|[Abra](/dotnet/api/System.Management.Automation.VerbsCommon.Open) (op)|Altera o estado de um recurso para que seja acessível, disponível ou utilizável. Esse verbo é emparelhado com `Close`.||
|[Otimizar](/dotnet/api/System.Management.Automation.VerbsCommon.Optimize) (om)|Aumenta a eficácia de um recurso.||
|[POP-](/dotnet/api/System.Management.Automation.VerbsCommon.Pop) (pop)|Remove um item da parte superior de uma pilha. Por exemplo, o `Pop-Location` cmdlet altera a localização atual para a localização que foi mais recentemente enviada na pilha.||
|[Push](/dotnet/api/System.Management.Automation.VerbsCommon.Push) (pu)|Adiciona um item na parte superior de uma pilha. Por exemplo, o `Push-Location` cmdlet envia por push a localização atual para a pilha.||
|[Redo](/dotnet/api/System.Management.Automation.VerbsCommon.Redo) (re)|Repõe um recurso para o estado que foi anulado.||
|[Remover](/dotnet/api/System.Management.Automation.VerbsCommon.Remove) (r)|Elimina um recurso a partir de um contentor. Por exemplo, o `Remove-Variable` cmdlet elimina uma variável e o respetivo valor. Esse verbo é emparelhado com `Add`.|Para esta ação, não utilize verbos, tais como limpar, cortar, Dispose, rejeição ou apagar.|
|[Mudar o nome](/dotnet/api/System.Management.Automation.VerbsCommon.Rename) (rn)|Altera o nome de um recurso. Por exemplo, o `Rename-Item` cmdlet, que é usado para acessar dados armazenados, altera o nome de um item no arquivo de dados.|Para esta ação, não utilize um verbo, tais como a alteração.|
|[Repor](/dotnet/api/System.Management.Automation.VerbsCommon.Reset) (rs)|Define um recurso de volta ao estado original.||
|[Pesquisa](/dotnet/api/System.Management.Automation.VerbsCommon.Search) (sr)|Cria uma referência a um recurso num contentor.|Para esta ação, não utilize verbos como Find ou localizar.|
|[Selecione](/dotnet/api/System.Management.Automation.VerbsCommon.Select) (sc)|Localiza um recurso num contentor. Por exemplo, o `Select-String` cmdlet localiza o texto em cadeias de caracteres e ficheiros.|Para esta ação, não utilize verbos como Find ou localizar.|
|[Definir](/dotnet/api/System.Management.Automation.VerbsCommon.Set) (s)|Substitui os dados num recurso existente ou cria um recurso que contém alguns dados. Por exemplo, o `Set-Date` cmdlet altera a hora do sistema no computador local. (O `New` verbo também pode ser utilizado para criar um recurso.) Esse verbo é emparelhado com `Get`.|Para esta ação, não utilize verbos como escrita, repor, atribuir ou configurar.|
|[Mostrar](/dotnet/api/System.Management.Automation.VerbsCommon.Show) (sh)|Um recurso torna visível para o usuário. Esse verbo é emparelhado com `Hide`.|Para esta ação, não utilize verbos como apresentar ou produzem.|
|[Ignorar](/dotnet/api/System.Management.Automation.VerbsCommon.Skip) (disco)|Ignora um ou mais recursos ou pontos numa sequência.|Para esta ação, não utilize um verbo, como ignorar ou atalhos.|
|[Divisão](/dotnet/api/System.Management.Automation.VerbsCommon.Split) (sl)|Separa a partes de um recurso. Por exemplo, o `Split-Path` cmdlet devolve diferentes partes de um caminho. Esse verbo é emparelhado com `Join`.|Para esta ação, não utilize um verbo tal separado.|
|[Passo](/dotnet/api/System.Management.Automation.VerbsCommon.Step) (st)|Move-o para o próximo ponto ou recurso numa seqüência.||
|[Comutador](/dotnet/api/System.Management.Automation.VerbsCommon.Switch) (sw)|Especifica uma ação que alterna entre os dois recursos, tal como para alterar entre duas localizações, responsabilidades ou Estados.||
|[Anular](/dotnet/api/System.Management.Automation.VerbsCommon.Undo) (NU)|Define um recurso para o estado anterior.||
|[Desbloquear](/dotnet/api/System.Management.Automation.VerbsCommon.Unlock) (Reino Unido)|Libera um recurso que foi bloqueado. Esse verbo é emparelhado com `Lock`.|Para esta ação, não utilize verbos como versão, Unrestrict ou inseguro.|
|[Assista](/dotnet/api/System.Management.Automation.VerbsCommon.Watch) (wc)|Continuamente inspeciona ou monitoriza um recurso para que as alterações.||

## <a name="communications-verbs"></a>Verbos de comunicações

PowerShell utiliza a [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications) classe para definir ações que se aplicam a comunicações.
A tabela seguinte lista a maioria dos verbos definidos.

|Verbo (alias)|Ação|Comentários|
|--------------------|------------|--------------|
|[Ligar](/dotnet/api/System.Management.Automation.VerbsCommunications.Connect) (cc)|Cria uma ligação entre uma origem e um destino. Esse verbo é emparelhado com `Disconnect`.|Para esta ação, não utilize verbos, tais como associação ou Telnet.|
|[Desligar](/dotnet/api/System.Management.Automation.VerbsCommunications.Disconnect) (dc)|Quebra a ligação entre uma origem e um destino. Esse verbo é emparelhado com `Connect`.|Para esta ação, não utilize verbos como garantia de reparação ou Logoff.|
|[Leitura](/dotnet/api/System.Management.Automation.VerbsCommunications.Read) (rd)|Adquire informações de uma origem. Esse verbo é emparelhado com `Write`.|Para esta ação, não utilize verbos como aquisição, aviso ou obter.|
|[Receber](/dotnet/api/System.Management.Automation.VerbsCommunications.Receive) (rc)|Aceita as informações enviadas a partir de uma origem. Esse verbo é emparelhado com `Send`.|Para esta ação, não utilize verbos como leitura, Accept, ou pré-visualização.|
|[Enviar](/dotnet/api/System.Management.Automation.VerbsCommunications.Send) (dp)|Fornece informações para um destino. Esse verbo é emparelhado com `Receive`.|Para esta ação, não utilize verbos como Put, difusão, postais ou Fax.|
|[Escrever](/dotnet/api/System.Management.Automation.VerbsCommunications.Write) (wr)|Adiciona informações para um destino. Esse verbo é emparelhado com `Read`.|Para esta ação, não utilize verbos como colocados ou de impressão.|

## <a name="data-verbs"></a>Verbos de dados

PowerShell utiliza a [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData) classe para definir ações que se aplicam a manipulação de dados.
A tabela seguinte lista a maioria dos verbos definidos.

|Nome de verbo (alias)|Ação|Comentários|
|-------------------------|------------|--------------|
|[Cópia de segurança](/dotnet/api/System.Management.Automation.VerbsData.Backup) (ba)|Armazena os dados ao replicá-los.|Para esta ação, não utilize verbos como salvar, grave, replicar ou sincronização.|
|[Ponto de verificação](/dotnet/api/System.Management.Automation.VerbsData.Checkpoint) (ch)|Cria um instantâneo do estado atual dos dados ou de sua configuração.|Para esta ação, não utilize um verbo, tais como a diferença|
|[Comparar](/dotnet/api/System.Management.Automation.VerbsData.Compare) (cr)|Avalia os dados a partir de um recurso com os dados de outro recurso.|Para esta ação, não utilize um verbo, tais como a diferença|
|[Comprimir](/dotnet/api/System.Management.Automation.VerbsData.Compress) (cm)|Compacta os dados de um recurso. Pares com `Expand`.|Para esta ação, não utilize um verbo, como o Compact.|
|[Converter](/dotnet/api/System.Management.Automation.VerbsData.Convert) (cv)|Altera os dados de uma representação para outra quando o cmdlet oferece suporte a conversão de bidirecional ou quando o cmdlet oferece suporte a conversão entre vários tipos de dados.|Para esta ação, não utilize verbos como alteração, redimensionar, ou Resample.|
|[ConvertFrom](/dotnet/api/System.Management.Automation.VerbsData.ConvertFrom) (cf)|Converte um tipo de principal de entrada (o substantivo do cmdlet indica a entrada) para um ou mais tipos de saída suportados.|Para esta ação, não utilize verbos como exportar, saída ou Out.|
|[ConvertTo](/dotnet/api/System.Management.Automation.VerbsData.ConvertTo) (ct)|Converte de um ou mais tipos de entrada para um tipo de saída primária (o substantivo do cmdlet indica o tipo de saída).|Para esta ação, não utilize verbos como importar, de entrada, ou no.|
|[Desmontar](/dotnet/api/System.Management.Automation.VerbsData.Dismount) (dm)|Desliga uma entidade nomeada de uma localização. Esse verbo é emparelhado com `Mount`.|Para esta ação, não utilize verbos como desmontar ou desassociar.|
|[Editar](/dotnet/api/System.Management.Automation.VerbsData.Edit) (ed)|Modifica os dados existentes ao adicionar ou remover conteúdo.|Para esta ação, não utilize verbos como alteração, atualização ou modificar.|
|[Expanda](/dotnet/api/System.Management.Automation.VerbsData.Expand) (pt)|Restaura os dados de um recurso que compactado ao estado original. Esse verbo é emparelhado com `Compress`.|Para esta ação, não utilize verbos como Explode ou Uncompress.|
|[Exportar](/dotnet/api/System.Management.Automation.VerbsData.Export) (ep)|Encapsula a entrada principal para um armazenamento de dados persistente, como um arquivo, ou para um formato de intercâmbio. Esse verbo é emparelhado com `Import`.|Para esta ação, não utilize verbos como cópia de segurança ou de extração.|
|[Grupo](/dotnet/api/System.Management.Automation.VerbsData.Group) (gp)|Organiza ou associa um ou mais recursos.|Para esta ação, não utilize verbos como agregação, dispor, associar ou correlacionar.|
|[Importar](/dotnet/api/System.Management.Automation.VerbsData.Import) (ip)|Cria um recurso de dados armazenados num arquivo de dados persistentes (como um arquivo) ou num formato de intercâmbio. Por exemplo, o `Import-CSV` cmdlet importa dados a partir de um ficheiro de valores separados por vírgulas (CSV) para objetos que podem ser utilizados por outros cmdlets. Esse verbo é emparelhado com `Export`.|Para esta ação, não utilize verbos como BulkLoad ou de carga.|
|[Inicializar](/dotnet/api/System.Management.Automation.VerbsData.Initialize) (in)|Prepara um recurso para uso e a define como um estado predefinido.|Para esta ação, não utilize verbos como apagar, Init, renovação, recompilação, reinicialize ou configuração.|
|[Limite](/dotnet/api/System.Management.Automation.VerbsData.Limit) (l)|Aplica-se restrições a um recurso.|Para esta ação, não utilize um verbo, por exemplo, a Quota.|
|[Intercalar](/dotnet/api/System.Management.Automation.VerbsData.Merge) (grupo de gestão)|Cria um único recurso de vários recursos.|Para esta ação, não utilize verbos como combinar ou uma associação.|
|[Montar](/dotnet/api/System.Management.Automation.VerbsData.Mount) (TA)|Anexa uma entidade nomeada para uma localização. Esse verbo é emparelhado com `Dismount`.|Para esta ação, não utilize o verbo Connect.|
|[Out](/dotnet/api/System.Management.Automation.VerbsData.Out) (s)|Envia dados para fora do ambiente. Por exemplo, o `Out-Printer` cmdlet envia dados para uma impressora.||
|[Publicar](/dotnet/api/System.Management.Automation.VerbsData.Publish) (HC)|Um recurso torna disponível para outros utilizadores. Esse verbo é emparelhado com `Unpublish`.|Para esta ação, não utilize verbos como implementar, versão, ou instalar.|
|[Restaurar](/dotnet/api/System.Management.Automation.VerbsData.Restore) (rr)|Define um recurso para um estado predefinido, como um Estado definido pela `Checkpoint`. Por exemplo, o `Restore-Computer` cmdlet inicia uma restauração do sistema no computador local.|Para esta ação, não utilize verbos como reparação, retorno, anulação ou correção.|
|[Guardar](/dotnet/api/System.Management.Automation.VerbsData.Save) (sv)|Preserva os dados para evitar a perda.||
|[Sincronização](/dotnet/api/System.Management.Automation.VerbsData.Sync) (sy)|Garante que duas ou mais recursos estão no mesmo Estado.|Para esta ação, não utilize verbos como replicar, Coerce, ou corresponder.|
|[Anular a publicação](/dotnet/api/System.Management.Automation.VerbsData.Unpublish) (ub)|Um recurso torna indisponível para outras pessoas. Esse verbo é emparelhado com `Publish`.|Para esta ação, não utilize verbos como desinstalar, reverter, ou ocultar.|
|[Atualização](/dotnet/api/System.Management.Automation.VerbsData.Update) (ud)|Oferece um recurso atualizado para manter o seu estado, a precisão, a conformidade ou a conformidade. Por exemplo, o `Update-FormatData` cmdlet atualiza e adiciona os arquivos de formatação para a consola atual do PowerShell.|Para esta ação, não utilize verbos como recálculo de atualização, renovação, ou voltar a indexar.|

## <a name="diagnostic-verbs"></a>Verbos de diagnóstico

PowerShell utiliza a [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic) classe para definir ações que se aplicam aos diagnósticos.
A tabela seguinte lista a maioria dos verbos definidos.

|Verbo (alias)|Ação|Comentários|
|--------------------|------------|--------------|
|[Depurar](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Debug) (db)|Examina um recurso para diagnosticar problemas operacionais.|Para esta ação, não utilize um verbo, como o diagnóstico.|
|[Medida](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Measure) (ms)|Identifica os recursos que são consumidos por uma operação especificada ou obtém estatísticas sobre um recurso.|Para esta ação, não utilize verbos como Calculate, determinar ou analisar.|
|[Ping](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Ping) (pi)|Utilize o `Test` verbo.||
|[Repair](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Repair) (rp)|Restaura um recurso a uma condição utilizável|Para esta ação, não utilize verbos como correção ou restauro.|
|[Resolve](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Resolve) (rv)|Mapeia uma representação de forma abreviada de um recurso para uma representação mais completa.|Para esta ação, não utilize verbos como expansão ou determinar.|
|[Teste](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Test) (t)|Verifica se a operação ou a consistência de um recurso.|Para esta ação, não utilize verbos como diagnosticar, analisar, residual ou certifique-se.|
|[Rastreio](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Trace) (tr)|Regista as atividades de um recurso.|Para esta ação, não utilize verbos como controlar, siga, Inspect, ou se aprofundar.|

## <a name="lifecycle-verbs"></a>Verbos de ciclo de vida

PowerShell utiliza a [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) classe para definir ações que se aplicam ao ciclo de vida de um recurso.
A tabela seguinte lista a maioria dos verbos definidos.

|Verbo (alias)|Ação|Comentários|
|--------------------|------------|--------------|
|[Aprovar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Approve) (ap)|Confirma ou concorda com o estado de um recurso ou processo.||
|[---Vyhodnocení](/dotnet/api/System.Management.Automation.VerbsLifecycle.Assert) (como)|Informa o estado de um recurso.|Para esta ação, não utilize um verbo, como Certify.|
|[Criar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Build) (DB)|Cria um artefacto (geralmente um binário ou documento) para fora de um conjunto de ficheiros de entrada (normalmente, código-fonte ou documentos declarativos)|Esse verbo foi adicionado no PowerShell v6|
|[Completa](/dotnet/api/system.management.automation.host.buffercelltype?view=powershellsdk-1.1.0) (cp)|É concluída uma operação.||
|[Confirmar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Confirm) (cn)|Reconhece, verifica ou valida o estado de um recurso ou processo.|Para esta ação, não utilize verbos como confirmação, Concordo, Certify, validar ou certifique-se.|
|[Negar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deny) (dn)|Recusa-se, objetos, bloqueia ou opposes o estado de um recurso ou processo.|Para esta ação, não utilize verbos como bloco, objeto, recusar ou rejeitar.|
|[Implementar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deploy) (dp)|Envia uma aplicação, um Web site ou uma solução para um destino remoto [s] de tal forma que um consumidor dessa solução pode aceder ao mesmo após a conclusão da implementação|Esse verbo foi adicionado no PowerShell v6|
|[Desativar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Disable) (d)|Configura um recurso para um estado inativo ou indisponível. Por exemplo, o `Disable-PSBreakpoint` cmdlet faz um ponto de interrupção inativos. Esse verbo é emparelhado com `Enable`.|Para esta ação, não utilize verbos como parar ou ocultar.|
|[Ativar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Enable) (e)|Configura um recurso para um estado disponível ou Active Directory. Por exemplo, o `Enable-PSBreakpoint` cmdlet faz um ponto de interrupção Active Directory. Esse verbo é emparelhado com `Disable`.|Para esta ação, não utilize verbos como iniciar ou Begin.|
|[Instalar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Install) (é)|Coloca um recurso num local e, opcionalmente, inicializa-lo. Esse verbo é emparelhado com `Uninstall`.|Para esta ação, fazer não um verbo de uso, como o programa de configuração.|
|[Invoke](/dotnet/api/System.Management.Automation.VerbsLifecycle.Invoke) (i)|Executa uma ação, como a execução de um comando ou um método.|Para esta ação, não utilize verbos como executar ou começar.|
|[Registar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Register) (rg)|Cria uma entrada para um recurso num repositório, como uma base de dados. Esse verbo é emparelhado com `Unregister`.||
|[Pedir](/dotnet/api/System.Management.Automation.VerbsLifecycle.Request) (rq)|Pede-lhe um recurso ou pede-lhe permissões.||
|[Reiniciar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Restart) (rt)|Para uma operação e, em seguida, inicia-o novamente. Por exemplo, o `Restart-Service` cmdlet pára e, em seguida, inicia um serviço.|Para esta ação, não utilize um verbo, por exemplo, a Reciclagem.|
|[Resume](/dotnet/api/System.Management.Automation.VerbsLifecycle.Resume) (ru)|Inicia uma operação que foi suspensa. Por exemplo, o `Resume-Service` cmdlet inicia um serviço que foi suspensa. Esse verbo é emparelhado com `Suspend`.||
|[Iniciar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Start) (sa)|Inicia uma operação. Por exemplo, o `Start-Service` cmdlet inicia um serviço. Esse verbo é emparelhado com `Stop`.|Para esta ação, não utilize verbos como iniciar, iniciar ou o arranque.|
|[Parar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Stop) (sp)|Discontinues uma atividade. Esse verbo é emparelhado com `Start`.|Para esta ação, não utilize verbos como final, eliminação, encerrar ou Cancelar.|
|[Submeter](/dotnet/api/System.Management.Automation.VerbsLifecycle.Submit) (sb)|Apresenta um recurso para aprovação.|Para esta ação, não utilize um verbo, como postagem.|
|[Suspender](/dotnet/api/System.Management.Automation.VerbsLifecycle.Suspend) (ss)|Coloca em pausa uma atividade. Por exemplo, o `Suspend-Service` cmdlet pausa um serviço. Esse verbo é emparelhado com `Resume`.|Para esta ação, não utilize um verbo, como colocar em pausa.|
|[Desinstalar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Uninstall) (us)|Remove um recurso a partir de uma localização indicada. Esse verbo é emparelhado com `Install`.||
|[Anular o registo](/dotnet/api/System.Management.Automation.VerbsLifecycle.Unregister) (sua)|Remove a entrada para um recurso a partir de um repositório. Esse verbo é emparelhado com `Register`.|Para esta ação, não utilize um verbo, tais como remover.|
|[Aguarde](/dotnet/api/System.Management.Automation.VerbsLifecycle.Wait) (w)|Coloca em pausa uma operação até que ocorra um evento especificado. Por exemplo, o `Wait-Job` cmdlet interrompe operações até que um ou mais das tarefas em segundo plano forem concluídas.|Para esta ação, não utilize verbos, como o modo de suspensão ou colocar em pausa.|

## <a name="security-verbs"></a>Verbos de segurança

PowerShell utiliza a [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity) classe para definir ações que se aplicam a segurança.
A tabela seguinte lista a maioria dos verbos definidos.

|Verbo (alias)|Ação|Comentários|
|--------------------|------------|--------------|
|[Bloco](/dotnet/api/System.Management.Automation.VerbsSecurity.Block) (bl)|Restringe o acesso a um recurso. Esse verbo é emparelhado com `Unblock`.|Para esta ação, não utilize verbos como impedir, limite ou negar.|
|[Concessão](/dotnet/api/System.Management.Automation.VerbsSecurity.Grant) (gr)|Permite o acesso a um recurso. Esse verbo é emparelhado com `Revoke`.|Para esta ação, não utilize verbos como permitir ou ativar.|
|[Proteger](/dotnet/api/System.Management.Automation.VerbsSecurity.Protect) (hora do Pacífico)|Protege um recurso de ataque ou perda. Esse verbo é emparelhado com `Unprotect`.|Para esta ação, não utilize verbos como Encrypt, salvaguardar ou selar.|
|[Revoke](/dotnet/api/System.Management.Automation.VerbsSecurity.Revoke) (rk)|Especifica uma ação que não permite o acesso a um recurso. Esse verbo é emparelhado com `Grant`.|Para esta ação, não utilize verbos como remover ou desativar.|
|[Desbloquear](/dotnet/api/System.Management.Automation.VerbsSecurity.Unblock) (ul)|Remove as restrições a um recurso. Esse verbo é emparelhado com `Block`.|Para esta ação, não utilize verbos como limpar ou permitir.|
|[Unprotect](/dotnet/api/System.Management.Automation.VerbsSecurity.Unprotect) (up)|Remove as proteções de um recurso que foram adicionados para impedi-lo de ataque ou perda. Esse verbo é emparelhado com `Protect`.|Para esta ação, não utilize verbos como desencriptar ou Unseal.|

## <a name="other-verbs"></a>Outros verbos

PowerShell utiliza a [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther) classe para definir os nomes de verbo canônico que não se encaixam numa categoria de nome de verbo específico, como o comum, comunicações, dados, ciclo de vida ou nomes de verbo de segurança verbos.

|Verbo (alias)|Ação|Comentários|
|--------------------|------------|--------------|
|[Utilize](/dotnet/api/System.Management.Automation.VerbsOther.Use) (u)|Utiliza ou inclui um recurso para fazer algo.||

## <a name="see-also"></a>Veja Também

[System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

[System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

[System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

[System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

[System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

[System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

[System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

[Declaração de cmdlet](./cmdlet-class-declaration.md)

[Guia do programador do Windows PowerShell](../prog-guide/windows-powershell-programmer-s-guide.md)

[Shell do Windows PowerShell SDK](../windows-powershell-reference.md)
