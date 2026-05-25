# Bios Selbsttest (Post) 

Power on self test = (**Post**)

## Test und Initialisierung zentraler Hardware: 

- Cpu
- Bios-ROM (Bildung der Prüfsumme)
- DMA-Controller
- Tastatur 
- ersten 64k des RAMs,
- Interrupt und Cache-Controller 

## Test und Initialisierung von System-Erweiterungen

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



# Bootloader 

Nach dem Post lädt das BIOS in den Mbr (Master boot record) des Ersten eingetragenen Bootmediums. 

unfertig:[Quelle](https://cgvr.cs.uni-bremen.de/teaching/programming_literatur/linuxfibel/booten.htm#allg)

# Windows uefi boot


## Schritt 1: UEFI

Setzt den Prozesser in einen definierten Ausgangszustand und Optional wird die Integrität der Firmwäre verifiziert, um sicherzustellen das sie nicht durch Schadsoftware verändert wurde[^1]. War das Verifiziern erfolgreich dann, dient die Firmware als Vertrauenswürdige Basis für den weitern Boot.

Als Nächstes wird der Arbeitsspeiche Initialiesiert. Zudem werden wichtig Treiber für Grafik, Netzwerk, USB-Controller und weiters geladen, deren Funktionsumfang wird aufs nötigste reduziert.

## Schritt 2: Der UEFI-Bootmanager




[^1]:Der Check passiert durch die »Root of Trust«: eine Unveränderliche Hardware komponente. Etwa TPM oder Intels Boot Gurad.















# Booten - Was/für was ist booten

Booten ist de Process des Starten eines Computers gestartet durch das drücken eines Knopfes oder durch einen Befehl durch die Software 

Wenn ein 



# Schnelles Booten 

# Bootloader 

https://en.wikipedia.org/wiki/Bootloader **noch nicht in den quellen**


# Schematische Ablauf 

Einschalten des Computers Power on self test durchführen$^{\color{blue}{1}}$





# Quellen

1. Linux-boot https://wiki.ubuntuusers.de/Bootvorgang/
2. Linux-boot https://documentation.suse.com/de-de/sled/15-SP5/html/SLED-all/cha-boot.html
3. https://wiki.archlinux.org/title/Arch_boot_process
4. [uni-bremen/Bootvorgang](https://cgvr.cs.uni-bremen.de/teaching/programming_literatur/linuxfibel/booten.htm)

[^1]: Ref
