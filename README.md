# 交接班系統 Handover System

目前已由前端 Prototype 升級為「前端 + Node.js API + SQLite 資料庫」架構。

## 已完成

- 早班／午班／夜班
- 倉庫部、拍賣部、物流部、資訊部
- 一般人員只能查看自己的部門
- 系統管理者可查看全部部門
- 每部門 1 名經理＋2 名職員
- 人員姓名與職稱
- 新增交接時指定接班人
- 交接資料寫入 SQLite，不再使用 localStorage
- 指定接班人產生持久化通知
- 右上角 🔔 未讀通知數量
- 通知已讀狀態會寫入資料庫
- JWT 登入驗證
- 密碼使用 bcrypt 雜湊儲存

## Demo 帳號

管理者：`admin / admin123`

倉庫部：
- `warehouse_mgr / 1234` 王志明／經理
- `warehouse_1 / 1234` 陳建宏／職員
- `warehouse_2 / 1234` 林冠廷／職員

拍賣部：
- `auction_mgr / 1234` 李明哲／經理
- `auction_1 / 1234` 張育誠／職員
- `auction_2 / 1234` 黃俊豪／職員

物流部：
- `logistics_mgr / 1234` 林志宏／經理
- `logistics_1 / 1234` 吳承翰／職員
- `logistics_2 / 1234` 許家豪／職員

資訊部：
- `it_mgr / 1234` 周文傑／經理
- `it_1 / 1234` 鄭宇翔／職員
- `it_2 / 1234` 郭冠廷／職員

## 本機試用

需要先安裝 Node.js。

在 Repository 根目錄執行：

```bash
npm install
npm start
```

看到：

```text
Handover System API running on http://localhost:3000
```

再用瀏覽器開啟：

```text
http://localhost:3000
```

### 測試通知

1. 使用 `warehouse_mgr / 1234` 登入。
2. 新增一筆「早班」交接。
3. 「交接給」選擇陳建宏。
4. 登出。
5. 使用 `warehouse_1 / 1234` 登入。
6. 右上角 🔔 應出現未讀通知。
7. 點擊通知後，通知會標記為已讀。
8. 再重新整理或重新登入，通知狀態仍由資料庫保留。

### 測試跨部門權限

使用 `warehouse_1 / 1234` 登入，只能看到倉庫部資料。

使用 `admin / admin123` 登入，可以看到四個部門全部交接資料。

## 重要：GitHub Pages

目前 GitHub Pages 只能提供靜態前端，無法直接執行 `server.js` 與 SQLite。因此升級後的正式版本不能只靠 GitHub Pages。

正式上線需要把 Node.js API 與 SQLite 放到可以執行 Node.js 的伺服器，例如公司內部 Windows/Linux Server 或雲端服務，再讓瀏覽器連線到 API。

建議正式環境至少使用：

- HTTPS
- `JWT_SECRET` 環境變數
- 資料庫定期備份
- 公司網路／VPN 或防火牆限制
- 正式帳號與強密碼
- AD/LDAP 整合（下一階段）

## 下一階段

1. 公司 AD / LDAP 登入
2. 管理者人員管理
3. 部門與職稱管理
4. 交接確認／已讀
5. 搜尋、日期與班別篩選
6. 附件上傳
7. 操作 Audit Log
8. 資料庫備份與還原
9. HTTPS 與正式部署
