# 交接班與巡檢作業平台 Handover System

目前系統已升級為「入口平台 + 交接班 + 巡檢 + 系統管理」架構。

## 入口架構

登入後會依帳號權限看到：

- 交接班系統：所有啟用帳號可使用
- 巡檢系統：只有被授予「巡檢系統」權限的人員可使用；系統管理者可使用
- 系統管理：只有系統管理者可使用

「人員與權限」已整合到「系統管理」，後續系統設定可繼續放入這個模組。

## 巡檢系統

- 依使用者部門顯示可巡檢設備
- 每次巡檢照片必填
- 支援手機相機 `capture="environment"`
- Server 記錄巡檢完成時間
- 可選擇取得 GPS 座標
- 正常／異常結果
- 異常說明
- 巡檢照片存於 `inspection_uploads/`
- 系統管理員可建立、修改、停用巡檢點
- 巡檢記錄可查看最近紀錄

## 系統管理

- 人員新增、編輯、停用
- 部門與職務名稱可直接輸入，不受預設清單限制
- 系統管理者／一般使用者
- 巡檢系統權限
- 本日貢獻度權限
- 市場行情權限
- Excel 批次匯入人員
- 新匯入人員初始密碼：`1234`
- 使用者可自行修改密碼
- 巡檢點設定

## Excel 匯入欄位

第一個工作表需包含：

```text
部門名稱
員工工號(帳號)
中文姓名
職務名稱
```

新匯入人員預設：

```text
系統權限：一般使用者
狀態：啟用
巡檢系統：關閉
本日貢獻度：關閉
市場行情：關閉
密碼：1234
```

工號若已存在會略過，不覆蓋既有帳號。

## 本機啟動

需要 Node.js 22 以上。

在 Repository 根目錄執行：

```bash
npm install
npm start
```

現在啟動的是 `gateway.js`，顯示：

```text
Handover Gateway running on http://localhost:3000
```

瀏覽器使用：

```text
http://localhost:3000
```

Gateway 會自動啟動原本的 `server.js` 於內部埠 `3001`，使用者不需直接連到 3001。

## 資料位置

SQLite：

```text
handover.db
```

巡檢照片：

```text
inspection_uploads/
```

兩者都應納入正式環境備份，但不應提交到 GitHub。

## 建議正式上線前

- HTTPS
- `JWT_SECRET` 環境變數
- 正式管理者密碼
- Windows Service / PM2
- SQLite 自動備份；中長期可評估 SQL Server / PostgreSQL
- Audit Log
- 公司 AD / LDAP
- 監控與告警
- 內網 DNS
- 防火牆規則
