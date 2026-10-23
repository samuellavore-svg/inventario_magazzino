# Inventario On Fun Padre Pio — versione web sincronizzata

Il gestionale usa Firebase Authentication e Firestore del progetto già creato. **La sincronizzazione funzionerà solo dopo la pubblicazione su HTTPS e l’accesso con l’account Firebase autorizzato.**

## Pubblicazione da telefono tramite GitHub Pages
1. Estrai lo ZIP sul telefono. In GitHub crea un nuovo repository, per esempio `inventario-magazzino`, preferibilmente **Private** (verifica che GitHub Pages sia disponibile per il tuo piano; in alternativa Public). Le pagine pubblicate possono essere accessibili a chiunque: **l’accesso ai dati resta protetto dalle regole Firestore**.
2. Nel repository usa **Add file → Upload files** e carica nella **radice** questi cinque file: `index.html`, `app.js`, `firebase-config.js`, `manifest.webmanifest`, `favicon.svg` (non la cartella contenitrice). Conferma con **Commit changes**. Su mobile può servire “Sito desktop”.
3. Vai su **Settings → Pages → Build and deployment**, scegli **Deploy from a branch**, `main`, cartella `/(root)` e **Save**.
4. Attendi l’URL indicato in Pages, normalmente `https://TUO-USERNAME.github.io/inventario-magazzino/`.
5. In Firebase Console → Authentication → Settings → Authorized domains aggiungi **solo** `TUO-USERNAME.github.io` (senza `https://` e senza percorso) se non è già presente.
6. Apri il sito, accedi con le credenziali Firebase create precedentemente. Sul telefono scegli “Aggiungi a schermata Home”.
7. Dal vecchio file HTML, **sullo stesso browser e dispositivo che contiene le giacenze**, esporta un **backup JSON**. Poi, dal sito nuovo, usa “Importa backup JSON” una sola volta. Verifica categorie, sottocategorie, quantità, minimi, colori e varianti.

## Regole Firestore
Il file `firestore.rules` contiene le regole per l’unico UID amministratore. Se le hai già pubblicate nella console, non devi ripubblicarle. Non sostituirle con regole che consentono l’accesso a tutti.

## Sicurezza e limiti
- Il repository e la pagina web non devono contenere password, chiavi private o file di backup. La configurazione web Firebase è pubblica per definizione.
- **Non caricare mai il backup JSON su GitHub.** Importalo solo dall’interfaccia dell’app dopo l’accesso.
- Chiunque possieda le credenziali dell’unico account può modificare ed eliminare tutti i dati. Sul PC condiviso usa una password robusta e blocca la sessione quando opportuno.
- Richiede Internet; non c’è modalità di modifica offline. I pulsanti quantità usano transazioni Firestore.
- La versione GitHub Pages è una web app: non serve Firebase Hosting. Per un dominio dedicato o installazione PWA completa si potrà migrare in seguito.
- La sintassi JavaScript è stata controllata, ma l’accesso e la sincronizzazione reali richiedono una prova nel tuo progetto Firebase.


## Varianti collegate
Le varianti con lo stesso nome nella stessa categoria e sottocategoria vengono visualizzate sotto un solo materiale. Ogni variante ha giacenza e soglia indipendenti. Le tendine partono chiuse.
