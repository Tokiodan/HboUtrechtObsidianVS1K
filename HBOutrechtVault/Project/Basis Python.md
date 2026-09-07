# Python basis - uitleg & spiekbriefje

  

Een overzicht van de basis die je tot nu toe hebt geleerd (opdracht PROG1.1 t/m 1.7).

Met uitleg, voorbeelden en hoe je het zelf aanpakt.

  

---

  

## 1. Variabelen

  

Een variabele is een "doosje" met een naam waar je een waarde in stopt. Je maakt hem met `=`.

  

```python

a = 6

b = 7

naam = 'Dani'

```

  

- Links van de `=` staat de **naam**, rechts de **waarde**.

- Je kunt de waarde later overschrijven: `a = 10` maakt van `a` nu 10.

- Gebruik duidelijke namen (`voornaam` is beter dan `n1`), dan snap je later nog wat er staat.

  

**Let op:** als je dezelfde naam twee keer gebruikt, overschrijf je de eerste.

```python

x = 'hoi'

x = 'doei'   # x is nu 'doei', 'hoi' is weg

```

  

---

  

## 2. Datatypes (soorten waarden)

  

| Type | Wat het is | Voorbeeld |

|------|-----------|-----------|

| `int` | heel getal | `5`, `-2`, `100` |

| `float` | kommagetal | `5.0`, `6.5`, `3.14` |

| `str` | tekst (string) | `'Dani'`, `'ice'` |

| `bool` | waar/onwaar | `True`, `False` |

| `list` | lijst (aanpasbaar) | `['a', 'b', 'c']` |

| `tuple` | lijst (niet aanpasbaar) | `('A', 'B', 'C')` |

  

Type opvragen kan met `type(...)`:

```python

print(type(5))       # <class 'int'>

print(type(5.0))     # <class 'float'>

print(type('5'))     # <class 'str'>

```

  

**Belangrijk:** `5` (getal) en `'5'` (tekst) zijn niet hetzelfde!

  

---

  

## 3. Rekenen met getallen

  

| Teken | Wat het doet | Voorbeeld | Uitkomst |

|-------|-------------|-----------|----------|

| `+` | optellen | `6 + 7` | `13` |

| `-` | aftrekken | `10 - 3` | `7` |

| `*` | vermenigvuldigen | `5 * 2` | `10` |

| `/` | delen (altijd float) | `10 / 2` | `5.0` |

| `//` | delen naar beneden afgerond | `6 // 7` | `0` |

| `%` | rest na deling (modulo) | `5 % 2` | `1` |

  

**Gemiddelde berekenen** (uit opdracht 3):

```python

c = (a + b) / 2

```

De haakjes zijn belangrijk! Python rekent `*` en `/` eerst uit, dan pas `+` en `-`.

Zonder haakjes zou `a + b / 2` betekenen: eerst `b / 2`, dan `+ a`. Dat is fout.

  

---

  

## 4. Strings (tekst)

  

Een string schrijf je tussen aanhalingstekens: `'...'` of `"..."`.

  

```python

voornaam = 'Dani'

```

  

**Lengte tellen** met `len()`:

```python

print(len('Supercalifragilisticexpialidocious'))   # 34

```

  

**Aan elkaar plakken** met `+` (dit heet "concatenatie"):

```python

mijnnaam = voornaam + ' ' + tussenvoegsel + ' ' + achternaam

# 'Dani Migeal Bouzidi'

```

De `' '` (spatie) zet je er zelf tussen, anders plakt alles vast: `DaniMigealBouzidi`.

  

**Zit iets erin?** met `in`:

```python

print('ice' in 'Supercalifragilisticexpialidocious')   # True

```

  

---

  

## 5. Boolean expressies (waar / onwaar)

  

Een boolean is `True` of `False`. Je krijgt hem als je iets vergelijkt.

  

| Teken | Betekenis | Voorbeeld | Uitkomst |

|-------|-----------|-----------|----------|

| `>` | groter dan | `5 > 1` | `True` |

| `<` | kleiner dan | `5 < 1` | `False` |

| `>=` | groter of gelijk | `5 >= 5` | `True` |

| `<=` | kleiner of gelijk | `4 <= 3` | `False` |

| `==` | gelijk aan | `5 == 5` | `True` |

| `!=` | niet gelijk aan | `5 != 4` | `True` |

  

**Let op:** `=` is toewijzen (variabele maken), `==` is vergelijken. Verwar ze niet!

  

**Combineren** met `and` en `or`:

```python

print(6.75 > a and 6.75 < b)   # True als BEIDE waar zijn

```

- `and` = allebei moeten waar zijn

- `or` = minstens één moet waar zijn

  

Voorbeelden uit opdracht 4:

```python

print(len(mijnnaam) == len(voornaam) + len(tussenvoegsel) + len(achternaam))

print(len(mijnnaam) >= 5 * c)

print(tussenvoegsel in achternaam)

```

  

