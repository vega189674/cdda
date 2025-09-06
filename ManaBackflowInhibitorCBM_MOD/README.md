# Mana Backflow Inhibitor CBM (Magiclysm)

## 目的
- Magiclysmの「bionic powerに応じた最大マナ低下（逆流ペナルティ）」相殺するCBMを追加する。
- 入手は自然配置とモンスター由来（解体/ドロップ）のみ。レシピなし。
- 同一CBMは1個まで（dupes_allowed:false）。

## 効果（キー式）
```
"enchantments": [ { "condition": "ALWAYS", "values": [ { "value": "BIONIC_MANA_PENALTY", "multiply": -1 } ] } ]
```
- 逆流ペナルティ係数を反転（例: 通常の減少効果を実質無効化）。

## 構成
ManaBackflowInhibitorCBM_MOD/
  modinfo.json
  bionics/bionics.json
  items/bionics.json
  itemgroups/spawn_bionics.json
  itemgroups/harvest_extend.json
  itemgroups/monster_death_drops.json
  README.md

## 導入
- `<game>/data/mods/ManaBackflowInhibitorCBM_MOD` へ配置 → 新規ワールドで `mana_backflow_inhibitor_cbm` を有効化。

## 入手
- 自然配置: `bionics` / `bionics_common` / `bionics_mil`（存在すれば `bionics_sci` / `bionics_op`）に重み10で追加。
- 解体: `mon_zomborg` / `mon_zomborg_devourer`（Zomborg_CBM_harvestに10%）、`mon_feral_technomancer`系（8〜10%）。
- ドロップ: `mon_feral_technomancer_death_drops` に5%。

## テスト
- Debug > Test Item Group で各グループに出現することを確認。
- インストール後、bionic電力の蓄電時に最大マナ低下が発生しない（相殺される）ことを確認。

