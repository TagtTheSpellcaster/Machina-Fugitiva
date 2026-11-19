# Machina Fugitiva

![Version](https://img.shields.io/badge/version-1.2.1-c79a56?style=flat-square)
![License](https://img.shields.io/badge/license-AGPL--3.0-blue?style=flat-square)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![Dependencies](https://img.shields.io/badge/dependencies-none-brightgreen?style=flat-square)

**Machina Fugitiva** (Officina degli Enigmi - Machina N. 005) è un videogioco platform 2D ad ambientazione steampunk sviluppato interamente in HTML5, CSS3 e JavaScript vanilla su singolo file, privo di dipendenze esterne.

L'obiettivo del giocatore è guidare un automa in fuga attraverso quattro settori meccanici, raccogliendo tutti gli ingranaggi disseminati lungo il percorso per sbloccare la porta di uscita ed evitare pericoli ambientali e pattuglie robotiche.

---

## Caratteristiche Principali

- **Architettura Zero-Dependency:** Motore di gioco, fisica, gestione delle collisioni, rendering grafico (HTML5 Canvas 2D) e sintesi audio (Web Audio API) sono contenuti in un unico file `machina-fugitiva.html`.
- **Fisica Platform Reattiva:** Implementazione di *coyote time* (tolleranza al salto dopo aver lasciato una piattaforma), *jump buffering* (memorizzazione dell'input di salto prima dell'atterraggio) e salto ad altezza variabile in base alla durata della pressione del tasto.
- **Quattro Livelli Tematici:**
  1. **La Fonderia** (*Primi passi tra le presse*): Introduzione alle meccaniche base, piattaforme mobili e primi automi pattugliatori.
  2. **Le Caldaie** (*Vapore, nastri e molle*): Introduzione di nastri trasportatori direzionali, getti di vapore intermittenti e molle di rimbalzo.
  3. **La Torre dell'Orologio** (*Ingranaggi sospesi nel vuoto*): Sezioni platform verticali su piattaforme sospese e ascensori meccanici.
  4. **Il Cuore della Macchina** (*Tutto in movimento*): Livello finale che combina tutte le trappole e gli elementi meccanici incontrati in precedenza.
- **Sistema Audio Ibrido:**
  - Effetti sonori generati proceduralmente in tempo reale tramite oscillatori della Web Audio API.
  - Supporto per traccia musicale di sottofondo (`Clockwork_Pursuit.mp3`) con regolazione logaritmica del volume.
- **Grafica con Fallback Automatico:** Supporto per sfondi fotografici/illustrati esterni con parallasse e sfocatura pre-renderizzata su canvas offscreen; qualora i file immagine non siano presenti, il motore genera automaticamente uno sfondo vettoriale procedurale multistrato coerente con la palette cromatica del livello.
- **Salvataggio Progressi:** Memorizzazione automatica dell'ultimo livello raggiunto e delle preferenze audio tramite `localStorage`.
- **Supporto Multi-Dispositivo:** Controlli ottimizzati per tastiera su desktop e pulsanti touch dedicati su schermi capacitivi (rilevati tramite media query `hover` e `pointer`).

---

## Installazione ed Esecuzione

Non è richiesta alcuna procedura di build, compilazione o installazione di pacchetti.

1. Clona il repository o scarica i file del progetto:
   ```bash
   git clone https://github.com/tuo-utente/machina-fugitiva.git
   ```
2. Apri il file `machina-fugitiva.html` con un qualsiasi browser web moderno (Chrome, Firefox, Edge, Safari).

### Risorse Opzionali

Il gioco funziona completamente anche con il solo file HTML. Tuttavia, per abilitare la colonna sonora e gli sfondi ad alta risoluzione, posizionare i seguenti file nella stessa directory di `machina-fugitiva.html`:

- `Clockwork_Pursuit.mp3` (Musica di sottofondo in loop)
- `fonderia.jpg` (Sfondo Livello 1)
- `caldaie.jpg` (Sfondo Livello 2)
- `torre.jpg` (Sfondo Livello 3)
- `cuore.jpg` (Sfondo Livello 4)

---

## Comandi di Gioco

### Tastiera
| Tasto | Azione |
| :--- | :--- |
| `A` / `Freccia Sinistra` | Muovi a sinistra |
| `D` / `Freccia Destra` | Muovi a destra |
| `Spazio` / `W` / `Freccia Su` | Salta (tieni premuto per un salto più alto) |
| `P` / `Esc` / `Invio` | Avvia partita / Metti in pausa / Riprendi |

### Dispositivi Touch
Su dispositivi privi di puntatore di precisione, sotto l'area di gioco compaiono automaticamente tre controlli dedicati per il movimento laterale e il salto.

### Codici Segreti (Easter Egg)
Digitando specifiche sequenze di tasti durante la sessione di gioco si attivano funzioni di debug.
No, non ve li dico.

---

## Struttura Tecnica

- **Risoluzione Logica Canvas:** `960x544` pixel (griglia composta da `30x17` tile da `32x32` pixel ciascuno).
- **Ciclo di Aggiornamento:** Loop a timestep fisso (`60 Hz`, `STEP = 1000/60 ms`) disaccoppiato dal rendering `requestAnimationFrame` per garantire determinismo fisico indipendente dal refresh rate del monitor.
- **Gestione Stati:** Macchina a stati finiti (`title`, `play`, `paused`, `dying`, `clear`, `gameover`, `win`).

---

## Licenza

Questo progetto è distribuito sotto i termini della licenza **GNU Affero General Public License v3.0 (AGPL-3.0)**. Consulta il file `LICENSE` nel repository per i dettagli completi.
