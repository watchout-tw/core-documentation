# Answer of ASK

- [List answers](#list-answers)
- [Get a single answer](#get-a-single-answer)

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
| --- | --- | --- | --- | --- | --- |
| `game` | string | 用原始問題的game過濾答案清單 | exact | `2018-taipei` |
| `q` | string | 用關鍵字過濾答案清單 `[1]` | exact | `殭屍` |
| `topics` | array of integers: topic IDs | 用原始問題的議題過濾答案清單 | 任一即可 | `[1, 2, 3]` |
| `personas` | array of integers: persona IDs | 用回答者的persona過濾答案清單 | 任一即可 | `[1, 2, 3]` |
| `have_reviewed` | integer | 用「是否已評分」過濾答案清單 | exact | `0` OR `1` |
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
      persona: {}
      question: {}
      index
      image
      content
      references: []
      data: {}
      persona_speech_targets: [ // [1]
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
      persona_speeches: [ // [2]
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
        count // [3]
        average // [4]
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
> 以這個A為source的Persona_Speech_Target列表

`[2]`
> **以目前active persona為發言人**，以`[1]`所列任一Persona_Speech_Target為target的Persona_Speech列表；權限不足則無此項目

`[3]`
> 所有以`[1]`所列target中任一為target，且type為ask_answer_review的Persona_Speech數目

`[4]`
> `[3]`所列的Persona_Speech取content平均值，也就是這個A的平均評分

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
