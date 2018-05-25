# Topic

- [List topics](#list-topics)
- [Create a topic](#create-a-topic)

## List topics
```
GET /console/park/topics
```

### Auth
- “editor”

### Paging
NO

### Response
```
{
  rows: [
    {
      id
      status
      slug
      type
      index
      image
      title
      description
      data: {}
    }
    ...
  ]
  totalRowCount
}
```

## Create a topic
```
POST /console/park/topics
```

### Auth
YES
- “editor”

### Paging
NO

### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `status` | String | 🌕 | 此議題的狀態 |
| `slug` | String | 🌕 | 此議題的短網址 |
| `type` | String | 🌕 | 此議題的類型 |
| `index` | Integer | 🌑 | 此議題的順序 |
| `image` | String | 🌑 | 此議題的封面圖片連結 |
| `title` | String | 🌕 | 此議題的標題 |
| `description` | Stirng | 🌑 | 此議題的敘述 |
| `data` | JSON | 🌑 | 此議題的其他資訊 |

### Sample input
```json
{
  "status": "regular",
  "slug": "china-relations",
  "type": "presidential",
  "index": 1,
  "image": "https://i.waa.tw/gUYUdY.png",
  "title": "兩岸關係",
  "description": "據主計處2017年7月份統計資料20-24歲青年失業率高達14.67%，也就代表每8個年輕人就有1位是屬失業狀態的。人力銀行分析其原因，主要為二：台灣的低薪環境、勞動環境惡劣；若再將30歲以下失業率計算進去，總數超過20萬人，比例已占全台近半失業率，這難道不是政府與企業該重視的警訊嗎？",
  "data": {
    "tagline": "兩岸一家親？？？",
    "keywords": ["兩岸", "習近平", "兩岸關係"]
  }
}
```
