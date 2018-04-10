---
ms.date: 06/05/2017
keywords: PowerShell, o cmdlet
title: Glossário do Windows PowerShell
ms.assetid: b0f88cbe-cb83-4912-a301-184534cb35c7
ms.openlocfilehash: fd15667939fd9b3ea705806686b626645519588a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2018
---
# <a name="windows-powershell-glossary"></a>Glossário do Windows PowerShell


|Termo|Definição|
|--------|--------------|
|módulo binário|Um módulo do Windows PowerShell módulo cuja raiz é um ficheiro de módulo binários (. dll). Um módulo binário pode ou não pode incluir um manifesto de módulo.|
|parâmetro comum|Um parâmetro que é adicionado a todos os cmdlets, funções avançadas e fluxos de trabalho pelo motor do Windows PowerShell.|
|origem de ponto|No Windows PowerShell, a iniciar um comando, escrevendo um ponto e um espaço antes do comando. Os comandos dot tenham origem a executam no âmbito atual, em vez de um novo âmbito. Quaisquer variáveis, aliases, funções ou unidades que comando cria são criadas no âmbito atual e estão disponíveis aos utilizadores quando o comando é concluído.|
|módulo dinâmico|Um módulo de que existe apenas na memória. Os cmdlets New-Module e importar-PSSession criar módulos dinâmicos.|
|parâmetro dinâmico|Um parâmetro que é adicionado a um cmdlet do Windows PowerShell, a função ou script em determinadas condições. Os cmdlets, funções, fornecedores e scripts, podem adicionar os parâmetros dinâmicos.|
|formatação do ficheiro|Um ficheiro XML do Windows PowerShell com o. a extensão de format.ps1xml e que define a forma como o Windows PowerShell apresenta um objeto com base no respetivo tipo de .NET Framework.|
|Estado da sessão global|O estado da sessão que contém os dados que esteja acessíveis para o utilizador de uma sessão do Windows PowerShell.|
|anfitrião|A interface que utiliza o motor do Windows PowerShell para comunicar com o utilizador. Por exemplo, o anfitrião Especifica a forma como os pedidos são processados entre do Windows PowerShell e o utilizador.|
|aplicação de anfitrião|Um programa que carrega o motor do Windows PowerShell para o respetivo processo e utiliza-o para executar operações.|
|processamento do método de entrada|Um método que pode utilizar um cmdlet para processar registos recebe como entrada. Os métodos de processamento de entrada incluem o método BeginProcessing, o método ProcessRecord, o método EndProcessing e o método StopProcessing.|
|módulo de manifesto|Um módulo do Windows PowerShell que tenha um manifesto e cuja chave RootModule está vazio.|
|manifesto de módulo|Um Windows PowerShell ficheiro de dados (. psd1) que descreve o conteúdo de um módulo e que controla a forma como é processado um módulo.|
|Estado da sessão de módulo|O estado da sessão que contém os dados públicos e privados de um módulo do Windows PowerShell. Os dados privados neste estado de sessão não estão disponíveis para o utilizador de uma sessão do Windows PowerShell.|
|Erro de não interrupção|Um erro que não a interromperá do Windows PowerShell de continuar a processar o comando.|
|substantivo|A palavra que se segue o hífen num nome de cmdlet do Windows PowerShell. O substantivo descreve os recursos no qual o cmdlet funcione.|
|Conjunto de parâmetros|Um grupo de parâmetros que pode ser utilizado no mesmo comando, para executar uma ação específica.|
|pipe|No Windows PowerShell, para enviar os resultados do comando anterior como entrada para o seguinte comando no pipeline.|
|Pipeline|Uma série de comandos ligados por operadores de pipeline (&#124;) (ASCII 124). O operador de pipeline envia os resultados do comando anterior como entrada para o comando seguinte.|
|PSSession|Um tipo de sessão do Windows PowerShell que é criada, gerido e fechado pelo utilizador.|
|módulo de raiz|O módulo especificado na chave RootModule num manifesto de módulo.|
|Espaço de execução|No Windows PowerShell, o ambiente de funcionamento em que cada comando num pipeline é executado.|
|Bloco de script|No Windows PowerShell de programação idioma, uma coleção de instruções ou expressões que podem ser utilizadas como uma única unidade. Um bloco de script pode aceitar argumentos e valores devolvidos.|
|módulo de script|Um módulo do Windows PowerShell módulo cuja raiz é um ficheiro de módulo de script (. psm1). Um módulo de script pode ou não pode incluir um manifesto de módulo.|
|ficheiro de módulo de script|Um ficheiro que contém um script do Windows PowerShell. O script define os membros que exporta o módulo de script. Ficheiros de script do módulo de ter a extensão de nome de ficheiro. psm1.|
|shell|O interpretador de comandos que é utilizado para passar os comandos para o sistema operativo.|
|parâmetro|Um parâmetro que não requeira um argumento.|
|Erro de terminação|Um erro que para o Windows PowerShell do processamento do comando.|
|Transação|Uma unidade atómica do trabalho. O trabalho de uma transação têm de ser concluído como um todo; Se qualquer parte da transação falhar, toda a transação falha.|
|ficheiro de tipos|Um ficheiro XML do Windows PowerShell que tenha a extensão de .ps1xml e que expande as propriedades dos tipos de Microsoft .NET Framework no Windows PowerShell.|
|Verbo|A palavra que precede o hífen num nome de cmdlet do Windows PowerShell. O verbo descreve a ação que executa o cmdlet.|
|Windows PowerShell|Uma tecnologia scripting baseada em tarefas que fornece controlo abrangente de administradores de TI e a automatização do sistema de tarefas de administração e shell da linha de comandos.|
|Comando do Windows PowerShell|Os elementos de um pipeline causam uma ação a ser executadas. Comandos do Windows PowerShell são escritos no teclado ou invocados através de programação.|
|Ficheiro de dados do Windows PowerShell|Um ficheiro de texto que tenha a extensão de nome de ficheiro. psd1. O Windows PowerShell utiliza ficheiros de dados para vários fins tais como armazenar dados de manifesto do módulo e armazenar cadeias traduzidas de internacionalização de script.|
|Unidade do Windows PowerShell|Uma unidade virtual que fornece acesso direto para um arquivo de dados. Pode ser definido por um fornecedor de Windows PowerShell ou criado na linha de comandos. Unidades criadas na linha de comandos são específicos da sessão unidades e são perdidas quando a sessão é fechada.|
|Windows PowerShell Integrated Scripting Environment (ISE)|Uma aplicação de anfitrião do Windows PowerShell, que permite-lhe para executar comandos e de escrita, testar e depurar scripts num ambiente compatível com Unicode amigável, a sintaxe-colored.|
|Módulo do Windows PowerShell|Uma unidade reutilizável autónomo que lhe permite partição, organizar e separar o código do Windows PowerShell. Um módulo pode conter os cmdlets, fornecedores, funções, variáveis e outros tipos de recursos que podem ser importados como uma única unidade.|
|Fornecedor do Windows PowerShell|Um Microsoft baseada no .NET Framework programa que faz com que os dados num arquivo de dados especializadas disponível no Windows PowerShell para que possa ver e geri-lo.|
|Script do Windows PowerShell|Um script que é escrito no idioma do Windows PowerShell.|
|Ficheiro de script do Windows PowerShell|Um ficheiro que tenha a extensão. ps1 e que contenha um script que é escrito no idioma do Windows PowerShell.|
|Snap-in do Windows PowerShell|Um recurso que define um conjunto de tipos de Microsoft .NET Framework que podem ser adicionados ao ambiente do Windows PowerShell, fornecedores e cmdlets.|
|O fluxo de trabalho do Windows PowerShell|Um fluxo de trabalho é uma sequência de passos programados e ligados que efetuam tarefas de longa execução ou requerem a coordenação de vários passos em vários dispositivos ou nós geridos. O fluxo de trabalho do Windows PowerShell permite que os profissionais de TI e os programadores criar sequências de atividades de gestão de vários dispositivos ou tarefas únicas num fluxo de trabalho, como os fluxos de trabalho. O fluxo de trabalho do Windows PowerShell permite-lhe adaptar e executar scripts do Windows PowerShell e ficheiros XAML como fluxos de trabalho.|