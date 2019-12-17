# Übergang in den Experten-Modus
## Einleitung
Ziel dieser Arbeit ist die Konzeption und Entwicklung einer Orchestrationslösung, welche es fachfremden Anwendern ermöglicht, lokale und containerbasierte Anwendungen auf eigenen (Edge-)Servern zu betreiben und den Gesundheitsstatus des Clusters zu überwachen. Dabei steht vor allem die Benutzbarkeit durch nicht technisch-versierte Anwender im Fokus. Daher soll die Anwendung einfach und intuitiv zu bedienen sein und den Benutzer nicht mit technischen Details überfordern.

Der Fokus liegt dabei auf einer vereinfachten Oberfläche. Dieser Anfänger-Modus soll die Entdeckbarkeit erhöhen und agiert nach dem Prinzip "see and point". Ein solcher Ansatz kann für Anfänger hilfreich sein, aber bietet eine niedrige Leistungsobergrenze [1].  Im Gegensatz zum Experten-Modus soll der Anfänger-Modus eine einfache Übersicht bieten und den Anwender zuerst nicht überfordern.

In unserem Anwendungsfall, der Konzeption und Entwicklung einer Orchestrationslösung, soll ein fachfremder Anwender im Anfänger-Modus beginnen und die Möglichkeit haben, in einen Experten-Modus zu wechseln, um mehr Informationen und Funktionalitäten freizuschalten. Dabei gibt es verschiedene Möglichkeiten, von dem Anfänger-Modus in den Experten-Modus zu wechseln. Daher sollen die verschiedenen Möglichkeiten zuerst herausgearbeitet und beschrieben werden. Danach sollen die Optionen verglichen und zuletzt eine Empfehlung im Anwendungsfall gegeben werden.

## Hauptteil
In dieser Arbeit stellen wir drei Möglichkeiten vor, in den Experte-Modus zu wechseln:
1. Ein Button auf der Oberfläche,
2. ein Prä- oder Suffix für die Domain (z.B. `expert.orchestration.de`), oder
3. eine Option in den Einstellungen.

### Vom Anfänger- zum Experten-Modus
Zuerst soll der Übergangsprozess von dem Anfänger-Modus in den Experten-Modus beschrieben werden. Dabei sollen Faktoren herausgearbeitet werden, die später auf die vorgestellten Möglichkeiten angewendet werden.

Während ein Anwender Erfahrung mit einer Oberfläche sammelt, geht er typischerweise durch drei Phasen [2]: (1) eine kognitive Phase, in der er durch visuelle Suche Befehle identifiziert, (2) eine assoziative Phase, in der er beginnt, Befehle zu verinnerlichen und (3) eine autonome Phase, in der er Befehle schnell und ohne große Aufmerksamkeit ausführt. Viele Anwender bestreiten während des neuartigen Lernprozesses nciht den Übergang in den Experten-Modus, da sie keine Fehler machen wollen [3].

Forscher haben viele Methoden vorgestellt, die Anfänger helfen sollen, diese Barrieren zu überkommen. Darunter Strategien wie Probedurchläufe im Expertenmodus, graduelle Erhöhung der Kosten im Anfänger-Modus oder Erinnerung an den Experten-Modus im angebrachten Kontext [5]. Besonders beliebt ist es dabei, den Anfänger Handlungsanweisungen und Rückmeldung zugeben [4], welche später entfernt werden können, wenn der Anwender mehr Erfahrung gesammelt hat. Diese Unterstützungsmechanismen sollen aber nicht weiter Teil der Arbeit sein, sollten aber für weitere Arbeiten vermerkt werden.

Anfänger oder unerfahrene Anwender schrecken vor einem Experten-Modus zurück, weil sie Angst haben Fehler zu machen [3]. Daher sollte der Übergang in den Experten-Modus bewusst geschehen und nur, wenn der Anwender die kognitive Phase überschritten hat (da er schon Erfahrung mit dem System sammeln konnte) [2]. Auf der eine Seite, sollte der Übergang zum Experten-Modus nicht schon in der kognitiven Phase übermäßig präsent sein. Auf der anderen Seite, sollte der Anwender beim Fortschreiten der kognitiven bzw. assoziativen Phase die Möglichkeit haben, den Übergang selbst zu initiieren und dabei im gewohnten Umfeld zu bleiben.

### Analyse der Transitionsmöglichkeiten
Als nächstes sollen die drei Transitionsmöglichkeiten genauer erläutert werden und deren Vor- bzw. Nachteile herausgearbeitet werden.

Beim **Button auf der Oberfläche** soll ein Button zum Wechsel in den Experten-Modus (und zurück) präsent auf der Oberfläche platziert werden. Zum Beispiel könnte der Button in der Statusleiste oben rechts verankert werden. Vorteil dieser Lösung ist die einfache Bedien- und Entdeckbarkeit. Für einen Anfänger ist es offensichtlich, wie man in den Experten-Modus wechselt. Diese einfache Bedienung birgt jedoch auch Gefahren. Befindet sich der Anwender noch in der kognitiven Phase und entdeckt die Funktionalitäten der Orchestrationslösungen, könnte er mit einem Wechsel in den Experten-Modus (z.B. aus explorativem Interesse) überfordert sein. Der eintretende Informationsüberfluss und die Vielzahl an Funktionen könnten den Anwender verunsichern und ihn auch in späteren Anwendungssituationen negativ beeinflussen. Daher ist ein zu einfacher und früher Wechsel, welcher ausversehen oder durch exploratives Interesse entsteht, zu vermeiden. Die Option eines Buttons auf der Oberfläche ist nicht die optimale Lösung.

