# <a name="ws-management-wsman-remoting-in-powershell-core"></a>Comunicação Remota do WS-Management (WSMan) no PowerShell Core

## <a name="instructions-to-create-a-remoting-endpoint"></a>Instruções para criar um ponto final de gestão remota

O pacote de núcleo do PowerShell para o Windows inclui um plug-in de WinRM (`pwrshplugin.dll`) e um script de instalação (`Install-PowerShellRemoting.ps1`) no `$PSHome`.
Estes ficheiros ativar o PowerShell aceitar ligações remotas de entrada do PowerShell quando o seu ponto final está especificado.

### <a name="motivation"></a>Motivação

Uma instalação do PowerShell pode estabelecer sessões de PowerShell para computadores remotos utilizando `New-PSSession` e `Enter-PSSession`.
Para ativá-la para aceitar ligações remotas a receber do PowerShell, o utilizador tem de criar um ponto de final de comunicação remota do WinRM.
Este é um explícito optar ativamente por participar no cenário em que o utilizador executa Install-PowerShellRemoting.ps1 para criar o ponto final do WinRM.
O script de instalação é uma solução de curta duração, até que iremos adicionar funcionalidades adicionais para `Enable-PSRemoting` para efetuar a mesma ação.
Para obter mais detalhes, consulte problema [#1193](https://github.com/PowerShell/PowerShell/issues/1193).

### <a name="script-actions"></a>Ações de script

O script

1. Cria um diretório para o plug-in dentro %windir%\System32\PowerShell
1. Copia pwrshplugin.dll para essa localização
1. Gera um ficheiro de configuração
1. Regista ou plug-in com WinRM

### <a name="registration"></a>Registo

O script tem de ser executado dentro de uma sessão do PowerShell de nível de administrador e é executado em dois modos.

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a>Executado pela instância do PowerShell que serão registados

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a>Executado por outra instância do PowerShell em nome de instância que serão registados

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

Por exemplo:

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

**Nota:** o script de registo do sistema de interação remota reiniciará WinRM, pelo que todas as sessões PSRP existentes irão terminar imediatamente após o script é executado. Se executar durante uma sessão remota, isto irá terminar a ligação.

## <a name="how-to-connect-to-the-new-endpoint"></a>Como ligar para o novo ponto final

Criar uma sessão do PowerShell para o novo ponto de final do PowerShell, especificando `-ConfigurationName "some endpoint name"`. Para ligar à instância do PowerShell de exemplo acima, utilize qualquer um dos seguintes itens:

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

Tenha em atenção que `New-PSSession` e `Enter-PSSession` invocações que não especificam `-ConfigurationName` destina-se o ponto final do PowerShell predefinido, `microsoft.powershell`.