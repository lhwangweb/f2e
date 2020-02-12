# F2E 實作

## 執行方式

### 方法一 
   - 直接以瀏覽器開啟 index.html 瀏覽即可。

### 方法二
   - 將 index.html 放置到任何 web 伺服器上，並以瀏覽器存取此檔案對應之 URI。

### Test Case

   - 如需調整測試案例，請修改 function get_orders_by_api 內的回傳值，如下範例，變更 orders 的內容：

```javascript
function get_orders_by_api() {
   // 請自行修改 orders 內容，填上相同格式的 Data
   return {
         orders: [ ... 訂單資料陣列 ... ]
   };
}
```

## 程式說明

### 訂單畫面產生流程

   - 以 init_page() 來做整個頁面的初始化， init_page 工作如下：

      1. 取得 API 資料 (這裡用一個 function return 靜態資料來模擬)

      2. 整理資料

         (1) 分類為『進行中』、『已完成』

         (2) 分別用日期排序(DESC)，用 javascript sort() 進行，如果日期解析失敗則順序不動。

      3. 分別根據『進行中』、『已完成』兩份資料，建立 HTML，並填充到版面上的對應區塊

         - 這裡僅簡單的用字串連接與 jQuery 的 append 來進行

   - 以 jQuery 的 $(document).ready() 執行 init_page() 

### 畫面建構

1. 使用 Bootstrap 進行版面建構，以 Bootstrap Card 為基底。
2. 有簡單的 RWD，以 576px 為界。
3. 大於 576px 時，品名有簡單進行字數行數的限制，超過兩行會裁切並附上英文句點，以 CSS 實作。
