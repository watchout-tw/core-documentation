# Persona speech target

## List persona speech targets
```
GET /park/persona_speech_targets
```

### Auth
- “citizen”

### Paging
NO

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `type` | string | 用target類型過濾target清單 | exact | `poll` `article` |
| `source_entity` | string: table name | 用source entity過濾target清單 | exact | `Poll` `Article` |
| `source_id` | integer: id to table referenced by `source_entity` | 用source ID過濾target清單 | exact | `1` `2` |

### Response
```
{
  rows: [
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
  ]
  totalRowCount
}
```
