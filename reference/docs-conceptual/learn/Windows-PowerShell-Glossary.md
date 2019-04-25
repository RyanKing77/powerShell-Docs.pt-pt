---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Glossário do Windows PowerShell
ms.assetid: b0f88cbe-cb83-4912-a301-184534cb35c7
ms.openlocfilehash: fd15667939fd9b3ea705806686b626645519588a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057365"
---
# <a name="windows-powershell-glossary"></a>Glossário do Windows PowerShell


|Termo|Definição|
|--------|--------------|
|módulo de binário|Um módulo do PowerShell de Windows cujo módulo de raiz é um ficheiro de módulo binário (. dll). Um módulo binário pode ou não pode incluir um manifesto de módulo.|
|parâmetro comum|Um parâmetro que é adicionado a todos os cmdlets, funções avançadas e fluxos de trabalho pelo mecanismo do Windows PowerShell.|
|origem de ponto|No Windows PowerShell, para iniciar um comando, digitando um ponto e um espaço antes do comando. Comandos que são o ponto de origem são executados no âmbito atual, em vez de num novo âmbito. Quaisquer variáveis, aliases, funções ou unidades de que o comando cria são criadas no âmbito atual e estão disponíveis para os utilizadores quando o comando é concluído.|
|módulo dinâmico|Um módulo que existe apenas na memória. Os cmdlets New-Module e Import-PSSession criar módulos dinâmicos.|
|parâmetro dinâmico|Um parâmetro que é adicionado um cmdlet do Windows PowerShell, função ou script sob determinadas condições. Cmdlets, funções, fornecedores e scripts, podem adicionar parâmetros dinâmicos.|
|formatação de ficheiro|Um ficheiro XML do Windows PowerShell com o. format.ps1xml extensão e de que define como o Windows PowerShell apresenta um objeto com base em seu tipo de .NET Framework.|
|Estado da sessão global|O estado de sessão que contém os dados que esteja acessíveis para o utilizador de uma sessão do Windows PowerShell.|
|anfitrião|A interface que o motor do Windows PowerShell utiliza para comunicar com o utilizador. Por exemplo, o anfitrião Especifica como os pedidos são processados entre o Windows PowerShell e o utilizador.|
|aplicativo de Host|Um programa que carrega o motor do Windows PowerShell no seu processo e utiliza-o para executar operações de mensagens em fila.|
|método de processamento de entrada|Um método que um cmdlet pode utilizar para processar os registos que recebe como entrada. Os métodos de processamento de entrada incluem o método BeginProcessing, o método ProcessRecord, o método EndProcessing e o método StopProcessing.|
|manifesto de módulo|Um módulo do Windows PowerShell com um manifesto de cuja chave RootModule está vazio.|
|manifesto do módulo|Um Windows PowerShell ficheiro de dados (. psd1) que descreve o conteúdo de um módulo e que controla a forma como um módulo é processado.|
|Estado da sessão de módulo|O estado de sessão que contém os dados públicos e privados de um módulo do Windows PowerShell. Os dados privados neste estado de sessão não estão disponíveis para o utilizador de uma sessão do Windows PowerShell.|
|Erro de não terminação|Um erro que não para o Windows PowerShell de continuar a processar o comando.|
|nome próprio|A palavra que se segue o hífen um nome de cmdlet do Windows PowerShell. O substantivo descreve os recursos no qual o cmdlet atua.|
|Conjunto de parâmetros|Um grupo de parâmetros que podem ser usados no mesmo comando a executar uma ação específica.|
|pipe|No Windows PowerShell, para enviar os resultados do comando anterior como entrada para o comando seguinte no pipeline.|
|Pipeline|Uma série de comandos, ligado por operadores de pipeline (&#124;) (ASCII 124). Cada operador de pipeline envia os resultados do comando anterior como entrada para o próximo comando.|
|PSSession|Um tipo de sessão do Windows PowerShell que é criado, gerido e fechado pelo usuário.|
|módulo de raiz|O módulo especificado na chave do RootModule num manifesto de módulo.|
|espaço de execução|No Windows PowerShell, o ambiente operacional em que cada comando num pipeline é executado.|
|Bloco de script|No Windows PowerShell de programação de linguagem, uma coleção de instruções ou expressões que podem ser utilizadas como uma única unidade. Um bloco de scripts pode aceitam argumentos e valores de retorno.|
|módulo de script|Um módulo do PowerShell de Windows cujo módulo de raiz é um ficheiro do módulo de script (. psm1). Um módulo de script pode ou não pode incluir um manifesto de módulo.|
|ficheiro de script de módulo|Um ficheiro que contém um script do Windows PowerShell. O script define os membros que exporta o módulo de script. Ficheiros de módulo de script têm a extensão de nome de ficheiro. psm1.|
|Shell|O interpretador de comandos que é utilizado para transmitir os comandos para o sistema operativo.|
|parâmetro de mudança|Um parâmetro que não assume um argumento.|
|Erro de terminação|Um erro que pára o Windows PowerShell de processamento do comando.|
|Transação|Uma unidade atômica de trabalho. O trabalho numa transação têm de ser concluído como um todo; Se qualquer parte da transação falhar, toda a transação falha.|
|ficheiro de tipos|Um ficheiro XML do Windows PowerShell com a extensão de .ps1xml de que expande as propriedades dos tipos de Microsoft .NET Framework no Windows PowerShell.|
|Verbo|A palavra que precede o hífen um nome de cmdlet do Windows PowerShell. O verbo descreve a ação que executa o cmdlet.|
|Windows PowerShell|Um shell da linha de comandos e tecnologia scripts baseados em tarefas que fornece controlo abrangente de administradores de TI e a automação do sistema de tarefas de administração.|
|Comando do Windows PowerShell|Os elementos num pipeline que fazer com que uma ação a ser realizada. Comandos do Windows PowerShell são digitados o teclado ou invocados programaticamente.|
|Ficheiro de dados do Windows PowerShell|Um ficheiro de texto que tem a extensão de nome de ficheiro. psd1. Windows PowerShell usa arquivos de dados para várias finalidades, como o armazenamento de dados de manifesto de módulo e armazenar as cadeias traduzidas para a internacionalização de script.|
|Unidade do Windows PowerShell|Uma unidade virtual que fornece acesso direto a um arquivo de dados. Pode ser definido por um fornecedor de Windows PowerShell ou criado na linha de comandos. Unidades criadas na linha de comandos são unidades de específico da sessão e são perdidas quando a sessão é fechada.|
|Windows PowerShell Integrated Scripting Environment (ISE)|Um aplicativo de host do Windows PowerShell que permite-lhe para executar comandos e escrever, testar e depurar scripts num ambiente amigável, a sintaxe de cores, compatível com Unicode.|
|Módulo do Windows PowerShell|Uma unidade autônoma reutilizável que lhe permite partição, organizar e abstrair o código do Windows PowerShell. Um módulo pode conter cmdlets, provedores, funções, variáveis e outros tipos de recursos que podem ser importados como uma única unidade.|
|Fornecedor de Windows PowerShell|Um com base no .NET Framework programa da Microsoft que disponibiliza os dados num armazenamento de dados especializados no Windows PowerShell para que possa ver e geri-lo.|
|Script do Windows PowerShell|Um script que é escrito no idioma do Windows PowerShell.|
|Ficheiro de script do Windows PowerShell|Um ficheiro que tenha a extensão. ps1 e que contém um script que é escrito no idioma do Windows PowerShell.|
|Snap-in Windows PowerShell|Um recurso que define um conjunto de cmdlets, fornecedores e tipos de Microsoft .NET Framework que podem ser adicionados ao ambiente do Windows PowerShell.|
|O fluxo de trabalho do Windows PowerShell|Um fluxo de trabalho é uma sequência de passos programados e ligados que efetuam tarefas de longa execução ou requerem a coordenação de vários passos em vários dispositivos ou nós geridos. O fluxo de trabalho do Windows PowerShell permite que os profissionais de TI e os programadores criar sequências de atividades de gestão de dispositivos ou tarefas únicas dentro de um fluxo de trabalho, como fluxos de trabalho. O fluxo de trabalho do Windows PowerShell permite-lhe adaptar e executar scripts do Windows PowerShell e arquivos XAML como fluxos de trabalho.|