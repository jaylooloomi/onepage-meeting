# One Page Meeting Assistant

單頁版會議助理工具，整合以下流程：

- 語音即時辨識 (Web Speech API)
- 音檔導入與轉錄 (Gemini)
- 自訂提示語 (Prompt) 管理
- 會議紀錄整理產生 (Gemini)
- 匯出 Markdown (`.md`) 檔

介面語系以繁體中文為主，支援 `zh-TW`、`en-US`、`ja-JP` 語音辨識。

## 功能特色

- 單一 HTML 檔即可執行，不需前後端框架
- 一鍵開始/停止錄音，文字即時回填到輸入區
- 支援上傳音檔 (`audio/*`，大小上限 25MB) 進行逐字轉錄
- 可新增、切換、刪除常用提示語卡片
- 依提示語將會議內容整理成 Markdown 結果
- 直接下載會議整理結果為 `.md` 檔案

## 檔案結構

```text
.
├── onepage-meeting.html
└── README.md
```

## 快速開始

1. 開啟 `onepage-meeting.html`。
2. 設定 API Key：
	- 在 `onepage-meeting.html` 內找到：
	  - `const apiKey = "";`
	- 填入可用的 Google AI Studio / Gemini API Key。
3. 重新整理頁面後開始使用。

## 使用流程

1. 在「語音和音檔輸入」區塊：
	- 點 `開始錄音`，即時把語音轉成文字。
	- 或點 `導入音檔` 上傳 `.mp3/.wav` 等音訊檔轉錄。
2. 在「自訂提示語」區塊：
	- 編輯當前提示語，或用 `+` 新增常用提示語。
3. 點 `生成會議記錄`：
	- 以會議內容 + 提示語呼叫 Gemini 產生 Markdown。
4. 點 `下載 .md 檔案`：
	- 匯出結果檔案，檔名格式：`Meeting_Notes_YYYY-MM-DD.md`。

## 技術說明

- 前端：原生 HTML/CSS/JavaScript
- 語音辨識：`SpeechRecognition / webkitSpeechRecognition`
- 生成模型：`gemini-2.5-flash-preview-09-2025`
- API：`generateContent` (`v1beta`)

## 注意事項

- 錄音功能依賴瀏覽器對 Web Speech API 的支援。
- 部分瀏覽器可能不支援即時語音辨識。
- API Key 請勿提交到公開版本庫，建議改為部署時注入。
- 音檔處理目前限制 25MB 以內。

## 待優化方向

- 將 API Key 改為環境變數或後端代理，避免前端明碼
- 加入 Prompt/內容本機儲存
- 增加多格式輸出 (TXT, DOCX)
- 強化錯誤訊息與重試提示
