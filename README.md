# Itaca Lite: modifiche estetiche

Modifiche **solo estetiche** per Itaca Lite (logo della galea animato, intestazione grande, pagina di benvenuto).
Le funzionalità non sono state toccate.

## Da dove partire

**Il file da usare è uno solo: [`INTEGRAZIONE-ESTETICA.md`](INTEGRAZIONE-ESTETICA.md).**

Dallo al tuo Claude insieme alla tua versione attuale di `Itaca Lite.html` e chiedigli di applicarlo.
Contiene i blocchi da aggiungere o sostituire, ognuno agganciato a un pezzo di testo riconoscibile
(mai a numeri di riga), quindi funziona anche se nel frattempo hai cambiato il file.
Ogni blocco è racchiuso tra commenti `[ESTETICA] inizio` / `[ESTETICA] fine`.

- **Lotto 1:** logo della galea, intestazione grande, logo animato, interruttore «Logo animato» in Impostazioni › Aspetto,
  icona della scheda e icone scaricabili.
- **Lotto 2:** pagina di benvenuto (giorno e notte) e Impostazioni › Pagina iniziale: Nessuna / Benvenuto.

## La cartella `riferimenti/`: solo da guardare

> ⚠️ **Non usare questi file al posto della tua app e non copiarli dentro.**
> Servono solo per vedere come deve venire il risultato.

| File | A cosa serve |
|---|---|
| `SOLO-ESEMPIO Itaca Lite 1.13.0 con estetica.html` | La versione **1.13.0** con le modifiche già applicate. Aprila nel browser per vedere il risultato. È più vecchia della tua: le tue funzionalità nuove qui non ci sono. |
| `anteprima-benvenuto.png` | Come appare la pagina di benvenuto. |
| `bozza-benvenuto.html` | La pagina di benvenuto da sola, da aprire nel browser. |
| `logo-itaca.svg` | Il disegno del logo (senza cerchio). |
| `logo-originale.jpg` | Il logo originale da cui è ricalcato. |
