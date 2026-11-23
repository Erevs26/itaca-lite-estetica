# Itaca Lite — modifiche estetiche da integrare

**Per il Claude che riceve questo file.** Contiene SOLO modifiche estetiche, preparate e provate su Itaca Lite 1.13.0.
Le funzionalità non sono state toccate. Applica i blocchi qui sotto al file `Itaca Lite.html` attuale. Ogni blocco
dice **dove** va, con un punto di aggancio testuale e non con numeri di riga, perché il file nel frattempo può essere cambiato.
Se un aggancio non corrisponde più esattamente, cerca l'elemento equivalente e chiedi conferma prima di procedere.
Ogni blocco è racchiuso tra commenti `[ESTETICA] inizio` / `[ESTETICA] fine`: se sono già presenti, quella parte è già stata integrata.

## Lotto 1 — nuovo marchio (galea), intestazione grande e logo animato

**Cosa cambia per chi usa l'app**
- La colonna greca è sostituita dalla galea (barca, sole, isola, onde) in stile cartone, senza cerchio.
- Logo e nome in alto a sinistra molto più grandi: «Itaca» su una riga, «LITE» + versione sotto.
- La barca è sempre in viaggio: ondeggia e il mare le scorre sotto da destra a sinistra. Quando si apre un altro documento arrivano
  folate di vento da sinistra (da dietro la barca), la vela si gonfia, la barca prende slancio e per un attimo le onde scorrono più veloci.
- Nuovo interruttore in Impostazioni › Aspetto: «Logo animato». Viene salvato in `localStorage` alla chiave `itaca-logo-motion`
  (`'off'` = fermo). L'animazione si ferma anche con «riduci movimento» del sistema.
- Icona della scheda e icone scaricabili (Impostazioni › File, PNG/ICO) diventano la galea semplificata.

**Note tecniche**
- Il cambio documento non è agganciato al codice che apre i file: il blocco 1.6 osserva `document.title`, che l'app
  imposta già a `«● nome — Itaca Lite»`. Se il formato del titolo cambia, aggiorna solo la funzione `docName` del blocco 1.6.
- Il nuovo interruttore ha `name="logoMotion"`. Il gestore `settingsForm.addEventListener('change', …)` lo ignora
  (non è in `settingChoices`), quindi non serve registrarlo da nessuna parte: è gestito interamente dal blocco 1.6.
- La funzione `itacaIconSvg` prima leggeva i tracciati da `.brandmark path`. Ora è autonoma (blocco 1.5): non dipende più dall'intestazione.
- Restano nel CSS le vecchie regole `.brandmark .brand-line` / `.brand-fill`: sono innocue. Si possono cancellare, se si vuole.

### 1.1 Icona della scheda — SOSTITUIRE
**Dove:** nel `<head>`, l'intera riga che inizia con `<link id="appIcon" rel="icon"`.

```html
  <!-- [ESTETICA] icona della scheda: galea -->
  <link id="appIcon" rel="icon" type="image/svg+xml" href="data:image/svg+xml,%3Csvg xmlns=%22http://www.w3.org/2000/svg%22 viewBox=%223 -134 850 850%22 stroke-linecap=%22round%22 stroke-linejoin=%22round%22%3E%3Ccircle cx=%22585%22 cy=%2262%22 r=%2252%22 fill=%22%23dcbf8c%22 /%3E%3Cg%3E%3Cpath d=%22M137,238 L260,191 C275,186 290,188 300,186 L500,121 C506,118 512,118 516,122 L578,160 L650,118 C656,115 662,115 668,118 L735,163 C745,168 760,163 772,168 C780,171 785,176 790,180 L842,236 Z%22 fill=%22%23dbbd8a%22 /%3E%3Cpath d=%22M655,118 L735,163 C745,168 760,163 772,168 C780,171 785,176 790,180 L842,236 L700,236 L640,188 C650,170 655,145 655,118 Z%22 fill=%22%23a0976e%22 /%3E%3Cpath d=%22M520,236 L585,196 L605,201 L640,188 L700,236%22 fill=%22none%22 stroke=%22%238a8766%22 stroke-width=%2218%22 /%3E%3Cpath d=%22M137,238 L260,191 C275,186 290,188 300,186 L500,121 C506,118 512,118 516,122 L578,160 L650,118 C656,115 662,115 668,118 L735,163 C745,168 760,163 772,168 C780,171 785,176 790,180 L842,236 Z%22 fill=%22none%22 stroke=%22%238a8766%22 stroke-width=%2222%22 /%3E%3Cpath d=%22M505,263 H592 M535,288 H597 M662,262 H735%22 stroke=%22%23dcc49c%22 stroke-width=%2222%22 /%3E%3C/g%3E%3Cg%3E%3Cg%3E%3Cg%3E%3Cpath d=%22M283,105 L470,57 C500,120 505,230 458,303 C445,295 420,287 380,288 C345,289 310,300 282,315 C305,260 312,170 283,105 Z%22 fill=%22%2396a181%22 /%3E%3Cpath d=%22M283,105 C305,160 312,250 282,315%22 fill=%22none%22 stroke=%22%23535540%22 stroke-width=%2222%22 /%3E%3Cpath d=%22M470,57 C500,120 505,230 458,303 L440,352%22 fill=%22none%22 stroke=%22%23535540%22 stroke-width=%2222%22 /%3E%3Cpath d=%22M208,354 C260,320 320,290 380,288 C420,287 445,295 458,303%22 fill=%22none%22 stroke=%22%23535540%22 stroke-width=%2222%22 /%3E%3C/g%3E%3Cpath d=%22M380,22 V357%22 stroke=%22%23535540%22 stroke-width=%2222%22 /%3E%3Cpath d=%22M255,106 L485,45%22 stroke=%22%23535540%22 stroke-width=%2222%22 /%3E%3Cpath d=%22M30,262 C28,345 60,405 150,455 C260,458 360,470 430,466 C470,463 470,448 500,450 C530,452 540,468 565,466 C595,463 600,446 630,444 C655,443 672,446 688,446 C662,432 648,415 648,385 L648,375 L190,375 C100,372 46,330 44,262 Z%22 fill=%22%23929c7d%22 /%3E%3Cpath d=%22M236,398 H640 L652,420 H214 Z%22 fill=%22%239aa585%22 /%3E%3Cpath d=%22M201,433 H660 L686,446 C600,446 560,470 520,462 C480,455 470,462 430,466 L172,462 Z%22 fill=%22%239aa585%22 /%3E%3Cpath d=%22M196,427 H655%22 stroke=%22%23535540%22 stroke-width=%2224%22 /%3E%3Cpath d=%22M236,398 L169,465 M303,398 L236,465 M370,398 L303,465 M438,398 L371,465 M506,398 L439,465%22 stroke=%22%23535540%22 stroke-width=%2222%22 /%3E%3Cpath d=%22M30,262 C28,345 60,405 150,455 C260,458 360,470 430,466 C470,463 470,448 500,450 C530,452 540,468 565,466 C595,463 600,446 630,444 C655,443 672,446 688,446%22 fill=%22none%22 stroke=%22%23535540%22 stroke-width=%2224%22 /%3E%3Cpath d=%22M647,380 C650,425 690,445 745,462%22 fill=%22none%22 stroke=%22%23535540%22 stroke-width=%2224%22 /%3E%3Cpath d=%22M90,249 C94,258 108,258 114,250 C116,246 116,242 116,238 C117,220 104,206 82,206 C55,206 42,230 44,262 C46,330 100,372 190,375 L500,375%22 fill=%22none%22 stroke=%22%23535540%22 stroke-width=%2264%22 stroke-linecap=%22round%22 /%3E%3Cpath d=%22M104,256 C109,254 113,250 115,246 C116,243 116,240 116,238 C117,220 104,206 82,206 C55,206 42,230 44,262 C46,330 100,372 190,375 L500,375%22 fill=%22none%22 stroke=%22%23dbbd8a%22 stroke-width=%2216%22 stroke-linecap=%22round%22 /%3E%3Cpath d=%22M480,390 H645%22 stroke=%22%23535540%22 stroke-width=%2228%22 stroke-linecap=%22butt%22 /%3E%3Cpath d=%22M626,272 H641 V383 H480 V367 C595,362 624,330 626,272 Z%22 fill=%22%23dbbd8a%22 /%3E%3Cpath d=%22M636,282 C630,340 600,372 540,383 L637,383 Z%22 fill=%22%23c9a46f%22 /%3E%3Cpath d=%22M632,276 V380%22 stroke=%22%23dbbd8a%22 stroke-width=%229%22 stroke-linecap=%22butt%22 /%3E%3Cpath d=%22M606,262 H653 V385 H641 V272 H626 C624,330 595,362 480,367 L480,355 C575,350 606,330 606,262 Z%22 fill=%22%23535540%22 /%3E%3Cg fill=%22%23535540%22%3E%3Ccircle cx=%22237%22 cy=%22382%22 r=%2212%22 /%3E%3Ccircle cx=%22305%22 cy=%22382%22 r=%2212%22 /%3E%3Ccircle cx=%22372%22 cy=%22382%22 r=%2212%22 /%3E%3Ccircle cx=%22440%22 cy=%22382%22 r=%2212%22 /%3E%3Ccircle cx=%22505%22 cy=%22382%22 r=%2212%22 /%3E%3C/g%3E%3Cg fill=%22%23535540%22 stroke=%22%23535540%22 stroke-width=%2210%22%3E%3Cpath d=%22M234,464 L242,470 L222,521 L184,521 L214,478 Z%22 /%3E%3Cpath d=%22M301,464 L309,470 L289,521 L251,521 L281,478 Z%22 /%3E%3Cpath d=%22M369,464 L377,470 L357,521 L319,521 L349,478 Z%22 /%3E%3Cpath d=%22M437,464 L445,470 L425,521 L387,521 L417,478 Z%22 /%3E%3C/g%3E%3Cpath d=%22M215,307 L146,440%22 stroke=%22%23535540%22 stroke-width=%2222%22 /%3E%3Cpath d=%22M124,443 L144,437 L148,447 L121,519 L76,519 Z%22 fill=%22%23dbbd8a%22 stroke=%22%23535540%22 stroke-width=%2218%22 /%3E%3C/g%3E%3C/g%3E%3Cg fill=%22none%22 stroke=%22%239ea68a%22 stroke-width=%2222%22%3E%3Cpath d=%22M17,456 C35,462 55,463 75,458 C95,453 105,448 118,446%22 /%3E%3Cpath d=%22M447,513 C480,500 520,497 550,502 C580,507 590,516 615,514 C645,511 665,500 682,493%22 /%3E%3Cpath d=%22M257,552 C290,535 340,530 380,538 C410,545 425,556 450,554 C490,550 520,535 575,537%22 /%3E%3C/g%3E%3C/svg%3E">
```

