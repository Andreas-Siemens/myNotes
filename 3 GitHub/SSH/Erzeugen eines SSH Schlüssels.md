Du kannst einen neuen SSH-Schlüssel auf deinem lokalen Rechner erzeugen. Nachdem Du den Schlüssel erzeugt hast, kannst Du den öffentlichen Schlüssel zu deinem Konto auf GitHub.com hinzufügen, um die Authentifizierung für Git-Vorgänge über SSH zu aktivieren.
## Schlüssel erzeugen

- Öffne die Git Bash
- Füge den unten stehenden Text ein, wobei Du die im Beispiel verwendete E-Mail-Adresse durch deine GitHub-E-Mail-Adresse ersetzen musst:
```shell
ssh-keygen -t ed25519 -C "your_email@example.com"
```
## Passphrase hinzufügen oder ändern 

Du kannst die Passphrase für einen vorhandenen privaten Schlüssel ändern, ohne das Schlüsselpaar neu zu erzeugen, indem Du den folgenden Befehl eingibst:
```shell
$ ssh-keygen -p -f ~/.ssh/id_ed25519
> Enter old passphrase: [Type old passphrase]
> Key has comment 'your_email@example.com'
> Enter new passphrase (empty for no passphrase): [Type new passphrase]
> Enter same passphrase again: [Repeat the new passphrase]
> Your identification has been saved with the new passphrase.
```

