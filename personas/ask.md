# Public info of a persona under ASK

## Marked questions
```
GET /personas/:id/ask/marked_questions
```

### Auth
NO

### Paging
NO

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `game` | string | 用game過濾答案清單 | exact | `2018-taipei` |

### Response
```
{
  persona_id
  games: [
    {
      game_id
      questions: [
        {
          question: {} // questionObject
          mark
          data: {} // JSON object
        }
        ...
      ]
    }
    ...
  ]
}
```
