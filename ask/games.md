# Game of ASK

- [List games](#list-games)
- [Get a single game BY SLUG](#get-a-single-game-BY-SLUG)
- [Get the latest config of a game BY SLUG](#get-the-latest-config-of-a-game-BY-SLUG)

## List games
```
GET /ask/games
```

### Auth
NO

### Paging
NO

### Response
`請參照 /console/ask/games`

## Get a single game BY SLUG
```
GET /ask/games/:slug
```

### Auth
NO

### Paging
NO

### Response
`請參照 /console/ask/games/:slug`

## Get the latest config of a game BY SLUG
```
GET /ask/games/:slug/config
```

### Auth
NO

### Paging
NO

### Response
```
{
  id
  game_id
  push_threshold
  push_duration
  data: {} // JSON object
  create_date // 特別需要create_date，告知使用者最新config生效時間
}
```
