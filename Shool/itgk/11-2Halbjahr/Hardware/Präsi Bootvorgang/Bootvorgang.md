# Vorwissen

## Runlevel

https://cgvr.cs.uni-bremen.de/teaching/programming_literatur/linuxfibel/booten.htm#sbininit

## Mounten 

Als „mounten“ wird der Vorgang des _Einhängens_ eines Dateisystems in die bestehende Verzeichnisstruktur bezeichnet. Dieses Einhängen ist notwendig, um mit üblichen Programmen auf Dateien eines Dateisystems zugreifen zu können.

## Partitionen

Eine Partition ist ein abgetrennter, logischer Bereich auf einem Datenträger.

## Grundlagen Bash

## PCI-Geräte

Ein PCI-Gerät (Peripheral Component Interconnect) ist eine Hardware-Komponente, die direkt in einen Erweiterungssteckplatz (PCI- oder PCIe-Slot) auf der Hauptplatine (Motherboard) Ihres Computers gesteckt wird.

## Sockets

Ein **Socket** in ist ein Kommunikationsendpunkt zum Datenaustausch 

## Dämonen

Ein Dämon ist ein Computerprogramm, das im Hintergrund und ohne direkte Steuerung durch den Benutzer arbeitet

## Root-Dateisystem

Das **Root-Dateisystem** (auch Wurzelverzeichnis genannt) ist die oberste Ebene der Verzeichnisstruktur.

## Bios-Rom

Das BIOS-ROM  ist der physische Chip auf dem Motherboard eines Computers, der die grundlegende Steuerungssoftware (Firmware) enthält.

## DMA-Controller

Ein DMA-Controller (Direct Memory Access) ist ein spezialisierter Prozessor, der Datentransfers zwischen dem Arbeitsspeicher und Peripheriegeräten (z. B. Festplatten oder Netzwerkkarten) selbstständig durchführ. Er entlastet die CPU vollständig, da diese keine einzelnen Kopierbefehle ausführen muss, was die Systemleistung und den Datendurchsatz massiv erhöht.

# Quelle: [uni-bremen](https://cgvr.cs.uni-bremen.de/teaching/programming_literatur/linuxfibel/booten.htm#sbininit)

## Bios Selbsttest (Post) 

Power on self test = (**Post**)

### Test und Initialisierung zentraler Hardware: 

- Cpu
- Bios-ROM (Bildung der Prüfsumme)
- DMA-Controller
- Tastatur 
- ersten 64k des RAMs,
- Interrupt und Cache-Controller 

### Test und Initialisierung von System-Erweiterungen

- Ram über 64k
- Schnittstellen 
- Disketten Festplatten Controler 
- Rom erweiterungen werden gesucht und Iitialisiert z.b Video-rom 
	- Beu SCSU-Systemen ist die ebenso

Tritt in dieser Phase ein Fehler auf dann wird eine Tonfolge abgespielt. Für bestimmter Fehler sind genaue signale vorgeschrieben:

![[Post_fehler_tabelle.png]]

Sind alle Tests vom Post erfolgreich sucht das Bios nach Bootgeräten für eine gültige Bootsquenz. Bootgeräte können volgende Geräte sein:
- Diskette 
- Festplatte 
- CD-ROM-Laufwerk
- Netzwerkkarte 
Welche Bootmedien durchsucht werden und die Reihenfolge, in der das BIOS die Geräte durchsucht, kann im CMOS-Setup eingestellt werden. Der erste gefundene Bootkode wird geladen und gestartet.




## Mbr 

Nach dem Post lädt das BIOS in den Mbr (Master boot record) dieser bootet das Erste valide eingetragenen Bootmediums. Wenn der Mbr fehlschlägt ein Bootmedium zu booten geht er zum nächsten über. Der Mbr erhält neben der Partitonstabelle auch  von den Koordinaten der bis zu 4 Primär Partionen. Außerdem enthält er auch die magic number also  AA55 diese markiert den Sektor als bootbar. Mbr ist der Vorgänger von GPT(GUID Partition Table)(siehe Überschrift: gpt)

