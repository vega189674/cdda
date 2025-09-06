Mod translations scaffold

Source PO files:
- `ManaBackflowInhibitorCBM_MOD/lang/po/ja.po`
- `ManaBackflowInhibitorCBM_MOD/lang/po/en.po`

Package layout for extracting at game root:
- `data/mods/ManaBackflowInhibitorCBM_MOD/**`  ← JSON and content files
- `mods/ManaBackflowInhibitorCBM_MOD/lang/mo/ja/LC_MESSAGES/mana_backflow_inhibitor_cbm.mo`  ← compiled JA translation (pattern A)
- `mods/lang/mo/ja/ManaBackflowInhibitorCBM_MOD/mana_backflow_inhibitor_cbm.mo`              ← alternative path some builds read (pattern B)

Build MO (Japanese):
- Pattern A: `msgfmt -o ManaBackflowInhibitorCBM_MOD/mods/ManaBackflowInhibitorCBM_MOD/lang/mo/ja/LC_MESSAGES/mana_backflow_inhibitor_cbm.mo ManaBackflowInhibitorCBM_MOD/lang/po/ja.po`
- Pattern B: `msgfmt -o ManaBackflowInhibitorCBM_MOD/mods/lang/mo/ja/ManaBackflowInhibitorCBM_MOD/mana_backflow_inhibitor_cbm.mo ManaBackflowInhibitorCBM_MOD/lang/po/ja.po`

Alternative (if your build ignores per‑mod MO files):
1) Backup game‐root `lang/mo/ja/LC_MESSAGES/cataclysm-dda.mo`
2) `msgunfmt lang/mo/ja/LC_MESSAGES/cataclysm-dda.mo > base.po`
3) `msgcat base.po ManaBackflowInhibitorCBM_MOD/lang/po/ja.po > merged.po`
4) `msguniq -o merged.po merged.po`
5) `msgfmt -o lang/mo/ja/LC_MESSAGES/cataclysm-dda.mo merged.po`

Notes:
- Keep JSON `name.str`/`description.str` in English. Translations override at runtime where supported.