### 1.2 Stile — AGGIUNGERE
**Dove:** in fondo al primo blocco `<style>` del documento (quello principale nel `<head>`), subito prima del suo `</style>`.
Deve stare dopo le regole esistenti `.brand` / `.brandmark`, perché le sovrascrive.

```css
/* [ESTETICA] inizio: marchio galea + intestazione */
.itaca-logo {
  --lg-ink: #535540; --lg-hill: #8a8766; --lg-sage: #96a181; --lg-hull: #929c7d; --lg-deck: #9aa585; --lg-sand: #dbbd8a;
  --lg-sand2: #c9a46f; --lg-sun: #dcbf8c; --lg-shade: #a0976e; --lg-sea: #9ea68a; --lg-glint: #dcc49c; --lg-wind: #7d8566;
}
:root[data-theme='dark'] .itaca-logo {   /* «Notte di luna» */
  --lg-ink: #cfc6a6; --lg-hill: #9c9473; --lg-sage: #7e9068; --lg-hull: #5d6b52; --lg-deck: #6b7b5d; --lg-sand: #b8995f;
  --lg-sand2: #977a4a; --lg-sun: #ebdcae; --lg-shade: #7b7152; --lg-sea: #86a08a; --lg-glint: #8f805c; --lg-wind: #d8d1b6;
}

/* intestazione: marchio grande, nome su due righe */
.brand { gap: 12px; min-height: 96px; padding: 20px calc(var(--side-x) + 2px) 14px; }
.brand .brandmark { flex: none; width: 112px; height: 73px; overflow: visible; }
.brand-text { display: grid; gap: 3px; min-width: 0; }
.brand .brand-name { font: 700 32px/1 var(--read); letter-spacing: -.01em; color: var(--ink); }
.brand-sub { display: flex; align-items: center; gap: 7px; font: 650 10.5px/1.2 var(--sans); letter-spacing: .16em; text-transform: uppercase; color: var(--muted); white-space: nowrap; }
.brand .brand-sub .app-version { margin: 0; letter-spacing: .02em; text-transform: none; }
@media (max-width: 1000px) {
  .brand { gap: 10px; }
  .brand .brandmark { width: 86px; height: 56px; }
  .brand .brand-name { font-size: 27px; }
}

/* movimento: la barca è sempre in viaggio verso destra (ondeggia, il mare le scorre sotto da destra a sinistra);
   al cambio documento arriva il vento da sinistra (da dietro), la vela si gonfia, la barca dà uno strappo e il mare accelera (velocità in 04-logo-motion.js) */
.itaca-logo .lg-boat { transform-box: view-box; transform-origin: 380px 450px; animation: lg-bob 4.2s ease-in-out infinite; }
.itaca-logo .lg-wave { transform-box: view-box; animation: lg-flow 3.6s linear infinite; }
.itaca-logo .lg-w1 { animation-delay: -1.2s; }
.itaca-logo .lg-w2 { animation-duration: 4s; animation-delay: -2.5s; }
.itaca-logo .lg-w3 { animation-duration: 4.4s; animation-delay: -.6s; }
.itaca-logo .lg-w4 { animation-duration: 3.2s; animation-delay: -1.9s; }
.itaca-logo .lg-w5 { animation-duration: 3.4s; animation-delay: -2.9s; }
/* !important: l'app spegne tutte le transizioni con «riduci movimento»; qui decide l'interruttore «Logo animato» */
.itaca-logo .lg-sail { transform-box: view-box; transform-origin: 380px 80px; transition: transform .7s cubic-bezier(.3, 1.5, .5, 1) !important; }
.itaca-logo.sailing .lg-sail { transition-delay: .35s !important; }
.itaca-logo .lg-wind path { stroke: var(--lg-wind); stroke-dasharray: 110 400; stroke-dashoffset: 110; opacity: 0; }
@keyframes lg-bob {
  0%, 100% { transform: translateY(0) rotate(-1.8deg); }
  50% { transform: translateY(16px) rotate(2deg); }
}
@keyframes lg-flow {
  0% { transform: translate(90px, 0); opacity: 0; }
  15% { opacity: 1; }
  50% { transform: translate(0, -6px); }
  85% { opacity: 1; }
  100% { transform: translate(-100px, 0); opacity: 0; }
}
@keyframes lg-surge { 0% { transform: none; } 40% { transform: translateX(30px); } 100% { transform: none; } }
@keyframes lg-gust { 0% { stroke-dashoffset: 110; opacity: 0; } 25% { opacity: 1; } 100% { stroke-dashoffset: -330; opacity: 0; } }
.itaca-logo.sailing .lg-wind path { animation: lg-gust .9s ease-in 2; }
.itaca-logo.sailing .lg-wind path:nth-child(2) { animation-delay: .12s; }
.itaca-logo.sailing .lg-wind path:nth-child(3) { animation-delay: .24s; }
.itaca-logo.sailing .lg-sail { transform: translateX(8px) scale(1.17, 1.05); }
.itaca-logo.sailing .lg-surge { animation: lg-surge 1.9s ease-in-out .45s; }
.itaca-logo.is-still *, .itaca-logo.is-still { animation: none !important; transition: none !important; }
/* [ESTETICA] fine: marchio galea + intestazione */
```

### 1.3 Intestazione — SOSTITUIRE
**Dove:** dentro `<header class="brand">`, sostituire le due righe
`<svg class="brandmark" …>…</svg>` (la colonna) e `<strong class="brand-name">Itaca Lite <span class="app-version" id="appVersion"></span></strong>`.
Il pulsante `#closeSidebar` che segue resta com'è. L'`id="appVersion"` è mantenuto, quindi il codice che scrive la versione continua a funzionare.

