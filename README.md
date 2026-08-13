# 交接班系統 Handover System

目前為前端 Prototype，支援三班制、部門分流與管理者總覽。

## 線上試用

1. 開啟 Repository 的 **Settings → Pages**。
2. 在 **Build and deployment** 選擇 **Deploy from a branch**。
3. Branch 選 `main`，資料夾選 `/ (root)`，按 **Save**。
4. 等待 GitHub Pages 部署完成後，使用 Pages 網址開啟系統。

## Demo 帳號

| 身分 | 帳號 | 密碼 |
|---|---|---|
| 管理者 | `admin` | `admin123` |
| 倉庫部 | `warehouse` | `1234` |
| 拍賣部 | `auction` | `1234` |
| 物流部 | `logistics` | `1234` |
| 資訊部 | `it` | `1234` |

## 建議測試流程

### 1. 管理者
登入 `admin / admin123`，確認可以看到儀表板、新增交接、交接紀錄與管理者總覽，且管理者能查看全部部門。

### 2. 部門分流
使用 `warehouse / 1234` 新增一筆倉庫部交接；登出後使用 `auction / 1234` 登入，確認看不到倉庫部資料；再使用管理者登入，確認可以看到兩個部門。

### 3. 三班制
分別建立早班、午班、夜班資料，確認紀錄會顯示正確班別。

## 目前資料儲存方式

目前使用瀏覽器 `localStorage`：
- 不同電腦不會共用資料。
- 清除瀏覽器網站資料可能造成資料消失。
- Demo 密碼只是前端測試用，不能作為正式驗證。

## 正式上線前需要補強

- 後端 API 與 SQL 資料庫
- AD / LDAP 或公司帳號登入
- RBAC 權限控制
- HTTPS
- 操作紀錄 / Audit Log
- 備份與還原
- 附件上傳
- 交接確認 / 已讀
- 搜尋、日期篩選與報表
- 管理者帳號與部門管理
- API 與資料庫安全性