---

  

## 6. Lists (lijsten)

  

Een lijst is een rij met waarden tussen blokhaken `[ ]`. Je kunt hem aanpassen.

  

```python

favorieten = ['Kendrick Lamar']

```

  

**Index** = plek in de lijst. Python telt vanaf **0**!

```python

lijst = ['a', 'b', 'c']

print(lijst[0])    # 'a'  (eerste)

print(lijst[1])    # 'b'  (tweede)

print(lijst[-1])   # 'c'  (laatste)

```

  

**Uitbreiden** met `.append(...)` (zet er iets achteraan):

```python

favorieten.append('Drake')     # ['Kendrick Lamar', 'Drake']

```

  

**Vervangen** via de index:

```python

favorieten[1] = 'Eminem'      # tweede item wordt vervangen

```

  

**Sorteren** met `.sort()` (zonder iets tussen de haakjes!):

```python

namen = ['Berlioz', 'Bartok', 'Bellini']

namen.sort()

print(namen[0])    # eerste in alfabet

print(namen[-1])   # laatste in alfabet

```

`sort()` verandert de lijst zelf en geeft NIETS terug. `print(namen.sort())` geeft dus `None`.

  

---

  

## 7. Handige functies voor lijsten en getallen

  

| Functie | Wat het doet | Voorbeeld |

|---------|-------------|-----------|

| `len(x)` | aantal items / lengte | `len([1,2,3])` = `3` |

| `min(x)` | kleinste waarde | `min([3, 7, -2])` = `-2` |

| `max(x)` | grootste waarde | `max([3, 7, -2])` = `7` |

| `sum(x)` | alles opgeteld | `sum([1, 2, 3])` = `6` |

| `x.count(item)` | hoe vaak item voorkomt | zie tuples |

  

**Bereik berekenen** (opdracht 6) = grootste min kleinste:

```python

lst = [3, 7, -2, 12]

print(max(lst) - min(lst))    # 14

```

Dit werkt met ELKE lijst getallen, want `max` en `min` zoeken zelf uit wat het grootst/kleinst is.

  

---

  

## 8. Tuples

  

Een tuple lijkt op een lijst, maar staat tussen ronde haakjes `( )` en kun je NIET aanpassen.

  

```python

letters = ('A', 'C', 'B', 'B', 'C', 'A', 'C', 'C', 'B')

```

  

**Tellen** met `.count(...)`:

```python

print(letters.count('A'))   # 2

```

  

**Opdracht 7** - aantal voorkomens in alfabetische volgorde:

```python

letters = ('A', 'C', 'B', 'B', 'C', 'A', 'C', 'C', 'B')

aantallen = [letters.count('A'), letters.count('B'), letters.count('C')]

print(aantallen)    # [2, 3, 4]

```

Je maakt een nieuwe lijst en zet daar de drie tellingen in, netjes in volgorde A, B, C.

  

---

  

## 9. Printen (resultaat laten zien)

  

`print(...)` zet iets op je scherm.

  

```python

print('Hallo')          # Hallo

print(6.5)              # 6.5

print(a + b)            # 13

```

  

Verschil tussen **expressie** en **printen**:

- Een expressie *berekent* een waarde (`(a + b) / 2`).

- `print(...)` *laat* die waarde *zien*.

  

Wil je het antwoord in de terminal zien? Dan moet er `print(...)` omheen.

  

---

  

## Veelgemaakte foutjes (en hoe je ze herkent)

  

| Fout | Wat er misgaat | Oplossing |

|------|---------------|-----------|

| `priont(...)` | typefout in `print` | goed spellen |

| `naam = Dani` | tekst zonder aanhalingstekens → `NameError` | `naam = 'Dani'` |

| `c = a % b` als gemiddelde | `%` is rest, geen gemiddelde | `c = (a + b) / 2` |

| `lijst.sort(lijst)` | niks tussen haakjes zetten → `TypeError` | `lijst.sort()` |

| `x = 5` vs `x == 5` | `=` toewijzen, `==` vergelijken | juiste teken kiezen |

| `mijnnaam = a + b` (plakt vast) | spaties vergeten | `a + ' ' + b` |

  

---

  

## Zo pak je een opdracht aan (stappenplan)

  

1. **Lees de vraag goed.** Wat is de input, wat moet eruit komen?

2. **Kies het juiste type.** Tekst → string, getallen → int/float, meerdere dingen → list/tuple.

3. **Bedenk welke functie past.** Tellen? `len` of `.count`. Grootste/kleinste? `max`/`min`.

4. **Schrijf de expressie** en zet er `print(...)` omheen om het te zien.

5. **Draai het** en check of de uitkomst klopt met wat de opdracht vraagt.

6. **Werkt het altijd?** Test met andere waarden als de opdracht daarom vraagt.