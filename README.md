# Condurre un Laser · ILCA

App web installabile (**PWA**) per imparare a condurre una deriva **Laser / ILCA**: rosa delle andature interattiva, anatomia della barca e dei suoi comandi, virata e strambata passo-passo, gestione di vento forte e raffiche (la tecnica del *sheet out* e dell'efficacia del timone) e recupero da scuffia.

Funziona **offline** una volta aperta e si può **installare sulla schermata Home** del telefono come un'app.

## File del progetto

```
index.html                 · l'app
manifest.webmanifest       · descrizione PWA (nome, icone, colori)
sw.js                      · service worker (cache offline)
icon-192.png               · icona
icon-512.png               · icona
icon-maskable-512.png      · icona "maskable" (Android)
apple-touch-icon.png       · icona iOS
favicon.svg / favicon-32.png · favicon
.nojekyll                  · evita l'elaborazione Jekyll su GitHub Pages
```

Tutti i percorsi sono **relativi**: l'app funziona correttamente anche servita da una sottocartella, come fa GitHub Pages.

## Pubblicare su GitHub Pages

1. Crea una repository chiamata **`CondurreUnLaserILCA`**.
2. Carica nella **radice** della repo tutti i file di questa cartella (trascinali nella pagina della repo, oppure usa `git`).
3. Vai su **Settings → Pages**.
4. In *Build and deployment*, alla voce **Source** scegli **Deploy from a branch**.
5. Seleziona il branch **`main`** e la cartella **`/ (root)`**, poi **Save**.
6. Attendi circa un minuto: l'app sarà online a

   ```
   https://<tuo-utente>.github.io/CondurreUnLaserILCA/
   ```

### Con git da terminale (alternativa al punto 2)

```bash
git init
git add .
git commit -m "PWA Condurre un Laser ILCA"
git branch -M main
git remote add origin https://github.com/<tuo-utente>/CondurreUnLaserILCA.git
git push -u origin main
```

## Installare l'app sul telefono

All'apertura compare un **disclaimer** da accettare una volta sola. Poi, se l'app non è già installata, vedi un pulsante **"Installa l'app"**:

- **Android (Chrome/Edge):** il pulsante apre il prompt di installazione nativo. A installazione avvenuta il pulsante sparisce da solo.
- **iPhone/iPad (Safari):** Apple non permette l'installazione automatica, quindi il pulsante mostra le istruzioni: **Condividi → Aggiungi alla schermata Home**. Quando apri l'app dall'icona in Home gira a schermo intero e il pulsante non appare più. (In Safari puoi anche toccare "L'ho già installata" per nasconderlo.)

Quando l'app gira già installata (modalità *standalone*) il pulsante resta nascosto.

## Aggiornare l'app dopo una modifica

Il service worker mette in cache i file. Dopo aver cambiato `index.html` o le icone, apri **`sw.js`** e incrementa la versione della cache, per esempio:

```js
const CACHE = 'laser-ilca-v2';
```

Così i dispositivi scaricheranno la versione nuova al successivo avvio.

## Nota

Contenuti a scopo **didattico**, sintesi in parole proprie di materiali di scuole e federazioni veliche riconosciute (ILCA, RYA Laser Handbook / The ILCA Book, NauticEd, note di vento forte di Glenn Bourke, fonti italiane per la terminologia). Non sostituisce un corso con istruttore o scuola riconosciuta (in Italia la **FIV**). Indossa sempre l'aiuto al galleggiamento e controlla il meteo.
