# 口條練習基地 Pro（含本機口條分析）

GitHub Pages 可直接部署的進階手機版。包含抽籤、倒數、錄音、練習統計、連續練習天數、成就徽章、收藏、主題類別分析，以及本機的音量／語速／口頭禪分析。

## 上傳方式

新建一個 GitHub repository，例如 `speaking-lottery-pro`。將 **本資料夾內** 的 `index.html`、`style.css`、`app.js` 上傳到 repository 的最外層（不要連同 `speaking-lottery-pro` 資料夾再包一層）。

GitHub Pages 設為 `main` branch / `(root)` 後，網址會是：

`https://owenwuwu.github.io/speaking-lottery-pro/`

## 錄音機制

使用原生 JavaScript 的 `navigator.mediaDevices.getUserMedia()` 取得麥克風，再以 `MediaRecorder` 錄製。錄音檔以瀏覽器的 IndexedDB 儲存在同一裝置，並可下載為音檔。

- 不需安裝軟體、不需要伺服器或 API 金鑰。
- GitHub Pages 的 HTTPS 網址可讓瀏覽器請求麥克風權限。
- 錄音與紀錄不會同步到其他裝置；清除瀏覽器資料會一併移除。

## 口條分析機制

- 使用 Web Audio API 分析錄音期間的音量，提示「音量偏低」或「疑似爆音」。
- 支援 Web Speech API 的瀏覽器會以 `zh-TW` 產生逐字稿，再估算「字／分」與統計「然後、就是、嗯、呃、那個」等口頭禪。
- 逐字稿功能的支援度依瀏覽器而異；建議使用最新版 Chrome。即使逐字稿不可用，錄音與音量分析仍可運作。

這些指標適合追蹤自己的進步，並非正式的發音或語意能力評分。

## 需要 AI 級評分時

若要取得更可靠的中文轉錄、逐句建議或語意結構回饋，可使用 OpenAI Speech-to-Text API；若要評估發音準確度與流暢度，Azure Speech 的 Pronunciation Assessment 是較專門的選項。兩者都必須經由 Cloudflare Worker、Netlify Function 等後端轉送 API 金鑰；不可把金鑰直接寫入 GitHub Pages 的 `app.js`。
