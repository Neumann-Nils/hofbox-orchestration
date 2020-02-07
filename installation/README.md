# Installation

Die offizielle Anleitung zur Installation von Portainer ist hier zu finden: https://portainer.readthedocs.io/en/stable/deployment.html


$ docker volume create hofbox_data

$ docker run -d -p 9000:9000 -p 8000:8000 --name HofBox --restart always -v /var/run/docker.sock -v hofbox_data:/data portainer/portainer


https://portainer.readthedocs.io/en/stable/contribute.html

Installation der grundlegenden Abhängigkeiten: git, yarn, Go (>= 1.11), NodeJS (>= 6), Docker

$ sudo apt install git yarn golang nodejs docker docker-compose

Git-Repository klonen:

$ git clone https://github.com/Neumann-Nils/portainer


Go-Verzeichnis erstellen und verlinken:

$ mkdir -p ${GOPATH}/src/github.com/portainer

$ ln -s ${PWD}/portainer ${GOPATH}/src/github.com/portainer/portainer


oder


$ mkdir -p $~/go/src/github.com/portainer

$ ln -s ${PWD}/portainer ~/go/src/github.com/portainer/portainer


Patch anwenden:

$ cd portainer

$ ./patch.sh



# Mögliche Probleme und Lösungen:

Es könnte sein, dass folgendes Problem auftritt: Bei der Anwendung des Patchs kann ein Fehler von yarn auftreten, dass das Verzeichnis 'build' nicht gefunden wurde.

Lösung von StackOverflow: https://stackoverflow.com/questions/46013544/yarn-install-command-error-no-such-file-or-directory-install

Lösung: Die Programme cmdtest und yarn entfernen, das offizielle yarn-Repository hinzufügen und yarn erneut installieren.

$ sudo apt remove cmdtest

$ sudo apt remove yarn

$ curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -

$ echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list

$ sudo apt-get update

$ sudo apt-get install yarn
