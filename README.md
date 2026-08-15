# Stay Young 青春無限 — 品牌主站

`stayyounglab.com` 的原始碼。純靜態單頁，不含報名功能 —— 報名一律在各營隊子站完成。

## 檔案結構

| 路徑 | 用途 |
|---|---|
| `index.html` | 單頁主站（Hero／營隊總覽／關於我們／聯絡／CTA） |
| `football/index.html` | 轉址頁 → `nthu-football.stayyounglab.com`（保留舊連結相容） |
| `badminton/index.html` | 轉址頁 → `ntu-badminton.stayyounglab.com` |
| `images/` | 主視覺與三張營隊卡照片 |
| `robots.txt`、`sitemap.xml` | SEO |
| `CNAME` | GitHub Pages 自訂網域，**請勿刪除** |

## 子站

各營隊為**獨立 repo、獨立 Apps Script、獨立 Google Sheet**，彼此不共用資料。

| 營隊 | 網址 | Repo |
|---|---|---|
| 清華大學足球冬令營 2027 | https://nthu-football.stayyounglab.com | [football-camp](https://github.com/Ryan1109-d/football-camp) |
| 台灣大學羽球冬令營 2027 | https://ntu-badminton.stayyounglab.com | [badminton-camp](https://github.com/Ryan1109-d/badminton-camp) |
| 清華大學羽球夏令營 2026 | https://nthu-badminton.stayyounglab.com | [summarcamp](https://github.com/Ryan1109-d/summarcamp) |

夏令營（summarcamp）維持**獨立品牌**：主辦單位掛「清華大學羽球校隊」，只在左上角放 Stay Young 標誌連回主站。

## DNS（Porkbun）

七筆 CNAME 全部指向 `ryan1109-d.github.io`：

| 主機 | 狀態 |
|---|---|
| `@`、`www` | 主站 |
| `nthu-football`、`ntu-badminton`、`nthu-badminton` | 三個子站，使用中 |
| `football`、`badminton` | **已失效**（一個 repo 只能綁一個自訂網域，這兩筆沒有對應 repo，會 404） |

舊的 `football.` / `badminton.` 連結請改用 `stayyounglab.com/football/`、`/badminton/` 轉址頁。

## 設計基準

```
底色        #ffffff        次要區塊  #f2f6fa        卡片  #fbfcfe
邊框        #d9e2ec        足球主色  #1560b8        羽球主色  #e07b1f
標題字      Noto Serif TC 900
內文字      Noto Sans TC
```

- Hero 是**白底品牌橫幅**。圖片本身自帶 STAY YOUNG 標誌，文字與按鈕排在圖片**下方**，不要壓在圖上。
- 營隊卡按**地區**分組（新竹｜清華大學、台北｜臺灣大學），不按運動項目分。
- 卡片照片無遮罩，文字靠 `text-shadow` 撐可讀性；`.camp-top` 的 `min-height:180px` 不能拿掉，否則會裁到人物。
- `.reveal` 滾動浮現動畫只播一次，不重播。

三張營隊卡照片與 Hero 為圖庫／AI 生成素材，**不可標示為「實拍」或放進「活動花絮」**。

## 待處理

- `index.html` 仍掛 `noindex`。`robots.txt` 與 `sitemap.xml` 已就緒，公開招生前要把 `noindex` 拿掉，否則 Google 不會收錄。
- 「關於我們」的「500+ 累計服務學員」為對外宣稱數字，需能舉證。

## 部署

GitHub Pages（`master` / root）。push 後約 1–3 分鐘生效；用 curl 輪詢驗證，不要只看 commit 有沒有進去。

本機修改前先 `git pull` —— 這個 repo 常直接在 GitHub 網頁上編輯，容易分岔。
