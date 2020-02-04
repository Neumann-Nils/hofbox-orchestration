# Digitale Hofbox - Orchestrationslösung
## Motivation
Reuter et al. [[Reuter18](https://dl.gi.de/bitstream/handle/20.500.12116/16930/Beitrag_330_final__a.pdf?sequence=1&isAllowed=y)] zeigen auf, dass der Landwirtschaft als kritische Infrastruktur und der notwendigen Auseinandersetzung mit den Sicherheitsaspekten der Technologien nur wenig Aufmerksamkeit eingeräumt wird. Diverse Ansätze der IT-Sicherheit fokussieren große Konzerne und nicht kleinere Unternehmen. Dabei sollte besonders der Ausfallsicherheit der landwirtschaftlichen Produktion beziehungsweise deren Resilienz besonderer Bedeutung gegeben werden, da die Landwirtschaft von existenzieller Bedeutung für eine Gesellschaft ist [[Reuter19](https://dl.gi.de/bitstream/handle/20.500.12116/23086/GIL_2019_Reuter_177-182.pdf?sequence=1&isAllowed=y)]. Reuter et al. plädieren daher dafür, `"resiliente Systeme zu erstellen, und gleichzeitig deren einfache Nutzbarkeit in den Vordergrund zu rücken".` [[Reuter18](https://dl.gi.de/bitstream/handle/20.500.12116/16930/Beitrag_330_final__a.pdf?sequence=1&isAllowed=y)].

## Zielsetzung
In modernen Infrastrukturen erlauben es containerbasierte Technologien, Anwendungen einfach zu verwalten und zu skalieren. Für die Orchestration dieser Anwendung gibt es viele verschiedene Anwendungen. Diese Werkzeuge erlauben es, neue Container zu erzeugen und den Status des eigenen Clusters zu überwachen. Aber die Oberflächen dieser Management-Werkzeuge werden hauptsächlich für Administratoren und technisch-versierte Anwender konzipiert. Sie bieten viele Möglichkeiten und einen detaillierten Einblick in den Gesundheitszustands des Systems. Für fachfremde Nutzer, wie zum Beispiel Landwirte, sind die komplexen und vielen Möglichkeiten ungeeignet. Die Management-Werkzeuge bieten einen ungewollten Informationsüberfluss.

Es muss dem Landwirt auf eine einfache Art und Weise ermöglicht werden, in einem einheitlichen Prozess neue Anwendungen zu installieren und den Status seines aktuellen Clusters zu überwachen. Ziel dieser Arbeit ist daher die Konzeption und Entwicklung einer solchen Orchestrationslösung, welche es fachfremden Anwendern ermöglicht, lokale und containerbasierte Anwendungen auf eigenen (Edge-)Servern zu betreiben und den Gesundheitsstatus des Clusters zu überwachen. Dabei steht vor allem die Benutzbarkeit durch nicht technisch-versierte Anwender im Fokus. Daher soll die Anwendung einfach und intuitiv zu bedienen sein und den Benutzer nicht mit technischen Details überfordern.

## Projektübersicht
In dem Ordner [docs](/docs/) werden alle wichtigen Dokumente und Informationen gesammelt. Darunter befinden sich folgende Dokuente:
- [Anforderungsanalyse](/docs/analysis/requirement-analysis.md)
- [Anwendungsfälle](/docs/analysis/use-cases.md)
- [Analyse bestehender Orchestrationslösungen](/docs/analysis/solution-analysis.md)
- [Analyse bezüglich des Übergangs in den Experten-Modus](/docs/analysis/expert-mode.md)
- [Analyse und Implementation des Bewertungssystems](/docs/analysis/grading-system.md)

Im Ordner [patch](/patch/) befindet sich die eigentlich Orchestrationslösung und eine [Anleitung](/patch/installation.md), um diese zu installieren.

## Credits
Dieses Projekt wurde im Rahmen des Praktikums "Verantwortung und Sicherheit in der Informatik" bzw. Projektpraktikums "Interaktive resiliente Informationstechnik" im Wintersemester 2019/2020 an der TU Darmstadt von Kevin Küchler und Nils Neumann erstellt.
