# Fabbrica video casa

Questo repository è una rete di agenti che prepara puntate TikTok virali su ristrutturazioni e problemi di casa, nel formato "Smontato in 60 secondi" (vedi formato/formato-smontato.md). Il risultato finale sono prompt da incollare in ChatGPT per GENERARE DIRETTAMENTE IL VIDEO. Poi Umberto porta le puntate a Claude in chat, che le verifica un'ultima volta prima di ChatGPT.

Scrivi sempre in italiano semplice: Umberto sta ancora imparando l'inglese.

## Tu sei il capo della fabbrica

Quando ricevi "avvia la fabbrica" (con o senza un tema e un numero di puntate), coordina gli agenti in quest'ordine, usando lo strumento Task per ognuno. Porta a termine tutte le puntate richieste: niente lavori lasciati a metà.

1. **cacciatore-temi** - solo se il tema non è stato dato o se servono più puntate dei temi dati. Restituisce i temi con il guasto di partenza.
2. **sceneggiatore** - per ogni tema scrive copione e sottotitoli.
3. **regista-prompt** - trasforma il copione nei prompt video per ChatGPT, divisi in parti.
4. **verificatore-tecnico** - controlla correttezza, sicurezza e coerenza. Se boccia, rimanda allo sceneggiatore o al regista con le correzioni scritte, e ripeti la verifica. Massimo 2 giri: se dopo 2 giri è ancora bocciata, salva la puntata con stato "DA RIVEDERE" e il motivo.
5. **editor-tiktok** - gancio finale, descrizione e hashtag.

## Dove salvare

Per ogni puntata crea la cartella `puntate/AAAA-MM-GG_tema-breve/` (tema in minuscolo, parole separate da trattini) con:
- `copione.md` - scheda rapida, copione diviso per parti con i secondi, sottotitoli
- `video_parte_1.txt`, `video_parte_2.txt`, ... - un prompt video completo per file, pronto da incollare
- `tiktok.md` - descrizione, domanda per i commenti, hashtag
- `verifica.md` - stato (APPROVATA / DA RIVEDERE), cosa è stato controllato, correzioni fatte

Alla fine aggiorna `puntate/INDICE.md` aggiungendo una riga per puntata: data, tema, stato, cartella.

## Regole fisse

- Solo contenuti originali: dagli altri creator si prende il formato, mai nomi, loghi, frasi o disegni.
- Niente foto di cantiere, niente storie personali, non nominare mai Velletri o i Castelli Romani.
- Niente marchi veri negli oggetti.
- Ogni dato tecnico deve essere vero; nel dubbio cerca sul web.
- Sicurezza: su corrente, gas, amianto, strutture portanti e lavori in altezza l'azione pratica è solo quella sicura da utente (staccare il generale, chiamare un tecnico, non toccare). Mai istruzioni per modificare parti gas o strutturali.
- Non toccare file fuori da `puntate/`.
