# 交接班系統 (handover-system)

一個可直接以 GitHub Pages 展示的交接班系統原型。

## 功能

- 早班、午班、夜班
- 部門分流：倉庫部、拍賣部、物流部、資訊部
- 一般使用者只看自己的部門
- 管理者可查看全部部門
- 新增交接、待辦事項、異常/注意事項
- 交接紀錄查詢
- Dashboard 統計
- Responsive 行動裝置介面
- 目前使用 localStorage 作為 Demo 資料儲存

## Demo 帳號

| 身分 | 帳號 | 密碼 |
|---|---|---|
| 管理者 | admin | admin123 |
| 倉庫部 | warehouse | 1234 |
| 拍賣部 | auction | 1234 |
| 物流部 | logistics | 1234 |
| 資訊部 | it | 1234 |

> 注意：目前帳密與資料儲存在前端，僅適合 Demo/原型展示。正式上線前應改成後端 API、資料庫與正式身分驗證。

## GitHub Pages

Repository → Settings → Pages → Deploy from a branch → `main` / `/ (root)`。

啟用後即可使用 GitHub Pages 網址開啟系統。