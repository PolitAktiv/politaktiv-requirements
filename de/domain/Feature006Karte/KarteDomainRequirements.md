# Beschreibung aus fachlicher Sicht

Bei der Entwicklung soll schrittweise vorgegangen werden.
1. Schritt: Basis-Komponenten von Leaflet werden in Liferay integriert.
 1. Die Daten der Komponenten werden persistent gemacht.
 2. Einzelnen Funktionen werden Berechtigungen zugeteilt
 3. Die Basiskomponenten und zusätzlich ein einfaches Plug-In werden integriert
 4. Die Ergebnisse sind nicht zur Nutzung auf Produktiv gedacht.
2. Schritt: Die wichtigsten Grundkomponenten sind verfügbar:
 1. Karte mit möglichst hoher Detailtiefe (noch auszusuchen)
 2. Festlegung des Standardmittelpunktes
 3. Zeichnen von Polygonen (Figuren)
 4. Markieren von Orten (Markerfunktion)
 5. Beschriften von erstellten Objekten (Markern, Figuren)
 6. Ein- und Ausblenden von erstellten Objekten
3. Schritt: Zusätzliche Komponenten sind verfügbar:
 1. Indoor-Darstellung und Indoor-Zooming
 2. Import von fertigen Figuren (Plänen)
 3. Bookmarks (URL der Seite mit dem Kartenportlet plus geografische Bookmarks
 4. Import/Export aller Figuren einer Karte
 5. 3D-Darstellung (später)
 6. Übergang zu Google-Earth mit Walkthrough

#Schritt 1 - Version1 & Version2

Schritt 1 ist abnahmefähig, wenn folgende Bedingungen erfüllt sind:
1. Das Kartenportlet ist mit den folgenden Funktionen auf intermediate lauffähig.
2. Das Kartenportlet kann aus der Liste der verfügbaren Portlets auf eine Seite der Wahl eingebaut werden. Vorschlag für Namen: „PA-Karte V2“
3. Die Basis-Karte mit höchster Detailtiefe wird verwendet. Noch auszusuchen!
4. Als Skala für den Zoom werden (+,-,*) verwendet (keine Thermometer-Skala)
5. Das Portlet unterliegt als Ganzes den üblichen Berechtigungen (Anzeige, Hinzufügen, …), damit es auf intermediate versteckt werden kann:
6. Marker sind verfügbar und können (einfach) beschriftet werden.
7. Marker und deren Beschriftung sind persistent.
8. Dazu wird das Plug-In Bookmark verwendet wie im Beispiel am 10.7.15
9. Die Marker gehören zur Instanz des Portlets, nicht zur Site. Also: Ein zweites Portlet auf einer anderen Page der Site zeigt nicht dieselben Marker wie das erste Portlet.
10. Eine einstellbare persistente Grundeinstellung wird (noch) nicht erwartet.
11. Alles ist mit Code, der einem Built unterliegt, nicht in einem Hook realisiert.

Anm mje: Punkt 9 nochmals diskutieren! -> Wir schieben das nach Schritt3 (mom / jem 25.09.)

##Berechtigungen
Die Berechtigungen sind nicht zu grob und nicht zu fein abzustufen.
Die im Folgenden geschilderten Berechtigungen müssen nicht schon im Schritt 1 verfügbar sein. Sie sind spätestens dann erforderlich, wenn das Kartenportlet V2 poduktiv geht.
1. Installation und Anzeige des Karten-Portlets durch einen Liferay-Nutzer unterliegt der üblichen Berechtigung für die Nutzung von Portlets.
2. Es gibt die Berechtigung, das Portlet als Ganzes zu manipulieren (anzeigen, hinzufügen, konfigurieren, …) wie üblich in Liferay. Diese Berechtigungen sind bei den Funktionen abgelegt.
 1. Mit der Berechtigung „Anzeige“ (=Portlet anzeigen) ist verbunden:
Zoom verändern und Karte verschieben
 2. Mit der Berechtigung „Hinzufügen“ (Portlet hinzufügen) ist verbunden:
Hinzufügen, korfigurieren
3. Es gibt die Berechtigung, die Objekte im Portlet „anzuzeigen“ (Anzeige). Dazu gehören:
 1. die Beschriftung ein/auszuschalten
 2. Marker und Figuren ein-/auszublenden
 3. Layer einzublenden / auszublenden. Diese Einstellungen werden nicht persistiert und auf alle Objekte gleichzeitig angewandt.
4. Es gibt die Berechtigung, Objekte zu erzeugen („hinzufügen“) und zu beschriften. Darunter:
 1. Polygone
 2. Marker
 3. Bookmarks
 4. Layer
 5. Objekte hochladen und auf Karte auf eigenem Layer darstellen.
Diese Einstellungen werden persistiert und auf alle Objekte gleich angewandt.
5. Wer das Recht hat, Objekte zu erzeugen, darf eigene Objekte auch bearbeiten.
Bei den Objekten muss also der Autor gespeichert werden.
6. Es gibt die Berechtigung, die Grundeinstellung vorzunehmen. Dazu gehört:
 1. Zentrum und Basis-Zoom
 2. Maximale Anzahl Layer
 3. Maximale Anzahl Marker
 4. Maximale Anzahl Figuren
 5. Export und Import von Objekten einer Instanz des Kartenportlets.
7. Wer das Recht hat, die Grundeinstellungen vorzunehmen, darf auch fremde (alle) Objekte bearbeiten.
8. Die Berechtigungen lassen sich bei der einzelnen Instanz des Portlets einstellen, nicht für alle Kartenportlets einer Site gemeinsam.
9. 

Anm mje: 
1. Layers muss es nicht geben, was bedeutet das für die Berechtigungen? -> Wir erstellen ein Layerkonzept - realisierung erst in Schritt3 (mom / jem 25.09.2015)
2. Was bedeutet 3.3? -> Anzeige Ein- / Aus-Schalten; -> Schritt3 (Noch offen - mom / jem 25.09.2015)
3. 4 zerfällt in zwei Rechte? Laut 5 soll das gekoppelt werden? -> Hinzufügen und Eigene bearbeiten nicht differenzieren. (mom / jem 25.09.2015)
4. 4.5 Konzept Layer ist noch nicht klar
5. 7. ist im Moment abgetrennt, sollen wir das zusammenführen? -> Konfigurieren und Fremde bearbeiten zusammenführen (mom / jem 25.09.2015)

#Schritt 2
Schritt 2 ist abnahmefähig, wenn folgende Bedingungen erfüllt sind:
1. Das Kartenportlet ist mit den folgenden Funktionen auf intermediate lauffähig:
2. Alles, was bereits im Schritt 1 verfügbar war
3. Marker sind verfügbar und können komfortabel beschriftet werden (einschließlich URL)
4. Figuren können eingezeichnet und komfortabel beschriftet (einschl. URL) und geändert werden.
Dazu wird das Plug-In verwendet, das es am 10.7.15 auf intermediate gab.
5. Zur komfortablen Beschriftung wird ein PlugIn verwendet, das am 10.7. in seiner ausführlichen Form vorgestellt wurde. Insbesondere ist wichtig, dass von einem Objekt aus ein URL und ein Bookmark auf eine Page der Site mit Portlet gelegt werden kann.
6. Und umgekehrt ist es möglich, dass von einem Content aus ein URL und eine geografische Bookmark auf ein Objekt im Kartenportlet gelegt werden kann.
7. Eine persistente Grundeinstellung kann vorgenommen werden, einschließlich:
 1. maximale Anzahl von Markern pro Portlet
 2. maximale Anzahl von Figuren pro Portlet
 3. Übernahme der aktuellen Zoom- und Zentrumseinstellung in die persistente.
8. Verschiedene Layer sind (noch) nicht erforderlich.
Figuren zu importieren ist (noch) nicht erforderlich.

Anm mje: 
1. Beschriftung URL fehlt zu 3.1 noch
2. 5. Plugin ist ein extra schritt? -> Schritt3 (mom / jem 25.09.2015)
3. 6. Referenzeirung von Kartenobjekten später -> Konzept in Schritt2 erstellen (mom / jem 25.09.2015)
4. 7. nochmal prüfen

#Weitere Schritte
Weitere Schritte werden in den folgenden Sprints aus den folgenden Features zusammengestellt:
1. Es ist möglich, Layer zu erzeugen und zu beschriften
2. Festlegung maximale Anzahl Layer pro Portlet
3. Die erzeugten Objekte können definierten Layern zugewiesen werden.
4. Ein Export und ein Import von Figuren mit ihren Beschriftungen und geografischen Bookmarks ist möglich.
5. Indoor-Funktion ist möglich.
Dazu gehört insbesondere Zoomen deutlich tiefer als die tiefste Stufe auf der Karte.
6. Import von Grafiken ist möglich, um z.B. Pläne von Architekten darstellen zu können.
Dazu gehört:
 1. Hochladen
 2. Einspielen
 3. Vergrößern, verkleinern in groben und feinen Stufen
 4. Höhen- und Breiten-Einstellungen
 5. Drehen in groben und feinen Stufen
 6. Beschriften der Grafik wie bei anderen Figuren auch.
g. NICHT aber: Strichdicke mit dem Zoom ändern
7. Beim Mouseover über eine Figur oder einen Marker oder eine importierte Grafik erscheint ein kurzer Text, der nicht identisch ist mit der ausführlichen Beschriftung.
8. Noch offen: Im Block für die ausführliche Beschriftung ist ein Content enthalten, der ein „normaler“ Content von Liferay ist. Er kann ausgewählt werden. Während der ausführlichen Beschriftung entsteht ein normaler Content von Liferay. Dazu steht der übliche embedded Editor von Liferay zur Verfügung.
9. 