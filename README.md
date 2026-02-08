# Telegram Custom Bot

[![hacs_badge](https://img.shields.io/badge/HACS-Custom-orange.svg)](https://github.com/hacs/integration)

Una versione personalizzata dell'integrazione standard **Telegram Bot** di Home Assistant, corretta per funzionare con **Home Assistant 2026.2** (Core) e successivi, che utilizzano **Python 3.13**.

E' consigliato usare questo componente insieme a Telegram Custom Notify: https://github.com/SalvatoreITA/Telegram-Custom

## ✅ Descrizione:
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
