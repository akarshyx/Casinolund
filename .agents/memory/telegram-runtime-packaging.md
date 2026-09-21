---
name: Telegram runtime packaging
description: Packaging quirk encountered when restoring the Telegram casino bot in this workspace.
---

The bot requires `python-telegram-bot`; an unrelated `telegram` distribution can leave the shared `telegram/` namespace without the library initializer, causing imports such as `InlineKeyboardButton` to fail.

**Why:** Installing or uninstalling similarly named distributions in the managed Python environment can remove or overwrite files belonging to the correct package.

**How to apply:** Keep only `python-telegram-bot` installed for this bot, verify `telegram.__version__` and a representative class import before restarting the workflow, and do not add the standalone `telegram` distribution.