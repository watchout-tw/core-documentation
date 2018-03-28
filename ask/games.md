# Game of ASK

- [List games](#list-games)
- [Get a single game BY SLUG](#get-a-single-game-BY-SLUG)

## List games
```
GET /ask/games
```

### Auth
NO

### Paging
NO

### Response
```
{
  rows: [
    {
      id
      status
      slug
      year
      type
      battlefield
      title
      before_title
      after_title
      image
      index
      data: {}
      players: []
    }
    ...
  ]
  totalRowCount
}
```

## Get a single game BY SLUG
```
GET /ask/games/:slug
```

### Auth
NO

### Paging
NO

### Response
```
{
  id
  status
  slug
  year
  type
  battlefield
  title
  before_title
  after_title
  image
  index
  data: {}
  players: []
  matches: [
    *matchObject*
  ]
}
```
