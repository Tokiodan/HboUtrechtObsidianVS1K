Een overzicht van wat je deze week hebt geleerd (opdracht PROG2.1 t/m 3.6).

Denk aan: expressies, input, `//` en `%`, `random`, if/elif/else, `and`/`or` en for-loops.

Met uitleg, voorbeelden en hoe je het zelf aanpakt.

  

---

  

## 1. Expressies & berekeningen (opdracht 2.1)

  

Een **expressie** is een stukje code dat een waarde uitrekent. Je stopt het resultaat vaak in een variabele.

  

```python

cijferPROJA = 8.0

cijferPROG = 7.5

cijferMOD = 7.0

  

gemiddelde = (cijferPROJA + cijferPROG + cijferMOD) / 3

beloning = (cijferPROJA + cijferPROG + cijferMOD) * 30

```

  

- De **haakjes** zijn belangrijk: eerst optellen, dan pas delen of keer doen.

- Zonder haakjes zou `a + b + c / 3` betekenen: eerst `c / 3`, dan de rest erbij. Dat is fout.

  

**Getallen aan tekst plakken** kan niet zomaar. Zet een getal eerst om naar string met `str(...)`:

  

```python

overzicht = 'Mijn cijfers (gemiddeld een ' + str(gemiddelde) + ') leveren een beloning van € ' + str(beloning) + ' op!'

print(overzicht)

```

  

**Let op:** `'tekst' + 5` geeft een `TypeError`. Het moet `'tekst' + str(5)` zijn.

  

---

  

## 2. Operator precedence (opdracht 2.2)

  

Python rekent in een vaste volgorde uit. Met **haakjes** bepaal jij wat er eerst gebeurt.

  

Belangrijk trucje: Python behandelt `True` als `1` en `False` als `0` in sommen.

  

```python

print(0 == (1 == 2))          # 1 == 2 is False (=0), dus 0 == 0 -> True

print(2 + (3 == 4) + 5 == 7)  # 3 == 4 is False (=0), dus 2 + 0 + 5 = 7 -> True

print((1 < -1) == (3 > 4))    # False == False -> True

```

  

Zonder haakjes worden vergelijkingen als een **keten** gelezen:

`0 == 1 == 2` betekent `0 == 1 AND 1 == 2`, wat `False` is.

  

**Kortom:** je verandert niks aan de getallen of tekens, alleen met haakjes stuur je de volgorde.

  

---

  

## 3. Input van de gebruiker (opdracht 2.3)

  

Met `input(...)` vraag je iets aan de gebruiker. Wat je terugkrijgt is **altijd tekst (string)**.

  

```python

uurloon = float(input('Wat verdien je per uur: '))

uren = int(input('Hoeveel uur heb je gewerkt: '))

```

  

Daarom zet je het meteen om:

  

| Functie | Zet om naar | Gebruik voor |

|---------|-------------|--------------|

| `int(...)` | heel getal | leeftijd, aantal, maandnummer |

| `float(...)` | kommagetal | uurloon, prijs met komma |

  

**Let op:** vergeet je `int(...)` en typ je `20`, dan is dat de tekst `'20'`. `'20' * 3` geeft dan `'202020'` in plaats van `60`.

  

```python

salaris = uurloon * uren

print(str(uren) + ' uur werken levert €' + str(salaris) + ' op')

```

  

---

  

## 4. Delen: `//` en `%` (opdracht 2.4 - wisselgeld)

  

Twee superhandige tekens bij hele getallen:

  

| Teken | Wat het doet | Voorbeeld | Uitkomst |

|-------|-------------|-----------|----------|

| `//` | hoe vaak past het er helemaal in | `107 // 50` | `2` |

| `%` | wat blijft er over (de rest) | `107 % 50` | `7` |

  

Hiermee reken je wisselgeld uit met zo min mogelijk munten. Werk van **grote naar kleine** munt:

  

```python

wisselgeld = 107

aantal50 = wisselgeld // 50   # 2 munten van 50

wisselgeld = wisselgeld % 50  # 7 blijft over

aantal5 = wisselgeld // 5     # 1 munt van 5

wisselgeld = wisselgeld % 5   # 2 blijft over

```

  

**Idee:** `//` geeft het *aantal* munten, `%` geeft de *rest* waarmee je verder gaat.

  

---

  

## 5. Willekeurige getallen met `random`

  

Wil je een willekeurig getal? Importeer bovenaan `random` en gebruik `randint`.

  

```python

import random

  

prijs = random.randint(10, 150)   # willekeurig getal van 10 t/m 150

```

  

`random.randint(a, b)` geeft een heel getal tussen `a` en `b`, allebei meegerekend.

  

---

  

## 6. If / else (opdracht 3.1)

  

Met `if` doe je iets **alleen als** een voorwaarde waar is.

  

```python

score = int(input('Geef je score: '))

  

if score > 15:

    print('Gefeliciteerd!')

    print('Met een score van ' + str(score) + ' ben je geslaagd!')

else:

    print('Helaas, je bent niet geslaagd!')

```

  

- Alles wat **inspringt** onder de `if` hoort erbij en gebeurt alleen als de voorwaarde waar is.

