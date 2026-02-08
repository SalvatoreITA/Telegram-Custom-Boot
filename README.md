# Telegram Custom Bot (Fix per Home Assistant 2026.2+)

[![hacs_badge](https://img.shields.io/badge/HACS-Custom-orange.svg)](https://github.com/hacs/integration)

Una versione personalizzata dell'integrazione standard **Telegram Bot** di Home Assistant, corretta per funzionare con **Home Assistant 2026.2** (Core) e successivi, che utilizzano **Python 3.13**.

## 🔴 Il Problema
Con l'aggiornamento a Home Assistant 2026.2 (basato su Python 3.13), la dipendenza interna `apscheduler` (usata dalla libreria `python-telegram-bot` per il polling) ha iniziato a rifiutare i fusi orari di sistema, generando il seguente errore durante l'avvio:

> `TypeError: Only timezones from the pytz library are supported`

Questo errore causava il fallimento completo dell'avvio del bot Telegram in modalità Polling.

## ✅ La Soluzione
Questo componente personalizzato include:
1.  **Vendoring**: La libreria `python-telegram-bot` è inclusa direttamente all'interno del componente (versione compatibile).
2.  **Patch su `_jobqueue.py`**: La logica interna dello scheduler è stata modificata per forzare l'uso del fuso orario `pytz.utc` ovunque, aggirando l'incompatibilità tra la vecchia versione di `apscheduler` e il nuovo ambiente Python 3.13.

## 💾 Installazione

### Opzione 1: HACS (Consigliata)
1.  Vai su HACS > Integrazioni.
2.  Clicca sui 3 puntini in alto a destra -> **Repository personalizzati**.
3.  Incolla l'URL di questo repository GitHub.
4.  Categoria: **Integrazione**.
5.  Clicca su **Aggiungi** e poi installa "Telegram Bot (Fixed)".
6.  Riavvia Home Assistant.

### Opzione 2: Manuale
1.  Scarica questo repository.
2.  Copia la cartella `custom_components/telegram_bot` dentro la cartella `/config/custom_components/` del tuo Home Assistant.
3.  Riavvia Home Assistant.

## ⚙️ Configurazione
Usa la tua configurazione Telegram esistente nel file `configuration.yaml`. **Non è necessario alcun cambiamento** se provieni dall'integrazione ufficiale.

```yaml
telegram_bot:
  - platform: polling
    api_key: "LA_TUA_CHIAVE_API_TELEGRAM"
    allowed_chat_ids:
      - 123456789
