# My Dashboard

Een persoonlijke productiviteits-app voor werk en school, opgebouwd uit tabbladen en widgets die je zelf indeelt. Voor **Windows** (echte app, installeerbaar) en **Android**. Standaard in het Nederlands, met Engels als optie.

## Wat kan het?
- **Tabbladen en widgets** die je vrij verplaatst en van grootte verandert: vandaag, to-do's, agenda, deadlines, rooster, snelle links, focustimer, gewoontes, notities (meerdere), aftellen, weer, citaten, zoeken.
- **Rooster** met eigen kleuren (palet), overlappende lessen naast elkaar, meerdere dagen tegelijk invoeren.
- **Agenda die twee kanten op synchroniseert** met **Google Agenda** (ook Samsung Agenda via je Google-account). Afspraken toevoegen, wijzigen en verwijderen in het dashboard komt ook in je agenda terecht.
- **Agenda-links** (alleen lezen) voor Outlook, iPhone/iCloud en andere diensten.
- **Synchronisatie tussen computer en gsm** via je eigen account, ook als de computer uit staat.
- **Eigen indeling voor je gsm**: andere volgorde van widgets, en widgets verbergen.
- **Automatische updates** op computer en gsm.

## Installeren
1. Download de nieuwste installer van de **Releases**-pagina van deze repository ([stappen](docs/installeren-pc.md)).
2. Voor Android: download de nieuwste `android-…` apk ([stappen](docs/gsm-app.md)).

## Handleidingen
| Onderwerp | Pagina |
|---|---|
| De app op je computer installeren | [docs/installeren-pc.md](docs/installeren-pc.md) |
| Google Agenda koppelen (twee richtingen) | [docs/google-agenda-koppelen.md](docs/google-agenda-koppelen.md) |
| Agenda-links (alleen lezen, ook voor Outlook) | [docs/agenda-links.md](docs/agenda-links.md) |
| De gsm-app | [docs/gsm-app.md](docs/gsm-app.md) |
| Synchroniseren tussen computer en gsm | [docs/synchroniseren-pc-gsm.md](docs/synchroniseren-pc-gsm.md) |
| Problemen oplossen | [docs/problemen-oplossen.md](docs/problemen-oplossen.md) |
| Updates en bouwen (voor de maker) | [docs/updates-en-bouwen.md](docs/updates-en-bouwen.md) |

In de app staan dezelfde handleidingen onder **Instellingen → Hulp en handleidingen**.

## Privacy en veiligheid
- Je gegevens staan op je computer (`%APPDATA%\ProductivityDashboard\`) en, voor de gsm-synchronisatie, in **jouw eigen** Firebase-account. De regels laten alleen jou je eigen gegevens zien.
- Inloggegevens voor Google staan alleen op je computer, buiten het dashboard-bestand en buiten OneDrive.
- Er zijn geen advertenties, geen analyse en geen gebruiksstatistieken.
- Volledige tekst: [privacybeleid](https://gerbenarnalsteen.github.io/Productivity-dashboard/privacy.html).

## Techniek in het kort
- Computer: Electron-app die een kleine Node-server (zonder afhankelijkheden) en een scherm in gewone HTML/CSS/JavaScript bevat.
- Gsm: dezelfde schermen in een Capacitor-app, met Firestore als opslag.
- Agenda's: Google Calendar API via OAuth 2.0 met PKCE, en alleen-lezen agenda-links (.ics). Er worden geen geheimen in het dashboard bewaard.
- Meer: [docs/updates-en-bouwen.md](docs/updates-en-bouwen.md).