```html
        <!-- [ESTETICA] inizio: marchio galea animato + nome -->
        <svg class="brandmark itaca-logo" viewBox="0 10 860 560" aria-hidden="true" stroke-linecap="round" stroke-linejoin="round"><circle cx="585" cy="62" r="52" style="fill:var(--lg-sun)" class="lg-sun" /><g class="lg-island"><path d="M137,238 L260,191 C275,186 290,188 300,186 L500,121 C506,118 512,118 516,122 L578,160 L650,118 C656,115 662,115 668,118 L735,163 C745,168 760,163 772,168 C780,171 785,176 790,180 L842,236 Z" style="fill:var(--lg-sand)" /><path d="M655,118 L735,163 C745,168 760,163 772,168 C780,171 785,176 790,180 L842,236 L700,236 L640,188 C650,170 655,145 655,118 Z" style="fill:var(--lg-shade)" /><path d="M520,236 L585,196 L605,201 L640,188 L700,236" fill="none" stroke-width="9" style="stroke:var(--lg-hill)" /><path d="M137,238 L260,191 C275,186 290,188 300,186 L500,121 C506,118 512,118 516,122 L578,160 L650,118 C656,115 662,115 668,118 L735,163 C745,168 760,163 772,168 C780,171 785,176 790,180 L842,236 Z" fill="none" stroke-width="11" style="stroke:var(--lg-hill)" /><path d="M505,263 H592 M535,288 H597 M662,262 H735" stroke-width="11" style="stroke:var(--lg-glint)" /></g><g class="lg-wind" fill="none" stroke-width="13"><path d="M-20,110 H285" /><path d="M-30,160 H300" /><path d="M-10,210 H290" /></g><g class="lg-surge"><g class="lg-boat"><g class="lg-sail"><path d="M283,105 L470,57 C500,120 505,230 458,303 C445,295 420,287 380,288 C345,289 310,300 282,315 C305,260 312,170 283,105 Z" style="fill:var(--lg-sage)" /><path d="M283,105 C305,160 312,250 282,315" fill="none" stroke-width="11" style="stroke:var(--lg-ink)" /><path d="M470,57 C500,120 505,230 458,303 L440,352" fill="none" stroke-width="11" style="stroke:var(--lg-ink)" /><path d="M208,354 C260,320 320,290 380,288 C420,287 445,295 458,303" fill="none" stroke-width="11" style="stroke:var(--lg-ink)" /></g><path d="M380,22 V357" stroke-width="11" style="stroke:var(--lg-ink)" /><path d="M255,106 L485,45" stroke-width="11" style="stroke:var(--lg-ink)" /><path d="M30,262 C28,345 60,405 150,455 C260,458 360,470 430,466 C470,463 470,448 500,450 C530,452 540,468 565,466 C595,463 600,446 630,444 C655,443 672,446 688,446 C662,432 648,415 648,385 L648,375 L190,375 C100,372 46,330 44,262 Z" style="fill:var(--lg-hull)" /><path d="M236,398 H640 L652,420 H214 Z" style="fill:var(--lg-deck)" /><path d="M201,433 H660 L686,446 C600,446 560,470 520,462 C480,455 470,462 430,466 L172,462 Z" style="fill:var(--lg-deck)" /><path d="M196,427 H655" stroke-width="12" style="stroke:var(--lg-ink)" /><path d="M236,398 L169,465 M303,398 L236,465 M370,398 L303,465 M438,398 L371,465 M506,398 L439,465" stroke-width="11" style="stroke:var(--lg-ink)" /><path d="M30,262 C28,345 60,405 150,455 C260,458 360,470 430,466 C470,463 470,448 500,450 C530,452 540,468 565,466 C595,463 600,446 630,444 C655,443 672,446 688,446" fill="none" stroke-width="12" style="stroke:var(--lg-ink)" /><path d="M647,380 C650,425 690,445 745,462" fill="none" stroke-width="12" style="stroke:var(--lg-ink)" /><path d="M90,249 C94,258 108,258 114,250 C116,246 116,242 116,238 C117,220 104,206 82,206 C55,206 42,230 44,262 C46,330 100,372 190,375 L500,375" fill="none" stroke-width="40" stroke-linecap="round" style="stroke:var(--lg-ink)" /><path d="M104,256 C109,254 113,250 115,246 C116,243 116,240 116,238 C117,220 104,206 82,206 C55,206 42,230 44,262 C46,330 100,372 190,375 L500,375" fill="none" stroke-width="16" stroke-linecap="round" style="stroke:var(--lg-sand)" /><path d="M480,390 H645" stroke-width="14" stroke-linecap="butt" style="stroke:var(--lg-ink)" /><path d="M626,272 H641 V383 H480 V367 C595,362 624,330 626,272 Z" style="fill:var(--lg-sand)" /><path d="M636,282 C630,340 600,372 540,383 L637,383 Z" style="fill:var(--lg-sand2)" /><path d="M632,276 V380" stroke-width="9" stroke-linecap="butt" style="stroke:var(--lg-sand)" /><path d="M606,262 H653 V385 H641 V272 H626 C624,330 595,362 480,367 L480,355 C575,350 606,330 606,262 Z" style="fill:var(--lg-ink)" /><g style="fill:var(--lg-ink)"><circle cx="237" cy="382" r="12" /><circle cx="305" cy="382" r="12" /><circle cx="372" cy="382" r="12" /><circle cx="440" cy="382" r="12" /><circle cx="505" cy="382" r="12" /></g><g stroke-width="5" style="fill:var(--lg-ink);stroke:var(--lg-ink)"><path d="M234,464 L242,470 L222,521 L184,521 L214,478 Z" /><path d="M301,464 L309,470 L289,521 L251,521 L281,478 Z" /><path d="M369,464 L377,470 L357,521 L319,521 L349,478 Z" /><path d="M437,464 L445,470 L425,521 L387,521 L417,478 Z" /></g><path d="M215,307 L146,440" stroke-width="11" style="stroke:var(--lg-ink)" /><path d="M124,443 L144,437 L148,447 L121,519 L76,519 Z" stroke-width="9" style="fill:var(--lg-sand);stroke:var(--lg-ink)" /></g></g><g fill="none" stroke-width="11" style="stroke:var(--lg-sea)" class="lg-sea"><path d="M17,456 C35,462 55,463 75,458 C95,453 105,448 118,446" class="lg-wave lg-w1" /><path d="M447,513 C480,500 520,497 550,502 C580,507 590,516 615,514 C645,511 665,500 682,493" class="lg-wave lg-w2" /><path d="M257,552 C290,535 340,530 380,538 C410,545 425,556 450,554 C490,550 520,535 575,537" class="lg-wave lg-w3" /><path d="M690,505 C712,496 740,496 762,503" class="lg-wave lg-w4" /><path d="M40,515 C62,507 92,507 114,514" class="lg-wave lg-w5" /></g></svg>
        <span class="brand-text">
          <strong class="brand-name">Itaca</strong>
          <span class="brand-sub">Lite <span class="app-version" id="appVersion"></span></span>
        </span>
        <!-- [ESTETICA] fine: marchio galea animato + nome -->
```

### 1.4 Impostazioni › Aspetto — AGGIUNGERE
**Dove:** nella scheda Aspetto, subito dopo la `<div class="set-row">` che contiene `aria-labelledby="crittersLabel"`
(la riga «Animazione: Nessuna / Gatto / Barchetta»), dentro la stessa `<div class="set-card">`.

```html
          <!-- [ESTETICA] inizio: interruttore marchio animato -->
          <div class="set-row">
            <label class="set-label" for="setLogoMotion"><b>Logo animato</b><small>La barca naviga e gonfia le vele quando cambi documento (con le animazioni di Windows spente parte fermo)</small></label>
            <input type="checkbox" class="switch" id="setLogoMotion" name="logoMotion">
          </div>
          <!-- [ESTETICA] fine: interruttore marchio animato -->
```

### 1.5 Icona scaricabile — SOSTITUIRE
**Dove:** l'intera funzione `function itacaIconSvg(size) { … }` (sezione «Icona di Itaca come file»).
`itacaIconPng` e `itacaIconIco` restano invariate. Si può aggiornare anche il commento sopra la funzione, che parla della colonna.

