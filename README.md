# dog — 毛球崛起寵物商城

貓狗零食、凍乾與飼料的靜態展示網站（純 HTML / CSS / JS，無後端）。

線上瀏覽：開啟 GitHub Pages 後為 https://ken1130.github.io/dog/

## 檔案

| 路徑 | 說明 |
|---|---|
| `index.html` | 主頁面（首頁 / 商品列表 / 商品頁 / 品牌故事 / FAQ 都在這一支） |
| `support.js` | 頁面框架，負責 `{{ }}` 樣板與狀態切換 |
| `image-slot.js` | `<image-slot>` 自訂元件，圖片欄位 |
| `_ds/` | design system：色彩、字體、間距等 token 與 styles.css |
| `uploads/` | 圖片資源 |

## 待辦

- **LINE 按鈕連結尚未設定**：`index.html` 裡搜尋 `YOUR_LINE_ID`，換成自己的
  LINE 官方帳號連結（格式 `https://line.me/R/ti/p/@你的ID`）。

## 圖片來源

`uploads/mao-*` 皆取自 CC0 / Public Domain 公眾領域圖庫（Openverse、Wikimedia
Commons、WordPress Photo Directory），可商業使用且無須標示出處。

其餘 `uploads/tw-*.webp` 與 `a2899c81…webp` 為原專案既有素材。
