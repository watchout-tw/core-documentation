# Persona speech

## List persona speeches
```
GET /park/persona_speeches
```

### Auth
- “editor”

### Paging
NO

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `persona_id` | int: persona ID | 用Persona ID過濾草民言論清單 | exact | `1` `2` `42` |
| `target_source_entity` | string: table name | 用speech target source entity name過濾草民言論清單；Source entity是指`Persona_Speech_Target.source_entity` | exact | `Poll` `Article` |
| `target_source_id` | integer: id to table referenced by `target_source_entity` | 用speech target source ID過濾草民言論清單；Source ID是指`Persona_Speech_Target.source_id`，傳入值必須是整數，並與`target_source_entity`所指table的key的格式相符 | exact | `1` `2` |

### 解釋

- `GET /park/persona_speeches?persona_id=42&target_source_entity=Poll&target_source_id=1`
  - → Persona ID `42`對ID為`1`的`Poll`所發表的所有言論

### Response
```
{
  rows: [
    {
      id
      persona_id
      persona_speech_target: {
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
      date
      type
      content
      data
    }
    ...
  ]
  totalRowCount
}
```
