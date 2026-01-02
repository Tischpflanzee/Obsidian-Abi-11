#ransomewre #itgk 
# 1. Ransomeware

## 1.1 Was ist Ransomware 

Ransomware sind Schadprogramme die es in unterschiedlichen Varianten gibt. Meistens ist ihr ziel die Verschlüsselung von Nutzer Daten um den Nutzer mit Lösegeld zu erpressen um das die Daten erst nach der Zahlung wieder entschlüsselt werden. 


# 2 Bedrohungslage

## 2.1 Wenn sie Betrifft 

Meisten werden Großkonzerne angegriffen aber auch mittelständische Unternehmen wie Krankenhäuser oder Kommunen.
Aber auch Privatpersonen können von Ransomware betroffen sein. 

## 2.2 Wie angegriffen wird

Es wird z.B über Spam-Mails die durch gefälschte Absendeaddressen und vermeintliche Antworten die dazu verleiten sollen eine schädliche Köder Datei Auszuführen und den Inhalt freizugeben. 
Es werden teilweise ganze Systeme gesperrt oder es wird über Server an alle verbunden Server, dies geht aber nur wenn der Angreife zur Verfügung von hohen Rechten oder nicht ausreichend durchdachter Backup-Konzept ach alle Datensicherungen verschlüsselt sofern die Backups nicht offline gehalten werden. 

### 2.2.3 Automatisierte und manuelle Aufklärung von Netzwerken

Durch automaisierten Ausbreitung späht das Schadprogramm das Netzwerk des Opfers aus und übermittelt dabei Informationen über: Systeme, Benutzer und es wird Schadsoftware installiert. 
Erst danach wird basierrend auf den gesamelten informationen entschieden ob das Ziel sich lohn oder nicht. Wenn das opfer ein sich „lohnendes ziel" ist. Wird durch Fernzugriff aufs Netzwerk zugegriffen und ziehen sich ggf. weiter Infos. 
**Diese Methode wird nur bei Hochwert zielen eingesetzt da es nur Begrenzte Kapazitäten gibt zur manuellen Aufklärung**

### 2.2.3.2 Schaden

#### 2.2.3.2.1 Sicherung existent 
Wenn (offline) Sicherungen verfügbar sind dann müssen sie nach der Bereinigung des Netzwerkes zurückgespielt werden und die Verlorene Zeit muss aufgearbeitet werden. **Mehrere Tage oder Wochen** 

#### 2.2.3.2.2 Sicherung **nicht** existent  

Alte Datei Sicherungen wiederherstellen (wenn existent) viel nacharbeit kann vor allem für kleine Unternehmen kann das existenten bedrohend sein.


### 2.2.4 Verschlüsselung von Systemen 

Wenn die Verschlüsselung von Daten großen Teil der Orginazion lahmlegen könnten und es sich um ein Zahlungskräftiges Unternehmen handelt. Rollen sie eine Ransomware  auf allen (Server-) Systemen aus, wodurch oftmals aufgrund des Angreifers hohen rechten oder nicht ausreichend durchdachter Backup-Konzepte häufig auch alle datei sicherungen  Verschlüsselt, sofern sie nicht ofline sind. 
Die löse geld summen liegen oftmals im 6stelliegen bereich es gab aber auch schon fälle wo die summe im 8stelliegen bereich lagen. Es kommt aber sehr auf das Unternehmen drauf an. 



#### 2.2.4.1 Schadenswirkung 

#####  2.2.4.1.1 Mit Datensicherungen 

- Netzwerk muss bereinigt werden 
- Daten werden wieder Zurück gespielt
	|-> **Beeinträchtigung der Arbeit von mehreren Tagen oder Wochen** 

##### 2.2.4.1.2 Ohne Datensicherungen 

- Rekonstruktion vereinzelter alter Sicherungen 
- Viele manuelle Nacharbeit
	|-> **Beeinträchtigung der Arbeit von mehreren Wochen bis Monaten.
	|-> Dieser Fall kann insbesondere für kleinere Unternehmen existenzbedrohend sein.**

##  2.3 Veröffentlichung von Daten

- Täter drohen damit die Daten vom Opfer zu veröffentlichen wenn eine Zahlung nicht getätigt wird.
	|-> da die Veröffentlichung von Daten für viele unternehmen unter Umstände ein **Reputationsverlust**  und weiter **negative finanzielle Auswirkungen** ergeben könnte.
		|-> Dadurch kann der Täter den Druck hoch halten.
- Teilweise werden auch Kunden mit den abgeflossenen Daten erpresst.

### Schaden 

