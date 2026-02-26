# Ugeopgave: Genbrug ved hjælp af komposition og arv

Denne opgave har tre dele. Du bestemmer selv hvor meget tid du bruger på hver.

---

## Del 1: En bygning med rum

Byg et system der kan holde styr på en bygning med rum, lamper og vinduer.

### Klasserne

**`Lamp`**
- Felter: `watt` (int), `isOn` (boolean)
- Konstruktør: tager `watt` som parameter, `isOn` starter som `false`
- Metoder: `void turnOn()`, `void turnOff()`, `toString()`

**`Window`**
- Felter: `widthCm` (int), `heightCm` (int)
- Konstruktør: tager bredde og højde
- Metoder: `int getAreaCm2()`, `toString()`

**`Room`**
- Felter: `name` (String), `lamps` (ArrayList\<Lamp\>), `windows` (ArrayList\<Window\>)
- Konstruktør: tager `name`
- Metoder:
    - `void addLamp(Lamp lamp)`
    - `void addWindow(Window window)`
    - `int getLampCount()`
    - `int getTotalWatt()` — sum af alle lampernes watt
    - `int getTotalWindowArea()` — sum af alle vinduers areal
    - `void printRoom()`

**`Building`**
- Felter: `name` (String), `rooms` (ArrayList\<Room\>)
- Konstruktør: tager `name`
- Metoder:
    - `void addRoom(Room room)`
    - `int getTotalLampCount()` — total antal lamper i hele bygningen
    - `int getTotalWatt()` — samlet wattal for hele bygningen
    - `void printBuilding()` — printer alle rum med deres lamper og vinduer

### Krav til main

Opret en bygning med mindst tre rum. Hvert rum skal have mindst to lamper og ét vindue. Print bygningen og svar på:
- Hvor mange lamper er der i hele bygningen?
- Hvad er det samlede wattal?

Forventet output (eksempel):
```
=== Kontorbygningen ===

Mødelokale (3 lamper, 2 vinduer)
  Lamper: 60W, 60W, 100W (total: 220W)
  Vinduer: 120x90cm, 120x90cm

Køkken (2 lamper, 1 vindue)
  Lamper: 40W, 40W (total: 80W)
  Vinduer: 60x60cm

Total: 8 lamper, 540W
```

---

## Del 2: Dyr der konkurrerer

Byg et system hvor dyr konkurrerer mod hinanden. Hvert dyr har et navn og en mængde energi — når energien når nul, er dyret ude af konkurrencen.

### Superklassen

Lav en klasse `Animal` med felterne:
- `name` (String)
- `energy` (int)

Lav konstruktør, relevante getters/setters, og en metode `boolean isActive()` der returnerer `true` hvis `energy` er større end 0.

Lav en metode `int attack()` der returnerer hvor meget energi dyret trækker fra sin modstander. Du bestemmer selv om den skal være abstrakt eller konkret — tænk over hvad der giver mest mening.

Lav en `toString()` der fx printer:
```
Lion "Simba" (energi: 80)
```

### Subklasserne

Lav mindst **tre** subklasser der nedarver fra `Animal`. De skal kalde `super()` i konstruktøren og implementere (eller override) `attack()` på hver sin måde:

- `Lion` — trækker altid et fast højt beløb
- `Wolf` — trækker et tilfældigt beløb
- `Rabbit` — trækker et lavt beløb men starter med meget energi

### Konkurrencen

Lav en klasse `Contest` med to `Animal`-felter og en tæller for antal runder.

Tilføj metoden `void playRound()` der lader de to dyr angribe hinanden og printer hvad der sker:
```
--- Runde 1 ---
Simba angriber Rabbit for 15! (Rabbit har 45 energi tilbage)
Rabbit angriber Simba for 4! (Simba har 76 energi tilbage)
```

Tilføj en metode `Animal getWinner()` der returnerer vinderen (eller `null` hvis begge stadig er aktive).

### Krav til main

Opret mindst fire dyr af mindst tre forskellige typer. Gem dem i en `ArrayList<Animal>`.

Lad dem konkurrere i par og print vinderen af hver kamp.

---

## Del 3: Kig på din SP1-opgave

Tag din SP1-kode og svar på følgende. Skriv svarene som kommentarer i koden eller i en separat fil.

**Komposition (has-a):** Find mindst ét sted hvor du allerede bruger komposition. Hvilke to klasser? Hvad er relationen?

**Nedarving (is-a):** Er der klasser der ligner hinanden — deler de felter eller metoder? Kunne de arve fra en fælles superklasse? Hvad ville den hedde?

Det er ikke et krav at du ændrer din kode — det er nok at du identificerer mulighederne.

---

## Review fredag

Til review skal du kunne forklare:
- Tegn et diagram over klasserne i Del 1 og Del 2 med has-a og is-a pile
- Hvad er fordelen ved `Building.getTotalLampCount()` frem for at tælle i `main`?
- Hvornår ville det give mening at gøre `Animal` abstrakt?
