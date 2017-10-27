# Term

- [List terms](#list-terms)
- [Get a single term](#get-a-single-term)
- [Create a term](#create-a-term)
- [Update a term](#update-a-term)
- [Delete a term](#delete-a-term)

## List terms
```
GET /console/lab/terms
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `term` | integer: term index | 屆期 | exact | `7` `8` |

### Response
```
{
  rows: [
    {
      index,
      start_date,
      end_date,
      sessions: [
        {
          session_index,
          temp_session_index,
          start_date,
          end_date
        }
        ...
      ],
      parties: [
        {
          id,
          name,
          abbreviation,
          color,
          emblem
        }
        ...
      ],
      caucuses: [
        {
          id,
          name,
          abbreviation,
          color,
          emblem
        }
        ...
      ],
      districts: [
        {
          name,
          abbreviation,
          zone_name,
          index,
          neighborhoods
        }
        ...
      ]
    }
  ],
  totalRowCount
}
```

## Get a single term
```
GET /console/lab/terms/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```
{
  index,
  start_date,
  end_date,
  sessions: [
    {
      session_index,
      temp_session_index,
      start_date,
      end_date
    }
    ...
  ],
  parties: [
    {
      id,
      name,
      abbreviation,
      color,
      emblem
    }
    ...
  ],
  caucuses: [
    {
      caucus: {
        id,
        name,
        abbreviation,
        color,
        emblem
      }
      parties: [
        {
          id,
          name,
          abbreviation,
          color,
          emblem
        }
        ...
      ]
    }
    ...
  ],
  districts: [
    {
      name,
      abbreviation,
      zone_name,
      index,
      neighborhoods
    }
    ...
  ]
}
```

## Create a term
```
POST /console/lab/terms
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Input

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `index` | integer | 🌕 | 屆期 |
| `start_date` | timestamp | 🌕 | 起始日 |
| `end_date` | timestamp | 🌕 | 終止日 |
| `sessions` **[1]** | array of objects | 🌕 | 這個屆期的會期 |
| `parties` | array of integers: party IDs | 🌕 | 這個屆期曾經有席次的政黨 |
| `caucuses` **[2]** | array of objects | 🌕 | 這個屆期曾經有席次的黨團或政團 |
| `districts` **[3]** | array of objects | 🌕 | 這個屆期的選區 |

`[1]`

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `session_index` | integer | 🌕 | 會期 |
| `temp_session_index` | integer | 🌕 | 臨時會期 |
| `start_date` | timestamp | 🌕 | 起（起始時間） |
| `end_date` | timestamp | 🌕 | 訖（結束時間） |

`[2]`

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `caucus` | integer | 🌕 | 黨團或政團的 ID |
| `parties` | array of integers: party ID | 🌕 | 與該黨團或政團關聯的政黨 ID 列表 |

`[3]`

| Key | Type | Required | Description |
| --- | --- | :---: | --- |
| `name` | string | 🌕 | 選區全名 |
| `abbreviation` | string | 🌕 | 選區短名 |
| `zone_name` | string | 🌕 | 區域 |
| `index` | integer | 🌕 | 編號 |
| `neighborhoods` | array of strings | 🌑 | 選區內行政區 |

### Sample input
```json
{
  "index": 8,
  "start_date": 1498838400000,
  "end_date": 1498838400000,
  "sessions": [
    {
      "session_index": 1,
      "temp_session_index": 0,
      "start_date": 1498838400000,
      "end_date": 1498838400000
    }
  ],
  "parties": [
    2, 3, 4
  ],
  "caucuses": [
    {
      "caucus": 2,
      "parties": [
        2, 4, 7
      ]
    }
  ],
  "districts": [
    {
      "name": "台北市第一選舉區",
      "abbreviation": "台北一",
      "zone_name": "台北",
      "index": 1,
      "neighborhoods": "北投區、士林區"
    }
  ]
}
```

### Response
> Returns the newly created term

## Update a term
```
PATCH /console/lab/terms/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

> 參考 [Create a term](#create-a-term)

## Delete a term
```
DELETE /console/lab/terms/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```javascript
204 No Content
```
