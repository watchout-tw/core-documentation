# Game of ASK

- [List games](#list-games)
- [Get a single game BY SLUG](#get-a-single-game-BY-SLUG)
- [Create an game](#create-an-game)
- [Update an game](#update-an-game-by-slug)

## List games
```
GET /console/ask/games
```

### Auth
NO

### Paging
No

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
      players: [
        {
          id
          type
          status
          title
          name
          avatar
          start_date
          end_date
          data: {}
        }
        ...
      ]
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
GET /console/ask/games/:gameSlug
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

## Create a game
```
POST /console/ask/games
```

### Auth
- `editor`

### Paging
NO

### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `status` | string | 🌑 | 此給問的狀態 |
| `slug` | string | 🌕 | 此給問的短網址 |
| `year` | integer | 🌕 | 給問的年份 |
| `type` | string | 🌕 | 此給問的類型，如 mayer, topic |
| `battlefield` | string | 🌕 | 此給問的戰場（地點或議題） |
| `image` | string | 🌑 | 此給問的封面圖片連結 |
| `index` | integer | 🌑 | 此給問排序 |
| `players` | array of integers: persona IDs  | 🌑 | 參與此給問的玩家 |
| `matches` | array of integers: event IDs  | 🌑 | 此給問的所有活動 |

## Update a game BY SLUG
```
PATCH /console/ask/games/:gameSlug
```

### Auth
- `editor`

### Paging
NO

> 參考 [Create an game](#create-an-game)

`[1]`
> 屬於這個game的問題數量

`[2]`
> 屬於這個game的問題的答案數量
