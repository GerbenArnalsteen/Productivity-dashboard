# Synchroniseren tussen computer en gsm

## Hoe het werkt
Je gegevens worden bewaard in **Firebase** (Cloud Firestore, een dienst van Google), in jouw eigen account. Er is geen ander centraal systeem.

- `users/{jouw-id}/dash/main`: je hele dashboard (to-do's, notities, rooster, instellingen, ...).
- `users/{jouw-id}/dash/ext`: een **alleen-lezen kopie** van je komende afspraken (ongeveer 4 maanden vooruit, uit Google, Outlook en agenda-links), voor de gsm. De gsm kan die diensten zelf niet bereiken. De kopie bevat geen afspraak-ID's, zodat hij klein blijft.

De computer-app meldt zich bij Firebase aan met het Google-account dat je bij de Google-koppeling gebruikte. De gsm doet dat met de accountkiezer van Android. De regels in Firestore zorgen ervoor dat **alleen jij** je eigen gegevens kunt lezen en schrijven.

## Regels
- **Laatste wijziging wint** voor het hele dashboard. Pas je op twee toestellen tegelijk dezelfde dingen aan, dan blijft de nieuwste staan.
- De computer controleert elke 45 seconden, de gsm elke 20 seconden (en bij het openen). Wijzigingen worden ongeveer 2,5 seconden na het typen verstuurd.
- **Eerste keer koppelen:** bestaat er al een kopie in de cloud, dan wint die. Een reservekopie van je computergegevens wordt bewaard als `data.before-sync-JJJJ-MM-DD.json`. Een nieuwe, lege gsm overschrijft nooit je echte gegevens.
- Zonder internet blijft alles werken. Wijzigingen worden verstuurd zodra er weer verbinding is.

## Aanzetten
1. Installeer de computer-app en log in via **Instellingen → Agenda's → Google** (de computer gebruikt daarvoor dezelfde login). Dit moet één keer opnieuw gebeuren na de update waarin sync is toegevoegd.
2. Onder **Instellingen → Synchroniseren met je gsm** staat dan "✓ Gesynchroniseerd met de gsm-app".
3. Installeer en open de gsm-app en log in met hetzelfde account ([gsm-app](gsm-app.md)).

Met **Nu synchroniseren** forceer je een controle. Met **Stoppen met synchroniseren** koppel je de computer los. Er wordt niets verwijderd.

## Zelf opzetten (voor wie de app zelf bouwt)
Een eigen Firebase-project is nodig. Dit gebeurt eenmalig.
1. Maak in **console.firebase.google.com** een project. Gebruik het Google Cloud-project waarin ook je Google-koppeling staat, dan hoef je het toestemmingsscherm niet opnieuw te doen.
2. **Authentication → Aan de slag → Google** inschakelen. Voeg bij *Geautoriseerde domeinen* het domein toe waar je privacypagina's staan (bijvoorbeeld `jouwnaam.github.io`).
3. **Firestore Database** maken, in productiemodus en in een Europese regio. Zet deze regels bij **Regels** en publiceer:
   ```
   rules_version = '2';
   service cloud.firestore {
     match /databases/{database}/documents {
       match /users/{uid}/{doc=**} {
         allow read, write: if request.auth != null && request.auth.uid == uid;
       }
     }
   }
   ```
4. Registreer een **web-app** en zet de configuratie (`apiKey`, `authDomain`, `projectId`, `appId`) in `public/firebase-config.json`. Deze gegevens zijn niet geheim.
5. Registreer een **Android-app** met pakketnaam `nl.gerben.mydashboard` en de **SHA-1** van je ondertekeningssleutel. Download `google-services.json` en zet het in het Android-project ([bouwen](updates-en-bouwen.md)).

## Gratis limiet
Firestore's gratis laag (Spark) staat 50.000 leesacties per dag toe. De app leest zuinig: de computer elke 45 seconden, de gsm elke 20 seconden en alleen als de app zichtbaar is. Voor één gebruiker met één computer en één gsm blijf je ruim onder de limiet.
