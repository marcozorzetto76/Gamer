# Meteo Park — Game Design Document

*Nome di lavoro. Alternative: Sunny Village, Cielo Park, Weatherlings.*

## 1. L'idea in una frase

Un gioco cozy di merge e collezione dove **il meteo e l'ora reali della città del giocatore
cambiano il mondo di gioco in tempo reale**: se fuori piove, nel tuo parco piove e compaiono
creature acquatiche rare; di notte escono le creature notturne; con la neve arrivano eventi
invernali.

## 2. Perché è una buona idea

### La novità (USP)
Nessun gioco casual mainstream usa il meteo reale come **motore centrale** del gameplay.
Pokémon GO lo usa marginalmente, ma richiede di camminare. Qui il meteo È il gioco:

- Crea un **motivo naturale e gratuito per riaprire l'app**: "Sta piovendo! Apro il gioco
  per prendere le creature della pioggia." Nessuna notifica invasiva: è il mondo reale a
  fare da notifica.
- È **immediatamente comprensibile a tutte le età**: un bambino di 6 anni e una nonna di 70
  capiscono "quando piove davvero, piove anche nel gioco".
- È **virale per natura**: le creature rare legate a eventi meteo insoliti (temporale,
  neve a bassa quota, nebbia) spingono a condividere ("da me c'è la nebbia, ho preso il
  Nebbiolo!").
- Ogni giocatore vive un gioco **diverso in base a dove abita**: un giocatore di Palermo e
  uno di Oslo hanno collezioni naturalmente complementari → scambi e social.

### Il core loop collaudato
La novità sta nel "contorno", ma il cuore è un **merge game**, uno dei generi con il
miglior rapporto semplicità/monetizzazione su mobile (vedi Merge Dragons, Merge Mansion:
centinaia di milioni di dollari). Non serve inventare un gameplay mai visto — serve un
gameplay che tutti sanno già giocare, con un guscio che nessuno ha ancora fatto.

## 3. Come si gioca

### Core loop (sessione da 3–5 minuti)
1. Nel tuo **parco** compaiono periodicamente "semi" e oggetti base.
2. **Trascini e unisci** (merge) due oggetti uguali → ne nasce uno di livello superiore
   (2 gocce → pozzanghera → stagno → laghetto...).
3. Gli oggetti evoluti **attirano creature** (i *Meteolini*): ogni creatura ha condizioni
   meteo precise per apparire. Il Girasolino appare col sole, il Tuffolo con la pioggia,
   il Lampino solo durante i temporali reali.
4. Le creature catturate **abitano il parco**, producono monete e si possono accarezzare,
   nutrire, far evolvere.
5. Con le monete **espandi e decori il parco** (meta-gioco di decorazione, fortissimo
   per la retention del pubblico casual).

### Il layer meteo (la magia)
- L'app legge posizione approssimativa (o città scelta a mano, per privacy/bambini) e
  interroga un servizio meteo (es. OpenWeatherMap / Open-Meteo, gratuito).
- Il parco riflette in tempo reale: sole, pioggia, neve, nebbia, vento, temporale,
  alba/tramonto/notte con il vero orario locale.
- **Ogni condizione sblocca contenuti diversi**: creature, semi speciali, mini-eventi.
- Chi vive in zone con poco meteo vario non è penalizzato: esistono "Palloni Meteo"
  (ottenibili giocando o comprabili) che evocano nel parco per 30 minuti un meteo a scelta.
  → Questa è anche una leva di monetizzazione elegante e non pay-to-win.

### Collezione (il Meteodex)
- ~120 creature al lancio, divise per famiglie meteo: Sole, Pioggia, Neve, Nebbia, Vento,
  Temporale, Notte, Alba, Arcobaleno (rarissime: serve pioggia+sole reali).
- Rarità: comune / rara / epica / leggendaria / stagionale.
- Eventi stagionali automatici: d'inverno famiglie Neve in evidenza, d'estate famiglie Sole.
  Il calendario dei contenuti si scrive quasi da solo seguendo le stagioni.

### Perché è per tutte le età
- Un solo gesto: trascinare. Niente riflessi, niente timer punitivi, niente game over.
- Estetica morbida, colorata, zero violenza → rating 4+/PEGI 3.
- Profondità opzionale: i bambini uniscono e accarezzano le creature; gli adulti
  ottimizzano la scacchiera, completano il Meteodex e decorano.

## 4. Monetizzazione (modello ibrido IAP + ads, lo standard più redditizio nel casual)

1. **Rewarded ads (volontarie)** — "Guarda un video per: raddoppiare le monete /
   un seme raro / 10 min di meteo speciale". Zero interstitial forzati: nel cozy
   distruggono retention e recensioni.
2. **Gemme (valuta premium)** — accelerare produzione, comprare Palloni Meteo,
   slot extra sulla scacchiera. Pacchetti da 1,99 € a 49,99 €.
3. **Season Pass stagionale (4,99 €)** — binario gratuito + premium, allineato alle
   stagioni reali (Pass Autunno, Pass Inverno...). È il singolo strumento con il miglior
   ROI nel genere.
4. **Cosmetici** — decorazioni per il parco, cappellini per le creature, skin meteo
   (pioggia di stelle, neve dorata). Margine puro, adorati dal pubblico casual.
5. **Remove Ads una tantum (3,99 €)** — converte chi odia la pubblicità.
6. **Starter pack (0,99–2,99 €)** — offerta unica nei primi giorni per la prima conversione.

Metriche obiettivo del genere: D1 retention ~40%, D30 ~10%, ARPDAU 0,05–0,15 $.
Il gancio meteo lavora esattamente sulla metrica più difficile: il ritorno spontaneo.

## 5. Fattibilità tecnica

| Scelta | Proposta |
|---|---|
| Engine | **Unity** (C#) — un solo codice per iOS+Android, ecosistema ads/IAP maturo. Alternativa più leggera: Godot 4 o Flutter+Flame |
| Grafica | 2D flat/cartoon, palette pastello. Asset commissionabili o da marketplace per l'MVP |
| Meteo | Open-Meteo (gratuito, senza API key) o OpenWeatherMap; cache lato server per non sforare i limiti |
| Backend | Firebase (auth anonima, cloud save, remote config, analytics) |
| Ads | AdMob o LevelPlay (mediazione) |
| IAP | Unity IAP / RevenueCat |
| Privacy | Posizione **opzionale**: si può scegliere la città a mano. Fondamentale per il rating bambini (COPPA/GDPR-K) |

### Roadmap MVP (~3 mesi di lavoro focalizzato)
1. **Mese 1** — Scacchiera merge + 3 catene di oggetti + economia base + salvataggio.
2. **Mese 2** — Integrazione meteo reale + 30 creature (3 famiglie) + parco decorabile.
3. **Mese 3** — Ads + IAP + tutorial + soft launch in 1–2 paesi piccoli (es. Filippine,
   Nuova Zelanda) per misurare retention prima del lancio globale.

## 6. Rischi e mitigazioni

- **"Il merge è affollato"** → vero, ma si compete con il *guscio* (meteo reale), non con
  la meccanica. In ASO/marketing si vende la novità: "il primo gioco che vive col tuo cielo".
- **Meteo monotono in alcune zone** → Palloni Meteo + eventi globali ("in questo weekend
  piove per tutti nel mondo di gioco").
- **Costo API meteo a scala** → cache per città lato server: 1 richiesta serve migliaia
  di utenti della stessa zona.
- **UA (costo acquisizione utenti)** → il gancio è fortemente "clippabile" per TikTok/Reels:
  video split-screen "fuori piove / nel gioco piove" a costo quasi zero.

## 7. Prossimi passi

1. Validare il nome e registrare i domini/handle social.
2. Prototipo greybox della scacchiera merge (1–2 settimane).
3. Prototipo del layer meteo con Open-Meteo.
4. Definire le prime 3 famiglie di creature con un artista.
5. Soft launch → misurare D1/D7 → iterare → lancio globale.
