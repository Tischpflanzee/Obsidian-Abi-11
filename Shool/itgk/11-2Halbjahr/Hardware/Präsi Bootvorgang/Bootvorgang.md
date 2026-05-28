# Quelle: c't 2026 11 S.152-154

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



# Bootloader 

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

Am Anfang sind die Tätigkeiten des Kernels sehr nahe an der Hardware und.

Anfangs nimmt sich init den prozess 0 und behält dies auch, auch wen dieses nicht sichtbar ist. 

**unfertig**: https://cgvr.cs.uni-bremen.de/teaching/programming_literatur/linuxfibel/booten.htm#kernel

# gpt

[Quelle](https://de.wikipedia.org/wiki/GUID_Partition_Table)










## Quelle

[Quelle](https://cgvr.cs.uni-bremen.de/teaching/programming_literatur/linuxfibel/booten.htm#allg)

# Windows uefi boot

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

1. Linux-boot https://wiki.ubuntuusers.de/Bootvorgang/
2. Linux-boot https://documentation.suse.com/de-de/sled/15-SP5/html/SLED-all/cha-boot.html
3. https://wiki.archlinux.org/title/Arch_boot_process
4. [uni-bremen/Bootvorgang](https://cgvr.cs.uni-bremen.de/teaching/programming_literatur/linuxfibel/booten.htm)
5. [Startup Windows Init vergleich](https://www.reddit.com/r/windows/comments/2on5ln/windows_init_system/?tl=de)
6. [Boot process von Windows](https://en.wikipedia.org/wiki/Booting_process_of_Windows) Windows nt soll sehr ähnlich so Windows 10 sein nach Quelle 5 


[^3]: Bsp: CD-Rom,Diskette,USB-Stick
