# Google Agenda koppelen (twee richtingen)

Met deze koppeling zie je je Google-afspraken in het dashboard, en wat je in het dashboard toevoegt, wijzigt of verwijdert komt ook in Google Agenda (en dus op je gsm). Dit werkt ook voor **Samsung Agenda**, zolang die zijn afspraken in je Google-account bewaart.

Je doet dit **één keer, op de computer** waar het dashboard draait. Rekentijd: ongeveer 15 minuten.

## Wat je nodig hebt
- Een Google-account (gewoon Gmail is genoeg).
- Het dashboard geïnstalleerd op je computer ([installeren](installeren-pc.md)).

## Stap 1: een project maken
1. Ga naar **console.cloud.google.com** en log in.
2. Klik bovenaan op de projectkiezer en maak een **nieuw project**. Naam: bijvoorbeeld "Dashboard".

## Stap 2: de Google Calendar API aanzetten
1. Zoek bovenaan op **Google Calendar API**.
2. Klik op **Inschakelen**. Zonder dit krijg je later de foutmelding dat de API uitstaat.

## Stap 3: het toestemmingsscherm (Google Auth Platform)
1. Ga naar **Google Auth Platform** (ook "OAuth-toestemmingsscherm" genoemd) en klik op **Aan de slag**.
2. Vul in: app-naam (bijvoorbeeld "DashboardApp"; vermijd merknamen en het woord "Google"), je e-mailadres voor ondersteuning en je e-mailadres als ontwikkelaarscontact.
3. Kies als doelgroep **Extern**.

## Stap 4: publiceren, zodat je niet elke 7 dagen opnieuw moet inloggen
Staat de app op **Testen**, dan vervalt je login na 7 dagen. Staat hij op **In productie**, dan niet. Google eist voor publiceren een **homepage-URL** en een **privacybeleid-URL**.

Een eenvoudige manier, gratis:
1. Maak een **publieke repository** op GitHub en zet daar een `index.html` (korte uitleg) en een `privacy.html` (privacybeleid) in de hoofdmap. In deze repository staan voorbeelden.
2. Zet in de repository bij **Settings → Pages** de bron op de branch `main`, map `/ (root)`.
3. Vul op de **Branding**-pagina in Google de twee adressen in (`https://jouwnaam.github.io/jouw-repo/` en `…/privacy.html`) en sla op.
4. Ga naar **Doelgroep** en klik op **App publiceren**.

**Liever niet publiceren?** Blijf dan op "Testen", voeg onder **Testgebruikers** je eigen Gmail-adres toe, en log elke 7 dagen opnieuw in (één klik op "Inloggen met Google").

## Stap 5: de client aanmaken
1. Ga naar **Clients** → **Client maken**.
2. Type: **Desktop-app**. Naam: bijvoorbeeld "Dashboard".
3. Kopieer de **Client-ID** en het **Clientgeheim**.

## Stap 6: in het dashboard
1. Open **Instellingen → Agenda's → tabblad Google**.
2. Plak de Client-ID en het geheim en klik op **Opslaan**, daarna op **Inloggen met Google**.
3. Er opent een tabblad in je browser. Je ziet de waarschuwing **"Google heeft deze app niet geverifieerd"**. Klik op **Geavanceerd** en daarna op **Doorgaan**. Dit is je eigen app. Geef toegang tot je agenda.
4. Je ziet "Verbonden met Google". Vink aan welke agenda's je wilt zien en kies met het bolletje **nieuwe afspraken** welke agenda nieuwe afspraken krijgt.

## Goed om te weten
- Wijzigingen op je gsm verschijnen binnen ongeveer 2 minuten (of meteen met **Nu verversen**).
- Bij een terugkerende afspraak verandert of verdwijnt **alleen die ene**.
- De sleutels en je login staan in `%APPDATA%\ProductivityDashboard\google.json`, niet in het dashboard-bestand en niet in OneDrive.
- Een andere gebruiker (bijvoorbeeld een vriend) kan jouw Client-ID gebruiken, tot maximaal 100 gebruikers zolang de app niet is geverifieerd.

Problemen? Zie [problemen oplossen](problemen-oplossen.md).
