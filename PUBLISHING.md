# 📦 Guida alla pubblicazione di Meteo Park

Il progetto è già impacchettato con [Capacitor](https://capacitorjs.com/): la cartella `app/`
contiene i progetti nativi **Android** (`app/android/`) e **iOS** (`app/ios/`) pronti da aprire
in Android Studio e Xcode.

## Struttura

```
prototype/index.html   ← il gioco (fonte unica della verità)
app/
  www/index.html       ← copia sincronizzata per l'app
  capacitor.config.json← ID app: com.zorzetto.meteopark
  assets/icon.png      ← icona 1024×1024 per gli store
  assets/splash.png    ← splash 2732×2732
  android/             ← progetto Android Studio (Gradle)
  ios/                 ← progetto Xcode
```

Dopo ogni modifica al gioco: `cd app && npm run sync` (copia `prototype/index.html` in
`www/` e aggiorna i progetti nativi).

## Cosa serve (una tantum)

| Cosa | Costo | Dove |
|---|---|---|
| Account Google Play Developer | 25 $ una tantum | https://play.google.com/console |
| Account Apple Developer | 99 $/anno | https://developer.apple.com |
| Android Studio (per l'AAB) | gratis | https://developer.android.com/studio |
| Xcode su un Mac (per iOS) | gratis | Mac App Store |
| Privacy policy pubblica (obbligatoria su entrambi gli store) | gratis | una pagina web qualsiasi |

## Android — passo per passo

1. Apri il progetto: `cd app && npx cap open android` (o apri `app/android` da Android Studio).
2. Genera le icone: in Android Studio → click destro su `res` → *New → Image Asset* →
   usa `app/assets/icon.png`. (In alternativa, sul tuo computer:
   `npm i -D @capacitor/assets && npx capacitor-assets generate` le genera tutte da `assets/`.)
3. Crea la chiave di firma (conservala per sempre, senza non potrai più aggiornare l'app):
   `Build → Generate Signed Bundle → crea nuovo keystore`.
4. Genera l'**Android App Bundle**: `Build → Generate Signed Bundle → AAB → release`.
5. Su Play Console: crea l'app → carica l'AAB in una release di produzione (o prima in
   *internal testing*, consigliato) → compila la scheda store → invia in revisione.
   La revisione richiede in genere 1–7 giorni.

## iOS — passo per passo

1. Su un Mac: `cd app && npx cap open ios` (apre Xcode; alla prima apertura Xcode risolve i
   pacchetti automaticamente).
2. In *Signing & Capabilities* seleziona il tuo team Apple Developer.
3. Trascina `app/assets/icon.png` nell'Asset Catalog `AppIcon` (Xcode 14+ genera da solo
   tutte le misure con "Single Size").
4. `Product → Archive` → *Distribute App* → App Store Connect.
5. Su App Store Connect: crea la scheda app → aggiungi build, screenshot, descrizione →
   invia in revisione (1–3 giorni in media).

## Scheda store (già pronta da adattare)

- **Nome**: Meteo Park
- **Sottotitolo**: Il gioco che vive col tuo cielo
- **Descrizione breve**: Fondi, colleziona e gioca col meteo vero della tua città!
  Quando piove fuori… piove anche nel tuo parco, e arrivano creature rare!
- **Categoria**: Giochi / Puzzle (casual)
- **Classificazione**: PEGI 3 / 4+ (nessun contenuto sensibile)
- **Parole chiave**: merge, meteo, weather, cozy, creature, collezione, rilassante, bambini
- **Screenshot**: falli dal gioco vero su device (obbligatori: 6.5" e 5.5" per iOS;
  telefono + tablet 7"/10" per Play). I video "fuori piove / nel gioco piove" sono l'asset
  di marketing più forte: preparane uno da 15–30 secondi.

## Privacy (importante, rating bambini)

- Il gioco chiede la **posizione solo quando l'utente tocca "Usa il mio meteo reale"**,
  e i permessi sono già dichiarati (Android `ACCESS_COARSE_LOCATION`, iOS
  `NSLocationWhenInUseUsageDescription`). La posizione non viene salvata né trasmessa
  a terzi (va solo a Open-Meteo per la richiesta meteo).
- Nella dichiarazione *Data Safety* (Play) e *App Privacy* (App Store) indica:
  posizione approssimativa, uso solo in-app, non collegata all'identità, nessun tracciamento.
- Pubblica una privacy policy (una pagina statica va benissimo) e linkala in entrambe le schede.

## Prossimi passi per la monetizzazione reale

Il gioco oggi ha una pubblicità *demo* (finta). Prima del lancio:

1. **AdMob** (rewarded video): plugin `@capacitor-community/admob` — sostituisci il
   pulsante demo con `RewardAd`. Configura `ca-app-pub-…` per iOS e Android.
2. **Acquisti in-app** (gemme, remove-ads): `@revenuecat/purchases-capacitor` è la via
   più semplice (gestisce ricevute di entrambi gli store).
3. Per il pubblico bambini: attiva su AdMob i "tag for child-directed treatment" e
   annunci certificati famiglie, o la revisione degli store respingerà l'app.

## Checklist finale prima dell'invio

- [ ] Testato su un telefono Android reale (`npx cap run android`)
- [ ] Testato su un iPhone reale
- [ ] Icone e splash generate in tutte le misure
- [ ] Versione e `versionCode`/`build number` impostati
- [ ] Privacy policy online e linkata
- [ ] Pubblicità demo sostituita con AdMob reale (o rimossa per la v1)
- [ ] Screenshot e video per la scheda store
- [ ] Keystore Android salvato in un posto sicuro (+ backup!)
