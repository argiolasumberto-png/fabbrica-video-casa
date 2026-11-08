# Fabbrica video casa - come si usa

Una rete di 5 agenti (Claude Code) che prepara puntate TikTok "Smontato in 60 secondi" su ristrutturazioni e problemi di casa:

1. **cacciatore-temi** - trova i problemi di casa che la gente vive e cerca
2. **sceneggiatore** - scrive copione e sottotitoli
3. **regista-prompt** - scrive i prompt video per ChatGPT, divisi in parti
4. **verificatore-tecnico** - controlla che sia tutto vero e sicuro, e rimanda indietro se sbagliato
5. **editor-tiktok** - descrizione, hashtag, gancio

Il capo è Claude Code stesso, seguendo CLAUDE.md. Le puntate finiscono nella cartella `puntate/`. Poi le porti a Claude in chat per l'ultimo controllo prima di ChatGPT.

## Preparazione (una volta sola)

1. Su GitHub crea un repository **pubblico** chiamato `fabbrica-video-casa` (pubblico serve perché Claude in chat lo possa leggere senza password; dentro ci sono solo copioni e prompt).
2. Carica tutti i file di questa cartella: "Add file" → "Upload files", trascina dentro anche le cartelle `.claude` e `.github` → "Commit changes".
3. Sul PC, nel terminale dove usi Claude Code, scrivi `claude setup-token` e copia il codice che ti dà. Serve un abbonamento Claude Pro o Max: gli agenti usano i limiti del tuo abbonamento.
4. Nel repository: Settings → Secrets and variables → Actions → New repository secret. Nome: `CLAUDE_CODE_OAUTH_TOKEN`. Valore: il codice copiato. Salva. Non incollarlo mai in chat o in altri posti.

## Come lanciarla

**Da GitHub (anche da telefono):** scheda Actions → "Fabbrica video casa" → "Run workflow" → scrivi il tema (o lascia vuoto) e quante puntate → "Run workflow". In 10-30 minuti trovi la puntata in `puntate/`.

**In automatico:** ogni lunedì mattina parte da sola e prepara 3 puntate.

**Dal PC con Claude Code:** apri la cartella del repository, avvia `claude` e scrivi: `avvia la fabbrica, tema: sciacquone che perde, 1 puntata`.

## Ultimo controllo con Claude in chat

Scrivi in chat: **"verifica le puntate nuove"** con il link del repository. Claude le legge, ricontrolla tutto e ti restituisce i prompt pronti da incollare in ChatGPT, uno per parte.

## Se qualcosa non va
Se un'esecuzione su Actions diventa rossa, apri l'esecuzione, copia le ultime righe dell'errore e mandale a Claude in chat.
