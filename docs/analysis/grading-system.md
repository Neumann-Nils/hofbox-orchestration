# Auswahl eines Bewertungssystems
## Einleitung
Ziel dieser Arbeit ist die Konzeption und Entwicklung einer Orchestrationslösung, welche es fachfremden Anwendern ermöglicht, lokale und containerbasierte Anwendungen auf eigenen (Edge-)Servern zu betreiben und den Gesundheitsstatus des Clusters zu überwachen. Dabei steht vor allem die Benutzbarkeit durch nicht technisch-versierte Anwender im Fokus. Daher soll die Anwendung einfach und intuitiv zu bedienen sein und den Benutzer nicht mit technischen Details überfordern.

Der Fokus liegt dabei auf einer vereinfachten Oberfläche. Ein Teil der Oberfläche präsentiert den Gesundheitsstatus des Clusters, wobei in einem einzigen Wert der aggregierten Status des Clusters bewertet werden soll.

In diesem Text möchten wir verschiedene Bewertungssysteme vorstellen und in den Kontext der angestrebten Orchestrationslösung stellen. Dabei wollen wir vor allem ein numerische Bewertungssystem mit Zahlen zwischen `1` und `100` sowie ein alphabetische Bewertungssystem von `A` bis `F` betrachten. Im besonderen Fokus liegt hierbei die Verständlichkeit durch fachfremde Anwender (z.B. dem Landwirt).

## Hauptteil
Wir betrachten die zwei folgenden Bewertungssystem:
1. Ein numerisches Bewertungssystem (z.B. von `1` bis `100`)
2. Ein alphabetisches Bewertungssystem (z.B. von `A` bis `F`)

Zuerst wollen wir darauf hinweisen, dass es einfach ist die beiden Bewertungssysteme "umzurechnen". Beispielsweise könnte folgende Umrechnung vorgenommen werden:

| Grade | Score |
|-------|--------|
| A | 90-100 |
| B | 80-89 |
| C | 70-79 |
| D | 51-69 |
| F | <50 |

Es gibt einige Beispiele, in dem ein numerisches Bewertungssytem benutzt wird, darunter Dienste die Webseiten bewerten (siehe z.B. https://website.grader.com/). Der Vorteil dieses Verfahrens ist die feine Granularität und die Linearität der Bewertung. Zum einen kann man kleine Unterschiede durch kleine Veränderungen der Bewertung ausdrücken (z.B. indem man die Bewertung um `1` verringert). Zum anderen ist eine `93` genau `3` Punkte besser als eine `90` sowie eine `84` genau `3` Punkte besser als eine `81` ist.

Das alphabetische Bewertungssystem wird oft in Schulen und Universitäten angewandt (darunter beispielsweise auch das amerikanische Schulsystem). Dieses Verfahren bietet keine besondere Granularität, wobei durch die Einführung von Zwischenwerten wie z.B. `A+` oder `C-` die Granularität erhöht werden kann. Weiterhin bietet dieses System keine echte Linearität ein `B` ist nicht in gleichem Maße besser als ein `B`, wie ein `D` besser als ein `F` ist. Dies liegt an den unterschiedlichen "Größen" der Stufen.

Das alphabetiche Bewertungssystem hat einen entscheidenden Vorteil; es bietet eine übersichtliche Darstellung des Systemstatusses. Ein  fachfremder Nutzer wird keinen großen Unterschied zwischen einer `91` und einer `87` sehen. Jedoch ist der Unterschied zwischen einem `A` und einem `B` eindeutig. Der Bezug zu dem alphabetischen Bewertungssystem für fachfremde Benutzer ist besonders gegeben, da den Stufen oft Begriffe zugeordnet werdern: So wird ein `A` als "sehr gut" und ein `B` als "gut" verstanden. Einen solchen Zusammenhang gibt es in dem numerischen Bewertungssystem nicht.

## Fazit
Zusammenfassend bietet das numerische Bewertungssystem eine bessere Granularität und Linearität. Für fachfremde Nutzer sind diese Eigenschaften von geringer Bedeutung. Wichtiger ist die Verständlichkeit, welche bei einem alphabetischen Bewertungsssytem im Vordergrund steht.

Daher ist es sinnvoll, ein alphabetisches Bewertungssystem zu verwenden, welches beispielsweise mit Zwischenwerten (z.B. `B+`) arbeitet und durch fabliche Noancen den Bewertungscharakter der einzelnen Stufen verdeutlicht. 
