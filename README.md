# DB-Test
## Aufgabe 1
Stelle Entitäten mittels Chen-Notation und Min,Max Notation dar.
Wähle ein sinnvolles Beispiel!
<pre>
___________                         ___________
| Camera   |_1,1____ shoots __1,*__ |   Foto  |
|__________|                        |_________|
</pre>

## Aufgabe 2
Kann eine Beziehung Attribute haben?
Wenn ja, wie stelle ich es im ERD dar?
<pre>
___________                          _____________
| Lehrer  |_1___ teach subject ___N__|  Schüler  |
|_________|           |              |___________|
                    Mark
</pre>
## Aufgabe 3
Welche Codd'schen Anforderungen gibt es (Nenne mindestens 5)

Katalog
Operation
Benutzerschichten
Integration
Transaktion
Integretätssicherung
Datensicherung
Zugriffskontrolle

## Aufgabe 4
Nenne den Unterschied zwischen Konzeptuellen und Logischem Schema

Konzeptuellen Schema ist eine wolke in dem die Entity und Attribute.
in einem Logischen Schema sind die Entity mit relationships verbunden und Attribute sind den Entitys und relationships zugewiesen.

## Aufgabe 5
Welche 3 Bestandteile gibt es im Entity Relationship Model

Entity 
Releationship 
Attribut

## Aufgabe 6
Welche Datentypen gibt es in MySQL? (Nenne mindestens 5)

varchar
int
boolean
double
float
char
timestamp

## Aufgabe 7
Welche Arten von Schlüsseln gibt es und welche Eigenschaften besitzen diese?#

PrimärSchlüssel: Identifizieren die Tabele es kann eine generierte ID sein oder ein natürlicher Schlüssel der einzigartig ist wie die SVN einer Person

FremdSchlüssel: verweist auf eine anderen Datensatz

## Aufgabe 8
Welche Arten von Beziehungen gibt es? Zeichne für jede ein Beispiel auf
<pre>
unäre
____________
| Schüler  |
|__________|
|          |
|Erziehungs|
 berechtigt

duale(binär)
____________                        ___________
| Camera   |_1____ shoots ______N__ |   Foto  |
|__________|                        |_________|
                   
Trinäre
____________                          ____________
| Entity A |__M____ relatioship ___N__| Entity B |
|__________|  M          |         M  |__________|
                       N | N
                   |¯¯¯¯¯¯¯¯¯¯¯|
                   | Entity C  |
                   ¯¯¯¯¯¯¯¯¯¯¯¯¯
</pre>
## Aufgabe 9
Was bedeutet der Begriff Kardinalität und welche Kardinalitäten gibt es?

Sie geben an wie die Beziehung der Entitys sind

1:1             Für Entity A gibt es genau eine Entity B und umgekehrt
1:N (N:1)       Entity A hat viele Entity B und jede B Entity hat genau eine A 
M:N             Eine Entity A hat viele Entity B und eine Entity B hat viele Entity A

## Aufgabe 10
Was bedeutet der Begriff Datenintegrität und worin unterscheidet sich Integrität und referentielle Integrität?

Datenintegrität beschreibt die Korrektheit der Daten.
Referentielle Integrität beschreibt die Korrektheit der Beziehungen.

## Aufgabe 11
Erkläre die 3 Normalformen

In der ersten Normalform werden die Datensätze auf Atomare Form heruntergebrochen
In der zweiten Normalform sind alle Daten vom PrimärSchlüssel abhänig.
In der dritten Normalform sind die Daten die keine Schlüssel sind unabhänig von einander.

## Aufgabe 12
Erkläre den Unterschied zwischen starken und Schwachen Entitäten und erstelle ein Beispiel.

Schwache Entitäten sind nur in Kombination mit dem Schlüssel der starken Entity identifizierbar.

## Aufgabe 13
Welche Grundregeln gibt es im Relationenmodell? (Nenne mindestens 4)

Bei der Textuelle notation in den die Entity mit den Attribute und den Datentypen
PrimärSchlüssel sind unterstriechen.
FremdSchlüssel sind strichliert unterstriechen.

## Aufgabe 14
Wie löst man eine M:N Beziehung auf? Erstelle ein Beispiel
<pre>
______________                    _____________
| Hersteller |_M___produziert___N_|  Artikel  |
|____________|                    |___________|
______________        ______________       _____________ 
| Hersteller |_1___N_ | produziert |_N___1_|  Artikel  |
|____________|        |_A_H________|       |___________|

produziert_A_H ist eine Entity
in produziert_A_H stehen die Schlüssel von Hersteller und Artikel als Fremdschlüssel (diese beiden Fremschlüssel werden als PrimärSchlüssel hergenommen)
</pre>

