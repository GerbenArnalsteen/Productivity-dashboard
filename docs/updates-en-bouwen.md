# Updates en bouwen (voor de maker)

Deze pagina beschrijft hoe nieuwe versies gebouwd en online gezet worden. Gewone gebruikers hebben dit niet nodig: de apps updaten zichzelf.

## Onderdelen
| Onderdeel | Bestanden |
|---|---|
| Server (lokaal, zonder afhankelijkheden) | `server.js`, `google.js`, `outlook.js`, `ics.js`, `cloud.js` |
| Scherm (Nederlands/Engels) | `public/` (`index.html`, `app.js`, `style.css`, `i18n.js`) |
| Computer-app (Electron) | `main.js`, `package.json` |
| Gsm-app (Capacitor, Android) | project in `C:\AndroidBuild\app` (gebouwd uit `public/`) |
| Scripts | `tools/` |

De computer-app draait de server zelf in het programma en toont `public/` in een eigen venster. De gsm-app toont dezelfde `public/` en praat met Firebase in plaats van met de lokale server.

## Eenmalig voorbereiden
- **Node.js**.
- Een **GitHub-token** (fine-grained, alleen deze repository, *Contents: Read and write*), als omgevingsvariabele:
  ```powershell
  [Environment]::SetEnvironmentVariable('GH_TOKEN', 'JE_TOKEN', 'User')
  ```
  Open daarna een nieuwe terminal. Zet de token nooit in een bestand of in een chat.
- Voor Android: **JDK 21**, de **Android SDK** (platform 36, build-tools 36) en een **ondertekeningssleutel**, alles buiten OneDrive in `C:\AndroidBuild`. **Bewaar een reservekopie van de sleutel** (`C:\AndroidBuild\keys`): zonder de sleutel kan nooit een update over de bestaande gsm-app heen geïnstalleerd worden.

## Computer-app
```powershell
powershell -File tools\build-desktop.ps1            # alleen bouwen
powershell -File tools\build-desktop.ps1 -Release   # versie ophogen, bouwen en op GitHub Releases zetten
```
Gebouwd wordt in `C:\DashboardBuild`. Geïnstalleerde apps vinden de nieuwe versie bij het opstarten en daarna elke 4 uur.

## Gsm-app
```powershell
powershell -File tools\build-android.ps1 -Web   # nieuwe schermen/functies: automatische update
powershell -File tools\build-android.ps1 -Apk   # nieuwe apk (alleen als de app zelf verandert, bijvoorbeeld nieuwe plug-ins)
```
- `-Web` zet een zip met `public/` online plus een controlegetal (SHA-256) in `app-update/latest.json`. De app downloadt die en gebruikt hem na een herstart.
- `-Apk` bouwt een ondertekende apk, zet hem als release `android-N` op GitHub en laat de app erom vragen.
- Het versienummer in de app (Instellingen → Account) is `apk.web`.

## Tests
```powershell
node tools/test-ics.js       # agenda-links
node tools/test-google.js    # Google, met een nep-Google
node tools/test-outlook.js   # Outlook, met een nep-Microsoft (inclusief zomer-/wintertijd)
node tools/dev-test-server.js   # veilige testserver op poort 3300 voor in de browser
```
De tests en de testserver gebruiken eigen tijdelijke bestanden en nep-diensten. Ze raken je echte gegevens, logins, agenda's en Firebase niet aan.

## Online zetten van de pagina's en handleidingen
```powershell
powershell -File tools\publish-docs.ps1
```
Zet `README.md`, de map `docs/` en de pagina's `site/index.html` en `site/privacy.html` in de repository.
