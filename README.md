# 產品專區｜保鮮盒全球供應商・產品頁直連（v2）

🔗 **線上瀏覽**：https://emily77.github.io/freshbox-product-hub/

保鮮盒（food storage container）全球供應商清單，把「找到符合的商品」直接對應到「該公司實際的產品頁面」，不必從官網首頁翻找。

## 內容

- **16 家供應商**（v1 為 13 家，v2 新增 Hotpack、Signoraware、Nayasa）
- **40 條產品頁直連**（v1 為 28 條），逐條確認可開啟
- 分三類可篩選：塑膠 PP（9 家）／耐熱玻璃（7 家）／品牌廠（6 家）
- **中東適配** 1–5 級，可一鍵只看「中東首選／近洋有利」（7 家）
- **即時搜尋**：容量、材質、國家、城市、形狀（例：`500ml`、`玻璃`、`杜拜`、`方形`）
- **★ 候選清單**：勾選後存 localStorage，關掉瀏覽器不會消失，可一鍵複製
- **英文 RFQ 產生器**：每家一鍵產生含產品直連、Jebel Ali 交貨、40HQ 一櫃、LFGB/FDA 要求的詢價信
- **不含價格**（價格洽談走 RFQ）

## 名單結構

| 類別 | 家數 | 供應商 |
|---|---|---|
| 塑膠 PP | 9 | RainHuo 瑞活、Xinghui 星輝、Nanrong 南榮、Joey Plastic、ZJ Aishang、Hotpack（阿聯）、Cello（印）、Pearlpet（印）、Nayasa（印） |
| 耐熱玻璃 | 7 | Feemio 菲米歐、Yeboda 業博達、HJ Glass、Deli Glass 德力、Paşabahçe（土）、Signoraware（印）、Nayasa（印） |
| 品牌廠 | 6 | Borosil（印）、Paşabahçe（土）、Pearlpet（印）、Cello（印）、Signoraware（印）、Nayasa（印） |

> 同一家可同時屬多類（例：Paşabahçe 是玻璃廠也是品牌廠），故類別家數加總大於 16。

### 中東優先序（`me` 值）

| 等級 | 說明 | 家數 |
|---|---|---|
| 5 | 中東首選（在地或自貿區） | 2 |
| 4 | 近洋有利（印度、土耳其，海運 10–20 天） | 5 |
| 3 | 海運較遠（東南亞、華南） | 6 |
| 2 | 需評估 | 3 |

## 連結驗證方式

v2 逐條以 HTTP 請求實測：

```
curl -sL -o NUL -w "%{http_code}" -A "<瀏覽器UA>" <URL>
```

- **27/40 條回 `200`**
- **13 條 Shopify 商店頁回 `429`（Too Many Requests）**：Pearlpet 4 條、Signoraware 5 條、Nayasa 4 條。這是站台對非瀏覽器請求的速率限制，不是連結失效——已用 `web_fetch` 取得頁面內容確認存在（Nayasa 其中 1 條重測回 `200`，證明站台正常）。冷卻 180 秒並拉長間隔至 12–25 秒仍無法繞過（IP 已被標記）。

因此頁面 badge 寫「連結逐條確認可開啟」，footer 說明驗證方式與 429 原因，不宣稱全部 200。

已剔除無法開啟者：`jy-glass.com`（連線逾時 000）、`roetell.com`（Cloudflare 520）、`miltonworld.com`（000）、`zenithindia.com`（000）。

部分條目為**整店產品列表頁**或**分類頁**（Alibaba 2 條、分類 6 條），需再進單品，已在頁面備註標示。

## 檔案

| 檔案 | 說明 |
|---|---|
| `index.html` | 單檔視覺頁（v2，約 29 KB），內嵌 CSS/JS，無外部依賴，可離線開 |
| `index_v1_backup.html` | v1 備份（13 家 / 28 條） |
| `產品直連清單.csv` | 16 家 40 列，欄位：編號、供應商代號、類別、公司、國家/地區、中東適配、品項名稱、容量/規格、產品頁直連URL、備註 |
| `產品專區_預覽.png` | 1400×3600 預覽截圖 |
| `README.md` | 本說明 |

## 更新流程

1. 改 `index.html` 的 `const DATA = [...]`（資料模型：`{id, n, c, t:[類別], me:1-5, note, l:[{t,u,cap}]}`）
2. 驗證：`node --check` 語法、卡片數／連結數／`id` 與 `url` 唯一性
3. 重跑 CSV 產生器（regex 解析 `DATA` 區塊）
4. 複製到 `publish\freshbox-product-hub\index.html`
5. `git add -A && git commit && git push origin main`
6. 等 GitHub Pages 重建（約 40–60 秒），驗證線上回 `200`

## 授權

本清單為供應商公開資料彙整，僅供採購評估參考。各產品頁內容與商標權利屬原公司所有。
