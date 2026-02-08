# Telegram Custom Bot

[![it](https://img.shields.io/badge/lang-it-green.svg)](https://github.com/SalvatoreITA/telegram-custom-bot/blob/main/README_it.md)
[![en](https://img.shields.io/badge/lang-en-red.svg)](https://github.com/SalvatoreITA/telegram-custom-bot/blob/main/README.md)

[![hacs_badge](https://img.shields.io/badge/HACS-Custom-41BDF5.svg)](https://github.com/hacs/integration)
[![version](https://img.shields.io/badge/version-1.0.2-blue.svg)]()
[![maintainer](https://img.shields.io/badge/maintainer-Salvatore_Lentini_--_DomHouse.it-green.svg)](https://www.domhouse.it)

<div align="center">
  <img src="https://github.com/SalvatoreITA/Telegram-Custom/blob/main/icon.png?raw=true" alt="Logo" width="150">
</div>

Una versione personalizzata dell'integrazione standard **Telegram Bot** di Home Assistant, corretta per funzionare con **Home Assistant 2026.2** (Core) e successivi, che utilizzano **Python 3.13**.

E' consigliato usare questo componente insieme a **Telegram Custom Notify**: https://github.com/SalvatoreITA/Telegram-Custom

## 🛡️ Perché questa versione è "Future-Proof"?

A differenza dell'integrazione nativa, questo Custom Component è stato progettato per essere **totalmente indipendente** dal Core di Home Assistant.

1.  **Gestione Connessione Autonoma**: Questo componente si occupa interamente della logica di connessione ai server di Telegram (Polling). Non si appoggia a librerie condivise che potrebbero essere rimosse o aggiornate in modo incompatibile da Home Assistant.
2.  **Librerie Incluse (Vendoring)**: Tutte le dipendenze necessarie (come `python-telegram-bot`) sono fisicamente incluse all'interno della cartella del componente.
    * *Integrazione Standard:* Usa le librerie di sistema. Se Home Assistant aggiorna Python e rompe la compatibilità (come successo con la 2026.2), l'integrazione smette di funzionare.
    * *Questo Custom Component:* Usa le **sue** librerie interne. Anche se Home Assistant cambia radicalmente il suo ambiente Python in futuro, questo componente continuerà a funzionare perché viaggia con il suo "kit di sopravvivenza" personale, isolato dai cambiamenti del sistema operativo.

In sintesi: **Installalo una volta e dimenticatene.** Finché le API di Telegram non cambieranno, questo componente continuerà a funzionare indipendentemente dagli aggiornamenti di Home Assistant.

## 💾 Installazione

### Opzione 1: Tramite HACS (Consigliato)
1.  Apri **HACS** > **Frontend**.
2.  Clicca sul menu (3 puntini in alto a destra) > **Repository personalizzati**.
3.  Aggiungi l'URL: `https://github.com/SalvatoreITA/telegram-custom-bot`
4.  Categoria: **Lovelace**.
5.  Clicca su **Aggiungi** e poi su **Scarica**.
6.  Ricarica il browser.

### Opzione 2: Manuale
1.  Scarica questo repository.
2.  Copia la cartella `custom_components/telegram_bot` dentro la cartella `/config/custom_components/` del tuo Home Assistant.
3.  Riavvia Home Assistant.

## ⚙️ Configurazione

### 1. Primo Avvio (Migrazione)
Se provieni da una vecchia installazione, mantieni inizialmente la tua configurazione nel file `configuration.yaml` per il primo riavvio.

```yaml
telegram_bot:
  - platform: polling
    api_key: "LA_TUA_CHIAVE_API_TELEGRAM"
    allowed_chat_ids:
      - 123456789
```
### 2. Pulizia
Dopo il riavvio, Home Assistant importerà automaticamente queste impostazioni nell'interfaccia grafica (Impostazioni > Dispositivi e Servizi). Se ricevi una notifica che ti chiede di rimuovere la configurazione Telegram dal file YAML, puoi cancellare (o commentare) tranquillamente quelle righe nel configuration.yaml. Il bot è ora configurato e gestito tramite l'interfaccia UI.

## ⚠️ Disclaimer (Esclusione di Responsabilità)
Questo progetto è un'integrazione indipendente e non ufficiale. Non è affiliato, associato, autorizzato, sponsorizzato o in alcun modo ufficialmente connesso con **Telegram** o una qualsiasi delle sue sussidiarie o affiliate.

Il sito ufficiale di Telegram è reperibile all'indirizzo [https://telegram.org](https://telegram.org).

## ❤️ Crediti
Sviluppato da [Salvatore Lentini - DomHouse.it](https://www.domhouse.it)
