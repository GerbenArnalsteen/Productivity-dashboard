# Beveiliging

Wat de app doet om je gegevens en inloggegevens te beschermen, en wat niemand kan beloven.

## Op je computer
- **De server in de app luistert alleen op deze computer** (`127.0.0.1`). Andere apparaten op je wifi kunnen hem niet bereiken.
- **Elke aanvraag moet een geheime sleutel van de sessie meesturen.** De app zet die in de pagina die ze zelf toont. Een andere website in je browser kan die pagina niet lezen en komt dus nergens.
- **De Host en de herkomst (Origin) worden gecontroleerd.** Dat blokkeert "DNS rebinding", waarbij een website de browser laat denken dat `localhost` een andere naam heeft. Alleen de Google-inlogredirect is vrijgesteld (die heeft zijn eigen eenmalige `state`).
- **Beveiligingsheaders** op de pagina: een strikt Content-Security-Policy (de pagina mag alleen verbinden met zichzelf en de weerdienst), geen inbedding in andere pagina's, geen gokken op bestandstypes.
- **Een losse kopie van de server (`node server.js`) weigert te starten**, zodat die nooit per ongeluk je echte gegevens en logins kan lezen. Testen gaat met `tools/dev-test-server.js`.

## Inloggegevens
- Google-login en de koppeling met de gsm-synchronisatie staan **versleuteld met Windows** (`google.enc`, `cloud.enc` in `%APPDATA%\ProductivityDashboard\`, via Electron `safeStorage`, gekoppeld aan jouw Windows-gebruiker). Een kopie van het bestand is op een andere computer of onder een andere gebruiker onleesbaar.
- Nieuwe en oude logins worden automatisch versleuteld. Een oud leesbaar bestand wordt pas verwijderd nadat de versleutelde kopie is geschreven en terug gelezen.
- Kan een versleuteld bestand niet gelezen worden (bijvoorbeeld na een Windows-herinstallatie), dan staat de app als "niet ingelogd" en log je opnieuw in. Er gaat niets kapot en het bestand wordt niet verwijderd.
- Inloggegevens staan nooit in `data.json`, nooit in OneDrive, nooit in Firebase en nooit op je gsm.

## Wat dit niet kan beschermen
- Schadelijke software die **als jij** op je computer draait, kan Windows vragen de gegevens te ontsleutelen. Dat kan geen enkele app op een gewone pc voorkomen. Houd Windows bijgewerkt en installeer niets onbetrouwbaars.
- De **updates** komen van GitHub. Wie schrijftoegang heeft tot de repository van de maker, kan een kwaadaardige update naar alle apparaten sturen. Voor de maker: zet **tweestapsverificatie of een passkey** op GitHub, gebruik een token met een korte looptijd en bewaar de ondertekeningssleutel van de gsm-app veilig. De installers zijn niet ondertekend met een betaald certificaat.
- Je **Google-account** en je **Firebase-regels** zijn de laatste verdedigingslinie voor de gegevens in de cloud. Houd je Google-account goed beveiligd.

## Tests
```powershell
node tools/test-google.js    # inclusief weigeringen: geen sleutel, verkeerde host, vreemde herkomst, tekst/plain-aanval
C:\DashboardBuild\node_modules\electron\dist\electron.exe tools\test-vault.js   # versleuteling onder de echte Electron
powershell -File tools\smoke-desktop.ps1                                         # het gebouwde programma in een geïsoleerde proefomgeving
```
De rooktest draait bij elke release automatisch. Mislukt hij, dan wordt er niets uitgebracht.

## Voor wie de code bekijkt
- `server.js`: `guard()` en de Content-Security-Policy.
- `vault.js`: opslag van logins.
- Electron meldt dat `safeStorage.encryptString` verouderd is ten gunste van een asynchrone variant. Het werkt in de gebruikte versie. Een latere versie van Electron kan een aanpassing nodig maken.