Benutzt man einen **Prä- oder Suffix** für eine Domain, so wird der Experten-Modus durch das Modifizieren der Domain erreicht. Wenn man annimmt, dass beispielsweise die Domain der Orchestrationslösung `orchestration.de` ist, so könnte der Experten-Modus durch folgende Domain erreicht werden: `expert.orchestration.de`. Der Vorteil dieser Lösung ist, dass ein Anwender nur in den Experten-Modus wechseln kann, wenn er bewusst die Dokumentation gelesen hat und sich für diesen manuellen Wechsel entscheidet. Da der Anwender die Dokumentation gelesen hat, wird ihm auch schon Hilfestellungen bei den verschiedenen Funktionalitäten bereitgestellt. Es kann davon ausgegangen werden, dass der Anwender gezielt nach einer Funktionalität des Experten-Modus gesucht hat und daher auch auf die Komplexität des Modus-Wechsels vorbereitet ist. Auf der anderen Seite ist eine Exploration auf der Oberfläche nicht möglich. In keinen der drei Phasen (kognitiv, assoziativ und autonom) wird der Anwender auf die Funktionalität aufmerksam. Diese große Hürde könnte Anwender abschrecken, da es sie aus der gewohnten Umgebung entreißt (da der Übergang nicht über die Oberfläche initiiert wird) und die Angst verstärkt, Fehler in einer "neuen" Umgebung zu machen. Daher ist diese Lösung nicht optimal.

Führt man eine **Option in den Einstellungen** ein, welche es dem Anwender erlaubt, vom Anfänger- in den Expertenmodus zu wechseln, so kann der Wechseln im Kontext der gewohnten Oberfläche durchgeführt werden. Dem Anwender wird die Angst vor dem Wechsel in den Experten-Modus etwas genommen, da er immer noch mit den gewohnten Aktionen interagieren kann. Weiterhin ist die Option aber nicht direkt in der kognitiven Phase erkennbar und Bedarf einer bewussten Aktion. Der Wechsel wird daher bewusst durch den Anwender initiiert, um eine Funktion im Expertenmodus zu nutzen. Es bleibt die Gefahr, dass der Anwender mit der Vielzahl an Informationen und Funktionen überfordert ist. Jedoch bietet diese Lösung einen Mittelweg zwischen des Buttons auf der Oberfläche und des Prä-/Suffixes der Domain.

## Fazit
Zusammenfassend soll der Übergangsprozess von dem Anfänger-Modus in den Experten-Modus bewusst durch den Anwender initiiert werden. Dabei soll er nicht zu früh (z.B. in der kognitiven Phase) negative Erfahrungen mit dem Experten-Modus sammeln. Im Gegensatz dazu soll er aber auch nicht aus dem gewohnten Umfeld entrissen werden, was hohe Hürden und Ängste vor Fehlern forcieren könnte. Ein Mittelweg zwischen den Lösungen eines Buttons auf der Oberfläche und des Prä-/Suffixes der Domain bietet die Option in den Einstellungen, welche es dem Anwender erlaubt im gewohnten Umfeld in den Experten-Modus zu wechseln, aber ohne in Gefahr zu laufen, ungewollt oder zu früh in den Experten-Modus zu wechseln.

Für weitere Arbeiten biete sich eine Untersuchung von Hilfestellungen an, die den Übergang für den Anwender in den Experten-Modus erleichtern (z.B. Probedurchläufe, Erinnerungen im Anfänger-Modus oder allgemeine Hinweise). Für eine gute Bedienbarkeit könnte eine verknüpfte Dokumentation erstellt werden, welche Anwender für Funktionen Hilfestellungen liefert und in durch die Anwendung begleitet. 

## Literaturverzeichnis
[1] Ben Shneiderman. (1983). Direct Manipulation: A Step Beyond Programming Languages. Computer (16), 57-69.

[2] Paul Morris Fitts and Michael I. Posner (1967). Human performance.

[3] Carl Gutwin, Andy Cockburn, and Benjamin Lafreniere (2015). Testing the Rehearsal Hypothesis with Two FastTap Interfaces. In Proc. of GI. Canadian Information Processing Society, 223–231

[4] William Buxton (1986). Chunking and phrasing and the design of human-computer dialogues. In IFIP Congress. 475–480.

[5] Alix Goguey, Sylvain Malacria, Andy Cockburn, Carl Gutwin (2019). Reducing Error Aversion to Support Novice-to-Expert Transitions with FastTap. Proceedings of the 31st French-speaking conference on Human-Machine Interaction (IHM 2019), 1-10.
