# Question of ASK

- [List questions](#list-questions)
- [Get a single question](#get-a-single-question)
- [Update a question](#update-a-question)
- [Remove a question](#remove-a-question)

## List questions
```
GET /console/ask/questions
```

### Auth
- `editor`

### Paging
YES

### Response
```
{
  rows: [
    {
      id
      status
      slug
      type
      persona: {}
      game: {}
      index
      topic
      topic_type
      image
      title
      content
      references: [
        {}
        ...
      ]
      chatroom
      data: {}
      assigned_personas: [
        *personaObject*
        ...
      ]
      persona_speech_targets: [
        *personaSpeechTargetObject*
      ]
      push: {
        count
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

## Get a single question
```
GET /console/ask/questions/:id
```

### Auth
- `editor`

### Paging
NO

### Response

> 與[List questions](#list-questions)中的Question object格式相同

## Update a question
```
PATCH /console/ask/questions/:id
```

### Auth
- `editor`

### Paging
NO

### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `status` | string | 🌑 | 此問題的狀態 |
| `slug` | string | 🌑 | 此問題的短網址 |
| `type` | string | 🌑 | 此問題類型 |
| `persona` | integer: persona ID |
| `game` | integer | 🌕 | 此問題所屬的game ID |
| `index` | integer | 🌑 | 此問題排序 |
| `topic` | integer | 🌕 | 與此問題相關連的topic ID |
| `image` | string | 🌑 | 此問題的封面圖片連結 |
| `title` | string | 🌕 | 此問題的標題 |
| `content` | string | 🌑 | 此問題的內容 |
| `references` | array of strings (JSON) | 🌑 | 此問題的參考資料 |
| `chatroom` | string: chatroom ID |  🌑 | 此問題的聊天室ID |
| `data` | JSON | 🌑 | 此問題的其他資訊 |
| `assigned_personas` | array of integers: persona IDs | 🌑 | 指定回答此問題的persona ID列表 |

### Sample input

```json
{
  "type": "default",
  "game": 1,
  "topic": 1,
  "image": "https://i.waa.tw/gUYUdY.png",
  "title": "青年失業問題該如何解決？",
  "content": "據主計處2017年7月份統計資料20-24歲青年失業率高達14.67%，也就代表每8個年輕人就有1位是屬失業狀態的。人力銀行分析其原因，主要為二：台灣的低薪環境、勞動環境惡劣；若再將30歲以下失業率計算進去，總數超過20萬人，比例已占全台近半失業率，這難道不是政府與企業該重視的警訊嗎？",
  "assigned_personas": [1, 2, 3]
}
```

## Remove a question
```
DELETE /console/ask/questions/:id
```

### Auth
- `editor`

### Paging
NO

### 行為
在`status`欄位標示`removed`

### 相關需要一併標示移除的資源及其關聯欄位

| 相關資源 | 關聯欄位 | 備註 |
| --- | --- | --- |
| `ASK_Question_Assigned_Persona` | `question_id` |
| `ASK_Answer` | `question_id` |
| `Persona_Speech_Target` | `source_entity` & `source_id` | `source_entity`為`ASK_Question`且`source_id`與移除目標的id相符 |
