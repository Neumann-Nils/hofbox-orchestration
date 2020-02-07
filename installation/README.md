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
