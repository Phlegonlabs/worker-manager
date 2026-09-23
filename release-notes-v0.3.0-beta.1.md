第一個公開測試版本。

## 主要內容

- 系統匣一鍵切換全機 Wrangler Profile，切換後自動驗證帳號，失敗自動還原
- 偵測 OAuth 登入過期（不會再誤判成網路問題），每個 Profile 都能「重新登入」，包括目前正在使用的
- 重新開啟視窗時自動重新驗證，不會顯示過期的舊狀態
- 刪除 Profile 需明確確認，只清除本機登入與綁定，不影響 Cloudflare 帳號或雲端資源

## 已知問題

- 使用自簽憑證（`CN=Phlegon Labs`，指紋 `531F2830B9511437ED4AA5A8B55F1B0228B7AA30`），第一次執行時 SmartScreen 會警告未知發行者。請先比對下方 SHA-256 再執行。
- 依賴 Wrangler 實驗性的 auth Profiles 功能；若未來 Wrangler 輸出格式改變，程式會明確報錯，不會猜測或誤動作。
- 目前只有 portable EXE，沒有自動更新，更新請手動下載新版。

## SHA-256

`Worker-Manager-0.3.0-beta.1-signed.exe`

```
BEE64DC20879733CBB2B4596B711B52634F344F4AB0020499818A32AC5E52A6D
```

## 系統需求

- Windows 10 或更新版本（x64）
- Wrangler 4.130.0 以上（終端機執行 `wrangler --version` 可用）

## 安裝與移除

下載 exe 直接執行即可；關閉視窗會縮到系統匣，要結束請用系統匣選單的「結束」。
移除＝刪掉 exe（Wrangler 的設定與登入不受影響）。
