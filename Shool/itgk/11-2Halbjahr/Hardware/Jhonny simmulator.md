# 3b

Addresbus = 42
ram -->db
db-->acc
plus
acc-->db
db-->ram

# 4
10+11+12-14 ges:15

Address Bus = 10
ram --> db
db -->acc
**Noch nicht fertig**

# 5 




| Mikrobefehl | Bedeutung                                                   |
| ----------- | ----------------------------------------------------------- |
| INC  **10** | Erhört den wert an stelle **10** des Arbeitspeicher um 1    |
| DEC **10**  | Veringert den wert an stelle **10** des Arbeitspeicher um 1 |
| NULL **10** | Setzt den wert an stelle **10** des Arbeitspeicher auf 0    |

# 6

## 6.a


| Mikrobefehl | Bedeutung                                                                                                     |
| ----------- | ------------------------------------------------------------------------------------------------------------- |
| JMP **10**  | Springt auf eine Stelle im Arbeitsspeicher bsp. **10**                                                        |
| TST **10**  | Testet ob der Wert null ist wenn dies eintrifft dann überspringt er die nächste Anweisung im Arbeitsspeicher  |

# 6.b

Aufgabe: 10 \* 11 = 12

Null **12**
DEC **10**
Take **12**
ADD **11**
SAVE **12**
TST **10** 
JMP **1**


[[Multiplizieren.ram]]

# 7

## 7.a

Das Programm verändert veränder sich in der Zweiten Zeile selbst sodass es den zuvor Gespeicherten Wert nicht überschreibt.

## 7.b


000 Null 7
001 Take 7
002 SAVE 101
003 INC 7
004 INC 2
005 INC 2
006 JMP 1
007 42












