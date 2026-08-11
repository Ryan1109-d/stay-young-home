# Stay Young 運動團隊 — 主頁

品牌主站，作為各營隊子站的入口。

## 檔案結構

| 檔案 | 用途 |
|------|------|
| `index.html` | 單頁主站（Hero／營隊總覽／關於我們／聯絡／CTA） |

## 網域

主站自訂網域：**stayyounglab.com**（Porkbun 管理 DNS，CNAME → `ryan1109-d.github.io`）。
repo 根目錄的 `CNAME` 檔由 GitHub Pages 自動產生，**請勿刪除**。

## 子站連結（路徑轉址）

| 營隊 | 主站路徑 | Repo | 實際網址 |
|------|---------|------|---------|
| 清華大學足球冬令營 2027 | `/football/` | [football-camp](https://github.com/Ryan1109-d/football-camp) | https://ryan1109-d.github.io/football-camp/ |
| 台灣大學羽球冬令營 2027 | `/badminton/` | [badminton-camp](https://github.com/Ryan1109-d/badminton-camp) | https://ryan1109-d.github.io/badminton-camp/ |

各營隊為**獨立 repo、獨立 GAS、獨立 Google Sheet**，主站只做連結，不含報名功能。
`football/index.html` 與 `badminton/index.html` 是轉址頁（`location.replace` + `meta refresh` 雙保險），
使用者從 `stayyounglab.com/football/` 進入後，網址列會變成該子站的 `github.io` 網址。

> **若要讓網址列全程維持品牌網域**，改用子網域較乾淨：
> Porkbun 加 CNAME `football` → `ryan1109-d.github.io`，
> 並在 football-camp repo 的 Pages 設定 Custom domain 填 `football.stayyounglab.com`（羽球同理）。

## 設計基準

沿用兩個營隊站的視覺語言，維持品牌一致：

- 底色白 `#ffffff`、次要區塊 `#f2f6fa`
- 主色深藍 `#1560b8`／`#0a2e57`，強調色琥珀 `#f0930f`
- 標題 Noto Serif TC 900、內文 Noto Sans TC
- Hero 深藍漸層＋格線＋琥珀強調；卡片 hover 浮起＋陰影

足球卡用深藍系、羽球卡用琥珀系，對應各自子站主色。

## 待填內容（TODO）

| # | 位置 | 內容 |
|---|------|------|
| 1 | Hero | 品牌主視覺照片（目前為純漸層背景） |
| 2 | 營隊卡 | 各營隊代表照片（目前為漸層＋emoji） |
| 3 | 關於我們 | 團隊實績數字、成立年份等（目前為通則描述） |
| 4 | 全站 | 自訂網域（買了再設定 CNAME） |

## 新增營隊的做法

1. 建立新營隊 repo（比照 football-camp / badminton-camp）
2. 在 `index.html` 的 `#camps` 區塊複製一張 `.camp` 卡片
3. 改 `href`、`camp-top` 的漸層 class、emoji、名稱、slogan、`.cm` 標籤與描述

## 部署

GitHub Pages（master / root）。push 後約 1–3 分鐘生效。
