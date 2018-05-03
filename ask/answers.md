# Answer of ASK

- [List answers](#list-answers)
- [Get a single answer](#get-a-single-answer)
- [Create an answer](#create-an-answer)
- [Review an answer](#review-an-answer)

## List answers
```
GET /ask/answers
```

### Auth
NO
> `persona_speeches`需要是“citizen” AND “self”

### Paging
YES

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `game` | string | 用原始問題的game過濾答案清單 | exact | `2018-taipei` |
| `q` | string | 用關鍵字過濾答案清單 `[1]` | exact | `殭屍` |
| `topics` | array of integers: topic IDs | 用原始問題的議題過濾答案清單 | 任一即可 | `[1, 2, 3]` |
| `personas` | array of integers: persona IDs | 用回答者的persona過濾答案清單 | 任一即可 | `[1, 2, 3]` |
| `me_reviewed` | integer | 是否有被active_persona評分？ | exact | `0` OR `1` |
| `order_by` | string `[2]` | 答案排序 | exact | `date` |

`[1]`
> 搜尋範圍：`ASK_Answer.content`, `ASK_Answer.references`

`[2]`
> 可能的string：`date`、`review_count`、`review_average`

### Response
```
{
  rows: [
    {
      id
      status
      slug
      persona: {
        id
        data
        name
        type
        title
        avatar: {
          id
          type
        }
        status
        end_date
        start_date
        game_summary: {
          answer_score_average // [1]
        }
      }
      question: {}
      index
      image
      content
      references: []
      data: {}
      persona_speech_targets: [ // [2]
        {
          id
          type
          source_entity
          source_id
          sp_type
          sp_per_persona
          start_date
          end_date
          data: {}
        }
        ...
      ]
      persona_speeches: [ // [3]
        {
          id
          target_id
          date
          type
          content
          data: {}
        }
        ...
      ]
      review: {
        count // [4]
        average // [5]
      }
    }
    ...
  ]
  totalRowCount
  paging: {
    page
    pages
    pageSize
    previous
    next
  }
}
```

`[1]`
> 回答這個答案的候選人，在所有他回答過的問題中，分數的平均值。Ex: xxx 回答過 3 個問題得到 4.9, 3, 2，answer_score_average = (4.9+3+2)/3

`[2]`
> 以這個 A 為 source 的 Persona_Speech_Target 列表

`[3]`
> **以目前 active persona 為發言人**，以`[1]`所列任一 Persona_Speech_Target 為 target 的Persona_Speech 列表；權限不足則無此項目

`[4]`
> 所有以`[2]`所列 target 中任一為 target，且 type 為 ask_answer_review的Persona_Speech 數目

`[5]`
> `[4]`所列的 Persona_Speech 取 content 平均值，也就是這個 A 的平均評分

## Get a single answer
```
GET /ask/answers/:id
```

### Auth
NO
> `persona_speeches`需要是“citizen” AND “self”；權限不足則無此項目

### Paging
NO

### Response
> 與[List answers](#list-answers)中的Answer object格式相同

## Create an answer
```
POST /ask/answers
```

### Auth
YES
- `citizen` && `guest` `[1]`

### Paging
NO

### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `question` | integer | 🌕 | 此答案所屬的 question ID |
| `image` | string | 🌑 | 此答案的封面圖片連結 |
| `content` | string | 🌕 | 此答案的內容 |
| `references` | JSON | 🌑 | 此問題的參考資料 |
| `data` | JSON | 🌑 | 此問題的其他資訊 |

### Sample input
```json
{
  "question": 1,
  "image": "https://i.waa.tw/gUYUdY.png",
  "content": "據主計處2017年7月份統計資料20-24歲青年失業率高達14.67%，也就代表每8個年輕人就有1位是屬失業狀態的。人力銀行分析其原因，主要為二：台灣的低薪環境、勞動環境惡劣；若再將30歲以下失業率計算進去，總數超過20萬人，比例已占全台近半失業率，這難道不是政府與企業該重視的警訊嗎？",
  "references": {},
  "data": {}
}
```

`[1]`
> 所有是這個Game的player的persona都可以回答此問題

## Review an answer
```
POST /ask/answers/:id/review
```

### Auth
- `citizen` AND `with_info`

### Paging
NO

### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `rate` | integer | 🌕 | 我對此答案的評分 |

### Response

> 與[Get a single answer](#get-a-single-answer)中的 Answer object 格式相同

#### Speech target missing
``` json
{
  "statusCode": 400,
  "error": "Bad Request",
  "message": "SPEECH_TARGET_MISSING"
}
```
#### Review limit exceeded
``` json
{
  "statusCode": 400,
  "error": "Bad Request",
  "message": "REVIEW_LIMIT_EXCEEDED"
}
```
