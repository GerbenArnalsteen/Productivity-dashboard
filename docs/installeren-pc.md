# Installeren op je computer (Windows)

1. Ga naar de **Releases**-pagina van deze repository en download van de nieuwste release (de naam begint met `v`, bijvoorbeeld `v1.0.6`) het bestand **`My-Dashboard-Setup-….exe`**.
2. Dubbelklik erop. De app installeert zichzelf, zonder beheerdersrechten, en zet een icoon op je bureaublad en in het startmenu.
3. **Windows SmartScreen** kan een blauwe melding tonen ("Windows heeft uw pc beschermd"). De app is niet ondertekend, dat kost een certificaat. Klik op **Meer informatie** → **Toch uitvoeren**.
4. Open **My Dashboard**. Er is geen browser of Node nodig.

## Bijwerken
De app controleert bij het opstarten en daarna elke 4 uur of er een nieuwe versie is, downloadt die op de achtergrond en vraagt **Nu herstarten**. Je hoeft niets handmatig te doen. Je gegevens blijven bewaard.

## Waar staan mijn gegevens?
In `%APPDATA%\ProductivityDashboard\`:

| Bestand | Inhoud |
|---|---|
| `data.json` | je dashboard (to-do's, notities, rooster, instellingen, ...) |
| `google.enc` | je koppeling met Google (versleuteld met Windows) |
| `cloud.enc` | je koppeling met de gsm-synchronisatie (versleuteld met Windows) |

Deze bestanden staan niet in OneDrive. Wil je een reservekopie, kopieer dan `data.json`.

## Verwijderen
Windows-instellingen → Apps → My Dashboard → Verwijderen. Je gegevens in `%APPDATA%\ProductivityDashboard\` blijven staan tot je de map zelf verwijdert.

## Volgende stappen
- [Google Agenda koppelen](google-agenda-koppelen.md)
- [Outlook-agenda tonen (link)](agenda-links.md)
- [De gsm-app installeren](gsm-app.md)
