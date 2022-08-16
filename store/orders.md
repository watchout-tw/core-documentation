# Orders

- [List plan orders](#list-period-orders)
- [List physical-product orders](#list-physical-product-orders)
- [Get an order by id](#get-an-order-by-id)
- [Create an order](#create-an-order)
- [Get all active CSV list](#get-all-active-CSV-list)
- [Get address CSV list](#get-address-CSV-list)

## List plan orders
```
GET /store/orders?type=plan
```

### Auth
- “editor”

### Paging
YES

### Available query parameters
YES

### Response
```
{
  rows: [
    {
      id
      merchant_trade_no
      order_status
      merchandise
      customer_email
      done_exec_times
      exec_times
      merchant_trade_date
    }
    ...
  ]
}
```

## List physical product orders
```
GET /store/orders?type=physical-product
```

### Auth
- “editor”

### Paging
YES

### Available query parameters
YES

### Response
```
{
  rows: [
    {
      id
      merchant_trade_no
      order_status
      merchandise
      price
      customer_email
      merchant_trade_date
    }
    ...
  ]
}
```

## Get an order by id
```
GET /store/orders/:id
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
| `order_status` | string | 訂單狀態 | active |
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
| `notes` | string | 訂單備註 |
| `commodity_id` | string | 大宗單號 |
| `remarks` | string | 行政使用的訂單註記 |

## Create an order
```
POST /store/orders
```

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

## Get all active CSV list

取得目前仍有定期定額名單的 CSV，提供草報寄送
```
GET /store/orders?order_status=active
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
GET /store/orders/address
```

### Paging
NO

### Available query parameters

| Key | Type | Required | Description |
| `start_date` | string | 🌑 | 起始時間 |
| `end_date` | string | 🌑 | 結束時間 |

*如果沒有設定，預設回傳近一週的名單*

### Response
```
customer_name,customer_addr,customer_phone
```
