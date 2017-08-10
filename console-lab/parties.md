# Party

- [List parties](#list-parties)
- [Get a single party](#get-a-single-party)
- [Create a party](#create-a-party)
- [Update a party](#update-a-party)
- [Delete a party](#delete-a-party)

## List parties
```
GET /console/lab/parties
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Available query parameters

| Key | Type | Description | Match | Example |
| --- | --- | --- | --- | --- |
| `name` | string | 用姓名過濾政黨清單 | partial | `無` `民` |

### Response
```
{
  rows: [
    {
      id,
      name,
      abbreviation,
      color,
      emblem,
      basic_info,
      add_info
    }
    ...
  ],
  totalRowCount
}
```

## Get a single party
```
GET /console/lab/parties/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```
{
  id,
  name,
  abbreviation,
  color,
  emblem,
  basic_info,
  add_info
}
```

## Create a party
```
POST /console/lab/parties
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Input

| Key | Type | Description |
| --- | --- | --- |
| `name` | string | **Required.** 名稱 |
| `abbreviation` | string | **Required.** 簡稱 |
| `color` | string array | 代表色 |
| `emblem` | string | 代表徽章的檔案路徑 |
| `basic_info` | string | 基本資訊 |
| `add_info` | string | 補充資訊 |

### Sample input
```json
{
  "name": "無黨籍",
  "abbreviation": "無黨籍",
  "color": "#000,#fff",
  "emblem": "/path/to/emblem.png",
  "basic_info": "Lorem ipsum.",
  "add_info": "Lorem ipsum."
}
```

### Response
> Returns the newly created party

## Update a party
```
PATCH /console/lab/parties/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

> 參考 [Create a party](#create-a-party)

## Delete a party
```
DELETE /console/lab/parties/:id
```

| Auth | Paging |
| :---: | :---: |
| 🌕 | 🌑 |

### Response
```javascript
204 No Content
```