- Het `else` gebeurt in alle andere gevallen.

  

**Let op de inspringing (indentatie)!** Zet je de tweede `print` niet in maar helemaal links, dan hoort hij niet meer bij het `if` en wordt hij **altijd** uitgevoerd, ook als de voorwaarde onwaar is.

  

---

  

## 7. If met `and` en `or` (opdracht 3.2)

  

In één `if` kun je meerdere voorwaarden tegelijk checken.

  

```python

leeftijd = int(input('Geef je leeftijd: '))

paspoort = input('Nederlands paspoort: ')

  

if leeftijd >= 18 and paspoort == 'ja':

    print('Gefeliciteerd, je mag stemmen!')

else:

    print('Helaas, je mag niet stemmen!')

```

  

| Operator | Wanneer `True` |

|----------|----------------|

| `and` | als **beide** voorwaarden waar zijn |

| `or` | als **minstens één** voorwaarde waar is |

  

Zo heb je maar één `if` nodig in plaats van meerdere achter elkaar.

  

---

  

## 8. If / elif / else (opdracht 3.3 - seizoenen)

  

Meer dan twee mogelijkheden? Gebruik `elif` (else-if) ertussen.

  

```python

maand = int(input('Geef een maandnummer: '))

  

if maand < 1 or maand >= 13:

    seizoen = 'ongeldig'

elif maand >= 3 and maand <= 5:

    seizoen = 'lente'

elif maand >= 6 and maand <= 8:

    seizoen = 'zomer'

elif maand >= 9 and maand <= 11:

    seizoen = 'herfst'

else:

    seizoen = 'winter'   # 12, 1, 2

  

print(seizoen)

```

  

- Python checkt van boven naar beneden en **stopt bij de eerste die waar is**.

- Vang ongeldige invoer het liefst bovenaan af.

- Het `else` vangt alles op wat overblijft (hier: winter).

  

---

  

## 9. For-loop over een lijst (opdracht 3.4 & 3.5)

  

Met een `for`-loop doorloop je een lijst item voor item.

  

```python

dagen = ['maandag', 'dinsdag', 'woensdag']

  

for woord in dagen:

    print(woord[:2])   # eerste twee letters: ma / di / wo

```

  

- `woord` is elke ronde het volgende item uit de lijst.

- `woord[:2]` heet **slicing**: pak karakter 0 t/m 1 (de eerste twee).

  

**For + if samen** (alleen even getallen printen):

  

```python

getallen = [3, 8, 15, 42, 7, 10, 23, 6]

  

for getal in getallen:

    if getal % 2 == 0:   # rest 0 bij deling door 2 = even

        print(getal)

```

  

`getal % 2 == 0` is de standaardmanier om te checken of iets even is.

  

---

  

## 10. For-loop over een string (opdracht 3.6 - klinkers)

  

Een string kun je ook letter voor letter doorlopen.

  

```python

s = "Guido van Rossum heeft programmeertaal Python bedacht."

  

for letter in s:

    if letter in 'aeiou':

        print(letter)

```

  

- `for letter in s:` loopt langs elk karakter (ook spaties en leestekens).

- `letter in 'aeiou'` is `True` als de letter een (kleine) klinker is.

- Wil je hoofdletters meepakken? Gebruik `'aeiouAEIOU'`.

  

---

  

## Veelgemaakte foutjes (en hoe je ze herkent)

  

| Fout | Wat er misgaat | Oplossing |

|------|---------------|-----------|

| `'tekst' + 5` | getal aan tekst plakken → `TypeError` | `'tekst' + str(5)` |

| `input(...)` zonder `int`/`float` | je rekent met tekst, `'2' + '3'` = `'23'` | `int(input(...))` |

| `if x = 5:` | `=` is toewijzen | vergelijken doe je met `==` |

| tweede `print` niet ingesprongen | hoort niet meer bij het `if` | netjes inspringen onder het `if` |

| `elif` vergeten, losse `if`'s | meerdere blokken worden los gecheckt | gebruik `if / elif / else` als het bij elkaar hoort |

| `randint(10, 150)` grenzen | beide grenzen tellen mee (10 én 150) | check of dat is wat je wilt |

| haakjes vergeten bij `%`/`//` | verkeerde volgorde | reken munt voor munt met `//` en `%` |

  

---

  

## Zo pak je een opdracht aan (stappenplan)

  

1. **Lees de vraag goed.** Wat vraag je aan de gebruiker (input) en wat moet eruit komen?

2. **Zet input om naar het juiste type** met `int(...)` of `float(...)`.

3. **Kies je bouwsteen:**

   - één voorwaarde → `if` (+ eventueel `else`)

   - meerdere voorwaarden tegelijk → `and` / `or`

   - meer dan twee gevallen → `if / elif / else`

   - iets herhalen voor elk item → `for`-loop

4. **Print het resultaat** zodat je het in de terminal ziet (`str(...)` om getallen).

5. **Draai het** en vergelijk met de voorbeelduitvoer.

6. **Test met andere waarden** (te weinig geld, ongeldige maand, oneven getal) om te zien of het altijd klopt.