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
| `target_source_id` | string: key to table referenced by `target_source_entity` | 用speech target source ID過濾草民言論清單；Source ID是指`Citizen_Speech_Target.source_id`，傳入值必須與`target_source_entity`所指table的key的格式相符 | exact | `1` `foo` |

### 解釋

- `GET /park/citizen_speeches?citizen_handle=chihao&target_source_entity=Poll&target_source_id=1`
  - → 草民代號`chihao`對ID為`1`的`Poll`所發表的所有言論

### Response
```
{
  rows: [
    {
      id,
      citizen: {
        id,
        handle
      },
      citizen_speech_target: {
        id,
        source_entity,
        source_id,
        source: {
          id,
          ?... /* 參考 source_entity */
        }
      },
      date,
      type,
      value
    }
    ...
  ],
  totalRowCount
}
```