[seite 4 mitte pdf](https://www.bsi.bund.de/SharedDocs/Downloads/DE/BSI/Cyber-Sicherheit/Themen/Ransomware_Managementabstract-Angriffe.pdf?__blob=publicationFile&v=2)


# 2.4 Schöne Grafik lol

![[Managementabstrakt Fortschrittliche Angriffe - Neue Qualität aktueller Angriffe und Prognose - Ransomware_Managementabstract-Angriffe.pdf]]


# 3 Präventation

## 3.1 Von dem Anderem Pdf

### 3.1.1 Patches und Updates

Die Ausnutzung einer (beriets bekannten) Schwachstelle in einem Softwareprogramm gehört zu den drei Häufigsten Einfallsvektoren von Ransomware-Gruppen  
	|-> Generell hilft es das Update vom Softwareentwickler runter zu laden um Sicherheitslücken zu vermeiden 

**Wirkung in Phase: 1**

### 3.1.2 Remote Zugänge 

Der zugriff von aussen also per remote sollte nicht offen sein. Stattdessen sollte der zugriff aufs Netzwerk nur mit Vpn und Zwei Factor Authentisierung möglich sein. 

**Wirkung in Phase: 1**

### 3.1.3 E-Mails und Makros

E-Mails sollten im nur in Text dargestellt werden und nicht in als HTML-Mail da so schad-links verschleiert werden können. Bsp.:

Was angezeigt wird: www.google.com

Wo es hinführt: www.schadsoftware.com

Wenn diese dartstellung nicht möglich ist dann sollte zummindestens die aktive Elemente bei HTML-Mails deaktiviert werden und Mitarbeiter sollten geschult werden wie Fake mails erkannt werden können.

**Wirkung in Phase: 1**

### 3.1.4 Ausführen von Programmen

Die einschränkung bzw. regelung von Ausführbaren Programmen kann die Infektion rate deutlich senken da nur bestimmte Programme ausgeführt werden können und so keine Schadsoftware von den Usern überhaupt ausgeführt werden können.

**Wirkung in Phase: 1**

### 3.1.5 Virenschutz 

Es sollten auf Virenschutz der  IPS also Intrusion Prevention-Module und Cloud-Dienste erkennt.

**Wirkung in Phase: 1**

### 3.1.6 Administartor Accounts 

Accounts mit Administrator rechten sollten keine funktion Email zu lesen oder mit dem Internet verbunden sein. Sie sollten auch nicht von außen erreichbar sein. 

**Wirkung in Phase: 2**

### 3.1.7 Netzwerke segmentieren

Eine Sauber Netzsegmentierung hilft schäden zu begrenzen, da die Ransomware nur in die Systeme in unmittelbare Nachbarschaft erreichen können.

**Wirkung in Phase: 3**

#### 3.1.7.1 Begriff Netzwerksegmentieren 

- in großes Netzwerk wird in **Subnetze** aufgeteilt, ähnlich wie ein Gebäude in verschiedene Brandabschnitte unterteilt wird.
    
- Die Kommunikation zwischen den Segmenten wird durch **Router**, **Firewalls** oder **VLANs** (Virtual Local Area Networks) kontrolliert.

### 3.1.8 Backups, Datensicherungskonzept 

Ein Daten Backup um Dateien wiederherzustellen und um Lösegeld zu umgehen.
Um diese Backups sehr sicher zu halten **müssen** sie offline sein, damit sie nicht von außen verschlüsselt werden können.
Man kann vor allem Usern die Schreib Rechte auf archiv Back-ups entziehen um Verschlüsselung zu umgehen.

**Wirkung in Phase: 5**

### 3.1.9 Härtung des Active Directories

Einer der ersten ziele eines Täter sind die zentralen Authentisierungsdienste, um erweiterte mit Erweiterten rechten auf Clients und Server inerhalb der Domäne zugreifen zu können und die Ransomware zentral zu verteilen, 
Hier sollte man weiter Maßnahmen ergreifen um den eingriff aufs Active Directory zu erschweren. 

**Wirkung in Phase: 3**

### 3.1.10. Notfalplan

Im fall davon das alle Systeme im Netzwerk verschlüsselt sind und ein Erpressungsschreiben vor liegt sollte ein Notfalplan exsistieren. Dieser Notfallplan sollte aus volgenden punkten bestehen:
- Wiederherstellung von geschäftskritischer Systeme
- geschäftskritische Systeme müssen identifiziert werden und alternative Kommunikationsmöglichkeiten vorbereitet sein.
- Wichtige Telefonnummern und Ansprechpartner sollten offline (Papier) vorgehalten werden.

**Wirkung in Phase: 6**

## Von dem einem PDF 

- Sicherheitskonzepte und Notfallpläne erstellen und regelmäßig überprüfen,
-  Netzwerk-Segmentierung und strikte Rechte-Trennung im Active Directory, um eine ungehemmte
- Ausbreitung von Schadprogrammen und vollständige Kompromittierung des Netzwerks zu verhindern,
- vollständige Backup-Strategie inkl. Offline-Backups (auch regelmäßig Wiederherstellung prüfen),
- Patch-Management verifizieren – insbesondere Sicherheitsupdates für kritische Schwachstellen müssen zeitnah ausgerollt werden
- Logging-Strategie umsetzen, über die ein Abfluss von Daten nachvollzogen werden kann,
-  Sensibilisierung von Mitarbeitern und Umsetzung technischer Maßnahmen zur Härtung von (Arbeitsplatz-)Systemen müssen Hand in Hand gehen,
- Maßnahmen entwickeln, wie mit einem Abfluss und einer Offenlegung unterschiedlicher auch sensibler Daten umgegangen werden kann sowie
-  Management-Awareness schaffen, um Cyber-Risiken als Bestandteil des Risiko- und Vorsorgemanagements zu verankern.

**mabye nochmals umschreiben** 


# 4. Detektion 

## 4.1 Unübliche Nutzung von Kommandozeileninterpretern

- Viele Angreifer nutzen die Commandozeile oder die Powershell um weiter schadsoftware nach zu laden oder erhörte rechte zu erlangen. 
- Daher sollten diese auf Unregelmäßigkeiten untersucht werden. Und änderungen über diese Programme sollten überwacht  werden.
**Wirkung in Phase: 1, 2, 3, 4 und 5**

## 4.2 Auslessen von Anmeldedaten

Das Auslessen von Anmelde daten wird von Angreifern insbesonders für die Ausbreitung im Netzwerk verwendet. 
|-> hier bei werden oftmals tools wie Mimikatz, Procdump oder nutzen bereits auf dem System befindliche Bormittel wie z.B die Windows-Libary "Comcvsc.dll". 
- Bei diesen Aktivitäten werden zum bsp. ein Dump des Local Security Authoirty Subsystem Service erstellet und Ausgeleseen, um Passwörter lokaler Nutzer zu erhalten.
Wenn solche Datenbanken ausgelesen werden sollte es Arlame generiern werden.

**Wirkung in Phase: 2 und 3**

## 4.3 Anlegen von Scheduled Tasks 

### 4.3.1 Was sind Scheduled Tasks

Die **Aufgabenplanung** (vormals **Taskplaner**) ist ein Bestandteil aller modernen Versionen von Microsoft Windows und ermöglicht das Starten von Anwendungen einmalig oder wiederkehrend zu festgelegten Zeitpunkten.

### 4.3.2 Scheduled Tasks im Kontext von Präventation

Scheduled Tasks werden von Angreifern erstellt um dauerhaft auf einem System einzudringen. Da diesse Technik zu einer der Beliebtesten gehört, sollte das erstellen von Scheduked Task genau überwacht werden. 

**Wirkung in Phase 1**

## 4.4  Auskundschaften des Netzwerks
Nachdem ein Angreifer zugriff auf ein System hat, wird oft versucht informationen über das netzwerk zu erlangen und dort vorhandenen Ressourcen zu bekommen.
Diese Informationen bestehen z.B aus Active Direcotrys wo alle Objekte wie Benutzer, Computer, Drucker und Software in einer hierarchischen Struktur gespeichert sind. 

**Wirkung in Phase: 3**

## 4.5 Überwachung von Dateizugriffen 

- Angreifer greifen auf Datein zu, vorallem um sie zu verschlüsseln. 
- Diese zugriffe können erkannt werden indem die Nutzung von so genannten Canary Files die allein für die Detektion von Angreifer vorgesehen sind. 
- Diese Dateien funktionieren indem ein üblicher User keine zugrif auf sie hat, sodass wenn sie verändert werden dies ein Starker Indiz für einen Laufenden angriff ist.  
- Die Datein sollten an Kritischen stellen plaziert werden. 
ein **Reputationsverlust**  und weiter **negative finanzielle Auswirkungen** ergeben könnte.
## 4.6  Löschung von Backups

https://www.bsi.bund.de/DE/Themen/Unternehmen-und-Organisationen/Cyber-Sicherheitslage/Analysen-und-Prognosen/Ransomware-Angriffe/Top-10-Massnahmen-Detektion/top-10-massnahmen-detektion_node.html


<<a<a<<<<<<<<<<<<<<<<

# Wörter --Erklärung

## Datenabfluss 

Geklaute daten (glaube ich )

## Acitve Directory 

Active Directory (AD)

ist ein zentrales Verzeichnis für Windows-Netzwerke, das alle Objekte wie Benutzer, Computer, Drucker und Software in einer hierarchischen Struktur organisier
# Quelle

## Pdfs

https://www.bsi.bund.de/SharedDocs/Downloads/DE/BSI/Cyber-Sicherheit/Themen/Ransomware_Managementabstract-Angriffe.pdf?__blob=publicationFile&v=2

## Links

1. https://www.ncsc.admin.ch/ncsc/de/home/cyberbedrohungen/datenabfluss.html
2. https://www.bsi.bund.de/DE/Themen/Unternehmen-und-Organisationen/Cyber-Sicherheitslage/Analysen-und-Prognosen/Ransomware-Angriffe/ransomware-angriffe_node.html
3. https://www.bsi.bund.de/DE/Themen/Unternehmen-und-Organisationen/Cyber-Sicherheitslage/Analysen-und-Prognosen/Ransomware-Angriffe/Top-10-Ransomware-Massnahmen/top-10-ransomware-massnahmen_node.html