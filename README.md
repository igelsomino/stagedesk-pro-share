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

## Relazione con StageDesk Pro

Il copione viene pubblicato da [StageDesk Pro](https://github.com/igelsomino/stagedesk-pro)
e reso disponibile tramite il sito pubblico [stagedesk-pro.aigconsulting.it](https://stagedesk-pro.aigconsulting.it/).
