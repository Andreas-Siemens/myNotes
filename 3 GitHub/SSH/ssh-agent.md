## Manueller Start

In einem neuen PowerShell-Fenster mit Administratorrechten die folgenden Befehle eingeben:

```powershell
# start the ssh-agent in the background
Get-Service -Name ssh-agent | Set-Service -StartupType Manual
Start-Service ssh-agent
```
## Automatischer Start

Du kannst den ssh-agent automatisch starten, wenn Du die Bash oder Git-Shell öffnest. Kopiere die folgenden Zeilen und fügen sie in deine ~/.profile- oder ~/.bashrc-Datei in der Git-Shell ein:

```bash
env=~/.ssh/agent.env

agent_load_env () { test -f "$env" && . "$env" >| /dev/null ; }

agent_start () {
    (umask 077; ssh-agent >| "$env")
    . "$env" >| /dev/null ; }

agent_load_env

# agent_run_state: 0=agent running w/ key; 1=agent w/o key; 2=agent not running
agent_run_state=$(ssh-add -l >| /dev/null 2>&1; echo $?)

if [ ! "$SSH_AUTH_SOCK" ] || [ $agent_run_state = 2 ]; then
    agent_start
    ssh-add
elif [ "$SSH_AUTH_SOCK" ] && [ $agent_run_state = 1 ]; then
    ssh-add
fi

unset env
```

Wenn Du nun Git Bash zum ersten Mal ausführst, wirst Du zur Eingabe deiner Passphrase aufgefordert:

```shell
> Initializing new SSH agent...
> succeeded
> Enter passphrase for /c/Users/YOU/.ssh/id_rsa:
> Identity added: /c/Users/YOU/.ssh/id_rsa (/c/Users/YOU/.ssh/id_rsa)
> Welcome to Git (version 1.6.0.2-preview20080923)
>
> Run 'git help git' to display the help index.
> Run 'git help <command>' to display help for specific commands.
```
## SSH Schlüssel hinzufügen

Füge in einem Terminalfenster ohne erweiterte Rechte deinen privaten SSH-Schlüssel zum ssh-agent hinzu:

```powershell
ssh-add c:/Users/YOU/.ssh/id_ed25519
```

#SSH #SSH-Agent #SSH-Key 