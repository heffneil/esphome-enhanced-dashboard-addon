# Changelog

## 0.2.11 — 2026-04-28

- Sort selection (column + ascending/descending) now persists across page reloads, browser restarts, and ingress sessions. Stored in `localStorage` per browser; clear it via DevTools → Application → Storage if you want to reset.

## 0.2.10 — 2026-04-28

- Rebuild on ESPHome 2026.4.3 (latest upstream release)

## 0.2.9 — 2026-04-24

- Fix **Show API Key** button always reporting "No API key found". Now reads the encryption key (or legacy password) directly from the device's YAML and resolves `!secret` references against `secrets.yaml`. Reports a clear error if no `api:` block is configured.

## 0.2.8 — 2026-04-23

Merges [#6](https://github.com/heffneil/esphome-enhanced-dashboard-addon/pull/6) from @lilmansplace:

- Populate **Platform, Name, Friendly Name, Comment** columns from the YAML config when a device has no StorageJSON (never compiled) or stale StorageJSON (renamed after last compile)
- Handle `packages:`, `!include`, and `${substitution}` references correctly via ESPHome's own `yaml_util`
- Indent-aware line-by-line fallback parser when `load_yaml` raises
- Live `entry_updated`/`entry_added` WebSocket events now apply the same YAML fallback so columns don't blank out after a compile/upload
- New **Friendly Name** column between Name and IP Address, toggleable from the ☰ column menu, sortable

## 0.2.7 — 2026-04-23

- Add **Secrets** button in the topbar that opens `secrets.yaml` in the embedded Ace editor — no need to round-trip through the classic dashboard to edit WiFi credentials, API keys, etc.

## 0.2.6 — 2026-04-23

- Expose `default_compile_process_limit` add-on option (matches the stock ESPHome add-on). Set the number of devices that can compile in parallel from the add-on Configuration tab.

## 0.2.5 — 2026-04-23

- Column show/hide menu now covers every column: IP Address, Platform, BT Proxy, ESPHome Version, Comment, Tags, Config File (Status and Name are always visible)

## 0.2.4 — 2026-04-23

- Fix Classic dashboard link 404 under HA ingress — the link was using an absolute path that bypassed the ingress proxy

## 0.2.3 — 2026-04-22

- Fix fetch / WebSocket URLs when running behind Home Assistant ingress (requests like Create Device and device actions were bypassing the ingress proxy and hitting HA's root, returning 404)

## 0.2.2 — 2026-04-19

- Rebuild on ESPHome 2026.4.1

## 0.2.1 — 2026-04-19

- Add BT Proxy column showing ✓ for devices with `bluetooth_proxy` configured
- New **☰** button in the topbar for hiding/showing the BT Proxy column (preference saved in localStorage)

## 0.2.0 — 2026-04-18

Initial Home Assistant add-on release. Based on ESPHome 2026.4.0 with the full enhanced dashboard overlay:

- Compact sortable table view with Status / Name / IP / Platform / Version / Comment / Tags / Config columns
- Live search
- Device tags with quick-filter bar
- Mark Inactive (skips polling)
- Archive & restore
- Side panel with Actions and Utilities sections
- Batch Update / Compile / Archive
- Install to Specific Address
- Ping Device utility
- Embedded Ace YAML editor
- In-page modal for command output
- New Device wizard matching the classic flow
- Clickable IP column opens device web UI
- Classic dashboard preserved at `/classic`
