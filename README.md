# Telegram Custom Bot

[![it](https://img.shields.io/badge/lang-it-green.svg)](https://github.com/SalvatoreITA/telegram-custom-bot/blob/main/README_it.md)
[![en](https://img.shields.io/badge/lang-en-red.svg)](https://github.com/SalvatoreITA/telegram-custom-bot/blob/main/README.md)

[![hacs_badge](https://img.shields.io/badge/HACS-Custom-41BDF5.svg)](https://github.com/hacs/integration)
[![version](https://img.shields.io/badge/version-1.0.2-blue.svg)]()
[![maintainer](https://img.shields.io/badge/maintainer-Salvatore_Lentini_--_DomHouse.it-green.svg)](https://www.domhouse.it)

<div align="center">
  <img src="https://github.com/SalvatoreITA/Telegram-Custom-Bot/blob/main/icon.png?raw=true" alt="Logo" width="150">
</div>

A customized version of the standard Home Assistant **Telegram Bot** integration, patched to work with **Home Assistant 2026.2** (Core) and later, which utilize **Python 3.13**.

It is recommended to use this component together with **Telegram Custom Notify**: https://github.com/SalvatoreITA/Telegram-Custom

## 🛡️ Why is this version "Future-Proof"?

Unlike the native integration, this Custom Component has been designed to be **totally independent** from the Home Assistant Core.

1.  **Autonomous Connection Management**: This component handles the Telegram server connection logic (Polling) entirely. It does not rely on shared libraries that could be removed or updated in incompatible ways by Home Assistant.
2.  **Included Libraries (Vendoring)**: All necessary dependencies (such as `python-telegram-bot`) are physically included inside the component folder.
    * *Standard Integration:* Uses system libraries. If Home Assistant updates Python and breaks compatibility (as happened with 2026.2), the integration stops working.
    * *This Custom Component:* Uses its **own** internal libraries. Even if Home Assistant radically changes its Python environment in the future, this component will continue to work because it travels with its personal "survival kit," isolated from operating system changes.

In short: **Install it once and forget about it.** As long as the Telegram APIs do not change, this component will continue to work regardless of Home Assistant updates.

## 💾 Installation

### Method 1: Via HACS (Recommended)
1.  Open **HACS** in your Home Assistant.
2.  Go to **Integrations** > **Menu (3 dots top right)** > **Custom repositories**.
3.  Paste the URL of this GitHub repository: 
    https://github.com/SalvatoreITA/telegram-custom-bot
4.  In the category, select **Integration**.
5.  Click **Add** and then **Download**.
6.  **Restart Home Assistant**.

### Option 2: Manual
1.  Download this repository.
2.  Copy the `telegram_bot` folder into the `/config/custom_components/` folder of your Home Assistant.
3.  Restart Home Assistant.

## ⚙️ Configuration

### 1. First Run (Migration)
If you are coming from an old installation, initially keep your configuration in the `configuration.yaml` file for the first restart.

```yaml
telegram_bot:
  - platform: polling
    api_key: "YOUR_TELEGRAM_API_KEY"
    allowed_chat_ids:
      - 123456789
```
### 2. Cleanup
After rebooting, Home Assistant will automatically import these settings into the GUI (Settings > Devices & Services). If you receive a notification asking you to remove the Telegram configuration from the YAML file, you can safely delete (or comment out) those lines in configuration.yaml. The bot is now configured and managed via the UI.

## ⚠️ Disclaimer
This project is an independent and unofficial integration. It is not affiliated, associated, authorized, sponsored, or in any way officially connected with **Telegram** or any of its subsidiaries or affiliates.

The official Telegram website can be found at: [https://telegram.org](https://telegram.org).

## ☕ Support the Project
Every little bit of support makes a huge difference: it keeps the enthusiasm alive and motivates me to create and share new solutions for the community. Thank you from the bottom of my heart! 🚀

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/salvatore_dh)


## ❤️ Credits
Developed by: [Salvatore Lentini - DomHouse.it](https://www.domhouse.it)
