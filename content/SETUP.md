---
title: SETUP — 如何把這套放上 Quartz 網站
draft: true
---

# Quartz 部署說明（給你自己看，不會被發佈）

這份檔案 `draft: true`，不會出現在網站上。以下步驟做完，主管就能用一個網址看到上面那些專案頁與圖片。

---

## 0. 前置需求
- Node.js（裝最新 LTS 即可；Quartz 目前需要較新版本，裝 v22 最保險）
- Git
- 一個 GitHub 帳號

## 1. 安裝 Quartz
```bash
git clone https://github.com/jackyzha0/quartz.git
cd quartz
npm i
npx quartz create
```
`npx quartz create` 會問你要怎麼初始化 `content/` 資料夾，選 **Empty Quartz** 即可。

## 2. 放入內容
Quartz 把 `content/` 這個資料夾當成你的 vault。做法二選一：

**做法 A（推薦，乾淨）**：把我給你的這些檔案放進 `content/`，再把你的圖片資料夾 `img/` 一起複製進去。完成後結構像這樣：
```
quartz/
  content/
    index.md                ← 首頁（主管的入口）
    Projects/
      CucumberRobot.md
      Sensors-PointCloud.md
      IsaacSim.md
      ROS2.md
      Paper.md
      TaiwanGermany.md
    img/
      202605_report/
        TOF1.png  d405_1.png  ...（你本機那些圖）
    _templates/             ← 範本，不會被發佈
```

**做法 B（直接用整個 vault）**：把你整個 `305_WORK` 當成 `content/`。這樣連 daily log、context.md、instructions.md 都會進來，**所以一定要做下一步的隱私設定**，否則內部檔會公開。

> 重點：`content/index.md` 一定要存在，否則 build 會警告甚至出錯。

## 3. 隱私設定（重要，避免內部檔外流）
編輯 `quartz.config.ts`，把 filter 改成「只發佈有標記的頁面」：
```ts
plugins: {
  transformers: [ /* 保持原樣 */ ],
  filters: [Plugin.ExplicitPublish()],   // 只發佈 frontmatter 有 publish: true 的頁
  emitters: [ /* 保持原樣 */ ],
}
```
- 預設 Quartz 用的是 `Plugin.RemoveDrafts()`（只擋掉 `draft: true`）。
- 改成 `Plugin.ExplicitPublish()` 後，**只有寫了 `publish: true` 的頁才會上站**。我給你的 index.md 和六個專案頁都已經寫好 `publish: true`；你的 daily log、`context.md`、`instructions.md` 沒寫，就會自動留在私人不公開。

另外在 `quartz.config.ts` 的 `ignorePatterns` 加上要完全略過的東西：
```ts
ignorePatterns: ["private", ".obsidian", "**/*.canvas"],
```

> ⚠️ 注意：不論用哪種 filter，**所有「非 markdown」檔案（圖片、PDF…）都會被發佈到網站上**。也就是說 `img/` 裡的圖會公開（這正是你要的）。但別把任何敏感的「非 .md 檔」放進 `content/`。如果你的 GitHub repo 設為 public，敏感檔也要記得加進 `.gitignore`。

## 4. 本機預覽
```bash
npx quartz build --serve
```
打開瀏覽器到 http://localhost:8080 ，確認圖片有出來、wikilink 點得到。改檔案會自動重建。

## 5. 部署到 GitHub Pages（免費）
1. 在 GitHub 開一個 repo，把整個 quartz 專案 push 上去。
2. 依官方說明加上部署用的 GitHub Action，並在 repo 的 Settings → Pages 把 Source 設為 **GitHub Actions**。
3. 之後每次 `git push`（或 `npx quartz sync`），GitHub Action 會自動重建並更新網站。
4. 官方完整步驟：https://quartz.jzhao.xyz/hosting

完成後網址大約是 `https://你的帳號.github.io/repo名稱/`，把這個丟給主管即可。

## 6. 讓圖片以後自動歸到同一資料夾（Obsidian 設定）
這樣你以後貼圖就不用一張張處理：
- Obsidian → 設定 → 檔案與連結 → **「附件的預設位置」→ 指定資料夾 →** 填 `img`（或 `img/年月`）。之後貼／拖任何圖都自動進這個資料夾。
- 同一頁的 **「使用 [[Wikilinks]]」維持開啟**（Quartz 支援，不用改寫成標準語法）。

## 7. 日常流程
1. 在 Obsidian 照常寫（daily log、更新專案頁的 `- [ ]`、貼圖）。
2. 要更新給主管看的內容時，更新對應的 `Projects/*.md`，把完成的項目打勾。
3. `git push`（或 `npx quartz sync`）→ 網站自動更新。

## 小提醒
- 給主管看的「總覽 dashboard」（index.md）請維持用**靜態的勾選清單與表格**，不要用 Dataview 產生——Dataview 只在你本機 Obsidian 會跑，上網站不會顯示。
- daily log 預設不公開（沒有 publish: true）。哪天想公開某一篇，在那篇的 frontmatter 加 `publish: true` 即可。
