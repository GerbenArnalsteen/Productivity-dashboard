# Outlook-agenda koppelen (twee richtingen)

Werkt met **Outlook.com / Hotmail / Live** en met **Microsoft 365** (school of werk). Je ziet je afspraken in het dashboard, en wat je daar toevoegt, wijzigt of verwijdert staat ook in Outlook en op je gsm.

Je doet dit **één keer, op de computer** waar het dashboard draait. Rekentijd: ongeveer 10 minuten. Google en Outlook kunnen tegelijk gekoppeld zijn.

> **School- of werkaccount?** Een beheerder kan het koppelen van eigen apps blokkeren. Krijg je bij het inloggen een melding dat toestemming van een beheerder nodig is, gebruik dan in plaats daarvan de [agenda-link](agenda-links.md) (alleen lezen).

## Stap 1: een app registreren bij Microsoft
1. Ga naar **entra.microsoft.com** en log in met je Outlook-account.
2. Open **App-registraties** → **Nieuwe registratie**.
3. **Naam:** bijvoorbeeld "Dashboard".
4. **Ondersteunde accounttypen:** kies *"Accounts in elke organisatiemap en persoonlijke Microsoft-accounts"*.
5. **Omleidings-URI:** kies als platform **"Openbare client/native (mobiel en desktop)"**, **niet** "Web", en vul in: `http://localhost`
6. Klik op **Registreren**.

> Zegt Microsoft dat je geen *directory* (map) hebt, of vraagt het om een gratis Azure-account? Dat gebeurt soms bij een persoonlijk account. Maak dan een gratis Azure-account aan (dat kan een creditcardcontrole vragen) en probeer het opnieuw. Voor deze koppeling hoef je niets te betalen.

## Stap 2: machtigingen
1. Open **API-machtigingen** → **Een machtiging toevoegen** → **Microsoft Graph** → **Gedelegeerde machtigingen**.
2. Voeg **Calendars.ReadWrite** toe. (`User.Read` staat er al.)
3. Goedkeuring door een beheerder is niet nodig.

## Stap 3: het ID kopiëren
Kopieer op de **Overzicht**-pagina de **Toepassings-ID (client)**. Het zijn 36 tekens met streepjes. Er is **geen geheim** om te kopiëren.

## Stap 4: in het dashboard
1. Open **Instellingen → Agenda's → tabblad Outlook**.
2. Plak het ID en klik op **Opslaan**, daarna op **Inloggen met Microsoft**.
3. Er opent een tabblad in je browser. Kies je account en geef toestemming om je agenda te lezen en te wijzigen.
4. Je ziet "Verbonden met Outlook". Vink aan welke agenda's je wilt zien en kies met het bolletje **nieuwe afspraken** welke agenda nieuwe afspraken krijgt.

Heb je zowel Google als Outlook gekoppeld, dan kies je met dat bolletje (in een van beide tabbladen) waar **nieuwe afspraken** heen gaan. Standaard is dat Google.

## Goed om te weten
- Het ID en je login staan in `%APPDATA%\ProductivityDashboard\outlook.json`, niet in het dashboard-bestand en niet in OneDrive.
- Bij een terugkerende afspraak verandert of verdwijnt **alleen die ene**.
- Je Microsoft-login blijft geldig zolang je het dashboard minstens af en toe gebruikt (Microsoft verlengt hem automatisch). Gaat hij toch verlopen, dan log je één keer opnieuw in.
- Sommige Microsoft-accounts hebben geen Outlook-mailbox die apps kunnen gebruiken. Dan zegt het dashboard dat er geen bruikbare agenda is.

Problemen? Zie [problemen oplossen](problemen-oplossen.md).