![[media/MBR_(Master_Boot_Record)_Anatomy.svg]]
 [Von Shmuel Csaba Otto Traian, CC BY-SA 3.0](https://commons.wikimedia.org/w/index.php?curid=28428192)

Die meisten systeme die einen Bootmanger mitbringen haben die unangeneme eigentschaft ihren Bootloader als bootable zu setzen, wodurch das booten in »fremdsysteme« gestopt wird. 

Oftamls verfügen bootloader über die Funktionalität ein System mit einem Password zu schützen. Oder das Laden von mehreren Betriebsystemen. Auch beim boot von einem Wechselmedium.[^3]
Bei solchen Umfangsreichen Funktionalität, passt der gesamte code eines Bootloader nicht in die dafür reservierten 512 Bytes, vorallem da 2 Bytes für die Bootable Flag und weiter 64Bytes für die Partionstabelle verbraucht werden.
Deshalb werden moderne Bootloader in zwei Stufen realisiert, wobei die erste Stufe im Bootsektor bzw. im Mbr steht. Dadurch ist die einzige aufgabe vom Mbr, die zweite, auf der Festplatte liegende Stufe, in den Hauptspeicher zu laden.

[^3]:Bsp: CD-Rom,Diskette,USB-Stick

## Kernel

Am Anfang sind die Tätigkeiten des Kernels sehr nahe an der Hardware und. Er ermittelt aus dem Bios elementare Parameter und schaltet den Prozessor in den Protected mode. Die nächsten Schritte betreffen die Initialisierung der Speicherverwaltung (MMU), des eventuell vorhandenen Coprozessors und der Interruptcontroller sowie die Erzeugung einer minimalen Umgebung.

Die bis jetzt getätigte schritten sind alles Assembler-Routinen. Die weitern Funktionen sind weniger Architekturabhängig und deswegen in der Sprache C implementiert.

Danach läuft kurzzeitig der Idel-Prozess, der Idle Prozesser ist ein Pseudo-Prozess und ist immer aktiv und kann als zwichenablage für die ungenutzte Proessor Kapzität verstanden werden.[^4] Danach ist er nicht mehr sichtbar 

[^4]:https://de.wikipedia.org/wiki/Leerlaufprozesshttps://de.wikipedia.org/wiki/Leerlaufprozess

Danach nimmt sich der init Process die Prozessnummer 0 und gilt dann als erster Prozess. Jeder Prozess bzw. Prozessfamile wird hat irgendwo den ursprung von Init.<br>
Init sorgt auch für seine absoluter Alleinherrschaft und sperrt prozess 0 bzw.  den Zugang zu den Kernelfunktionen, da in den nächsten Schriten init keiner dazwichen funken darf. Init kommt seinen Namen gleich und fängt an zu initialisieren, worum es sich konkret handel hängt zwar vom Kernel, grundlegend werden PCI-Geräte und Sockets.
Ersten Dämonen werden ins Leben gerufen bdflush zu synchronisation von Cache und Dateisystemen und der kswapd zur Verwaltung des Swapspeichers. Anschließend wird dem Kernel unterstützte Binärformate und Dateisysteme bekannt gegeben und anschließen wird versucht, das Root-Dateisystem zu mounten. Ist nichts Schief gelaufen gibt init den Kernel wieder Frei und lässt den anderen Prozessen eine Chance




### Ramdisks 

Um auf Hardware zugreifen zu können braucht Linux entsprechende treibe zum Beispiel Treiber für den Festplatten-Controller. Diese Treibe können entweder direkt in dem Kernel integriert sein oder auf dynamisch ladbaren Modulen vorliegen. Die Menge der fest einkompilierten Treiber ist allerdings beschränkt, da in der Ladephase des Kernels dieser vollständig in den Hauptspeicher passen muss. Zum Zeitpunkt des Ladens befindet sich der Rechner noch im Real Modus, dass heißt das der adressierbare Hauptspeicher und damit auch die Größe des Kernels begrenzt ist. (640kByte)

#### Problem

Um module Verwenden zu können müssen diese irgendwo auf der Festplatte liegen, dass heißt der Kernel muss auf die festplatte zugreifen können wofür er den Treiber braucht. Nur leider gibt es nicht den einen Treiber es gibt etliche Treiber. Bei einem Universalen Treiber wie z.B linux sind das ziemlich viele Treiber.

#### Lösung

Eine Ramdisk ist ein Lösung zu diesem Problem und löst dies in zwei schritten. Die Ramdisk belegt einen Teil des RAM und legt ein Dateisystem an. Der bootloader legt nun in diesem Speicher die datei »initrd« und den (minimalen)Kernel hintereinander ab. Der nun zu startenen (minimalen) Kernel. Dieser Kernel erhält nun den Treiber, um den Inhalt aus von »initrd« in eine Ramdisk zu entpacken und diese als sein Root-Dateisystem zu mounten. Die ursprüngliche Datei »initrd« wird aus dem Hauptspeicher entfernt. 

In der Ramdisk sollte nun eine Datei /linuxrc existieren, die nun abgearbeitet wird (im auftrag beinhaltet diese ausführbare Datei Schritte zum Testen der Hardware und zum Laden der notwendigen Module zum Zugriff auf die erkannten Geräte). Sobald die Datei abgearbeitet wurde, wird das »eigentliche« Dateisystem als Wurzelverzeichnis gemountet.


## Der erste Prozess 

Bei einer Fehlenden Configartionsdatei von init, bootet das System in den Singel User Modus, diese stellt nur die nötigsten Prozesse zur Verfügung um dem Systemadministrator alle möglichen Ressourcen  zu geben. Außerdem gibt es dem Systemadministrator die Option sich anzumelden. 

Im falle eines Multi user Modus lässt **init** alle dem jeweiligen Runlevel zugeordneten Skripte von einem Shellskript namens **rc** starten. Das ist auch der Zeitpunkt wo die zahlreichen Meldungen über gestartete Dämonenprozesse über den Bildschirm flimmern. Ist das aktuelle Runlevel erreicht dann starte init eine Reihe von getty-Prozessen, die dann wiederum das Komando für den Login ausführen.

### Bsp. eines Init-Skripts


```bash
#!/bin/sh  
#  
# xfs:       Starts the X Font Server  
#  
# Version:      @(#) /etc/rc.d/init.d/xfs 1.6  
#  
# chkconfig: 2345 90 10  
# description: Starts and stops the X Font Server at boot time and shutdown.  
#  
# processname: xfs  
# config: /etc/X11/fs/config  
# hide: true  
  
# Source function library.  
. /etc/rc.d/init.d/functions  
# See how we were called.  
case "$1" in  
  start)  
        echo -n "Starting X Font Server: "  
        rm -fr /tmp/.font-unix  
        daemon xfs -droppriv -daemon -port -1  
        touch /var/lock/subsys/xfs  
        echo  
        ;;  
  stop)  
        echo -n "Shutting down X Font Server: "  
        killproc xfs  
        rm -f /var/lock/subsys/xfs  
        echo  
        ;;  
  status)  
        status xfs  
        ;;  
  restart)  
        echo -n "Restarting X Font Server. "  
        if [ -f /var/lock/subsys/xfs ]; then  
            killproc xfs -USR1  
        else  
            rm -fr /tmp/.font-unix  
            daemon xfs -droppriv -daemon -port -1  
            touch /var/lock/subsys/xfs  
        fi  
        echo  
        ;;  
  *)  
        echo "*** Usage: xfs {start|stop|status|restart}"  
        exit 1  
esac  
  
exit 0
```






# gpt

[Quelle](https://de.wikipedia.org/wiki/GUID_Partition_Table)










## Quelle

[Quelle](https://cgvr.cs.uni-bremen.de/teaching/programming_literatur/linuxfibel/booten.htm#allg)

# Windows uefi boot Quelle: c't 2026 11 S.152-154

## Schritt 1: UEFI

Setzt den Prozesser in einen definierten Ausgangszustand und Optional wird die Integrität der Firmwäre verifiziert, um sicherzustellen das sie nicht durch Schadsoftware verändert wurde[^1]. War das Verifiziern erfolgreich dann, dient die Firmware als Vertrauenswürdige Basis für den weitern Boot.

Als Nächstes wird der Arbeitsspeiche Initialiesiert. Zudem werden wichtig Treiber für Grafik, Netzwerk, USB-Controller und weiters geladen, deren Funktionsumfang wird aufs nötigste reduziert.

[^1]:Der Check passiert durch die »Root of Trust«: eine Unveränderliche Hardware komponente. Etwa TPM oder Intels Boot Gurad.


## Schritt 2: Der UEFI-Bootmanager

Der UEFI-Bootmanger hat die Wessentliche aufgabe einen Betriebsystem-Bootmanger zu laden und die Kontrolle zu übergeben.

Die nötigen Informationen dazu findet er in den UEFI-Boot-Variablen, diese sind auf einen nicht Flüchtige speicher  auf dem Mainboard[^2]. Die Darin abgespeicherten Informationen bestimmen unter anderm  die Boot-reinfolge auch, ob über das Netzwerk geboote werden soll, steht dort auch beschrieben. Scheitert der Bootvorgang. 

In weitern UEFI-Variablen steht wo genau der Bootmanager zu suchen ist. Informationen, aber auch Systemsprache und ob das UEFI über bestimmte Fähigkeiten besitzt. So weiß windows ob es nach dem neustart ins UEFI-Setup  anbieten oder Firmware-Update einspielen darf und ob das UEFI direkt eine Wiederherstellungsumgebung starten kann.

[^2]:z.B NVRAM oder Flash 

## BCD und BCDedit

BCDedit kann zum auslesen oder bearbeiten von boot variablen genutzt werden. In der Powershell oder cmd folgendes ausführen:

```cmd
BCDedit.exe
```

Bsp. Ausgabe:

dc

BCD steht für Boot configuraiton data. In der BCD stehen alle informationen die ein PC braucht um zu booten. Diese Informationen stehen nicht nur in UEFI-Variablen sonder auch in spezilen Dateien  (BCD-Store).

# Linux Boot

## Init



https://documentation.suse.com/de-de/sles/15-SP5/html/SLES-all/cha-boot.html


# Live USB










# (Booten - Was/für was ist booten)

Booten ist de Process des Starten eines Computers gestartet durch das drücken eines Knopfes oder durch einen Befehl durch die Software 

Wenn ein 





# Bootloader 

https://en.wikipedia.org/wiki/Bootloader **noch nicht in den quellen**


# Schematische Ablauf 

Einschalten des Computers Power on self test durchführen$^{\color{blue}{1}}$





# Quellen

1. [Linux-boot-ubuntu](https://wiki.ubuntuusers.de/Bootvorgang/)
2. [Linux-boot-suse](https://documentation.suse.com/de-de/sled/15-SP5/html/SLED-all/cha-boot.html)
3. https://wiki.archlinux.org/title/Arch_boot_process
4. [uni-bremen/Bootvorgang](https://cgvr.cs.uni-bremen.de/teaching/programming_literatur/linuxfibel/booten.htm)
5. [Startup Windows Init vergleich](https://www.reddit.com/r/windows/comments/2on5ln/windows_init_system/?tl=de)
6. [Boot process von Windows](https://en.wikipedia.org/wiki/Booting_process_of_Windows) Windows nt soll sehr ähnlich so Windows 10 sein nach Quelle 5 
7. [Wiki Leerlaufprozess](https://de.wikipedia.org/wiki/Leerlaufprozesshttps://de.wikipedia.org/wiki/Leerlaufprozess)


[^3]: Bsp: CD-Rom,Diskette,USB-Stick

[^4]: 
