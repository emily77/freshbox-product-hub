# 產品專區｜保鮮盒全球供應商・產品頁直連

🔗 **線上瀏覽**：https://emily77.github.io/freshbox-product-hub/

保鮮盒（food storage container）全球供應商清單，把「找到符合的商品」直接對應到「該公司實際的產品頁面」，不必從官網首頁翻找。

## 內容

- **13 家供應商**
- **28 條產品頁直連**，全部以 HTTP 請求實測回應 `200`
- 分三類可篩選：塑膠 PP／耐熱玻璃／品牌廠
- **不含價格**（價格洽談走 RFQ）

## 名單結構

| 類別 | 家數 | 供應商 |
|---|---|---|
| 塑膠 PP | 5 | RainHuo 瑞活、Xinghui 星輝、Nanrong 南榮、Joey Plastic、ZJ Aishang |
| 耐熱玻璃 | 4 | Feemio 菲米歐、Yeboda 業博達、HJ Glass、Deli Glass 德力 |
| 品牌廠 | 4 | Borosil（印）、Paşabahçe（土）、Pearlpet（印）、Cello（印） |

## 連結驗證

全部 28 條實測：

```
curl -sL -o NUL -w "%{http_code}" -A "<瀏覽器UA>" <URL>
```

已剔除無法開啟者：`jy-glass.com`（連線逾時 000）、`roetell.com`（Cloudflare 520）。

部分條目為**整店產品列表頁**或**分類頁**（Alibaba 2 條、分類 4 條），需再進單品，已在頁面備註標示。

## 檔案

| 檔案 | 說明 |
|---|---|
| `index.html` | 單檔視覺頁，內嵌 CSS/JS，無外部依賴，可離線開 |

## 授權

本清單為供應商公開資料彙整，僅供採購評估參考。各產品頁內容與商標權利屬原公司所有。
