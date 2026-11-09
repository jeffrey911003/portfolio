# CLAUDE.md — Jeffrey 的作品展示網站

> 這份文件寫給 AI（Claude、Codex、Cursor 等）和未來的我。
> 修改或新增任何內容前，請先完整讀完這份文件，並嚴格照著規則做。

---

## 1. 專案目的

- 用來展示 **Jeffrey（GitHub: `jeffrey911003`）** 自己做的程式作品。
- 讓看的人（老師、面試官、同學）在 **30 秒內**知道：這個作品在做什麼、用了什麼技術、我負責哪部分、在哪裡可以實際操作。
- 網站部署在 **GitHub Pages**，網址：`https://jeffrey911003.github.io/portfolio/`
- 最重要的目標：**之後每新增一件作品，只要照第 6 節的流程，10 分鐘內就能完成。**

---

## 2. 技術限制（不可違反）

| 規則 | 說明 |
|---|---|
| 只用純 HTML + CSS + 少量原生 JS | 不使用 React、Vue、npm、打包工具，GitHub Pages 直接能跑 |
| 不需要建置步驟 | 直接用瀏覽器開啟 `index.html` 就能看到完整網站 |
| 外部資源只允許 Google Fonts | 不引入 Bootstrap、Tailwind、jQuery 等 CDN |
| 所有路徑使用**相對路徑** | 例如 `assets/css/style.css`、`../assets/...`，不能用 `/assets/...` 開頭（在 GitHub Pages 子路徑會壞掉） |
| 所有樣式寫在 `assets/css/style.css` | HTML 中不寫 `style="..."` 行內樣式，也不寫 `<style>` 區塊 |

---

## 3. 資料夾結構

```
portfolio/
├── CLAUDE.md                 ← 本文件（AI 規則）
├── README.md                 ← 給人看的簡介
├── index.html                ← 首頁：Hero、關於我、作品列表、聯絡
├── works/
│   ├── _template.html        ← 作品詳細頁範本（新增作品時複製它）
│   ├── pitchlab.html         ← 作品頁
│   └── web-recommend.html    ← 作品頁
└── assets/
    ├── css/style.css         ← 全站唯一的樣式檔
    ├── js/main.js            ← 全站唯一的 JS（年份、導覽列）
    └── images/works/<slug>/  ← 每件作品一個資料夾
        ├── cover.webp        ← 封面（必要）
        └── screenshot-01.webp ← 其他截圖（選用，依序編號）
```

---

## 4. 命名規則

- **slug**（作品代號）：全小寫英文 + 連字號，例如 `pitchlab`、`web-recommend`、`casino-game`。
  - 作品頁：`works/<slug>.html`
  - 圖片資料夾：`assets/images/works/<slug>/`
- 圖片：封面一律叫 `cover.webp`；其他截圖叫 `screenshot-01.webp`、`screenshot-02.webp`……
- 圖片格式用 `.webp`，寬度不超過 1600px，單張盡量小於 300KB。
- 封面比例約 **2:1**（例如 1600×800）。首頁卡片以 2:1 顯示，比例差太多時重要文字會被裁掉。
- 截圖要**裁掉瀏覽器網址列與 Windows 工作列**，只留網頁本身的畫面。
- 檔名不可有中文、空白或大寫。

---

## 5. 視覺風格

整體風格：**深色、簡約、工程師作品集感**。資訊清楚優先，不加花俏動畫。

### 5.1 顏色（只能使用 `style.css` 裡 `:root` 定義的變數）

| 變數 | 色碼 | 用途 |
|---|---|---|
| `--bg` | `#0b0f17` | 頁面背景 |
| `--surface` | `#131a26` | 卡片、區塊背景 |
| `--border` | `#243044` | 邊框、分隔線 |
| `--text` | `#e6edf3` | 主要文字 |
| `--muted` | `#8b98a9` | 次要文字、說明 |
| `--accent` | `#ff7a45` | 強調色（按鈕、連結、標籤） |

**不可以新增其他主色。** 需要新顏色時，先在 `:root` 加變數並更新這張表。

### 5.2 字體

- 內文：`Noto Sans TC`
- 程式碼、技術標籤、日期：`JetBrains Mono`

### 5.3 共用元件（只能用這些 class，不要另外發明）

| class | 用途 |
|---|---|
| `.container` | 內容置中、最大寬度 1100px |
| `.section` / `.section-title` | 區塊與區塊標題 |
| `.btn` / `.btn-primary` / `.btn-ghost` | 按鈕 |
| `.work-card` | 首頁作品卡片 |
| `.tag` | 技術標籤（例如 Python、React） |
| `.meta-list` | 作品頁右側的資訊欄（時間、角色、技術） |
| `.gallery` | 作品頁截圖區 |

### 5.4 響應式

