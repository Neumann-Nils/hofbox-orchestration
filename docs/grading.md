TODO: Korrekturlesen


Das Bewertungssystem für den allgemeinen Systemzustand unterteilt sich in vier Teile:
 - Bewerung der einzelnen Komponenten (CPU-Temperatur, CPU-Auslastung, RAM-Auslastung, Speicherbelegung)
 - Einen "Bewertungsfaktor" mit einbeziehen, welcher bestimmt, wie stark sich die Bewertung einer Komponente auf die Gesamtwertung auswirkt
 - Umrechnung vom Wertebereich 0 - 600 (0 > 600) in den Wertebereich 0 - 100 (100 > 0)
 - Definition der Abstufungen von A+ bis F (A > F)

Die Bewertung der CPU-Auslastung erfolgt über drei Zeiträume:
 - Auslastung der letzten 60 Sekunden
 - Auslastung der letzten 5 Minuten
 - Auslastung der letzten 15 Minute

Diese drei Zeiträume werden in betracht gezogen, um kurzzeitige Auslastungsspitzen, z.B. durch das Laden der Seite oder anderweitigen Ereignissen, in der Bewertung abzufedern. Ein sich ständig verändernder Wert durch solche Auslastungsspitzen kann den Benutzer verunsichern, obwohl das System einwandfrei funktioniert.
Solange die CPU-Auslastung unter 50% liegt ist alles in Ordnung, da dem System noch das Doppelte der momentan genutzten Rechenleistung zu Verfügung steht. Ab >50% CPU-Auslastung steigt die Wertung langsam an. Für eine Auslastung über 50% in den letzten 60 Sekunden können maximal 150 von 600 Punkten gesammelt werden. Liegt die CPU-Auslastung bereits seit 5 Minuten über 50%, wird dieser Wert verdoppelt, es können also maximal 300 von 600 Punkten gesammelt werden. Liegt die CPU-Auslastung nun mehr als 15 Minuten über 50% wird der Wert insgesammt vervierfacht, es können also bis zu 600 Punkte gesammelt werden. 600 Punkte können nur dann erreicht werden, wenn die CPU-Auslastung in den letzten 15 Minuten dauerhaft über 90% lag.

Die normale Betriebstemperatur eines Raspberry Pi's liegt ca. um die 50-60°C (siehe untenstehende Links). Wir haben uns dazu entschiede die Wertung ab einer Temperatur von 55°C beginnen zu lassen. In 5°C-Schritte steigt nun der Wert, bis er bei mehr als 85°C den Maximalwert von 600 Punkten erreicht hat. Eine CPU-Temperatur von mehr als 85°C wird als schlecht erachtet. Trotz bestehender Schutzmechanismen sollte der Nutzer dringend Maßnahmen ergreifen, um die CPU-Temperatur zu senken. Hohe Hardware-Temperaturen verkürzen die Lebendauer dieser.

Die Bewertung der RAM-Auslastung ist sehr simpel: Ab >50% Auslastung steigt die Wertung langsam an. Je höher die Auslastung, desto schneller steigt die Wertung an. Dieses Steigungsverhalten ist daher sinnvoll, da der Arbeitsspeicher eine signifikante Rolle in einem Computersystem hat. Steht nicht genügend Arbeitsspeicher zur Verfügung, können Prozesse nicht mehr richtig arbeiten.

Die Bewertung der Speicherbelegung ist ebenfalls sehr simpel: Ab einer Auslastung über 50% steigt die Wertung langsam an. Der Unterschied zur Bewertung der RAM-Auslastung ist jener, dass die Wertung erst ab >90% sehr stark steigt. Festplattenspeicher wächst unter normalen Umständen nicht rasant an und ist meist auch in größeren Kapazitäten vorhanden, als z.B. RAM, wodurch der prozentuale Anteil der Auslastung wesentlich mehr Speicher repräsentiert. So sind z.B. bei eriner 100 GB Festplatte mit einer Speicherbelegung von 80% noch 20GB vorhanden: Für unser Anwendungsszenario mehr als ausreichend.



Für jede Bewertung existiert ein eigener Bewertungsfakter, welcher bestimmt, wie stark die jeweilige Bewertung in die Gesamtwertung einfließt. Dieser Bewertungsfaktor liegt typischerweise zwischen 0 (0%) und 1 (100%). Vor der Konvertierung in den Wertebereich 0 - 100 wird jede einzelne Bewertung mit ihrem Bewertungsfaktor multipliziert.



Die Umrechnung aus dem Wertebereicht 0 - 600 in 0 - 100 erfolgt nach dieser Formel:
100 - ((Wertung / (600 * (cpuGradingFactor + ramGradingFactor + diskGradingFactor + temperatureGradingFactor))) * 100);



Die Abstufung erfolgt in 5-Punkte-Schirtten:
 - 100-95 Punkte: A+
 -  94-90 Punkte: A
 -  89-85 Punkte: B+
 -  84-80 Punkte: B
 -  79-75 Punkte: C+
 -  74-70 Punkte: C
 -  69-60 Punkte: D
 -  59-50 Punkte: E
 -  49- 0 Punkte: F



Anpassungen am Bewertungsalgorithmus können in der app/docker/helpers/gradingHelper.js gemacht werden.

Nützliche Links:

CPU temperature for Raspberry Pi:
 - https://linuxhint.com/raspberry_pi_temperature_monitor/
 - https://www.raspberrypi.org/forums/viewtopic.php?t=243500
 
=> Normal: ~50°C, critical: >85°C
