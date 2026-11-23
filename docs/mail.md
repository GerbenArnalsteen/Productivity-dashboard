# Mail

Al je postvakken in één lijst, in het tabblad **Mail** (of in een Mail-widget die je zelf op een tabblad zet). Je kunt **zoveel postvakken koppelen als je wilt**.

> Mail werkt alleen **op je computer**. Je postvakken, wachtwoorden en mails gaan nooit naar je gsm of naar de cloud.

## Een postvak koppelen
**Instellingen → Mail → ＋ Postvak koppelen** (of de knop in de Mail-widget). Kies waar het postvak staat:

| Dienst | Hoe |
|---|---|
| **Gmail** (aanbevolen) | Inloggen met Google in je browser. Geen wachtwoord in de app. |
| **iCloud Mail** | E-mailadres + een **app-specifiek wachtwoord**: [uitleg van Apple](https://support.apple.com/nl-nl/102654) |
| **Yahoo Mail** | E-mailadres + een **app-wachtwoord**: [uitleg van Yahoo](https://help.yahoo.com/kb/SLN15241.html) |
| **Andere (IMAP)** | GMX, school, werk, eigen domein: e-mailadres, app-wachtwoord (of het wachtwoord dat je provider voor mail-apps geeft) en de IMAP-server (meestal poort 993). |
| **Gmail met app-wachtwoord** | Alleen als inloggen met Google niet lukt: [app-wachtwoord maken](https://myaccount.google.com/apppasswords) (tweestapsverificatie moet aanstaan). |
| **Outlook / Hotmail** | Niet beschikbaar: Microsoft vereist dat de maker de app registreert. Tip: stuur je Outlook-mail door naar een Gmail-adres (Outlook.com → Instellingen → E-mail → Doorsturen) en koppel dat. |

Bij elk postvak kies je **wat de app mag doen**:
- **🔒 Alleen lezen:** de app kan je mail alleen bekijken. Er verandert niets in je postvak, ook niet of een mail "gelezen" is.
  - Bij Gmail krijgt de app dan alleen het recht `gmail.readonly` van Google.
  - Bij een app-wachtwoord opent de app je postvak alleen-lezen en weigert ze zelf elke wijziging.
- **✎ Lezen en schrijven:** de app kan ook als gelezen of ongelezen markeren, archiveren en naar de **prullenbak** verplaatsen (nooit definitief verwijderen). Bij Gmail is dat het recht `gmail.modify`. **Mails versturen komt in een volgende versie.**

Je kunt dit later wijzigen via **Instellingen → Mail → Wijzig**. Bij Gmail betekent wijzigen: opnieuw inloggen, omdat het een toestemming bij Google is.

### Gmail: eenmalig in Google Cloud (voor wie de app zelf instelt)
In hetzelfde Google Cloud-project als de agenda-koppeling:
1. Zet de **Gmail API** aan.
2. Voeg bij **Google Auth Platform → Gegevenstoegang** de rechten `gmail.readonly` en `gmail.modify` toe en sla op.
3. Bij het inloggen toont Google "niet geverifieerd" (Geavanceerd → Doorgaan) en een vakje voor Gmail: **vink dat aan**, anders lukt het koppelen niet. De app zegt het je als dat vakje niet aangevinkt was.

Google noemt de Gmail-rechten "beperkt". Een niet-geverifieerde app mag ze voor maximaal 100 gebruikers gebruiken.

## De Mail-widget
- **Links: je postvakken.** Elke rij heeft een kleur, het aantal ongelezen mails, "alleen lezen" of "lezen en schrijven", en een **schakelaar om het postvak te tonen of te verbergen**. Bovenaan zet één schakelaar alles aan of uit. Onder de lijst zie je hoeveel postvakken verborgen zijn, met een knop "alles tonen".
- **Midden: één lijst** van alle zichtbare postvakken, nieuwste eerst, per dag gegroepeerd. Het gekleurde streepje en de initialen tonen uit welk postvak een mail komt. Ongelezen mails staan vet. Zoeken en "Ongelezen" filteren de lijst.
- **Rechts: het leesvenster.** Mail wordt als gewone tekst getoond, zonder afbeeldingen van buitenaf (die kunnen verraden dat je de mail las). Een link toont het echte adres en opent pas nadat je bevestigt. Bijlagen worden alleen met naam en grootte getoond.
- Is de widget smal, dan staan de postvakken boven de lijst en opent een mail in een venster.

### Weergave aanpassen (⚙ Weergave)
- **Indeling:** lijst met leesvenster ernaast, leesvenster onder de lijst, of alleen een lijst (mail opent in een venster).
- **Ruimte:** ruim (twee regels) of compact (één regel). **Tekstgrootte:** klein, normaal of groot.
- **Tonen:** voorbeeldtekst, initialen van de afzender, groeperen per dag.
- **Mails per postvak:** 25, 50 of 100. **Volgorde:** nieuwste of oudste eerst. **Bij openen:** alle mail of alleen ongelezen.
- **Als gelezen markeren bij openen** (alleen bij postvakken met lezen en schrijven).
- **Welke postvakken** deze widget toont. Je kunt meerdere Mail-widgets maken, bijvoorbeeld één voor school en één voor privé.

Naam, kleur, volgorde en rechten van een postvak wijzig je in **Instellingen → Mail**.

## Veiligheid
- Postvakken en wachtwoorden staan **versleuteld met Windows** in `%APPDATA%\ProductivityDashboard\mail.enc`. Ze komen nooit in `data.json`, in OneDrive, in Firebase of op je gsm.
- Mails worden alleen in het geheugen bewaard zolang de app open is en nooit op schijf geschreven.
- Alleen beveiligde verbindingen (TLS) met gecontroleerde certificaten.
- Als je een Gmail-postvak verwijdert, trekt de app ook zijn toestemming bij Google in. Je mail zelf blijft in je postvak staan.
- Een postvak dat niet werkt (verkeerd wachtwoord, server onbereikbaar), houdt de andere niet tegen. Je ziet de melding bij dat postvak.

## Wat er nog komt
- AI-samenvattingen van je mail van vandaag of gemiste mails, met een lokaal model op je eigen computer (Ollama, gemma3:4b).
- Zelf antwoorden en versturen, met een optioneel concept van de AI. De app verstuurt nooit zelf iets.