```js
// [ESTETICA] inizio: icona scaricabile = galea (sostituisce la colonna)
function itacaIconSvg(size) {
  const f = size <= 24 ? 2.2 : size <= 48 ? 1.7 : size <= 128 ? 1.3 : 1;   // tratti più spessi nelle misure piccole
  return `<svg width="${size}" height="${size}" xmlns="http://www.w3.org/2000/svg" viewBox="3 -134 850 850" stroke-linecap="round" stroke-linejoin="round"><circle cx="585" cy="62" r="52" fill="#dcbf8c" /><g><path d="M137,238 L260,191 C275,186 290,188 300,186 L500,121 C506,118 512,118 516,122 L578,160 L650,118 C656,115 662,115 668,118 L735,163 C745,168 760,163 772,168 C780,171 785,176 790,180 L842,236 Z" fill="#dbbd8a" /><path d="M655,118 L735,163 C745,168 760,163 772,168 C780,171 785,176 790,180 L842,236 L700,236 L640,188 C650,170 655,145 655,118 Z" fill="#a0976e" /><path d="M520,236 L585,196 L605,201 L640,188 L700,236" fill="none" stroke="#8a8766" stroke-width="${+(9*f).toFixed(1)}" /><path d="M137,238 L260,191 C275,186 290,188 300,186 L500,121 C506,118 512,118 516,122 L578,160 L650,118 C656,115 662,115 668,118 L735,163 C745,168 760,163 772,168 C780,171 785,176 790,180 L842,236 Z" fill="none" stroke="#8a8766" stroke-width="${+(11*f).toFixed(1)}" /><path d="M505,263 H592 M535,288 H597 M662,262 H735" stroke="#dcc49c" stroke-width="${+(11*f).toFixed(1)}" /></g><g><g><g><path d="M283,105 L470,57 C500,120 505,230 458,303 C445,295 420,287 380,288 C345,289 310,300 282,315 C305,260 312,170 283,105 Z" fill="#96a181" /><path d="M283,105 C305,160 312,250 282,315" fill="none" stroke="#535540" stroke-width="${+(11*f).toFixed(1)}" /><path d="M470,57 C500,120 505,230 458,303 L440,352" fill="none" stroke="#535540" stroke-width="${+(11*f).toFixed(1)}" /><path d="M208,354 C260,320 320,290 380,288 C420,287 445,295 458,303" fill="none" stroke="#535540" stroke-width="${+(11*f).toFixed(1)}" /></g><path d="M380,22 V357" stroke="#535540" stroke-width="${+(11*f).toFixed(1)}" /><path d="M255,106 L485,45" stroke="#535540" stroke-width="${+(11*f).toFixed(1)}" /><path d="M30,262 C28,345 60,405 150,455 C260,458 360,470 430,466 C470,463 470,448 500,450 C530,452 540,468 565,466 C595,463 600,446 630,444 C655,443 672,446 688,446 C662,432 648,415 648,385 L648,375 L190,375 C100,372 46,330 44,262 Z" fill="#929c7d" /><path d="M236,398 H640 L652,420 H214 Z" fill="#9aa585" /><path d="M201,433 H660 L686,446 C600,446 560,470 520,462 C480,455 470,462 430,466 L172,462 Z" fill="#9aa585" /><path d="M196,427 H655" stroke="#535540" stroke-width="${+(12*f).toFixed(1)}" /><path d="M236,398 L169,465 M303,398 L236,465 M370,398 L303,465 M438,398 L371,465 M506,398 L439,465" stroke="#535540" stroke-width="${+(11*f).toFixed(1)}" /><path d="M30,262 C28,345 60,405 150,455 C260,458 360,470 430,466 C470,463 470,448 500,450 C530,452 540,468 565,466 C595,463 600,446 630,444 C655,443 672,446 688,446" fill="none" stroke="#535540" stroke-width="${+(12*f).toFixed(1)}" /><path d="M647,380 C650,425 690,445 745,462" fill="none" stroke="#535540" stroke-width="${+(12*f).toFixed(1)}" /><path d="M90,249 C94,258 108,258 114,250 C116,246 116,242 116,238 C117,220 104,206 82,206 C55,206 42,230 44,262 C46,330 100,372 190,375 L500,375" fill="none" stroke="#535540" stroke-width="${+(16+24*f).toFixed(1)}" stroke-linecap="round" /><path d="M104,256 C109,254 113,250 115,246 C116,243 116,240 116,238 C117,220 104,206 82,206 C55,206 42,230 44,262 C46,330 100,372 190,375 L500,375" fill="none" stroke="#dbbd8a" stroke-width="16" stroke-linecap="round" /><path d="M480,390 H645" stroke="#535540" stroke-width="${+(14*f).toFixed(1)}" stroke-linecap="butt" /><path d="M626,272 H641 V383 H480 V367 C595,362 624,330 626,272 Z" fill="#dbbd8a" /><path d="M636,282 C630,340 600,372 540,383 L637,383 Z" fill="#c9a46f" /><path d="M632,276 V380" stroke="#dbbd8a" stroke-width="9" stroke-linecap="butt" /><path d="M606,262 H653 V385 H641 V272 H626 C624,330 595,362 480,367 L480,355 C575,350 606,330 606,262 Z" fill="#535540" /><g fill="#535540"><circle cx="237" cy="382" r="12" /><circle cx="305" cy="382" r="12" /><circle cx="372" cy="382" r="12" /><circle cx="440" cy="382" r="12" /><circle cx="505" cy="382" r="12" /></g><g fill="#535540" stroke="#535540" stroke-width="${+(5*f).toFixed(1)}"><path d="M234,464 L242,470 L222,521 L184,521 L214,478 Z" /><path d="M301,464 L309,470 L289,521 L251,521 L281,478 Z" /><path d="M369,464 L377,470 L357,521 L319,521 L349,478 Z" /><path d="M437,464 L445,470 L425,521 L387,521 L417,478 Z" /></g><path d="M215,307 L146,440" stroke="#535540" stroke-width="${+(11*f).toFixed(1)}" /><path d="M124,443 L144,437 L148,447 L121,519 L76,519 Z" fill="#dbbd8a" stroke="#535540" stroke-width="${+(9*f).toFixed(1)}" /></g></g><g fill="none" stroke="#9ea68a" stroke-width="${+(11*f).toFixed(1)}"><path d="M17,456 C35,462 55,463 75,458 C95,453 105,448 118,446" /><path d="M447,513 C480,500 520,497 550,502 C580,507 590,516 615,514 C645,511 665,500 682,493" /><path d="M257,552 C290,535 340,530 380,538 C410,545 425,556 450,554 C490,550 520,535 575,537" /></g></svg>`;
}
// [ESTETICA] fine: icona scaricabile
```

### 1.6 Comportamento del logo — AGGIUNGERE
**Dove:** in fondo al documento, subito prima dell'ultimo `</body>` (quello reale, non quello dentro la stringa del modello di esportazione HTML).

