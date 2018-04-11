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
      summary: {
        question_count // [1]
        answer_count // [2]
      }
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
  summary: {
    question_count // [1]
    answer_count // [2]
  }
  matches: [
    *matchObject*
  ]
}
```

`[1]`
> 屬於這個game的問題數量

`[2]`
> 屬於這個game的問題的答案數量
