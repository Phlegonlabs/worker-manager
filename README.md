# Worker Manager

Windows 系統匣小工具，用來切換這台電腦目前使用的 Wrangler OAuth Profile。

> An independent desktop profile manager for the Wrangler CLI.
> Not affiliated with or endorsed by Cloudflare.

## 下載

到 [Releases](https://github.com/Phlegonlabs/worker-manager/releases) 下載最新的
`Worker-Manager-<版本>-signed.exe`（單一執行檔，免安裝）。目前為公開測試（beta）階段。

## 需求

- Windows 10 或更新版本（x64）
- 已安裝 Wrangler 4.130.0 以上，終端機執行 `wrangler --version` 有反應
- 至少一個 Wrangler auth Profile（也可以在 App 內新增）

## 功能

- 在系統匣或視窗中一鍵切換全機（目前 Windows 使用者）使用的 Cloudflare 帳號
- 切換後自動以 `wrangler whoami` 驗證，驗證失敗會自動還原原本狀態
- 偵測登入憑證過期，每個 Profile 都可一鍵「重新登入」（包括目前正在使用的）
- 刪除 Profile 前需確認，只移除本機登入與資料夾綁定，不會動 Cloudflare 帳號或雲端資源

## 關於 SmartScreen 警告（重要）

本程式目前使用自簽憑證簽署：

- 簽署者：`CN=Phlegon Labs`
- 憑證指紋：`531F2830B9511437ED4AA5A8B55F1B0228B7AA30`

自簽憑證不在 Windows 內建的受信任發行者清單，第一次執行時 SmartScreen
可能顯示「未知的發行者」。這是自簽憑證的預期行為，不代表檔案被竄改。

下載後請先比對 SHA-256（各 Release 說明頁會公佈）：

```powershell
Get-FileHash .\Worker-Manager-<版本>-signed.exe -Algorithm SHA256
```

與公佈值一致再執行。之後的版本會改用受信任的程式碼簽章憑證。

## 隱私

- 不讀取、不儲存、不上傳 Wrangler OAuth token、Cloudflare API token、密碼或瀏覽器 cookie
- 帳號狀態儲存在 Wrangler 自己的設定檔（`~/.wrangler`），本程式不另外保存任何帳號資料
- 沒有遙測、沒有聯網回報；所有操作都是在本機執行 `wrangler` 命令

## 安全回報

請使用 GitHub 的私密安全性公告（Security → Report a vulnerability）回報，
不要把未修補的安全問題開成公開 issue。詳見 [SECURITY.md](SECURITY.md)。

## 授權

© 2026 Phlegon Labs. All rights reserved.
