tags: #präsentation #rastergrafiken
# Eigenschaften  
-die meisten digitalen Bilder sind Rastergrafiken.
- Bilder werden in ein Pixelraster gespeichert, das überlicherweise als Bitmap bzw. Bitmap-Grafik bezeichent wird 
## Kompremierung
-Da Rastergrafiken so viel informationen spreichern gibt es Kompressionsalgorithmen  z.B: Png JPEG GIF [Unkompremirte Dateiformate](https://unlimited.ethz.ch/spaces/DD/pages/194127898/Archivtaugliche+Dateiformate)
-Beim runterskalieren verliehren Rastergraffiken kein qualität. Aber beim hochskalieren verliehrt ein BItmap-bild an Qualität bzw. erscheint das bild unscharf. 
- Deswegen werden Vektorgrafiken bei bestimmten bilder benutzt. Wie bei z.B Firmen logo 

# Anwendungen 
-Rastergrafiken eignen sich zur Darstellung komplexer Bilder wie Fotos, die nicht mit vektorgrafiken beschreib sind. 
	-Können mit [Scanner](https://de.wikipedia.org/wiki/Scanner_(Datenerfassung)) , Digitalkammeras oder Bildbearbeitungssoftware erstellt werden 
Minimalistische Pixelgrafiken als Kunst 

# Nachteile
Heutige Computerbildschirme werden ausschlislich über Rastergrafik, die im [Framebuffer](https://de.wikipedia.org/wiki/Framebuffer) abgelegt ist und den gesamten Bildschirm inhalt enthält, angesteuert. Daher müssen Vektorgrafiken vor der Ausgabe gerastert werden.
Nachteile gegenüber vektorgrafiken;
- Hoher speicher verbrauch 
	- Da rastergrafiken nur aus einer begrenzten Anzahl von Pixeln bestehen, werden zweidimensionale geometrische Formen nur angenähert. Dabei enstehen wie z.b bei einem kreis ein Treppeneffekt (auch aliaseffekt)
		- Es gibt ein [Antialiasing](https://de.wikipedia.org/wiki/Antialiasing_(Computergrafik))  wo pixel abgerundert werden (glaube ich)4[[Antiallising]]
	- Es können informationen bei der Runterskalierung 

# Umwandlungen 
Rasterung: Umwandlung von vektorgrafiken in Rastergrafiken 
- Dieser vorgang passiert **immer** benutzt wenn einen vektorgrafik angezeigt wird 
- **Vektorisierung** von Rastergrafiken ist schwieriger. 
	- Manuel durch nachzeichen 
	- Funktion Trace Bitmap von Inkspace, Potrace; oft vehlerhaft da grafische Primitve (Greaden,Kreise oder Kurven) in der Rastergrafik nur ungenau abgebildet werden und nicht exact erkannt.
		- Probleme enstehen vorallem x^
![[Kreis_reingez grdnojf.png]]

# Image Resolution
Des so höher die Auflösung desto mehr details hat das Bild.
|-> das trifft auf digitale bilder filme und andere typen von Bildern.
Die Auflösung ist in: Breite x Höhe angegeben
## Einordnung
Die Auflösung ist in der Praxis mehrdeutig und in vielen Bereichen verwendet, wodurch eszu Missverständnissen kommen kann.
Im physikalischen Sinn bezeichnet die Punktdichte einer Wiedergabe oder Bildabtastung und ist damit neben der Farbtiefe ein Maß für die Qualität 

[Quelle](https://de.wikipedia.org/wiki/Bildaufl%C3%B6sung)


# Nochmal angucken !!!!


# Quelle
[quelle](https://de.wikipedia.org/wiki/Rastergrafik)
#Shool
