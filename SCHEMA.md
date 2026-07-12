# Wiki Schema — 股票資訊

## Domain
台股個股、產業概念、財經節目（podcast／YouTube 電視版）的 persistent knowledge base。
聚焦 **台股** — ticker code 為 TWSE（上市）或 TPEx（上櫃）四位數字。

## Conventions

### File naming
- **Entity pages** (個股): `TWSE-2327國巨.md` / `TPEx-8046禾伸堂.md` — `{market}-{code}{中文名}.md`，全形中文、**不要**用空白分隔
- **Concept pages** (產業／主題): 繁中、英文或混用皆可，例如 `被動元件.md`、`矽晶圓.md`、`ETF.md`、`台積電法說.md`
- **Show pages** (節目單集): `YYYY-MM-DD-{show-slug}-{short-id}.md`，例如 `2026-07-09-lsm-e36.md`
- **Compare pages** (多家比較): `compare-{topic}.md`
- 全部使用 kebab-case lower，**沒有空格的檔名**（中文屬於檔名一部分，不是分隔）
- Raw 來源描述檔名: `raw/articles/{site}-{slug}-{YYYY-MM-DD}.md`

### Frontmatter (必要)
每個 wiki page 開頭都要有 YAML frontmatter:
```yaml
---
title: 國巨
created: 2026-07-12
updated: 2026-07-12
type: entity | concept | show | compare | query
market: TWSE | TPEx | null   (entity 必填,其他選填)
ticker: "2327"               (entity 必填,其他為 null)
industry: [被動元件, MLCC]   (entity / concept 用)
tags: [from taxonomy]
sources: [raw/transcripts/ezK6Uefj5qY-fw.txt]
confidence: high | medium | low
contested: true | false
contradictions: []
---
```

### Wiki-links
- 用 `[[wikilinks]]` 串起頁面。每個 page 至少要有 2 個 outbound wiki link
- Ticker link 範例: `[[TWSE-2327國巨]]`
- Concept link 範例: `[[被動元件]]`、`[[矽晶圓]]`

### Index / Log
- 新頁面一律寫到 `index.md`（同 section 內字母／筆畫排序）
- 任何動作 append 到 `log.md`（一年超過 500 條時 rotate）

## Tag Taxonomy

Sector 類:
- `passive-component` (被動元件)
- `mlcc` (積層陶瓷電容)
- `wafer` (矽晶圓)
- `memory` (記憶體)
- `ccl` (銅箔基板)
- `pcb` (載板)
- `equipment` (半導體設備)
- `military` (軍工)
- `defense-uas` (無人機)
- `quartz` (石英元件)

Event 類:
- `earnings-call` (法說會)
- `revenue-print` (營收公布)
- `rate-decision` (央行利率決議)
- `geopolitics` (地緣政治)

Meta 類:
- `show` (podcast 集數)
- `entity-ticker` (個股頁)
- `concept` (產業／主題頁)
- `compare` (比較頁)
- `pivot` (換手策略)
- `pullback` (拉回策略)
- `position-sizing` (資金管理)

新增 tag 之前必須在這個清單加上。

## Page Thresholds
- 同一個 ticker 收到**第一手**來源就要建 entity page（給它 future 來源能裝）
- Concept 至少要在 **2 個來源** 提到，或**1 個來源深入討論**才建
- 不要為了一句順路提及建 stub
- 一頁超過 200 行：拆

## Update Policy
- 新來源與既有內容衝突時：較新 timestamp 為主，但雙方都保留，frontmatter `contradictions:` 標清
- 新資料優於舊猜測

## Quality Signals
- `confidence:` 沒把握設 medium 或 low，不要無故用 high
- 解讀性內容、或只從 1 個來源：建議 medium 起步
- 多來源交叉確認：高

## Entity 頁結構
每個 ticker 頁要有:
1. 概述（做什麼、公司性質、市場）
2. 關鍵事件（法說、營收、處置、減資）
3. 與其他標的的關係（[[wikilinks]]）
4. 技術面關鍵價（若來源有提到）
5. 信心標記

## Concept 頁結構
1. 定義
2. 關鍵個股（用 [[wikilinks]] 串）
3. 目前狀態
4. 事件時間軸
5. 反向因子（影響這個族群的逆風）

## Show 頁結構
1. 集基本資料（主持人／來賓／上傳日期）
2. 主題清單
3. 逐字稿關鍵段落（時間戳 → 重點）
4. 提到個股對照表（time/ticker/quote）
5. 結論／takeaway

## Provenance
單一來源頁不用加。3+ 來源頁：在該段尾端加 `^[raw/...]` 連結。
