# 3b

Addresbus = 42
ram -->db
db-->acc
plus
acc-->db
db-->ram

# 4

10+11+12-14 ges:15

acc+ \* 10
acc -->db
db-->ins
ins-->pc
ins-->ab
ram-->db
db-->acc
pc++
pc-->ab
ram-->db
plus
pc++
pc-->ab
ram-->db
plus
pc++
pc++
pc-->ab
ram-->db
minus
pc++
pc-->ab
acc-->db
db-->ram




**Noch nicht fertig**

# 5 




| Mikrobefehl | Bedeutung                                                   |
| ----------- | ----------------------------------------------------------- |
| INC  **10** | Erhört den wert an stelle **10** des Arbeitspeicher um 1    |
| DEC **10**  | Veringert den wert an stelle **10** des Arbeitspeicher um 1 |
| NULL **10** | Setzt den wert an stelle **10** des Arbeitspeicher auf 0    |

# 6

## 6.a


| Mikrobefehl | Bedeutung                                                                                                    |
| ----------- | ------------------------------------------------------------------------------------------------------------ |
| JMP **10**  | Springt auf eine Stelle im Arbeitsspeicher bsp. **10**                                                       |
| TST **10**  | Testet ob der Wert null ist wenn dies eintrifft dann überspringt er die nächste Anweisung im Arbeitsspeicher |

# 6.b

Aufgabe: 10 \* 11 = 12

000 Null **12**
001 DEC **10**
002 Take **12**
003 ADD **11**
004 SAVE **12**
005 TST **10** 
006 JMP **1**


[[Multiplizieren.ram]]

# 7

## 7.a

Das Programm verändert veränder sich in der Zweiten Zeile selbst sodass es den zuvor Gespeicherten Wert nicht überschreibt.

## 7.b


000 Take 8
001 SAVE 101
002 DEC 9
003 INC 8
004 INC 1
005 INC 1
006 TST 9
007 JMP 0
008 42
009 13

# 8

## 8.a


$31 \cdot 32 \cdot 33 =35$

| Addresse | Asm  | Opnd |
| -------- | ---- | ---- |
| 0        | NULL | 35   |
| 1        | NULL | 34   |
| 2        | DEC  | 31   |
| 3        | TAKE | 34   |
| 4        | ADD  | 32   |
| 5        | SAVE | 34   |
| 6        | TST  | 31   |
| 7        | JMP  | 2    |
| 8        | DEC  | 34   |
| 9        | TAKE | 35   |
| 10       | ADD  | 33   |
| 11       | SAVE | 35   |
| 12       | TST  | 34   |
| 13       | JMP  | 8    |


[[3_Zahlen_Multipliezieren.ram]]

## 8.b


| Addresse | Asm  | Opnd |
| -------- | ---- | ---- |
| 0        | NULL | 22   |
| 1        | TAKE | 20   |
| 2        | SUB  | 21   |
| 3        | SAVE | 20   |
| 4        | INC  | 22   |
| 5        | TST  | 20   |
| 6        | JMP  | 1    |

[[Dividieren_Zwei_Zahlen.ram]]

## 8.c








![[03_AB_JohnnySimulator.pdf]]







