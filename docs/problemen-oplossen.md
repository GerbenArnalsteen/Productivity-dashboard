# Problemen oplossen

## Installeren
**Windows toont een blauwe SmartScreen-melding.** De app is niet ondertekend. Klik op *Meer informatie* → *Toch uitvoeren*.

**Op de gsm: "Installeren geblokkeerd".** Zet in Android de toestemming "Apps van onbekende bronnen installeren" aan voor Chrome. Waarschuwt Play Protect, kies dan *Toch installeren*.

## Google Agenda
**"Google heeft deze app niet geverifieerd".** Normaal voor een eigen app. Klik op *Geavanceerd* → *Doorgaan*.

**"Toegang geblokkeerd" of "Fout 403: access_denied".** Staat je app op *Testen*, voeg dan je Gmail-adres toe onder *Doelgroep → Testgebruikers*. Of publiceer de app.

**Elke 7 dagen opnieuw inloggen.** De app staat op *Testen*. Publiceer hem ([stappen](google-agenda-koppelen.md)) en log daarna één keer opnieuw in.

**"De Google Calendar API staat uit".** Zet in Google Cloud de *Google Calendar API* aan (stap 2).

**Publiceren kan niet (grijze knop).** Google eist een homepage-URL en een privacybeleid-URL op de Branding-pagina. Zie [Google Agenda koppelen, stap 4](google-agenda-koppelen.md).

**Afspraken verschijnen niet.** Controleer in het Google-tabblad of de agenda is aangevinkt. Klik op *Nu verversen*. Wijzigingen op je gsm komen binnen ongeveer 2 minuten binnen.

## Outlook
**Geen toestemming / "beheerder nodig" (AADSTS65001 of vergelijkbaar).** Je school of werk blokkeert het koppelen van apps. Gebruik de [agenda-link](agenda-links.md) (alleen lezen), of vraag je beheerder.

**"Dat lijkt niet op een Toepassings-ID".** Het ID heeft 36 tekens met streepjes. Gebruik de *Toepassings-ID (client)*, niet de map-ID of een geheim.

**Inloggen lukt, maar de app meldt een fout bij de omleiding.** Controleer dat de omleidings-URI `http://localhost` is, met als platform *Openbare client/native (mobiel en desktop)*, niet *Web*.

**"Dit Microsoft-account heeft geen Outlook-agenda die apps kunnen gebruiken".** Sommige accounts hebben geen bruikbare mailbox. Gebruik de [agenda-link](agenda-links.md).

**Je Outlook-login is verlopen.** Log in Instellingen → Agenda's → Outlook opnieuw in.

## Synchroniseren met de gsm
**Op de computer staat geen ✓ onder "Synchroniseren met je gsm".** Log opnieuw in via het Google-tabblad (eenmalig, de app heeft ook je e-mailadres nodig). Staat er "Nu geen verbinding", controleer dan je internet.

**Wijzigingen komen niet aan.** Wacht tot 45 seconden (computer) of 20 seconden (gsm). Open de app opnieuw. Gebruik *Nu synchroniseren* op de computer.

**Afspraken zijn oud op de gsm.** Die komen van de computer en worden daar ongeveer elke 10 minuten bijgewerkt. De computer moet aanstaan.

**Lege of verkeerde gegevens op de gsm.** Log uit en weer in met hetzelfde account als op de computer. Een nieuwe gsm haalt altijd de bestaande gegevens op.

## Updates
**De gsm krijgt geen update.** Open *Instellingen → Account* en tik op *↻ Zoeken naar updates*. De melding zegt of het gelukt is. Vereist internet.

**De computer krijgt geen update.** De app controleert bij het starten en elke 4 uur. Sluit en open hem opnieuw. Je kunt ook de nieuwste installer van Releases downloaden en over de oude heen installeren.

## Overig
**De app start niet / poort bezet.** De app zoekt zelf een vrije poort (3000 en hoger). Sluit andere kopieën van het dashboard.

**Ik wil mijn gegevens terugzetten.** Kopieer een reservekopie van `data.json` terug naar `%APPDATA%\ProductivityDashboard\` terwijl de app gesloten is. Bij het eerste koppelen met sync wordt ook een `data.before-sync-….json` bewaard.

**Alles opnieuw beginnen.** Sluit de app en verwijder de map `%APPDATA%\ProductivityDashboard\`. Verwijder je ook je gegevens in Firebase niet, dan komen ze bij het volgende inloggen terug.
