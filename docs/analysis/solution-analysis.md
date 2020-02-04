# Analyse bestehender Lösungen
## [Gardener](https://github.com/gardener/gardener)
Gardener ist ein Open-Source Tool zur Verwaltung von Kubernetes Clustern, dessen Fokus auf großer Skalierbarkeit liegt. Auch bei einer Vielzahl von Containern soll die Verwaltung dieser einfach und schnell bleiben. Mit Hilfe des webbasierten Dashboards ist der Benutzer sowohl in der Lage den Zustand der einzelnen Cluster einzusehen, als auch einzelne Cluster zu überwachen und zu bearbeiten. Die Bereitstellung einer Applikation ist einfach und mit wenigen Klicks erledigt.
Gardener bietet verschiedene Cloud-Dienstleister zur Bereitstellung der Cluster an. Für unsere Zwecke ist dies nicht annehmbar, da die vorgegebene Infrastruktur lokal und nicht bei großen Cloud-Dienstleistern liegen soll. Für einen kostengünstigen, schnellen und einfachen Betrieb ist dies eine Lösungsmöglichkeit, jedoch birgt eine Auslagerung ein weiteres, schlecht kalkulierbares Risiko. Ein Ausfall der Infrastruktur kann immer passieren. Bei externen Anbietern ist der Nutzer auf diese angewiesen und ist selbst machtlos.

## [Rancher](https://github.com/rancher/rancher)
Rancher ist ein Software-Stack zu operationellen und sicheren Verwaltung von vielen Kubernetes Clustern über verschiedene Infrastrukturen hinweg. Es bietet eine Vielzahl an Informationen zu Clustern in einer visuell gut aufbereiteten Oberfläche, sodass der Benutzer einfach den Zustand seiner Cluster überwachen kann.
Rancher bietet eine “Backup and Disaster Recovery” Funktion, welche es dem Benutzer erlaubt, ganze Cluster oder einzelne Container zu sichern und später wiederherzustellen.
Der hohe Funktionsumfang kommt allerdings auch mit nicht annehmbaren Systemvoraussetzungen. Rancher benötigt mindestens 1GB freien Arbeitsspeicher, zuzüglich der Betriebssystem Ressourcen. Unsere Zielsysteme sind 1-Platinen-Computer, wie der Raspberry Pi. Diese bieten nicht viele Ressourcen. Der Raspberry Pi wird mit maximal 1GB Arbeitsspeicher ausgeliefert.

## [Cockpit Project](https://github.com/cockpit-project/cockpit)
Cockpit verfolgt einen größeren Ansatz und bietet direkt eine Systemverwaltung. Es ist möglich einzelne Rechner, Virtuelle Maschinen und Cluster zu verwalten. Die Oberfläche ist dabei sehr klar und strukturiert gehalten. Sie bereitet die Systeminformationen visuell gut auf und zeigt dem Benutzer schnell die wichtigsten Informationen.
Mit Cockpit lässt sich der Systemspeicher gut verwalten und auch Netzwerkressourcen einbinden (NetworkFileSystems).
Mit dem Docker-Plugin lassen sich Docker-Container erstellen und verwalten. Es ist möglich aus dem DockerHub Images herunterzuladen. Neue Images müssen entweder auf DockerHub hochgeladen oder lokal erstellt werden.

## [Portainer](https://github.com/portainer/portainer)
Portainer zielt auf die Verwaltung von Docker-Umgebungen ab. Es bietet die Möglichkeit lokale, als auch entfernte Docker Instanzen zu verwalten. Die leichte und gut strukturierte Weboberfläche bietet dem Nutzer einen schnellen Überblick über seine Cluster. Weiterhin erlaubt Portainer das Benutzen einer lokalen Image-Registry und das Verwalten von Backups.

## Fazit
Zusammenfassend sind Gardener und Rancher nicht für die geplante Orchestrationslösung geeignet. Gardner bietet nur die Möglichkiet Cluster bei Cloud-Dienstleistern zu erstellen und Rancher braucht zu viele Ressourcen, um es auf einen Rasberry Pi laufen zu lassen.

Im Vergleich zwischen Cockpit Project und Portainer haben wir uns für Portainer entschieden, da es die Möglichkeiten zur Benutzung einer lokalen Image-Registry bietet und auch das Verwalten von Backups nativ unterstützt.
