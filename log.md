# Wiki Log

> 所有 wiki 動作的時序紀錄，append-only。
> 格式：`## [YYYY-MM-DD] action | subject`
> 動作類：create, ingest, update, query, lint, archive, delete
> 當這個檔超過 500 條時 rotate: rename 成 `log-YYYY.md`，重新開始。

## [2026-07-12] create | Wiki 初始化
- Domain: 台股個股、產業概念、財經節目
- 建立 SCHEMA.md, index.md, log.md
- 資料夾：raw/ (transcripts, articles, assets), entities/, concepts/, shows/, comparisons/, queries/
- 路徑：`/mnt/e/OB/Stock/股票資訊/` (Obsidian vault)

## [2026-07-12] ingest | 2026-07-09 理財達人秀電視版
- 來源：YouTube video ID ezK6Uefj5qY
- 原始逐字稿：`raw/transcripts/ezK6Uefj5qY-fw.txt` (faster-whisper tiny)
- 建立頁面：
  - `shows/2026-07-09-lsm-e36.md` (Show page)
  - `entities/TWSE-2327國巨.md`
  - `entities/TWSE-2492華新科.md`
  - `entities/TWSE-8046禾伸堂.md`
  - `entities/TWSE-2330台積電.md`
  - `concepts/被動元件.md`
  - `concepts/矽晶圓.md`
  - `concepts/軍工.md`
  - `concepts/科技ETF.md`
  - `concepts/台塑集團.md`
  - `entities/TWSE-6488環球晶.md`
  - `concepts/石英元件.md`
  - `concepts/記憶體.md`
- 更新 `index.md` (共 12 頁)
- 信心：`medium` — tiny 模型有錯讀，待 large-v3 重跑驗證

## [2026-07-12] lint | wiki 完整性
- 14 個 .md 頁面（5 個系統頁 + 9 個內容頁）
- 15 個 broken wikilinks → 已修：(a) 建立 stub 頁面（環球晶、石英元件、記憶體），(b) 移除順帶一提的 wikilink 改純文字
- 沒有真正 orphan 內容頁（每頁 inbound ≥ 4）
- 持續追蹤：tiny whisper 文字需用 large-v3 重新校正後才能把 confidence 升為 high

## [2026-07-12] update | 第二輪 stub 建置
- 新增頁面：
  - `entities/TWSE-1301台塑.md`、`TWSE-1303南亞.md`、`TWSE-1326台化.md`
  - `concepts/CCL.md`、`concepts/半導體.md`
  - `concepts/2026-07-16-tsmc-earnings-call.md`
- 更新 `index.md` (共 18 頁 → 後 23 個檔案總計)
- 完整檔案結構見下方

## [2026-07-13] ingest | 2026-07-08 理財達人秀回補
- 來源: YouTube video Or-gZxDhTS0
- 下載 mp3 (57 MB, 48:50)
- faster-whisper tiny 跑 1998 段 (133s wall clock)
- raw transcript 寫入 vault: `raw/transcripts/Or-gZxDhTS0-fw.txt`
- 建立 show page: `shows/2026-07-08-lsm-e34.md`
- 建立 entity stub:
  - `entities/KRX-005930三星電子.md`
  - `entities/KRX-000660SK-Hynix.md`
- 更新 `index.md` (21 頁)
- 信心 medium：tiny 模型字詞誤讀常見（如 兆華→造華、三星→三倍、南亞→眼欄）

## [2026-07-13] ingest | 2026-07-07 雙集回補
- 來源 1: YouTube kMQpMKFxXkM (理財達人秀 完整版)
- 來源 2: YouTube V_jJvPjytSg (兆華艾綸說 網路獨播版)
- 下載 mp3 兩支共 116 MB
- faster-whisper tiny 跑約 4.5 分鐘 (1798 + 2001 段)
- raw 寫入: `raw/transcripts/kMQpMKFxXkM-fw.txt` + `V_jJvPjytSg-fw.txt`
- show pages: 
  - `shows/2026-07-07-lsm-e33.md`
  - `shows/2026-07-07-ealun-lsm.md`
- 兩集主題相近：開高殺低、AI 利空報告連發、被動+CCL+矽晶圓重殺
- 重點待驗證項目：whisper 讀的「CME in the Lies」是哪家分析機構 (Citigroup / Morgan Stanley / 其他)
- 更新 `index.md` (23 頁)
