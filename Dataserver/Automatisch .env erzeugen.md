Die folgende Anleitung zeigt, wie man automatisch eine `.env` Datei erzeugt, die die UID (User ID) und GID (Group ID) des aktuellen Benutzers enthält. Nützlich ist sie z.B. für eine Docker Compose Datei, damit der Container mit den rechten des aktuellen Benutzers ausgeführt wird.

Zunächst wird die Skriptdatei `generate-env.sh` erzeugt:

```shell
#!/bin/bash
echo "UID=$(id -u)" > .env
echo "GID=$(id -g)" >> .env
```

Dann wird sie ausführbar gemacht:

```shell
chmod +x generate-env.sh
```

Zum Schluss ausführen:

```shell
./generate-env.sh
```

Ergebnis: `.env` enthält die aktuelle UID und GID:

```shell
UID=1000
GID=1000
```

