# Question of ASK

- [List questions](#list-questions)
- [Get a single question](#get-a-single-question)
- [Create a question](#create-a-question)
- [Push a question](#push-a-question)

## List questions
```
GET /ask/questions
```

### Auth
NO
> `persona_speeches`需要是“citizen” AND “self”

### Paging
YES

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `game` | string | 用game slug過濾問題清單 | exact | `2018-taipei` |
| `q` | string | 用關鍵字過濾問題清單 `[1]` | exact | `殭屍` |
| `topics` | array of integers: topic IDs | 用議題過濾問題清單 | 任一即可 | `[1, 2, 3]` |
| `statuses` | array of strings: statuses `[2]` | 用「狀態」過濾問題清單 | 全部符合 | `["keep_pushing", "expect_answers"]` |
| `have_pushed` | integer | 用「是否已連署」過濾問題清單 | exact | `0` OR `1` |
| `order_by` | string `[3]` | 問題排序 | exact | `start_date` |

`[1]`
> 搜尋範圍：`ASK_Question.title`, `ASK_Question.content`, `ASK_Question.references`

`[2]`
> 可能的string：`keep_pushing`、`expect_answers`、`failed`

```js
all_targets = all Persona_Speech_Target
targets = all_targets.filter(target =>
  target.source_entity === 'ASK_Question' &&
  target.source_id === question.id &&
  target.sp_type === 'ask_question_push'
)
assert(targets.length === 1) // 一定有一個，且只有一個符合條件的target
question.target = targets[0]
```

`keep_pushing`
```js
Now.time <= Question.target.start_date
```

`expect_answers`
```js
Question.push.count >= Question.data.threshold
```

`failed`
```js
Now.time > Question.target.start_date && Question.push.count < Question.data.threshold
```

`[3]`
> 可能的string：`start_date`、`push_count`

### Response
```
{
  rows: [
    {
      id
      status
      slug
      type
      persona: {} // 與GET /persona格式相同
      game: {} // 與GET /ask/games中的Game object格式相同
      index
      topic_type
      topic_id
      image
      title
      content
      references: [
        {}
        ...
      ]
      chatroom_id
      data: {}
      assigned_personas: [ // [1]
        *personaObject*
        ...
      ]
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
      push: {
        count // [4]
      }
      answers: [
        {
          id
          status
          slug
          persona: {}
          index
          image
          content
          references: [
            {}
            ...
          ]
          data: {}
        }
      ]
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
> From ASK_Question_Assigned_Persona

`[2]`
> 以這個Q為source的Persona_Speech_Target列表

`[3]`
> **以目前active persona為發言人**，以`[2]`所列任一Persona_Speech_Target為target的Persona_Speech列表；權限不足則無此項目

`[4]`
> 計算以`[2]`所列target中任一為target，且type是ask_question_push的Persona_Speech數量，也就是這個Q的連署人數

## Get a single question
```
GET /ask/questions/:id
```

### Auth
NO
> `persona_speeches`需要是“citizen” AND “self”；權限不足則無此項目

### Paging
NO

### Response
> 與[List questions](#list-questions)中的Question object格式相同

## Create a question
```
POST /ask/questions
```

### Auth
- `citizen`

### Paging
NO

## Push a question
```
POST /ask/questions/:id/push
```

### Auth
- `citizen` AND `with_info`

### Paging
NO
