# 口條練習基地 Pro

GitHub Pages 可直接部署的進階手機版。包含抽籤、倒數、錄音、逐字稿、語速與口頭禪統計、練習統計、連續練習天數、成就徽章、收藏與主題類別分析，以及提醒使用者將口條練習延伸到真實的人際互動。

## 上傳方式

新建一個 GitHub repository，例如 `speaking-lottery-pro`。將 **本資料夾內** 的 `index.html`、`style.css`、`social-reminder.css`、`app.js` 上傳到 repository 的最外層（不要連同 `speaking-lottery-pro` 資料夾再包一層）。

GitHub Pages 設為 `main` branch / `(root)` 後，網址會是：

`https://owenwuwu.github.io/speaking-lottery-pro/`

## 錄音機制

使用原生 JavaScript 的 `navigator.mediaDevices.getUserMedia()` 取得麥克風，再以 `MediaRecorder` 錄製。錄音檔以瀏覽器的 IndexedDB 儲存在同一裝置，並可下載為音檔。

- 不需安裝軟體、不需要伺服器或 API 金鑰。
- GitHub Pages 的 HTTPS 網址可讓瀏覽器請求麥克風權限。
- 錄音與紀錄不會同步到其他裝置；清除瀏覽器資料會一併移除。

## 手機逐字稿

開始錄音時，網站會嘗試使用瀏覽器的 Web Speech API 以繁體中文（`zh-TW`）即時產生逐字稿，並依錄音秒數計算語速與「然後、就是、嗯、呃、那個」等口頭禪出現次數。

- 建議使用最新版 Android Chrome，並從 GitHub Pages 的 HTTPS 網址開啟網站。
- 第一次使用時請允許麥克風權限，且語音辨識通常需要網路連線。
- Safari、部分手機瀏覽器或公司／學校受管理裝置可能不提供 Web Speech API；遇到這種情況，網站仍會保留錄音，並可在「辨識文字」欄位手動貼上或修正逐字稿。
- 若需要所有手機都能把錄音檔轉成文字，必須再串接雲端語音辨識服務（例如 Azure Speech 或 OpenAI Speech-to-Text），不能只靠靜態 GitHub Pages 網頁完成。
