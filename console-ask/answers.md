# Answer of ASK

- [List answers](#list-answers)
- [Get a single answer](#get-a-single-answer)
- [Create an answer](#create-an-answer)
- [Update an answer](#update-an-answer)

## List answers
```
GET /console/ask/answers
```

### Auth
NO

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
      persona: {}
      question: {}
      index
      image
      content
      references: []
      data: {}
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

## Get a single answer
```
GET /console/ask/answers/:id
```

### Auth
NO

### Paging
NO

### Response
> 與[List answers](#list-answers)中的Answer object格式相同

## Create an answer
```
POST /console/ask/answers
```

### Auth
- `editor`

### Paging
NO

### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `status` | string | 🌑 | 此答案的狀態 |
| `slug` | string | 🌑 | 此答案的短網址 |
| `persona` | integer: persona ID | 🌕 | 回答此答案的 Persona ID |
| `question` | integer: question ID | 🌕 | 此答案所屬的問題 ID |
| `index` | integer | 🌑 | 此答案排序 |
| `image` | string | 🌑 | 此答案的封面圖片連結 |
| `content` | string | 🌕 | 此答案的內容 |
| `references` | array of objects (JSON) | 🌑 | 此答案的參考資料 |
| `data` | JSON | 🌑 | 此答案的其他資訊 |

## Update an answer
```
PATCH /console/ask/answers/:id
```

### Auth
- `editor`

### Paging
NO

> 參考 [Create an answer](#create-an-answer)
