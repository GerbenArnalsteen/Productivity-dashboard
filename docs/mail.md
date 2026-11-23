# Mail

Al je postvakken in één lijst, in het tabblad **Mail** (of in een Mail-widget die je zelf op een tabblad zet). Je kunt **zoveel postvakken koppelen als je wilt**.

> Mail werkt alleen **op je computer**. Je postvakken, wachtwoorden en mails gaan nooit naar je gsm of naar de cloud.

## Een postvak koppelen
**Instellingen → Mail → ＋ Postvak koppelen** (of de knop in de Mail-widget). Kies waar het postvak staat:

| Dienst | Hoe |
|---|---|
| **Gmail** (aanbevolen) | Inloggen met Google in je browser. Geen wachtwoord in de app. |
| **iCloud Mail** | E-mailadres + een **app-specifiek wachtwoord**: [uitleg van Apple](https://support.apple.com/nl-nl/102654) |
| **Yahoo Mail** | E-mailadres + een **app-wachtwoord**: [uitleg van Yahoo](https://help.yahoo.com/kb/SLN15241.html). Zie hieronder als de optie ontbreekt. |
| **Andere (IMAP)** | GMX, school, werk, eigen domein: e-mailadres, app-wachtwoord (of het wachtwoord dat je provider voor mail-apps geeft) en de IMAP-server (meestal poort 993). |
| **Gmail met app-wachtwoord** | Alleen als inloggen met Google niet lukt: [app-wachtwoord maken](https://myaccount.google.com/apppasswords) (tweestapsverificatie moet aanstaan). |
| **Outlook / Hotmail** | Niet beschikbaar: Microsoft vereist dat de maker de app registreert. Tip: stuur je Outlook-mail door naar een Gmail-adres (Outlook.com → Instellingen → E-mail → Doorsturen) en koppel dat. |

### Yahoo: ik zie geen "app-wachtwoord maken"
Yahoo toont die optie meestal pas als **tweestapsverificatie aanstaat**.
1. Ga naar de accountbeveiliging van Yahoo (`login.yahoo.com/account/security`).
2. Zet **Tweestapsverificatie** aan (je hebt een telefoonnummer nodig) en zorg dat je account een wachtwoord heeft (niet alleen "inloggen zonder wachtwoord").
3. Daarna verschijnt **App-wachtwoord maken** (onder "Externe verbindingen"). Kies als naam bijvoorbeeld "Dashboard" en plak het wachtwoord van 16 tekens in de app.
Bij een heel nieuw Yahoo-account kan het enkele dagen tot weken duren voor de optie verschijnt. Server: `imap.mail.yahoo.com`, poort 993 (staat al ingevuld).

### Gmail: welke tabbladen zie je?
Gmail sorteert je inbox in tabbladen: **Primair, Sociaal, Promoties, Updates, Forums**. De app toont standaard **alleen Primair**, zodat reclame en meldingen je echte mail niet bedelven. Het aantal ongelezen mails telt ook alleen wat je ziet.
Je kiest welke tabbladen je ziet via **Instellingen → Mail → Wijzig** bij dat postvak. Heb je de tabbladen in Gmail zelf uitgezet, vink dan alles aan.

Bij elk postvak kies je **wat de app mag doen**:
- **🔒 Alleen lezen:** de app kan je mail alleen bekijken. Er verandert niets in je postvak, ook niet of een mail "gelezen" is.
  - Bij Gmail krijgt de app dan alleen het recht `gmail.readonly` van Google.
  - Bij een app-wachtwoord opent de app je postvak alleen-lezen en weigert ze zelf elke wijziging.
- **✎ Lezen en schrijven:** de app kan ook als gelezen of ongelezen markeren, archiveren en naar de **prullenbak** verplaatsen (nooit definitief verwijderen). Je kunt ook **zelf mails schrijven en beantwoorden** (zie hieronder). Bij Gmail is dat het recht `gmail.modify`; dat recht omvat ook versturen, dus je hoeft niet opnieuw in te loggen.

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

## AI-samenvattingen (optioneel, op je eigen computer)
De app kan elke mail in één korte zin samenvatten en zeggen of je er iets mee **moet doen** (🔶), of dat hij **verdacht** is (⚠️). Daarvoor draait een klein AI-model **op je eigen computer**. **Je mail gaat nooit naar internet of een clouddienst**, en er wordt niets op schijf bewaard: samenvattingen staan alleen in het geheugen en verdwijnen als je de app sluit.

**Eenmalig instellen**
1. Installeer **Ollama** (gratis, geen account nodig): ga naar ollama.com, download de installer voor Windows en installeer hem. Laat hem niet met Windows laten opstarten als je dat niet wilt: de app start zijn eigen exemplaar wanneer het nodig is.
2. Open **Instellingen → Mail → ✨ AI-samenvattingen** en zet **Mijn mail samenvatten met AI** aan.
3. Klik op **Model downloaden** (ongeveer 3,4 GB, eenmalig). Het model heet `gemma3:4b` en kiest goed Nederlands.
4. Staat er "✓ Klaar", dan kun je beginnen.

**Gebruik**
- **Een mail openen:** boven de tekst staat de samenvatting met een label: *Actie nodig*, *Verdacht* of *Informatie*. Het verschijnt terwijl het geschreven wordt. Wil je dat niet automatisch, zet dat dan uit in de instellingen (dan krijg je een knop "Deze mail samenvatten").
- **✨ Overzicht** (knop boven de lijst): kies **Vandaag**, **Gemist** (ongelezen mail van de afgelopen dagen) of **Alle ongelezen**. De AI leest die mails (maximaal 25) en sorteert ze in **Te doen**, **Verdacht** en **Informatie**. Klik op een regel om de mail te openen.
- In de lijst krijgen mails waar je iets mee moet doen 🔶 en verdachte mails ⚠️, zodra ze samengevat zijn.

**Snelheid.** Op een pc als de testcomputer (Ryzen 7 en een ingebouwde videokaart) duurt een mail ongeveer 4 seconden. De allereerste keer duurt langer, omdat het model geladen wordt: de app doet dat alvast op de achtergrond zodra je het Mail-tabblad opent. Bij **"De videokaart gebruiken"** (standaard aan, experimenteel) gebruikt de AI de ingebouwde videokaart: ongeveer twee keer zo snel. Lukt dat niet, dan valt Ollama zelf terug op de processor. Een nieuw AMD-stuurprogramma kan helpen.

**Let op**
- Een AI kan **fouten maken**. De samenvatting is een hulpmiddel. Controleer de mail zelf voordat je iets doet, vooral bij geld, wachtwoorden of deadlines.
- Een mail is **onbetrouwbare tekst**: de AI heeft geen enkele actie tot zijn beschikking (hij kan niets versturen, openen of wijzigen) en geeft alleen tekst terug. Instructies in een mail ("negeer alles en…") worden niet uitgevoerd. In een test van 12 voorbeeldmails werd een mail met zo'n instructie als *verdacht* herkend. De prompt is afgesteld op diezelfde voorbeelden, dus het cijfer van 11 van de 12 goede labels is optimistisch.
- Het model draait in een **eigen Ollama-proces** dat alleen op deze computer luistert, zonder je sleutels of wachtwoorden. De app stopt het na 20 minuten niets doen of als je de app sluit.
- Met **Samenvattingen vergeten** en **AI stoppen** (in de instellingen) wis je het geheugen of stop je het model meteen.

## Mail schrijven en beantwoorden
Alleen bij postvakken met **✎ lezen en schrijven**.
- Open een mail en kies **↩ Beantwoorden** of **↩↩ Allen beantwoorden**, of druk bovenaan op **✎ Nieuw** voor een nieuwe mail.
- Aan, Cc en het onderwerp zijn al ingevuld. Je kunt ze nog aanpassen. Bij een antwoord kan de originele mail eronder staan (vinkje).
- **Versturen** gaat in twee stappen: eerst zie je precies vanaf welk adres en naar wie de mail gaat, daarna druk je op **Ja, versturen**. De app verstuurt nooit zelf iets.
- Bij Gmail komt een antwoord in hetzelfde gesprek en in je map *Verzonden*.
- Bij andere postvakken (iCloud, Yahoo, school…) gaat versturen via de **uitgaande server (SMTP)** met hetzelfde app-wachtwoord. Voor iCloud, Yahoo en Gmail is die al ingevuld. Bij **Andere** vul je hem in via **Instellingen → Mail → Wijzig → Versturen** en druk je op **Testen en opslaan**. Alleen beveiligde poorten (465 of 587) zijn mogelijk.
- De app zet een kopie in je map **Verzonden**. Zie je elke verzonden mail dubbel? Zet het vinkje *Een kopie in "Verzonden" zetten* dan uit.
- **Bijlagen** kunnen nog niet.

**✨ Concept van de AI** (als de AI aanstaat): typ in een paar woorden wat je wilt antwoorden ("ja, ik kom", "vraag een week uitstel") en druk op **Concept schrijven**. Het concept komt in het tekstvak. Lees het na en pas het aan: het model kan fouten maken. Het concept vult alleen de tekst in, niet de ontvangers of het onderwerp, en het verstuurt niets. Duurt ongeveer 4 tot 7 seconden (de eerste keer langer, terwijl het model laadt).

Is een mail door de AI als **⚠️ verdacht** gemarkeerd, dan vraagt de app eerst of je toch wilt antwoorden. Stuur nooit wachtwoorden, codes of bankgegevens per mail.

**Beveiliging bij versturen**
- Het afzenderadres is altijd het adres van het postvak zelf. De pagina kan het niet veranderen.
- Adressen en onderwerp worden gecontroleerd. Een regeleinde of een ongeldig adres wordt geweigerd, nooit stilletjes "verbeterd", zodat niemand extra ontvangers in de mail kan smokkelen.
- Maximaal 50 ontvangers per mail en 20 mails per 10 minuten per postvak, als rem op een fout die anders veel mails zou versturen.
- Een concept leeft alleen in het venster. Het wordt niet bewaard en niet gesynchroniseerd. Sluit je het venster met tekst erin, dan vraagt de app eerst of je die wilt weggooien.

## Wat er nog komt
- Bijlagen meesturen.
- Andere AI-keuzes (een eigen sleutel van een dienst), voor wie geen Ollama wil.
