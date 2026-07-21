# StageDesk Share

Pagina web responsive per la consultazione di un copione condiviso da StageDesk Pro.

## Funzionalità

- autenticazione con gli stessi provider configurati per StageDesk Pro;
- accesso a una condivisione tramite URL e PIN a cinque cifre;
- selezione di uno o più personaggi;
- modalità per mostrare solo i personaggi selezionati oppure nascondere le loro battute;
- ricerca unificata di battute e personaggi;
- stati di studio per ogni battuta;
- bookmark persistenti, navigazione tra bookmark e ritorno all'inizio del copione;
- caricamento progressivo dei contenuti per copioni lunghi;
- layout responsive per desktop e dispositivi mobili.
- recupero password via e-mail con impostazione guidata della nuova password;
- registrazione e-mail con nome, cognome, telefono, profili multipli, privacy, termini d'uso e consenso informativo;
- profili operativi **Attore/Attrice** e **Autore/Autrice** oltre a Regista e Altro;
- completamento obbligatorio del profilo dopo l'autenticazione OAuth, prima dell'inserimento del PIN;
- recupero password gestito da Supabase Auth: un account nato con Google, GitHub o Azure può aggiungere una credenziale email/password senza creare un secondo account.

## Struttura

- `share/`: sorgente della pagina condivisa;
- `share-assets/`: asset pubblicati dalla pagina;
- `functions/share-config.js`: Function Cloudflare per il recupero della configurazione della condivisione;
- `assets/stagedesk-pro-icon.png`: icona usata nella pagina;
- `_headers`, `_redirects`: configurazione Cloudflare Pages.

## Deploy Cloudflare Pages

```bash
npx wrangler pages deploy . --project-name stagedesk-pro-share
```

La Function richiede i secret Cloudflare Pages `SUPABASE_URL` e
`SUPABASE_PUBLISHABLE_KEY`. Le credenziali non sono incluse nel repository.

Il recupero password usa come redirect la stessa pagina della condivisione:
`https://stagedesk-pro.aigconsulting.it/share/*`. Inserisci questo pattern, oppure gli URL `/share/[UID]` necessari, nelle URL di reindirizzamento consentite in Supabase. Il callback dei provider resta `https://insoqzhjmrbrgfrsmlnj.supabase.co/auth/v1/callback`.

Un account creato tramite provider esterno può completare il recupero password via e-mail e continuare a utilizzare lo stesso account per accedere alla condivisione.

## Relazione con StageDesk Pro

Il copione viene pubblicato da [StageDesk Pro](https://github.com/igelsomino/stagedesk-pro)
e reso disponibile tramite il sito pubblico [stagedesk-pro.aigconsulting.it](https://stagedesk-pro.aigconsulting.it/).
