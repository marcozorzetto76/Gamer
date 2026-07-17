# 🌦️ Meteo Park

Un gioco mobile cozy di merge e collezione dove **il meteo reale della tua città cambia il gioco in tempo reale**.

- 📄 [Game Design Document](GAME_DESIGN.md) — concept, monetizzazione, roadmap
- 🎮 [Prototipo giocabile](prototype/index.html) — HTML5, apri il file nel browser (meglio da smartphone)
- 📦 [Guida alla pubblicazione](PUBLISHING.md) — progetto Capacitor in `app/` con Android e iOS già scaffolded

## Il prototipo

| Cosa | Stato |
|---|---|
| Scacchiera merge 6×6 con drag & drop touch | ✅ |
| 3 catene di oggetti (Acqua, Pianta, Stella), 4 livelli ciascuna | ✅ |
| 9 Meteolini catturabili, legati a 7 condizioni meteo | ✅ |
| Meteo con effetti visivi (pioggia, neve, lampi, nebbia, notte, arcobaleno) | ✅ |
| Meteo reale via Open-Meteo (geolocalizzazione, con fallback demo) | ✅ |
| Meteodex (collezione) + reddito passivo dalle creature | ✅ |
| Monetizzazione demo (rewarded ad finta +50 monete, Palloni Meteo) | ✅ |
| 10 lingue: IT, EN, ES, FR, DE, PT-BR, JA, KO, ZH, RU | ✅ |
| Salvataggio automatico (localStorage) | ✅ |
| Grafica vettoriale disegnata a mano (21 sprite SVG) | ✅ |
| Effetti sonori + musica generativa (WebAudio, zero asset) | ✅ |
| Splash screen animata, combo, parco vivo con creature | ✅ |
| Missioni giornaliere localizzate con ricompense | ✅ |
| Progetti nativi Android + iOS (Capacitor, in `app/`) | ✅ |

Nessuna dipendenza, nessuna build: un solo file HTML. Per la pubblicazione sugli store
si impacchetta con [Capacitor](https://capacitorjs.com/) (iOS + Android dallo stesso codice)
oppure si porta il game design su Unity per la versione di produzione.

## Come si gioca

1. Tocca la **nuvola ☁️** per far apparire oggetti.
2. **Trascina due oggetti uguali** uno sull'altro per unirli nel livello successivo.
3. Le unioni attirano i **Meteolini** — ma solo quelli del meteo attuale! Toccali per catturarli.
4. Cambia il meteo con i **Palloni 🎈** (demo) o usa il **meteo reale** della tua posizione.
5. Completa il **Meteodex 📔**: le creature catturate producono monete nel tempo.