- 寬度 ≤ 720px 時，作品卡片改成單欄，導覽列文字縮小。
- 新增內容後必須確認手機寬度（375px）沒有出現橫向捲軸。

---

## 6. 新增一件作品的標準流程（最重要）

當我說「新增作品：xxx」時，AI 必須依序完成以下 **5 步**，缺一不可：

1. **確認資料**：作品資料必須包含下表的必填欄位，缺少時先問我，不可自己捏造。
2. **放圖片**：建立 `assets/images/works/<slug>/`，放入 `cover.webp`（與其他截圖）。
3. **建立作品頁**：複製 `works/_template.html` 為 `works/<slug>.html`，把所有 `{{ }}` 佔位字替換掉，**不可留下任何 `{{`**。
4. **更新首頁**：在 `index.html` 的 `<!-- WORKS:START -->` 與 `<!-- WORKS:END -->` 之間，**最上方**新增一張 `.work-card`（新作品排最前面），格式照抄現有卡片。
5. **自我檢查**：照第 8 節檢查清單逐項確認。

### 作品資料欄位

| 欄位 | 必填 | 範例 |
|---|---|---|
| 作品名稱 | ✅ | PitchLab 棒球數據分析平台 |
| slug | ✅ | `pitchlab` |
| 一句話簡介（卡片用，≤ 40 字） | ✅ | 用 MLB Statcast 數據分析每一球，並預測下一球球種。 |
| 詳細介紹（2～4 段） | ✅ | 解決什麼問題、怎麼運作、功能有哪些 |
| 製作時間（YYYY.MM） | ✅ | 2026.05 |
| 我的角色 | ✅ | 個人專案，前後端全部獨立完成 |
| 使用技術 | ✅ | Python、FastAPI、React |
| Demo 網址 | 選填 | https://... |
| GitHub 網址 | 選填 | https://github.com/jeffrey911003/... |
| 封面圖 | ✅ | `cover.webp` |

---

## 7. 文字撰寫規則

- 網站主要語言為**繁體中文**，技術名詞保留英文原名（Python、FastAPI、React、Top-K）。
- 中文與英文、數字之間**加一個半形空格**：`使用 Python 開發`、`Top-3 推薦`。
- 語氣：第一人稱、簡潔、具體。多寫「做了什麼、結果是什麼」，少寫空泛的形容詞（「非常厲害」「超級強大」）。
- 作品詳細頁的「功能特色」用條列，每點一行，不超過 30 字。
- 不要誇大或虛構數據；成果數字只寫我提供的。

---

## 8. AI 修改時的規則與檢查清單

### 必須遵守

- ✅ 只改和這次任務有關的檔案，不順手重構其他地方。
- ✅ 新增樣式時，優先重用第 5.3 節的 class；真的需要新 class 才加進 `style.css`，並更新第 5.3 節的表。
- ✅ 結構或規則有變動時，**同步更新這份 `CLAUDE.md`**。
- ❌ 不可刪除 `<!-- WORKS:START -->` / `<!-- WORKS:END -->` 標記。
- ❌ 不可改變現有色彩、字體設定，除非我明確要求。
- ❌ 不可加入追蹤碼、廣告或不明外部腳本。

### 完成後檢查清單

- [ ] 所有連結、圖片都使用相對路徑，而且檔案真的存在
- [ ] 作品頁沒有殘留 `{{ }}` 佔位字
- [ ] 首頁卡片連到正確的 `works/<slug>.html`
- [ ] 作品頁的「← 返回作品列表」可以回到首頁
- [ ] 外部連結（Demo、GitHub）都有 `target="_blank" rel="noopener"`
- [ ] 每張圖片都有中文 `alt` 描述
- [ ] 手機寬度沒有橫向捲軸
- [ ] `<title>` 格式為：`作品名稱｜Jeffrey Portfolio`

---

## 9. 部署方式

1. 把整個 `portfolio/` 推到 GitHub repo `jeffrey911003/portfolio` 的 `main` 分支。
2. Repo → Settings → Pages → Source 選 `Deploy from a branch` → `main` / `/ (root)`。
3. 約 1 分鐘後，網站會出現在 `https://jeffrey911003.github.io/portfolio/`。
4. 之後每次 `git push` 都會自動更新網站。

Commit 訊息格式：`feat: 新增作品 <slug>`、`fix: 修正 <內容>`、`style: 調整 <內容>`、`docs: 更新 CLAUDE.md`。

---

## 10. 目前作品清單

| slug | 作品 | 時間 | 技術 |
|---|---|---|---|
| `web-recommend` | 網頁推薦系統（企業數據分析後台） | 2026.06 | Python、HistGradientBoosting、React |
| `pitchlab` | PitchLab 棒球數據分析平台 | 2026.05 | Python、FastAPI、React |

> 新增作品後，請把它加在這張表的最上面。
