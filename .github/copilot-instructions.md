# Copilot instructions for not1mm

## Architecture snapshot
- PyQt6 desktop app; primary UI/controller is `MainWindow` in [../not1mm/__main__.py](../not1mm/__main__.py). UI widgets are loaded from Qt Designer `.ui` files in [../not1mm/data/](../not1mm/data/).
- Data storage is SQLite via `DataBase` in [../not1mm/lib/database.py](../not1mm/lib/database.py). The app maintains contest metadata tables and the `DXLOG` QSO table (see table creation in that file).
- Contest rules are implemented as plugins in [../not1mm/plugins/](../not1mm/plugins/). Each plugin defines UI wiring, scoring, and export logic. Shared helpers live in [../not1mm/lib/plugin_common.py](../not1mm/lib/plugin_common.py).
- Preferences are JSON in `fsutils.CONFIG_FILE` and user data in `fsutils.USER_DATA_PATH` (see [../not1mm/fsutils.py](../not1mm/fsutils.py)). Multiple services read these settings (e.g., [../not1mm/lookupservice.py](../not1mm/lookupservice.py), [../not1mm/rtc_service.py](../not1mm/rtc_service.py)).

## Plugin conventions (critical)
- Plugin naming: contest display name is lowercased with spaces to underscores; the file must exist in [../not1mm/plugins/](../not1mm/plugins/). Example: “ARRL 10M” → [../not1mm/plugins/arrl_10m.py](../not1mm/plugins/arrl_10m.py).
- The contest picker list is hardcoded in [../not1mm/data/new_contest.ui](../not1mm/data/new_contest.ui). Adding a plugin requires adding a matching `<item>` there (see [../Anatomy_Of_A_Plugin.md](../Anatomy_Of_A_Plugin.md)).
- Use `EXCHANGE_HINT` and `SOAPBOX_HINT` constants in plugins; the UI reads these in [../not1mm/lib/new_contest.py](../not1mm/lib/new_contest.py).

## Integration points & data flow
- CAT/rig control: `Radio` → `CAT` abstraction ([../not1mm/radio.py](../not1mm/radio.py), [../not1mm/lib/cat_interface.py](../not1mm/lib/cat_interface.py)); supports `rigctld`, `flrig`, and `fake` interfaces.
- N1MM compatible UDP output lives in [../not1mm/lib/n1mm.py](../not1mm/lib/n1mm.py).
- Multicast data bus for multi‑multi and inter‑window comms via [../not1mm/lib/multicast.py](../not1mm/lib/multicast.py).
- External integrations include WSJT‑X UDP listener ([../not1mm/lib/ft8_watcher.py](../not1mm/lib/ft8_watcher.py)), FLDIGI XML‑RPC ([../not1mm/lib/fldigi_sendstring.py](../not1mm/lib/fldigi_sendstring.py)), and real‑time score posts ([../not1mm/rtc_service.py](../not1mm/rtc_service.py)).

## Workflows & tooling
- Local editable install uses [../rebuild.sh](../rebuild.sh) (uv build + `uv pip install -e .`). The entry point is `not1mm.__main__:run` (see [../pyproject.toml](../pyproject.toml)).
- Tests are minimal and UI‑driven; see pytest suite in [../test/contests.py](../test/contests.py).
- Changelog/README updates are automated by [../update_changes.sh](../update_changes.sh), which inserts a line under “Recent Changes” in [../README.md](../README.md) and at the top of [../CHANGELOG.md](../CHANGELOG.md).

## Project patterns to follow
- UI wiring is done with `uic.loadUi(...)` and direct widget attribute access; avoid introducing new UI abstraction layers unless necessary (see [../not1mm/__main__.py](../not1mm/__main__.py)).
- Plugin functions like `interface()`, `set_tab_next()`, `set_contact_vars()`, and scoring functions are expected by the main window; mirror existing plugins to stay compatible (see [../Anatomy_Of_A_Plugin.md](../Anatomy_Of_A_Plugin.md)).
- Database updates often rely on raw SQL strings in plugins; keep SQL consistent with `DXLOG` column names from [../not1mm/lib/database.py](../not1mm/lib/database.py).
