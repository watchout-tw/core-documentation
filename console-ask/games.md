# Game of ASK

- [List games](#list-games)
- [Get a single game BY SLUG](#get-a-single-game-BY-SLUG)
- [Create an game](#create-a-game)
- [Update an game](#update-a-game-by-slug)

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

`[1]`
> 屬於這個 game 的問題數量

`[2]`
> 屬於這個 game 的問題的答案數量

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
| `status` | String | 🌑 | 此給問的狀態 |
| `slug` | String | 🌕 | 此給問的短網址 |
| `year` | Integer | 🌕 | 給問的年份 |
| `type` | String | 🌕 | 此給問的類型，如 mayor, topic |
| `battlefield` | String | 🌕 | 此給問的戰場（地點或議題） |
| `title` | String | 🌑 | 此給問的標題 |
| `before_title` | String | 🌑 | 此給問的 before_title |
| `after_title` | String | 🌑 | 此給問的 after_title |
| `image` | String | 🌑 | 此給問的封面圖片連結 |
| `index` | Integer | 🌑 | 此給問排序 |
| `data` | Object | 🌑 | 此給問的其它資訊 |
| `players` **[3]** | Array of objects: personas | 🌑 | 參與此給問的玩家 |
| `matches` **[4]** | Array of objects: matches | 🌑 | 此給問的所有活動 |

`[3]`

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `id` | Integer | 🌕 | 此玩家的 Persona ID |
| `status` | String | 🌑 | 此玩家在此給問的狀態 |
| `type` | String | 🌑 | 此玩家在此給問的類型 |
| `index` | String | 🌑 | 此玩家在此給問的排序 |
| `data` | Object | 🌑 | 此玩家的其它資訊 |

`[4]`

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `id` | Integer | 🌕 | 此給問活動的 Event ID |
| `slug` | String | 🌑 | 此給問活動的短網址 |
| `status` | String | 🌑 | 此給問活動的狀態 |
| `type` | String | 🌑 | 此給問活動的類型 |
| `index` | String | 🌑 | 此活動在此給問的排序 |
| `data` | Object | 🌑 | 此給問活動的其它資訊 |

## Update a game BY SLUG
```
PATCH /console/ask/games/:gameSlug
```

### Auth
- `editor`

### Paging
NO

> 參考 [Create a game](#create-a-game)
