  
  

Alles over functies uit opdracht PROG4.1 t/m 4.4.

Met uitleg, voorbeelden en hoe je het zelf aanpakt.

  

---

  

## Wat is een functie?

  

Een **functie** is een stukje code met een naam dat je steeds opnieuw kunt gebruiken.

Je maakt hem met `def`, geeft er waarden aan mee (parameters) en krijgt een antwoord terug met `return`.

  

```python

def naam(parameter1, parameter2):

    # code die inspringt hoort bij de functie

    return resultaat

```

  

- `def` = start van de functie.

- Tussen de haakjes staan de **parameters** (de waarden die binnenkomen).

- `return` geeft de uitkomst **terug** naar waar je de functie aanriep.

- **Aanroepen** doe je met de naam en waarden ertussen: `naam(3, 5)`.

  

**Verschil `return` en `print`:**

- `return` geeft de waarde *terug* zodat je er verder mee kunt (opslaan, printen, rekenen).

- `print` zet alleen iets op het scherm.

- Test een `return`-functie dus door hem te printen: `print(naam(...))`.

  

---

  

## 4.1 - Functie met drie parameters

  

Schrijf `som()` met 3 parameters die de optelling teruggeeft.

  

```python

def som(getal1, getal2, getal3):

    return getal1 + getal2 + getal3

  

print(som(3, 5, 7))       # 15

print(som(10, 20, 30))    # 60

```

  

De getallen die je meegeeft (`3, 5, 7`) heten **argumenten**. Ze vullen in volgorde de parameters `getal1, getal2, getal3`.

  

---

  

## 4.2 - Functie met een lijst als parameter

  

Nu krijgt `som()` één parameter: een hele lijst met getallen. Gebruik de kant-en-klare functie `sum(...)`.

  

```python

def som(getallenLijst):

    return sum(getallenLijst)

  

print(som([3, 5, 7]))         # 15

print(som([10, 20, 30, 40]))  # 100

```

  

- `sum(lijst)` telt alle getallen in de lijst bij elkaar op. Dat scheelt een for-loop.

- Verwar `sum` (kant-en-klare functie van Python) niet met `som` (jouw eigen functie).

  

**Mag ook met een for-loop** (als je het zelf wilt optellen):

  

```python

def som(getallenLijst):

    totaal = 0

    for getal in getallenLijst:

        totaal = totaal + getal

    return totaal

```

  

---

  

## 4.3 - Functie met een if (Efteling-attractie)

  

De functie geeft afhankelijk van de lengte een andere tekst terug.

  

```python

def lang_genoeg(lengte):

    if lengte >= 120:

        return 'Je bent lang genoeg voor de attractie!'

    else:

        return 'Sorry, je bent te klein!'

  

print(lang_genoeg(130))   # lang genoeg

print(lang_genoeg(120))   # lang genoeg (120 telt mee door >=)

print(lang_genoeg(110))   # te klein

```

  

- `>=` betekent "groter dan of gelijk aan", dus 120 telt nog mee.

- Je kunt een functie ook een **string** laten teruggeven, niet alleen een getal.

- Zodra `return` wordt uitgevoerd, stopt de functie meteen.

  

---

  

## 4.4 - Functie met if met meerdere condities (wachtwoord)

  

Het nieuwe wachtwoord is alleen goed als het:

- verschilt van het oude wachtwoord, **en**

- minimaal 6 tekens lang is, **en**

- minstens 1 cijfer bevat (optionele eis).

  

```python

def new_password(oldpassword, newpassword):

    # Eerst kijken of er een cijfer in het nieuwe password zit

    bevat_cijfer = False

    for teken in newpassword:

        if teken.isdigit():        # True als het teken een cijfer is

            bevat_cijfer = True

  

    if newpassword != oldpassword and len(newpassword) >= 6 and bevat_cijfer:

        return True

    else:

        return False

  

print(new_password('geheim', 'nieuw12'))   # True

print(new_password('geheim', 'geheim'))    # False (zelfde)

print(new_password('geheim', 'abc1'))      # False (te kort)

print(new_password('geheim', 'abcdefg'))   # False (geen cijfer)

```

  

Wat hier gebeurt:

- `!=` betekent "niet gelijk aan" (het nieuwe moet anders zijn dan het oude).

- `len(newpassword) >= 6` checkt de lengte.

- `teken.isdigit()` is `True` als een los teken een cijfer is (`'5'.isdigit()` → True, `'a'.isdigit()` → False).

- Met de for-loop lopen we langs elk teken; vinden we een cijfer, dan zetten we `bevat_cijfer` op `True`.

- De drie eisen combineren we met `and`: alle drie moeten waar zijn.

  

**Zonder de optionele cijfer-eis** zou het zo kunnen:

  

```python

def new_password(oldpassword, newpassword):

    if newpassword != oldpassword and len(newpassword) >= 6:

        return True

    else:

        return False

```

  

---

  

## Veelgemaakte foutjes (en hoe je ze herkent)

  

| Fout | Wat er misgaat | Oplossing |

|------|---------------|-----------|

| `return` maar niks zien | je print het resultaat niet | `print(functie(...))` |

| `print` i.p.v. `return` | je kunt er daarna niks mee rekenen | gebruik `return` |

| code niet ingesprongen onder `def` | hoort niet bij de functie | netjes inspringen |

| `som` vs `sum` door elkaar | eigen functie vs Python-functie | let op de naam |

| eisen los met meerdere `if`'s | wordt niet in één keer gecheckt | combineer met `and` |

| `=` i.p.v. `==` of `!=` | `=` is toewijzen | vergelijken met `==` / `!=` |

  

---

  

## Zo pak je een functie-opdracht aan (stappenplan)

  

1. **Lees de opdracht:** hoeveel parameters, en wat moet de functie teruggeven?

2. **Schrijf de kop:** `def naam(parameters):`.

3. **Bedenk de logica:** optellen? `+` of `sum`. Keuze maken? `if / else`. Meerdere eisen? `and`.

4. **Gebruik `return`** om het antwoord terug te geven (niet `print` binnen de functie).

5. **Test de functie** door hem aan te roepen binnen een `print(...)`, met verschillende waarden.

6. **Check de grensgevallen:** precies 120 cm, precies 6 tekens, lege lijst, enzovoort.