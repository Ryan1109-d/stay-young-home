# Stay Young 運動團隊 — 主頁

品牌主站，作為各營隊子站的入口。

## 檔案結構

| 檔案 | 用途 |
|------|------|
| `index.html` | 單頁主站（Hero／營隊總覽／關於我們／聯絡／CTA） |

## 網域

主站自訂網域：**stayyounglab.com**（Porkbun 管理 DNS，CNAME → `ryan1109-d.github.io`）。
repo 根目錄的 `CNAME` 檔由 GitHub Pages 自動產生，**請勿刪除**。

## 子站（各自擁有子網域）

| 營隊 | 子網域 | Repo | 主站路徑（轉址） |
|------|--------|------|----------------|
| 清華大學足球冬令營 2027 | https://football.stayyounglab.com | [football-camp](https://github.com/Ryan1109-d/football-camp) | `/football/` |
| 台灣大學羽球冬令營 2027 | https://badminton.stayyounglab.com | [badminton-camp](https://github.com/Ryan1109-d/badminton-camp) | `/badminton/` |

各營隊為**獨立 repo、獨立 GAS、獨立 Google Sheet**，主站只做連結，不含報名功能。

**全站不外露 github.io**：三種入口都會落在品牌網域

1. 主頁卡片 → 直接連子網域
2. `stayyounglab.com/football/` → 轉址頁導向子網域（保留舊連結相容）
3. 有人直接開 `ryan1109-d.github.io/football-camp/` → GitHub 自動 301 到子網域

### DNS 設定（Porkbun）

| 類型 | 主機 | 目標 |
|------|------|------|
| CNAME | `@` | `ryan1109-d.github.io` |
| CNAME | `www` | `ryan1109-d.github.io` |
| CNAME | `football` | `ryan1109-d.github.io` |
| CNAME | `badminton` | `ryan1109-d.github.io` |

三個 repo 根目錄各有 GitHub 自動產生的 `CNAME` 檔，**請勿刪除**；
在本機對子站套用修改前記得先 `git pull`。

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