```html
<!-- [ESTETICA] inizio: comportamento del marchio animato (blocco autonomo, non tocca il resto) -->
<script>
(() => {
  // Chi decide se il logo si muove: la scelta fatta in Impostazioni › Aspetto › «Logo animato»
  // ('on' / 'off' in localStorage). Finché non si è scelto, si segue il sistema: se è attivo
  // «riduci movimento» (in Windows: effetti di animazione spenti) il logo parte fermo.
  const KEY = 'itaca-logo-motion';
  const logo = document.querySelector('.brand .itaca-logo');
  const toggle = document.getElementById('setLogoMotion');
  if (!logo) return;
  const reduce = window.matchMedia ? matchMedia('(prefers-reduced-motion: reduce)') : null;
  let stored = null;
  try { stored = localStorage.getItem(KEY); } catch {}
  let enabled = true;
  const decide = () => { enabled = stored ? stored === 'on' : !(reduce && reduce.matches); };
  const apply = () => { logo.classList.toggle('is-still', !enabled); if (toggle) toggle.checked = enabled; };
  decide(); apply();
  if (reduce && reduce.addEventListener) reduce.addEventListener('change', () => { if (!stored) { decide(); apply(); } });
  if (toggle) {
    toggle.addEventListener('change', () => {
      enabled = toggle.checked;
      stored = enabled ? 'on' : 'off';
      try { localStorage.setItem(KEY, stored); } catch {}
      apply();
    });
  }
  // Cambio documento: l'app aggiorna il titolo della scheda («● nome — Itaca Lite»).
  // Lo osserviamo invece di agganciarci al codice che apre i documenti.
  const docName = () => document.title.replace(/^●\s*/, '').replace(/\s+—\s+Itaca Lite$/, '');
  let last = docName(), timer = 0;
  const sail = () => {
    if (!enabled) return;
    logo.classList.remove('sailing');
    void logo.getBoundingClientRect();             // riparte anche con cambi ravvicinati
    logo.classList.add('sailing');
    clearTimeout(timer);
    timer = setTimeout(() => logo.classList.remove('sailing'), 2500);
    // il mare accelera mentre la barca prende il vento, poi rallenta piano (senza scatti)
    seaRush();
  };
  // velocità del mare nel tempo (ms dal cambio documento): sale con la folata, poi torna normale piano
  const RUSH = [[0, 1], [450, 1], [1150, 3.5], [1600, 3.5], [2800, 1]];
  let rushId = 0;
  const seaRush = () => {
    const waves = [...logo.querySelectorAll('.lg-wave')].flatMap(w => w.getAnimations ? w.getAnimations() : []);
    if (!waves.length) return;
    const id = ++rushId, t0 = performance.now();
    const setRate = r => waves.forEach(a => a.updatePlaybackRate ? a.updatePlaybackRate(r) : (a.playbackRate = r));
    const step = now => {
      if (id !== rushId) return;                     // è partito un nuovo cambio documento
      const t = now - t0;
      const i = RUSH.findIndex(([ms]) => ms > t);
      if (i === -1) return setRate(1);
      const [a, ra] = RUSH[i - 1], [b, rb] = RUSH[i];
      setRate(ra + (rb - ra) * (t - a) / (b - a));
      requestAnimationFrame(step);
    };
    requestAnimationFrame(step);
  };
  const title = document.querySelector('title');
  if (title) new MutationObserver(() => {
    const name = docName();
    if (name === last) return;
    last = name;
    if (name && name !== 'Itaca Lite') sail();
  }).observe(title, { childList: true, characterData: true, subtree: true });
})();
</script>
<!-- [ESTETICA] fine: comportamento del marchio animato -->
```

### Verifica dopo l'integrazione
1. Si apre l'app: la galea compare grande in alto a sinistra e ondeggia. In tema scuro i contorni sono chiari.
2. Si cambia documento: arriva il vento da sinistra, la vela si gonfia, le onde accelerano e poi tornano normali (circa 2,5 secondi).
3. Impostazioni › Aspetto › «Logo animato» disattivato: la barca si ferma, e resta ferma anche ricaricando la pagina.
4. Impostazioni › File › Mac PNG / Windows ICO: l'icona scaricata è la galea.
5. La console non mostra errori nuovi.

## Lotto 2: pagina di benvenuto

**Cosa cambia per chi usa l'app**
- All'apertura compare subito, già completa, una pagina a tutto schermo «Benvenuto su Itaca»: il logo grande (sole o luna,
  isola, galea), il titolo, la frase e i pulsanti.
- La scena resta viva: la barca naviga e circa ogni 7 secondi una folata gonfia la vela.
- Un clic su un pulsante o in un punto qualsiasi: sole, isola e nave volano rimpicciolendosi fino al logo dell'intestazione
  (in alto a sinistra, `.brand .itaca-logo`) e la pagina sfuma nell'app. Con **Esc** si entra subito. Se la barra laterale è chiusa
  (logo non visibile) si entra subito con una dissolvenza.
- I pulsanti premono quelli già esistenti dell'app: «Apri cartella» → `#openDir`, «Importa cartella» → `#importFolder`.
  «Riprendi il viaggio» compare solo se l'app ricorda una cartella (`#startAction` mostra «Consenti accesso» o «Mostra documenti»,
  oppure `#workStart` è nascosto) e in quel caso preme `#startAction`.
- Segue il tema chiaro/scuro dell'app (attributo `data-theme` su `<html>`).
- Compare a ogni nuova apertura della scheda, ma non ricaricando la pagina (`sessionStorage` alla chiave `itaca-welcome-seen`).
- Nuova scelta in Impostazioni › Aspetto, «Pagina iniziale: Nessuna / Benvenuto», salvata in `localStorage` alla chiave
  `itaca-welcome` (`'off'` = nessuna; assente = Benvenuto).
- Movimento: segue la stessa regola del logo (interruttore «Logo animato»; senza una scelta si segue «riduci movimento»).
  Se il movimento è spento, la scena è ferma e si entra senza approdo.

**Note tecniche**
- Con una cartella ricordata, l'app chiede l'accesso al primo `pointerdown` ovunque (`reopenOnFirstInteraction`). Il blocco 2.3
  ferma quel `pointerdown` solo sui pulsanti «Apri cartella» / «Importa cartella» della pagina di benvenuto, per non aprire due finestre.
  Per questo il suo script deve stare dopo lo script principale dell'app (in fondo al documento), così si registra per primo.
- Il nuovo campo `name="welcomePage"` non è in `settingChoices`: il gestore delle impostazioni lo ignora, e lo gestisce il blocco 2.3.
- La pagina usa `z-index: 9000` e la classe `gone` (display none) quando è chiusa.

### 2.1 Stile della pagina di benvenuto: AGGIUNGERE
**Dove:** in fondo al primo blocco `<style>`, subito prima del suo `</style>` (dopo il blocco 1.2).

