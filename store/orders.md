# Orders

- [List plan orders](#list-period-orders)
- [List physical-product orders](#list-physical-product-orders)
- [Get an order by id](#get-an-order-by-id)
- [Create an order](#create-an-order)
- [Update an order](#update-an-order)
- [Get all active CSV list](#get-all-active-CSV-list)
- [Get address CSV list](#get-address-CSV-list)
- [Get allow marketing CSV list](#get-allow-marketing-CSV-list)

## List plan orders
```
GET /store/orders?type=plan
```

### Auth
- “editor”

### Paging
YES

### Available query parameters
| Key | Type | Description | Sample |
| --- | --- | :---: | --- |
| `merchandise_id` | integer | 商品編號 | 1 |
| `merchant_trade_no` | string | 訂單編號 | 00000001655428912135 |
| `customer_email` | string | 訂購人 Email | abc@gmail.com |
| `order_status` | string | 訂單狀態，`active` 或 `inactive` 兩種 | `active`、`inactive` |
| `expire_in_six_month` | tinyint | 是否於六個月內到期 | `0` 或 `1` |
| `page` | integer | 分頁編號 | 1, 2, 3... |

### Response
```
{
  rows: [
    {
      id
      merchant_trade_no
      order_status
      merchandise_name
      customer_email
      total_success_times
      exec_times
      last_process_date
      last_process_status
      merchant_trade_date
    }
    ...
  ]
}
```

| Key | Type | Description | Sample |
| --- | --- | :---: | --- |
| `id` | integer | 資料庫 ID | 13 |
| `merchant_trade_no` | string | 定期定額訂單編號 | 00000001655428912135 |
| `order_status` | string | 訂單狀態 | `active`、`inactive` |
| `merchantdise_name` | string | 定期定額方案名稱 | 定期定額-519 |
| `customer_email` | string | 訂購人 Email | abc@gmail.com |
| `total_success_times` | string | 已執行成功次數 | 5 |
| `exec_times` | string | 執行次數 | 99 |
| `last_process_date` | string | 最後一次刷卡執行日期 | 2022/06/17 01:21:52 |
| `last_process_status` | string | 最後一次刷卡執行成功與否 | `success`, `Pay Fail.` |
| `merchant_trade_date` | string | 訂單成立時間 | 2022/06/17 01:21:52 |

## List physical product orders
```
GET /store/orders?type=physical-product
```

### Auth
- “editor”

### Paging
YES

### Available query parameters
| Key | Type | Description | Sample |
| --- | --- | :---: | --- |
| `merchandise_id` | integer | 商品編號 | 1 |
| `merchant_trade_no` | string | 訂單編號 | 00000001655428912135 |
| `customer_email` | string | 訂購人 Email | abc@gmail.com |
| `allow_marketing` | tinyint | 是否願意收到行銷資訊 | `0` 或 `1` |
| `page` | integer | 分頁編號 | 1, 2, 3... |

### Response
```
{
  rows: [
    {
      id
      merchant_trade_no
      merchandise_name
      price
      customer_email
      allow_marketing
      merchant_trade_date
    }
    ...
  ]
}
```

| Key | Type | Description | Sample |
| --- | --- | :---: | --- |
| `id` | integer | 資料庫 ID | 13 |
| `merchant_trade_no` | string | 商品訂單編號 | 00000001655428912135 |
| `merchantdise_name` | string | 商品名稱 | 公民行動指南 |
| `price` | integer | 價格 | 350 |
| `customer_email` | string | 訂購人 Email | abc@gmail.com |
| `allow_marketing` | tinyint | 是否願意收到行銷資訊 | `0` 或 `1` |
| `merchant_trade_date` | string | 訂單成立時間 | 2022/06/17 01:21:52 |

## Get an order by merchant trade No.
```
GET /store/orders/:tradeNo
```
*定期定額或實體商品皆可*

### Auth
- “editor”

### Paging
NO

### Response
```
{
  id
  merchant_trade_no
  payment_status
  order_status
  merchant_trade_date
  exec_times
  frequency
  period_type
  customer_company
  customer_identifier
  customer_name
  customer_nickname
  customer_phone
  customer_email
  customer_addr
  invoice_type
  invoice_code
  notes
}
```

| Key | Type | Description | Sample |
| --- | --- | :---: | --- |
| `id` | integer | 資料庫 ID | 13 |
| `merchant_trade_no` | string | 定期定額訂單編號 | 00000001655428912135 |
| `order_status` | string | 訂單狀態（定期定額訂單用），`active` 或 `inactive` 兩種 | active |
| `merchant_trade_date` | string | 訂單成立時間 | 2022/06/17 01:21:52 |
| `exec_times` | string | 執行次數 | 99 |
| `frequency` | string | 執行頻率 | 1 |
| `period_type` | string | 單位間隔 | M |
| `customer_company` | string | 訂購人公司 | 沃草有限公司 |
| `customer_identifier` | string | 訂購人公司統編 | 54648398 |
| `customer_name` | string | 訂購人姓名 | 洪國鈞 |
| `customer_nickname` | string | 訂購人暱稱 | ㄇㄇ |
| `customer_phone` | string | 訂購人電話 | 0983737383 |
| `customer_email` | string | 訂購人 Email | abc@gmail.com |
| `customer_addr` | string | 訂購人地址 | 110台北市懷寧街 |
| `invoice_type` | string | 發票類型 | `identifier`、`donation`、`memberCarruer`、`cellphoneCarruer` |
| `invoice_code` | string | 發票編號 | 可為載具編號、愛心碼編號 |
| `notes` | string | 訂單備註 | 平常可能沒人在家 |
| `commodity_id` | string | 大宗單號（商品訂單用） | LGN-097 |
| `allow_marketing` | tinyint | 是否願意收到行銷資訊（商品訂單用） | `0` 或 `1` |
| `remarks` | string | 行政使用的訂單註記 | 出貨但無人接應 |
| `total_success_times` | string | 累計刷卡成功次數（定期定額訂單用） | 5 |
| `last_process_date` | string | 最後一次刷卡執行日期 | 2022/06/17 01:21:52 |
| `last_process_status` | string | 最後一次刷卡執行成功與否 | `success`、`Pay Fail.` |

## Create an order
```
POST /store/orders
```
*定期定額或實體商品皆可*

### Auth
- “editor”

### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `merchandise` | string | 🌕 | 定期定額方案的短網址 (slug), 請見 /store/merchandises |
| `merchandiseType` | string | 🌕 | 定期定額方案的類型 (type), 請見 /store/merchandises |
| `customPrice` | string | 🌑 | 由訂購人自行輸入的定期定額金額，merchandise 為 `support-custom` 時使用  |
| `customerCompany` | string | 🌑 | 訂購人公司 |
| `customerName` | string | 🌑 | 訂購人姓名 |
| `customerNickname` | string | 🌑 | 訂購人暱稱 |
| `customerCountryCode` | string | 🌕 | 訂購人電話國碼 |
| `customerPhone` | string | 🌕 | 訂購人電話 |
| `customerZipcode` | string | 🌑 | 訂購人地址郵遞區號（三碼） |
| `customerCity` | string | 🌑 | 訂購人地址（城市） |
| `customerDistrict` | string | 🌑 | 訂購人地址（區域） |
| `customerStreet` | string | 🌑 | 訂購人地址（街道） |
| `customerEmail` | string | 🌕 | 訂購人 Email |
| `confirmEmail` | string | 🌕 | 再次確認訂購人 Email |
| `invoiceOption` | string | 🌑 | 發票類型，可為 `donation`、`memberCarruer`、`cellphoneCarruer` |
| `carruerNum` | string | 🌑 | 手機載具編號，`invoiceOption` 為 `cellphoneCarruer` 時使用 |
| `loveCode` | string | 🌑 | 愛心碼編號，`invoiceOption` 為 `donation` 時使用 |
| `customerIdentifier` | string | 🌑 | 公司統編，`invoiceOption` 為 `identifier` 時使用 |
| `allowMarketing` | boolean | 🌕 | 是否願意收到行銷資訊 |
| `notes` | string | 🌑 | 訂購人填寫的備註 |

### Special Rules

- 當填入 `customeCompany` 及 `customerIdentifier` 時，則不需填入 `invoiceOption`
- `customerName` 與 `customerNickname` 須擇一填入
- 當 `invoiceOption` 為 `cellphoneCarruer` 時，需填入 `carruerNum`
- 當 `invoiceOption` 為 `donation` 時，需填入 `loveCode`

### Response
> 由綠界 SDK 提供的刷卡頁面 (HTML string)

## Update an order
```
PATCH /store/orders/:tradeNo
```
*定期定額或實體商品皆可*

### Auth
- “editor”

### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `id` | integer | 🌕 | 資料庫 ID，Ex: `13` |
| `merchant_trade_no` | string | 🌕 | 定期定額訂單編號，Ex: `00000001655428912135` |
| `order_status` | string | 🌑 | 訂單狀態（定期定額使用），可為 `active` 或 `inactive` |
| `commodity_id` | string | 🌑 | 大宗單號（單筆訂單使用） |
| `remarks` | string | 🌑 | 行政使用的訂單註記 |
| `allow_marketing` | tinyint | 🌑 | 是否願意收到行銷資訊（單筆訂單使用），可為 `0` 或 `1` |

### Sample input
```json
{
  "id": 13,
  "merchant_trade_no": "00000001655428912135",
  "order_status": "inactive"
}
{
  "id": 13,
  "merchant_trade_no": "00000001655428912135",
  "commodity_id": "KMI-0038495",
  "remarks": "已被退回第二次",
  "allow_marketing": 0
}
```

## List transaction records of an order
```
GET /store/orders/:tradeNo/transactions
```

### Auth
- “editor”

### Paging
NO

### Available query parameters
NO

### Response
```
{
  rows: [
    id,
    merchant_trade_no,
    amount,
    auth_code,
    exec_times,
    first_auth_amount,
    frequency,
    gwsr,
    period_type,
    process_date,
    rtn_code,
    rtn_msg,
    store_id,
    total_success_times,
    custom_field_1,
    custom_field_2,
    custom_field_3,
    custom_field_4
    ...
  ]
}
```

| Key | Type | Description | Sample |
| --- | --- | :---: | --- |
| `id` | integer | 資料庫 ID | 13 |
| `merchant_trade_no` | string | 定期定額訂單編號 | 00000001655428912135 |
| `amount` | integer | 本次交易金額 | 300 |
| `auth_code` | string | 綠界的驗證碼 | 930303 |
| `exec_times` | string | 執行次數 | 99 |
| `first_auth_amount` | string | 本定期定額訂單，首次刷卡交易金額 | 300 |
| `frequency` | string | 執行頻率 | 1 |
| `gwsr` | string | 綠界的授權交易單號 | 85520066 |
| `period_type` | string | 單位間隔 | M |
| `process_date` | string | 本交易執行時間 | 2022-08-15T02:29:17.000Z |
| `rtn_code` | string | 交易結果代碼，`1`為成功，其餘皆為失敗 | 1 |
| `rtn_msg` | string | 交易結果訊息 | `success`, `Pay Fail.`  |
| `store_id` | string | 綠界特約商店編號（無使用） | 無範例 |
| `total_success_times` | string | 累計刷卡成功次數 | 5 |
| `custom_field_1` | string | 綠界客製化欄位（無使用） | 無範例 |
| `custom_field_2` | string | 綠界客製化欄位（無使用） | 無範例 |
| `custom_field_3` | string | 綠界客製化欄位（無使用） | 無範例 |
| `custom_field_4` | string | 綠界客製化欄位（無使用） | 無範例 |

## Get all active CSV list

取得目前仍有定期定額名單的 CSV，提供草報寄送
```
GET /store/orders/csv/newsletter
```

### Auth
- “editor”

### Paging
NO

### Available query parameters
NO

### Response
```
customer_nickname,customer_email
```

## Get address CSV list
```
GET /store/orders/csv/address
```

### Paging
NO

### Available query parameters
| Key | Type | Required | Description | Example |
| --- | --- | :---: | --- | --- |
| `start_date` | string | 🌑 | 起始時間 | 2022-05-01 |
| `end_date` | string | 🌑 | 結束時間 | 2022-06-01 |

*如果沒有設定，預設回傳近一週的名單*

### Response
```
customer_name,customer_addr,customer_phone
```

## Get allow marketing CSV list

從單筆購買的訂單中，取得同意接收行銷資訊名單的 CSV
```
GET /store/orders/csv/allowMarketing
```

### Auth
- “editor”

### Paging
NO

### Available query parameters
NO

### Response
```
customer_nickname,customer_email
```