## Aufgabe 15
Ein Handelsbetrieb verkauft ein Sortiment von Artikeln, die er von verschiedenen Herstellern bezieht. Der Handelsbetrieb hat einen bestimmten Kundenkreis, der regelmäßig Bestellungen aufgibt. Eine Bestellung kann mehrere Artikel umfassen. Ein Artikel kann von mehreren Lieferanten bezogen werden und ein Lieferant liefert natürlich meist mehr als einen Artikel. Erstelle ein ERD und ein Relationenmodell, welches der 3. Normalform entspricht.
<pre>
______________        ______________       _____________        ___________       _____________
| Hersteller |_1___N_ | produziert |_N___1_|  Artikel  |_1___N_ | bezieht |_N___1_| Lieferant |
|____________|        |_A_H________|       |___________|        |_A_L_____|       |___________|
                                                |       _______________       ______________
                                                ∟_1___N_| umfasst_A_B |_N___1_| Bestellung |
                                                        |_____________|       |____________|

Hersteller:
Key:    Hersteller_ID: int
        Name: varchar
        Adresse: varchar
        ...

produziert_A_H:
key,fkey:   Hersteller_ID: int
key,fkey:   Artikel_ID: int

Artikel:
key:    Artikel_ID: int
        Name: varchar
        Beschreibung: varchar
        ...

bezieht_A_L:
key,fkey:    Artikel_ID: int
key,fkey:    Lieferant_ID: int

Lieferant:
key:    Lieferant_ID: int
        name: varchar
        Beschreibung: varchar
        ...

umfasst_A_B:
key,fkey:    Artikel_ID: int
key,fkey:    Bestellung_ID: int

Bestellung
key:    Bestellung_ID: int
        name des Kunden: varchar
        Adresse: varchar
        ...
</pre>

## Aufgabe 16
Welche Anomalien kennst du und was beschreiben sie?

Erstellungs Anomalien, Änderungs Anomalien und die Lösungs Anomalien

Es sollen immer nur so viel Daten ein getragen werden wie angegeben
Es sollen immer nur genau so viele Daten geändert werden wie angegeben
Es sollen immer nur genau so viele Daten gelöscht werden wie angegeben 
sonst entsteht eine Anomalie.

## Aufgabe 17
Modellieren Sie den angeführten Realitätsausschnitt einer Fluggesellschaft mit Hilfe eines Entity Relationship- Diagramms. Treffen Sie, falls notwendig, sinnvolle Annahmen und dokumentieren Sie diese nachvollziehbar in Ihrer Lösung. Der zu betrachtende Realitätsausschnitt der Fluggesellschaft umfasst folgenden
Sachverhalt:
Flughäfen haben ein Kürzel (= Schlüssel) und gehören zu einer Stadt (z.B. „FRA“ für Frankfurt, „FCO“ für Roma Fiumicino).
Flüge haben eine Flugnummer (z.B. „LH 306“), führen von einem Flughafen zu einem anderen, mit jeweils einer festen Abflugs- und Ankunftszeit (z.B. ab Frankfurt um 07:30 nach Roma Fiumicino mit Ankunft um 09:15).
Jeder Flugzeugtyp hat einen Namen (z.B. „747-400“) und eine Sitzanzahl (z.B. 430 Sitze).
Piloten haben einen Namen (z.B. „Meier“), ein Geburtsdatum (z.B. „1.1.1960“) und eine Berechtigung, bestimmte Flugzeugtypen zu fliegen (z.B. „747-400“ und „A310“).
Jedes einzelne Flugzeug ist von einem bestimmten Flugzeugtyp (z.B. „747-400“) und hat einen Namen (z.B. „Mozart“).
Bei einem Flug-Einsatz wird ein Flug (z.B. „LH 306“) an einem bestimmten Datum (z.B. „6.2.2011“) von einem bestimmten Piloten (z.B. „Meier“) mit einem bestimmten Flugzeug (z.B. „Mozart“) geflogen.
Bilden Sie das konzeptuelle Schema in ein relationales Schema ab. Das relationale Schema soll der 3. Normalform genügen
<pre>
________                _____________       ____________        ____________       _____________
| Flug |_N__startet__1__| Flughafen |_1___N_| Flugzeug |_1___N_ | fliegt   |_N___1_| Pilot     |
|______|_N__landet___1__|___________|       |__________|        |_FZ_P_____|       |___________|
  |   |                                           |                                       |
  |   ∟__1________einsatz______________________1__|                                       |
  |                                                                                       |
   ∟__1___________dienst_______________________________________________________________1__|

Flughafen:
key:    Kürzel: varchar
key:    StadtKürzel: varchar

Flug:
key:    Flugnummer: int
fkey:   AbflugFlughafen
            -Kürzel
            -StadtKürzel
fkey:   AnkunftFlughafen
            -Kürzel
            -StadtKürzel
        Ankunftzeit: timestamp
        Abflugzeit: timestamp
        datum: timestamp

Flugzeug:
key:        Flugzeug_ID: int
key,fkey:   Flugnummer: int
            Flugzeugtyp: varchar
            Sitzanzahl: int

fliegt_FZ_P:
key,fkey:    Flugzeug_ID: int
key,fkey:    Pilot_SVN: int

Pilot:
key:    Pilot_SVN: int
        Namen: varchar
        Geburtsdatum: timestamp
        Berechtigung: varchar
</pre>