```css
/* [ESTETICA] inizio: pagina di benvenuto */
.wl {
  --wl-ink: #535540; --wl-hill: #8a8766; --wl-sage: #96a181; --wl-hull: #929c7d; --wl-deck: #9aa585; --wl-sand: #dbbd8a;
  --wl-sand2: #c9a46f; --wl-sun: #dcbf8c; --wl-shade: #a0976e; --wl-sea: #9ea68a; --wl-glint: #dcc49c; --wl-wind: #7d8566;
  --wl-sky1: #f6f1e6; --wl-sky2: #efe5d0; --wl-sky3: #e6dcc3; --wl-cloud: #fbf8f1; --wl-text: #3e4130; --wl-muted: #7a7b62;
  --wl-btn: #535540; --wl-btn-text: #f6f1e6; --wl-read: 'Sitka Text', Charter, 'Bitstream Charter', Cambria, Georgia, serif;
  position: fixed; inset: 0; z-index: 9000; overflow: hidden; cursor: pointer; user-select: none;
  display: grid; grid-template-rows: 1fr auto; justify-items: center; isolation: isolate;
  color: var(--wl-text); font-family: 'Segoe UI Variable Text', 'Segoe UI', system-ui, sans-serif;
}
html[data-theme='dark'] .wl {   /* «Notte di luna» */
  --wl-ink: #cfc6a6; --wl-hill: #9c9473; --wl-sage: #7e9068; --wl-hull: #5d6b52; --wl-deck: #6b7b5d; --wl-sand: #b8995f;
  --wl-sand2: #977a4a; --wl-sun: #ebdcae; --wl-shade: #7b7152; --wl-sea: #86a08a; --wl-glint: #8f805c; --wl-wind: #d8d1b6;
  --wl-sky1: #0d161d; --wl-sky2: #15242c; --wl-sky3: #1d2f33; --wl-cloud: #2a3b40; --wl-text: #eee6cc; --wl-muted: #a6a58c;
  --wl-btn: #cfc6a6; --wl-btn-text: #15242c;
}
.wl::before { content: ''; position: absolute; inset: 0; z-index: -2; background: linear-gradient(var(--wl-sky1) 0%, var(--wl-sky2) 58%, var(--wl-sky3) 100%); }
.wl-sky { z-index: -1; }
.wl-stage { position: relative; width: min(90vw, 780px, calc((100vh - 380px) * 1.5)); align-self: end; margin-bottom: -1vh; }
.wl-scene { display: block; width: 100%; height: auto; overflow: visible; }
.wl-copy { display: grid; justify-items: center; gap: 10px; padding: 0 16px max(4vh, 22px); text-align: center; cursor: default; }
.wl-title { margin: 0; font: 700 clamp(34px, 5.6vw, 68px)/1.05 var(--wl-read); letter-spacing: -.01em; }
.wl-title small { display: block; margin-top: 10px; font: 700 15px/1 'Segoe UI', sans-serif; letter-spacing: .3em; text-transform: uppercase; color: var(--wl-text); opacity: .85; }
.wl-tag b.wl-sail-call { display: inline-block; margin-top: 4px; font-style: normal; font-weight: 700; color: var(--wl-text); letter-spacing: .02em; }
.wl-tag { margin: 4px 0 10px; font: italic 400 clamp(16px, 2vw, 20px)/1.4 var(--wl-read); color: var(--wl-muted); }
.wl-actions { display: flex; flex-wrap: wrap; justify-content: center; gap: 10px; }
.wl-btn { display: grid; align-content: center; gap: 3px; min-width: 170px; padding: 12px 20px; border-radius: 12px; border: 2px solid var(--wl-btn);
  background: transparent; color: var(--wl-text); font: 650 15px/1.15 'Segoe UI', sans-serif; cursor: pointer; transition: transform .15s, background .15s; }
.wl-btn:hover { transform: translateY(-2px); background: color-mix(in srgb, var(--wl-btn) 12%, transparent); }
.wl-btn.primary { background: var(--wl-btn); color: var(--wl-btn-text); }
.wl-btn.primary:hover { background: color-mix(in srgb, var(--wl-btn) 88%, #000); }
.wl-btn small { font-weight: 450; font-size: 12px; opacity: .8; }
.wl-hint { margin-top: 6px; font-size: 12.5px; color: var(--wl-muted); }
.wl-hint kbd { font: inherit; padding: 1px 6px; border: 1px solid currentColor; border-radius: 5px; }

/* cielo: nuvole di giorno, stelle di notte (solo sopra l'orizzonte, cioè la base dell'isola: --wl-horizon lo calcola lo script) */
.wl-stars { position: absolute; left: 0; right: 0; top: 0; height: var(--wl-horizon, 45vh); overflow: hidden; }   /* stelle e nuvole stanno qui dentro */
.wl-stage::before {   /* il mare: parte esattamente dalla base dell'isola (y 238 del disegno) e si sposta insieme al disegno */
  content: ''; position: absolute; z-index: -1; left: -100vw; right: -100vw; top: calc((238 - 10) / 560 * 100%); height: 200vh; pointer-events: none;
  background: linear-gradient(color-mix(in srgb, var(--wl-sea) 12%, var(--wl-sky2)), color-mix(in srgb, var(--wl-sea) 30%, var(--wl-sky3)) 60vh); }
.wl-sky { position: absolute; inset: 0; pointer-events: none; }
.wl-cloud { position: absolute; height: 26px; border-radius: 26px; background: var(--wl-cloud); opacity: .9; animation: wl-cloud 70s linear infinite; }
.wl-cloud::before, .wl-cloud::after { content: ''; position: absolute; bottom: 8px; border-radius: 50%; background: inherit; }
.wl-cloud::before { left: 18%; width: 42%; aspect-ratio: 1; }
.wl-cloud::after { left: 48%; width: 30%; aspect-ratio: 1; }
.wl-cloud.c1 { top: 22%; width: 150px; animation-delay: -20s; }
.wl-cloud.c2 { top: 52%; width: 100px; animation-duration: 95s; animation-delay: -62s; opacity: .7; }
.wl-cloud.c3 { top: 8%; width: 120px; animation-duration: 85s; animation-delay: -5s; opacity: .6; }
html[data-theme='dark'] .wl-cloud { opacity: .35; }
.wl-star { position: absolute; width: 2px; height: 2px; border-radius: 50%; background: #f3ead0; opacity: 0; animation: wl-twinkle 3.5s ease-in-out infinite; }
html:not([data-theme='dark']) .wl-star { display: none; }
@keyframes wl-cloud { from { transform: translateX(110vw); } to { transform: translateX(-30vw); } }
@keyframes wl-twinkle { 0%, 100% { opacity: .15; } 50% { opacity: .9; } }


/* il logo (stessi disegni dell'intestazione) */
.wl-scene .wl-wind path { stroke: var(--wl-wind); stroke-dasharray: 110 400; stroke-dashoffset: 110; opacity: 0; }
.wl-scene .wl-boat { transform-box: view-box; transform-origin: 380px 450px; animation: wl-bob 4.2s ease-in-out infinite; }
.wl-scene .wl-wave { transform-box: view-box; animation: wl-flow 3.6s linear infinite; }
.wl-scene .wl-w2 { animation-duration: 4s; animation-delay: -2.5s; }
.wl-scene .wl-w3 { animation-duration: 4.4s; animation-delay: -.6s; }
.wl-scene .wl-w4 { animation-duration: 3.2s; animation-delay: -1.9s; }
.wl-scene .wl-w5 { animation-duration: 3.4s; animation-delay: -2.9s; }
.wl-scene .wl-sail { transform-box: view-box; transform-origin: 380px 80px; transition: transform .7s cubic-bezier(.3, 1.5, .5, 1) !important; }
.wl-scene .wl-sun, .wl-scene .wl-island, .wl-scene .wl-enter, .wl-scene .wl-sea, .wl-scene .wl-surge { transform-box: view-box; }
html[data-theme='dark'] .wl-scene .wl-sun { filter: drop-shadow(0 0 18px #ebdcae99); }
@keyframes wl-bob { 0%, 100% { transform: translateY(0) rotate(-1.8deg); } 50% { transform: translateY(16px) rotate(2deg); } }
@keyframes wl-flow { 0% { transform: translate(90px, 0); opacity: 0; } 15% { opacity: 1; } 50% { transform: translate(0, -6px); } 85% { opacity: 1; } 100% { transform: translate(-100px, 0); opacity: 0; } }

/* 2) SCENA VIVA: ogni tanto una folata da poppa gonfia la vela */
@keyframes wl-surge { 0% { transform: none; } 40% { transform: translateX(30px); } 100% { transform: none; } }
@keyframes wl-gust { 0% { stroke-dashoffset: 110; opacity: 0; } 25% { opacity: 1; } 100% { stroke-dashoffset: -330; opacity: 0; } }
.wl.gust .wl-wind path { animation: wl-gust .9s ease-in 2; }
.wl.gust .wl-wind path:nth-child(2) { animation-delay: .12s; }
.wl.gust .wl-wind path:nth-child(3) { animation-delay: .24s; }
.wl.gust .wl-sail { transform: translateX(8px) scale(1.17, 1.05); transition-delay: .35s !important; }
.wl.gust .wl-surge { animation: wl-surge 1.9s ease-in-out .45s; }

/* 3) USCITA: sole, isola e nave volano sul logo in alto a sinistra (posizione calcolata dallo script), il resto sfuma */
.wl.flying { pointer-events: none; }
.wl.flying .wl-stage { transform-origin: 0 0; transition: transform 1.15s cubic-bezier(.65, 0, .3, 1); }
.wl.flying .wl-copy { opacity: 0; transition: opacity .35s ease-in; }
.wl.flying::before, .wl.flying .wl-sky { opacity: 0; transition: opacity .7s ease-in .35s; }
.wl.flying .wl-stage::before { opacity: 0; transition: opacity .3s ease-in; }
.wl.flying.landed .wl-stage { opacity: 0; transition: opacity .25s; }
.wl.skip { pointer-events: none; animation: wl-out .35s ease-in both; }
@keyframes wl-out { to { opacity: 0; } }
.wl.gone { display: none; }
.wl:focus { outline: none; }
.wl.still, .wl.still * { animation: none !important; transition: none !important; }   /* movimento spento: scena ferma */
.wl-btn[hidden] { display: none; }
@media (max-width: 600px) { .wl-btn { min-width: 0; flex: 1 1 100%; } .wl-cloud.c1 { width: 100px; } }
/* [ESTETICA] fine: pagina di benvenuto */
```

### 2.2 Impostazioni › Aspetto: AGGIUNGERE
**Dove:** subito dopo il blocco 1.4 (dopo la riga `<!-- [ESTETICA] fine: interruttore marchio animato -->`), nella stessa `set-card`.

```html
          <!-- [ESTETICA] inizio: scelta della pagina iniziale -->
          <div class="set-row">
            <span class="set-label" id="welcomePageLabel"><b>Pagina iniziale</b><small>Cosa compare quando apri Itaca (si vede alla prossima apertura della scheda)</small></span>
            <div class="segmented" role="radiogroup" aria-labelledby="welcomePageLabel"><label><input type="radio" name="welcomePage" value="off"><span>Nessuna</span></label><label><input type="radio" name="welcomePage" value="2d"><span>Benvenuto</span></label></div>
          </div>
          <!-- [ESTETICA] fine: scelta della pagina iniziale -->
```

