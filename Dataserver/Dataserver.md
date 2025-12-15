## Allgemein

bla bla bla ...

| Username | Passwort     |
| -------- | ------------ |
| datauser | data2025     |
## Installation Docker

[Online Dokumentation Docker](https://docs.docker.com/)
### Set up Docker's apt repository

Before you install Docker Engine for the first time on a new host machine, you need to set up the Docker apt repository. Afterward, you can install and update Docker from the repository.

```Shell
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```
To install the latest version, run:

```shell
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
The Docker service starts automatically after installation. To verify that Docker is running, use:

```shell
sudo systemctl status docker
```

## Install Portainer CE

[Online Dokumentation Portainer](https://docs.portainer.io/)

To install using Docker Compose create a `portainer-compose.yaml` file with the following contents:

```yaml
version: '3'
services:
  portainer:
    container_name: portainer
    image: portainer/portainer-ce:lts
    restart: always
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
      - portainer_data:/data
    ports:
      - 9443:9443

volumes:
  portainer_data:
    name: portainer_data

networks:
  default:
    name: portainer_network
```
Nachdem Sie die Compose-Datei erstellt oder heruntergeladen haben, können Sie sie mit dem folgenden Befehl bereitstellen:

```shell
sudo docker compose -f portainer-compose.yaml up -d
```
Nachdem die Installation abgeschlossen ist, können Sie sich bei Ihrer Portainer Server-Instanz anmelden, indem Sie einen Webbrowser öffnen und folgende Adresse aufrufen:

```shell
https://localhost:9443
```
Ersetzen Sie localhost bei Bedarf durch die entsprechende IP-Adresse oder den FQDN und passen Sie den Port an, wenn Sie ihn zuvor geändert haben.

### Passwörter

| Username | Passwort     |
| -------- | ------------ |
| admin    | PW!admin2025 |
| datauser | data2025     |
[Link zu Portainer](https://192.168.178.36:9443)
## Installation Gitlab

[Online Dokumentation Gitlab](https://docs.gitlab.com/install/docker/)

Docker Compose File:

```yaml
services:
  web:
    image: 'gitlab/gitlab-ee:latest'
    restart: always
    hostname: '192.168.178.36'
    container_name: gitlab-ee
    environment:
      GITLAB_ROOT_EMAIL: "admin@localhost"
      GITLAB_ROOT_PASSWORD: "PW!admin2025"
      GITLAB_OMNIBUS_CONFIG: |
        external_url 'http://192.168.178.36:8929'
    ports:
      - '8929:8929'
      - '443:443'
      - '22:22'
    volumes:
      - '/env/gitlab/config:/etc/gitlab'
      - '/env/gitlab/logs:/var/log/gitlab'
      - '/env/gitlab/data:/var/opt/gitlab'
```

### Default Root Passwort

Der Standardbenutzername ist root, der standardmäßig festgelegt ist. Um das Passwort zu erhalten, müssen Sie einen einfachen Docker-Befehl innerhalb des laufenden GitLab-Containers ausführen.

Rufen Sie zunächst die Details des laufenden Containers mit dem folgenden Befehl ab.

```shell
sudo docker ps | grep gitlab-ee
```
Die Ausgabe kann folgendermaßen aussehen:
```shell
221077d4a326   gitlab/gitlab-ee:latest
```
Kopieren Sie die Container-ID 221077d4a326, öffnen Sie ein neues Terminal und führen Sie diesen Befehl aus:
```shell
sudo docker exec -it 4009bc9fee22 cat /etc/gitlab/initial_root_password
```

## Installation Gitea

[Online Hilfe zur Installation](https://docs.gitea.com/installation/install-with-docker)

Docker Compose File:

```yaml
---
```
