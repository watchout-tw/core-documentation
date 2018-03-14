# Speech

- [List speeches](#list-speeches)
- [Get a single persona speech](#get-a-single-persona-speech)
- [Create a persona speech](#create-a-persona-speech)

## List speeches
```
GET /persona/speeches
```

### Auth
- “citizen” AND “self”

### Paging
NO

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `target_source_entity` | string: table name | 用speech target source entity name過濾草民言論清單；Source entity是指`Persona_Speech_Target.source_entity` | exact | `Poll` `Article` |
| `target_source_id` | integer: id to table referenced by `target_source_entity` | 用speech target source ID過濾草民言論清單；Source ID是指`Persona_Speech_Target.source_id`，傳入值必須是整數，並與`target_source_entity`所指table的key的格式相符 | exact | `1` `2` |

### 解釋

- `GET /persona/speeches?target_source_entity=Poll&target_source_id=1`
  - → 目前Persona對ID為`1`的`Poll`所發表的所有言論

### Response
```
{
  rows: [
    {
      id
      persona_speech_target: {
        id
        type
        source_entity
        source_id
        sp_type
        sp_per_persona
        data: {}
      }
      date
      type
      content
    }
    ...
  ]
  totalRowCount
}
```

## Get a single persona speech
```
GET /persona/speeches/:id
```

### Auth
- “citizen” AND “self”

### Paging
NO

## Create a persona speech
```
POST /persona/speeches
```

### Auth
- “citizen” AND “self”

### Paging
NO

### Input

| Key | Type | Description |
| --- | --- | --- |
| persona_speech_target_id | integer: persona speech target ID | persona speech target ID |
| type | string | 言論類型 |
| content | string | 言論內容 |
| data | object | 資料 |

### Sample input
```json
{
  "persona_speech_target_id": 1,
  "type": "ballot",
  "content": "黃培閎"
}
```

### Response
> Returns the newly created persona speech