### 2.3 Pagina di benvenuto (struttura e comportamento): AGGIUNGERE
**Dove:** in fondo al documento, subito prima dell'ultimo `</body>` reale, dopo il blocco 1.6.

```html
<!-- [ESTETICA] inizio: pagina di benvenuto -->
<div class="wl gone" id="welcome" tabindex="-1" role="dialog" aria-label="Benvenuto in Itaca">
  <div class="wl-sky" aria-hidden="true">
    <div class="wl-stars"><i class="wl-cloud c1"></i><i class="wl-cloud c2"></i><i class="wl-cloud c3"></i></div>
  </div>
  <div class="wl-stage"><svg class="wl-scene" viewBox="0 10 860 560" aria-hidden="true" stroke-linecap="round" stroke-linejoin="round"><circle cx="585" cy="62" r="52" style="fill:var(--wl-sun)" class="wl-sun" /><g class="wl-island"><path d="M137,238 L260,191 C275,186 290,188 300,186 L500,121 C506,118 512,118 516,122 L578,160 L650,118 C656,115 662,115 668,118 L735,163 C745,168 760,163 772,168 C780,171 785,176 790,180 L842,236 Z" style="fill:var(--wl-sand)" /><path d="M655,118 L735,163 C745,168 760,163 772,168 C780,171 785,176 790,180 L842,236 L700,236 L640,188 C650,170 655,145 655,118 Z" style="fill:var(--wl-shade)" /><path d="M520,236 L585,196 L605,201 L640,188 L700,236" fill="none" stroke-width="9" style="stroke:var(--wl-hill)" /><path d="M137,238 L260,191 C275,186 290,188 300,186 L500,121 C506,118 512,118 516,122 L578,160 L650,118 C656,115 662,115 668,118 L735,163 C745,168 760,163 772,168 C780,171 785,176 790,180 L842,236 Z" fill="none" stroke-width="11" style="stroke:var(--wl-hill)" /><path d="M505,263 H592 M535,288 H597 M662,262 H735" stroke-width="11" style="stroke:var(--wl-glint)" /></g><g class="wl-wind" fill="none" stroke-width="13"><path d="M-20,110 H285" /><path d="M-30,160 H300" /><path d="M-10,210 H290" /></g><g class="wl-enter"><g class="wl-surge"><g class="wl-boat"><g class="wl-sail"><path d="M283,105 L470,57 C500,120 505,230 458,303 C445,295 420,287 380,288 C345,289 310,300 282,315 C305,260 312,170 283,105 Z" style="fill:var(--wl-sage)" /><path d="M283,105 C305,160 312,250 282,315" fill="none" stroke-width="11" style="stroke:var(--wl-ink)" /><path d="M470,57 C500,120 505,230 458,303 L440,352" fill="none" stroke-width="11" style="stroke:var(--wl-ink)" /><path d="M208,354 C260,320 320,290 380,288 C420,287 445,295 458,303" fill="none" stroke-width="11" style="stroke:var(--wl-ink)" /></g><path d="M380,22 V357" stroke-width="11" style="stroke:var(--wl-ink)" /><path d="M255,106 L485,45" stroke-width="11" style="stroke:var(--wl-ink)" /><path d="M30,262 C28,345 60,405 150,455 C260,458 360,470 430,466 C470,463 470,448 500,450 C530,452 540,468 565,466 C595,463 600,446 630,444 C655,443 672,446 688,446 C662,432 648,415 648,385 L648,375 L190,375 C100,372 46,330 44,262 Z" style="fill:var(--wl-hull)" /><path d="M236,398 H640 L652,420 H214 Z" style="fill:var(--wl-deck)" /><path d="M201,433 H660 L686,446 C600,446 560,470 520,462 C480,455 470,462 430,466 L172,462 Z" style="fill:var(--wl-deck)" /><path d="M196,427 H655" stroke-width="12" style="stroke:var(--wl-ink)" /><path d="M236,398 L169,465 M303,398 L236,465 M370,398 L303,465 M438,398 L371,465 M506,398 L439,465" stroke-width="11" style="stroke:var(--wl-ink)" /><path d="M30,262 C28,345 60,405 150,455 C260,458 360,470 430,466 C470,463 470,448 500,450 C530,452 540,468 565,466 C595,463 600,446 630,444 C655,443 672,446 688,446" fill="none" stroke-width="12" style="stroke:var(--wl-ink)" /><path d="M647,380 C650,425 690,445 745,462" fill="none" stroke-width="12" style="stroke:var(--wl-ink)" /><path d="M90,249 C94,258 108,258 114,250 C116,246 116,242 116,238 C117,220 104,206 82,206 C55,206 42,230 44,262 C46,330 100,372 190,375 L500,375" fill="none" stroke-width="40" stroke-linecap="round" style="stroke:var(--wl-ink)" /><path d="M104,256 C109,254 113,250 115,246 C116,243 116,240 116,238 C117,220 104,206 82,206 C55,206 42,230 44,262 C46,330 100,372 190,375 L500,375" fill="none" stroke-width="16" stroke-linecap="round" style="stroke:var(--wl-sand)" /><path d="M480,390 H645" stroke-width="14" stroke-linecap="butt" style="stroke:var(--wl-ink)" /><path d="M626,272 H641 V383 H480 V367 C595,362 624,330 626,272 Z" style="fill:var(--wl-sand)" /><path d="M636,282 C630,340 600,372 540,383 L637,383 Z" style="fill:var(--wl-sand2)" /><path d="M632,276 V380" stroke-width="9" stroke-linecap="butt" style="stroke:var(--wl-sand)" /><path d="M606,262 H653 V385 H641 V272 H626 C624,330 595,362 480,367 L480,355 C575,350 606,330 606,262 Z" style="fill:var(--wl-ink)" /><g style="fill:var(--wl-ink)"><circle cx="237" cy="382" r="12" /><circle cx="305" cy="382" r="12" /><circle cx="372" cy="382" r="12" /><circle cx="440" cy="382" r="12" /><circle cx="505" cy="382" r="12" /></g><g stroke-width="5" style="fill:var(--wl-ink);stroke:var(--wl-ink)"><path d="M234,464 L242,470 L222,521 L184,521 L214,478 Z" /><path d="M301,464 L309,470 L289,521 L251,521 L281,478 Z" /><path d="M369,464 L377,470 L357,521 L319,521 L349,478 Z" /><path d="M437,464 L445,470 L425,521 L387,521 L417,478 Z" /></g><path d="M215,307 L146,440" stroke-width="11" style="stroke:var(--wl-ink)" /><path d="M124,443 L144,437 L148,447 L121,519 L76,519 Z" stroke-width="9" style="fill:var(--wl-sand);stroke:var(--wl-ink)" /></g></g></g><g fill="none" stroke-width="11" style="stroke:var(--wl-sea)" class="wl-sea"><path d="M17,456 C35,462 55,463 75,458 C95,453 105,448 118,446" class="wl-wave wl-w1" /><path d="M447,513 C480,500 520,497 550,502 C580,507 590,516 615,514 C645,511 665,500 682,493" class="wl-wave wl-w2" /><path d="M257,552 C290,535 340,530 380,538 C410,545 425,556 450,554 C490,550 520,535 575,537" class="wl-wave wl-w3" /><path d="M690,505 C712,496 740,496 762,503" class="wl-wave wl-w4" /><path d="M40,515 C62,507 92,507 114,514" class="wl-wave wl-w5" /></g></svg></div>
  <div class="wl-copy">
    <h1 class="wl-title">Benvenuto su Itaca<small>Lite version</small></h1>
    <p class="wl-tag">Il dono della conoscenza si ottiene dopo un lungo viaggio.<br><b class="wl-sail-call">Salpiamo!</b></p>
    <div class="wl-actions">
      <button class="wl-btn primary" data-go="resume" hidden>Riprendi il viaggio<small></small></button>
      <button class="wl-btn" data-go="open">Apri cartella</button>
      <button class="wl-btn" data-go="import">Importa cartella</button>
    </div>
    <div class="wl-hint">Clicca ovunque per salpare · <kbd>Esc</kbd> per entrare subito</div>
  </div>
</div>
<script>
(() => {
  // Pagina di benvenuto. Blocco autonomo: legge solo elementi esistenti dell'app (#openDir, #importFolder,
  // #startAction, #rootName, #workStart) e ne preme i pulsanti; non cambia nessuna funzione.
  const KEY = 'itaca-welcome';            // 'off' = nessuna pagina iniziale; assente = Benvenuto
  const SEEN = 'itaca-welcome-seen';      // sessionStorage: resta col ricaricare, sparisce chiudendo la scheda
  const wl = document.getElementById('welcome');
  if (!wl) return;
  const $id = id => document.getElementById(id);
  const read = (store, key) => { try { return store.getItem(key); } catch { return null; } };
  const write = (store, key, value) => { try { value == null ? store.removeItem(key) : store.setItem(key, value); } catch {} };

  // Impostazioni › Aspetto › Pagina iniziale
  let mode = read(localStorage, KEY) || '2d';
  document.querySelectorAll('input[name="welcomePage"]').forEach(radio => {
    radio.checked = radio.value === mode;
    radio.addEventListener('change', () => {
      if (!radio.checked) return;
      mode = radio.value;
      write(localStorage, KEY, mode === '2d' ? null : mode);
    });
  });
  if (mode === 'off' || read(sessionStorage, SEEN) === '1') return;
  write(sessionStorage, SEEN, '1');

  // Movimento: stessa regola del logo (interruttore «Logo animato»; senza scelta si segue «riduci movimento»).
  const pref = read(localStorage, 'itaca-logo-motion');
  const moving = pref ? pref === 'on' : !(window.matchMedia && matchMedia('(prefers-reduced-motion: reduce)').matches);

  // orizzonte = base dell'isola nel disegno (y 238 su viewBox 10..570): stelle e nuvole restano sopra
  const scene = wl.querySelector('.wl-scene');
  const horizon = () => { const r = scene.getBoundingClientRect(); wl.style.setProperty('--wl-horizon', (r.top + r.height * (238 - 10) / 560) + 'px'); };
  const sky = wl.querySelector('.wl-stars');
  for (let i = 0; i < 70; i++) {
    const s = document.createElement('i');
    s.className = 'wl-star';
    s.style.left = (Math.random() * 100) + '%';
    s.style.top = (Math.random() * 96) + '%';
    s.style.animationDelay = (-Math.random() * 3.5) + 's';
    if (Math.random() < .2) s.style.width = s.style.height = '3px';
    sky.appendChild(s);
  }

  // «Riprendi il viaggio» solo se l'app ricorda una cartella (ne mostra il nome in #rootName)
  const resume = wl.querySelector('[data-go="resume"]');
  const openBtn = wl.querySelector('[data-go="open"]');
  // c'è una cartella ricordata quando l'app propone «Consenti accesso» o «Mostra documenti», o ha già aperto qualcosa
  const syncResume = () => {
    const name = ($id('rootName')?.textContent || '').trim();
    const start = $id('startAction'), area = $id('workStart');
    const known = !!name && (!!area?.hidden || /consenti|mostra documenti/i.test(start?.textContent || ''));
    resume.hidden = !known;
    resume.querySelector('small').textContent = 'Ultima rotta: ' + name;
    openBtn.classList.toggle('primary', !known);
  };
  syncResume();
  const watch = new MutationObserver(syncResume);
  ['rootName', 'startAction'].forEach(id => $id(id) && watch.observe($id(id), { childList: true, characterData: true, subtree: true }));
  if ($id('workStart')) watch.observe($id('workStart'), { attributes: true, attributeFilter: ['hidden'] });

  // Mostra
  wl.className = moving ? 'wl' : 'wl still';   // la scena è già completa, subito
  horizon();
  addEventListener('resize', horizon);
  // le scritte possono cambiare altezza dopo l'apertura (caratteri, dimensione del testo dell'app):
  // il disegno si sposta, quindi la linea del mare va ricalcolata ogni volta
  const follow = window.ResizeObserver ? new ResizeObserver(() => horizon()) : null;
  if (follow) [wl, wl.querySelector('.wl-copy'), wl.querySelector('.wl-stage')].forEach(el => el && follow.observe(el));
  if (document.fonts?.ready) document.fonts.ready.then(horizon);
  setTimeout(horizon, 300); setTimeout(horizon, 1200);
  wl.focus({ preventScroll: true });
  let gustTimer = 0, introTimer = 0;   // introTimer: prima folata
  const gust = () => {
    wl.classList.remove('gust'); void wl.offsetWidth; wl.classList.add('gust');
    setTimeout(() => wl.classList.remove('gust'), 2500);
  };
  if (moving) introTimer = setTimeout(() => { gust(); gustTimer = setInterval(gust, 7000); }, 2500);

  // Uscita: sole, isola e nave volano sul logo dell'intestazione (in alto a sinistra) e la pagina sfuma.
  // Esc, movimento spento o logo non visibile (barra laterale chiusa): si entra subito.
  const stage = wl.querySelector('.wl-stage');
  const leave = fast => {
    if (/(flying|skip|gone)/.test(wl.className)) return;
    clearInterval(gustTimer); clearTimeout(introTimer);
    wl.classList.remove('gust');
    const logo = document.querySelector('.brand .itaca-logo');
    const to = logo && logo.getBoundingClientRect(), from = scene.getBoundingClientRect();
    if (fast || !moving || !to || to.width < 8) {
      wl.classList.add('skip');
      setTimeout(() => { wl.classList.add('gone'); removeEventListener('resize', horizon); follow?.disconnect(); }, 400);
      return;
    }
    const k = to.width / from.width;   // stessi disegni e stesse proporzioni: basta scalare e spostare
    wl.classList.add('flying');
    stage.style.transform = `translate(${to.left - from.left}px, ${to.top - from.top}px) scale(${k})`;
    setTimeout(() => wl.classList.add('landed'), 1150);
    setTimeout(() => { wl.classList.add('gone'); stage.style.transform = ''; removeEventListener('resize', horizon); follow?.disconnect(); }, 1450);
  };
  // I pulsanti premono subito quelli dell'app (il browser apre le cartelle solo durante il clic), poi si approda.
  const actions = {
    open: () => $id('openDir')?.click(),
    import: () => $id('importFolder')?.click(),
    resume: () => { const a = $id('startAction'); if (a && !$id('workStart')?.hidden && /consenti/i.test(a.textContent)) a.click(); },
  };
  wl.addEventListener('click', event => {
    const btn = event.target.closest('[data-go]');
    if (btn) { actions[btn.dataset.go]?.(); leave(false); return; }   // il pulsante apre subito la finestra dell'app, intanto il disegno vola
    if (!event.target.closest('.wl-copy')) leave(false);
  });
  addEventListener('keydown', event => { if (event.key === 'Escape' && !wl.classList.contains('gone')) leave(true); });
  // Con una cartella ricordata, l'app chiede l'accesso al primo clic ovunque: non deve farlo
  // quando il clic è su «Apri cartella» / «Importa cartella» della pagina di benvenuto.
  addEventListener('pointerdown', event => {
    if (event.target.closest?.('#welcome [data-go="open"], #welcome [data-go="import"]')) event.stopImmediatePropagation();
  }, true);
})();
</script>
<!-- [ESTETICA] fine: pagina di benvenuto -->
```

### Verifica del lotto 2
1. Si apre l'app in una scheda nuova: compare subito «Benvenuto su Itaca», già completa.
2. Si ricarica la pagina (F5): la pagina di benvenuto non ricompare. Si chiude la scheda e la si riapre: ricompare.
3. Un clic sullo sfondo: il disegno vola sul logo in alto a sinistra e si vede l'app. Esc: si entra subito.
4. «Apri cartella» e «Importa cartella» aprono la stessa finestra dei pulsanti della barra laterale (una sola finestra).
5. Con una cartella già usata in passato compare «Riprendi il viaggio» con il suo nome.
6. Impostazioni › Aspetto › Pagina iniziale: con «Nessuna» non compare più nemmeno in una scheda nuova.
7. In tema scuro la scena è notturna (luna e stelle). La console non mostra errori nuovi.
