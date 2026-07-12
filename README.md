# 口條練習基地 Pro

GitHub Pages 可直接部署的進階手機版。包含抽籤、倒數、錄音、練習統計、連續練習天數、成就徽章、收藏與主題類別分析。

## 上傳方式

新建一個 GitHub repository，例如 `speaking-lottery-pro`。將 **本資料夾內** 的 `index.html`、`style.css`、`app.js` 上傳到 repository 的最外層（不要連同 `speaking-lottery-pro` 資料夾再包一層）。

GitHub Pages 設為 `main` branch / `(root)` 後，網址會是：

`https://owenwuwu.github.io/speaking-lottery-pro/`

## 錄音機制

使用原生 JavaScript 的 `navigator.mediaDevices.getUserMedia()` 取得麥克風，再以 `MediaRecorder` 錄製。錄音檔以瀏覽器的 IndexedDB 儲存在同一裝置，並可下載為音檔。

- 不需安裝軟體、不需要伺服器或 API 金鑰。
- GitHub Pages 的 HTTPS 網址可讓瀏覽器請求麥克風權限。
- 錄音與紀錄不會同步到其他裝置；清除瀏覽器資料會一併移除。
