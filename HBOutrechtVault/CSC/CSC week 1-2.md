# CSC - Netwerken spiekbriefje

  

Een overzicht van de netwerkbasis uit CSC2.1 en CSC2.2.

Met uitleg, voorbeelden, de stappen op Windows en veelgemaakte foutjes.

  

---

  

## 1. Wat is een IP-adres?

  

Een IP-adres is het "huisnummer" van een apparaat in een netwerk. Elk apparaat heeft er een nodig om te kunnen praten met andere apparaten.

  

Een IPv4-adres bestaat uit 4 getallen (0-255) met puntjes ertussen:

```

10.0.1.3

```

- Elk getal heet een **octet** (8 bits).

- `10.0.1` is hier het netwerkdeel, `.3` is het apparaatdeel (host).

  

**Jouw groepsreeks** (X = groepsnummer):

```

10.0.X.1  t/m  10.0.X.10

```

| Groep | Start | Eind | Netwerkmasker |

|-------|-------|------|---------------|

| 1 | 10.0.1.1 | 10.0.1.10 | 255.255.255.0 |

| 2 | 10.0.2.1 | 10.0.2.10 | 255.255.255.0 |

| 3 | 10.0.3.1 | 10.0.3.10 | 255.255.255.0 |

| ... | ... | ... | 255.255.255.0 |

  

---

  

## 2. Wat is een netwerkmasker (subnetmask)?

  

Het masker (`255.255.255.0`) bepaalt welk deel van het IP-adres het **netwerk** is en welk deel het **apparaat**.

  

- `255` = "dit stuk is het netwerk, moet hetzelfde zijn"

- `0` = "dit stuk mag verschillen (de apparaten)"

  

Bij `255.255.255.0`:

- `10.0.1` = netwerkdeel (moet gelijk zijn voor alle pc's in de groep)

- laatste getal = het apparaat (mag 1 t/m 254 zijn)

  

**Gevolg:** `10.0.1.3` en `10.0.1.2` zitten in hetzelfde netwerk (kunnen elkaar direct bereiken). `10.0.1.3` en `10.0.2.3` zitten in een ANDER netwerk (daar heb je een router voor nodig).

  

---

  

## 3. IP-adres instellen op Windows (statisch)

  

Dit heb je bij CSC2.1 gedaan:

  

1. **Zoeken / Search** → "Netwerkverbindingen" / Network Connections

2. Klik op **Ethernet** → **Eigenschappen** / Properties

3. Selecteer **Internet Protocol Version 4 (TCP/IPv4)** → **Eigenschappen**

4. Kies **"Het volgende IP-adres gebruiken"** en vul in:

   - IP-adres: bijv. `10.0.1.3`

   - Subnetmasker: `255.255.255.0`

   - DNS: **hoef je nu niet in te vullen** (we pingen op IP, niet op naam)

  

---

  

## 4. Pingen (test of een apparaat bereikbaar is)

  

`ping` stuurt een klein pakketje naar een IP-adres en kijkt of er antwoord komt. Handig om te testen of een verbinding werkt.

  

Open **Opdrachtprompt** (cmd) of **PowerShell** en typ:

```

ping 10.0.1.2

```

  

**Geslaagd** ziet er zo uit (je krijgt "Reply from"):

```

Reply from 10.0.1.2: bytes=32 time=3ms TTL=115

...

Packets: Sent = 4, Received = 4, Lost = 0 (0% loss)

```

- `Reply from` = het apparaat antwoordt → verbinding werkt

- `Lost = 0` = geen pakketten kwijt → goed

- `time=3ms` = hoe snel het antwoord kwam

  

**Mislukt** ziet er zo uit:

- `Request timed out` = geen antwoord

- `Destination host unreachable` = geen route naar dat adres

  

---

  

## 5. Als pingen niet lukt (checklist)

  

| Probleem | Oplossing |

|----------|-----------|

| Verkeerd IP-adres gebruikt | Check het adres van je medestudent |

| Netwerkkabel niet aangesloten | Kabel/USB-adapter goed erin? |

| Firewall van medestudent staat dicht | Firewall (heel) tijdelijk uitzetten |

| Niet in hetzelfde netwerk | Zelfde `10.0.X` en `255.255.255.0`? |

  

---

  

## 6. Netwerken koppelen met een router (CSC2.2)

  

Een **switch** verbindt apparaten binnen één netwerk. Een **router** koppelt verschillende netwerken aan elkaar.

  

- Sluit de switch aan op een routerpoort: gebruik **eth1, eth2, eth3** (per 3 groepen).

- **eth0 en eth4** worden nu niet gebruikt.

  

Zo kun je apparaten in ANDERE netwerken bereiken:

```

ping 192.168.x.y

```

  

---

  

## 7. DHCP (automatisch een IP-adres krijgen)

  

Bij CSC2.1 stelde je het IP-adres handmatig in (statisch). Met **DHCP** krijgt je laptop automatisch een adres van de router.

  

Instellen op Windows:

1. TCP/IPv4 eigenschappen (zelfde menu als hierboven)

2. Kies **"Automatisch een IP-adres verkrijgen"** (DHCP)

  

**Controleren welk adres je hebt gekregen:**

```

ipconfig /all

```

Dit toont je IP-adres, subnetmasker en meer. Handig om aan de docent te laten zien dat DHCP werkt.

  

De Raspberry Pi bereiken via ping:

```

ping 192.168.1.2    (Raspberry Pi A)

ping 192.168.4.2    (Raspberry Pi B)

```

  

---

  

## 8. Handige commando's (cmd / PowerShell)

  

| Commando | Wat het doet |

|----------|-------------|

| `ping <ip>` | test of een apparaat bereikbaar is |

| `ipconfig` | toont je IP-adres (kort) |

| `ipconfig /all` | toont alle netwerkgegevens (IP, mask, DHCP, MAC) |

| `ping <ip> -t` | blijft pingen tot je stopt (Ctrl+C) |

  

---

  

## 9. Belangrijke begrippen kort

  

| Begrip | Betekenis |

|--------|-----------|

| **IP-adres** | uniek "huisnummer" van een apparaat |

| **Subnetmask** | bepaalt netwerkdeel vs apparaatdeel |

| **Switch** | verbindt apparaten in één netwerk |

| **Router** | koppelt verschillende netwerken |

| **DHCP** | deelt automatisch IP-adressen uit |

| **DNS** | vertaalt namen naar IP-adressen (komt later) |

| **Ping** | test of een apparaat bereikbaar is |

| **UTP** | de gewone netwerkkabel |

| **TTL** | "Time To Live", hoeveel stappen een pakket nog mag doen |

  

---

  

## 10. Packet Tracer opdracht (thuis)

  

Maak een eigen netwerkontwerp in Packet Tracer met minimaal:

- **Internet (Cloud)**

- **SoHo router** (de modem)

- **Bedrade én onbedrade apparaten**: PC, laptop, printer

- Uitbreiden mag

  

Lever in als **screenshot**.

  

---

  

## Stappenplan bij een netwerkopdracht

  

1. **Weet je adres.** Welk IP en subnetmask hoor je te gebruiken? (`10.0.X.y`)

2. **Stel het in.** Statisch (zelf invullen) of DHCP (automatisch).

3. **Controleer** met `ipconfig /all` of het klopt.

4. **Test** met `ping` of je de ander bereikt.

5. **Lukt het niet?** Loop de checklist af (kabel, adres, firewall, zelfde netwerk).