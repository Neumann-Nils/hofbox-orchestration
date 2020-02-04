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

# Implementierung eines Bewertungssystems
Im folgenden beschreiben wir die Implementierungsentscheidungen unseres Bewertungssystems. Das Bewertungssystem für den allgemeinen Systemzustand unterteilt sich in vier Komponenten:
1. Bewertung der einzelnen Komponenten (CPU-Temperatur, CPU-Auslastung, RAM-Auslastung, Speicherbelegung)
2. "Bewertungsfaktor", welcher die Gewichtung der Bewertung einzelner Komponente in der Gesamtwertung definiert
3. Umrechnung vom Wertebereich `0 - 600` (wobei `0` der beste und `600` der schlechteste Wert ist) in den Wertebereich `0 - 100` (wobei `100` der beste und `0` der schlechteste Wert ist)
4. Definition der Abstufungen von `A+` bis `F` (wobei `A+` der beste und `F` der schlechteste Wert ist)

## Bewertung einzelner Komponenten
Die Bewertung der **CPU-Auslastung** erfolgt über drei Zeiträume:
- Auslastung der letzten 60 Sekunden
- Auslastung der letzten 5 Minuten
- Auslastung der letzten 15 Minute

Diese drei Zeiträume werden betrachtet, um kurzzeitige Auslastungsspitzen (z.B. durch das Laden der Seite) in der Bewertung abzufedern. Ein sich ständig verändernder Wert durch solche Auslastungsspitzen kann den Benutzer verunsichern. Eine CPU-Auslastung unter 50% wird als unkritisch betrachtet, da dem System noch mehr als die Hälfte der Rechenleistung zu Verfügung steht. Ab 50% CPU-Auslastung steigt die Wertung langsam an. Für eine Auslastung über 50% in den letzten 60 Sekunden können maximal 150 von 600 Punkten gesammelt werden. Liegt die CPU-Auslastung bereits seit 5 Minuten über 50%, wird dieser Wert verdoppelt (es können also maximal 300 von 600 Punkten gesammelt werden). Liegt die CPU-Auslastung nun mehr als 15 Minuten über 50% wird der Wert insgesammt vervierfacht (es können also bis zu 600 Punkte gesammelt werden). 600 Punkte können nur dann erreicht werden, wenn die CPU-Auslastung in den letzten 15 Minuten dauerhaft über 90% lag.

Die normale Betriebstemperatur (**CPU-Temperatur**) eines Raspberry Pi's liegt zwischen 50-60°C. Wir haben uns dazu entschieden, mit der Wertung ab einer Temperatur von 55°C zu beginnen. In 5°C-Schritte steigt nun der Wert, bis er bei mehr als 85°C den Maximalwert von 600 Punkten erreicht hat. Eine CPU-Temperatur von mehr als 85°C wird als bedenklich erachtet. Trotz bestehender Schutzmechanismen sollte der Nutzer dringend Maßnahmen ergreifen, um die CPU-Temperatur zu senken. Hohe Hardware-Temperaturen verkürzen deren Lebendauer.

Die Bewertung der **RAM-Auslastung** ist wie folgt definert: Ab >50% Auslastung steigt die Wertung zuerst linear an. Je höher die Auslastung, desto schneller steigt die Wertung an. Dieses Steigungsverhalten ist sinnvoll, da der Arbeitsspeicher eine signifikante Rolle in einem Computersystem hat. Steht nicht genügend Arbeitsspeicher zur Verfügung, können Prozesse nicht mehr richtig arbeiten.

Die Bewertung der **Speicherbelegung** erfolgt nach dem gleichen Schema: Ab einer Auslastung über 50% steigt die Wertung zuerst linear an. Im Unterschied zur Bewertung der RAM-Auslastung, steigt die Wertung erst ab >90% sehr stark. Festplattenspeicher wächst unter normalen Umständen nicht rasant an und ist meist auch in größeren Kapazitäten vorhanden, wodurch der prozentuale Anteil der Auslastung wesentlich mehr Speicher repräsentiert.

## "Bewertungsfaktor"
Für jede Bewertung existiert ein eigener Bewertungsfaktor. Dieser bestimmt, wie stark die jeweilige Bewertung in die Gesamtwertung des Sytems einfließt. Dieser Bewertungsfaktor liegt typischerweise zwischen `0` (0%) und `1` (100%). Vor der Konvertierung in den Wertebereich `0 - 100` wird jede einzelne Bewertung mit ihrem Bewertungsfaktor multipliziert.

## Umrechnung vom Wertebereich
Die Umrechnung aus dem Wertebereicht `0 - 600` in `0 - 100` erfolgt nach folgender Formel:
```
100 - ((Wertung / (600 * (cpuGradingFactor + ramGradingFactor + diskGradingFactor + temperatureGradingFactor))) * 100)
```

## Umwandlung in ein alphabetisches Bewertungssystem
Die letzendliche Abstufung erfolgt in 5-Punkte-Schirtten. Das Bewerungssystem beginnt bei ´A+´ und endet bei `F`:

| Grade | Score |
|-------|--------|
| A+ | 95-100 |
| A | 94-90 |
| B+ | 85-89 |
| B | 80-84 |
| C+ | 75-59 |
| C | 70-74 |
| D | 60-69 |
| E | 50-59 |
| F | <50 |

## Anmerkungen
Anpassungen am Bewertungsalgorithmus können in der Datei `app/docker/helpers/gradingHelper.js` gemacht werden.

Verwendete Ressourcen sind unter anderem:
- CPU temperature for Raspberry Pi (=> Normal: ~50°C, critical: >85°C)
  - https://linuxhint.com/raspberry_pi_temperature_monitor/
  - https://www.raspberrypi.org/forums/viewtopic.php?t=243500
 
