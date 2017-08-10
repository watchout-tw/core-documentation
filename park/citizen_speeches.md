# Citizen speech

## List citizen speeches
```
GET /park/citizen_speeches
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `citizen_handle` | string: citizen handle | 用草民代號過濾草民言論清單 | exact | `chihao` `chiawei` `charlie` |
| `target_source_entity` | string: table name | 用speech target source entity name過濾草民言論清單；Source entity是指`Citizen_Speech_Target.source_entity` | exact | `Poll` `Article` |
| `target_source_id` | integer: id to table referenced by `target_source_entity` | 用speech target source ID過濾草民言論清單；Source ID是指`Citizen_Speech_Target.source_id`，傳入值必須是整數，並與`target_source_entity`所指table的key的格式相符 | exact | `1` `2` |

### 解釋

- `GET /park/citizen_speeches?citizen_handle=chihao&target_source_entity=Poll&target_source_id=1`
  - → 草民代號`chihao`對ID為`1`的`Poll`所發表的所有言論

### Response
```
{
  rows: [
    {
      id,
      citizen_handle,
      citizen_speech_target: {
        id,
        type,
        source_entity,
        source_id
      },
      date,
      type,
      content
    }
    ...
  ],
  totalRowCount
}
```

## Get a single citizen speech

## Create a citizen speech
```
POST /park/citizen_speeches
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Input

| Key | Type | Description |
| --- | --- | --- |
| citizen_speech_target_id | integer: citizen speech target ID | citizen speech target ID |
| type | string | 言論類型 |
| content | string | 言論內容 |

### Sample input
```json
{
  "citizen_speech_target_id": 1,
  "type": "ballot",
  "content": "黃培閎"
}
```

### Response
> Returns the newly created citizen speech
